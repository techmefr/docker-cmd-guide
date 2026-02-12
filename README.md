
# 🐳 Guide Complet des Commandes Docker / Complete Docker CLI Reference

Ce guide pratique est conçu pour accompagner les utilisateurs, du niveau débutant à avancé.
*This guide is designed for users ranging from beginners to advanced.*

---

## 📦 1. Installation & Service

*Gestion du daemon et vérification de l'état.*

| Commande / Command | Description (FR) | Description (EN) |
| --- | --- | --- |
| `yum install docker -y` | Installer Docker (CentOS/RHEL) | Install Docker (CentOS/RHEL) |
| `docker version` | Afficher la version de Docker | Show Docker version |
| `systemctl status docker` | Vérifier l'état du service | Check service status |
| `systemctl start docker` | Démarrer le service Docker | Start Docker service |

---

## 🖼️ 2. Images Docker / Docker Images

*Les modèles en lecture seule utilisés pour créer des conteneurs.*

| Commande / Command | Description (FR) | Description (EN) |
| --- | --- | --- |
| `docker images` | Lister les images locales | List local images |
| `docker pull <image>` | Télécharger une image depuis le Hub | Pull image from Docker Hub |
| `docker rmi <image>` | Supprimer une image | Remove an image |
| `docker build -t <nom> .` | Construire une image (via Dockerfile) | Build image from Dockerfile |
| `docker image inspect <nom>` | Détails techniques de l'image | Inspect image details |

---

## 📦 3. Conteneurs / Containers

*L'instance d'exécution d'une image.*

### ▶️ Lancement / Running

* `docker run <image>` : Exécuter un conteneur / *Run a container.*
* `docker run -it --name <nom> <image>` : Mode interactif / *Interactive mode.*
* `docker run -d --name <nom> <image>` : Mode arrière-plan (detached) / *Background mode.*
* `docker run -p 8081:80 <image>` : Mapping de port (Host:Container) / *Port mapping.*

### 📋 Gestion / Management

| Commande / Command | Description (FR) | Description (EN) |
| --- | --- | --- |
| `docker ps` | Liste des conteneurs actifs | List running containers |
| `docker ps -a` | Liste de tous les conteneurs | List all containers |
| `docker stop <nom>` | Arrêter un conteneur | Stop a container |
| `docker start <nom>` | Démarrer un conteneur arrêté | Start a stopped container |
| `docker rm <nom>` | Supprimer un conteneur | Remove a container |
| `docker container prune` | Supprimer les conteneurs inactifs | Remove all stopped containers |

### 🔍 Debug & Accès / Debug & Access

* `docker inspect <nom>` : Voir les détails (IP, config, etc.) / *View container details.*
* `docker logs <nom>` : Afficher les logs / *Fetch container logs.*
* `docker exec -it <nom> bash` : Ouvrir un terminal dans le conteneur / *Execute bash inside container.*
* `CTRL + P + Q` : Quitter sans arrêter le conteneur / *Exit without stopping.*

---

## 💾 4. Volumes & Stockage / Volumes & Storage

*Pour la persistance des données.*

* `docker volume create <nom>` : Créer un volume / *Create a volume.*
* `docker volume ls` : Lister les volumes / *List volumes.*
* `docker volume inspect <nom>` : Détails du volume / *Inspect volume.*
* **Montage (Mounting) :**
* `docker run -v volume_name:/data <image>` : Volume nommé / *Named volume.*
* `docker run -v $(pwd):/app <image>` : Bind mount (répertoire local) / *Local directory mount.*



---

## 🌐 5. Réseaux / Networks

*Gérer la communication entre les conteneurs.*

* `docker network ls` : Lister les réseaux / *List networks.*
* `docker network create <nom>` : Créer un réseau / *Create a network.*
* `docker network connect <réseau> <conteneur>` : Connecter un conteneur / *Connect container to network.*
* `docker network rm <nom>` : Supprimer un réseau / *Remove network.*

---

## 🧩 6. Docker Compose

*Outil pour définir et lancer des applications multi-conteneurs.*

| Commande / Command | Description (FR) | Description (EN) |
| --- | --- | --- |
| `docker-compose up -d` | Lancer les services en arrière-plan | Start services in background |
| `docker-compose down` | Arrêter et supprimer les ressources | Stop and remove resources |
| `docker-compose ps` | État des services | Check services status |
| `docker-compose logs -f` | Suivre les logs en temps réel | Follow logs in real-time |
| `docker-compose build` | Reconstruire les images | Rebuild images |

---

## ☁️ 7. Docker Hub & Registres / Registries

*Partagez vos images avec le monde.*

1. `docker login` : Se connecter / *Login.*
2. `docker tag <image_locale> <user>/<repo>:<tag>` : Taguer l'image / *Tag image.*
3. `docker push <user>/<repo>:<tag>` : Envoyer sur le Hub / *Push to Hub.*

---

## 🏗️ 8. Orchestration (Swarm & Stack)

*Pour les clusters de serveurs Docker.*

* `docker swarm init` : Initialiser un cluster / *Initialize swarm.*
* `docker node ls` : Lister les nœuds du cluster / *List nodes.*
* `docker service create --replicas 3 <image>` : Créer un service / *Create a service.*
* `docker stack deploy -c file.yml <nom>` : Déployer une stack / *Deploy a stack.*

---

## 💽 9. Système / System

*Nettoyage et diagnostic.*

* `docker system df` : Utilisation de l'espace disque / *Check disk usage.*
* `docker system prune -a` : **Nettoyage complet** (Supprime tout ce qui n'est pas utilisé) / *Full cleanup (unused data).*

