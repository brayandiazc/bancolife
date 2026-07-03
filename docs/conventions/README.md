# Convenciones

Esta carpeta documenta **cómo trabajamos** en BancoLite: reglas y
estándares transversales que aplican al día a día, independientes de cualquier
feature concreta.

> Diferencia con `docs/architecture/`: aquí van las **reglas** ("cómo modelamos
> datos"); en `architecture/` va **este** proyecto en concreto ("cuál es nuestro
> modelo de datos").

## Convenciones incluidas

| Convención                               | Tema                               |
| ---------------------------------------- | ---------------------------------- |
| [authentication.md](authentication.md)   | Autenticación y autorización       |
| [database.md](database.md)               | Modelado de datos y migraciones    |
| [deploy.md](deploy.md)                   | Despliegue y operaciones           |
| [quality-tooling.md](quality-tooling.md) | Linters, formato y git hooks       |
| [secrets.md](secrets.md)                 | Manejo de secretos y credenciales  |
| [testing.md](testing.md)                 | Estrategia y estándares de testing |

> Se omitieron las convenciones que no aplican a este proyecto (branding,
> design-system, views-and-layouts, i18n, seo, transactional-emails). Puedes
> añadirlas con [`_template.md`](_template.md) si el alcance crece.

## Agregar una convención

Copia [`_template.md`](_template.md), renómbralo en `kebab-case` y documenta el
nuevo tema. Añádelo a la tabla de arriba.

## Convenciones adicionales opcionales

No se incluyen por defecto; créalas con `_template.md` si tu proyecto las necesita.

- **Genéricas / SaaS**: pagos, webhooks, multi-tenancy, PWA, administración,
  aceptación legal, observabilidad.
- **Móvil**: release a stores (versionado, firma/code-signing, capturas y ASO),
  permisos del dispositivo, notificaciones push, modo offline.
- **Escritorio**: empaquetado e instaladores por SO, code signing y notarización,
  auto-update, telemetría / reporte de crashes.
