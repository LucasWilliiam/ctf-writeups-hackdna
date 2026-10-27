# 🚩 HackDNA - Include me

- **Plataforma:** HackDNA
- **Dificuldade:** Fácil (Easy)
- **Categoria:** Segurança Web & API
- **Tópico Principal:** LFI (Local File Inclusion) & PHP
- **Flags:** 1 (`flag.txt`)
---

## 📌 Visão Geral

O desafio **Include me** foca-se em vulnerabilidades de aplicações web relacionadas com a inclusão insegura de ficheiros locais (**LFI - Local File Inclusion**), decorrentes do uso inadequado de funções de inclusão em **PHP** (como `include`, `require`, `file_get_contents`, etc.). O objetivo principal é manipular os parâmetros de entrada do utilizador para forçar o servidor a ler ficheiros sensíveis do sistema operativo e capturar a flag escondida.

---

## 🛠️ Ferramentas & Conceitos Utilizados

- **Tecnologias Web:** PHP, HTTP/HTTPS.
- **Ferramentas:** `cURL`, `Burp Suite`, Navegador Web.
- **Técnica:** Path Traversal (`../`), injeção de caminhos relativos e leitura de ficheiros locais do sistema.

---

## 1. Reconhecimento & Análise da Aplicação (Recon)

Ao iniciar o laboratório e aceder à aplicação web, o processo consistiu em:

1. **Mapeamento de Parâmetros:** Identificação de parâmetros no URL ou em formulários que pareciam carregar páginas dinamicamente (ex: `?page=index.php` ou `?file=`).
2. **Teste de Comportamento:** Modificação do valor do parâmetro para verificar se a aplicação refletia o conteúdo de ficheiros locais do servidor.

---

## 2. Exploração (Exploitation)

Após identificar o ponto de entrada vulnerável à inclusão de ficheiros:

 **Path Traversal (`../`):** Injeção de sequências de diretório pai para escapar ao diretório web root e navegar pelo sistema de ficheiros do servidor:
   ```bash
   curl "http://<TARGET_IP>/?page=../../../../etc/passwd"
   ```
   Obtenção da Flag: Direcionamento da consulta para o caminho onde se encontrava o ficheiro alvo da flag (flag.txt), recuperando o seu conteúdo diretamente através da resposta HTTP da aplicação.

## 3. Conclusão & Obtenção da Flag
A aplicação processou o parâmetro sem a devida sanitização, revelando o conteúdo confidencial do ficheiro alvo e permitindo submeter com sucesso a flag.txt na plataforma HackDNA.

## 🛡️ Lições Aprendidas & Mitigação (Visão Defensiva)
Evitar Inclusão Dinâmica Baseada em Input: Nunca utilizar diretamente variáveis fornecidas pelo utilizador em funções de inclusão de ficheiros do PHP (include, require, etc.).

Lista Branca (Whitelist): Se a inclusão dinâmica for estritamente necessária, implementar uma validação rigorosa utilizando uma lista restrita de ficheiros permitidos.

Desativação de Allow URL Include: Garantir que diretivas sensíveis no ficheiro de configuração do PHP (php.ini) estejam devidamente restritas (allow_url_include = Off).


<img width="1392" height="616" alt="image" src="https://github.com/user-attachments/assets/58b4662b-2055-4771-8b00-0b9262eed39a" />
