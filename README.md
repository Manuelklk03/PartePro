# PartePro

Gestión de avisos e intervenciones para técnicos a domicilio.

PartePro permitirá recibir un aviso, asignarlo a un técnico, registrar el trabajo y entregar un parte al cliente. Después incorporará presupuestos con versiones y captura de notas y fotos sin conexión.

**Estado: documentación inicial. Todavía no existe una aplicación ejecutable ni una demo.**
Este paquete contiene directrices y tareas; las tecnologías, pruebas y automatizaciones indicadas son el objetivo, salvo que se señale expresamente lo contrario.

## Recorrido previsto

1. El responsable crea un cliente y un aviso.
2. Asigna un técnico y una visita.
3. El técnico registra el trabajo desde el móvil.
4. El responsable cierra el aviso y consulta su historial.
5. En fases posteriores: presupuesto, aceptación del cliente, PDF y sincronización.

El primer ámbito de trabajo será un pequeño negocio con técnicos a domicilio. No se presupone que Cerrajería NOA vaya a utilizarlo. La validación con usuarios está pendiente.

## Stack elegido para el plan

| Parte | Elección |
| --- | --- |
| Frontend | Vue 3, TypeScript estricto, Vite, Vue Router, Pinia |
| Backend | Java, Spring Boot, Spring Security, Spring Data JPA, Maven Wrapper |
| Datos | PostgreSQL, Flyway |
| Sesión | Cookie HttpOnly y protección CSRF |
| Calidad | ESLint, Prettier, comprobación de tipos, análisis Java |
| Pruebas | Vitest, Vue Test Utils, JUnit, pruebas de integración y Playwright |
| Entorno y entrega | Docker Compose, GitHub Actions, SonarQube Cloud |
| Offline, en fase posterior | Service worker, IndexedDB y cola de operaciones |

Las versiones exactas de Java, Node, Spring Boot y dependencias se verificarán y fijarán en la fase 1. No hay instaladores, imágenes ni pipelines implementados en este paquete.

## Documentación

- [Empezar](00-EMPEZAR.md)
- [Pautas para agentes](AGENTS.md)
- [Estado actual](docs/STATUS.md)
- [Producto y alcance](docs/producto.md)
- [Arquitectura](docs/arquitectura.md)
- [Modelo y reglas](docs/dominio.md)
- [Fases](docs/roadmap.md)
- [Flujo de Git](docs/git-workflow.md)
- [Calidad y entrega](docs/calidad-devops.md)
- [Seguridad](docs/seguridad.md)
- [Sincronización](docs/offline.md)
- [Diseño](docs/diseno.md)
- [Validación del producto](docs/validacion.md)
- [Decisiones](docs/decisiones/README.md)
- [Continuar con una IA](docs/CONTINUAR-CON-IA.md)
- [Fuentes técnicas](docs/fuentes.md)
- [Cambios](CHANGELOG.md)

## Autor

Manuel Casinos Pérez · [GitHub](https://github.com/Manuelklk03) · [Portfolio](https://manuelcasinos.es/)

Licencia: pendiente de elección antes de distribuir la aplicación como software reutilizable.
