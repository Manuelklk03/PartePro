# Flujo de Git

Una rama por tarea; una PR acotada hacia main. Excepción: el commit inicial del repositorio vacío.

## Secuencia habitual

1. Revisar cambios locales con git status; no descartarlos.
2. Volver a main y actualizar con git pull --ff-only.
3. Crear rama: feat/avisos, fix/permisos-aviso, docs/modelo o ci/comprobaciones.
4. Implementar la tarea y actualizar documentación relacionada.
5. Ejecutar comprobaciones correspondientes a lo modificado.
6. Revisar git diff y git diff --check.
7. Añadir archivos selectivamente con git add RUTA.
8. Revisar git diff --cached y crear un commit.
9. Publicar con git push -u origin NOMBRE-RAMA.
10. Abrir una única PR hacia main, con problema, resultado y validación.
11. Revisar CI y cambios; resolver fallos.
12. Integrar usando **Create a merge commit**, borrar la rama y actualizar main con pull --ff-only.

No forzar un pull ni reescribir historial para resolver una divergencia sin revisar la causa.
Separar commits por cambios comprensibles, sin un número mínimo artificial.

## Conventional Commits en español

- feat: permitir asignar un aviso a un técnico
- fix: impedir notas en avisos cerrados
- test: comprobar la repetición de una operación
- docs: actualizar el estado de la fase online
- ci: ejecutar pruebas de integración con PostgreSQL
- refactor: separar el cálculo del presupuesto
- chore: actualizar dependencias compatibles

## Protección de main

Configurar cuando existan los checks: exigir PR y comprobaciones pertinentes.
En un proyecto mantenido por una persona, no exigir una aprobación externa imposible de obtener.
No afirmar que la protección está activa sin comprobarla.
Los resultados remotos de CI son distintos de haber ejecutado comandos en local.

## Cambios sin autorización de escritura remota

Preparar rama, diff y descripción local según el alcance disponible.
No inventar PR, enlaces ni commits publicados.
