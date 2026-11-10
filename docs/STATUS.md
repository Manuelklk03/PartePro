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

## Registro de sesión

Fecha: 2026-11-10
Rama y commit: feat/base-tecnica, partiendo de bc60728.
Objetivo: F1.1, comprobar el entorno y fijar versiones.
Cambios verificados: instalado Temurin 25.0.5 LTS con winget (JAVA_HOME configurado); Docker Desktop arrancado y `docker run hello-world` correcto; extensiones de VS Code para Vue, Java y Spring Boot instaladas; versiones registradas en docs/herramientas.md y ADR-009.
Comprobaciones y resultados: `git --version`, `node --version`, `npm --version`, `java -version`, `docker --version`, `docker compose version` y `gh auth status` correctos.
Limitaciones o bloqueos: ninguno. Hay que abrir Docker Desktop antes de usar `docker`. Las terminales abiertas antes de instalar Java deben reiniciarse para ver `java`.
Commits: fd94100 (F1.1) y normas de Git de Manuel en docs/git-workflow.md y AGENTS.md, ambos en la PR #1.
Cambios sin commit: ninguno.
Siguiente tarea: merge de la PR #1 desde la terminal con mensaje; después F1.2.
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
