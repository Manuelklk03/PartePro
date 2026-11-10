# Seguridad del producto

## Sesión y acceso

- Hash de contraseña con el mecanismo apropiado de Spring Security.
- Cookies HttpOnly, HTTPS en publicación, CSRF y cierre de sesión real.
- Comprobar permisos y estado del usuario en todas las operaciones.
- Un UUID difícil de adivinar no sustituye la autorización.
- Limitar intentos de autenticación y registrar eventos sin datos sensibles.
- Un enlace externo no permite listar clientes, otros presupuestos ni datos internos.

## Enlaces de presupuesto

Token aleatorio de alta entropía, solo hash persistido, alcance a una revisión concreta, caducidad y revocación.
Consultar mediante GET no acepta un presupuesto.
La respuesta exige acción explícita, estado vigente y una transacción.
Evitar tokens en logs, analítica y Referer; usar política Referrer-Policy y página sin terceros.
No prometer valor jurídico o firma certificada.

## Adjuntos

Empezar con JPEG/PNG, límites documentados de tamaño y cantidad.
Validar contenido y dimensiones, generar nombres propios y excluir rutas aportadas por el usuario.
Servir desde un área protegida, con autorización por aviso.
No aceptar HTML ni SVG activo como imágenes de trabajo.
Eliminar metadatos sensibles cuando sea viable y prevenir archivos excesivos o corruptos.
Elegir almacenamiento persistente: el disco efímero del hosting no es un archivo duradero.

## Datos locales y offline

Guardar el mínimo necesario, con separación por usuario y sesión.
No almacenar cookies ni credenciales en IndexedDB.
No cachear indiscriminadamente respuestas privadas mediante el service worker.
En logout, avisar de pendientes y ofrecer sincronizar antes de salir; al confirmar salida, eliminar datos locales privados, incluidas notas pendientes, con explicación explícita.
Si el usuario cancela la salida, conservar sesión y borradores.
Tras caducar sesión, bloquear sincronización hasta reautenticar; nunca enviar pendientes bajo otra identidad.
No prometer cifrado local que no esté implementado.

## API y datos

Validar entradas, paginación, límites de peticiones y permisos del responsable.
Respuestas de error sin trazas internas ni secretos.
Eventos de auditoría acotados: actor, objeto, operación y fecha, sin duplicar datos personales completos.
La política de conservación y borrado se definirá antes de admitir clientes reales.
Una copia de seguridad solo está comprobada cuando se puede restaurar.

## Validación mínima antes de demo pública

Usuarios ficticios, permisos comprobados, límites de escritura y adjuntos, restauración y reinicio de datos.
No abrir una aplicación con credenciales bootstrap fijas o endpoints administrativos sin protección.
