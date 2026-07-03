# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

El formato se basa en [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/)
y este proyecto adhiere a [Semantic Versioning](https://semver.org/lang/es/).

## [Unreleased]

### Added

### Changed

### Deprecated

### Removed

### Fixed

### Security

## [0.1.0] - 2026-07-02

Primera versión documentada de BancoLite: MVP funcional y adopción de la plantilla
de documentación.

### Added

- API REST con Flask para gestión de **clientes**, **cuentas** y **transferencias**.
- Endpoint de salud `GET /health`.
- Persistencia en **PostgreSQL** vía SQLAlchemy, con creación automática de tablas.
- Frontend en **JavaScript vanilla** servido por Nginx que consume la API.
- Orquestación de los tres servicios con **Docker Compose**.
- Documentación completa en `docs/` (arquitectura, producto, decisiones y
  convenciones) siguiendo la plantilla de proyecto.
- Archivos de gobernanza: `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`,
  `LICENSE` (MIT), `CHANGELOG.md`, `.editorconfig` y plantillas de `.github/`.
- ADR 0002 documentando la decisión de no incluir autenticación (alcance educativo).

### Security

- Se dejó de versionar el archivo `.env`; ahora está en `.gitignore` y se provee
  `.env.example` con el contrato de variables (sin valores reales).

<!--
Enlaces de comparación entre versiones:
[Unreleased]: https://github.com/brayandiazc/bancolife/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/brayandiazc/bancolife/releases/tag/v0.1.0
-->
