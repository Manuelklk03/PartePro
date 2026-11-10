# Calidad, DevOps y DevSecOps

Este documento es un plan de implementación, no una lista de herramientas configuradas.

## Comprobaciones previstas

| Área | Validación |
| --- | --- |
| Frontend | ESLint, Prettier, vue-tsc, build y Vitest |
| Backend | Maven verify, JUnit, integración con PostgreSQL y cobertura JaCoCo |
| Recorrido | Playwright con usuarios y datos ficticios |
| Contenedores | Build y prueba de salud del conjunto |
| Análisis | SonarQube Cloud con informes de cobertura reales |
| Dependencias | Actualizaciones automatizadas y análisis compatible con el stack |

Elegir una comprobación de formato Java al crear el backend y fijar su versión.
No establecer un porcentaje de cobertura como sustituto de comprobar reglas importantes.

## Pruebas prioritarias

- Autorización del técnico por aviso, tanto lectura como escritura.
- Transiciones de estado inválidas y trabajo con usuarios inactivos.
- Notas repetidas y reintentos simultáneos.
- Conflictos de edición y rollback de transacciones.
- Importes, impuestos y redondeo de presupuestos.
- Aceptación de revisión sustituida.
- Offline: guardar, recargar, recuperar conexión y verificar una sola nota.

Usar PostgreSQL real en integración (servicio de CI o Testcontainers, según entorno).
No dar por equivalente una base en memoria cuando el comportamiento SQL importa.

## CI

En pull_request hacia main y push a main:
1. Instalar versiones fijadas y dependencias desde lockfiles/wrappers.
2. Ejecutar calidad, tipos, pruebas y build.
3. Generar cobertura.
4. Ejecutar análisis de Sonar según credenciales disponibles.
5. Construir y comprobar contenedores cuando existan.

Una PR externa no recibe los secretos del repositorio. Sus pruebas básicas deben funcionar sin ellos.
No usar pull_request_target para ejecutar código de contribuciones con secretos.
Los fallos reales de pruebas y análisis no se silencian con continue-on-error.
Fijar versiones o SHA verificadas de las Actions al implementar el workflow; no inventarlas.

## CD

Publicar únicamente después de checks satisfactorios y dentro del alcance autorizado.
Construir artefactos o imágenes versionadas por commit; desplegar el mismo artefacto probado.
Registrar URL, versión y una prueba de salud y del recorrido.
Añadir rollback y copia de datos antes de migraciones con riesgo.
No desplegar producción ni publicar imágenes desde PR no confiables.

## Secretos y entorno

.env.example solo contiene nombres y ejemplos no sensibles.
Tokens en GitHub Secrets o el gestor del proveedor; nunca en commits o logs.
GITHUB_TOKEN con permissions mínimos y explícitos.
Contenedores sin root cuando el runtime lo permita.
Revisar dependencias y hallazgos de seguridad con contexto; no añadir servicios de pago por defecto.

## Comandos

Los scripts definitivos se documentarán tras crear las aplicaciones.
La fase inicial no proporciona un npm test ni un Maven verify ejecutables.
Registrar siempre qué se ejecutó realmente y qué quedó pendiente.
