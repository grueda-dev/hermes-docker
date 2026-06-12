# Dilly (Hermes Gateway)

This repo runs the `docker.io/nousresearch/hermes-agent:latest` container via Docker Compose.

## .env (recommended)

Docker Compose will automatically load a `.env` file from the repo root (same folder as `docker-compose.yml`).

Create `.env` with at least:

```bash
OPENROUTER_API_KEY=...  # required
HERMES_UID=1000
HERMES_GID=1000
```

Set `HERMES_UID`/`HERMES_GID` to match the user on the host. This ensures the container creates/owns files in `./projects` and `./hermes` using *your* UID/GID, so you can modify them from outside the container.

On Linux/macOS (or inside WSL):

```bash
id -u
id -g
```

## Start the container

From the repo root:

```bash
docker compose up -d
```

To stop it:

```bash
docker compose down
```

## Open a shell in the running container

```bash
docker compose exec hermes bash
```

## Use the Hermes/Gateway CLI (activate the container virtualenv)

The CLI binaries live in the container virtual environment, so they will not be on `PATH` until you activate it.

Inside the container shell:

```bash
source .venv/bin/activate
```

After activation you can run the hermes command.

```bash
hermes --help
```

The first command should be configure your hermes by going through the setup wizard:

```bash
hermes setup
```

It is also strongly recommended to configure the holographic memory with:

```bash
hermes memory setup
```

To configure a new messaging connection run:

```bash
hermes gateway setup
```

## URLs

- Gateway API: `http://localhost:8642/`
- Dashboard: `http://localhost:9119/`

## Random notes
The agent's home directory in the container is actually /opt/data/home.   So if you want to do things
like storing git credentials, you should do it in /opt/data/home/.git-credentials. 
