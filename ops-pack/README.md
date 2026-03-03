# Ops Pack v0.1 — Self-hosted n8n (Production Basics)

This document records the current production setup and the minimum operational knowledge required to maintain it safely.

## 1) Entry & Security Baseline
- Public domain: `n8n.yan-auto.me`
- Reverse proxy: Caddy (HTTPS enabled)
- Public ports: 22 / 80 / 443 only (UFW enabled)
- n8n is NOT exposed directly to the public internet (no host port mapping for 5678)

## 2) Deployment (Docker Compose)
- Host: Ubuntu 24.04 (VPS)
- Compose path: `/root/n8n-docker/docker-compose.yml`
- Services:
  - `caddy:latest` (reverse proxy)
  - `docker.n8n.io/n8nio/n8n` (current version: `2.8.3`)

## 3) Data & Critical Files (Most Important)
### Docker volumes
- `n8n-docker_n8n_data`
  - Mountpoint: `/var/lib/docker/volumes/n8n-docker_n8n_data/_data`
- `n8n-docker_caddy_data`
  - Mountpoint: `/var/lib/docker/volumes/n8n-docker_caddy_data/_data`
- `n8n-docker_caddy_config`
  - Mountpoint: `/var/lib/docker/volumes/n8n-docker_caddy_config/_data`

### n8n internal storage
Inside the n8n container: `/home/node/.n8n/`
Key files:
- `config` (contains encryptionKey; **required to decrypt credentials after restore**)
- `database.sqlite` (+ `database.sqlite-wal` / `database.sqlite-shm`)
- `n8nEventLog.log`

## 4) Operational Notes
- TLS certificates are handled automatically by Caddy.
- Current DB is SQLite (sufficient for small scale; backup must include sqlite + wal/shm).
- Next milestone: run a full backup + restore drill (Day 2).
