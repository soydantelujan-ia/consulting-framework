# Skill: Plan de contenidos y MAC

## What this does
Guía al consultor a construir un calendario editorial con las 4 áreas del MAC (Historias, Educación, Ayuda, Convencimiento) y a multiplicar cada activo madre en piezas derivadas (video → podcast → artículo → reel → carrusel) para sostener autoridad inbound sin quemarse produciendo.

## When to use it
**Activate this skill when the user:**
- Says: "no sé qué publicar esta semana"
- Says: "necesito armar un plan de contenidos / calendario editorial para mí o mi cliente"
- Asks to: "reutilizar / multiplicar / reciclar el contenido que ya grabé"
- Asks to: "armar píldoras de video de menos de 1 minuto"
- Starts a situation like: "estoy publicando en LinkedIn pero no genera nada, ¿qué cambio?"
- Starts a situation like: "tengo una entrevista / webinar grabado y no sé cómo bajarlo a redes"
- Says: "qué publico en Instagram además de tips"
- Says: "quiero un sistema para no improvisar el contenido cada semana"

## How to execute

### Step 1 — Anclar posicionamiento y objetivo del contenido
- **Action**: Antes de planificar, confirmar que existe un eje de posicionamiento (horizontal × vertical) y un pitch 7P. Si no existen, derivar a `skill_marca_personal` y volver. Si existen, traerlos a la conversación como filtro de pertinencia: todo lo que se publique debe reforzar ese eje, no temas de moda.
- **Ask the user for**: frase de posicionamiento, cliente ideal vertical, metodología propia con nombre, y objetivo SMART del trimestre (autoridad, leads, ventas, eventos).
- **Produce**: Una "regla del filtro" en una línea: "Solo publico contenido que demuestre [diferenciador] para [vertical] y empuje hacia [objetivo SMART]".

### Step 2 — Mapear los 4 pilares del MAC
- **Action**: Distribuir los temas en las 4 áreas mínimas, cubriendo las 9 piezas base: Historias (video "mi por qué", entrevistas, apariciones en medios), Educación (video educativo, artículo, podcast), Ayuda (descargable / quiz / tutoriales / respuestas en Quora-YouTube), Convencimiento (testimonios, casos de éxito, webinars). Cada pilar debe tener al menos 5 ideas concretas de contenido vinculadas al pitch 7P (problema externo, problema interno, plan, éxito/tragedia).
- **Ask the user for**: dolores frecuentes del cliente, casos de éxito disponibles, materiales ya grabados, eventos próximos, lead magnets activos.
- **Produce**: Tabla de 4 columnas × ≥5 filas con ideas tageadas por pilar, formato sugerido y CTA.

### Step 3 — Diseñar el activo madre semanal (pilar de contenido)
- **Action**: Definir UNA pieza ancla por semana — usualmente video largo o entrevista de 15-30 min — sobre la especialidad real (no temas de moda). Ese activo madre es la materia prima de todo lo demás. Dejar agendada la grabación en bloque mensual (4 piezas en una sesión).
- **Ask the user for**: capacidad real de producción (cámara, edición, tiempo), formato preferido (video, audio, texto), día y hora de grabación.
- **Produce**: Calendario de grabación mensual + brief del activo madre de la semana 1 (título, hook, 3 puntos clave, CTA al lead magnet).

### Step 4 — Multiplicar el activo madre en piezas derivadas
- **Action**: Aplicar la cadena de multiplicación sobre cada activo madre:
  - Video largo → episodio de podcast (audio).
  - Transcripción → artículo de blog SEO + post de LinkedIn largo.
  - Mejores 30-59 segundos → 2-4 píldoras de reel/short/TikTok con subtítulos.
  - Frases potentes → 1 carrusel + 2-3 quotes para Instagram/X.
  - Pregunta del activo → 1 respuesta en Quora / comentarios en YouTube.
  - Insight clave → idea de lead magnet o nuevo correo a la lista.
  Cada derivado lleva CTA al lead magnet (link en primer comentario, no dentro del post).
- **Ask the user for**: canales activos y prioritarios (default: LinkedIn + Instagram como ejes).
- **Produce**: Lista de 8-12 piezas derivadas por activo madre, con canal, formato, hook y CTA.

