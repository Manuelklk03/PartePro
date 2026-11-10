# Flujo de Git

Una rama por bloque de trabajo y una PR hacia main. Excepción: el commit inicial del repositorio vacío.

## Preferencias de Manuel

- Todo Git y GitHub se hace desde la terminal (git y gh), incluidos la PR y el merge. No usar la web salvo para consultar.
- PR grandes cuando se pueda: agrupar varias tareas relacionadas de la misma fase en una rama, con un commit por tarea o cambio comprensible.
- El merge se hace con merge commit y un mensaje propio que explique qué incorpora: la PR y sus commits.

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
10. Abrir la PR hacia main con `gh pr create`, con problema, resultado y validación. Los commits siguientes de la misma rama se añaden a la PR al hacer push.
11. Revisar CI y cambios con `gh pr checks` y `gh pr diff`; resolver fallos.
12. Integrar con merge commit y mensaje propio, borrar la rama y actualizar main con pull --ff-only (ver plantilla).

## Merge con mensaje

```powershell
gh pr merge NUMERO --merge --delete-branch `
  --subject "Merge #NUMERO: resumen de lo que incorpora" `
  --body "PR #NUMERO (rama NOMBRE-RAMA): objetivo de la PR.

Commits:
- tipo: mensaje del commit 1
- tipo: mensaje del commit 2

Validación: comprobaciones ejecutadas y resultado."
git switch main
git pull --ff-only
```

Obtener la lista de commits con `git log --oneline main..NOMBRE-RAMA` antes del merge.

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
