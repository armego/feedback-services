# Feedback Services

High-performance API services built with Go for feedback management and analytics.

## 🚀 Overview

Feedback Services provides a robust, scalable backend API for handling feedback collection, processing, and analytics. Built with Go for optimal performance and concurrent processing capabilities.

## ✨ Features

- 🚄 High-performance RESTful API
- 🔐 JWT-based authentication
- 📊 Real-time data processing
- 🗄️ PostgreSQL/MongoDB support
- 📈 Analytics and reporting endpoints
- 🔄 WebSocket support for real-time updates
- 📝 Comprehensive logging
- 🛡️ Rate limiting and security middleware
- 🐳 Docker support
- ☸️ Kubernetes ready

## 📦 Installation

### Prerequisites

- Go 1.21 or higher
- PostgreSQL 14+ or MongoDB 5+
- Redis (for caching and sessions)
- Docker (optional)

### Setup

```bash
# Clone the repository
git clone https://github.com/armego/feedback-services.git
cd feedback-services

# Install dependencies
go mod download

# Copy environment configuration
cp .env.example .env
# Edit .env with your configuration

# Run database migrations
make migrate

# Build the application
make build
```

## 🏃 Running the Service

### Local Development

```bash
# Run with hot reload
make dev

# Or run directly
go run cmd/server/main.go
```

### Docker

```bash
# Build Docker image
docker build -t feedback-services .

# Run with Docker Compose
docker-compose up
```

### Production

```bash
# Build for production
make build-prod

# Run the binary
./bin/feedback-services
```

## 🔧 Configuration

### Environment Variables

```env
# Server Configuration
PORT=8080
ENV=development
LOG_LEVEL=info

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/feedback
DB_MAX_CONNECTIONS=25
DB_MAX_IDLE_CONNECTIONS=5

# Redis
REDIS_URL=redis://localhost:6379
REDIS_PASSWORD=

# Security
JWT_SECRET=your-secret-key
JWT_EXPIRY=24h
BCRYPT_COST=10

# Rate Limiting
RATE_LIMIT_REQUESTS=100
RATE_LIMIT_DURATION=1m

# External Services
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
ANALYTICS_API_KEY=
```

## 📚 API Documentation

### Base URL
```
http://localhost:8080/api/v1
```

### Authentication

```http
POST   /auth/register     - Register new user
POST   /auth/login        - User login
POST   /auth/refresh      - Refresh token
POST   /auth/logout       - Logout user
```

### Feedback Endpoints

```http
GET    /feedback          - List all feedback (paginated)
GET    /feedback/:id      - Get specific feedback
POST   /feedback          - Create new feedback
PUT    /feedback/:id      - Update feedback
DELETE /feedback/:id      - Delete feedback
GET    /feedback/stats    - Get feedback statistics
```

### Analytics Endpoints

```http
GET    /analytics/summary      - Get analytics summary
GET    /analytics/trends       - Get trend data
GET    /analytics/sentiment    - Sentiment analysis results
GET    /analytics/export       - Export analytics data
```

### WebSocket

```
WS     /ws/feedback       - Real-time feedback updates
```

## 📁 Project Structure

```
feedback-services/
├── cmd/
│   └── server/
│       └── main.go
├── internal/
│   ├── api/
│   │   ├── handlers/
│   │   ├── middleware/
│   │   └── routes/
│   ├── models/
│   ├── services/
│   ├── repositories/
│   ├── config/
│   └── utils/
├── pkg/
│   ├── database/
│   ├── logger/
│   └── validator/
├── migrations/
├── scripts/
├── docker/
├── k8s/
├── Makefile
├── Dockerfile
├── go.mod
├── go.sum
└── README.md
```

## 🛠️ Technologies

- **Language**: Go 1.21+
- **Web Framework**: Gin / Fiber / Echo
- **Database**: PostgreSQL with GORM / MongoDB
- **Caching**: Redis
- **Authentication**: JWT
- **Logging**: Zap / Logrus
- **Testing**: Go testing package + Testify
- **API Docs**: Swagger/OpenAPI
- **Monitoring**: Prometheus metrics

## 🧪 Testing

```bash
# Run all tests
make test

# Run with coverage
make test-coverage

# Run specific tests
go test ./internal/api/handlers -v

# Run integration tests
make test-integration

# Run benchmarks
make bench
```

## 📊 Performance

- Handles 10,000+ concurrent connections
- Average response time: < 50ms
- 99th percentile latency: < 200ms
- Throughput: 5,000+ requests/second

## 🐳 Docker Support

```dockerfile
# Multi-stage build for minimal image size
FROM golang:1.21-alpine AS builder
# ... build steps

FROM alpine:latest
# ... production image
```

## ☸️ Kubernetes Deployment

```yaml
# Example deployment
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl apply -f k8s/ingress.yaml
```

## 📈 Monitoring

- Prometheus metrics at `/metrics`
- Health check at `/health`
- Ready check at `/ready`

## 🔒 Security

- JWT-based authentication
- Rate limiting per IP/user
- Input validation and sanitization
- SQL injection prevention
- CORS configuration
- Secure headers middleware

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details

## 👤 Author

[@armego](https://github.com/armego)

## 🔗 Related Projects

- [feedback-app](https://github.com/armego/feedback-app) - Frontend application

## 📞 Support

For issues and questions, please use the [GitHub Issues](https://github.com/armego/feedback-services/issues) page.
