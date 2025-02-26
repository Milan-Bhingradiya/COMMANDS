# Docker Complete Guide

## Installing Docker
Download and install Docker from the official website: [https://www.docker.com/get-started](https://www.docker.com/get-started)

## Verify Docker Installation
```sh
docker --version  # Check installed Docker version
docker info  # Get system-wide Docker information
```

## Working with Docker Images
### Pull an Image from Docker Hub
```sh
docker pull ubuntu  # Pull Ubuntu image
docker pull node  # Pull Node.js image
```

### List Available Images
```sh
docker images
```

### Remove an Image
```sh
docker rmi <image-id>
```

## Working with Docker Containers
### Run a Container
```sh
docker run -it ubuntu  # Run Ubuntu interactively
docker run -d -p 8080:80 nginx  # Run Nginx in detached mode with port mapping
```

### List Running Containers
```sh
docker ps  # List active containers
docker ps -a  # List all containers (including stopped ones)
```

### Stop and Remove Containers
```sh
docker stop <container-id>
docker rm <container-id>
```

### Start and Restart Containers
```sh
docker start <container-id>
docker restart <container-id>
```

### Execute Commands in Running Containers
```sh
docker exec -it <container-id> bash  # Open a shell inside the container
docker logs <container-id>  # View container logs
```

## Docker Volumes (Persistent Data Storage)
```sh
docker volume create myvolume  # Create a volume
docker run -v myvolume:/data ubuntu  # Attach volume to a container
docker volume ls  # List volumes
```

## Docker Networking
### List Networks
```sh
docker network ls
```

### Create a Network
```sh
docker network create mynetwork
```

### Connect a Container to a Network
```sh
docker network connect mynetwork <container-id>
```

## Docker Compose (Multi-Container Applications)
### Install Docker Compose
```sh
sudo apt install docker-compose  # Linux
```

### Example `docker-compose.yml`
```yaml
version: '3'
services:
  app:
    image: node
    ports:
      - "3000:3000"
  db:
    image: postgres
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
```

### Start Services
```sh
docker-compose up -d  # Start services in detached mode
```

### Stop Services
```sh
docker-compose down  # Stop and remove containers
```

## Building Custom Docker Images
### Create a `Dockerfile`
```dockerfile
FROM node:16
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]
```

### Build and Run the Image
```sh
docker build -t myapp .
docker run -p 3000:3000 myapp
```

## Docker Security Best Practices
- Always pull trusted images.
- Use minimal base images (e.g., `alpine`).
- Remove unused images and containers to free up space.

## Clean Up Docker System
```sh
docker system prune  # Remove unused images, containers, and networks
```

This guide covers essential Docker commands and workflows for container management.

