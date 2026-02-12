# 🐳 Guide Complet des Commandes Docker

### 🌍 Langues / Languages

[🇬🇧 English](./README.md) | [🇫🇷 Français](./README-FR.md) | [🇪🇸 Español](./README-ES.md) | [🇮🇹 Italiano](./README-IT.md) | [🇩🇪 Deutsch](./README-DE.md) | [🇵🇹 Português](./README-PT.md) | [🇨🇳 中文](./README-ZH.md)

---

## 🔧 1. Installation & Service

*Gestion du daemon et vérification de l'état.*

| Commande | Description |
| --- | --- |
| `sudo pacman -S docker` | Installer Docker (Arch Linux). |
| `sudo apt install docker.io` | Installer Docker (Debian/Ubuntu/Pop!_OS). |
| `sudo dnf install docker` | Installer Docker (Fedora/RHEL). |
| `docker version` | Afficher la version de Docker. |
| `systemctl status docker` | Vérifier l'état du service Docker. |
| `systemctl start docker` | Démarrer le service Docker. |

---

## 💿 2. Images Docker

*Les modèles en lecture seule utilisés pour créer des conteneurs.*

| Commande | Description |
| --- | --- |
| `docker images` | Lister toutes les images locales. |
| `docker pull <image>` | Télécharger une image depuis le Docker Hub. |
| `docker rmi <image>` | Supprimer une image locale. |
| `docker build -t <nom> .` | Construire une image (via Dockerfile). |
| `docker image inspect <nom>` | Détails techniques de l'image. |

---

## 📦 3. Conteneurs

*L'instance d'exécution d'une image.*

### ▶️ Lancement

* `docker run <image>` : Exécuter un conteneur.
* `docker run -it --name <nom> <image>` : Mode interactif avec terminal.
* `docker run -d --name <nom> <image>` : Mode arrière-plan (détaché).
* `docker run -p 8081:80 <image>` : Mapping de port (Hôte:Conteneur).

### 📋 Gestion

| Commande | Description |
| --- | --- |
| `docker ps` | Liste des conteneurs actifs. |
| `docker ps -a` | Liste de tous les conteneurs (même arrêtés). |
| `docker stop <nom>` | Arrêter un conteneur. |
| `docker start <nom>` | Démarrer un conteneur arrêté. |
| `docker rm <nom>` | Supprimer un conteneur. |
| `docker container prune` | Supprimer tous les conteneurs inactifs. |

### 🔍 Debug & Accès

* `docker inspect <nom>` : Voir les détails (IP, config, etc.).
* `docker logs <nom>` : Afficher les logs du conteneur.
* `docker exec -it <nom> bash` : Ouvrir un terminal dans le conteneur.
* `CTRL + P + Q` : Quitter sans arrêter le conteneur.

---

## 💾 4. Volumes & Stockage

*Pour la persistance des données.*

* `docker volume create <nom>` : Créer un volume.
* `docker volume ls` : Lister les volumes.
* `docker volume inspect <nom>` : Détails du volume.
* **Montage (Mounting) :**
* `docker run -v nom_volume:/data <image>` : Volume nommé.
* `docker run -v $(pwd):/app <image>` : Bind mount (répertoire local).



---

## 🌐 5. Réseaux (Networks)

*Gérer la communication entre les conteneurs.*

* `docker network ls` : Lister les réseaux.
* `docker network create <nom>` : Créer un réseau.
* `docker network connect <réseau> <conteneur>` : Connecter un conteneur au réseau.
* `docker network rm <nom>` : Supprimer un réseau.

---

## 🧩 6. Docker Compose

*Définir et lancer des applications multi-conteneurs.*

| Commande | Description |
| --- | --- |
| `docker-compose up -d` | Lancer les services en arrière-plan. |
| `docker-compose down` | Arrêter et supprimer les ressources. |
| `docker-compose ps` | État des services. |
| `docker-compose logs -f` | Suivre les logs en temps réel. |
| `docker-compose build` | Reconstruire les images. |

---

## ☁️ 7. Docker Hub & Registres

*Partagez vos images.*

1. `docker login` : Se connecter au registre.
2. `docker tag <image_locale> <user>/<repo>:<tag>` : Taguer l'image.
3. `docker push <user>/<repo>:<tag>` : Envoyer vers le Hub.

---

## 🏗️ 8. Orchestration (Swarm & Stack)

*Pour les clusters de serveurs.*

* `docker swarm init` : Initialiser un cluster.
* `docker node ls` : Lister les nœuds du cluster.
* `docker service create --replicas 3 <image>` : Créer un service répliqué.
* `docker stack deploy -c file.yml <nom>` : Déployer une stack complète.

---

## 🧹 9. Système

*Nettoyage et diagnostic.*

* `docker system df` : Utilisation de l'espace disque.
* `docker system prune -a` : **Nettoyage complet** (supprime tout ce qui est inutilisé).
