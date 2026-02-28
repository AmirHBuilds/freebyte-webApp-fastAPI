# FreeByte FastAPI App (Dockerized)

## Security and secrets
- Sensitive values were removed from `private.py` (file deleted).
- App now reads config from `.env` through `settings.py` (Pydantic Settings).

Edit your `.env` file and set your secrets before production use.

## Run with Docker (auto migration)

```bash
docker compose up --build
```

What happens:
1. `db` starts (PostgreSQL)
2. `migrate` runs `alembic upgrade head`
3. `web` starts only after migration succeeds

App URL:
- http://localhost:${APP_PORT:-8005}/home

## Stop

```bash
docker compose down
```

## Reset database volume

```bash
docker compose down -v
```

## Notes
- If you change models, create a migration with Alembic and commit it:

```bash
alembic revision --autogenerate -m "describe change"
alembic upgrade head
```
