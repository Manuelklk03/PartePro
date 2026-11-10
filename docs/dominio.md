# Modelo y reglas del dominio

## Modelo inicial

| Entidad | Campos principales |
| --- | --- |
| Usuario | id, nombre, email, hash de contraseña, rol, activo |
| Cliente | id, nombre, teléfono opcional, email opcional, dirección, versión |
| Aviso | id, clienteId, título, descripción, técnicoId opcional, estado, visitaPrevista opcional, versión, fechas |
| Nota | id, avisoId, autorId, texto, operationId, fecha del servidor |
| EventoAviso | id, avisoId, actorId, tipo, estado anterior/nuevo, fecha |

Se empieza con una empresa por instalación; no simular aislamiento entre empresas sin implementarlo.

## Estados iniciales del aviso

| Origen | Destino permitido | Quién |
| --- | --- | --- |
| NUEVO | ASIGNADO, CANCELADO | Responsable |
| ASIGNADO | EN_CURSO | Técnico asignado o responsable |
| ASIGNADO | CANCELADO | Responsable |
| EN_CURSO | PENDIENTE_CIERRE | Técnico asignado o responsable |
| EN_CURSO | CANCELADO | Responsable, con motivo |
| PENDIENTE_CIERRE | CERRADO, EN_CURSO | Responsable |

CERRADO y CANCELADO son finales en la primera versión. Una nueva intervención crea un aviso relacionado.
Reasignar un aviso requiere responsable y queda registrado. Si estaba en curso, permanece en curso y cambia el técnico autorizado; validar el impacto en notas offline al sincronizar.
Un aviso cerrado no admite nuevas notas operativas. Los comentarios administrativos posteriores se diseñarán por separado si se necesitan.

## Reglas verificables

- No se asigna trabajo a usuarios inactivos.
- Se exige técnico para pasar de NUEVO a ASIGNADO.
- Todo cambio de estado y asignación tiene actor y fecha del servidor.
- El técnico B no accede al trabajo del técnico A modificando una URL.
- No se elimina un cliente con avisos: se archiva o se aplica la política de conservación.
- Un cambio con versión antigua devuelve conflicto y no pisa datos.
- El envío repetido de la misma nota no crea una segunda nota.

## Presupuestos: fase posterior

Presupuesto → revisiones inmutables → líneas y eventos de respuesta.
Cada revisión guarda concepto, cantidad, precio, impuestos, moneda y totales.
Al enviar se congela la revisión; cambiar importes crea otra revisión.
Una aceptación identifica exactamente la revisión aceptada.
Una revisión sustituida o un enlace vencido no permite una aceptación nueva.
Aceptación y sustitución deben comprobar el estado en una transacción para resolver carreras.
Los importes se calculan en el servidor con redondeo explícito y pruebas.

No introducir facturación fiscal como extensión implícita de estos documentos.
