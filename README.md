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
git clone https://github.com/seu-usuario/ai-platform.git
cd ai-platform

# Crie seu .env (opcional, mas recomendado)
cp .env.example .env

# Suba tudo com um único comando
docker-compose up --build -d

# Acesse:
# 👁️  Frontend: http://localhost:3000
# 🧠  Backend: http://localhost:5000/api/users
# 📊  Grafana: http://localhost:3003 (admin/admin)
# 📈  Prometheus: http://localhost:9090


### 2.3. Banco de Dados Utilizados e Criados

-   **Banco de Dados**: SQLite é utilizado para desenvolvimento e testes. O arquivo do banco de dados é `app.db` e está localizado em `ai-backend/src/database/`.
-   **ORM**: SQLAlchemy é o Object-Relational Mapper utilizado, permitindo a definição de modelos Python que são mapeados para tabelas no banco de dados.
-   **Tabelas Criadas**: As tabelas `user`, `agent`, `automation`, `integration` e `log` são criadas automaticamente pelo SQLAlchemy (`db.create_all()`) com base nas definições dos modelos.

## 3. Frontend (Next.js - React)

O frontend é a interface do usuário da aplicação, construída com Next.js para renderização do lado do servidor e React para componentes interativos.

### 3.1. Arquivos de Código e Lógica de Programação

-   **`frontend/src/app/`**: Contém as páginas da aplicação, utilizando o App Router do Next.js.
    -   `login/page.tsx`: Página de login com formulário para email e senha. Lógica para autenticação com o backend.
    -   `dashboard/page.tsx`: Página principal após o login, exibindo métricas e resumos. Inclui componentes de cards e gráficos.
    -   `agents/page.tsx`: Página para gerenciar agentes inteligentes, listando-os e exibindo seus status e desempenho.
    -   `automations/page.tsx`: Página para gerenciar fluxos de automação, com lista de fluxos, status e atividades recentes.
    -   `integrations/page.tsx`: Página para visualizar e gerenciar integrações de API e webhooks.
    -   `reports/page.tsx`: Página para exibir relatórios e logs detalhados do sistema.
    -   **Lógica**: Cada `page.tsx` é um componente React que define a UI e a lógica de busca de dados para aquela rota específica. Utilizam `fetch` para interagir com as APIs do backend. O estado é gerenciado com `useState` e efeitos colaterais com `useEffect`.

-   **`frontend/src/components/`**: Contém componentes React reutilizáveis.
    -   `Layout.tsx`: Componente de layout principal que inclui a barra de navegação (sidebar) e o cabeçalho (header). Garante consistência visual em todas as páginas.
    -   `StatsCard.tsx`: Componente para exibir estatísticas em formato de cartão, com ícones e valores destacados.
    -   `Chart.tsx`: Componente genérico para renderizar gráficos (utiliza uma biblioteca de gráficos como Recharts ou Chart.js, ou simulações).
    -   **Lógica**: Componentes React que recebem `props` e renderizam partes da UI. Podem ter seu próprio estado interno e lógica de interação.

-   **`frontend/src/app/globals.css`**: Arquivo de estilos globais. Contém estilos base, variáveis CSS e classes utilitárias personalizadas do Tailwind CSS.
    -   **Lógica**: Define o tema azul marinho escuro para o `body`, estilos para scrollbar, e classes para cards (`.glass-card`), botões (`.btn-primary`) e textos com gradiente (`.gradient-text`). Também define estilos para status (ativo, erro, inativo) e atividades.

### 3.2. Arquivos de Configuração do Frontend

-   **`frontend/package.json`**: Define as dependências do projeto Node.js (Next.js, React, Tailwind CSS, etc.) e scripts para desenvolvimento (`dev`), build (`build`) e início (`start`).
-   **`frontend/tailwind.config.js`**: Configuração do Tailwind CSS. Define cores personalizadas (incluindo `navy-blue`, `primary-blue`, `accent-blue`), fontes, espaçamentos e outras propriedades de design. Também estende as animações para ícones.
-   **`frontend/next.config.js`**: Configurações específicas do Next.js, como otimização de imagens, variáveis de ambiente e configurações de build.
-   **`frontend/tsconfig.json`**: Configuração do TypeScript para o projeto, definindo opções de compilação e regras de tipo.

