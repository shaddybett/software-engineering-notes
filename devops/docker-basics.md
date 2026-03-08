# Docker Basics

Docker packages applications and dependencies into isolated containers, ensuring consistent environments across development, testing, and production.

## Key Concepts

- **Image**: Read-only template with application code and dependencies
- **Container**: Running instance of an image
- **Dockerfile**: Script defining how to build an image
- **Registry**: Storage for images (Docker Hub, ECR)

## Essential Commands

```bash
# Build image from Dockerfile
docker build -t myapp:1.0 .

# Run container
docker run -d -p 3000:3000 --name myapp myapp:1.0

# List running containers
docker ps

# View logs
docker logs myapp

# Stop and remove container
docker stop myapp && docker rm myapp

# Remove image
docker rmi myapp:1.0
```

## Dockerfile Example

```dockerfile
# Node.js application
FROM node:20-alpine

WORKDIR /app

# Copy package files first (layer caching)
COPY package*.json ./
RUN npm ci --only=production

# Copy application code
COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

## Docker Compose

Orchestrate multi-container applications:

```yaml
# docker-compose.yml
version: "3.8"
services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - DATABASE_URL=postgres://db:5432/mydb
    depends_on:
      - db
  db:
    image: postgres:15
    environment:
      - POSTGRES_DB=mydb
```

## Best Practices

- Use specific image tags, not `latest`
- Minimize layers and image size (alpine base)
- Don't run as root in containers
- Use `.dockerignore` to exclude files
- Leverage build cache with proper layer ordering
