# 🐳 Complete Docker CLI Reference Guide

### 🌍 Languages

[ 🇬🇧 English ](https://www.google.com/search?q=%23-complete-docker-cli-reference-guide) | [ 🇫🇷 Français ](https://www.google.com/search?q=./README-FR.md) | [ 🇪🇸 Español ](https://www.google.com/search?q=./README-ES.md) | [ 🇮🇹 Italiano ](https://www.google.com/search?q=./README-IT.md) | [ 🇩🇪 Deutsch ](https://www.google.com/search?q=./README-DE.md) | [ 🇵🇹 Português ](https://www.google.com/search?q=./README-PT.md) | [ 🇨🇳 中文 ](https://www.google.com/search?q=./README-ZH.md)

---

## 📦 1. Installation & Service

*Daemon management and system status.*

| Command | Description |
| --- | --- |
| `yum install docker -y` | Install Docker (CentOS/RHEL). |
| `docker version` | Show installed Docker version. |
| `systemctl status docker` | Check Docker service status. |
| `systemctl start docker` | Start Docker service. |

---

## 🖼️ 2. Docker Images

*Read-only templates used to create containers.*

| Command | Description |
| --- | --- |
| `docker images` | List all local images. |
| `docker pull <image>` | Download an image from Docker Hub. |
| `docker rmi <image>` | Remove a local image. |
| `docker build -t <name> .` | Build an image from a Dockerfile. |
| `docker image inspect <name>` | Display detailed image information. |

---

## 📦 3. Containers

*The runnable instance of an image.*

### ▶️ Running

* `docker run <image>` : Run a basic container.
* `docker run -it --name <name> <image>` : Run in interactive mode with a terminal.
* `docker run -d --name <name> <image>` : Run in background (detached mode).
* `docker run -p 8081:80 <image>` : Port mapping (Host:Container).

### 📋 Management

| Command | Description |
| --- | --- |
| `docker ps` | List running containers. |
| `docker ps -a` | List all containers (including stopped ones). |
| `docker stop <name>` | Stop a running container. |
| `docker start <name>` | Start a stopped container. |
| `docker rm <name>` | Delete a container. |
| `docker container prune` | Remove all stopped containers. |

### 🔍 Debug & Access

* `docker inspect <name>` : View technical details (IP, config, etc.).
* `docker logs <name>` : Show container logs.
* `docker exec -it <name> bash` : Open a terminal inside the container.
* `CTRL + P + Q` : Exit container without stopping it.

---

## 💾 4. Volumes & Storage

*Data persistence across container restarts.*

* `docker volume create <name>` : Create a named volume.
* `docker volume ls` : List all volumes.
* `docker volume inspect <name>` : Inspect volume details.
* **Mounting:**
* `docker run -v volume_name:/data <image>` : Use a named volume.
* `docker run -v $(pwd):/app <image>` : Bind mount (current local directory).



---

## 🌐 5. Networks

*Manage communication between containers.*

* `docker network ls` : List networks.
* `docker network create <name>` : Create a new network.
* `docker network connect <network> <container>` : Connect a container to a network.
* `docker network rm <name>` : Remove a network.

---

## 🧩 6. Docker Compose

*Define and run multi-container applications.*

| Command | Description |
| --- | --- |
| `docker-compose up -d` | Start services in the background. |
| `docker-compose down` | Stop and remove resources. |
| `docker-compose ps` | List status of services. |
| `docker-compose logs -f` | Follow logs in real-time. |
| `docker-compose build` | Rebuild images defined in compose file. |

---

## ☁️ 7. Docker Hub & Registries

*Share your images.*

1. `docker login` : Login to the registry.
2. `docker tag <local_image> <user>/<repo>:<tag>` : Tag image for upload.
3. `docker push <user>/<repo>:<tag>` : Push image to Hub.

---

## 🏗️ 8. Orchestration (Swarm & Stack)

*For server clusters.*

* `docker swarm init` : Initialize a swarm cluster.
* `docker node ls` : List nodes in the cluster.
* `docker service create --replicas 3 <image>` : Create a replicated service.
* `docker stack deploy -c file.yml <name>` : Deploy a full stack.

---

## 💽 9. System

*Cleanup and diagnostics.*

* `docker system df` : View Docker disk usage.
* `docker system prune -a` : **Full cleanup** (removes all unused data).
