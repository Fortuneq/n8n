# n8n — self-hosted automation server

A Docker Compose setup for running a self-hosted [n8n](https://n8n.io) instance on a custom domain behind HTTPS, with persistent data and basic auth.

## Run

```bash
cp .env.example .env     # basic-auth credentials, domain, integration tokens
docker compose up -d
```

n8n is available on port `5678`; put it behind a reverse proxy (nginx / Caddy) for HTTPS on your domain and set `N8N_HOST` to that domain.

## Restart without losing data

```bash
docker compose down
docker compose up -d
```

Workflow data lives in a Docker volume, so containers can be recreated freely. See [`DEPLOYMENT.md`](DEPLOYMENT.md) for the full procedure, including the nginx config of the main site.

Related: [postgres](https://github.com/Fortuneq/postgres) — pgvector store used by the n8n RAG agent.
