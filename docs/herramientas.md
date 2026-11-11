# Herramientas y entorno

Estado: comprobado el 2026-11-10 en Windows 11 (F1.1).

## Registro de versiones

| Herramienta | Versión elegida | Evidencia |
| --- | --- | --- |
| Git | 2.56.0.windows.4 | git --version |
| Node | 24.21.0 | node --version; Vite 8.3.7 exige `^20.19.0 \|\| >=22.12.0` (npm view vite engines.node) |
| npm | 12.1.0 | npm --version |
| Java | Temurin 25.0.5+8 LTS | java -version; instalado con `winget install EclipseAdoptium.Temurin.25.JDK`; JAVA_HOME configurado |
| Maven Wrapper | Pendiente (F1.3) | Se generará con el proyecto; Spring Boot 4.1.2 exige Maven 3.6.3+ |
| Docker y Compose | Docker 29.9.2, Compose v5.6.1 | docker --version / docker compose version; `docker run hello-world` correcto |
| Spring Boot | 4.1.2 (estable) | docs.spring.io/spring-boot/system-requirements.html: Java 17 a 27, Spring Framework 7.0.10+ |
| Vue y herramientas | Instalado (F1.2, 2026-11-11) | create-vue 3.24.0; Vue 3.5.45, Vue Router 5.5.0, Pinia 4.1.0, Vite 8.3.8, TypeScript 6.0.3, vue-tsc 3.3.14, ESLint 10.14.0, Oxlint 1.82.0, Prettier 3.9.6 (frontend/package-lock.json). Engines del proyecto: Node `^22.18.0 \|\| >=24.12.0`, compatible con Node 24.21.0 |

Motivo de Java 25: es la LTS más reciente y está dentro del rango de Spring Boot 4.1.2. Java 26 y 27 no son LTS.
Docker Desktop debe estar abierto para usar `docker`; no arranca solo con el sistema salvo que se configure.

## Extensiones de VS Code comprobadas

| Extensión | Propósito |
| --- | --- |
| Vue.volar (Vue - Official) | Soporte de Vue y TypeScript en plantillas |
| vscjava.vscode-java-pack | Java: lenguaje, depuración, Maven y pruebas |
| vmware.vscode-spring-boot | Ayuda con propiedades y estructura de Spring Boot |
| dbaeumer.vscode-eslint, esbenp.prettier-vscode | Ya instaladas; se usarán con la configuración del proyecto |

No usar versiones de otra conversación sin comprobar el equipo.
Registrar compatibilidad de Node con Vite, y de Java con Spring Boot.
Usar dependencias estables; evitar snapshots y versiones RC por defecto.

## Plugins y asistentes

Manuel podrá pedir a Claude que proponga la configuración.
Registrar por cada herramienta: nombre real, propósito, disponibilidad comprobada y configuración aplicada.
No afirmar que hay plugins instalados o activos si no se ha verificado.
Las instrucciones compartidas viven en AGENTS.md; CLAUDE.md apunta a él.

### Skills de Claude seleccionadas (propuesta del 2026-11-11)

Disponibilidad comprobada: aparecen en la lista de skills de Claude Code de esta máquina. Codex CLI 0.164.0 está instalado y lee AGENTS.md. "Activar" significa usarla cuando encaje; no se instala nada.

| Skill | Cuándo | Para qué |
| --- | --- | --- |
| superpowers:brainstorming, writing-plans | Ahora | Diseñar y planificar antes de tareas grandes (F2 en adelante) |
| superpowers:verification-before-completion | Ahora | No dar una tarea por hecha sin ejecutar lint, tipos y build |
| superpowers:systematic-debugging | Ahora | Errores de instalación, CI o arranque |
| superpowers:test-driven-development | F1.6 y F2 | Pruebas antes del código en reglas de dominio |
| frontend-stack:frontend-stack (router) | Primera pantalla (F2) | Decide qué skill de diseño lidera; evita mezclar estilos |
| impeccable (shape, audit, polish) | F2 en adelante | Planificar UX y auditar accesibilidad y estados vacío/carga/error |
| antislop:antislop, antislop-ui, antislop-forms | F2 en adelante | Evitar aspecto genérico de IA; formularios de aviso y parte |
| web-design-guidelines | Al revisar pantallas | Revisión de accesibilidad y UX |
| chrome-devtools-mcp (a11y-debugging, lighthouse) | Con la primera pantalla | Auditar rendimiento y accesibilidad móvil |
| playwright-cli / plugin playwright | F1.6 y F2 | Pruebas E2E del recorrido aviso a parte |
| vercel-react-best-practices, nextjs, ai-sdk y resto de vercel:* | No | PartePro usa Vue y Spring Boot; solo Vercel CLI si se elige ese hosting |
| supabase:* | No | La base es PostgreSQL propio con Flyway (ADR del stack) |
| security-audit (global) | F5 (antes de demo pública) | Revisión de sesión, CSRF y roles; no se lanza una auditoría completa por defecto |
| gsap-*, threejs, scroll-world, cinematic-scroll, canvas-design | No | Sin necesidad en el alcance; GSAP, Lenis y animaciones solo si una pantalla lo pide |
| emil-design-eng (animate, review-animations) | Más adelante | Solo al pulir transiciones, tras accesibilidad |
| claude-seo:*, ai-seo | No | Es una herramienta interna con login, no una web pública |
| claude-mem, mempalace, oh-my-claudecode, caveman, ponytail | Ya instalados | Memoria y estilo de respuesta personales; no forman parte del repositorio |

### Reparto de trabajo con Codex

- Fuente de verdad común: AGENTS.md y docs/STATUS.md. Ninguno duplica instrucciones.
- Claude: guía paso a paso a Manuel, instala herramientas, redacta documentación, revisa el diff.
- Codex: segunda opinión o revisión independiente (`/codex:rescue`, agente `codex:codex-rescue`), diagnóstico de fallos que se atasquen y tareas acotadas que Manuel pida delegar.
- Regla: un solo agente edita a la vez en el mismo árbol; el otro revisa. Manuel escribe el código en las tareas guiadas.
