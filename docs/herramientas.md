# Herramientas y entorno

Estado: comprobado el 2026-11-10 en Windows 11 (F1.1).

## Registro de versiones

| Herramienta | Versión elegida | Evidencia |
| --- | --- | --- |
| Git | 2.56.0.windows.4 | git --version |
| Node | 24.21.0 | node --version; Vite 8.3.7 exige `^20.19.0 \|\| >=22.12.0` (npm view vite engines.node) |
| npm | 12.1.0 | npm --version |
| Java | Temurin 25.0.5+8 LTS | java -version; instalado con `winget install EclipseAdoptium.Temurin.25.JDK`; JAVA_HOME configurado |
| Maven Wrapper | 3.3.4, descarga Maven 3.10.1 | backend/.mvn/wrapper/maven-wrapper.properties; `mvnw verify` correcto; Spring Boot 4.1.3 exige Maven 3.6.3+ |
| Docker y Compose | Docker 29.9.2, Compose v5.6.1 | docker --version / docker compose version; `docker run hello-world` correcto |
| PostgreSQL | 18.7 (imagen `postgres:18.7-alpine`) | Docker Hub (2026-11-24): la 19.0 acaba de publicarse, se elige la 18, mayor estable anterior. `docker compose up -d --wait` correcto; Flyway confirma PostgreSQL 18.7 |
| Persistencia y pruebas | Hibernate 7.4.15, Flyway 12.4.0, driver PostgreSQL 42.7.14, Testcontainers 2.0.5 | `mvnw dependency:tree`; versiones del BOM de Spring Boot 4.1.3 |
| Spring Boot | 4.1.3 (estable) | Spring Initializr (2026-11-23) ya no ofrece la 4.1.2: se usa el parche 4.1.3 de la misma línea; existe la 4.2.0 y no se adopta. Requisitos: Java 17 a 27, Spring Framework 7.0.10+ (docs.spring.io/spring-boot/system-requirements.html) |
| Vue y herramientas | Instalado (F1.2, 2026-11-11) | create-vue 3.24.0; Vue 3.5.45, Vue Router 5.5.0, Pinia 4.1.0, Vite 8.3.8, TypeScript 6.0.3, vue-tsc 3.3.14, ESLint 10.14.0, Oxlint 1.82.0, Prettier 3.9.6 (frontend/package-lock.json). Engines del proyecto: Node `^22.18.0 \|\| >=24.12.0`, compatible con Node 24.21.0 |

Motivo de Java 25: es la LTS más reciente y está dentro del rango de Spring Boot 4.1.3. Java 26 y 27 no son LTS.
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

### Plugins del proyecto (decisión del 2026-11-17)

`.claude/settings.json` desactiva en este repositorio los plugins que no encajan con PartePro o que solo hacen falta en una fase. La configuración global de Manuel no cambia. Los cambios se aplican al reiniciar Claude Code.

- **Activo:** disponible desde ya.
- **En espera:** desactivado hasta su fase. Al llegar, Claude pone su línea a `true` (o la borra) en `.claude/settings.json` y lo anota aquí.
- **Descartado:** no encaja con el alcance. Se reevalúa solo si el alcance cambia.

Con esto quedan 17 plugins activos de 119. Claude carga mucho menos contexto en cada sesión.

#### Activos ahora

| Plugin | Para qué en PartePro |
| --- | --- |
| superpowers | brainstorming y writing-plans antes de tareas grandes; verification-before-completion antes de dar algo por hecho; systematic-debugging ante fallos; TDD desde F1.6 |
| frontend-stack | Router que decide qué skill de diseño lidera cada fase de UI |
| antislop | Evitar el aspecto genérico de IA en pantallas y textos |
| code-documentation | `code-explain`: explicar código paso a paso mientras Manuel aprende |
| documentation-generation | ADR, changelog y especificación OpenAPI |
| javascript-typescript | TypeScript avanzado y pruebas de JavaScript |
| backend-development, jvm-languages | Diseño de API y arquitectura de Spring Boot (activados en F1.3, 2026-11-23). `java-pro` orienta a Spring Boot 3.x, así que se contrasta con la documentación oficial de 4.1 |
| database-design, database-migrations | Diseño de tablas en PostgreSQL y migraciones SQL (activados en F1.4, 2026-11-24) |
| chrome-devtools-mcp | Lighthouse y accesibilidad con la primera pantalla |
| Personales: ponytail, caveman, claude-mem, mempalace, headroom, oh-my-claudecode, codex, claude-code-setup, grill-me, andrej-karpathy-skills | Estilo, memoria y herramientas de Manuel; no forman parte del repositorio |

