# Dilly (Hermes Gateway)

This repo runs the `nousresearch/hermes-agent:latest` container via Docker Compose.

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

After activation, you can run the gateway command (the container itself starts with `gateway run`):

```bash
gateway --help
# or
gateway run
```

If you are specifically looking for a `hermes` command, check whether it exists in the venv:

```bash
command -v hermes
hermes --help
```

## URLs

- Gateway API: `http://localhost:8642/`
- Dashboard: `http://localhost:9119/`
