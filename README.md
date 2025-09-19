# 🤖 ComunicaBot

Um bot de comunicados para Discord que facilita a comunicação oficial em servidores. Com ele, você pode enviar mensagens com anexos, notificar todos os membros com prioridade, solicitar confirmação de leitura e gerar relatórios em Excel com o status de visualização.

## ✨ Funcionalidades
- Envio de comunicados com até **5 arquivos anexos**
- Notificação com menção a todos os membros do servidor
- Confirmação de leitura individual
- Geração de **relatório em Excel** com quem visualizou ou não
- Controle de permissões por cargo (configurável via `config.json`)

## ⚙️ Pré-requisitos
- Python 3.10 ou superior
- Conta no Discord
- Permissão para adicionar bots ao servidor

## 🛠️ Criando o bot no Discord Developer Portal
1. Acesse https://discord.com/developers/applications  
2. Clique em **“New Application”**, dê um nome (ex: `ComunicaBot`) e **Create**  
3. Em **Bot ▶ Add Bot**, copie o **Token** (para o `.env`)  
4. Em **Privileged Gateway Intents**, ative **Server Members Intent** e **Message Content Intent**  
5. Em **OAuth2 ▶ URL Generator**, marque `bot` e `applications.commands`; em Bot Permissions selecione `Send Messages`, `Attach Files`, `Mention Everyone`, `Read Message History`, `Manage Messages`, `Use Slash Commands`, `View Channels`; copie a URL gerada e abra no navegador para adicionar o bot ao seu servidor  

## 🚀 Como usar
1. Clone o repositório: `git clone https://github.com/seu-usuario/comunicabot.git && cd comunicabot`  
2. Instale as dependências: `pip install -r requirements.txt`  
3. Configure o `.env` na raiz com: `DISCORD_TOKEN=seu_token_do_bot`, `CANAL_ID=id_do_canal_de_comunicados`, `CANAL_COMANDOS_ID=id_do_canal_de_comandos`  
4. Configure os cargos permitidos em `config.json`: `{"roles_allowed":["RH","CEO","Head Financeiro","Planejamento","Qualidade","Supervisão"]}`  
5. Execute o bot: `python comunicabot.py`
   
## 📌 Comandos disponíveis
| Comando              | Descrição                                     |
|----------------------|-----------------------------------------------|
| `/comunicado`        | Cria e envia um comunicado oficial com anexos |
| `/relatorio`         | Gera e envia o relatório de leitura em Excel  |
| `/apagar_comunicado` | Apaga o último comunicado enviado             |

## 🛡️ Permissões
Apenas usuários com cargos previamente definidos em `config.json` podem usar `/comunicado` e `/apagar_comunicado`.  

## 📊 Relatórios
Relatórios em `.xlsx` armazenados em `relatorios/`, contendo: Nome do membro; Status de leitura (Viu / Não viu); Data e hora da visualização (se aplicável)  

## 🧠 Tecnologias utilizadas
- discord.py  
- python-dotenv  
- openpyxl  

## 📁 Estrutura sugerida do projeto
    comunicabot/
    ├── bot.py
    ├── views.py
    ├── utils.py
    ├── config.json
    ├── relatorios/
    ├── .env
    ├── .gitignore
    ├── requirements.txt
    └── README.md  

## 🧼 Boas práticas
- Use `.env` para proteger dados sensíveis  
- Adicione `.gitignore` com: `.env`, `__pycache__/`, `relatorios/`, `*.xlsx`  
- Documente funções com docstrings  
- Considere testes com `pytest`  
