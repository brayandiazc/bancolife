# Convenciones de calidad y tooling

> Linters, formato, análisis estático y git hooks de BancoLite.
> **Última actualización**: 2026-07-02

> Nota: el tooling de calidad aún no está cableado en el repo (ver
> [roadmap](../product/roadmap.md)). Este documento define las herramientas
> recomendadas y cómo usarlas.

## Stack

- **Linter**: Ruff (o Flake8).
- **Formateador**: Black.
- **Análisis estático / seguridad**: Bandit.
- **Auditoría de dependencias**: pip-audit.
- **Orquestador de git hooks**: pre-commit (opcional).

## Git hooks

Estrategia sugerida: hooks baratos y rápidos en `pre-commit`, los más costosos en
`pre-push`. CI ejecuta todo de nuevo en el servidor.

### pre-commit (en cada commit)

- Linter sobre archivos cambiados.
- Formato automático.
- Verificación de trailing whitespace, fin de archivo, conflictos sin resolver.

### pre-push (al subir)

- Linter completo.
- Tests (o un subconjunto rápido).
- Auditoría de dependencias.

## Reglas

- El código Python sigue PEP 8; líneas de máximo 88 caracteres (default de Black).
- El código debe pasar linter y formato antes del merge.
- Los checks de calidad son **bloqueantes** en CI.

## Comandos útiles

```bash
ruff check backend        # Linter
black backend             # Formateo
bandit -r backend         # Análisis de seguridad
pip-audit -r backend/requirements.txt   # Auditoría de dependencias
```

## Referencias

- [Ruff](https://docs.astral.sh/ruff/) · [Black](https://black.readthedocs.io/) ·
  [Bandit](https://bandit.readthedocs.io/) · [pip-audit](https://pypi.org/project/pip-audit/)
