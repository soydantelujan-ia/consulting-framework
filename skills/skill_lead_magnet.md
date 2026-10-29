# Skill: Diseñar lead magnet y funnel de captación

## What this does
Guía al agente para diseñar un lead magnet premium (plantilla+ejemplo, estudio propio o masterclass evergreen) con su landing, prefiltro y conexión al calendario, de modo que el consultor capte leads calificados de forma inbound y sostenida.

## When to use it
**Activate this skill when the user:**
- Says: "necesito un lead magnet" / "armemos un imán de leads"
- Says: "quiero hacer una masterclass evergreen" o "un webinar de venta automatizado"
- Asks to: "diseñar un funnel de captación inbound"
- Asks to: "convertir mi ebook/checklist en algo más premium"
- Starts a situation like: "estoy publicando contenido pero nadie me deja los datos"
- Starts a situation like: "tengo tráfico en redes pero no convierte a calls"
- Says: "quiero que mi link en bio capture leads, no que sólo lleve a contactar"
- Says: "no sé qué regalar a cambio del email"

## How to execute
Esta skill es lineal: cada paso alimenta al siguiente. No saltar el Step 1 aunque el usuario llegue con el lead magnet "ya pensado" — primero validar posicionamiento y promesa.

### Step 1 — Anclar audiencia y promesa
- **Action**: Recuperar (o forzar a definir) el eje horizontal × vertical del consultor y el problema #1 que su cliente ideal pagaría por resolver YA. Si no existe posicionamiento claro, detenerse y derivar a `skill_posicionamiento`.
- **Ask the user for**: nicho vertical específico, sub-especialización, frase de posicionamiento ("Ayudo a X a Y mediante Z"), top 3 dolores reales del buyer persona, qué servicio paga al final del funnel.
- **Produce**: una promesa de lead magnet en una frase: "En [tiempo corto], [audiencia] obtiene [resultado tangible] sin [obstáculo típico]".

### Step 2 — Elegir formato premium (no genérico)
- **Action**: Descartar checklist simple / ebook básico. Proponer y elegir UNO de los tres formatos premium según madurez del consultor:
  - **Plantilla + ejemplo resuelto**: ideal si el consultor tiene metodología propia y entregables replicables.
  - **Estudio propio / benchmark**: ideal si tiene data, casos o acceso a una muestra del nicho.
  - **Masterclass evergreen (webinar de venta automatizado)**: ideal si ya hay autoridad y se busca cerrar calls de alto ticket.
- **Ask the user for**: nivel de autoridad actual, ticket del servicio final, si tiene casos/data/metodología documentada, tiempo disponible para producirlo.
- **Produce**: decisión de formato + justificación + título tentativo con beneficio específico (no "Guía de…", sí "La plantilla de [resultado] que uso con clientes que facturan [X]").

