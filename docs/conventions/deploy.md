# Convenciones de despliegue

> Cómo se ejecuta y opera BancoLite. Fuente de verdad de cómo se levanta el
> sistema y cómo se hace rollback.
> **Última actualización**: 2026-07-02

> Nota: BancoLite es un proyecto educativo. **No hay un despliegue de producción
> configurado**; se ejecuta localmente con Docker Compose. Esta convención describe
> ese flujo y sienta las bases para un despliegue futuro.

## Stack de infraestructura

- **Contenedores / orquestación**: Docker + Docker Compose.
- **Servidor web (frontend)**: Nginx.
- **Base de datos**: PostgreSQL (volumen persistente `postgres_data`).
- **CI/CD**: GitHub Actions (ver [`.github/workflows/`](../../.github/workflows/)).

## Ambientes

| Ambiente | URL                            | Rama   | Deploy         |
| -------- | ------------------------------ | ------ | -------------- |
| Local    | http://localhost (frontend)    | `main` | `docker-compose up` |
| Local    | http://localhost:5000 (API)    | `main` | `docker-compose up` |

## Reglas

- El entorno se levanta de forma reproducible con un solo comando.
- Las variables de entorno y secretos se gestionan según [`secrets.md`](secrets.md).
- Verificar el health check tras cada arranque.

## Procedimiento

```bash
# 1. Construir y levantar los servicios
docker-compose up --build

# 2. En segundo plano
docker-compose up -d

# 3. Verificar la API
curl http://localhost:5000/health
```

## Rollback / parada

```bash
# Detener los servicios
docker-compose down

# Detener y eliminar volúmenes (borra los datos)
docker-compose down -v
```

## Health checks y monitoreo

- Endpoint de salud: `GET /health`.
- Logs: `docker-compose logs -f`.

## Referencias

- [Documentación de Docker Compose](https://docs.docker.com/compose/)
