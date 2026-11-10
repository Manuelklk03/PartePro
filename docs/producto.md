# Producto y alcance

## Problema que queremos contrastar

Un pequeño negocio de servicios a domicilio necesita saber qué avisos tiene, quién los atiende, qué trabajo se realizó y qué se acordó con el cliente.
La hipótesis es que una herramienta móvil sencilla puede reducir información dispersa y trabajo repetido.
No hay entrevistas ni métricas que validen esa hipótesis todavía.

## Personas y permisos previstos

| Persona | Responsabilidad |
| --- | --- |
| Responsable | Clientes, usuarios, avisos, asignaciones, presupuesto y cierre |
| Técnico | Consultar sus avisos y registrar notas y trabajo autorizado |
| Cliente externo | En fase posterior, consultar y responder a una versión de presupuesto mediante acceso limitado |

El cliente externo no tiene una cuenta de usuario en el primer alcance.
Los permisos se aplican en la API para cada recurso, además de adaptar la interfaz.

## Primera versión útil: un aviso completo online

Incluye autenticación, clientes mínimos, avisos, asignación, visita prevista, notas, historial de estados y cierre.
Un responsable puede utilizar el sistema sin que el cliente tenga que registrarse.
Un técnico solo ve los avisos asignados actualmente a él.

Recorrido de aceptación:
1. Responsable crea un cliente ficticio y un aviso.
2. Lo asigna al técnico A.
3. El técnico A lo consulta, inicia el trabajo y añade una nota.
4. El técnico B no puede acceder.
5. El responsable cierra el aviso y ve quién cambió cada estado.

## Ampliaciones por orden

1. Presupuesto editable como borrador; al enviarlo se crea una revisión inmutable.
2. Aceptación o rechazo del cliente vinculado a esa revisión.
3. Parte PDF e imágenes adjuntas.
4. Notas offline y sincronización.
5. Fotos offline y resolución visible de conflictos.

## Fuera del primer alcance

- Varias empresas usando una misma instalación.
- Cobros reales, contabilidad, facturación fiscal o integración bancaria.
- Firma electrónica con certificación o valor legal garantizado.
- Rutas óptimas, GPS continuo, marketplace o chat en tiempo real.
- Integración automática con WhatsApp, IA o proveedores de pago.
- Funcionamiento completo sin conexión de todas las pantallas.

Un presupuesto aceptado es un evento del producto. No se presenta como firma electrónica certificada.

## Demo

Usar dos técnicos y un responsable ficticios; nombres, direcciones y fotos de ejemplo.
Añadir un reinicio de datos documentado antes de abrir una demo al público.
No publicar contraseñas reutilizadas ni datos de un negocio real.
