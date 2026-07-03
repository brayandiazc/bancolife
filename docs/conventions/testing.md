# Convenciones de testing

> Cómo escribimos y ejecutamos tests en BancoLite.
> **Última actualización**: 2026-07-02

> Nota: la suite de tests aún no está implementada (ver [roadmap](../product/roadmap.md)).
> Este documento define la convención a seguir cuando se añadan.

## Stack

- **Framework de tests**: pytest.
- **Cobertura**: pytest-cov.
- **Cliente HTTP**: cliente de test de Flask para probar los endpoints.

## Tipos de test

| Tipo        | Qué cubre                 | Carpeta                     |
| ----------- | ------------------------- | --------------------------- |
| Unitarios   | Funciones/clases aisladas | `backend/tests/unit`        |
| Integración | Endpoints + base de datos | `backend/tests/integration` |

## Reglas

- Todo cambio funcional se acompaña de tests.
- Estructura **Arrange-Act-Assert** (AAA): preparar, ejecutar, verificar.
- Un test verifica **una** cosa; nombres descriptivos del comportamiento esperado.
- Los tests deben ser deterministas (sin dependencia de red, reloj o orden).
- Cobertura mínima esperada: 70%.

## Ejemplos

```text
describe "POST /transferencias"
  it "rechaza la transferencia cuando el saldo es insuficiente"
    # Arrange: crear cuentas con saldo conocido
    # Act: POST /transferencias con monto > saldo
    # Assert: 400 y saldos sin cambios
```

## Comandos útiles

```bash
pytest                    # Ejecutar todos los tests
pytest --cov=backend      # Con reporte de cobertura
pytest -k transferencia   # Ejecutar por palabra clave
```

## Referencias

- [Documentación de pytest](https://docs.pytest.org/)
