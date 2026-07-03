# Stack Tecnológico

> Fuente de verdad de las tecnologías y versiones del proyecto.
> **Última actualización**: 2026-07-02

## Frontend

| Categoría | Tecnología          | Versión | Por qué                                              |
| --------- | ------------------- | ------- | ---------------------------------------------------- |
| Lenguaje  | JavaScript (ES6+)   | —       | Sin build ni framework; simplicidad educativa.       |
| Markup    | HTML5               | —       | Estructura de la interfaz.                           |
| Estilos   | CSS3 (vanilla)      | —       | Estilos propios sin dependencias.                    |
| Servidor  | Nginx               | alpine  | Sirve los estáticos y actúa como punto de entrada.   |

## Backend

| Categoría           | Tecnología     | Versión | Por qué                                                   |
| ------------------- | -------------- | ------- | --------------------------------------------------------- |
| Runtime             | Python         | 3.11    | Ecosistema maduro y legible para un proyecto didáctico.   |
| Framework           | Flask          | 3.0.0   | Microframework mínimo para exponer una API REST.          |
| ORM / capa de datos | SQLAlchemy     | 2.0.23  | Mapea las entidades a PostgreSQL sin SQL manual.          |
| Validación          | Pydantic       | 2.5.0   | Modelos de validación de los payloads de entrada/salida.  |
| CORS                | Flask-CORS     | 4.0.0   | Permite el consumo desde el frontend en otro origen.      |
| Driver PostgreSQL   | psycopg2-binary| 2.9.9   | Conector de PostgreSQL para SQLAlchemy.                   |
| Entorno             | python-dotenv  | 1.0.0   | Carga de variables de entorno desde `.env`.               |

## Base de Datos

| Categoría | Tecnología | Versión   | Por qué                                          |
| --------- | ---------- | --------- | ------------------------------------------------ |
| Principal | PostgreSQL | 15-alpine | Base relacional robusta para cuentas y saldos.   |

> No se usa capa de cache ni cola de mensajes: el alcance actual no lo requiere.

## DevOps & Herramientas

| Categoría    | Tecnología                     |
| ------------ | ------------------------------ |
| CI/CD        | GitHub Actions (ver `.github/workflows/`) |
| Contenedores | Docker                         |
| Orquestación | Docker Compose                 |
| Servidor web | Nginx (frontend)               |

## Servicios externos

No hay servicios externos de terceros. Toda la funcionalidad corre en los tres
contenedores locales (`db`, `backend`, `frontend`).

## Justificación de elecciones

| Tecnología elegida | Alternativa descartada | Razón                                                        |
| ------------------ | ---------------------- | ------------------------------------------------------------ |
| Flask              | FastAPI / Django       | Menor superficie; ideal para enseñar los fundamentos de REST.|
| JS vanilla         | React / Vue            | Evita el paso de build y mantiene el foco en el CRUD.        |
| PostgreSQL         | SQLite                 | Persistencia realista con volúmenes y contenedores.          |

## Versiones mínimas soportadas

- Python >= 3.11
- PostgreSQL >= 15
- Docker Engine + Docker Compose v2
