# 🐳 Docker Command Cheat Sheet

---

## 📦 1. Docker Installation & Info

```bash
docker --version              # Show Docker version
docker info                   # System-wide information
docker system df              # Show disk usage by Docker
```

---

## 🖼️ 2. Working with Docker Images

```bash
docker pull IMAGE             # Download image from Docker Hub
docker images                 # List all local images
docker rmi IMAGE_ID           # Remove image
docker build -t name:tag .    # Build image from Dockerfile
```

---

## 🚀 3. Working with Containers

```bash
docker run IMAGE                      # Run container from image
docker run -it IMAGE bash             # Run interactively
docker run -d -p 80:80 IMAGE          # Run detached and expose port
docker ps                             # List running containers
docker ps -a                          # List all containers
docker stop CONTAINER_ID              # Stop container
docker start CONTAINER_ID             # Start container
docker rm CONTAINER_ID                # Remove container
```

---

## 🗃️ 4. Volumes and Networks

```bash
docker volume create my-volume        # Create volume
docker volume ls                      # List volumes
docker network ls                     # List networks
docker network create my-net          # Create network
```

---

## 📈 5. Logs, Shell Access and Monitoring

```bash
docker logs CONTAINER_ID              # View logs
docker exec -it CONTAINER_ID bash     # Run bash inside container
docker top CONTAINER_ID               # Show running processes
docker stats                          # Live container resource usage
```

---

## 🛠️ 6. Dockerfile & Docker Compose

### 📄 Dockerfile (Basic Example)

```Dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get install -y nginx
CMD ["nginx", "-g", "daemon off;"]
```

### ⚙️ Docker Compose (Basic Commands)

```bash
docker-compose up                     # Start services
docker-compose down                   # Stop and remove services
docker-compose build                  # Build services
docker-compose ps                     # List running services
```

---

