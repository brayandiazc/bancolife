# 0002. Sin autenticación por alcance educativo

- **Estado**: Aceptada
- **Fecha**: 2026-07-02
- **Decisores**: Brayan Díaz C

## Contexto y problema

BancoLite modela operaciones bancarias (clientes, cuentas, transferencias) donde
la seguridad sería crítica en un producto real. Sin embargo, el objetivo del
proyecto es **didáctico**: mostrar de forma clara una API REST con persistencia y
un frontend que la consume. Añadir autenticación y autorización aumentaría la
superficie de código y desviaría el foco de los fundamentos.

## Opciones consideradas

- **Autenticación completa desde el inicio (JWT/sesión + roles)** — realista pero
  con mayor complejidad y curva de aprendizaje.
- **Autenticación mínima (API key)** — algo de protección con poco código, pero
  añade fricción sin aportar al objetivo pedagógico central.
- **Sin autenticación** — todos los endpoints públicos; foco en el CRUD y la
  lógica de negocio.

## Decisión

Elegimos **no implementar autenticación ni autorización** en la versión actual.
Los endpoints son públicos y solo se aplican validaciones de negocio (unicidad de
correo, saldo suficiente, montos válidos).

## Consecuencias

**Positivas:**

- Código más simple y legible; el lector se concentra en el flujo REST + datos.
- Onboarding inmediato: `docker-compose up` y a probar la API.

**Negativas / costos:**

- La aplicación **no es segura para un despliegue público** (documentado en
  [`../architecture/auth.md`](../architecture/auth.md) y [SECURITY.md](../../SECURITY.md)).

**Neutras / a vigilar:**

- La autenticación está prevista como objetivo de la v1.0 en el
  [roadmap](../product/roadmap.md); si se retoma, este ADR se reemplazará.

## Referencias

- [`../architecture/auth.md`](../architecture/auth.md)
- [`../product/roadmap.md`](../product/roadmap.md)
