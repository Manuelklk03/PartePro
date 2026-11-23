# Estado actual de PartePro

Actualizado: **2026-11-11**.

## Decisión del usuario

Desarrollar PartePro, ReconcileLab y RelayLab, en ese orden.
Se comienza con PartePro. Los otros dos quedan como proyectos posteriores y separados.

## Estado comprobado

| Elemento | Estado |
| --- | --- |
| Documentación inicial | Preparada |
| Validación con técnicos | Pendiente |
| Repositorio PartePro en GitHub | Creado; main sincronizada con origin (bc60728) |
| Entorno de desarrollo (F1.1) | Comprobado; versiones en docs/herramientas.md |
| Frontend | F1.2 terminada: marco de la app (router, cabecera, vista de inicio provisional y estilos base) sobre create-vue. `oxlint`, `eslint`, `vue-tsc`, `vite build` y `prettier --check` correctos. Sin pruebas todavía (F1.6) |
| Backend | No inicializado |
| Base de datos y migraciones | No implementadas |
| Pruebas de aplicación | No existen |
| Docker, CI, SonarQube y CD | Planificados |
| Demo y hosting | No configurados |
| Plugins de desarrollo | Seleccionados por fase (docs/herramientas.md); `.claude/settings.json` desactiva el resto |

## Tarea activa

**F1.3: backend con Spring Boot, Maven Wrapper, validación y endpoint de salud.**
Modo de trabajo acordado: guiado. Manuel escribe el código y la IA le guía paso a paso; la IA hace configuraciones, dependencias, documentación y Git.

## Próximo resultado esperado

Rama nueva `feat/f1-backend-base` desde main. Claude activa en `.claude/settings.json` los plugins backend-development y jvm-languages y genera `backend/` con Spring Initializr (Java 25, Spring Boot 4.1.2, Maven Wrapper, Web y Validation). Decisión pendiente: paquete Java; propuesta `es.manuelcasinos.partepro`.
Manuel escribe `HealthResponse` (record), `HealthController` (`GET /api/health`, sin datos sensibles) y su prueba con MockMvc. Antes de darle el código, Claude contrasta las anotaciones de prueba de Spring Boot 4 con la documentación actual.

## Registro de sesión

Fecha: 2026-11-10
Rama y commit: feat/base-tecnica, partiendo de bc60728.
Objetivo: F1.1, comprobar el entorno y fijar versiones.
Cambios verificados: instalado Temurin 25.0.5 LTS con winget (JAVA_HOME configurado); Docker Desktop arrancado y `docker run hello-world` correcto; extensiones de VS Code para Vue, Java y Spring Boot instaladas; versiones registradas en docs/herramientas.md y ADR-009.
Comprobaciones y resultados: `git --version`, `node --version`, `npm --version`, `java -version`, `docker --version`, `docker compose version` y `gh auth status` correctos.
Limitaciones o bloqueos: ninguno. Hay que abrir Docker Desktop antes de usar `docker`. Las terminales abiertas antes de instalar Java deben reiniciarse para ver `java`.
Commits: F1.1 y normas de Git de Manuel (terminal, formato de merge, sin coautoría de IA) en la PR #1, integrada con merge commit.
Cambios sin commit: ninguno.
Siguiente tarea: F1.2 en una rama nueva desde main.
Pendientes externos: validación con técnicos; elección posterior de hosting y licencia.

Fecha: 2026-11-11
Rama y commit: feat/frontend-base, partiendo de 3d33392 (PR abierta con varios commits).
Objetivo: F1.2, parte automática (scaffold y herramientas).
Cambios verificados: skills y reparto con Codex en docs/herramientas.md; `npm create vue@latest frontend -- --ts --router --pinia --eslint --prettier`; `npm install`; package-lock.json versionado.
Comprobaciones y resultados: `npm run lint`, `npm run type-check` y `npm run build` correctos. `npm audit`: 1 aviso moderado (minimatch, dependencia transitiva de ESLint 10, solo desarrollo); el arreglo propuesto baja ESLint a 9, cambio mayor, no aplicado.
Limitaciones o bloqueos: ninguno. Sin Vitest todavía (F1.6). Contenido de demo de create-vue sin limpiar.
Cambios sin commit: ninguno tras el commit de documentación.
Siguiente tarea: parte guiada de F1.2 (limpiar demo, primera vista y store, con Manuel escribiendo el código).

Fecha: 2026-11-23
Rama y commit: feat/f1-marco-app (PR #4), partiendo de def1412.
Objetivo: cerrar F1.2 con el marco propio de la app y seleccionar los plugins por fase.
Cambios verificados: router, App.vue, HomeView.vue y main.css escritos por Manuel; index.html con lang es y título PartePro; .claude/settings.json con 102 plugins desactivados en este repositorio.
Comprobaciones y resultados: `oxlint`, `eslint`, `vue-tsc --build`, `vite build` y `prettier --check src/` correctos. Primer intento de build fallido por `var(--color border)` en App.vue (falta un guion); corregido. Ni el lint ni los tipos detectan CSS inválido; solo lo detecta el build.
Limitaciones o bloqueos: ninguno. No se ha comprobado visualmente en el navegador con `npm run dev` en esta sesión.
Cambios sin commit: ninguno.
Siguiente tarea: F1.3 (ver "Próximo resultado esperado").

## Plantilla para siguientes sesiones

Fecha:
Rama y commit:
Objetivo:
Cambios verificados:
Comprobaciones y resultados:
Limitaciones o bloqueos:
Cambios sin commit:
Siguiente tarea:
