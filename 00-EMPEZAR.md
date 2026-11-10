# Empezar PartePro

## 1. Crear un repositorio vacío

En GitHub, crea un repositorio llamado **PartePro** en tu cuenta.
Descripción sugerida:

> Gestión de intervenciones para técnicos a domicilio con Vue y Spring Boot. Avisos, presupuestos con versiones, historial y trabajo sin conexión por fases.

Puedes hacerlo público para el portfolio. Deja desmarcada la creación automática de README, .gitignore y licencia: este paquete ya incluye los dos primeros. La licencia se decidirá por separado.

## 2. Clonar y copiar los documentos

En la terminal de Windows, desde la carpeta donde guardas tus proyectos:

```powershell
git clone https://github.com/Manuelklk03/PartePro.git
cd PartePro
```

Es normal que Git avise de que el repositorio está vacío.
Descomprime el ZIP y copia **el contenido de la carpeta PartePro** dentro del clon.
README.md y AGENTS.md deben quedar en la raíz, sin una segunda carpeta PartePro.

## 3. Publicar la documentación inicial

Esta es la creación inicial de main. Las siguientes tareas se harán con rama y PR.

```powershell
git status
git add README.md 00-EMPEZAR.md AGENTS.md CLAUDE.md CHANGELOG.md .editorconfig .gitignore .github/pull_request_template.md docs
git diff --cached --check
git diff --cached --stat
git commit -m "docs: definir alcance y directrices iniciales de PartePro"
git branch -M main
git push -u origin main
```

Si Git pide nombre y correo, configura tu identidad antes del commit.
No subas archivos .env, credenciales ni datos de clientes.

## 4. Primera tarea de desarrollo

```powershell
git switch main
git pull --ff-only
git switch -c feat/base-tecnica
```

Abre el proyecto en tu editor y pasa el texto de [CONTINUAR-CON-IA](docs/CONTINUAR-CON-IA.md) a Claude o Codex.

La primera tarea es **F1.1: verificar el entorno y fijar versiones**.
Después se inicializarán frontend y backend, se conectará PostgreSQL y se montarán las comprobaciones.
No hay comandos npm o Maven disponibles hasta crear esas aplicaciones.

## 5. Qué debes poder enseñar al terminar la fase 1

- Vue servido desde frontend/.
- API con endpoint de salud sin información sensible.
- Migraciones de PostgreSQL aplicadas.
- Variables documentadas en .env.example, sin secretos reales.
- Docker Compose arrancando el conjunto.
- Comprobaciones de frontend y backend reproducibles.
- Un primer pipeline que ejecute esas comprobaciones.

Las conexiones a SonarQube, registros de imágenes y hosting se documentarán al configurarlas.
No se necesitan pagos ni cuentas nuevas para preparar los documentos y desarrollar en local.
El hosting se elegirá más adelante según sus límites vigentes.
