# 🐳 Guía Completa de Comandos Docker

### 🌍 Idiomas / Languages

[🇬🇧 English](./README.md) | [🇫🇷 Français](./README-FR.md) | [🇪🇸 Español](./README-ES.md) | [🇮🇹 Italiano](./README-IT.md) | [🇩🇪 Deutsch](./README-DE.md) | [🇵🇹 Português](./README-PT.md) | [🇨🇳 中文](./README-ZH.md)

---

## 🔧 1. Instalación y Servicio

*Gestión del daemon y estado del sistema.*

| Comando | Descripción |
| --- | --- |
| `yum install docker -y` | Instalar Docker (CentOS/RHEL). |
| `docker version` | Mostrar la versión instalada de Docker. |
| `systemctl status docker` | Verificar el estado del servicio Docker. |
| `systemctl start docker` | Iniciar el servicio Docker. |
| `systemctl enable docker` | Habilitar Docker al arranque del sistema. |

---

## 💿 2. Imágenes Docker

*Plantillas de solo lectura utilizadas para crear contenedores.*

| Comando | Descripción |
| --- | --- |
| `docker images` | Listar todas las imágenes locales. |
| `docker pull <imagen>` | Descargar una imagen desde Docker Hub. |
| `docker rmi <imagen>` | Eliminar una imagen local. |
| `docker build -t <nombre> .` | Construir una imagen desde un Dockerfile. |
| `docker image inspect <nombre>` | Mostrar información detallada de la imagen. |
| `docker history <imagen>` | Mostrar el historial (capas) de una imagen. |

---

## 📦 3. Contenedores

*La instancia ejecutable de una imagen.*

### ▶️ Ejecución

* `docker run <imagen>` : Ejecutar un contenedor básico.
* `docker run -it --name <nombre> <imagen>` : Ejecutar en modo interactivo con terminal.
* `docker run -d --name <nombre> <imagen>` : Ejecutar en segundo plano (modo separado).
* `docker run -p 8081:80 <imagen>` : Mapeo de puertos (Host:Contenedor).
* `docker run --restart always <imagen>` : Reinicio automático del contenedor.

### 📋 Gestión

| Comando | Descripción |
| --- | --- |
| `docker ps` | Listar contenedores en ejecución. |
| `docker ps -a` | Listar todos los contenedores (incluidos los detenidos). |
| `docker stop <nombre>` | Detener un contenedor en ejecución. |
| `docker start <nombre>` | Iniciar un contenedor detenido. |
| `docker rm <nombre>` | Eliminar un contenedor. |
| `docker rename <antiguo> <nuevo>` | Renombrar un contenedor existente. |

### 🔍 Depuración y Monitoreo

* `docker stats` : **Flujo en vivo** del uso de recursos (CPU/RAM).
* `docker top <nombre>` : Mostrar los procesos en ejecución de un contenedor.
* `docker logs -f <nombre>` : Seguir los logs en tiempo real.
* `docker exec -it <nombre> bash` : Abrir una terminal dentro del contenedor.
* `docker inspect <nombre>` : Ver detalles técnicos (IP, configuración, etc.).

### 📂 Transferencia de Archivos

* `docker cp <ruta_host> <contenedor>:<ruta>` : Copiar archivo del Host al Contenedor.
* `docker cp <contenedor>:<ruta> <ruta_host>` : Copiar archivo del Contenedor al Host.

---

## 💾 4. Volúmenes y Almacenamiento

*Persistencia de datos entre reinicios de contenedores.*

* `docker volume create <nombre>` : Crear un volumen con nombre.
* `docker volume ls` : Listar todos los volúmenes.
* `docker volume rm <nombre>` : Eliminar un volumen específico.
* **Montaje:**
* `docker run -v nombre_volumen:/data <imagen>` : Usar un volumen con nombre.
* `docker run -v $(pwd):/app <imagen>` : Bind mount (directorio local actual).

---

## 🌐 5. Redes

*Gestionar la comunicación entre contenedores.*

* `docker network ls` : Listar redes.
* `docker network create <nombre>` : Crear una nueva red.
* `docker network connect <red> <contenedor>` : Conectar un contenedor a una red.
* `docker network disconnect <red> <contenedor>` : Desconectar un contenedor de una red.

---

## 🧩 6. Docker Compose

*Definir y ejecutar aplicaciones multi-contenedor.*

| Comando | Descripción |
| --- | --- |
| `docker-compose up -d` | Iniciar servicios en segundo plano. |
| `docker-compose down` | Detener y eliminar recursos (contenedores, redes). |
| `docker-compose ps` | Listar el estado de los servicios. |
| `docker-compose logs -f` | Seguir los logs de todos los servicios. |
| `docker-compose build --no-cache` | Reconstruir imágenes desde cero. |

---

## ☁️ 7. Docker Hub y Registros

*Compartir y almacenar tus imágenes.*

1. `docker login` : Iniciar sesión en el registro.
2. `docker tag <imagen_local> <usuario>/<repo>:<tag>` : Preparar imagen para subir.
3. `docker push <usuario>/<repo>:<tag>` : Subir imagen al Hub.

---

## 🏗️ 8. Orquestación (Swarm y Stack)

*Para clusters de servidores y despliegues en producción.*

* `docker swarm init` : Inicializar un cluster swarm.
* `docker node ls` : Listar nodos del cluster.
* `docker service create --name <nombre> --replicas 3 <imagen>` : Crear un servicio.
* `docker service scale <nombre>=5` : Escalar un servicio a 5 réplicas.
* `docker stack deploy -c docker-compose.yml <nombre_stack>` : Desplegar una stack.

---

## 🧹 9. Sistema y Mantenimiento

*Limpieza y diagnóstico.*

* `docker system df` : Ver uso de disco de Docker.
* `docker system prune` : Eliminar datos no utilizados (contenedores detenidos, redes sin uso).
* `docker system prune -a` : **Limpieza profunda** (elimina todas las imágenes y datos sin uso).
* `docker image prune` : Eliminar solo imágenes huérfanas (sin etiqueta).
