# 🐳 Guida Completa ai Comandi Docker

### 🌍 Lingue / Languages

[🇬🇧 English](./README.md) | [🇫🇷 Français](./README-FR.md) | [🇪🇸 Español](./README-ES.md) | [🇮🇹 Italiano](./README-IT.md) | [🇩🇪 Deutsch](./README-DE.md) | [🇵🇹 Português](./README-PT.md) | [🇨🇳 中文](./README-ZH.md)

---

## 🔧 1. Installazione e Servizio

*Gestione del daemon e stato del sistema.*

| Comando | Descrizione |
| --- | --- |
| `sudo pacman -S docker` | Installare Docker (Arch Linux). |
| `sudo apt install docker.io` | Installare Docker (Debian/Ubuntu/Pop!_OS). |
| `sudo dnf install docker` | Installare Docker (Fedora/RHEL). |
| `docker version` | Mostrare la versione installata di Docker. |
| `systemctl status docker` | Verificare lo stato del servizio Docker. |
| `systemctl start docker` | Avviare il servizio Docker. |
| `systemctl enable docker` | Abilitare Docker all'avvio del sistema. |

---

## 💿 2. Immagini Docker

*Modelli in sola lettura utilizzati per creare contenitori.*

| Comando | Descrizione |
| --- | --- |
| `docker images` | Elencare tutte le immagini locali. |
| `docker pull <immagine>` | Scaricare un'immagine da Docker Hub. |
| `docker rmi <immagine>` | Rimuovere un'immagine locale. |
| `docker build -t <nome> .` | Creare un'immagine da un Dockerfile. |
| `docker image inspect <nome>` | Mostrare informazioni dettagliate sull'immagine. |
| `docker history <immagine>` | Mostrare la cronologia (livelli) di un'immagine. |

---

## 📦 3. Contenitori

*L'istanza eseguibile di un'immagine.*

### ▶️ Esecuzione

* `docker run <immagine>` : Eseguire un contenitore di base.
* `docker run -it --name <nome> <immagine>` : Eseguire in modalità interattiva con terminale.
* `docker run -d --name <nome> <immagine>` : Eseguire in background (modalità separata).
* `docker run -p 8081:80 <immagine>` : Mappatura delle porte (Host:Contenitore).
* `docker run --restart always <immagine>` : Riavvio automatico del contenitore.

### 📋 Gestione

| Comando | Descrizione |
| --- | --- |
| `docker ps` | Elencare i contenitori in esecuzione. |
| `docker ps -a` | Elencare tutti i contenitori (compresi quelli arrestati). |
| `docker stop <nome>` | Arrestare un contenitore in esecuzione. |
| `docker start <nome>` | Avviare un contenitore arrestato. |
| `docker rm <nome>` | Eliminare un contenitore. |
| `docker rename <vecchio> <nuovo>` | Rinominare un contenitore esistente. |

### 🔍 Debug e Monitoraggio

* `docker stats` : **Flusso in tempo reale** dell'utilizzo delle risorse (CPU/RAM).
* `docker top <nome>` : Mostrare i processi in esecuzione di un contenitore.
* `docker logs -f <nome>` : Seguire i log in tempo reale.
* `docker exec -it <nome> bash` : Aprire un terminale all'interno del contenitore.
* `docker inspect <nome>` : Visualizzare dettagli tecnici (IP, configurazione, ecc.).

### 📂 Trasferimento File

* `docker cp <percorso_host> <contenitore>:<percorso>` : Copiare file dall'Host al Contenitore.
* `docker cp <contenitore>:<percorso> <percorso_host>` : Copiare file dal Contenitore all'Host.

---

## 💾 4. Volumi e Archiviazione

*Persistenza dei dati tra i riavvii dei contenitori.*

* `docker volume create <nome>` : Creare un volume con nome.
* `docker volume ls` : Elencare tutti i volumi.
* `docker volume rm <nome>` : Eliminare un volume specifico.
* **Montaggio:**
* `docker run -v nome_volume:/data <immagine>` : Usare un volume con nome.
* `docker run -v $(pwd):/app <immagine>` : Bind mount (directory locale corrente).

---

## 🌐 5. Reti

*Gestire la comunicazione tra contenitori.*

* `docker network ls` : Elencare le reti.
* `docker network create <nome>` : Creare una nuova rete.
* `docker network connect <rete> <contenitore>` : Collegare un contenitore a una rete.
* `docker network disconnect <rete> <contenitore>` : Scollegare un contenitore da una rete.

---

## 🧩 6. Docker Compose

*Definire e eseguire applicazioni multi-contenitore.*

| Comando | Descrizione |
| --- | --- |
| `docker-compose up -d` | Avviare i servizi in background. |
| `docker-compose down` | Arrestare e rimuovere le risorse (contenitori, reti). |
| `docker-compose ps` | Elencare lo stato dei servizi. |
| `docker-compose logs -f` | Seguire i log di tutti i servizi. |
| `docker-compose build --no-cache` | Ricostruire le immagini da zero. |

---

## ☁️ 7. Docker Hub e Registri

*Condividere e archiviare le tue immagini.*

1. `docker login` : Accedere al registro.
2. `docker tag <immagine_locale> <utente>/<repo>:<tag>` : Preparare l'immagine per il caricamento.
3. `docker push <utente>/<repo>:<tag>` : Caricare l'immagine sul Hub.

---

## 🏗️ 8. Orchestrazione (Swarm e Stack)

*Per cluster di server e distribuzioni in produzione.*

* `docker swarm init` : Inizializzare un cluster swarm.
* `docker node ls` : Elencare i nodi del cluster.
* `docker service create --name <nome> --replicas 3 <immagine>` : Creare un servizio.
* `docker service scale <nome>=5` : Scalare un servizio a 5 repliche.
* `docker stack deploy -c docker-compose.yml <nome_stack>` : Distribuire uno stack.

---

## 🧹 9. Sistema e Manutenzione

*Pulizia e diagnostica.*

* `docker system df` : Visualizzare l'utilizzo del disco di Docker.
* `docker system prune` : Rimuovere dati inutilizzati (contenitori arrestati, reti non utilizzate).
* `docker system prune -a` : **Pulizia profonda** (rimuove tutte le immagini e i dati inutilizzati).
* `docker image prune` : Rimuovere solo le immagini orfane (senza tag).
