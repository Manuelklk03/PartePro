# Estado actual de PartePro

Actualizado: **2026-11-10**.

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
| Frontend y backend | No inicializados |
| Base de datos y migraciones | No implementadas |
| Pruebas de aplicación | No existen |
| Docker, CI, SonarQube y CD | Planificados |
| Demo y hosting | No configurados |
| Plugins de desarrollo | No seleccionados |

## Tarea activa

**F1.2: inicializar Vue, TypeScript, Router, Pinia, ESLint y Prettier en frontend/.**
Modo de trabajo acordado: guiado. Manuel escribe el código y la IA le guía paso a paso; la IA instala herramientas y dependencias.

## Próximo resultado esperado

Scaffold de frontend/ con create-vue, lockfile versionado y `npm run lint`, `npm run type-check` y `npm run build` correctos.

Paso siguiente exacto: desde la raíz, `npm create vue@latest frontend` con TypeScript, Router, Pinia, Vitest, ESLint y Prettier: sí. JSX, Playwright y código de ejemplo: no.

## Rama de trabajo

`feat/f1-base-tecnica`: agrupa toda F1 (F1.2 a F1.7), con un commit por tarea y una sola PR al completar F1. No borrarla hasta entonces.

## Continuar desde otro equipo

1. Comprobar herramientas con las versiones de docs/herramientas.md: `git --version`, `node --version` (22.12+), `java -version` (25), `docker --version`, `gh auth status`.
   Si falta Java: `winget install --id EclipseAdoptium.Temurin.25.JDK --source winget` y reabrir la terminal.
2. Abrir Docker Desktop antes de usar `docker`.
3. Traer el repositorio y la rama:
   ```powershell
   git clone https://github.com/Manuelklk03/PartePro.git
   cd PartePro
   git switch feat/f1-base-tecnica
   ```
   Si ya estaba clonado: `git fetch` y `git switch feat/f1-base-tecnica`, después `git pull --ff-only`.
4. Pasar a la IA el texto de docs/CONTINUAR-CON-IA.md. Las normas de Git de Manuel están en docs/git-workflow.md (sección "Preferencias de Manuel").

## Registro de sesión

Fecha: 2026-11-10
Rama y commit: F1.1 en feat/base-tecnica y después en feat/entorno-f1-1 (PR #2, merge 3d33392). Ahora feat/f1-base-tecnica.
Objetivo: F1.1, comprobar el entorno y fijar versiones.
Cambios verificados: instalado Temurin 25.0.5 LTS con winget (JAVA_HOME configurado); Docker Desktop arrancado y `docker run hello-world` correcto; extensiones de VS Code para Vue, Java y Spring Boot instaladas; versiones registradas en docs/herramientas.md y ADR-009.
Comprobaciones y resultados: `git --version`, `node --version`, `npm --version`, `java -version`, `docker --version`, `docker compose version` y `gh auth status` correctos.
Limitaciones o bloqueos: ninguno. Hay que abrir Docker Desktop antes de usar `docker`. Las terminales abiertas antes de instalar Java deben reiniciarse para ver `java`.
Commits: F1.1 y normas de Git de Manuel (terminal, formato de merge, sin coautoría de IA) integrados por la PR #2. La PR #1 se cerró sin merge porque contenía un commit con coautoría de IA. En feat/f1-base-tecnica: norma para borrar ramas tras el merge.
Cambios sin commit: ninguno. Rama publicada en origin.
Siguiente tarea: F1.2 (ver "Paso siguiente exacto").
Pendientes externos: validación con técnicos; elección posterior de hosting y licencia.

## Plantilla para siguientes sesiones

Fecha:
Rama y commit:
Objetivo:
Cambios verificados:
Comprobaciones y resultados:
Limitaciones o bloqueos:
Cambios sin commit:
Siguiente tarea:
