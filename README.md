## 👋 Welcome to supabase 🚀

Open-source Firebase alternative with Postgres database

## 📋 Description

Open-source Firebase alternative with Postgres database

## 🚀 Services

- **studio**: supabase/studio:20241014-c083b3b
- **kong**: kong:2.8.1
- **auth**: supabase/gotrue:v2.158.1
- **realtime**: supabase/realtime:v2.30.34
- **storage**: supabase/storage-api:v1.11.13
- **imgproxy**: darthsim/imgproxy:v3.8.0
- **functions**: supabase/edge-runtime:v1.59.0
- **analytics**: supabase/logflare:1.4.0
- **vector**: timberio/vector:0.28.1-alpine
- **supavisor**: supabase/supavisor:1.1.56

### Infrastructure Components

- **rest**: Postgrest database
- **meta**: Postgres-Meta database
- **db**: Postgres database


## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/supabase/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/supabase" ~/.local/srv/docker/supabase
cd ~/.local/srv/docker/supabase
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install supabase
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:3000

## 📂 Volumes

- `./rootfs/data/supabase` - Application data

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose logs -f studio
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
