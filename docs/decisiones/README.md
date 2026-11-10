# Decisiones técnicas

## Decisiones iniciales

| ID | Decisión | Motivo |
| --- | --- | --- |
| ADR-001 | Vue y TypeScript en el frontend | Incorporar Vue al portfolio con un producto completo |
| ADR-002 | Spring Boot y PostgreSQL | Reforzar el backend que Manuel ya conoce |
| ADR-003 | Backend modular único | Acotar infraestructura y facilitar transacciones |
| ADR-004 | Recorrido online antes de offline | Fijar reglas y permisos antes de sincronizar |
| ADR-005 | Una empresa por instalación | Evitar multiempresa antes de validar la primera utilidad |
| ADR-006 | Sesión con cookie y CSRF | Mantener credenciales fuera del almacenamiento JavaScript |
| ADR-007 | Presupuestos con revisiones inmutables | Relacionar cada respuesta con el contenido exacto enviado |
| ADR-008 | Sin herramientas de IA dentro del producto por defecto | Las funciones iniciales no lo requieren |
| ADR-009 | Java 25 LTS (Temurin), Spring Boot 4.1.2 y Node 24 (2026-11-10, aceptada) | Versiones LTS/estables y compatibles según la documentación oficial; detalle en docs/herramientas.md |

Las decisiones ADR-001 a ADR-008 son del diseño inicial, no implementaciones verificadas.

## Pendientes

Versiones de dependencias de frontend y PostgreSQL; publicación; almacenamiento de adjuntos; caducidad de enlaces;
retención offline; estrategia de sesión en varios procesos; librería de PDF;
formato Java; licencia.

## Plantilla para ampliar

ID y título:
Fecha:
Estado: propuesta / aceptada / sustituida.
Problema:
Alternativas consideradas:
Decisión y motivo:
Consecuencias:
Cómo se verificará:
Qué decisión sustituye, si corresponde:
