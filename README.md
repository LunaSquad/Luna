# 🦋 Luna — Plataforma Escolar Inclusiva

O **Luna** é um sistema web integrado (Front-end e Back-end) voltado para escolas e professores. Nosso foco é a gestão humanizada de alunos, turmas e corpo docente, com forte suporte à neurodiversidade, permitindo o acompanhamento de alunos através de registro de hiperfocos e anexação de laudos.

---

## 🚀 Tecnologias

### 💻 Front-End
- **[React](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)**
- **[Vite](https://vitejs.dev/)**
- **React Router DOM** para roteamento
- **Lucide React** para iconografia
- **date-fns** & **react-day-picker** para gestão de calendário

### ⚙️ Back-End
- **[Node.js](https://nodejs.org/) + [Express](https://expressjs.com/)**
- **[MongoDB](https://www.mongodb.com/) + [Mongoose](https://mongoosejs.com/)**
- **JWT & Bcrypt** para autenticação e segurança
- **Zod** para validação rigorosa de dados de ponta a ponta
- **Cloudinary + Multer** para upload de imagens e mídias

---

## 📋 Funcionalidades Principais

- **Autenticação Segura:** Login baseado em JWT com controle de acesso (perfis de Escola e Professor).
- **Dashboard Escolar:** Resumo estatístico rápido (total de alunos, professores e turmas ativas).
- **Gestão Completa (CRUD):** Administração de Instituições, Professores, Alunos e Turmas.
- **Perfil Inclusivo do Aluno:** Suporte a upload de fotos de perfil e laudos médicos direto para a nuvem.
- **Área do Professor:** Dashboard próprio com visão de matérias, turmas, calendário para criação/exclusão de eventos e planos de aula.
- **Interface Responsiva:** Otimizada para visualização em mobile, tablet e Full HD.

---

## ⚙️ Como rodar localmente

### Pré-requisitos
- Node.js 18+
- npm ou yarn
- Conta no MongoDB Atlas (ou cluster local rodando)
- Conta no Cloudinary (para armazenamento dos arquivos)

---

### Instalação e Preparação

```bash
# Clone o repositório
git clone https://github.com/LunaSquad/Luna.git

# Entre na pasta do projeto
cd Luna

# Instale as dependências de todo o projeto (Front e Back)
npm run setup

```

### Variáveis de ambiente

Você precisará configurar as variáveis de ambiente tanto no Back-end quanto no Front-end antes de popular o banco de dados.

**No Back-end (`Luna-web-Backend/.env`):**

```env
DB_URL=mongodb+srv://<usuario>:<senha>@<cluster>.<dominio>.mongodb.net/<database>?appName=<nome_do_app>
JWT_SECRET=sua_chave_secreta_jwt
CLOUDINARY_CLOUD_NAME=seu_cloud_name
CLOUDINARY_API_KEY=sua_api_key
CLOUDINARY_API_SECRET=seu_api_secret

```

**No Front-end (`Luna-web-FrontEnd/luna-front/.env`):**

```env
VITE_API_URL=http://localhost:4000

```

### Rodando o Projeto

1. Com o arquivo `.env` do Back-end devidamente configurado com a URL do banco, popule o MongoDB com as matérias padrão rodando o comando abaixo na **raiz do projeto**:

```bash
npm run seed

```

2. Ainda na raiz do projeto, inicie os servidores (Front-end e Back-end simultaneamente):

```bash
npm run dev

```

* O **Front-end** estará rodando em: `http://localhost:5173`
* O **Back-end** (API) estará rodando em: `http://localhost:4000`

---

## 🔗 Principais Rotas da API

| Método | Rota | Descrição |
| --- | --- | --- |
| POST | `/login` | Autenticação do usuário (retorna o Token JWT) |
| GET | `/escolas/estatisticas` | Retorna totais de alunos, professores e turmas |
| GET/POST/PUT/DELETE | `/escolas` | CRUD da instituição escolar |
| GET/POST/PUT/DELETE | `/professores` | CRUD do corpo docente |
| GET | `/professores/turma` | Retorna as métricas da turma do professor autenticado |
| GET/POST/PUT/DELETE | `/alunos` | CRUD de alunos (suporta upload de foto e laudo) |
| GET/POST/PUT/DELETE | `/turmas` | CRUD de turmas escolares |
| GET | `/materias` | Listagem das matérias cadastradas |

> **Nota:** As rotas de `/login`, listagem de `/materias` e a criação de conta em `/escolas` (POST) são públicas. Todas as demais exigem a passagem do token via header: `Authorization: Bearer <token>`.

---

## 📁 Estrutura do Repositório

```text
/
├── Luna-web-Backend/       # API REST em Node.js
│   ├── controllers/        # Lógica de requisições e respostas
│   ├── middlewares/        # Interceptadores (Uploads, Auth, Validação)
│   ├── models/             # Esquemas do banco de dados
│   ├── routes/             # Definição de endpoints
│   └── scripts/            # Scripts utilitários (ex: seed)
│
├── Luna-web-FrontEnd/      # Aplicação Single Page (SPA) em React
│   └── luna-front/
│       ├── src/
│       │   ├── assets/     # Imagens e ícones
│       │   ├── components/ # Componentes reutilizáveis (Escola, Calendário)
│       │   ├── pages/      # Telas principais e modais
│       │   └── services/   # Configuração do Axios e chamadas à API
│       └── ...
│
└── package.json            # Scripts unificados de inicialização

```

---

## 👥 Equipe de Desenvolvimento (Luminous)
