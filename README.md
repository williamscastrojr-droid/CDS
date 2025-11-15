Carteira Chatbot — Vercel (Frontend + Python serverless)
=======================================================

Estrutura do projeto:

carteira_chatbot_vercel/
  api/
    chat.py        -> endpoint POST /api/chat (chatbot natural language)
    add_gasto.py   -> optional: same endpoints used by bot (not required)
    get_gastos.py
    saldo.py
  carteira.db      -> SQLite inicializado com tabelas
  index.html       -> frontend chat UI (static)
  vercel.json
  requirements.txt
  README.md

Funcionalidades do chatbot (texto natural):
- "adicionar gasto 20 alimentação"  -> registra gasto
- "gastar 15,50 em gasolina"        -> registra gasto
- "definir saldo 200"               -> define saldo
- "saldo" or "qual o meu saldo"   -> mostra saldo
- "listar gastos"                   -> lista últimos gastos
- "limpar dados"                    -> apaga tudo (confirmação necessária via UI)

Observações importantes:
- O projeto usa SQLite dentro de funções serverless. Em ambientes serverless, a persistência de alterações no arquivo pode não ser garantida. Recomendado para testes e uso pessoal. Para produção, migre para um banco gerenciado (Neon/Postgres, Planetscale).
- Deploy: faça upload do ZIP no Vercel (New Project -> Import -> Upload) ou use CLI (vercel --prod).

Endpoints relevantes:
- POST /api/chat    { "message": "texto do usuário" }
- GET  /api/get_gastos
- POST /api/add_gasto  { "categoria": "...", "valor": 12.5 }
- GET  /api/saldo
- POST /api/saldo { "valor": 100 }