## 4. Funcionalidade de Cada API

As APIs do backend são projetadas para serem RESTful e fornecerem acesso aos recursos do sistema:

-   **`/api/auth/register` (POST)**: Registra um novo usuário no sistema. Requer `username` e `email`.
-   **`/api/auth/login` (POST)**: Autentica um usuário existente e retorna um token JWT para acesso a rotas protegidas.
-   **`/api/users` (GET)**: Retorna uma lista de todos os usuários registrados.
-   **`/api/users` (POST)**: Cria um novo usuário.
-   **`/api/users/<id>` (GET, PUT, DELETE)**: Operações CRUD para um usuário específico pelo seu ID.
-   **`/api/agents/` (GET)**: Retorna uma lista de todos os agentes inteligentes.
-   **`/api/agents/` (POST)**: Cria um novo agente inteligente.
-   **`/api/agents/<id>` (GET, PUT, DELETE)**: Operações CRUD para um agente específico pelo seu ID.
-   **`/api/agents/stats` (GET)**: Retorna estatísticas agregadas sobre os agentes (ex: número de tarefas concluídas por agente).
-   **`/api/automations/` (GET)**: Retorna uma lista de todos os fluxos de automação.
-   **`/api/automations/` (POST)**: Cria um novo fluxo de automação.
-   **`/api/automations/<id>` (GET, PUT, DELETE)**: Operações CRUD para uma automação específica pelo seu ID.
-   **`/api/integrations/` (GET)**: Retorna uma lista de todas as integrações configuradas.
-   **`/api/integrations/` (POST)**: Cria uma nova integração.
-   **`/api/integrations/<id>` (GET, PUT, DELETE)**: Operações CRUD para uma integração específica pelo seu ID.
-   **`/api/ai/agent_response` (POST)**: Gera uma resposta de agente inteligente com base no tipo de agente e entrada do usuário.


## 5. Utilização do Grafana

O Grafana é uma ferramenta de código aberto para visualização e análise de métricas. Ele foi configurado para monitorar os dados gerados e gerenciados pelo backend da AI Platform.

### 5.1. Configuração e Acesso

-   **Instalação**: O Grafana é executado em um container Docker, facilitando a implantação e o isolamento.
    ```bash
    sudo docker run -d --name grafana -p 3000:3000 -v /home/ubuntu/ai-platform/backend-python/ai-backend/src/database:/var/lib/grafana/data/databases grafana/grafana:latest
    ```
-   **Acesso**: Após iniciar o container, o Grafana fica acessível na porta `3000` (ex: `http://localhost:3000` ou a URL exposta pelo sandbox).
-   **Credenciais Padrão**: `admin` / `admin` (será solicitado a alteração no primeiro login).


1.  **Planejamento e Design:**
    *   Definição de requisitos e funcionalidades.
    *   Criação de protótipos de UI/UX para o frontend.
    *   Design da arquitetura do sistema (frontend, backend, banco de dados, monitoramento).
    *   Definição das especificações da API.

2.  **Configuração do Ambiente:**
    *   Inicialização dos repositórios para frontend e backend.
    *   Configuração do Docker e Docker Compose para o ambiente de desenvolvimento.
    *   Instalação de dependências iniciais.

3.  **Desenvolvimento do Frontend:**
    *   Implementação da estrutura básica do Next.js.
    *   Estilização com Tailwind CSS para corresponder aos protótipos.
    *   Criação de componentes reutilizáveis (e.g., `Layout`, `StatsCard`, `Chart`, `AnimatedIcon`).
    *   Desenvolvimento das páginas da aplicação (Login, Dashboard, Agentes, Automações, Integrações, Relatórios).
    *   Implementação de animações e responsividade.

