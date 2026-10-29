# Skill: Productividad 50/50 del consultor

## What this does
Audita el uso real del tiempo del consultor, rediseña su semana bajo el principio 50/50 (mitad facturable a clientes, mitad invertido en construir el negocio), y baja eso a un día operable con Top 3 y bloques de foco profundo.

## When to use it
**Activate this skill when the user:**
- Says: "no me alcanza el tiempo", "estoy todo el día apagando incendios", "no tengo tiempo para vender", "trabajo 12 horas y no avanzo"
- Asks to: "ayudame a organizar mi semana", "armemos mi agenda tipo", "necesito priorizar", "cómo bloqueo foco"
- Starts a situation like: procrastinación con tareas comerciales, semana 100% reactiva al cliente, sensación de estar saturado sin facturar más, arranque de lunes sin claridad
- Says: "tengo que hacer mil cosas y no sé por dónde empezar"
- Says: "siempre termino postergando lo de mi propio negocio"
- Asks: "cómo divido tiempo entre clientes y crecer"

## How to execute

### Step 1 — Auditoría de tiempo real (últimos 7 días)
- **Action**: Pedir al consultor que reconstruya la última semana hábil hora por hora, agrupando por entregable/cliente, no por "tareas sueltas".
- **Ask the user for**: lista de clientes activos, entregables comprometidos esta semana, horas estimadas dedicadas a cada uno, horas dedicadas a su propio negocio (marketing, ventas, operaciones internas, formación), horas perdidas en interrupciones.
- **Produce**: tabla con columnas `Categoría | Actividad | Horas reales | % del total`. Calcular ratio Cliente vs Negocio vs Pérdida.

### Step 2 — Diagnóstico del desbalance
- **Action**: Comparar el ratio real contra el objetivo 50/50 y marcar las 2-3 fugas principales (reuniones sin agenda, retrabajos, clientes fuera de scope, ausencia de bloques propios).
- **Ask the user for**: cuáles de esas tareas son delegables, automatizables, eliminables o renegociables con el cliente.
- **Produce**: diagnóstico breve (5-7 líneas) con el gap entre estado actual y 50/50, y las causas raíz.

### Step 3 — Diseño de la semana tipo 50/50
- **Action**: Construir una grilla semanal (Lun-Vie) que reserve aproximadamente 50% a entrega de cliente y 50% a construir el negocio (prospección, contenido, sistemas, formación, descanso estratégico).
- **Ask the user for**: horarios de mayor energía cognitiva, días con reuniones fijas de cliente, compromisos personales innegociables.
- **Produce**: agenda tipo en bloques de 90-120 min, etiquetando cada bloque como `[CLIENTE]`, `[NEGOCIO]`, `[FOCO PROFUNDO]`, `[ADMIN]`, `[BUFFER]`.

### Step 4 — Top 3 diario y regla del foco profundo
- **Action**: Definir el método del Top 3: cada noche o primera hora del día, el consultor elige las 3 tareas que, si solo hace esas, el día fue exitoso. Una de las 3 debe ser de la columna NEGOCIO.
- **Ask the user for**: contexto del día siguiente (entregas, reuniones, deadlines).
- **Produce**: plantilla diaria con `Top 3`, `Bloque foco profundo (90-120 min sin notificaciones)`, `Bloque admin (email, mensajes, coordinación)`.

### Step 5 — Reglas anti-procrastinación y rituales de cierre
- **Action**: Instalar 3-5 reglas operativas: no abrir email antes del primer bloque de foco, reuniones solo en franja designada, cierre de día con revisión de Top 3 + planificación del siguiente, viernes con bloque de revisión semanal 50/50.
- **Produce**: lista corta de reglas pegables al monitor.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_productividad/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Métrica de seguimiento
- **Action**: Definir 1 sola métrica semanal: `% real de horas en bloques NEGOCIO vs CLIENTE`. El consultor la registra cada viernes.
- **Produce**: mini-dashboard simple (puede ser una fila en Sheets o Notion) para trackear 4 semanas.

## Output
Documento entregable que contiene:
1. Tabla de auditoría de la última semana.
2. Diagnóstico del desbalance (5-7 líneas).
3. Grilla semanal tipo 50/50 (Lun a Vie, por bloques).
4. Plantilla del Top 3 diario + bloque de foco profundo.
5. Reglas operativas anti-procrastinación.
6. Métrica semanal de seguimiento y cómo registrarla.

## Key consulting principles applied
- Principio 50/50: la mitad del tiempo se entrega, la mitad se construye negocio. Sin la segunda mitad, no hay crecimiento.
- El tiempo se audita por entregable, no por tarea suelta — así se ve qué cliente o servicio drena horas no facturadas.
- Foco profundo en bloques de 90-120 min: el trabajo de alto valor (estrategia, propuestas, contenido) no sobrevive en multitasking.
- Top 3 diario fuerza priorización real; lo demás es ruido administrable.
- Lo que no se mide, no se mejora: una sola métrica semanal alcanza para corregir rumbo.

## Chains with
- skill_equipo_proveedores: cuando la auditoría revela tareas delegables que justifican incorporar VA, freelancer o proveedor para liberar horas de cliente.
- skill_planificacion_proyecto: cuando los bloques `[CLIENTE]` necesitan estructurarse como proyectos con hitos, no como horas sueltas que se desbordan.

## Templates used
- **PLANTILLA - To-do.xlsx** → ./skill_productividad/PLANTILLA - To-do.xlsx — Hoja de cálculo para listar tareas pendientes, priorizar el Top 3 diario y trackear bloques de foco a lo largo de la semana.

## Source modules
modulo11
