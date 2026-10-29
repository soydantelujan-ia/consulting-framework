# Skill: Diseñar escalera de servicios y customer journey

## What this does
Guía al consultor a diseñar una escalera de 4 escalones de precio con upsells lógicos y un mapa de touchpoints del customer journey (de awareness a recompra), para retener al cliente 9-18 meses en lugar de venderle un solo proyecto.

## When to use it
**Activate this skill when the user:**
- Says: "ya tengo mi servicio estrella, ¿qué le vendo después?"
- Says: "necesito armar mi escalera de servicios / escalera de precios"
- Asks to: "mapear el customer journey de mi cliente"
- Asks to: "diseñar upsells o un mentoring grupal arriba del core offer"
- Starts a situation like: "el cliente termina el proyecto y desaparece, no sé cómo retenerlo"
- Starts a situation like: "vendo un solo servicio y no tengo nada por debajo ni por encima"
- Says: "quiero escalonar mis precios" o "no sé cómo subir el ticket sin perder al cliente"
- Asks to: "armar un funnel desde contenido gratuito hasta high-ticket"

## How to execute

### Step 1 — Validar prerequisitos
- **Action**: Confirmar que el consultor tenga nicho, avatar y servicio estrella ya definidos. Si falta el servicio estrella, derivar a `skill_servicio_estrella` antes de continuar — la escalera se construye alrededor del core offer, no al revés.
- **Ask the user for**: nombre y descripción del servicio estrella, precio actual, avatar (1 frase), transformación que entrega ("paso de X a Y").
- **Produce**: ficha resumen de inputs validados o redirección a la skill previa si falta base.

### Step 2 — Mapear el Customer Journey de 5 etapas
- **Action**: Construir tabla de 5 etapas con touchpoints concretos por etapa: (1) No nos conocen, (2) Conscientes del problema, (3) Conscientes de la solución, (4) Presentación del producto, (5) Compra y recompra.
- **Ask the user for**: canales donde está el avatar (RRSS, podcast, eventos, referidos), contenidos que ya produce, lead magnets existentes.
- **Produce**: tabla Customer Journey con 2-3 touchpoints por etapa (ej: etapa 2 → post de dolor + carrusel + newsletter; etapa 4 → call de diagnóstico + dossier + propuesta).

### Step 3 — Ubicar el servicio estrella en el escalón correcto
- **Action**: Forzar al consultor a colocar el core offer en el escalón 2 (rango 200-1.000 USD o equivalente local). NUNCA en el escalón más bajo. Validar que el precio actual sea coherente con ese rango; si no lo es, marcar como ajuste pendiente.
- **Ask the user for**: precio actual del servicio estrella y rentabilidad estimada.
- **Produce**: confirmación del posicionamiento del core offer + alerta si está mal ubicado.

### Step 4 — Diseñar los 4 escalones de la escalera
- **Action**: Completar los 4 escalones con producto/servicio concreto en cada uno, asegurando que cada escalón sea prerequisito lógico del siguiente:
  - **Escalón 1 (<200)**: ebook, mini-curso, plantilla, masterclass grabada, libro físico → captura y califica.
  - **Escalón 2 (200-1.000) — CORE OFFER**: el servicio estrella ya definido.
  - **Escalón 3 (1.000-3.000)**: fee mensual, formación premium, programa grupal, retainer.
  - **Escalón 4 (top tier)**: mentoring grupal high-ticket, consultoría presencial, intensivos, llave en mano.
- **Ask the user for**: ideas que ya tenga para cada escalón, tiempo disponible para delivery, si quiere o no hacer presencial.
- **Produce**: esquema visual de escalera con nombre, precio, formato y transformación de cada escalón.

### Step 5 — Sembrar semillas de upsell
- **Action**: Para cada escalón, definir qué "semilla" del siguiente escalón se siembra desde la propuesta inicial (ej: dentro del core offer, mencionar el programa grupal como continuidad natural; dentro del escalón 1, ofrecer call de diagnóstico que lleva al escalón 2).
- **Ask the user for**: nada — se deriva del paso 4.
- **Produce**: tabla "Semillas de upsell" con 1 semilla concreta por escalón.

### Step 6 — Definir el filtro del high-ticket (escalón 4)
- **Action**: Si el escalón 4 es mentoring grupal o consultoría premium, diseñar el embudo de calificación: Ads/contenido → webinar 15 min → formulario duro → call de calificación → pago. NUNCA botón "comprar" directo en high-ticket.
- **Ask the user for**: si va a hacer Ads o tráfico orgánico, capacidad de plazas (sugerido 3-8).
- **Produce**: flujo de calificación del top tier en 4-5 pasos.

### Step 7 — Cruzar escalera con customer journey
- **Action**: Combinar los outputs de los pasos 2 y 4 en un único mapa: qué escalón se ofrece en qué etapa del journey, con qué touchpoint y a través de qué contenido.
- **Ask the user for**: nada.
- **Produce**: mapa final integrado escalera × journey.

### Step 8 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos). En esta skill se usan AMBAS plantillas: una para el customer journey (Step 2) y otra para la escalera (Steps 3-5).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_escalera_servicios/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

## Output
Documento "Escalera de Servicios & Customer Journey" con:
1. Tabla del Customer Journey de 5 etapas con touchpoints.
2. Esquema visual de los 4 escalones (precio, nombre, formato, transformación).
3. Tabla de semillas de upsell por escalón.
4. Embudo de calificación del high-ticket (si aplica).
5. Mapa integrado escalera × journey listo para ejecutar marketing y ventas en los próximos 90 días.

## Key consulting principles applied
- **Nunca todos los huevos en una canasta**: siempre hay un próximo escalón que el cliente todavía no puede comprar.
- **El core offer va en el escalón 2, no en el más barato**: el escalón 1 califica, no factura.
- **Sembrá semillas en cada etapa**: los upsells se preparan desde la propuesta inicial, no al final del proyecto.
- **Filtrá sin miedo el high-ticket**: mentoring premium sin filtro previo erosiona la marca.
- **Cada escalón debe ser prerequisito lógico del siguiente**: el journey es ascendente, no un catálogo plano.
- **Retención 9-18 meses > venta única**: el LTV se construye con escalera, no con descuentos.

## Chains with
- skill_servicio_estrella: prerequisito obligatorio — sin core offer definido no hay escalón 2 sobre el cual construir.
- skill_roadmap_monetizacion: una vez diseñada la escalera, encadenar para priorizar qué escalón lanzar primero, segundo y tercero según capacidad y cash flow.

## Templates used
- **PLANTILLA - Customer Journey.xlsx** → ./skill_escalera_servicios/PLANTILLA - Customer Journey.xlsx — matriz editable para mapear las 5 etapas del journey con touchpoints, contenidos y canales por etapa.
- **PLANTILLA - La escalera de tu negocio_.xlsx** → ./skill_escalera_servicios/PLANTILLA - La escalera de tu negocio_.xlsx — esquema de los 4 escalones de precio con nombre, formato, transformación y semillas de upsell por escalón.

## Source modules
modulo2, modulo9