4.  **Desenvolvimento do Backend:**
    *   Configuração do Flask e CORS.
    *   Definição dos modelos de dados (e.g., `User`, `Agent`, `Automation`).
    *   Implementação das rotas da API (e.g., autenticação, usuários).
    *   Integração com o banco de dados (SQLite para desenvolvimento).
    *   Geração da documentação da API com Swagger UI.

5.  **Integração e Monitoramento:**
    *   Configuração do Grafana para monitoramento de métricas e logs.
    *   Criação de fontes de dados e dashboards no Grafana.
    *   Conexão do frontend com as APIs do backend.

6.  **Testes:**
    *   Testes unitários para as APIs do backend (e.g., `pytest`).
    *   Testes de integração para verificar a comunicação entre os serviços.
    *   Testes de UI/UX para garantir a conformidade com os protótipos e a responsividade.

7.  **Documentação:**
    *   Atualização da documentação do projeto (`PROJECT_DOCUMENTATION.md`).
    *   Criação de instruções de deployment (`DEPLOYMENT.md`).
    *   Manutenção da documentação de workflow (`WORKFLOW.md`).
    *   Atualização da documentação da API no Swagger.

8.  **Deployment:**
    *   Preparação do ambiente de produção.
    *   Deployment dos containers Docker.
    *   Monitoramento pós-deployment.

## Estrutura do Projeto

```
ai-platform/
├── backend-node/                  # Backend em Node.js (se aplicável)
│   ├── Dockerfile
│   └── package.json
├── backend-python/                # Backend em Python (Flask)
│   ├── ai-backend/
│   │   ├── src/
│   │   │   ├── __init__.py
│   │   │   ├── main.py
│   │   │   ├── models/            # Modelos de dados
│   │   │   │   ├── agent.py
│   │   │   │   ├── automation.py
│   │   │   │   ├── integration.py
│   │   │   │   ├── log.py
│   │   │   │   └── user.py
│   │   │   ├── routes/            # Definições de rotas da API
│   │   │   │   ├── agents.py
│   │   │   │   ├── ai_services.py
│   │   │   │   ├── auth.py
│   │   │   │   ├── automations.py
│   │   │   │   ├── integrations.py
│   │   │   │   └── user.py
│   │   │   └── services/          # Lógica de negócio e serviços
│   │   │       └── ai_service.py
│   │   ├── static/                # Arquivos estáticos, incluindo swagger.json
│   │   │   └── swagger.json
│   │   ├── tests/                 # Testes unitários e de integração
│   │   │   ├── test_auth.py
│   │   │   └── test_status.py
│   │   └── Dockerfile
│   │   └── requirements.txt
├── docker/                        # Configurações do Docker Compose
│   └── docker-compose.yml
├── frontend/                      # Frontend em Next.js
│   ├── app/                       # Páginas do Next.js (App Router)
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
│   │   ├── layout.tsx
│   │   └── page.tsx
│   ├── public/                    # Arquivos estáticos do frontend
│   ├── src/
│   │   ├── app/
│   │   │   └── globals.css
│   │   └── components/            # Componentes React reutilizáveis
│   │       ├── AnimatedIcon.tsx
│   │       ├── Chart.tsx
│   │       ├── Layout.tsx
│   │       └── StatsCard.tsx
│   ├── Dockerfile
│   ├── next-env.d.ts
│   ├── next.config.js
│   ├── package-lock.json
│   ├── package.json
│   └── tailwind.config.js
├── grafana/                       # Configurações do Grafana
│   └── provisioning/
│       └── datasources/
│           └── datasource.yml
├── .env.example                   # Exemplo de variáveis de ambiente
├── DEPLOYMENT.md                  # Instruções de deployment
├── PROJECT_DOCUMENTATION.md       # Documentação geral do projeto
├── README.md                      # README principal do projeto
└── WORKFLOW.md                    # Documentação de workflow e estrutura
```


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




