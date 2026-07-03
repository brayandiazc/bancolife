# Referencia de API

> Endpoints y convenciones de la API REST de **BancoLite**.
>
> **Última actualización**: 2026-07-02

## Convenciones generales

- **URL base**: `http://localhost:5000`
- **Versionado**: sin prefijo de versión (API v0, alcance educativo).
- **Formato**: JSON (`Content-Type: application/json`).
- **Fechas**: ISO 8601 (`YYYY-MM-DDTHH:mm:ss`).
- **CORS**: habilitado para todos los orígenes en desarrollo.

## Autenticación de la API

La API **no requiere autenticación** en su versión actual. Todos los endpoints son
públicos. Ver [`auth.md`](auth.md).

## Manejo de errores

Los errores se devuelven con un objeto `error` y el código HTTP correspondiente:

```json
{
  "error": "El correo ya está registrado"
}
```

| Código HTTP | Significado                                      |
| ----------- | ------------------------------------------------ |
| 200         | Éxito                                            |
| 201         | Recurso creado                                   |
| 400         | Solicitud inválida (validación de negocio)       |
| 404         | Recurso no encontrado                            |
| 500         | Error interno                                    |

## Endpoints

### Clientes

```http
GET  /clientes          # Listar todos los clientes
GET  /clientes/:id      # Obtener un cliente
POST /clientes          # Crear un cliente
```

**Crear cliente:**

```http
POST /clientes
Content-Type: application/json

{
  "nombre": "Juan Pérez",
  "correo": "juan@email.com"
}
```

**Respuesta `201`:**

```json
{
  "id": 1,
  "nombre": "Juan Pérez",
  "correo": "juan@email.com",
  "mensaje": "Cliente creado exitosamente"
}
```

### Cuentas

```http
GET  /cuentas           # Listar todas las cuentas
GET  /cuentas/:id       # Obtener una cuenta
POST /cuentas           # Crear una cuenta
```

**Crear cuenta:**

```http
POST /cuentas
Content-Type: application/json

{
  "cliente_id": 1,
  "saldo": 1000.00
}
```

### Transferencias

```http
GET  /transferencias    # Listar todas las transferencias
POST /transferencias    # Realizar una transferencia
```

**Realizar transferencia:**

```http
POST /transferencias
Content-Type: application/json

{
  "cuenta_origen": 1,
  "cuenta_destino": 2,
  "monto": 500.00
}
```

**Respuesta `201`:**

```json
{
  "id": 1,
  "cuenta_origen": 1,
  "cuenta_destino": 2,
  "monto": 500.0,
  "fecha": "2026-07-02T12:00:00",
  "mensaje": "Transferencia realizada exitosamente"
}
```

Validaciones: monto `> 0`, cuentas distintas y existentes, saldo suficiente en la
cuenta origen.

### Salud

```http
GET /health             # Estado de la API
```

**Respuesta `200`:**

```json
{
  "status": "OK",
  "message": "BancoLite API funcionando correctamente"
}
```

## Rate limiting

No implementado en la versión actual.

## Changelog de la API

- **v0** (inicial): endpoints de clientes, cuentas, transferencias y health.
