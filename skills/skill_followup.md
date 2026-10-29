# Skill: Follow-up y reconversión de leads

## What this does
Guía al consultor a sostener cada oportunidad abierta con un máximo de dos contactos de seguimiento, reconvertir los "no" en referidos calificados y medir el ratio de aceptación para iterar oferta, audiencia o precio.

## When to use it
**Activate this skill when the user:**
- Says: "tengo que hacer seguimiento a una propuesta que mandé"
- Says: "el cliente no me contesta hace varios días"
- Says: "quiero reactivar prospectos viejos / leads fríos"
- Asks to: "armame un mensaje de follow-up para X"
- Asks to: "calculá mi ratio de cierre y decime qué ajustar"
- Starts a situation like: "me dijeron que no, ¿qué hago?"
- Starts a situation like: "mandé la propuesta el lunes y silencio"
- Says: "no sé cuándo dar por perdido a un prospecto"

## How to execute

### Step 1 — Inventariar oportunidades abiertas y clasificarlas
- **Action**: Pedir el listado de prospectos pendientes y clasificarlos por estado: (a) propuesta enviada sin respuesta, (b) reunión pendiente de agendar, (c) "no" reciente, (d) lead frío >60 días.
- **Ask the user for**: nombre del prospecto, fecha del último contacto, canal (email/WhatsApp/Loom), última acción del consultor, monto estimado de la propuesta.
- **Produce**: tabla con columnas: prospecto | estado | días desde último contacto | próximo paso sugerido | contacto # (1 o 2).

### Step 2 — Definir la cadencia de máximo dos contactos
- **Action**: Para cada oportunidad, asignar contacto #1 (a los 3-5 días hábiles del envío) o contacto #2 (a los 7-10 días del contacto #1). Si ya se hicieron los dos, marcar como "cerrar y reconvertir".
- **Ask the user for**: confirmar fechas reales y si hubo apertura del Loom o lectura del mensaje.
- **Produce**: cronograma de envíos con día y hora exactos para cada follow-up, agrupados por canal.

### Step 3 — Redactar el mensaje de seguimiento sin perder postura
- **Action**: Escribir un mensaje breve (3-5 líneas) que aporte valor (un dato del diagnóstico, un caso, una métrica del rubro) antes de pedir respuesta. Nunca rebajar precio ni cambiar la oferta en el follow-up. Tono cordial, postura firme, deadline implícito.
- **Ask the user for**: detalle de la propuesta enviada y un dato/insight reciente del rubro del prospecto.
- **Produce**: dos versiones del mensaje (contacto #1 más informativo, contacto #2 más directo con cierre tipo "¿lo dejamos en pausa o avanzamos esta semana?").

### Step 4 — Cierre claro y liberación de agenda
- **Action**: Tras el contacto #2 sin respuesta, enviar un "breakup message" que cierra la conversación de forma elegante y libera la agenda. Pedir feedback honesto a los "no" explícitos para detectar si la objeción fue precio, timing, alcance o decisor.
- **Ask the user for**: confirmación de cuáles prospectos pasan a estado "perdido".
- **Produce**: mensaje de cierre + ficha de feedback (motivo del no, en una línea) por cada prospecto descartado.

### Step 5 — Reconvertir el "no" en referido
- **Action**: A cada "no" claro, enviar pedido de referido en el mismo hilo: "¿conocés a alguien en tu red para quien esto sí encaje?". Ofrecer incentivo blando (sesión de diagnóstico gratis para el referido, o % de fee si aplica). Mantener al prospecto en una lista de nurturing para reactivar a los 90 días con contenido, no con venta.
- **Ask the user for**: si tiene programa de referidos vigente o hay que armar uno simple para esta gestión.
- **Produce**: mensaje de pedido de referido + lista de nurturing 90 días con fecha de próxima reactivación.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_followup/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Calcular ratio y diagnosticar qué ajustar
- **Action**: Sumar propuestas enviadas vs. aprobadas en los últimos 30-90 días. Comparar contra benchmark 3/7 (42%). Si <42%, recomendar ajuste en este orden estricto: audiencia → oferta → precio (nunca al revés). Si >70%, recomendar subir precio o escalar capacidad.
- **Ask the user for**: total de propuestas enviadas y cerradas en el período.
- **Produce**: número de ratio actual + diagnóstico de qué palanca tocar primero + 1-2 hipótesis concretas de ajuste.

## Output
Un documento de seguimiento que incluye: (1) tabla de oportunidades abiertas con próximo paso y fecha, (2) mensajes listos para copiar/pegar para contacto #1, contacto #2 y cierre, (3) mensaje de pedido de referido, (4) lista de nurturing a 90 días, (5) ratio de cierre actualizado con diagnóstico de ajuste.

## Key consulting principles applied
- Máximo dos contactos de seguimiento: más insistencia quema marca y postura.
- Un "no" claro libera agenda; el silencio prolongado la consume sin retorno.
- En follow-up no se baja precio: si hay que mover algo, se reduce alcance (ver skill_negociacion).
- El "no" es materia prima: siempre pedir feedback y referido antes de cerrar el hilo.
- Validación del servicio es un número (3/7 = 42%), no una sensación.
- Si el ratio cae, ajustar audiencia → oferta → precio, en ese orden, nunca al revés.
- Aportar valor antes de pedir respuesta: cada follow-up debe dejar algo útil al prospecto.

## Chains with
- skill_negociacion: cuando el follow-up genera respuesta con objeción de precio o alcance, encadenar para defender tarifa bajando entregables, no la tarifa.
- skill_captacion: cuando el ratio queda <42% y el diagnóstico apunta a "audiencia", encadenar para revisar el perfil de prospecto que se está atrayendo y los canales de captación.

## Templates used
- **PLANTILLA ADC - Seguimiento de prospectos.xlsx** → ./skill_followup/PLANTILLA ADC - Seguimiento de prospectos.xlsx — planilla maestra para inventariar prospectos abiertos, registrar fechas de contacto #1 y #2, motivos de "no" y calcular el ratio de cierre.

## Source modules
modulo5, modulo3
