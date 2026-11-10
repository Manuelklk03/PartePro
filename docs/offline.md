# Trabajo sin conexión y sincronización

Se implementará después del recorrido online. Instalar una PWA no equivale a guardar trabajo offline.

## Primer alcance offline

Consultar una copia limitada de los avisos asignados y añadir notas.
Fotos y edición de datos existentes llegan después.
El servidor conserva la autoridad sobre permisos, asignación, estado y versiones.

## Datos de una operación pendiente

operationId UUID, usuario propietario, tipo, recurso, payload, versión esperada cuando aplique, fecha local informativa, intentos y estado.
Estados visibles: pendiente, enviando, sincronizada, requiere intervención.
La fecha del dispositivo no ordena decisiones de negocio: el servidor asigna su fecha al aceptar.

## Envío

1. Guardar nota y operación en IndexedDB en una transacción local.
2. Mostrarla como pendiente.
3. Sincronizar con conexión, sesión válida y aplicación activa, o mediante botón.
4. El backend revalida acceso al aviso y registra la operación una sola vez.
5. Solo eliminar de la cola después de confirmar éxito del servidor.

No depender de Background Sync: no está garantizado en todos los navegadores.
La UI no declara éxito remoto antes de recibir confirmación.

## Idempotencia del backend

Clave única por usuario y operationId, ligada a hash del contenido y tipo de operación.
Persistir deduplicación, nota y resultado de forma atómica.
Dos peticiones simultáneas con la misma clave crean una sola nota.
Repetir la misma clave y contenido devuelve el resultado anterior.
Reutilizar la clave con contenido distinto devuelve conflicto.
Revalidar autorización antes de exponer resultados guardados.
La retención del registro debe cubrir la ventana máxima de sincronización; fijar ambas antes de publicar offline.

## Errores

| Situación | Comportamiento |
| --- | --- |
| Sin red o error transitorio | Conservar pendiente y reintentar con espera creciente y límite |
| Sesión caducada | Pausar y pedir acceso de nuevo al mismo usuario |
| Usuario distinto | No mostrar ni enviar los pendientes del anterior |
| Aviso reasignado o cerrado | Mantener error visible; no aplicar a la fuerza |
| Versión antigua | Mostrar conflicto; no sobrescribir |
| Entrada inválida | Permitir corregir o descartar conscientemente |
| Almacenamiento local lleno | Informar antes de declarar guardado; conservar texto en pantalla para copiar |

La ventana y política de reintentos se fijan al implementar; no reintentar indefinidamente errores permanentes.

## Pruebas de aceptación

- Guardar nota offline y recargar: sigue pendiente.
- Recuperar conexión y enviar dos veces: una sola nota remota.
- Simular respuesta perdida después de guardar: el reintento no duplica.
- Reasignar o cerrar el aviso antes de sincronizar: rechazo explicado.
- Cerrar sesión o cambiar usuario: no hay filtración de borradores.
- Simular almacenamiento local agotado: no afirmar que se guardó.

## Fotos: fase posterior

Límites locales y remotos, compresión con calidad razonable, comprobación del archivo y progreso.
Cada subida tiene identidad y confirmación propias.
No borrar el archivo local antes de confirmar su persistencia remota.
