# 🚩 HackDNA - Anonymous

- **Plataforma:** HackDNA
- **Dificuldade:** Fácil (Easy)
- **Categoria:** Redes & Infraestrutura
- **Tópico Principal:** FTP (File Transfer Protocol)
- **Flags:** 1 (`flag.txt`)

---

## 📌 Visão Geral

O desafio **Anonymous** foca na exploração de serviços de transferência de arquivos mal configurados, especificamente o **FTP (File Transfer Protocol)**. O objetivo é identificar permissões anónimas ativas, enumerar ficheiros sensíveis disponíveis no servidor e explorar essas informações para obter o acesso e capturar a flag.

---

## 🛠️ Ferramentas & Conceitos Utilizados

- **Protocolos de Rede:** FTP (Porta 21), TCP.
- **Ferramentas:** `Nmap`, `ftp` (cliente CLI), `Netcat`.
- **Técnica:** Enumeração de serviços, Login Anónimo (*Anonymous FTP Login*) e recolha de dados sensíveis.

---

## 1. Reconhecimento & Enumeração (Recon)

Com o início da máquina, o primeiro passo foi realizar a varredura de portas para identificar os serviços em execução:

```bash
nmap -sC -sV -p- <IP_DA_MAQUINA>
'''

Resultados encontrados:
Porta 21/FTP: Serviço vsftpd ativo, permitindo o acesso de utilizadores não autenticados através de login anónimo.

2. Exploração (Exploitation)
Com base na descoberta de que o serviço FTP permitia conexões genéricas:

Acesso Anónimo: Efetuou-se a ligação ao servidor FTP utilizando o utilizador anonymous (sem palavra-passe ou com uma credencial genérica):

Bash
ftp <TARGET_IP>
Enumeração de Diretórios: Listaram-se os diretórios e ficheiros disponíveis no servidor com o comando ls -la para encontrar elementos ocultos ou partilhas abertas.

Transferência de Ficheiros: Utilizou-se o comando get para transferir os ficheiros descobertos para a máquina local.

3. Conclusão & Obtenção da Flag
Através da análise dos ficheiros transferidos do servidor FTP, localizou-se a flag correspondente (flag.txt), concluindo com sucesso o laboratório na plataforma HackDNA.

