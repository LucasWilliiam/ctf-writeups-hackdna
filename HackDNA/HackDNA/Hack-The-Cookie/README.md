# 🚩 HackDNA - Hack the Cookie: Ataque de Envenenamento de Cookie

- **Plataforma:** HackDNA
- **Dificuldade:** Muito Fácil / Fácil (Very Easy / Easy)
- **Categoria:** Segurança Web & API
- **Tópico Principal:** Cookie Poisoning, Session Tampering & Base64 Encoding
- **Flags:** 1 (`User Flag`)

---

## 📌 Visão Geral

Este laboratório focou na exploração de uma vulnerabilidade de **envenenamento de cookie (*Cookie Poisoning*)** num portal corporativo. A aplicação confiava de forma cega em dados armazenados do lado do cliente contidos num cookie de sessão codificado em **Base64**. O objetivo consistiu em intercetar o cookie, decodificá-lo, alterar o parâmetro de privilégio/papel (*role*) para administrador (`admin`) e reescrevê-lo no navegador para elevar privilégios e capturar a flag[cite: 13].

---

## 🛠️ Ferramentas & Conceitos Utilizados

- **Ferramentas:** Ferramentas de Desenvolvimento do Navegador (*Browser DevTools*), descodificadores Base64 (CLI ou Online).
- **Conceitos:** Gestão de Sessões, Manipulação de Cookies, Codificação vs. Criptografia, Controlo de Acesso Baseado em Papéis (*RBAC*).

---

## 1. Reconhecimento & Análise da Aplicação (Recon)

Ao aceder à aplicação web com uma conta de utilizador comum:

1. **Inspeção de Armazenamento:** Utilizou-se o *Browser DevTools* (Application/Storage > Cookies) para analisar os cookies emitidos pela aplicação durante a autenticação.
2. **Identificação da Codificação:** Verificou-se que o valor do cookie de sessão estava codificado em **Base64** (apresentando caraterísticos blocos de codificação alfanumérica com padding `=` no fim).

---

## 2. Exploração (Exploitation)

1. **Descodificação do Cookie:** O valor do cookie capturado foi copiado e decodificado para texto legível (ex: formato JSON ou parâmetro simples indicando o papel do utilizador como `role=user`).
2. **Manipulação (*Session Tampering*):** Alterou-se o atributo do papel de utilizador de `user` para `admin`.
3. **Recodificação & Envenenamento:** O novo payload modificado foi codificado novamente em **Base64**.
4. **Injeção no Navegador:** Através das Ferramentas de Programador, o cookie original foi substituído pelo valor envenenado, forçando a aplicação a aceitar o novo nível de autorização ao atualizar a página.

---

## 3. Conclusão & Obtenção da Flag

- A aplicação validou incorretamente o cookie manipulado sem verificar a integridade ou assinatura do mesmo, concedendo acesso privilegiado de administrador e revelando a `User Flag` correspondente.

---

## 🛡️ Lições Aprendidas & Mitigação (Visão Defensiva)

- **Nunca Confiar em Dados do Cliente:** Cookies de sessão ou de autenticação nunca devem armazenar dados críticos ou papéis de utilizador em texto claro ou simplesmente codificados (Base64), pois são facilmente adulterados.
- **Uso de Tokens Assinados (JWT / Criptografia):** Se for necessário passar dados estruturados no cliente, estes devem ser devidamente assinados criptograficamente (ex: HMAC) ou encriptados para evitar adulterações.
- **Gestão de Sessão no Lado do Servidor:** O papel (*role*) e os privilégios do utilizador devem residir na base de dados do servidor associados a uma sessão segura, e não em parâmetros manipuláveis no navegador.

---

## 📸 Evidência de Conclusão

<img width="1359" height="632" alt="image" src="https://github.com/user-attachments/assets/1142c8f0-7a44-436a-a2e6-cc75ceae6be0" />

