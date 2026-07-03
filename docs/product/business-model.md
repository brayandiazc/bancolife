# BancoLite — Modelo de Negocio

> Marco: **Lean Canvas**. Describe por qué existe el proyecto y cómo genera valor.
> **Última actualización**: 2026-07-02

> BancoLite es un **proyecto educativo/demostrativo**, no un producto comercial.
> Este canvas se completa a modo de ejercicio para ilustrar el marco.

## 1. Problema

- Aprender a construir una aplicación bancaria fullstack suele requerir montar
  muchas piezas (API, base de datos, frontend, contenedores) desde cero.
- La mayoría de los tutoriales se quedan en un solo lado (solo backend o solo UI).
- **Alternativas actuales**: tutoriales dispersos, boilerplates pesados con
  frameworks que ocultan los fundamentos.

## 2. Segmentos de cliente

| Segmento               | Descripción                                    | Notas         |
| ---------------------- | ---------------------------------------------- | ------------- |
| Estudiantes de dev     | Personas aprendiendo desarrollo fullstack.     | Early adopter |
| Docentes / bootcamps   | Necesitan un ejemplo claro y reproducible.     | ICP           |

- **Cliente ideal (ICP)**: docente o autodidacta que quiere un ejemplo end-to-end
  simple de leer.
- **Early adopters**: estudiantes que arrancan con Flask + Docker.

## 3. Propuesta de valor única

- Un ejemplo bancario fullstack **mínimo, completo y levantable con un comando**.
- **Concepto de alto nivel**: "un Hola Mundo bancario con Docker Compose".

## 4. Solución (el producto)

| Módulo / Capacidad | Qué resuelve                                             |
| ------------------ | -------------------------------------------------------- |
| Gestión de clientes| Muestra un CRUD con restricción de unicidad.            |
| Gestión de cuentas | Relaciona entidades (cliente → cuentas).                |
| Transferencias     | Ilustra lógica de negocio y validaciones de saldo.      |
| Docker Compose     | Reproduce el entorno completo sin configuración manual. |

## 5. Canales

- Repositorio público en GitHub, README y documentación en `docs/`.

## 6. Modelo de ingresos

No aplica: proyecto de código abierto sin fines de lucro (licencia MIT).

## 7. Estructura de costos y rentabilidad

- **Costos**: nulos; corre localmente en contenedores.
- **Rentabilidad**: se mide en valor educativo, no en ingresos.

## 8. Métricas clave

- Stars/forks del repositorio.
- Facilidad de puesta en marcha (tiempo hasta `docker-compose up` exitoso).

## 9. Ventaja competitiva

- Simplicidad deliberada: sin frameworks de frontend ni pasos de build ocultos.

## Decisiones pendientes

- [ ] ¿Evolucionar hacia una versión con autenticación como segundo módulo didáctico?
