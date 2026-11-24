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
| Backend | F1.3 terminada: Spring Boot 4.1.3 con Maven Wrapper (Java 25, Web y Validation) y `GET /api/health`. `mvnw verify` correcto con 1 prueba; comprobado con el `.jar` real (HTTP 200 y `{"status":"UP"}`). Sin base de datos todavía |
| Base de datos y migraciones | No implementadas |
| Pruebas de aplicación | No existen |
| Docker, CI, SonarQube y CD | Planificados |
| Demo y hosting | No configurados |
| Plugins de desarrollo | Seleccionados por fase (docs/herramientas.md); `.claude/settings.json` desactiva el resto |

## Tarea activa

**F1.4: PostgreSQL, Flyway y configuración por entorno.**
Modo de trabajo acordado: guiado. Manuel escribe el código y la IA le guía paso a paso; la IA hace configuraciones, dependencias, documentación y Git.

## Próximo resultado esperado

F1.4 en la rama `feat/f1-backend-base`, con una sola PR para F1.3 y F1.4.
Hecho por Claude: plugins database-design y database-migrations activados; `compose.yaml` con PostgreSQL 18.7; `.env.example`; dependencias de JPA, Flyway, el driver y Testcontainers; `application.properties` por variables de entorno (carga `../.env` si existe). Verificado: `mvnw verify` correcto y la API arranca contra PostgreSQL con `/api/health` en HTTP 200; Flyway no encuentra migraciones, como se espera.
Falta, de Manuel: `V1__crear_tabla_usuario.sql` a partir de docs/dominio.md y `MigracionesTest`, una prueba de integración con PostgreSQL real que compruebe que Flyway aplica la migración.

Para trabajar en otro equipo: copiar `.env.example` a `.env` y cambiar las dos claves (la misma en `POSTGRES_PASSWORD` y `DB_PASSWORD`); `docker compose up -d --wait` en la raíz; `.mvnw.cmd spring-boot:run` en `backend/`. Si se cambia la clave después de crear el volumen, hay que borrarlo con `docker compose down -v`, lo que elimina los datos locales.

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

Fecha: 2026-11-24
Rama y commit: feat/f1-backend-base (sin PR todavía), partiendo de d2914d3.
Objetivo: F1.3, backend con Spring Boot y endpoint de salud.
Cambios verificados: proyecto generado con Spring Initializr (Java 25, Spring Boot 4.1.3, Maven Wrapper 3.3.4 con Maven 3.10.1, Web y Validation); HealthResponse, HealthController y HealthControllerTest escritos por Manuel.
Comprobaciones y resultados: `mvnw verify` con exit 0 y 1 prueba correcta; el `.jar` arrancado responde HTTP 200 con `{"status":"UP"}` en `/api/health` y HTTP 404 en una ruta inexistente. En Spring Boot 4, `@WebMvcTest` está en `org.springframework.boot.webmvc.test.autoconfigure`. Primer intento: el test estaba en src/main en lugar de src/test y la clase vacía; corregido.
Limitaciones o bloqueos: Initializr ya no ofrecía Spring Boot 4.1.2, se usó 4.1.3 (ADR-009 ajustado). Mockito avisa de que se autoadjunta como agente en el JDK; inofensivo hoy, se trata en F1.6.
Cambios sin commit: ninguno tras el commit de documentación.
Siguiente tarea: F1.4 (ver "Próximo resultado esperado").

## Plantilla para siguientes sesiones

Fecha:
Rama y commit:
Objetivo:
Cambios verificados:
Comprobaciones y resultados:
Limitaciones o bloqueos:
Cambios sin commit:
Siguiente tarea:
