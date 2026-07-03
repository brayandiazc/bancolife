# Roadmap — BancoLite

> Estado y dirección del producto. Documento vivo.
> **Última actualización**: 2026-07-02

## Leyenda

- ✅ Hecho
- 🚧 En curso
- 📋 Planificado
- ⏸️ Diferido

## Visión

Ser un ejemplo de referencia, mínimo y reproducible, de una aplicación bancaria
fullstack (Flask + PostgreSQL + JS vanilla, orquestada con Docker) que sirva para
aprender los fundamentos de una API REST con persistencia.

## Estado actual

Aplicación funcional con CRUD de clientes y cuentas, transferencias con validación
de saldo y frontend que consume la API. Todo se levanta con `docker-compose up`.

## Por versión / fase

### v0.1 — MVP funcional ✅

- [x] API REST de clientes, cuentas y transferencias.
- [x] Frontend vanilla que consume la API.
- [x] Orquestación con Docker Compose y PostgreSQL.
- [x] Documentación del proyecto según plantilla.

### v0.2 — Robustez 📋

- [ ] Suite de tests automatizados (pytest) para la API.
- [ ] Migraciones versionadas (Alembic) en lugar de `create_all()`.
- [ ] Manejo de transferencias dentro de una transacción atómica explícita.
- [ ] Restringir CORS a orígenes conocidos.

### v1.0 — Seguridad y calidad 📋

- [ ] Autenticación (JWT o sesión) y autorización por propietario.
- [ ] Hashing de contraseñas.
- [ ] CI con linting y tests en GitHub Actions.
- [ ] Validación de payloads con los modelos Pydantic existentes.

## Backlog / ideas sin agendar

- Paginación y filtrado en los listados.
- Historial de movimientos por cuenta en el frontend.
- Exportación de transferencias (CSV).

## Fuera de alcance

- Multi-moneda, intereses, comisiones y cumplimiento regulatorio: quedan fuera por
  ser un proyecto educativo.

## Cómo se actualiza este documento

- Revisar al cerrar cada versión/fase.
- Las decisiones que cambian el rumbo se registran como ADRs en [`../decisions/`](../decisions/README.md).
