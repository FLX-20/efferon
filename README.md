# Efferon Projekt

Dieses Projekt besteht aus einem Frontend und einem Backend.

## Voraussetzungen

Installiert sein sollten:

- Node.js und npm
- Python
- pip
- uv

Falls `uv` nicht installiert ist:

```bash
pip install uv
```

Alternativ kann `uv` je nach System auch über Homebrew installiert werden:

```bash
brew install uv
```

---

## Projektstruktur

```bash
efferon/
├── Frontend/
└── Backend/
```

---

## Frontend starten

In den Frontend-Ordner wechseln:

```bash
cd Frontend
```

Abhängigkeiten installieren:

```bash
npm install
```

Development-Server starten:

```bash
npm run dev
```

Das Frontend läuft anschließend unter:

```text
http://localhost:3000
```

Optional kann ein Production-Build erstellt werden mit:

```bash
npm run build
```

Wichtig: Nicht `npm build` verwenden. Der korrekte Befehl ist:

```bash
npm run build
```

---

## Backend starten

In den Backend-Ordner wechseln:

```bash
cd Backend
```

Abhängigkeiten installieren:

```bash
pip install -r requirements.txt
```

Falls ein `uv.lock` und `pyproject.toml` vorhanden sind, kann alternativ bzw. zusätzlich verwendet werden:

```bash
uv sync
```

Falls eine `.env.example` vorhanden ist, diese zu `.env` kopieren:

```bash
cp .env.example .env
```

Falls keine `.env.example` vorhanden ist, muss die `.env` manuell erstellt oder vom Projektteam bereitgestellt werden.

Backend-Server starten:

```bash
uv run uvicorn main:app --reload
```

Das Backend läuft anschließend unter:

```text
http://127.0.0.1:8000
```

---

## Kompletter Startablauf

### Terminal 1: Frontend

```bash
cd Frontend
npm install
npm run dev
```

### Terminal 2: Backend

```bash
cd Backend
pip install -r requirements.txt
uv sync
uv run uvicorn main:app --reload
```

---

## Häufige Fehler

### `sh: next: command not found`

Dieser Fehler bedeutet, dass die Frontend-Abhängigkeiten noch nicht installiert wurden.

Lösung:

```bash
cd Frontend
npm install
npm run dev
```

---

### `Unknown command: "build"`

Der Befehl wurde falsch eingegeben.

Falsch:

```bash
npm build
```

Richtig:

```bash
npm run build
```

---

### `zsh: command not found: uv`

`uv` ist nicht installiert.

Lösung:

```bash
pip install uv
```

Danach erneut ausführen:

```bash
uv sync
uv run uvicorn main:app --reload
```

---

### `cp: .env.example: No such file or directory`

Die Datei `.env.example` existiert nicht im aktuellen Ordner.

Prüfen:

```bash
ls
```

Falls keine `.env.example` vorhanden ist, muss die `.env` manuell erstellt oder aus einer anderen Quelle bereitgestellt werden.

---

## Entwicklungsserver

Frontend:

```text
http://localhost:3000
```

Backend:

```text
http://127.0.0.1:8000
```
