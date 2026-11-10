# Instrucciones para trabajar en PartePro

## Objetivo y contexto

El propietario es Manuel Casinos Pérez. Está preparando proyectos para su primer empleo como desarrollador.
Explicar los cambios en español claro, de forma práctica y paso a paso.

Orden de proyectos acordado: **PartePro → ReconcileLab → RelayLab**.
Este repositorio solo contiene PartePro. No crear los otros proyectos aquí.

Estado inicial: documentación, sin aplicación. No confundir requisitos con funcionalidades implementadas.

## Lectura al empezar

1. README.md.
2. docs/STATUS.md.
3. docs/roadmap.md.
4. docs/decisiones/README.md.
5. La documentación del área que se va a modificar.

Inspeccionar el repositorio y Git antes de proponer cambios. El código y las comprobaciones actuales pueden revelar que un documento se ha quedado antiguo: señalar la diferencia y corregirla con evidencia.

## Forma de trabajar

- Avanzar por una tarea o recorrido acotado.
- Explicar brevemente qué se hará y para qué.
- Mantener frontend Vue y backend Spring Boot; documentar cambios de arquitectura antes de extenderlos.
- Organizar por funcionalidades, con un backend modular y una sola base de datos.
- Empezar con una organización por instalación y usuarios con roles.
- Incorporar offline después del recorrido online. No afirmar que hay soporte offline por tener solo un manifest o caché de archivos.
- Mobile first; accesibilidad, estados de carga y errores desde la primera pantalla.
- CSS propio con BEM y estilos de componentes acotados. Evitar duplicar sistemas de estilos.
- No añadir librerías, servicios, IA, microservicios o infraestructura sin una necesidad de la tarea.
- Claude podrá proponer plugins según su disponibilidad real y explicar para qué sirven. Registrar los elegidos en docs/herramientas.md. Este paquete no instala ninguno.
- Usar datos ficticios en demos, capturas y fixtures.
- No inventar resultados, despliegues, cobertura, benchmarks ni usuarios.
- No sobrescribir trabajo ajeno ni cambios locales sin revisar.
- Respetar la autorización vigente del usuario; no introducir nuevas pausas por rutina.
- Si hace falta una decisión real, explicar qué falta. Continuar las tareas independientes que sigan autorizadas.

## Git y calidad

Seguir docs/git-workflow.md: ramas, commits pequeños en español y PR que pueden agrupar varias tareas relacionadas.
Manuel hace todo Git y GitHub desde la terminal (git y gh). El merge es un merge commit con un mensaje que resume la PR y sus commits.
La creación inicial de main está descrita en 00-EMPEZAR.md.
Usar add selectivo, revisar diff y ejecutar comprobaciones adecuadas al cambio.
No mezclar correcciones ajenas ni ocultar fallos de CI. No guardar secretos.

## Al terminar una sesión

Actualizar docs/STATUS.md con:
- rama y commit consultados;
- cambios terminados, pendientes y sin commit;
- comandos ejecutados y resultados;
- bloqueos reales;
- una siguiente tarea concreta.

Actualizar CHANGELOG y decisiones cuando proceda.
La entrega debe explicar qué cambió, cómo se verificó y qué limitaciones quedan.
