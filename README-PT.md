# 🐳 Guia Completo de Comandos Docker

### 🌍 Idiomas / Languages

[🇬🇧 English](./README.md) | [🇫🇷 Français](./README-FR.md) | [🇪🇸 Español](./README-ES.md) | [🇮🇹 Italiano](./README-IT.md) | [🇩🇪 Deutsch](./README-DE.md) | [🇵🇹 Português](./README-PT.md) | [🇨🇳 中文](./README-ZH.md)

---

## 🔧 1. Instalação e Serviço

*Gestão do daemon e estado do sistema.*

| Comando | Descrição |
| --- | --- |
| `sudo pacman -S docker` | Instalar Docker (Arch Linux). |
| `sudo apt install docker.io` | Instalar Docker (Debian/Ubuntu/Pop!_OS). |
| `sudo dnf install docker` | Instalar Docker (Fedora/RHEL). |
| `docker version` | Mostrar a versão instalada do Docker. |
| `systemctl status docker` | Verificar o estado do serviço Docker. |
| `systemctl start docker` | Iniciar o serviço Docker. |
| `systemctl enable docker` | Ativar Docker no arranque do sistema. |

---

## 💿 2. Imagens Docker

*Modelos somente leitura utilizados para criar contentores.*

| Comando | Descrição |
| --- | --- |
| `docker images` | Listar todas as imagens locais. |
| `docker pull <imagem>` | Descarregar uma imagem do Docker Hub. |
| `docker rmi <imagem>` | Remover uma imagem local. |
| `docker build -t <nome> .` | Construir uma imagem a partir de um Dockerfile. |
| `docker image inspect <nome>` | Mostrar informações detalhadas da imagem. |
| `docker history <imagem>` | Mostrar o histórico (camadas) de uma imagem. |

---

## 📦 3. Contentores

*A instância executável de uma imagem.*

### ▶️ Execução

* `docker run <imagem>` : Executar um contentor básico.
* `docker run -it --name <nome> <imagem>` : Executar em modo interativo com terminal.
* `docker run -d --name <nome> <imagem>` : Executar em segundo plano (modo separado).
* `docker run -p 8081:80 <imagem>` : Mapeamento de portas (Host:Contentor).
* `docker run --restart always <imagem>` : Reinício automático do contentor.

### 📋 Gestão

| Comando | Descrição |
| --- | --- |
| `docker ps` | Listar contentores em execução. |
| `docker ps -a` | Listar todos os contentores (incluindo os parados). |
| `docker stop <nome>` | Parar um contentor em execução. |
| `docker start <nome>` | Iniciar um contentor parado. |
| `docker rm <nome>` | Eliminar um contentor. |
| `docker rename <antigo> <novo>` | Renomear um contentor existente. |

### 🔍 Debug e Monitorização

* `docker stats` : **Fluxo em tempo real** da utilização de recursos (CPU/RAM).
* `docker top <nome>` : Mostrar os processos em execução de um contentor.
* `docker logs -f <nome>` : Seguir os logs em tempo real.
* `docker exec -it <nome> bash` : Abrir um terminal dentro do contentor.
* `docker inspect <nome>` : Ver detalhes técnicos (IP, configuração, etc.).

### 📂 Transferência de Ficheiros

* `docker cp <caminho_host> <contentor>:<caminho>` : Copiar ficheiro do Host para o Contentor.
* `docker cp <contentor>:<caminho> <caminho_host>` : Copiar ficheiro do Contentor para o Host.

---

## 💾 4. Volumes e Armazenamento

*Persistência de dados entre reinícios de contentores.*

* `docker volume create <nome>` : Criar um volume com nome.
* `docker volume ls` : Listar todos os volumes.
* `docker volume rm <nome>` : Eliminar um volume específico.
* **Montagem:**
* `docker run -v nome_volume:/data <imagem>` : Usar um volume com nome.
* `docker run -v $(pwd):/app <imagem>` : Bind mount (diretório local atual).

---

## 🌐 5. Redes

*Gerir a comunicação entre contentores.*

* `docker network ls` : Listar redes.
* `docker network create <nome>` : Criar uma nova rede.
* `docker network connect <rede> <contentor>` : Ligar um contentor a uma rede.
* `docker network disconnect <rede> <contentor>` : Desligar um contentor de uma rede.

---

## 🧩 6. Docker Compose

*Definir e executar aplicações multi-contentor.*

| Comando | Descrição |
| --- | --- |
| `docker-compose up -d` | Iniciar serviços em segundo plano. |
| `docker-compose down` | Parar e remover recursos (contentores, redes). |
| `docker-compose ps` | Listar o estado dos serviços. |
| `docker-compose logs -f` | Seguir os logs de todos os serviços. |
| `docker-compose build --no-cache` | Reconstruir imagens de raiz. |

---

## ☁️ 7. Docker Hub e Registos

*Partilhar e armazenar as tuas imagens.*

1. `docker login` : Iniciar sessão no registo.
2. `docker tag <imagem_local> <utilizador>/<repo>:<tag>` : Preparar imagem para envio.
3. `docker push <utilizador>/<repo>:<tag>` : Enviar imagem para o Hub.

---

## 🏗️ 8. Orquestração (Swarm e Stack)

*Para clusters de servidores e implementações em produção.*

* `docker swarm init` : Inicializar um cluster swarm.
* `docker node ls` : Listar nós do cluster.
* `docker service create --name <nome> --replicas 3 <imagem>` : Criar um serviço.
* `docker service scale <nome>=5` : Escalar um serviço para 5 réplicas.
* `docker stack deploy -c docker-compose.yml <nome_stack>` : Implementar uma stack.

---

## 🧹 9. Sistema e Manutenção

*Limpeza e diagnóstico.*

* `docker system df` : Ver utilização de disco do Docker.
* `docker system prune` : Remover dados não utilizados (contentores parados, redes sem uso).
* `docker system prune -a` : **Limpeza profunda** (remove todas as imagens e dados não utilizados).
* `docker image prune` : Remover apenas imagens órfãs (sem tag).
