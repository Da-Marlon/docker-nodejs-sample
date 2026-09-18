# ToDo-Applikation

## Projektbeschreibung

Dieses Projekt ist eine ToDo-Applikation mit Node.js.
Im der Abschlussaufgabe wird die Anwendung lokal eingerichtet, mit Git und GitHub versioniert und danach mit Docker containerisiert.

## Voraussetzungen

Für die lokale Ausführung werden diese Programme benötigt:

1. Git
2. Node.js
3. npm
4. Docker Desktop
5. Visual Studio Code oder eine andere Entwicklungsumgebung

## Repository klonen

Das Repository wird zuerst von GitHub auf den lokalen Computer geklont:

```bash
git clone DEINE-REPOSITORY-URL
```

Danach in das Projektverzeichnis wechseln:

```bash
cd docker-nodejs-sample
```

## Pakete installieren

Die benötigten Node.js-Pakete werden mit npm installiert:

```bash
npm install
```

Die benötigten Abhängigkeiten sind in der Datei `package.json` definiert.

## Anwendung lokal starten

Die Anwendung wird mit diesem Befehl gestartet:

```bash
npm run dev
```

Nach erfolgreichem Start erscheint im Terminal:

```text
Listening on port 3000
```

Die Anwendung ist danach im Browser erreichbar unter:

```text
http://localhost:3000
```

## Docker-Image erstellen

Vor dem Erstellen des Docker-Images muss Docker Desktop gestartet sein.

Das Docker-Image wird mit diesem Befehl erstellt:

docker build -t todo-app .

Dabei bedeutet:

docker build erstellt ein neues Docker-Image.
-t todo-app gibt dem Image den Namen todo-app.
. verwendet das aktuelle Verzeichnis als Build-Kontext.

Die vorhandenen Docker-Images können mit folgendem Befehl angezeigt werden:

docker image ls

## Anwendung mit Docker starten

Mit dem erstellten Image kann ein Container gestartet werden:

docker run --name todo-container -p 3000:3000 todo-app

Die Portangabe

3000:3000

bedeutet, dass Port 3000 des Computers mit Port 3000 des Containers verbunden wird.

Die Anwendung ist danach wieder unter dieser Adresse erreichbar:

<http://localhost:3000>

Ein bereits vorhandener und gestoppter Container kann mit dem Befehl erneut gestartet werden:

docker start todo-container

Laufende Container können angezeigt werden mit:

docker ps

## Anwendung mit Docker Compose starten

Die Datei compose.yaml enthält die Konfiguration für den Docker-Container.

Die Anwendung kann mit dem Befehl gestartet und bei Bedarf neu gebaut werden:

docker compose up --build

Für einen Start im Hintergrund verwendet man:

docker compose up -d

Der aktuelle Status kann angezeigt werden mit:

docker compose ps

Wenn sich der Quellcode geändert hat und die Änderung noch nicht im Container sichtbar ist, muss das Docker-Image neu erstellt werden:

docker compose up -d --build

## Anwendung stoppen

Ein einzelner Docker-Container kann mit diesem Befehl gestoppt werden:

docker stop todo-container

Der Container kann danach entfernt werden mit:

docker rm todo-container

Eine mit Docker Compose gestartete Umgebung wird mit dem Befehl beendet:

docker compose down

Das Docker-Image bleibt dabei erhalten.
