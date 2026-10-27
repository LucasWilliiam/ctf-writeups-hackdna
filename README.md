# 🚩 HackDNA CTF Writeups

![Cybersecurity](https://img.shields.io/badge/Focus-Cybersecurity-red?style=for-the-badge&logo=shield)
![Platform](https://img.shields.io/badge/Platform-HackDNA-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In_Progress-brightgreen?style=for-the-badge)

Este repositório centraliza a documentação técnica, metodologias de invasão/defesa e relatórios detalhados (*writeups*) das máquinas e desafios resolvidos na plataforma **HackDNA**.

---

## 🎯 Objetivo

O intuito deste portfólio é demonstrar competências práticas em **Segurança da Informação**, **Testes de Intrusão (Pentest)**, **Análise de Vulnerabilidades** e **DevSecOps**, mantendo uma abordagem voltada tanto para o lado ofensivo (*Red Team*) quanto defensivo (*Blue Team*).

---

## 📑 Máquinas & Desafios Resolvidos

| Plataforma | Nome da Máquina / Desafio | Dificuldade | Categoria | Relatório (Writeup) |
| :--- | :--- | :---: | :---: | :---: |
| **HackDNA** | **Spoof!** | `Fácil` | Network & Infrastructure | [📄 Acessar Writeup](./HackDNA/Spoof/) |
| **HackDNA** | **Anonymous** | `Fácil` | Redes & Infraestrutura | [📄 Acessar Writeup](./HackDNA/Anonymous/) |
| **HackDNA** | **Lab Nmap & PrivEsc** | `Muito Fácil` | Redes & Infraestrutura | [📄 Acessar Writeup](./HackDNA/Lab-Nmap-PrivEsc/) |
| **HackDNA** | **Include me** | `Fácil` | Segurança Web & API | [📄 Acessar Writeup](./HackDNA/Include-Me/) |
| **HackDNA** | **Hack the Cookie** | `Muito Fácil` | Segurança Web & API | [📄 Acessar Writeup](./HackDNA/Hack-The-Cookie/) |
| **HackDNA** | **Hack the Login** | `Muito Fácil` | Segurança Web & API | [📄 Acessar Writeup](./HackDNA/Hack-The-Login/) |

---

## 🛠️ Ferramentas & Tecnologias Utilizadas

- **Enumeração & Reconhecimento:** `Nmap`, `Gobuster`, `HTTPie`, `cURL`, `ftp`, `telnet`.
- **Análise & Exploração Web:** `Burp Suite`, `OWASP ZAP`, `Browser DevTools`, `Python (Requests/Scapy)`.
- **Conceitos Chave:** IP Spoofing, Anonymous FTP, Privilege Escalation (Linux), LFI (Local File Inclusion), Cookie Poisoning, Session Tampering, Client-Side Authentication Bypass.
- **Sistemas Operacionais:** `Kali Linux`, `Ubuntu`.

---

## 📁 Estrutura do Repositório

```text
ctf-writeups-hackdna/
│
├── README.md                 # Índice principal do repositório
└── HackDNA/                  # Plataforma de desafios
    ├── Anonymous/            # Desafio Anonymous (FTP)
    │   └── README.md
    ├── Hack-The-Cookie/      # Desafio Hack the Cookie (Cookie Poisoning / Base64)
    │   └── README.md
    ├── Hack-The-Login/       # Desafio Hack the Login (Client-Side Bypass)
    │   └── README.md
    ├── Include-Me/           # Desafio Include me (LFI / PHP)
    │   └── README.md
    ├── Lab-Nmap-PrivEsc/     # Desafio Lab Nmap & PrivEsc (Telnet / Linux Root)
    │   └── README.md
    └── Spoof/                # Desafio Spoof! (IP Spoofing / HTTP Headers)
        ├── README.md
        └── screenshots/      # Evidências e capturas de tela
