# Arquitectura propuesta

## Estructura objetivo

- frontend/: Vue y TypeScript, organizado por funcionalidades.
- backend/: aplicación Spring Boot y Maven Wrapper.
- docs/: documentos de producto y desarrollo.
- .github/workflows/: automatizaciones al implementarlas.
- compose.yaml y .env.example: entorno local al implementarlo.

Estas rutas, salvo docs/ y la plantilla de PR, todavía no contienen implementación.

## Despliegue lógico

Navegador → frontend y proxy /api → Spring Boot → PostgreSQL.
Una única aplicación backend con módulos de identidad, clientes, avisos, presupuestos y adjuntos.
En local, Docker Compose incluirá servicios de frontend, API y base de datos.
Se prioriza un origen común para web y API para simplificar cookies y CSRF.

## Frontend

Vue con Composition API y componentes script setup, TypeScript estricto, Router y Pinia.
Cada funcionalidad reúne vistas, componentes, acceso HTTP y tipos propios.
Pinia se reserva para estado compartido; no duplicar todo el servidor en stores.
Un cliente HTTP común trata errores, expiración de sesión y token CSRF.
Los tipos de API se alinean con OpenAPI; generar cliente o tipos cuando el contrato esté definido.
La aplicación debe distinguir error HTTP, falta de conexión y conflicto de versión.

## Backend

Controladores con DTO, validación de entrada y servicios que aplican reglas en transacciones.
Persistencia con JPA y migraciones Flyway. No devolver entidades JPA directamente.
Separar módulos por responsabilidad; no añadir interfaces y capas que no resuelvan una dependencia real.
Elegir versiones de Java y Spring compatibles en F1.1 y registrar el motivo.
Errores estructurados con código estable y mensajes adecuados para la interfaz.

## Identidad

Sesión de servidor con cookie HttpOnly, Secure en HTTPS y SameSite apropiado.
CSRF para operaciones que modifican datos. Credenciales fuera del almacenamiento accesible a JavaScript.
Sin registro público inicial: el responsable crea o invita técnicos según el mecanismo que se defina.
El primer responsable se inicializa con un procedimiento local seguro, sin contraseña fija en el repositorio.
La operación de bootstrap no queda pública después de completarse.

## Datos y concurrencia

UUID en recursos expuestos, fechas de servidor en UTC y presentación Europe/Madrid.
Las visitas se guardan con un instante y una zona definida; validar cambios de hora.
Entidades mutables con versión para evitar sobrescrituras silenciosas.
Importes con BigDecimal en backend y NUMERIC en PostgreSQL; no float para cálculos monetarios.

## Operación

Logs con identificador de petición, sin credenciales ni contenido sensible.
Endpoint de salud mínimo. OpenAPI accesible según entorno y permisos.
No añadir Redis, RabbitMQ, Kafka o Kubernetes en la primera versión.
La cola offline empieza en el navegador; no exige un broker en el servidor.
Antes de desplegar: verificar que sesiones, adjuntos y datos persisten o tienen un comportamiento de recuperación documentado.
