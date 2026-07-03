# Convenciones de autenticación y autorización

> Reglas transversales de autenticación y autorización en BancoLite.
> Para cómo funciona (o no) la auth en este proyecto ver
> [`../architecture/auth.md`](../architecture/auth.md).
> **Última actualización**: 2026-07-02

> Estado actual: **BancoLite no implementa autenticación** (ver ADR
> [0002](../decisions/0002-no-authentication-educational-scope.md)). Este documento
> define las reglas a seguir **cuando se adopte** (objetivo de la v1.0 del
> [roadmap](../product/roadmap.md)).

## Stack recomendado

- **Autenticación**: JWT o sesión (p. ej. Flask-JWT-Extended / Flask-Login).
- **Autorización**: por propietario del recurso (un cliente solo opera sus cuentas).
- **Hashing de contraseñas**: bcrypt o argon2.

## Reglas

- La autorización se valida **siempre en el servidor**, en cada request.
- Nunca confiar en checks de cliente para decisiones de seguridad.
- Las contraseñas se almacenan hasheadas con un algoritmo robusto y salt.
- Los tokens/sesiones se rotan en cada login y tienen expiración.
- Los flujos OAuth/SSO se validan server-side (email y UID).

## Modelo

- **Usuario**: aún no existe una identidad de acceso; la entidad `clientes` no
  tiene credenciales. Al adoptar auth se añadirán campos (`password_hash`, etc.).
- **Sesión / token**: por definir (JWT firmado o cookie de sesión).
- **Roles / permisos**: por definir (mínimo: propietario de cuenta).

## Ejemplos

```text
# Pseudocódigo de verificación de autorización
if not current_user.puede(accion, recurso):
    rechazar(403)
```

## Referencias

- [`../architecture/auth.md`](../architecture/auth.md)
- [ADR 0002 — Sin autenticación por alcance educativo](../decisions/0002-no-authentication-educational-scope.md)
- [SECURITY.md](../../SECURITY.md)
