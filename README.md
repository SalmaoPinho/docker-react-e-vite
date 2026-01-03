# Docker React + Vite

Um projeto full-stack moderno utilizando Docker para orquestrar uma aplicação React com Vite, backend NestJS, PostgreSQL e Nginx como proxy reverso.

## 🚀 Tecnologias

- **Frontend**: React 19 + Vite 7
- **Backend**: NestJS (planejado)
- **Banco de Dados**: PostgreSQL (Alpine)
- **Proxy Reverso**: Nginx
- **Gerenciamento de BD**: pgAdmin 4
- **Containerização**: Docker & Docker Compose

## 📋 Pré-requisitos

- [Docker](https://www.docker.com/get-started) instalado
- [Docker Compose](https://docs.docker.com/compose/install/) instalado

## 🔧 Configuração

### Variáveis de Ambiente

O projeto utiliza um arquivo `.env` para configuração. As principais variáveis são:

```env
# Portas
FRONTEND_PORT=5173
BACKEND_PORT=3000
POSTGRES_PORT=5432
NGINX_PORT=8080

# PostgreSQL
POSTGRES_DB=mydatabase
POSTGRES_USER=myuser
POSTGRES_PASSWORD=mypassword

# pgAdmin
PGADMIN_DEFAULT_EMAIL=admin@admin.com
PGADMIN_DEFAULT_PASSWORD=admin
```

> **⚠️ Importante**: Altere as credenciais padrão antes de usar em produção!

## 🏃 Como Executar

### Iniciar todos os serviços

```bash
docker-compose up -d
```

### Parar todos os serviços

```bash
docker-compose down
```

### Reconstruir os containers

```bash
docker-compose up -d --build
```

## 🌐 Acessando os Serviços

Após iniciar os containers, você pode acessar:

- **Frontend (React)**: http://localhost:5173
- **Backend (NestJS)**: http://localhost:3000
- **Nginx**: http://localhost:8080
- **pgAdmin**: http://localhost:8880
  - Email: `admin@admin.com`
  - Senha: `admin`

## 📁 Estrutura do Projeto

```
docker-react-e-vite/
├── frontend/              # Aplicação React + Vite
│   ├── src/              # Código fonte
│   ├── public/           # Arquivos estáticos
│   ├── Dockerfile        # Dockerfile do frontend
│   └── package.json      # Dependências do frontend
├── backend/              # Aplicação NestJS (a ser implementado)
│   └── Dockerfile        # Dockerfile do backend
├── nginx/                # Configuração do Nginx
│   ├── Dockerfile        # Dockerfile do Nginx
│   └── nginx.conf        # Arquivo de configuração
├── docker-compose.yml    # Orquestração dos containers
└── .env                  # Variáveis de ambiente
```

## 🐳 Serviços Docker

### Frontend
- Container React com Vite
- Hot reload habilitado
- Porta: 5173

### Backend
- Container NestJS
- Conectado ao PostgreSQL
- Porta: 3000

### PostgreSQL
- Banco de dados relacional
- Imagem Alpine (leve)
- Volume persistente para dados
- Porta: 5432

### pgAdmin
- Interface web para gerenciar PostgreSQL
- Porta: 8880

### Nginx
- Proxy reverso
- Balanceamento de carga
- Porta: 8080

## 🔨 Desenvolvimento

### Frontend

Para trabalhar apenas no frontend:

```bash
cd frontend
npm install
npm run dev
```

### Backend

Para trabalhar apenas no backend:

```bash
cd backend
npm install
npm run start:dev
```

## 📝 Scripts Disponíveis

### Frontend
- `npm run dev` - Inicia o servidor de desenvolvimento
- `npm run build` - Cria build de produção
- `npm run lint` - Executa o linter
- `npm run preview` - Preview do build de produção

## 🗄️ Banco de Dados

### Conectar ao PostgreSQL via pgAdmin

1. Acesse http://localhost:8880
2. Faça login com as credenciais do `.env`
3. Adicione um novo servidor:
   - **Host**: `postgres`
   - **Port**: `5432`
   - **Database**: `mydatabase`
   - **Username**: `myuser`
   - **Password**: `mypassword`

## 🛠️ Troubleshooting

### Containers não iniciam
```bash
docker-compose down -v
docker-compose up -d --build
```

### Verificar logs
```bash
docker-compose logs -f [nome-do-serviço]
```

### Limpar volumes
```bash
docker-compose down -v
```

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👤 Autor

Samuel Pinho

---

⭐ Se este projeto foi útil, considere dar uma estrela!
