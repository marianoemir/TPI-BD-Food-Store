# Food Store — TPI Base de Datos

Sistema de gestión de pedidos de comida. Trabajo Práctico Integrador — Base de Datos 2 , Tecnicatura Universitaria en Programación, UTN Facultad Regional Mendoza.

Toda la interacción con el sistema se realiza mediante SQL directo sobre PostgreSQL — no hay interfaz de usuario ni API.

## Integrantes

- [Facundo Quiroga]
- [Mariano Chirino]
- [Andres Fabre]

## Requisitos

- PostgreSQL 16 o superior
- pgAdmin (opcional, recomendado para ejecutar los scripts)

## Cómo crear la base de datos

1. Crear la base:
```sql
CREATE DATABASE food_store;
```

2. Ejecutar los siguientes scripts **en este orden exacto** (desde el Query Tool de pgAdmin, o con `psql -f archivo.sql`):

| Orden | Archivo | Qué hace |
|---|---|---|
| 1 | `schema.sql` | Crea los tipos ENUM, las 5 tablas, restricciones e índices |
| 2 | `objects.sql` | Crea las vistas, la función de cálculo de total, los triggers y el procedimiento `sp_crear_pedido` |
| 3 | `data.sql` | Carga datos de ejemplo (categorías, productos, usuarios y pedidos) |
| 4 | `queries.sql` | Consultas resueltas de las 16 historias de usuario + 5 analíticas |
| 5 | `transacciones.sql` | Escenarios de transacciones y concurrencia (atomicidad, aislamiento, bloqueos) |

**Importante:** `data.sql` crea los pedidos usando `CALL sp_crear_pedido(...)`, nunca con `INSERT` directo sobre `pedido`/`detalle_pedido` — así los triggers de subtotal/total quedan correctamente calculados.

## Estructura del repositorio

```
food-store-tpi/
├── schema.sql
├── objects.sql
├── data.sql
├── queries.sql
├── transacciones.sql
├── README.md
└── docs/
    ├── diagrama-er.png
    └── capturas/
```

## Cómo reproducir las pruebas de transacciones

Los escenarios de aislamiento y bloqueo (`transacciones.sql`) requieren **dos sesiones simultáneas** de psql o dos pestañas de Query Tool en pgAdmin, ejecutando las consultas en el orden indicado en los comentarios del archivo.

## Documentación

- 📄 **Informe completo (PDF)**: [completar con link o "ver `Food_Store_TPI.pdf` en la raíz del repositorio"]
- 🎥 **Video demostración**: [completar con link de YouTube/Drive]
