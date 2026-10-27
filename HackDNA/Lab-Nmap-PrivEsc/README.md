# 🚩 HackDNA - Lab de comandos Nmap: da varredura de portas à escalação de privilégios

- **Plataforma:** HackDNA
- **Dificuldade:** Muito Fácil (Very Easy)
- **Categoria:** Redes & Infraestrutura / Linux
- **Tópico Principal:** Nmap, Telnet & Escalação de Privilégios
- **Flags:** 2 (`User Flag` e `Root Flag`)

---

## 📌 Visão Geral

Este laboratório prático focou na utilização avançada dos comandos **Nmap** para reconhecimento de rede, descoberta de portas e identificação de serviços vulneráveis. O desafio incluiu a exploração de um serviço **Telnet** exposto com credenciais fracas, permitindo o acesso inicial (User Flag) e culminando num processo de **escalação de privilégios** até alcançar o nível de root (Root Flag)[cite: 11].

---

## 🛠️ Ferramentas & Conceitos Utilizados

- **Reconhecimento:** `Nmap` (Port Scanning, Script Scanning, Version Detection).
- **Acesso Inicial:** `Telnet` (Porta 23).
- **Escalação de Privilégios:** Auditoria de permissões e comandos locais no Linux.
- **Conceitos:** Mapeamento de superfície de ataque, gestão de credenciais e privilégios de sistema.

---

## 1. Reconhecimento & Varredura (Recon)

O laboratório iniciou-se com a varredura ativa de portas e serviços na máquina-alvo utilizando o `Nmap`:

```bash
nmap -sC -sV -p- <IP_DA_MAQUINA>
```
## Resultados encontrados:
Porta 23/Telnet: Serviço ativo, revelando potencial acesso via texto plano e portador de credenciais fracas ou padrão.

## 2. Acesso Inicial (User Flag)
Ligação Telnet: Com base na enumeração de portas, estabeleceu-se comunicação com o serviço Telnet exposto:

```Bash
telnet <TARGET_IP> 23
```
Autenticação: Utilização das credenciais identificadas/obtidas no laboratório para aceder ao sistema como utilizador comum.

Captura: Localização e leitura da primeira flag do desafio (User Flag).

## 3. Escalação de Privilégios (Root Flag)
Enumeração Pós-Acesso: Verificação de permissões de utilizador (sudo -l), ficheiros com SUID e configurações locais mal definidas.

Exploração: Execução dos vetores de privilégio identificados para elevar o acesso de utilizador standard para root.

Captura Final: Acesso ao diretório privilegiado e obtenção da Root Flag.

## 🛡️ Lições Aprendidas & Mitigação (Visão Defensiva)
Desativação de Protocolos Inseguros: O uso de Telnet deve ser totalmente evitado na infraestrutura moderna, sendo substituído por alternativas criptografadas como o SSH.

Políticas de Palavras-Passe Fortes: Garantir que contas de serviço ou utilizadores não utilizem credenciais fracas ou pré-definidas.

Princípio do Menor Privilégio: Auditar regularmente os binários com permissões SUID e as permissões de comandos sudo para evitar escalações de privilégio indesejadas no Linux.

<img width="1318" height="715" alt="image" src="https://github.com/user-attachments/assets/c8512673-e4fa-4d76-a12c-e106d36d86b2" />
