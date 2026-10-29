# PontoPy
> **Seu ponto de partida para programar.**

PontoPy é um mini-SaaS educativo para quem está começando em Python. Inspirado na gamificação do Duolingo, o app ensina programação por meio de lições curtas, exercícios com correção automática, um mascote animado (Rive) que reage ao seu progresso e um tutor com IA que faz perguntas em vez de entregar respostas prontas.

Projeto integrador: MVP desenvolvido em 30 dias.

---

## Funcionalidades do MVP

- **Trilha de lições** de Python (Fundamentos: variáveis, condicionais, laços, funções e listas), com 20 lições e 3 a 5 exercícios cada.
- **Editor de código** no navegador, com botão "Executar" e área de saída.
- **Correção automática** por testes, executados no próprio navegador (Pyodide).
- **Mascote animado** (Rive) com State Machine, reagindo a acertos, erros, pensamento e conquistas.
- **Tutor com IA** (chatbot socrático) que explica erros e dá dicas em três níveis, sem entregar a solução completa.
- **Gamificação:** XP, sequência de dias (streak) com congelador semanal e perfil de progresso.

## Stack

| Camada | Tecnologia |
|---|---|
| Interface | React + Vite |
| Animações | Rive (`@rive-app/react-canvas`) |
| Execução de Python | Pyodide (roda no navegador) |
| Editor | CodeMirror 6 |
| Backend | FastAPI (Python) |
| Tutor IA | API de LLM (Groq ou Claude) |
| Dados de progresso | Supabase |
| Deploy | Vercel (front) e Render (back) |

## Estrutura de pastas

```
pontopy/
├── README.md                  # Este arquivo
├── .gitignore
├── frontend/                  # Aplicação web (React + Vite)
│   ├── public/
│   │   ├── riv/               # Arquivos .riv do mascote (exportados do Rive)
│   │   └── icons/             # Favicon e ícones do app
│   └── src/
│       ├── pages/             # Telas: Splash, Home, Lição, Exercício, Perfil, Configurações
│       ├── components/        # Componentes reutilizáveis: Mascote, Editor, Chatbot, XPBar
│       ├── lib/               # Lógica: Pyodide, integração Rive, progresso, cliente da API
│       └── styles/            # Estilos globais e tokens de cor (azul, branco e complementares)
├── backend/                   # API (FastAPI)
│   └── app/                   # Rotas do chatbot, prompts do tutor e configurações
├── content/
│   └── lessons/               # Lições em JSON: texto, exercícios, testes e dicas
└── docs/                      # Documentação de apoio (escopo, decisões técnicas, beta)
```

## Como rodar (a partir da Semana 2)

> As instruções completas serão preenchidas conforme cada parte do projeto for entregue.

### Pré-requisitos
- Node.js 20 ou superior
- Python 3.11 ou superior
- Git

### Front-end
```bash
cd frontend
npm install
npm run dev
```

### Back-end
```bash
cd backend
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env           # Preencha suas chaves
uvicorn app.main:app --reload
```

### Variáveis de ambiente
Crie `backend/.env` a partir de `backend/.env.example`:
- `LLM_API_KEY`: chave da API do modelo de linguagem
- `SUPABASE_URL` e `SUPABASE_KEY`: banco de dados do progresso

Nunca envie o arquivo `.env` ao repositório. Ele já está no `.gitignore`.

## Convenções

- **Commits:** mensagens curtas no imperativo, por exemplo `Adiciona lição 01 de variáveis`.
- **Branches:** `main` estável; trabalhe em `feat/nome-da-funcionalidade` e abra um pull request para `main`.
- **Lições:** cada arquivo em `content/lessons/` segue o mesmo formato JSON (título, teoria, exercícios, testes e dicas).

## Marcos do roadmap

| Marco | Data prevista | Entregável |
|---|---|---|
| 1 | 03/11/2026 | Protótipo e mascote reagindo a inputs |
| 2 | 10/11/2026 | 10 lições jogáveis de ponta a ponta |
| 3 | 17/11/2026 | Chatbot, gamificação e progresso |
| 4 | 24/11/2026 | Beta publicado e métricas |

Entrega final e folga: 25/11 a 26/11/2026.

---

## Licença

Projeto acadêmico. Uso educacional.

---

Autor: Joabe Carvalho Neco e Silva · Faculdade Estadual PIT (Piauí Instituto de Tecnologia)
