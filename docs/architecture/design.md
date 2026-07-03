# Diseño — BancoLite

> Decisiones de diseño técnico y de producto: cómo se resuelve el problema y
> cómo se ve y se siente el producto. Las decisiones relevantes se promueven a
> ADRs en [`../decisions/`](../decisions/README.md).
>
> **Última actualización**: 2026-07-02

## Contexto y objetivos

- **Problema**: enseñar cómo se construye una aplicación bancaria fullstack
  mínima (clientes, cuentas, transferencias) de forma reproducible.
- **Objetivos**: CRUD funcional, API REST clara, persistencia real y un entorno
  levantable con un solo comando (`docker-compose up`).
- **No-objetivos**: autenticación, escalabilidad productiva, cumplimiento
  regulatorio, multi-moneda, intereses o comisiones.

## Requisitos

### Funcionales

- Crear y listar clientes (correo único).
- Crear y listar cuentas asociadas a un cliente, con saldo.
- Realizar transferencias entre cuentas con validación de saldo.
- Consultar el historial de transferencias.

### No funcionales

- Reproducibilidad: todo corre en contenedores.
- Simplicidad: sin frameworks de frontend ni pasos de build.
- Legibilidad del código por sobre la optimización.

## Diseño propuesto

- **Enfoque general**: SPA vanilla que consume una API Flask; PostgreSQL como
  almacenamiento. Ver [`architecture.md`](architecture.md).
- **Componentes y flujos**: tres contenedores (`frontend`, `backend`, `db`)
  en una red Docker compartida.

## Alternativas consideradas

| Alternativa            | Pros                          | Contras                          | ¿Por qué se descartó?                   |
| ---------------------- | ----------------------------- | -------------------------------- | --------------------------------------- |
| Frontend con framework | DX, componentes reutilizables | Paso de build, más dependencias  | Añade complejidad innecesaria al foco.  |
| SQLite embebido        | Cero infraestructura          | Persistencia menos realista      | Se prefirió PostgreSQL en contenedor.   |
| FastAPI                | Async, OpenAPI automático     | Curva mayor para el objetivo     | Flask es suficiente y más didáctico.    |

## Identidad visual y sistema de diseño

- **Principios de diseño**: claridad y simplicidad; una sola vista con formularios
  y listados.
- Sin sistema de diseño ni librería de componentes: estilos CSS propios y mínimos.

## Accesibilidad

- Contraste de color (objetivo WCAG AA).
- Navegación por teclado y foco visible en formularios.
- Etiquetas asociadas a cada campo de entrada.

## Estados de la interfaz

Cada vista debe contemplar: **carga**, **vacío**, **error** y **éxito**.

## Modelo de datos afectado

Ver [`database.md`](database.md) — entidades `clientes`, `cuentas` y
`transferencias`.

## Riesgos y mitigaciones

| Riesgo                                  | Impacto | Mitigación                                            |
| --------------------------------------- | ------- | ----------------------------------------------------- |
| Ausencia de auth expone toda la data    | Alto    | No desplegar en público; documentado en `auth.md`.    |
| Transferencia sin transacción atómica   | Medio   | Validar y confirmar en una sola sesión de SQLAlchemy. |
| CORS abierto a todos los orígenes       | Medio   | Restringir orígenes antes de cualquier despliegue.    |

## Preguntas abiertas

- [ ] ¿Se añadirá autenticación en una futura versión?
- [ ] ¿Conviene mover la creación de tablas a migraciones versionadas?
