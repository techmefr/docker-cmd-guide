# 🐳 Vollständige Docker-Befehlsreferenz

### 🌍 Sprachen / Languages

[🇬🇧 English](./README.md) | [🇫🇷 Français](./README-FR.md) | [🇪🇸 Español](./README-ES.md) | [🇮🇹 Italiano](./README-IT.md) | [🇩🇪 Deutsch](./README-DE.md) | [🇵🇹 Português](./README-PT.md) | [🇨🇳 中文](./README-ZH.md)

---

## 🔧 1. Installation und Service

*Daemon-Verwaltung und Systemstatus.*

| Befehl | Beschreibung |
| --- | --- |
| `sudo pacman -S docker` | Docker installieren (Arch Linux). |
| `sudo apt install docker.io` | Docker installieren (Debian/Ubuntu/Pop!_OS). |
| `sudo dnf install docker` | Docker installieren (Fedora/RHEL). |
| `docker version` | Installierte Docker-Version anzeigen. |
| `systemctl status docker` | Docker-Dienststatus prüfen. |
| `systemctl start docker` | Docker-Dienst starten. |
| `systemctl enable docker` | Docker beim Systemstart aktivieren. |

---

## 💿 2. Docker-Images

*Schreibgeschützte Vorlagen zur Erstellung von Containern.*

| Befehl | Beschreibung |
| --- | --- |
| `docker images` | Alle lokalen Images auflisten. |
| `docker pull <image>` | Ein Image von Docker Hub herunterladen. |
| `docker rmi <image>` | Ein lokales Image entfernen. |
| `docker build -t <name> .` | Ein Image aus einem Dockerfile erstellen. |
| `docker image inspect <name>` | Detaillierte Image-Informationen anzeigen. |
| `docker history <image>` | Verlauf (Schichten) eines Images anzeigen. |

---

## 📦 3. Container

*Die ausführbare Instanz eines Images.*

### ▶️ Ausführung

* `docker run <image>` : Einen einfachen Container ausführen.
* `docker run -it --name <name> <image>` : Im interaktiven Modus mit Terminal ausführen.
* `docker run -d --name <name> <image>` : Im Hintergrund ausführen (getrennter Modus).
* `docker run -p 8081:80 <image>` : Port-Mapping (Host:Container).
* `docker run --restart always <image>` : Automatischen Neustart des Containers sicherstellen.

### 📋 Verwaltung

| Befehl | Beschreibung |
| --- | --- |
| `docker ps` | Laufende Container auflisten. |
| `docker ps -a` | Alle Container auflisten (einschließlich gestoppter). |
| `docker stop <name>` | Einen laufenden Container stoppen. |
| `docker start <name>` | Einen gestoppten Container starten. |
| `docker rm <name>` | Einen Container löschen. |
| `docker rename <alt> <neu>` | Einen bestehenden Container umbenennen. |

### 🔍 Debug und Überwachung

* `docker stats` : **Live-Stream** der Ressourcennutzung (CPU/RAM).
* `docker top <name>` : Laufende Prozesse eines Containers anzeigen.
* `docker logs -f <name>` : Logs in Echtzeit verfolgen.
* `docker exec -it <name> bash` : Ein Terminal im Container öffnen.
* `docker inspect <name>` : Technische Details anzeigen (IP, Konfiguration, usw.).

### 📂 Dateiübertragung

* `docker cp <host_pfad> <container>:<pfad>` : Datei vom Host zum Container kopieren.
* `docker cp <container>:<pfad> <host_pfad>` : Datei vom Container zum Host kopieren.

---

## 💾 4. Volumes und Speicher

*Datenpersistenz über Container-Neustarts hinweg.*

* `docker volume create <name>` : Ein benanntes Volume erstellen.
* `docker volume ls` : Alle Volumes auflisten.
* `docker volume rm <name>` : Ein bestimmtes Volume löschen.
* **Einbindung:**
* `docker run -v volume_name:/data <image>` : Ein benanntes Volume verwenden.
* `docker run -v $(pwd):/app <image>` : Bind Mount (aktuelles lokales Verzeichnis).

---

## 🌐 5. Netzwerke

*Kommunikation zwischen Containern verwalten.*

* `docker network ls` : Netzwerke auflisten.
* `docker network create <name>` : Ein neues Netzwerk erstellen.
* `docker network connect <netzwerk> <container>` : Einen Container mit einem Netzwerk verbinden.
* `docker network disconnect <netzwerk> <container>` : Einen Container vom Netzwerk trennen.

---

## 🧩 6. Docker Compose

*Multi-Container-Anwendungen definieren und ausführen.*

| Befehl | Beschreibung |
| --- | --- |
| `docker-compose up -d` | Dienste im Hintergrund starten. |
| `docker-compose down` | Ressourcen stoppen und entfernen (Container, Netzwerke). |
| `docker-compose ps` | Status der Dienste auflisten. |
| `docker-compose logs -f` | Alle Dienst-Logs verfolgen. |
| `docker-compose build --no-cache` | Images von Grund auf neu erstellen. |

---

## ☁️ 7. Docker Hub und Registries

*Deine Images teilen und speichern.*

1. `docker login` : Am Registry anmelden.
2. `docker tag <lokales_image> <benutzer>/<repo>:<tag>` : Image für den Upload vorbereiten.
3. `docker push <benutzer>/<repo>:<tag>` : Image zum Hub hochladen.

---

## 🏗️ 8. Orchestrierung (Swarm und Stack)

*Für Server-Cluster und Produktions-Deployments.*

* `docker swarm init` : Einen Swarm-Cluster initialisieren.
* `docker node ls` : Knoten im Cluster auflisten.
* `docker service create --name <name> --replicas 3 <image>` : Einen Dienst erstellen.
* `docker service scale <name>=5` : Einen Dienst auf 5 Replikate skalieren.
* `docker stack deploy -c docker-compose.yml <stack_name>` : Einen Stack deployen.

---

## 🧹 9. System und Wartung

*Bereinigung und Diagnose.*

* `docker system df` : Docker-Speichernutzung anzeigen.
* `docker system prune` : Ungenutzte Daten entfernen (gestoppte Container, ungenutzte Netzwerke).
* `docker system prune -a` : **Tiefenreinigung** (entfernt alle ungenutzten Images und Daten).
* `docker image prune` : Nur verwaiste Images entfernen (ohne Tag).
