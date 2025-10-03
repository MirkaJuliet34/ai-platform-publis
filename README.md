<h1 align="center">🤖 AI Platform – Plataforma Inteligente de Automação com IA</h1>


<p align="center">
  <a href="https://youtu.be/SEU_VIDEO_ID">
    <img src="https://github.com/user-attachments/assets/50455849-d499-4dcd-96bc-cd84ab84a219" alt="Assista ao vídeo"/>
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white"/>
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white"/>
  <img src="https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white"/>
</p>


> **Uma plataforma full-stack completa para automação com inteligência artificial, monitoramento em tempo real e integrações externas — tudo em um único monorepo.**


![Private](https://img.shields.io/badge/Status-Privado-red?style=for-the-badge&logo=github)
---

## ⚙️ Backend (Flask - Python)

O **coração da aplicação** — responsável pela lógica de negócios, APIs RESTful, banco de dados e integração com serviços de IA.

### 📁 Estrutura de Código

#### 📄 `ai-backend/main.py`
> **Ponto de entrada da aplicação**

- ✅ Inicializa o Flask com configurações de segurança (`SECRET_KEY`)
- ✅ Configura **CORS** para permitir requisições do frontend
- ✅ Integra **SQLAlchemy** com PostgreSQL
- ✅ Registra todos os **Blueprints** das rotas
- ✅ Cria automaticamente as tabelas no banco (`db.create_all()`)
- ✅ Serve arquivos estáticos (frontend) e expõe métricas para **Prometheus**

#### 📁 `ai-backend/src/models/`
> **Modelos de dados com SQLAlchemy**

| Arquivo | Entidade | Campos Principais |
|--------|--------|------------------|
| `user.py` | 👤 Usuário | `id`, `username`, `email`, `password` |
| `agent.py` | 🤖 Agente | `id`, `name`, `description`, `status`, `agent_type` |
| `automation.py` | ⚙️ Automação | `id`, `name`, `description`, `status`, `integration` |
| `integration.py` | 🔗 Integração | `id`, `name`, `type`, `status`, `service` |
| `log.py` | 📝 Log | `id`, `timestamp`, `message`, `level` |

> 💡 Todos os modelos herdam de `db.Model` e usam `db.Column` com restrições como `primary_key`, `unique` e `nullable`.

#### 📁 `ai-backend/src/routes/`
> **Rotas organizadas por funcionalidade (Blueprints)**

| Arquivo | Rotas | Descrição |
|--------|------|----------|
| `auth.py` | `POST /register`, `POST /login` | 🔐 Autenticação com **JWT** |
| `user.py` | `GET /users`, `POST /users`, `PUT /:id`, `DELETE /:id` | 👥 Gerenciamento de usuários |
| `agents.py` | `GET /`, `POST /`, `GET /stats` | 🤖 Criação e monitoramento de agentes |
| `automations.py` | `GET /`, `POST /`, `PUT /:id` | ⚙️ Automações personalizadas |
| `integrations.py` | `GET /`, `POST /` | 🔌 Conexão com HubSpot, Slack, Salesforce, etc. |
| `ai_services.py` | `/ocr`, `/transcribe`, `/translate`, `/sentiment` | 🧠 Serviços de IA com **OpenAI + LangChain** |

#### 📄 `ai-backend/src/services/ai_service.py`
> **Orquestração de IA**

- 🌐 Integração com **OpenAI API** via `openai`
- 🧩 Orquestração avançada com **LangChain**
- 📝 Métodos implementados:
  - `process_ocr()` → Extração de texto de imagens
  - `process_transcription()` → Transcrição de áudio
  - `process_translation()` → Tradução automática
  - `generate_agent_response()` → Respostas inteligentes
  - `analyze_sentiment()` → Análise de sentimento

> ⚠️ Atualmente usa **mocks** para simular respostas — pronto para conectar a APIs reais!

---

## 🚀 Recursos em Destaque

- ✅ **Autenticação JWT** segura
- ✅ **Agentes inteligentes** com status em tempo real
- ✅ **Integrações externas** (HubSpot, Slack, Salesforce, Stripe)
- ✅ **Monitoramento com Grafana + Prometheus**
- ✅ **Métricas automáticas** do Flask (`/metrics`)
- ✅ **Arquitetura containerizada** com Docker Compose
- ✅ **Pronto para produção** — basta adicionar suas chaves de API

---

## 🐳 Como Rodar Localmente

```bash
## 🚀 Como rodar o projeto

Clone o repositório e entre na pasta do projeto:

```bash
git clone https://github.com/seu-usuario/ai-platform.git
cd ai-platform

cd backend-python/ai-backend
python src/main.py

cd frontend
npm install
npm run dev

# Acesse:
# 👁️  Frontend: http://localhost:3000
# 🧠  Backend: http://localhost:5000/api/users
# 📊  Grafana: http://localhost:3003 (admin/admin)
# 📈  Prometheus: http://localhost:9090
```
> **Pré-requisitos: Docker Desktop (com WSL2 no Windows)**

---

## Estrutura do Projeto

```
ai-platform/
├── backend-node/                     # Backend em Node.js (opcional)
│   ├── Dockerfile
│   └── package.json
│
├── backend-python/                   # Backend em Python (Flask)
│   ├── ai-backend/
│   │   ├── src/
│   │   │   ├── __init__.py
│   │   │   ├── main.py               # Ponto de entrada do Flask
│   │   │   │
│   │   │   ├── models/               # Modelos de dados (SQLAlchemy)
│   │   │   │   ├── agent.py
│   │   │   │   ├── automation.py
│   │   │   │   ├── integration.py
│   │   │   │   ├── log.py
│   │   │   │   └── user.py
│   │   │   │
│   │   │   ├── routes/               # Blueprints da API
│   │   │   │   ├── agents.py
│   │   │   │   ├── ai_services.py
│   │   │   │   ├── auth.py
│   │   │   │   ├── automations.py
│   │   │   │   ├── integrations.py
│   │   │   │   └── user.py
│   │   │   │
│   │   │   └── services/             # Lógica de negócios / serviços
│   │   │       └── ai_service.py
│   │   │
│   │   ├── static/                   # Arquivos estáticos (swagger.json, etc.)
│   │   │   └── swagger.json
│   │   │
│   │   ├── tests/                    # Testes unitários e integração
│   │   │   ├── test_auth.py
│   │   │   └── test_status.py
│   │   │
│   │   ├── Dockerfile
│   │   └── requirements.txt
│
├── docker/                           # Docker Compose e configurações globais
│   └── docker-compose.yml
│
├── frontend/                         # Frontend em Next.js + React
│   ├── app/                          # Páginas do Next.js (App Router)
│   │   ├── agents/
│   │   │   └── page.tsx
│   │   ├── automations/
│   │   │   └── page.tsx
│   │   ├── dashboard/
│   │   │   └── page.tsx
│   │   ├── integrations/
│   │   │   └── page.tsx
│   │   ├── login/
│   │   │   └── page.tsx
│   │   ├── reports/
│   │   │   └── page.tsx
│   │   ├── layout.tsx                 # Layout principal (sidebar + header)
│   │   └── page.tsx                   # Página root
│   │
│   ├── public/                        # Arquivos estáticos do frontend
│   │
│   ├── src/
│   │   ├── app/
│   │   │   └── globals.css            # Estilos globais / Tailwind CSS
│   │   │
│   │   └── components/                # Componentes React reutilizáveis
│   │       ├── AnimatedIcon.tsx
│   │       ├── Chart.tsx
│   │       ├── Layout.tsx
│   │       └── StatsCard.tsx
│   │
│   ├── Dockerfile
│   ├── next-env.d.ts
│   ├── next.config.js
│   ├── package-lock.json
│   ├── package.json
│   └── tailwind.config.js
│
├── grafana/                           # Configurações do Grafana
│   └── provisioning/
│       └── datasources/
│           └── datasource.yml
│
├── .env.example                       # Exemplo de variáveis de ambiente
├── DEPLOYMENT.md                       # Guia de deploy
├── PROJECT_DOCUMENTATION.md            # Documentação geral do projeto
├── README.md                           # README principal
└── WORKFLOW.md                          # Documentação de workflow e estrutura

```
## 🗄️ Banco de Dados Utilizados e Criados

💾  SQLite é utilizado para desenvolvimento e testes. O arquivo do banco de dados está localizado em:  

`ai-backend/src/database/app.db`

🔗 **ORM**  
SQLAlchemy é o Object-Relational Mapper utilizado, permitindo que modelos Python sejam mapeados diretamente para tabelas do banco de dados.

🛠️ **Tabelas Criadas (SQL)**

```sql
-- 👤 Usuários do sistema
CREATE TABLE user (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT NOT NULL UNIQUE,
    email TEXT NOT NULL UNIQUE
);

-- 🤖 Agentes inteligentes
CREATE TABLE agent (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    description TEXT,
    status TEXT,
    agent_type TEXT
);

-- 🔄 Fluxos de automação
CREATE TABLE automation (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    description TEXT,
    status TEXT,
    integration TEXT
);

-- 🔗 Integrações configuradas
CREATE TABLE integration (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    type TEXT,
    status TEXT,
    service TEXT
);

-- 📜 Registros de eventos e logs
CREATE TABLE log (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP,
    message TEXT NOT NULL,
    level TEXT
);
```



## 🌐 Frontend (Next.js + React)

O frontend é a **interface do usuário** da aplicação, construída com **Next.js** para renderização do lado do servidor e **React** para componentes interativos.  
Ele oferece uma experiência **fluida, responsiva e consistente**, alinhada aos protótipos visuais.



#### 📁 3.1 Estrutura de Código e Lógica

##### Páginas da aplicação (`frontend/src/app/`) – App Router do Next.js

| Página | Descrição | Lógica principal |
|--------|-----------|-----------------|
| **login/page.tsx** | Formulário de login com email e senha | Autenticação via backend, validação do formulário, gerenciamento de estado com `useState` e chamadas API com `useEffect` |
| **dashboard/page.tsx** | Página principal com métricas e resumos | Renderiza cards e gráficos, busca dados das APIs e atualiza estado dinamicamente |
| **agents/page.tsx** | Gerenciamento de agentes inteligentes | Lista agentes, exibe status, desempenho e informações detalhadas |
| **automations/page.tsx** | Gerenciamento de fluxos de automação | Lista fluxos, status e atividades recentes |
| **integrations/page.tsx** | Gerenciamento de integrações de API e webhooks | Visualização e controle de integrações configuradas |
| **reports/page.tsx** | Relatórios detalhados e logs do sistema | Exibe logs, eventos e análises do sistema |

> 💡 Cada página é um **componente React**, utilizando `useState` para estado interno e `useEffect` para chamadas assíncronas ao backend.

---

##### Componentes Reutilizáveis (`frontend/src/components/`)

| Componente | Função |
|------------|-------|
| **Layout.tsx** | Layout principal com **sidebar** e **header**, garantindo consistência visual |
| **StatsCard.tsx** | Cartões de estatísticas com **ícones e valores destacados** |
| **Chart.tsx** | Renderização de gráficos (Recharts, Chart.js ou simulações) |
| **AnimatedIcon.tsx** | Ícones animados para melhorar a experiência visual |

> ⚡ Componentes podem receber **props**, ter **estado interno** e lógica própria para interações dinâmicas.

---

##### Estilos Globais (`frontend/src/app/globals.css`)

- Tema **branco** para o `body`  
- Estilos para **scrollbar**, **cards** (`.glass-card`), **botões** (`.btn-primary`) e **textos com gradiente** (`.gradient-text`)  
- Status visual para elementos: **ativo ✅**, **erro ❌**, **inativo ⚪**  
- Utiliza **Tailwind CSS** para consistência e produtividade em estilização  

> ✨ Garantindo que o frontend seja **100% responsivo** e **fiel aos protótipos fornecidos**.




### Arquivos de Configuração do Frontend

-   **`frontend/package.json`**: Define as dependências do projeto Node.js (Next.js, React, Tailwind CSS, etc.) e scripts para desenvolvimento (`dev`), build (`build`) e início (`start`).
-   **`frontend/tailwind.config.js`**: Configuração do Tailwind CSS. Define cores personalizadas (incluindo `navy-blue`, `primary-blue`, `accent-blue`), fontes, espaçamentos e outras propriedades de design. Também estende as animações para ícones.
-   **`frontend/next.config.js`**: Configurações específicas do Next.js, como otimização de imagens, variáveis de ambiente e configurações de build.
-   **`frontend/tsconfig.json`**: Configuração do TypeScript para o projeto, definindo opções de compilação e regras de tipo.

#


## ⚙️ Funcionalidade de Cada API

As APIs do backend são projetadas para serem **RESTful**, fornecendo acesso aos recursos do sistema.  


#### 🔐 Autenticação

| Endpoint | Método | Descrição |
|----------|--------|-----------|
| `/api/auth/register` | POST | Registra um novo usuário. Requer `username` e `email`. 👤 |
| `/api/auth/login` | POST | Autentica um usuário existente e retorna um **token JWT** para rotas protegidas. 🔑 |

---

#### 👥 Usuários

| Endpoint | Método | Descrição |
|----------|--------|-----------|
| `/api/users` | GET | Lista todos os usuários registrados. |
| `/api/users` | POST | Cria um novo usuário. |
| `/api/users/<id>` | GET, PUT, DELETE | Operações CRUD para um usuário específico pelo ID. |

---

#### 🤖 Agentes Inteligentes

| Endpoint | Método | Descrição |
|----------|--------|-----------|
| `/api/agents/` | GET | Lista todos os agentes inteligentes. |
| `/api/agents/` | POST | Cria um novo agente inteligente. |
| `/api/agents/<id>` | GET, PUT, DELETE | Operações CRUD para um agente específico pelo ID. |
| `/api/agents/stats` | GET | Retorna estatísticas agregadas sobre os agentes (ex: número de tarefas concluídas). 📊 |

---

#### 🔄 Fluxos de Automação

| Endpoint | Método | Descrição |
|----------|--------|-----------|
| `/api/automations/` | GET | Lista todos os fluxos de automação. |
| `/api/automations/` | POST | Cria um novo fluxo de automação. |
| `/api/automations/<id>` | GET, PUT, DELETE | Operações CRUD para uma automação específica pelo ID. |

---

#### 🔗 Integrações

| Endpoint | Método | Descrição |
|----------|--------|-----------|
| `/api/integrations/` | GET | Lista todas as integrações configuradas. |
| `/api/integrations/` | POST | Cria uma nova integração. |
| `/api/integrations/<id>` | GET, PUT, DELETE | Operações CRUD para uma integração específica pelo ID. |

---

#### 🤖 Serviços de IA

| Endpoint | Método | Descrição |
|----------|--------|-----------|
| `/api/ai/agent_response` | POST | Gera uma resposta de agente inteligente com base no tipo de agente e entrada do usuário. |

-   **`/api/ai/agent_response` (POST)**: Gera uma resposta de agente inteligente com base no tipo de agente e entrada do usuário.

  #


## Utilização do Grafana

O **Grafana** é uma ferramenta de código aberto para **visualização e análise de métricas**.  
Na AI Platform, ele foi configurado para **monitorar os dados gerados pelo backend**, permitindo dashboards interativos e acompanhamento em tempo real.

---

#### ⚙️ Configuração e Acesso

**Instalação:**  
O Grafana é executado em um **container Docker**, garantindo isolamento e facilidade de deploy.

```bash
sudo docker run -d \
  --name grafana \
  -p 3000:3000 \
  -v /home/ubuntu/ai-platform/backend-python/ai-backend/src/database:/var/lib/grafana/data/databases \
  grafana/grafana:latest
````
### 🔑 Acesso ao Grafana

Após iniciar o container, o Grafana estará disponível na porta **3000**:

- 🔗 **Local:** [http://localhost:3000](http://localhost:3000)  
- 🌐 **Sandbox ou servidor:** use a URL correspondente ao ambiente de deploy

**Credenciais Padrão:**

- Usuário: `admin`  
- Senha: `admin`  

> ⚠️ O Grafana solicitará a alteração da senha no primeiro login.


#

<center>

## ⚙️🚀 Configuração do Docker e Docker Compose para o ambiente de desenvolvimento

</center>




### CORS Configurado

O CORS (Cross-Origin Resource Sharing) está configurado para permitir requisições de qualquer origem (`origins="*"`), facilitando a comunicação com o frontend durante o desenvolvimento e em ambientes de produção.

### Documentação da API (Swagger UI)

A documentação interativa da API está disponível via Swagger UI. Após iniciar o backend, acesse `/swagger` para explorar as rotas, modelos e testar os endpoints diretamente.

**URL do Swagger UI:** `http://localhost:5000/swagger` (ou a URL de deploy do backend seguida de `/swagger`)

## Frontend (Next.js)

O frontend é construído com Next.js, utilizando React para a interface do usuário e Tailwind CSS para estilização. Ele oferece uma experiência de usuário rica e responsiva, seguindo os protótipos fornecidos.

### Páginas e Componentes

-   **Páginas:** Login, Dashboard, Agentes, Automações, Integrações, Relatórios.
-   **Componentes Reutilizáveis:** Layout, StatsCard, Chart, etc.

### Estilização e Responsividade

-   **Tailwind CSS:** Utilizado para uma estilização rápida e consistente, com foco em um tema azul marinho escuro.
-   **Responsividade:** O design é adaptativo para diferentes tamanhos de tela, garantindo uma boa experiência em dispositivos desktop e mobile.
-   **Fidelidade Visual:** A interface foi desenvolvida para ser 100% fiel aos protótipos visuais fornecidos.

## Configuração e Deploy

### Ambiente de Desenvolvimento

O projeto é configurado para um ambiente de desenvolvimento fácil com Docker:

-   **Dockerfiles:** Para o frontend (Next.js) e backend (Flask).
-   **Docker Compose:** Orquestra os serviços, permitindo iniciar todo o ambiente com um único comando.
-   **Variáveis de Ambiente:** Gerenciadas via arquivo `.env` (exemplo em `.env.example`).

### Guia de Deploy

Consulte o arquivo `DEPLOYMENT.md` para instruções detalhadas sobre como implantar o frontend e o backend em diferentes ambientes (Vercel, VPS, EasyPanel, etc.).

## Testes e Validação

### Testes de API

Um script Python (`test_apis.py`) foi criado para realizar testes funcionais em todas as APIs do backend, verificando o status e a resposta dos endpoints.

### Testes de Integração Frontend-Backend

Os testes de integração garantem que a comunicação entre o frontend e o backend funcione corretamente, incluindo autenticação, carregamento de dados e interações com as APIs.

### Validação Visual

A interface do usuário é validada para garantir que corresponda aos protótipos fornecidos, com atenção à estilização, responsividade e funcionalidade dos componentes.

## Monitoramento com Grafana

O Grafana foi configurado para permitir a criação de dashboards de monitoramento para visualizar métricas e logs do sistema em tempo real. Você pode conectar o Grafana ao banco de dados SQLite do backend para criar visualizações personalizadas.

**URL do Grafana:** `http://localhost:3000` (ou a URL de deploy do Grafana)

**Credenciais Padrão:** `admin`/`admin`

**Caminho do Banco de Dados no Container Grafana:** `/var/lib/grafana/data/databases/app.db`

## Próximos Passos e Melhorias

-   Implementar testes unitários mais abrangentes para frontend e backend.
-   Adicionar autenticação JWT completa e gerenciamento de sessões.
-   Expandir os serviços de IA com mais modelos e funcionalidades.
-   Melhorar a gestão de erros e logging.
-   Implementar um sistema de notificação em tempo real.
-   Otimizar o desempenho do frontend e backend para produção em larga escala.

---




