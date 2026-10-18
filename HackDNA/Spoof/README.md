# 🚩 HackDNA - Spoof!

- **Plataforma:** HackDNA
- **Dificuldade:** Fácil (Easy)
- **Categoria:** Network & Infrastructure
- **Tópico Principal:** IP Spoofing
- **Flags:** 1 (`flag.txt`)

---

## 📌 Visão Geral

O desafio **Spoof!** aborda conceitos fundamentais de segurança em redes e infraestrutura, focando no desvio ou manipulação de controlo de acesso baseado em endereço IP através de técnicas de **IP Spoofing**. O objetivo principal é simular o envio de pacotes com um IP de origem confiável para validar o acesso a recursos protegidos.

---

## 🛠️ Ferramentas & Conceitos Utilizados

- **Protocolos de Rede:** TCP/IP, HTTP/HTTPS.
- **Ferramentas:** `cURL` / `HTTPie` / `Burp Suite` / Scripts Python (Scapy/Requests).
- **Técnica:** Manipulação de cabeçalhos HTTP (`X-Forwarded-For`, `X-Real-IP`, `X-Originating-IP`) ou pacotes IP.

---

## 1. Reconhecimento & Análise do Alvo

Após iniciar a máquina no laboratório, foi feita a análise da aplicação/serviço para compreender as restrições impostas:

1. Mapeamento da aplicação e resposta do servidor (ex: verificação de bloqueios do tipo *403 Forbidden* ou mensagens como *"Access restricted to internal network"*).
2. Análise do comportamento da aplicação em relação às solicitações HTTP/Rede.

---

## 2. Exploração (Exploitation)

Para contornar a restrição baseada em endereço IP, explorou-se a técnica de **IP Spoofing**:

1. **Injeção de Cabeçalhos / Pacotes:** Adição do cabeçalho de origem confiável (ex: `127.0.0.1` ou IP interno da rede) para simular o tráfego legítimo.
2. **Requisição Exemplo:**
   ```bash
   curl -H "X-Forwarded-For: 127.0.0.1" http://<TARGET_IP>/
   🛡️ Lições Aprendidas & Mitigação (Visão Defensiva)
Confiança Cega em Cabeçalhos: Aplicações web não devem confiar unicamente em cabeçalhos HTTP configuráveis pelo cliente (como X-Forwarded-For) para autenticar ou autorizar acessos críticos.

Autenticação Forte: Implementação de mecanismos de autenticação e autorização baseados em tokens (ex: JWT, OAuth) ou certificados, e não em dados de origem facilmente manipuláveis.

Configuração de Reverse Proxy / Firewall: Garantir que o Proxy/WAF limpe ou reescreva adequadamente os cabeçalhos de encaminhamento vindos de redes externas não confiáveis.
