# MinIO Docker Compose (Producao)

Configuracao do MinIO com credenciais obrigatorias, persistencia, healthcheck e limites de recursos.

## Requisitos

- Docker 20.10+
- Docker Compose 2.0+

## Inicio rapido

```bash
cd miniio
cp .env.example .env
nano .env
```

Suba o servico:

```bash
docker-compose up -d
```

## Variaveis (.env)

```env
MINIO_ROOT_USER=change_me
MINIO_ROOT_PASSWORD=change_me
MINIO_PORT=9000
MINIO_CONSOLE_PORT=9001
MINIO_BROWSER_REDIRECT_URL=http://localhost:9001
MINIO_SERVER_URL=http://localhost:9000
```

## Seguranca

- Troque o usuario e a senha antes de producao.
- Evite expor as portas publicamente; use firewall ou rede interna.
- Use HTTPS em ambientes publicos e ajuste as URLs.

## Healthcheck

O servico valida disponibilidade via `GET /minio/health/ready`.

## Persistencia

Os dados ficam em `data/` (nao versionado).

## Comandos uteis

```bash
# Ver logs
docker-compose logs -f minio

# Acessar a console (exemplo local)
open "http://localhost:${MINIO_CONSOLE_PORT:-9001}"
```
