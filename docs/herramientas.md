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
| Vue y herramientas | Pendiente (F1.2) | create-vue 3.24.0 y Vite 8.3.7 disponibles; se fijarán con package.json y lockfile |

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
