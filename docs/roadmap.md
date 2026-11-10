# Fases de PartePro

Las casillas describen trabajo pendiente. Completar una exige evidencia.

## F0. Preparación

- [x] Documentación inicial.
- [ ] Repositorio y primer commit.
- [ ] Revisar el recorrido con al menos una persona que haga trabajo a domicilio.
- [ ] Registrar hipótesis y respuestas sin convertirlas en hechos no comprobados.

La entrevista puede avanzar en paralelo al entorno técnico.

## F1. Base técnica

- [ ] F1.1: comprobar herramientas y fijar versiones compatibles.
- [ ] F1.2: inicializar Vue, TypeScript, Router, Pinia, ESLint y Prettier.
- [ ] F1.3: inicializar Spring Boot, Maven Wrapper, validación y endpoint de salud.
- [ ] F1.4: PostgreSQL, Flyway y configuración por entorno.
- [ ] F1.5: Compose y .env.example reproducibles.
- [ ] F1.6: tests iniciales útiles, pipeline de lint/tipos/build/pruebas y análisis Sonar.
- [ ] F1.7: dependencias y configuración de desarrollo documentadas.

Salida: arranque desde un clon limpio y comprobaciones reproducibles.
No escribir pruebas que solo verifiquen que el scaffold existe.

## F2. Primer recorrido online

- [ ] Sesión, CSRF, bootstrap del responsable y usuarios técnicos.
- [ ] Clientes y listado paginado.
- [ ] Crear, asignar y consultar avisos.
- [ ] Estados, notas e historial.
- [ ] Control de versiones y permisos por recurso.
- [ ] Recorrido E2E del responsable y técnico.
- [ ] Demo con datos ficticios, si ya existe un entorno adecuado.

Salida: recorrido de docs/producto.md completo y verificado.

## F3. Presupuestos y documentos

- [ ] Revisión enviada inmutable y cálculo monetario.
- [ ] Enlace de consulta limitado, revocable y con caducidad.
- [ ] Aceptación/rechazo de una revisión concreta.
- [ ] Parte PDF.
- [ ] Adjuntos online con permisos y límites.
- [ ] Pruebas de revisión sustituida y respuestas concurrentes.

Salida: modificar un presupuesto aceptado conserva la evidencia anterior.

## F4. Notas sin conexión

- [ ] Cachear solo recursos públicos del app shell.
- [ ] Persistir avisos asignados y borradores necesarios por usuario.
- [ ] Outbox de notas en IndexedDB.
- [ ] Sincronización manual y al volver a primer plano/conexión.
- [ ] Idempotencia transaccional, permisos y estados revalidados.
- [ ] Interfaz de pendientes y errores.
- [ ] Pruebas E2E desconectando y reconectando la red.

Salida: una nota sobrevive a recargar y se sincroniza una sola vez.

## F5. Fotos y conflictos

- [ ] Cola de fotos y límites locales.
- [ ] Reintentos y limpieza.
- [ ] Cambios versionados y resolución de conflictos.
- [ ] Casos de reasignación, cierre y sesión caducada.
- [ ] Verificación en dispositivos/navegadores objetivo.

Salida: no sobrescribir cambios ajenos ni perder pendientes silenciosamente.

## F6. Publicación y operación

Aplicar las tareas necesarias antes de cada publicación; esta fase agrupa el cierre operativo.
- [ ] Hosting y costes/límites actuales revisados.
- [ ] HTTPS, cookies y proxy verificados.
- [ ] Backup y restauración probada.
- [ ] CI/CD funcionando, con rollback documentado.
- [ ] Logs, salud y límites de demo.
- [ ] README con capturas y solo funciones disponibles.
- [ ] Vídeo corto con un caso completo.
