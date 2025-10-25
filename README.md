# Travel Management System - CI/CD Lab Exam

A full-stack Travel Management System demonstrating CI/CD best practices with Docker deployment.

## 🏗️ Architecture

- **Backend**: Spring Boot with JWT authentication
- **Frontend**: React with Vite
- **Database**: MySQL with Docker volumes
- **Deployment**: Docker Compose orchestration

## 🚀 Quick Start

### Prerequisites
- Docker and Docker Compose
- Node.js (for frontend development)
- Java 21 (for backend development)

### Backend Deployment (Docker)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Leo-Stephen/In-Sem-Lab-CICD.git
   cd In-Sem-Lab-CICD
   ```

2. **Start the Docker services:**
   ```bash
   docker compose up --build -d
   ```

3. **Verify deployment:**
   - Backend API: http://localhost:8082
   - Database: MySQL on port 3309
   - Health Check: http://localhost:8082/actuator/health

### Frontend Development

1. **Navigate to frontend:**
   ```bash
   cd carrental-frontend
   npm install
   npm run dev
   ```

2. **Access the application:**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:8082

## 🔧 API Endpoints

### Authentication
- `POST /auth/signup` - User registration
- `POST /auth/login` - User login
- `GET /auth/users` - Get all users (for demonstration)

### Health & Monitoring
- `GET /actuator/health` - Application health
- `GET /actuator/info` - Application information

## 🐳 Docker Configuration

### Services
- **carrental-backend**: Spring Boot application (port 8082)
- **mysql-carrental**: MySQL database (port 3309)

### Volumes
- `mysql_data`: Database persistence
- `backend_data`: Application data
- `backend_logs`: Application logs

## 🧪 Testing

### API Testing
```bash
# Test user registration
curl -X POST http://localhost:8082/auth/signup \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","email":"test@example.com","password":"test123"}'

# Test user login
curl -X POST http://localhost:8082/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","password":"test123"}'

# Get all users
curl http://localhost:8082/auth/users
```

### Browser Testing
- **Frontend**: http://localhost:5173
- **Backend Health**: http://localhost:8082/actuator/health
- **User Data**: http://localhost:8082/auth/users

## 📁 Project Structure

```
In-Sem-Lab-CICD/
├── carrental-backend/          # Spring Boot backend
│   ├── src/main/java/         # Java source code
│   ├── src/main/resources/    # Configuration files
│   ├── Dockerfile.prod        # Production Dockerfile
│   └── pom.xml               # Maven configuration
├── carrental-frontend/        # React frontend
│   ├── src/                   # React source code
│   ├── package.json          # Node.js dependencies
│   └── vite.config.js         # Vite configuration
├── docker-compose.yml         # Docker orchestration
├── mysql-init/               # Database initialization
└── README.md                 # This file
```

## 🔒 Security Features

- JWT token authentication
- Password encryption with BCrypt
- CORS configuration for frontend integration
- Input validation and sanitization

## 🚀 CI/CD Best Practices

- **Containerization**: Docker for consistent deployments
- **Volume Management**: Persistent data storage
- **Health Checks**: Application monitoring
- **Environment Configuration**: Separate dev/prod configs
- **Automated Builds**: Docker Compose orchestration

## 📊 Monitoring & Logs

### Docker Logs
```bash
# View backend logs
docker logs carrental-backend-prod

# View database logs
docker logs mysql-carrental-prod

# View all services
docker compose logs
```

### Health Monitoring
- Application health: http://localhost:8082/actuator/health
- Container status: `docker ps`
- Volume usage: `docker volume ls`

## 🎯 Demonstration Points

1. **Docker Deployment**: Complete containerization
2. **Volume Support**: Data persistence across restarts
3. **API Functionality**: User registration, login, data retrieval
4. **Frontend Integration**: React app consuming backend APIs
5. **CI/CD Practices**: Automated deployment and monitoring

## 📝 Notes

- Backend runs on port 8082 (Docker) vs 8081 (local)
- Database uses port 3309 (Docker) vs 3306 (local)
- All data persists in Docker volumes
- Frontend configured to use Docker backend (port 8082)

## 🔗 Links

- **Repository**: https://github.com/Leo-Stephen/In-Sem-Lab-CICD.git
- **Backend API**: http://localhost:8082
- **Frontend**: http://localhost:5173
- **Health Check**: http://localhost:8082/actuator/health
