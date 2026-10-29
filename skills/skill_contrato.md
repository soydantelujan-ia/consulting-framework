# Skill: Contrato, NDA y cobro inicial

## What this does
Guía al agente para producir un paquete legal-comercial blindado: contrato de consultoría con cláusulas críticas, NDA anexo, cálculo y cobro de anticipo (30-50%) y entrega de enlaces de pago listos para que el cliente firme y pague el mismo día.

## When to use it
**Activate this skill when the user:**
- Says: "necesito redactar el contrato para [cliente]"
- Says: "armame el NDA para mandarle antes de la reunión"
- Asks to: "cobrar el anticipo de [cliente]" o "generá los enlaces de pago"
- Says: "blindemos este acuerdo antes de arrancar"
- Says: "el cliente ya aceptó la propuesta, ¿qué le mando para firmar?"
- Starts a situation like: propuesta aprobada verbalmente y necesita formalizar antes de empezar a trabajar
- Says: "tengo miedo de que este cliente me corra con los pagos / me copie la metodología"
- Asks to: "incluir cláusula de mora / permanencia / propiedad intelectual"

## How to execute

### Step 1 — Levantar datos del acuerdo cerrado
- **Action**: Reconstruir el acuerdo a partir de la propuesta aprobada (no improvisar términos nuevos). Si la skill_negociacion ya corrió, tomá de ahí: alcance final, precio, plazos en mes 1/mes 2/mes 3, condiciones que se endurecieron a cambio de descuentos.
- **Ask the user for**:
  - Razón social y datos fiscales del cliente (CUIT/RFC/NIT, domicilio, representante legal)
  - Razón social y datos fiscales del consultor
  - Monto total cerrado y modalidad (único / fraccionado / fee + comisión / recurrente)
  - Alcance final exacto (qué SÍ entra y qué NO — confirmá ambos)
  - Duración del servicio y permanencia mínima si aplica
  - Sensibilidad de la información que va a compartir el cliente (¿requiere NDA reforzado?)
- **Produce**: Ficha interna con todos los campos para popular las plantillas, sin huecos.

### Step 2 — Redactar el contrato de consultoría con cláusulas críticas
- **Action**: Generar el contrato con TODAS estas cláusulas — son no negociables porque protegen al consultor:
  1. **Objeto y alcance**: copiar literal el alcance recortado (A, B) y listar explícitamente los add-ons (C, D) con su precio aparte.
  2. **Honorarios y forma de pago**: monto total, anticipo del 30-50% como condición de inicio, cronograma de pagos vinculado a entregables (mes 1 / mes 2 / mes 3, nunca fechas de calendario).
  3. **Mora**: interés diario por atraso + suspensión automática del servicio a los X días de impago. "Tiene que dolernos a los dos."
  4. **Revisión de tarifas**: ajuste periódico (anual o por inflación) en contratos recurrentes.
  5. **Permanencia mínima** (si hay fee recurrente): cuántos meses, penalidad por salida anticipada.
  6. **Propiedad intelectual**: la metodología, fórmulas y plantillas son del consultor; los entregables finales se ceden al cliente RECIÉN tras pago total.
  7. **Confidencialidad**: remite al NDA anexo.
  8. **Requerimientos al cliente**: qué tiene que entregar (accesos, información, responsable asignado) y consecuencia si no lo hace (replanificación + cargo).
  9. **Limitación de responsabilidad**: el consultor no garantiza resultados específicos sin 30 días de data; el tope de responsabilidad es el monto cobrado.
  10. **Causales de rescisión** y jurisdicción.
- **Ask the user for**: confirmación del % de anticipo (default 30%, recomendar 50% si el cliente es nuevo o el riesgo es alto).
- **Produce**: Contrato listo para firmar, en formato vertical, sin huecos ni "[completar]".

### Step 3 — Anexar NDA proporcional al riesgo
- **Action**: Generar NDA como anexo del contrato (no documento suelto). Calibrar dureza:
  - **NDA estándar**: definición de info confidencial, obligación de no divulgar, vigencia (típico 2-5 años post-contrato), excepciones (info pública, requerida por ley).
  - **NDA reforzado** (si el cliente comparte data sensible: financiera, clientes finales, código): sumar cláusula penal por incumplimiento, devolución/destrucción de info al cierre, no-solicitación de empleados/clientes.
- **Ask the user for**: si necesita NDA bilateral (ambas partes protegidas) o unilateral (solo el cliente protege su info).
- **Produce**: NDA anexo, coherente con el contrato (mismas partes, misma jurisdicción).

