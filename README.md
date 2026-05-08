# Efferon Project

This project consists of a frontend and a backend.

## Requirements

The following should be installed:

- Node.js and npm
- Python
- pip
- uv

If `uv` is not installed:

```bash
pip install uv
```

Alternatively, depending on the system, `uv` can also be installed via Homebrew:

```bash
brew install uv
```

---

## Project Structure

```bash
efferon/
├── Frontend/
└── Backend/
```

---

## Starting the Frontend

Switch to the frontend folder:

```bash
cd Frontend
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

The frontend will then be available at:

```text
http://localhost:3000
```

Optionally, a production build can be created with:

```bash
npm run build
```

Important: Do not use `npm build`. The correct command is:

```bash
npm run build
```

---

## Starting the Backend

Switch to the backend folder:

```bash
cd Backend
```

Install dependencies:

```bash
pip install -r requirements.txt
```

If a `uv.lock` and `pyproject.toml` are present, the following can alternatively or additionally be used:

```bash
uv sync
```

If a `.env.example` file is present, copy it to `.env`:

```bash
cp .env.example .env
```

If no `.env.example` file is present, the `.env` file must be created manually or provided by the project team.

Start the backend server:

```bash
uv run uvicorn main:app --reload
```

The backend will then be available at:

```text
http://127.0.0.1:8000
```

After the server has started, upload and process all PDF files that should be used by running the following command from the backend folder:

```bash
cd Backend
curl -X POST http://localhost:8000/api/index \
  $(find data -maxdepth 1 -type f -name "*.pdf" -exec printf -- '-F files=@%s\n' {} \;)
```

---

## Complete Startup Flow

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

After the backend server has started, open another terminal or run the following command from the backend folder to upload and process all PDF files in the `data` folder:

```bash
cd Backend
curl -X POST http://localhost:8000/api/index \
  $(find data -maxdepth 1 -type f -name "*.pdf" -exec printf -- '-F files=@%s\n' {} \;)
```

---

## Common Errors

### `sh: next: command not found`

This error means that the frontend dependencies have not been installed yet.

Solution:

```bash
cd Frontend
npm install
npm run dev
```

---

### `Unknown command: "build"`

The command was entered incorrectly.

Incorrect:

```bash
npm build
```

Correct:

```bash
npm run build
```

---

### `zsh: command not found: uv`

`uv` is not installed.

Solution:

```bash
pip install uv
```

Then run again:

```bash
uv sync
uv run uvicorn main:app --reload
```

---

### `cp: .env.example: No such file or directory`

The `.env.example` file does not exist in the current folder.

Check:

```bash
ls
```

If no `.env.example` file is present, the `.env` file must be created manually or provided from another source.

---

## Development Servers

Frontend:

```text
http://localhost:3000
```

Backend:

```text
http://127.0.0.1:8000
```