Fuera de los plugins, `playwright-cli` (skill suelta) se usa en F1.6 y F2 para el E2E.

#### En espera, por fase

| Fase | Plugins | Para qué |
| --- | --- | --- |
| F1.6 | cicd-automation, unit-testing, tdd-workflows, dependency-management | GitHub Actions y secretos, pruebas, TDD y auditoría de dependencias |
| F2 (inicio) | impeccable, frontend-design, ui-ux-pro-max, taste, ui-design, accessibility-compliance | Identidad visual, paleta, componentes y accesibilidad de las primeras pantallas; el router de frontend-stack decide quién lidera |
| F2 (inicio) | backend-api-security, frontend-mobile-security, security-scanning, developer-essentials | Sesión, CSRF, roles, XSS y patrones de autenticación y E2E |
| F2 (inicio) | api-testing-observability, comprehensive-review | Contrato OpenAPI y revisión antes de cada merge |
| F2 (pulido) | emil-design-eng | Transiciones, solo después de la accesibilidad |
| F6 | observability-monitoring, application-performance, performance-testing-review | Logs, salud, rendimiento y límites de la demo |
| F6 | deployment-strategies, deployment-validation, incident-response | CD, rollback y verificación del despliegue |
| F6 | security-compliance, hr-legal-compliance | Revisión de seguridad antes de la demo y política de datos (RGPD) |
| F6 | c4-architecture, avoid-ai-writing | Diagramas de arquitectura y redacción del README final |

#### Descartados

| Grupo | Plugins | Motivo |
| --- | --- | --- |
| Alojamiento y datos ajenos al stack | supabase, vercel | La base es PostgreSQL propio con Flyway; el hosting se decide en F6 |
| SEO y marketing | claude-seo, seo-content-creation, seo-technical-optimization, seo-analysis-monitoring, content-marketing, customer-sales-automation, social-publishing, hermes-tweet, brand-landingpage | Es una herramienta interna con login, no una web pública |
| Animación, vídeo e imagen | scroll-world, lemo-opuscar, baoyu-skills, imagegen-skills, meigen-ai-design, pptx-deck-creation, cli-anything, file-conversion | Fuera del alcance del producto |
| Negocio | business-analytics, startup-business-analyst | No se evalúa el negocio en este repositorio |
| Otros lenguajes | python-development, systems-programming, web-scripting, functional-programming, julia-development, arm-cortex-microcontrollers, dotnet-contribution, shell-scripting | El stack es Java y TypeScript; el entorno es PowerShell |
| IA y datos | llm-application-dev, llm-finetuning, agent-orchestration, context-management, machine-learning-ops, data-engineering, dgx-spark-ops | ADR-008: sin IA dentro del producto |
| Otros dominios | payment-processing, blockchain-web3, quantitative-trading, game-development, reverse-engineering | Sin cobros ni dominios ajenos al producto |
| Multiagente que choca con el modo guiado | agent-teams, conductor, ship-mate, full-stack-orchestration, team-collaboration, operating-kit | Manuel escribe el código; un solo agente edita a la vez |
| React, móvil y API en Python | frontend-mobile-development, multi-platform-apps, api-scaffolding, data-validation-suite | El frontend es Vue y el backend Spring Boot |
| Infraestructura fuera de alcance | kubernetes-operations, cloud-infrastructure, database-cloud-optimization | Docker Compose es suficiente |
| Flujo propio de Git y depuración | git-pr-workflows, debugging-toolkit, error-debugging, error-diagnostics, distributed-debugging | Manuel usa su flujo de `docs/git-workflow.md`; superpowers cubre la depuración |
| Refactorización sin petición | code-refactoring, codebase-cleanup, framework-migration | No se hacen refactorizaciones no solicitadas |
| Utilidades sin uso previsto | documentation-standards, before-you-build, skill-forge-essentials, superself, plugin-eval, protect-mcp, signed-audit-trails, review-agent-governance, block-no-verify | Sin necesidad en el alcance |

### Reparto de trabajo con Codex

- Fuente de verdad común: AGENTS.md y docs/STATUS.md. Ninguno duplica instrucciones.
- Claude: guía paso a paso a Manuel, instala herramientas, redacta documentación, revisa el diff.
- Codex: segunda opinión o revisión independiente (`/codex:rescue`, agente `codex:codex-rescue`), diagnóstico de fallos que se atasquen y tareas acotadas que Manuel pida delegar.
- Regla: un solo agente edita a la vez en el mismo árbol; el otro revisa. Manuel escribe el código en las tareas guiadas.