### Step 4 — Configurar cobro y enlaces de pago
- **Action**: Antes de enviar el contrato, dejar listos los 3 enlaces en Thrivecart (o pasarela equivalente):
  - **Único**: pago total con descuento por pronto pago (opcional 5-10%).
  - **Fraccionado**: anticipo 30-50% + cuotas atadas al cronograma.
  - **Reserva**: solo el anticipo, para bloquear agenda mientras se firma.
- **Ask the user for**: pasarela que usa (Thrivecart, Stripe, Mercado Pago), si quiere ofrecer las 3 opciones o solo una.
- **Produce**: Bloque de email/mensaje con los enlaces listos para pegar, vinculados al contrato.

### Step 5 — Empaquetar envío y disparar firma + cobro
- **Action**: Armar el envío completo en un solo movimiento para que el cliente firme y pague el mismo día (la rapidez multiplica el ratio de cierre).
- **Ask the user for**: vía de envío (DocuSign / firma simple / PDF + email) y si ya tiene fecha de kickoff tentativa.
- **Produce**:
  - Email/mensaje de envío con: contrato + NDA anexos, enlace de pago del anticipo, fecha tentativa de inicio CONDICIONADA a recepción de firma + anticipo, próximo paso (kickoff / onboarding).
  - Recordatorio interno al consultor: NO empezar a trabajar hasta que el anticipo esté acreditado.

### Step 6 — Checklist de cierre legal
- **Action**: Antes de dar el OK al envío, correr checklist:
  - Nombre del cliente correcto en TODO el documento (buscar nombres de clientes anteriores).
  - Montos coinciden entre propuesta, contrato y enlace de pago.
  - Alcance del contrato = alcance final negociado (sin agregados ni recortes silenciosos).
  - Datos fiscales completos de ambas partes.
  - Fechas en formato mes 1 / mes 2 / mes 3, no calendario.
  - NDA anexado y referenciado en el contrato.
  - Enlace de pago testeado (abre, monto correcto, moneda correcta).
- **Produce**: GO/NO-GO para envío.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_contrato/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow). En este caso son DOS archivos: el contrato y el NDA — generá ambos.
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

## Output
Paquete legal-comercial completo:
1. **Contrato de consultoría** (PDF, vertical, listo para firmar) con las 10 cláusulas críticas.
2. **NDA anexo** (estándar o reforzado según riesgo).
3. **Enlaces de pago** (1-3 opciones en Thrivecart o equivalente) con anticipo 30-50% bloqueado como condición de inicio.
4. **Email de envío** con el paquete y el próximo paso (kickoff condicionado al pago).
5. **Checklist firmado** internamente confirmando que el envío está blindado.

## Key consulting principles applied
- "Tiene que dolernos a los dos": anticipo + permanencia + mora alinean compromiso del cliente.
- No se empieza a trabajar sin anticipo acreditado — política, no excepción.
- La metodología y las fórmulas son del consultor; los entregables se ceden contra pago total.
- Rapidez en el envío (mismo día del SÍ) multiplica el cierre efectivo.
- El contrato refleja el alcance recortado de la negociación: no se cuelan entregables nuevos "de onda".
- Sin garantía de resultados específicos antes de tener 30 días de data.
- El checklist físico/digital previo al envío es obligatorio: errores de nombre o monto matan credibilidad.

## Chains with
- skill_negociacion: corre antes — define alcance final, precio defendido y condiciones endurecidas que esta skill traduce en cláusulas.
- skill_onboarding: corre después — arranca SOLO cuando el anticipo está acreditado y el contrato firmado; usa los requerimientos al cliente del contrato como input.

## Templates used
- **NDA - Acuerdo de Confidencialidad.docx** → ./skill_contrato/NDA - Acuerdo de Confidencialidad.docx — Modelo de NDA listo para anexar al contrato; cubre definición de información confidencial, obligaciones de no divulgación, vigencia y excepciones.
- **Plantilla+Contrato+Consultoría+Estratégica (1).docx** → ./skill_contrato/Plantilla+Contrato+Consultoría+Estratégica (1).docx — Plantilla base del contrato de consultoría estratégica en formato vertical, para popular con las 10 cláusulas críticas (objeto, honorarios, mora, permanencia, propiedad intelectual, limitación de responsabilidad, etc.).

## Source modules
modulo3, modulo5, modulo6
