# Skill: Planificación dual del proyecto

## What this does
Construye, para cada cliente, un plan dual que combina el plano financiero (presupuesto, costes directos/indirectos, margen objetivo, flujo de cobros) con el plano operativo (hitos, entregables, dependencias, responsables y riesgos), de modo que el consultor pueda comprometer fechas y rentabilidad antes de arrancar el delivery.

## When to use it
**Activate this skill when the user:**
- Says: "armame el plan del proyecto de [cliente]"
- Says: "necesito el cronograma con hitos para [cliente]"
- Asks to: "calcular el presupuesto y margen de este proyecto"
- Asks to: "definir entregables, fechas y dependencias"
- Starts a situation like: "ya cerré la propuesta con [cliente], ¿cómo lo planifico?"
- Starts a situation like: "tengo dudas si este proyecto me va a dar rentabilidad"
- Says: "hagamos el plan operativo y financiero antes de arrancar"
- Says: "revisemos riesgos y plan B del proyecto de [cliente]"

## How to execute

### Step 1 — Confirmar alcance y supuestos
- **Action**: Releer la propuesta firmada o el resumen comercial del cliente. Listar objetivos, entregables comprometidos, fecha de inicio y fecha límite. Marcar supuestos no validados.
- **Ask the user for**: nombre del cliente, copia/resumen de la propuesta aceptada, fecha de kickoff, fecha tope, tarifa acordada y forma de cobro.
- **Produce**: ficha de alcance con objetivos, entregables, fechas marco y supuestos a validar.

### Step 2 — Plan financiero
- **Action**: Calcular presupuesto total, costes directos (horas propias, freelancers, herramientas, APIs, licencias), costes indirectos (overhead estimado), margen bruto y margen neto objetivo. Construir cronograma de cobros (anticipo, hitos, final) y proyectar flujo de caja del proyecto.
- **Ask the user for**: tarifa hora propia, costes de terceros conocidos, % de overhead que usa, margen mínimo aceptable, condiciones de pago acordadas.
- **Produce**: tabla de presupuesto con ingresos, costes, margen $ y %, y calendario de cobros con fechas estimadas.

### Step 3 — Plan operativo (WBS + hitos)
- **Action**: Descomponer el alcance en fases y entregables. Para cada entregable definir: tareas, responsable, esfuerzo estimado en horas, dependencias (qué bloquea a qué), fecha de inicio y fin. Marcar hitos visibles para el cliente (milestones de cobro y de validación).
- **Ask the user for**: equipo disponible y disponibilidad semanal, herramientas que ya usa para tracking (Asana, Notion, etc.).
- **Produce**: cronograma con fases, entregables, responsables, fechas e hitos de cliente claramente identificados.

### Step 4 — Riesgos y plan B
- **Action**: Identificar 4-8 riesgos concretos del proyecto (técnicos, de cliente, de equipo, de scope creep, de cobro). Para cada uno: probabilidad (alta/media/baja), impacto, señal temprana de alerta y mitigación o plan B.
- **Ask the user for**: experiencias pasadas con clientes parecidos, dependencias críticas que ya detecta.
- **Produce**: matriz de riesgos priorizada con mitigaciones accionables.

### Step 5 — Validación cruzada financiero ↔ operativo
- **Action**: Cruzar horas planificadas × tarifa contra el presupuesto. Si el margen real proyectado cae por debajo del mínimo, alertar y proponer ajustes (recortar alcance, subir precio, reasignar recursos, mover hitos). No avanzar sin que ambos planos cierren.
- **Ask the user for**: confirmación de qué palanca prefiere mover si hay desajuste.
- **Produce**: semáforo de salud del proyecto (verde/amarillo/rojo) con recomendación.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_planificacion_proyecto/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Consolidar entregable y próximos pasos
- **Action**: Unificar todo en un único documento maestro del proyecto. Sugerir cargar hitos y tareas en la herramienta de gestión que use el consultor (encadenar con skill_onboarding si aún no se hizo el kickoff).
- **Produce**: documento "Plan de Proyecto — [Cliente]" listo para compartir internamente y para basar el kickoff.

## Output
Un documento estructurado por cliente con seis bloques: (1) Ficha de alcance y supuestos, (2) Plan financiero con tabla de presupuesto y calendario de cobros, (3) Cronograma operativo con WBS, hitos y responsables, (4) Matriz de riesgos con mitigaciones, (5) Validación cruzada y semáforo de salud, (6) Próximos pasos accionables. Pensado para servir como fuente única de verdad durante todo el delivery.

## Key consulting principles applied
- Ningún proyecto arranca sin plan financiero y plan operativo cerrados en simultáneo.
- El margen se diseña antes, no se descubre después.
- Los hitos del cliente coinciden con hitos de cobro siempre que se pueda.
- Los riesgos se nombran al inicio: lo que no se anticipa, se sufre.
- Si el cruce horas × tarifa rompe el margen mínimo, se ajusta alcance, precio o recursos — nunca se absorbe en silencio.

## Chains with
- skill_onboarding: una vez aprobado el plan, alimenta el kickoff y la configuración inicial con el cliente.
- skill_delivery: el cronograma e hitos de esta skill son la línea base que delivery ejecuta y monitorea.
- skill_finanzas: el calendario de cobros y el presupuesto se sincronizan con el control financiero global del consultor.

## Templates used
- **PLANTILLA ADC - Presupuesto.xlsx** → ./skill_planificacion_proyecto/PLANTILLA ADC - Presupuesto.xlsx — Plantilla propia de ADC para armar el presupuesto del proyecto con costes directos, indirectos, ingresos y margen objetivo.
- **PLANTILLA-BUDGET-PLANNING-WORKSHEET.xlsx** → ./skill_planificacion_proyecto/PLANTILLA-BUDGET-PLANNING-WORKSHEET.xlsx — Hoja de trabajo para planificación financiera detallada del proyecto y proyección del flujo de cobros por hito.
- **PLANTILLA-PROJECT-PLANNING-TOOL.xlsx** → ./skill_planificacion_proyecto/PLANTILLA-PROJECT-PLANNING-TOOL.xlsx — Herramienta de planificación operativa para armar WBS, hitos, dependencias, responsables y cronograma del proyecto.

## Source modules
modulo6, modulo11
