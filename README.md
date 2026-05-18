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