### Step 5 — Armar el calendario editorial vivo
- **Action**: Volcar todo en un calendario semanal con cadencia mínima sostenible: 1 píldora educativa ≤59s por semana, 2-3 posts de pilares mixtos, 3-5 historias diarias en Instagram, 1 envío a la lista cada 2 semanas. Etiquetar cada slot con pilar MAC, formato, canal, estado (idea / grabado / editado / publicado) y carta de hashtags (3-4 principales + 10-20 secundarios + 5-6 branded).
- **Ask the user for**: días/horarios de mejor performance históricos, herramienta de scheduling (Notion, Metricool, Later, Sheet).
- **Produce**: Calendario editorial de 4 semanas listo para ejecutar + biblioteca de hashtags por pilar.

### Step 6 — Definir métricas y ritual de iteración
- **Action**: Cerrar el ciclo con medición. Cada mes: identificar la pieza ganadora, producir su versión A/B con un cambio claro (hook, formato, subtítulos, voz en off), invertir ≥20 USD de pauta por versión, reportar y consolidar la ganadora como contenido de autoridad evergreen. Registrar qué pilar MAC tracciona más y rebalancear el siguiente mes.
- **Ask the user for**: métrica norte (leads capturados, agendamientos, alcance, guardados).
- **Produce**: Tablero mensual con KPI por pilar + decisión de iteración del mes siguiente.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_contenido/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

## Output
Un paquete editorial accionable que incluye: (1) regla del filtro de posicionamiento, (2) mapa MAC con 4 pilares × ≥5 ideas, (3) plan mensual de activos madre, (4) cadena de multiplicación con 8-12 derivados por activo, (5) calendario editorial de 4 semanas con canales/hashtags/CTA, y (6) tablero de KPI con ritual mensual de A/B testing.

## Key consulting principles applied
- **Educar antes de vender**: la mayoría del calendario es Educación + Ayuda; Convencimiento aparece dosificado.
- **Especificidad gana**: el contenido habla de la especialidad real, nunca de temas de moda genéricos.
- **Coherencia omnicanal**: un solo concepto, lenguajes adaptados a cada red.
- **Show, don't tell**: cada pilar exige pruebas (casos, números, hitos) sobre adjetivos.
- **Constancia × Interés × Relaciones**: cadencia sostenible vence a sprints de volumen.
- **CTA siempre a captura, nunca a "contactar"**: todo derivado empuja al lead magnet.
- **Activo madre primero**: producir en bloque y multiplicar, no improvisar pieza por pieza.

## Chains with
- skill_marca_personal: prerequisito — sin posicionamiento + pitch 7P, el calendario no tiene filtro y se vuelve ruido.
- skill_lead_magnet: cada pieza derivada necesita un soborno ético al cual apuntar; si el lead magnet es genérico, el contenido no convierte.
- skill_captacion: el contenido alimenta el top of funnel inbound; coordinar con la estrategia de captación para que los CTAs y la pauta de A/B empujen al embudo correcto.

## Templates used
- **CALENDARIO DE CONTENIDOS INSTAGRAM.xls** → ./skill_contenido/CALENDARIO DE CONTENIDOS INSTAGRAM.xls — Grilla mensual específica para planificar feed y stories de Instagram con pilar, formato y CTA por slot.
- **MEGA PLANTILLA - Plan de marketing (Presentación).pptx** → ./skill_contenido/MEGA PLANTILLA - Plan de marketing (Presentación).pptx — Plan de marketing integral en formato presentación para encuadrar el contenido dentro de la estrategia comercial del cliente.
- **PLANTILLA _ CALENDARIO DE PLANIFICACIÓN DE CONTENIDOS.xlsx** → ./skill_contenido/PLANTILLA _ CALENDARIO DE PLANIFICACIÓN DE CONTENIDOS.xlsx — Calendario editorial multicanal con estado (idea/grabado/editado/publicado), pilar MAC y hashtags por pieza.
- **PLANTILLA para guiones.docx** → ./skill_contenido/PLANTILLA para guiones.docx — Estructura de guion para activo madre y píldoras (hook, 3 puntos clave, CTA al lead magnet).
- **Plantilla Plan de Social Media.pptx** → ./skill_contenido/Plantilla Plan de Social Media.pptx — Plan de social media presentable para cliente, con objetivos, pilares, cadencia y KPIs por canal.

## Source modules
modulo4, modulo12
