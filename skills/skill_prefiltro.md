# Skill: Pre-cualificar prospectos

## What this does
Diseña un formulario de prefiltro con scoring, anclaje de precio, identificación de decisor y peor escenario para filtrar prospectos antes de invertir tiempo en una call de descubrimiento.

## When to use it
**Activate this skill when the user:**
- Says: "estoy perdiendo tiempo con clientes que no compran"
- Says: "necesito filtrar los leads antes de la reunión"
- Asks to: "armar un formulario de calificación"
- Asks to: "diseñar un scoring para prospectos"
- Starts a situation like: "tuve tres calls esta semana y ninguno tenía presupuesto"
- Starts a situation like: "me llegan muchos leads del lead magnet pero la mayoría no califica"
- Says: "cómo evito clientes tóxicos"
- Says: "quiero un cuestionario antes de agendar"

## How to execute

### Step 1 — Diagnóstico del perfil ideal y tóxico
- **Action**: Antes de diseñar preguntas, alinear con el consultor sobre a quién quiere atraer y a quién quiere descartar.
- **Ask the user for**:
  - Servicio/oferta principal y ticket promedio.
  - Características del cliente ideal (industria, tamaño, madurez digital, urgencia).
  - Señales de cliente tóxico que ya vivió (regateo, micromanagement, expectativas irreales, sin decisor, sin presupuesto).
  - Capacidad mensual de nuevos clientes.
- **Produce**: Perfil ICP + lista de señales rojas concretas.

### Step 2 — Definir las 4 dimensiones de calificación
- **Action**: Mapear preguntas alrededor de los 4 ejes críticos: **Presupuesto (anclaje de precio)**, **Autoridad (decisor)**, **Necesidad (dolor real)** y **Tiempo (urgencia)** — más una quinta de **Peor escenario** para detectar expectativas tóxicas.
- **Produce**: Tabla con las 4-5 dimensiones y qué busca medir cada una.

### Step 3 — Redactar el formulario
- **Action**: Escribir entre 7 y 12 preguntas, mezclando opción múltiple (para scoring automático) y abiertas (para leer contexto). Reglas:
  - **Anclaje de precio**: incluir un rango de inversión donde el mínimo sea ~70% del ticket real (ej: "¿Qué presupuesto tienes asignado? a) <USD X b) USD X-Y c) USD Y-Z d) Aún no defino"). Esto filtra y precondiciona.
  - **Decisor**: pregunta directa "¿Eres quien toma la decisión final de contratación? ¿Quién más participa?".
  - **Peor escenario**: "Si no resuelves esto en los próximos 6 meses, ¿qué pasa?" — descarta a quien no tiene dolor real.
  - **Urgencia**: "¿Cuándo necesitas tener esto resuelto?".
  - **Contexto**: facturación, equipo, intentos previos.
- **Produce**: Formulario completo con preguntas, opciones y lógica.

### Step 4 — Diseñar el scoring
- **Action**: Asignar puntos a cada respuesta (0-3 típicamente). Definir umbrales:
  - **>= 80%**: agendar call de descubrimiento directo.
  - **50-79%**: enviar contenido de nutrición + reintento en 30 días.
  - **< 50%**: respuesta automática educativa, no agendar.
- **Produce**: Matriz de scoring + reglas de enrutamiento.

### Step 5 — Definir los siguientes pasos automáticos
- **Action**: Especificar qué pasa después de enviar el formulario para cada tramo de score (email automático, link de calendario, secuencia de nurturing).
- **Produce**: Flujo post-formulario con triggers claros.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_prefiltro/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Recomendar implementación
- **Action**: Sugerir herramienta concreta según el stack del consultor (Tally, Typeform, Google Forms + Zapier, Calendly con preguntas previas). Indicar dónde insertarlo en el funnel (después del lead magnet, antes del calendario).
- **Produce**: Recomendación técnica + ubicación en el funnel.

## Output
Un documento entregable con:
1. Perfil ICP y señales tóxicas.
2. Formulario de prefiltro listo para copiar (preguntas + opciones).
3. Matriz de scoring con puntajes y umbrales.
4. Reglas de enrutamiento por tramo de score.
5. Flujo post-formulario (qué pasa con cada lead).
6. Recomendación de herramienta e implementación.

## Key consulting principles applied
- **Filtrar antes de vender**: el tiempo del consultor es el activo más caro; las calls solo deben ocurrir con prospectos calificados.
- **Anclaje de precio temprano**: el rango de presupuesto en el formulario precondiciona la conversación y descarta regateadores.
- **Calificar sobre dolor, no sobre interés**: el "peor escenario" revela urgencia real.
- **Decisor o no hay reunión**: vender al influenciador prolonga el ciclo y baja la tasa de cierre.
- **Automatizar el descarte**: los leads de bajo score reciben valor (nurturing) sin consumir tiempo humano.

## Chains with
- skill_lead_magnet: el prefiltro va inmediatamente después del lead magnet — quien descarga, recibe el formulario antes de poder agendar.
- skill_sesion_descubrimiento: solo los leads con score alto pasan a la sesión de descubrimiento; el formulario alimenta de contexto previo a esa call.

## Templates used
- **PLANTILLA_ Pre-cualifica clientes.xlsx** → ./skill_prefiltro/PLANTILLA_ Pre-cualifica clientes.xlsx — Planilla base con formulario de prefiltro, matriz de scoring y reglas de enrutamiento por tramo de puntaje.

## Source modules
modulo5, modulo11
