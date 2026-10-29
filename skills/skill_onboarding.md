# Skill: Onboarding del cliente

## What this does
Guía al consultor a ejecutar el SOP de "primeras veces" con un cliente nuevo: firma de contrato, primer cobro, alta de accesos en LastPass, creación de carpetas estándar, calendario interno y reunión de kick-off — para que ningún proyecto arranque sin las bases operativas listas.

## When to use it
**Activate this skill when the user:**
- Says: "tengo un cliente nuevo, hay que arrancar el proyecto"
- Says: "armame el kit de bienvenida para [cliente]"
- Asks to: "preparar el onboarding de [cliente]"
- Asks to: "organizar los accesos del cliente en LastPass"
- Starts a situation like: "el cliente firmó la propuesta, ¿qué sigue?"
- Starts a situation like: "necesito agendar el kick-off con [cliente]"
- Says: "todavía no cobré la seña / el primer pago"
- Says: "no tengo claro qué carpetas crear para este proyecto"

## How to execute
Ejecuta el SOP de onboarding en orden estricto. No avances al siguiente step si el anterior no está cerrado — cada uno destraba al siguiente.

### Step 1 — Validar precondiciones comerciales
- **Action**: Confirmar que existe propuesta aceptada por escrito (mail, WhatsApp o firma digital). Si no existe, detener el onboarding y derivar a `skill_contrato` o cierre comercial.
- **Ask the user for**: nombre legal/razón social del cliente, contacto principal (nombre + mail + teléfono), alcance acordado, monto y forma de pago, fecha tentativa de inicio.
- **Produce**: ficha mínima del cliente con esos campos completos.

### Step 2 — Contrato firmado
- **Action**: Generar contrato a partir de la propuesta aceptada (invocar `skill_contrato` si hace falta) y enviarlo a firma. Registrar fecha de envío y fecha de firma.
- **Ask the user for**: datos fiscales del cliente (CUIT/RUT/RFC según país), domicilio legal, representante que firma.
- **Produce**: contrato firmado guardado en la carpeta del cliente; recordatorio de seguimiento si no se firma en 72 hs.

### Step 3 — Primer cobro (seña / anticipo)
- **Action**: Emitir factura/recibo del anticipo según condiciones del contrato. No habilitar accesos ni kick-off hasta que el pago esté confirmado.
- **Ask the user for**: porcentaje o monto del anticipo, medio de pago (transferencia, Stripe, MercadoPago, etc.), datos de facturación.
- **Produce**: comprobante de cobro registrado y confirmación al cliente del recibo del pago.

### Step 4 — Accesos en LastPass
- **Action**: Crear carpeta del cliente en LastPass con la nomenclatura estándar `Clientes/[Nombre Cliente]`. Cargar credenciales que el cliente entregue (web, hosting, redes, herramientas) y compartir solo con el equipo asignado al proyecto.
- **Ask the user for**: lista de accesos que el cliente debe entregar, miembros del equipo interno que necesitan acceso.
- **Produce**: carpeta LastPass creada y poblada; checklist de accesos pendientes que el cliente todavía no entregó.

### Step 5 — Carpetas y estructura documental
- **Action**: Crear estructura estándar en Google Drive: `01_Comercial`, `02_Contrato`, `03_Kick-off`, `04_Entregables`, `05_Reuniones`, `06_Facturación`. Mover propuesta y contrato a sus carpetas correspondientes.
- **Ask the user for**: nombre exacto del cliente para nombrar la carpeta raíz, si comparte con el cliente o solo interno.
- **Produce**: carpeta raíz del cliente con subcarpetas creadas y permisos configurados.

### Step 6 — Calendario interno y kick-off
- **Action**: Agendar el kick-off con el cliente (60–90 min) y bloquear hitos clave del proyecto en el calendario interno (entregas, revisiones, cierre). Enviar invitación con agenda al cliente.
- **Ask the user for**: disponibilidad propia y del cliente, asistentes obligatorios, modalidad (presencial/Meet/Zoom).
- **Produce**: evento de kick-off confirmado con agenda adjunta y bloqueos de tiempo internos en el calendario.

### Step 7 — Cierre del onboarding
- **Action**: Generar el resumen del onboarding y confirmar al cliente por escrito (mail) que todo quedó listo para arrancar. Encadenar con `skill_planificacion_proyecto`.
- **Produce**: mail de bienvenida + checklist de onboarding marcado como completado.

## Output
Un **kit de onboarding cerrado** que incluye:
- Ficha del cliente completa
- Contrato firmado archivado
- Comprobante de primer cobro
- Carpeta LastPass con accesos
- Estructura de carpetas en Drive
- Evento de kick-off agendado con agenda
- Mail de bienvenida enviado
- Checklist de onboarding 100% completo

Más un **listado de pendientes del cliente** (accesos o datos faltantes) si los hay.

## Key consulting principles applied
- **No empezar a entregar sin cobrar**: el anticipo es condición de inicio, no negociable.
- **Documentar antes de hacer**: contrato firmado y carpetas creadas antes que cualquier trabajo operativo.
- **Accesos centralizados**: nada de credenciales sueltas en mails o WhatsApp — todo en LastPass.
- **Kick-off como contrato emocional**: alinea expectativas, alcance y forma de trabajo desde el día uno.
- **Secuencia estricta**: cada paso destraba al siguiente; saltar pasos genera deuda operativa.

## Chains with
- skill_contrato: cuando aún no existe contrato formal y hay que generarlo antes del Step 2.
- skill_planificacion_proyecto: inmediatamente después del kick-off, para definir cronograma y entregables detallados.
- skill_delivery: una vez completado el onboarding y la planificación, para arrancar la ejecución.

## Templates used
- Checklist de onboarding → `templates/checklist_onboarding.md`
- Estructura de carpetas estándar → `templates/estructura_carpetas_drive.md`
- Agenda de kick-off → `templates/agenda_kickoff.md`
- Mail de bienvenida → `templates/mail_bienvenida.md`

## Source modules
modulo6
