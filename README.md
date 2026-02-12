# 🐳 Complete Docker CLI Reference Guide

### 🌍 Languages

[🇬🇧 English](./README.md) | [🇫🇷 Français](./README-FR.md) | [🇪🇸 Español](./README-ES.md) | [🇮🇹 Italiano](./README-IT.md) | [🇩🇪 Deutsch](./README-DE.md) | [🇵🇹 Português](./README-PT.md) | [🇨🇳 中文](./README-ZH.md)

---

## 🔧 1. Installation & Service

*Daemon management and system status.*

| Command | Description |
| --- | --- |
| `yum install docker -y` | Install Docker (CentOS/RHEL). |
| `docker version` | Show installed Docker version. |
| `systemctl status docker` | Check Docker service status. |
| `systemctl start docker` | Start Docker service. |
| `systemctl enable docker` | Enable Docker to start on boot. |

---

## 💿 2. Docker Images

*Read-only templates used to create containers.*

| Command | Description |
| --- | --- |
| `docker images` | List all local images. |
| `docker pull <image>` | Download an image from Docker Hub. |
| `docker rmi <image>` | Remove a local image. |
| `docker build -t <name> .` | Build an image from a Dockerfile. |
| `docker image inspect <name>` | Display detailed image information. |
| `docker history <image>` | Show the history (layers) of an image. |

---

## 📦 3. Containers

*The runnable instance of an image.*

### ▶️ Running

* `docker run <image>` : Run a basic container.
* `docker run -it --name <name> <image>` : Run in interactive mode with a terminal.
* `docker run -d --name <name> <image>` : Run in background (detached mode).
* `docker run -p 8081:80 <image>` : Port mapping (Host:Container).
* `docker run --restart always <image>` : Ensure container restarts automatically.

### 📋 Management

| Command | Description |
| --- | --- |
| `docker ps` | List running containers. |
| `docker ps -a` | List all containers (including stopped ones). |
| `docker stop <name>` | Stop a running container. |
| `docker start <name>` | Start a stopped container. |
| `docker rm <name>` | Delete a container. |
| `docker rename <old> <new>` | Rename an existing container. |

### 🔍 Debug & Monitoring

* `docker stats` : **Live stream** of container(s) resource usage (CPU/RAM).
* `docker top <name>` : Display the running processes of a container.
* `docker logs -f <name>` : Follow logs in real-time.
* `docker exec -it <name> bash` : Open a terminal inside the container.
* `docker inspect <name>` : View technical details (IP, config, etc.).

### 📂 File Transfer

* `docker cp <host_path> <container>:<path>` : Copy file from Host to Container.
* `docker cp <container>:<path> <host_path>` : Copy file from Container to Host.

---

## 💾 4. Volumes & Storage

*Data persistence across container restarts.*

* `docker volume create <name>` : Create a named volume.
* `docker volume ls` : List all volumes.
* `docker volume rm <name>` : Delete a specific volume.
* **Mounting:**
* `docker run -v volume_name:/data <image>` : Use a named volume.
* `docker run -v $(pwd):/app <image>` : Bind mount (current local directory).



---

## 🌐 5. Networks

*Manage communication between containers.*

* `docker network ls` : List networks.
* `docker network create <name>` : Create a new network.
* `docker network connect <network> <container>` : Connect a container to a network.
* `docker network disconnect <network> <container>` : Remove container from network.

---

## 🧩 6. Docker Compose

*Define and run multi-container applications.*

| Command | Description |
| --- | --- |
| `docker-compose up -d` | Start services in the background. |
| `docker-compose down` | Stop and remove resources (containers, networks). |
| `docker-compose ps` | List status of services. |
| `docker-compose logs -f` | Follow all service logs. |
| `docker-compose build --no-cache` | Rebuild images from scratch. |

---

## ☁️ 7. Docker Hub & Registries

*Share and store your images.*

1. `docker login` : Login to the registry.
2. `docker tag <local_image> <user>/<repo>:<tag>` : Prepare image for upload.
3. `docker push <user>/<repo>:<tag>` : Push image to Hub.

---

## 🏗️ 8. Orchestration (Swarm & Stack)

*For server clusters and production deployments.*

* `docker swarm init` : Initialize a swarm cluster.
* `docker node ls` : List nodes in the cluster.
* `docker service create --name <name> --replicas 3 <image>` : Create a service.
* `docker service scale <name>=5` : Scale a service to 5 replicas.
* `docker stack deploy -c docker-compose.yml <stack_name>` : Deploy a stack.

---

## 🧹 9. System & Maintenance

*Cleanup and diagnostics.*

* `docker system df` : View Docker disk usage.
* `docker system prune` : Remove unused data (stopped containers, unused networks).
* `docker system prune -a` : **Deep Cleanup** (removes all unused images and data).
* `docker image prune` : Remove only dangling images (untagged).
