# ROUTE DevOps

This repository contains the Docker Compose configuration for orchestrating the ROUTE application's backend and frontend services.

## 📋 Overview

This DevOps setup provides a containerized development and deployment environment for the ROUTE project, managing both backend and frontend services through Docker Compose.

## 🏗️ Architecture

The project consists of two main services:

- **Backend**: API service running on port `8000`
- **Frontend**: Web application running on port `3000`

The frontend service depends on the backend service and will wait for it to be ready before starting.

## 🚀 Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://www.docker.com/get-started) (version 20.10 or higher)
- [Docker Compose](https://docs.docker.com/compose/install/) (version 2.0 or higher)

## 📦 Project Structure

```
devops/
├── docker-compose.yaml    # Docker Compose configuration
└── README.md              # This file

../backend/                # Backend service source code
../frontend/               # Frontend service source code
```

## 🛠️ Getting Started

### 1. Clone the Repository

Make sure you have the complete project structure with both `backend` and `frontend` directories at the same level as the `devops` directory.

### 2. Start the Services

From the `devops` directory, run:

```bash
docker-compose up
```

To run in detached mode (background):

```bash
docker-compose up -d
```

### 3. Build and Start Services

If you need to rebuild the images:

```bash
docker-compose up --build
```

### 4. Stop the Services

To stop all running services:

```bash
docker-compose down
```

To stop and remove volumes:

```bash
docker-compose down -v
```

## 🌐 Accessing the Services

Once the services are running:

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8000

## 📝 Available Commands

| Command | Description |
|---------|-------------|
| `docker-compose up` | Start all services |
| `docker-compose up -d` | Start all services in detached mode |
| `docker-compose up --build` | Rebuild images and start services |
| `docker-compose down` | Stop and remove containers |
| `docker-compose ps` | List running containers |
| `docker-compose logs` | View logs from all services |
| `docker-compose logs [service]` | View logs from a specific service |
| `docker-compose restart` | Restart all services |

## 🔧 Service Details

### Backend Service

- **Container Name**: `backend-container`
- **Port**: `8000:8000`
- **Build Context**: `../backend`
- **Dockerfile**: `Dockerfile`

### Frontend Service

- **Container Name**: `frontend-container`
- **Port**: `3000:3000`
- **Build Context**: `../frontend`
- **Dockerfile**: `Dockerfile`
- **Dependencies**: Backend service

## 🐛 Troubleshooting

### Port Already in Use

If you encounter port conflicts:

1. Check if ports 3000 or 8000 are already in use:
   ```bash
   lsof -i :3000
   lsof -i :8000
   ```

2. Modify the port mappings in `docker-compose.yaml` if needed

### Services Not Starting

1. Check Docker and Docker Compose versions:
   ```bash
   docker --version
   docker-compose --version
   ```

2. View service logs:
   ```bash
   docker-compose logs backend
   docker-compose logs frontend
   ```

3. Ensure the backend and frontend directories exist and contain valid Dockerfiles

### Rebuilding After Changes

If you've made changes to the backend or frontend code:

```bash
docker-compose up --build
```

## 📚 Additional Resources

- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)

## 📄 License

[Add your license information here]

## 👥 Contributors

[Add contributor information here]

