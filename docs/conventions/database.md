# Convenciones de base de datos

> Reglas y estándares de modelado de datos en BancoLite.
> Para el modelo de datos concreto del proyecto ver
> [`../architecture/database.md`](../architecture/database.md).
> **Última actualización**: 2026-07-02

## Stack

- **Motor**: PostgreSQL 15.
- **Capa de acceso / ORM**: SQLAlchemy 2.0.
- **Migraciones**: hoy las tablas se crean con `Base.metadata.create_all()`.
  Alembic está previsto como herramienta de migraciones (ver [roadmap](../product/roadmap.md)).

## Reglas de modelado

- **Primary keys**: enteras autoincrementales (`id`), de forma consistente.
- **Nombres**: tablas y columnas en `snake_case`, en español (dominio del proyecto).
- **Foreign keys**: siempre indexadas; `NOT NULL` salvo justificación explícita.
- **Timestamps**: registrar `fecha`/marcas de tiempo relevantes (p. ej. en
  `transferencias`); considerar `created_at`/`updated_at` al crecer el modelo.
- **Tipos preferidos**:

| Caso              | Tipo (SQLAlchemy / PostgreSQL) |
| ----------------- | ------------------------------ |
| Email             | `String` (con UNIQUE)          |
| Texto corto       | `String`                       |
| Texto largo       | `Text`                         |
| JSON estructurado | `JSONB`                        |
| Dinero            | `Numeric` (evitar `Float` en producción) |
| Fecha/hora        | `DateTime`                     |
| Booleano          | `Boolean` con default          |

> ⚠️ El proyecto usa `Float` para `saldo`/`monto` por simplicidad educativa. En un
> sistema real, usar `Numeric`/`Decimal` para evitar errores de redondeo.

## Migraciones

- Reversibles y no destructivas siempre que sea posible.
- Una migración por cambio lógico; nunca editar una migración ya aplicada en `main`.
- Revisar el impacto en datos existentes antes de aplicar en producción.

## Comandos útiles

```bash
# Con Alembic (cuando se adopte):
alembic revision --autogenerate -m "descripcion"
alembic upgrade head
alembic downgrade -1
```

## Referencias

- [Documentación de SQLAlchemy](https://docs.sqlalchemy.org/)
- [Documentación de PostgreSQL](https://www.postgresql.org/docs/)
