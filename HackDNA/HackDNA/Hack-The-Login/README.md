# 🚩 HackDNA - Hack the Login

- **Plataforma:** HackDNA
- **Dificuldade:** Muito Fácil (Very Easy)
- **Categoria:** Segurança Web & API
- **Tópico Principal:** Authentication Bypass & Client-Side Security
- **Flags:** 1 (`User Flag`)

---

## 📌 Visão Geral

Este laboratório focou-se na exploração de uma falha de **desvio de autenticação do lado do cliente (*Authentication Bypass*)**. A aplicação web realizava a validação das credenciais de login diretamente no código executado no navegador, expondo informações sensíveis (como credenciais de acesso ou lógica de validação) através das Ferramentas de Programador (*DevTools*). O objetivo consistiu em inspecionar o código-fonte para descobrir as credenciais escondidas e efetuar login com sucesso para capturar a flag.

---

## 🛠️ Ferramentas & Conceitos Utilizados

- **Ferramentas:** Ferramentas de Desenvolvimento do Navegador (*Browser DevTools* - Inspecionar Elemento / Código-Fonte JavaScript).
- **Conceitos:** Segurança do Lado do Cliente, Lógica de Autenticação Insegura, Análise de Código JavaScript.

---

## 1. Reconhecimento & Análise do Alvo (Recon)

Ao aceder à página de login do laboratório:

1. **Inspeção do Código-Fonte:** Utilizou-se o atalho de inspecionar elementos do navegador para examinar o código HTML, ficheiros JavaScript associados e scripts embutidos na página.
2. **Descoberta de Credenciais:** Identificou-se que a validação do formulário utilizava variáveis em texto claro ou lógica lógica condicional diretamente no lado do cliente, revelando utilizador e palavra-passe pré-definidos.

---

## 2. Exploração (Exploitation)

1. **Utilização das Credenciais Expostas:** Recolheram-se os dados de acesso descobertos na análise do código-fonte.
2. **Submissão do Login:** Inseriram-se as credenciais nos campos do formulário de autenticação da página web para contornar a restrição de acesso.

---

## 3. Conclusão & Obtenção da Flag

- Com o sucesso na autenticação simulada pelo lado do cliente, o portal desbloqueou o acesso restrito e revelou a `User Flag` correspondente, concluindo o laboratório.

---

## 🛡️ Lições Aprendidas & Mitigação (Visão Defensiva)

- **Autenticação no Lado do Servidor:** Validações de login, palavras-passe ou tokens **nunca** devem ser processadas ou armazenadas no lado do cliente (HTML/JavaScript), pois qualquer utilizador consegue inspecioná-las.
- **Princípio de Ocultação de Dados Sensíveis:** O código executado no navegador deve ser considerado público; portanto, nenhuma credencial de acesso ou lógica de controlo de acesso deve residir no front-end.
- **Implementação de Hashing e APIs Seguras:** As credenciais devem ser validadas de forma segura no servidor contra uma base de dados utilizando funções de hash robustas (ex: bcrypt, Argon2).

---

## 📸 Evidência de Conclusão

<img width="1380" height="505" alt="image" src="https://github.com/user-attachments/assets/bae28cf7-88ae-468d-9045-e8b2a0782c4f" />
