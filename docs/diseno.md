# Diseño y experiencia

## Objetivo

Una herramienta fácil de usar en una visita desde el móvil.
Priorizar lectura, formularios cortos y acceso a la tarea actual.

## Pantallas iniciales

- Acceso.
- Bandeja de avisos, con filtros por estado y técnico.
- Detalle del aviso y acciones según permiso.
- Formulario de cliente y aviso.
- Registro de trabajo e historial.
- Administración básica de técnicos.

Después: presupuestos, vista del cliente y pendientes de sincronización.

## Criterios

- Mobile first y disposición adaptable para escritorio.
- HTML semántico, etiquetas en formularios, foco visible y navegación por teclado.
- Estados distinguibles por texto e icono, además del color.
- Campos de fecha y hora con zona clara.
- Guardar explícito cuando la operación lo necesite.
- Mensajes de error cerca del campo y resumen si ayuda.
- Confirmación en cancelar un aviso o descartar pendientes.
- Respetar reducción de movimiento.
- Sin animaciones que retrasen acciones.

No copiar el estilo Matrix del portfolio: este producto necesita su propia identidad.
Paleta y componentes se decidirán al crear las primeras pantallas, comprobando contraste.

## Estados que siempre se diseñan

Carga, vacío, error, falta de permisos, sesión caducada y conflicto.
En fase offline: sin conexión, guardado solo en este dispositivo, enviando y sincronizado.
"Guardado en este dispositivo" y "Guardado en el servidor" deben distinguirse claramente.