### Step 3 — Diseñar la estructura del activo
- **Action**: Esqueletar el contenido del lead magnet de modo que demuestre metodología (Show, don't tell) y deje al lead "educado pero hambriento" del servicio pago.
  - Plantilla+ejemplo: 1 plantilla editable + 1 caso real resuelto paso a paso + 3 errores típicos.
  - Estudio: hallazgo principal + 3-5 datos accionables + benchmark vs. competencia + CTA al servicio.
  - Masterclass: hook (3 min) → problema externo + interno (7 min) → método propio con nombre (25 min) → caso de éxito + tragedia (10 min) → oferta + CTA al calendario (10 min).
- **Ask the user for**: ejemplos reales que pueda ceder, métricas/data si va por estudio, nombre de su metodología (si no existe, crearlo aquí).
- **Produce**: índice/guion del lead magnet listo para producirse + nombre de metodología propia.

### Step 4 — Landing de captura con prefiltro
- **Action**: Diseñar la landing page con above-the-fold orientado a conversión y prefiltro embebido en el formulario para descalificar leads malos sin fricción.
  - Above-the-fold: titular = promesa del Step 1, subtítulo con dolor concreto, mockup del entregable, formulario corto, CTA con verbo de acción ("Quiero la plantilla").
  - Bajo el fold: 3 bullets de qué se llevan + mini-bio con autoridad (1 logo de medio, 1 cifra, 1 cara) + 1 testimonio + FAQ corto + legales.
  - Prefiltro: añadir 1-2 campos cualificadores (facturación actual, tipo de negocio, mayor obstáculo) que luego use `skill_prefiltro` para segmentar.
  - Píxeles: instruir instalar Meta Pixel + GA4 + tag de evento "Lead" en thank-you page.
- **Ask the user for**: dominio o subdominio donde irá, herramienta (Framer, Webflow, WP, etc.), CRM/email tool, si tiene calendario (Calendly/Cal.com) ya conectado.
- **Produce**: wireframe textual de la landing + copy de cada sección + spec del formulario con campos de prefiltro + lista de píxeles a instalar.

### Step 5 — Secuencia post-captura y enlace al calendario
- **Action**: Definir qué pasa entre que dejan el email y que reservan call. La regla: el lead magnet entrega valor inmediato y la secuencia educa antes de vender.
  - Email 1 (instantáneo): entrega del recurso + 1 tip extra + CTA blando al calendario para leads que cumplen prefiltro.
  - Email 2 (24-48h): caso de éxito breve + invitación a la masterclass evergreen (si aplica) o a artículo pilar.
  - Email 3 (72h): tragedia / problema interno + CTA a sesión de diagnóstico gratuita (calendario).
  - Email 4 (día 5-7): testimonios + oferta del servicio + CTA fuerte.
  - Para masterclass evergreen: la secuencia se dispara según comportamiento (vio la clase / no la vio / vio pero no agendó).
- **Ask the user for**: link de calendario, duración y nombre de la primera call (diagnóstico, descubrimiento, etc.), tono editorial.
- **Produce**: mapa de la secuencia + drafts de los 3-4 emails + reglas de segmentación según prefiltro.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_lead_magnet/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Distribución y test
- **Action**: Conectar el lead magnet con el ecosistema MAC del consultor (NO dejarlo huérfano).
  - Link en bio de Instagram + LinkedIn → landing.
  - Una píldora educativa semanal (≤59s) con CTA al lead magnet.
  - Un artículo pilar SEO + 1 video YouTube apuntando a la landing.
  - Pauta mínima: 20 USD por variante para test A/B (titular o creatividad).
  - Métricas a trackear: CTR del CTA, conversión de landing, % que cumple prefiltro, % que agenda, show-rate, cierre.
- **Ask the user for**: presupuesto disponible para pauta, canales activos.
- **Produce**: plan de distribución 30 días + 2 variantes para test A/B + tablero de métricas con benchmarks (landing >25% conversión, prefiltro-aprobados >40%, agenda >15%).

## Output
Documento entregable que contiene:
1. Promesa y formato del lead magnet (decisión justificada).
2. Índice/guion completo del activo + nombre de metodología propia.
3. Wireframe + copy de la landing con campos de prefiltro y píxeles.
4. Secuencia de emails (3-5) con triggers y conexión al calendario.
5. Plan de distribución 30 días + variantes A/B + tablero de métricas.

## Key consulting principles applied
- **Educar antes de vender**: el lead magnet entrega valor real, no es un anzuelo vacío.
- **Show, don't tell**: plantilla con ejemplo resuelto, estudio con data, masterclass con metodología nombrada — la autoridad se demuestra, no se declara.
- **Especificidad gana**: títulos y promesas atadas al nicho vertical, no genéricas.
- **CTA de captura, no de "contacto"**: el funnel reemplaza el botón "contactar" por soborno ético.
- **Coherencia omnicanal**: el lead magnet vive en redes, web, offline y pauta con un solo concepto.
- **Diferenciate o sé barato**: descartar formatos genéricos cuando el mercado ya pide premium.
- **Datos sobre supuestos**: nunca lanzar sin píxeles ni sin test A/B con pauta mínima.

## Chains with
- skill_posicionamiento: prerrequisito — sin eje horizontal × vertical claro, el lead magnet no convierte. Si falta, derivar antes del Step 1.
- skill_contenido: el lead magnet necesita el MAC vivo (píldoras, artículo pilar, video) para alimentarlo. Encadenar tras el Step 6.
- skill_captacion: para escalar con pauta paga y campañas frías una vez validada la conversión orgánica.
- skill_prefiltro: define las reglas de segmentación que la landing del Step 4 y la secuencia del Step 5 ejecutan.

## Templates used
- **ESTRUCTURA WEBINAR AUTOMATIZADO - ADC.docx** → ./skill_lead_magnet/ESTRUCTURA WEBINAR AUTOMATIZADO - ADC.docx — estructura completa de masterclass evergreen / webinar de venta automatizado (hook, problema, método propio, caso de éxito, oferta y CTA al calendario) que se aplica en el Step 3 cuando el formato elegido es masterclass.

## Source modules
modulo4, modulo5, modulo12
