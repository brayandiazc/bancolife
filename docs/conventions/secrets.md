# Convenciones de secretos y credenciales

> Cómo gestionamos secretos en BancoLite.
> **Última actualización**: 2026-07-02

## Filosofía

- Los secretos **nunca** se commitean en texto plano.
- Separación clara entre **configuración** (no sensible) y **secretos** (sensible).

## Dónde vive cada cosa

| Tipo                         | Dónde                                         |
| ---------------------------- | --------------------------------------------- |
| Secretos de aplicación       | `.env` local (desarrollo)                     |
| Variables de infraestructura | Variables de entorno del entorno              |
| Secretos de CI/CD            | Secrets del proveedor (p. ej. GitHub Actions) |

## Reglas

- El archivo `.env` está en `.gitignore`; solo se versiona `.env.example` (sin valores).
- Comparte secretos con nuevos colaboradores **fuera de banda** (nunca por git, email plano ni chat público).
- Rota credenciales periódicamente (sugerido cada 90 días) y de inmediato ante sospecha de fuga.
- Si un secreto se commitea por error: **rota el secreto primero**, luego limpia la historia.

## Ejemplos

```bash
# Copiar la plantilla de variables
cp .env.example .env
# Completar valores reales (que nunca se suben)
```

## En este proyecto

- El archivo `.env` está **ignorado** por git; solo se versiona
  [`.env.example`](../../.env.example) con el contrato de variables (sin valores).
- Las variables por defecto de `docker-compose.yml` son credenciales locales de
  desarrollo, no secretos reales de producción.

## Referencias

- [SECURITY.md](../../SECURITY.md) — política de seguridad.
- [`.env.example`](../../.env.example) — contrato de variables de entorno.
