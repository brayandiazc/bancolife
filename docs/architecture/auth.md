# Autenticación y Autorización

> Cómo se autentican y autorizan los usuarios en **BancoLite**.
> Para las reglas transversales ver [`../conventions/authentication.md`](../conventions/authentication.md).
>
> **Última actualización**: 2026-07-02

## Visión general

> ⚠️ **BancoLite no implementa autenticación ni autorización** en su versión
> actual. Es una decisión consciente para mantener el proyecto simple y enfocado
> en el CRUD y la lógica de negocio con fines educativos.

- **Método de autenticación**: ninguno. Todos los endpoints son públicos.
- **Almacenamiento de credenciales**: no aplica (no hay usuarios autenticables).
- **Hashing de contraseñas**: no aplica.

## Modelo de identidad

La entidad `clientes` representa a los titulares de cuentas, pero **no** es una
identidad de acceso: no tiene contraseña, rol ni sesión. Ver
[`database.md`](database.md).

## Autorización

- **Modelo**: sin control de acceso. Cualquier consumidor de la API puede leer y
  escribir todos los recursos.
- **Dónde se valida**: solo se aplican validaciones de negocio (saldo, unicidad de
  correo, montos), no de identidad.

## Roadmap de seguridad

Si el proyecto evoluciona a un escenario realista, se deberían incorporar
(ver [roadmap](../product/roadmap.md)):

- Autenticación por token (JWT) o sesión.
- Autorización por propietario: un cliente solo opera sobre sus cuentas.
- Hashing de contraseñas con bcrypt/argon2.

## Consideraciones de seguridad

Ver [SECURITY.md](../../SECURITY.md) para la política completa. **No desplegar esta
aplicación en un entorno público** sin añadir antes autenticación y endurecer CORS.
