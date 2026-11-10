# Continuar con Claude o Codex

Copia este texto al abrir el repositorio:

> Estoy desarrollando PartePro, una aplicación de gestión de intervenciones para técnicos a domicilio. Lee AGENTS.md, README.md, docs/STATUS.md, docs/roadmap.md y las decisiones antes de cambiar nada. Inspecciona el repositorio y Git para comprobar el estado real. Quiero avanzar paso a paso, entender qué hacemos y mantener actualizada la documentación para poder continuar con otra IA.
>
> Usaremos Vue y TypeScript, Spring Boot y PostgreSQL. Quiero GitHub Flow con ramas, commits en español, PR y merge commit; ESLint, Prettier, pruebas, Docker, GitHub Actions y SonarQube. Distingue lo planificado de lo implementado y verificado. No des por configuradas cuentas, plugins, secretos ni despliegues.
>
> Empieza por la siguiente tarea de STATUS. En el estado inicial es F1.1: verificar herramientas y fijar versiones compatibles. Después prepara la base técnica por tareas acotadas. Si estoy en modo guiado, dame los pasos y archivos concretos; si te pido implementar, haz el trabajo autorizado y verifícalo. No desarrolles todas las fases de golpe. Termina actualizando el estado con resultados reales y el siguiente paso.

## Comprobar antes de relevar

El siguiente agente debe encontrar la rama actual, cambios pendientes, pruebas realizadas y siguiente tarea.
No depender del historial del chat para conocer decisiones que afectan al código.
