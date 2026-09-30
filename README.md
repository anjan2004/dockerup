# Docker PR CI Workflow

This repository demonstrates how to automatically trigger **`docker compose up`** whenever a **Pull Request (PR)** is opened or updated in GitHub.

## 🚀 How It Works

1. A developer creates a Pull Request targeting branch `main`.
2. GitHub Actions detects the event:
   ```yaml
   on:
     pull_request:
       branches: [ main ]
   ```
3. The runner builds the Docker image and executes:
   ```bash
   docker compose up -d --build
   ```
4. A health check queries `http://localhost:8080` to verify the container is running and healthy.
5. Once verified, it displays container logs and tears down containers (`docker compose down`).
6. The PR check is marked green ✅.

## 💻 Local Testing

You can run the same command on your local machine:
```bash
docker compose up -d --build
```
Then visit `http://localhost:8080` in your browser.

To stop the container:
```bash
docker compose down
```
