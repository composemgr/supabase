## 👋 Welcome to supabase 🚀

Self-hosted Supabase backend: Postgres, auth, storage, realtime and analytics

## 📋 Description

Self-hosted Supabase backend: Postgres, auth, storage, realtime and analytics

## 🚀 Services

- **studio**: supabase/studio:2026.04.27-sha-5f60601
- **kong**: kong/kong:3.9.1
- **auth**: supabase/gotrue:v2.186.0
- **rest**: postgrest/postgrest:v14.8
- **realtime**: supabase/realtime:v2.76.5
- **storage**: supabase/storage-api:v1.48.26
- **imgproxy**: darthsim/imgproxy:v3.30.1
- **meta**: supabase/postgres-meta:v0.96.3
- **functions**: supabase/edge-runtime:v1.71.2
- **analytics**: supabase/logflare:1.36.1
- **db**: supabase/postgres:15.8.1.085
- **vector**: timberio/vector:0.53.0-alpine
- **supavisor**: supabase/supavisor:2.7.4

## 📦 Installation

### Option 1: Quick Install

```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/supabase/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone

```bash
git clone "https://github.com/composemgr/supabase" ~/.local/srv/docker/supabase
cd ~/.local/srv/docker/supabase
cp default.env .env
docker compose --env-file .env up -d
```

### Option 3: Using composemgr

```bash
composemgr install supabase
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=...
BASE_HOST_NAME=...
DB_ADMIN_PASS=...
DB_CREATE_DATABASE_NAME=...
ANON_KEY=...
SERVICE_ROLE_KEY=...
APP_JWT_TOKEN=...
APP_SECRET_TOKEN_64=...
APP_API_TOKEN=...
ENCRYPTION_KEY=...
APP_ADMIN_USER=...
APP_ADMIN_PASS=...
```

See `docker-compose.yaml` for the complete list of configurable options.

### Environment Files

`default.env.sample` holds the full set of variables and is copied to `.env`
before starting the stack:

```bash
cp default.env .env
docker compose --env-file .env up -d
```

`app.env.sample` holds the app-specific overrides and is copied to `app.env`:

```bash
cp app.env.sample app.env
```

`composemgr up` applies `app.env` and `default.env` automatically. Raw
`docker compose` commands need `--env-file .env` to pick up the same values.

The stack also boots with the inline defaults in `docker-compose.yaml`, so no
env file is strictly required.

### Reverse Proxy

Three standalone compose files ship in this repo:

| File | Use |
|------|-----|
| `docker-compose.yaml` | Default, published on `172.17.0.1:64359` |
| `docker-compose.traefik.yaml` | Behind an existing external `traefik` network |
| `docker-compose.tunnel.yaml` | Behind an existing external `cloudflare` tunnel network |

```bash
docker compose -f docker-compose.traefik.yaml --env-file .env up -d
```

The proxy variants publish no host ports; the app is reached only through the
proxy network.

## 🌐 Access

- **Web Interface**: <http://172.17.0.1:64359>

## 📂 Volumes

- `./volumes/db/data` - Postgres data directory
- `./volumes/db` - Database init scripts
- `./volumes/api/kong.yml` - Kong declarative configuration
- `./volumes/functions` - Edge function sources
- `./volumes/logs/vector.yml` - Vector log pipeline configuration
- `./volumes/pooler/pooler.exs` - Supavisor pooler configuration
- `./volumes/storage` - Object storage

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose --env-file .env logs -f kong
```

## 🛠️ Management

```bash
# Start services
docker compose --env-file .env up -d

# Stop services
docker compose --env-file .env down

# Update to latest images
docker compose --env-file .env pull && docker compose --env-file .env up -d

# View logs
docker compose --env-file .env logs -f

# Restart services
docker compose --env-file .env restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
