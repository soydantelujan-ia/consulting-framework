# Skill: Construir marca personal omnicanal

## What this does
Guía al consultor a construir un sistema de autoridad omnicanal coherente —hub web, press kit, perfiles LinkedIn/Instagram optimizados y dossier de speaker— que convierta su posicionamiento en activos digitales y físicos capaces de atraer clientes inbound calificados sin depender del boca a boca.

## When to use it
**Activate this skill when the user:**
- Says: "ayudame a armar mi LinkedIn" o "tengo que optimizar mi perfil"
- Asks to: "armar un press kit" o "necesito un dossier para presentarme como speaker"
- Says: "quiero hacer mi web personal" o "mi web actual no me trae clientes"
- Starts a situation like: "me invitaron a dar una conferencia y no tengo materiales"
- Says: "necesito trabajar mi marca personal" o "no me toman en serio en el mercado"
- Asks to: "revisar mi bio de Instagram" o "mejorar mi presencia digital"
- Says: "quiero pasar de freelance a referente de mi nicho"
- Starts a situation like: "googleo mi nombre y no aparece nada serio"

## How to execute
Trabajá en orden los activos de autoridad. NO arranques por diseño visual: la marca se construye desde el posicionamiento hacia afuera. Si el usuario aún no tiene posicionamiento claro, derivá primero a `skill_posicionamiento` y volvé acá.

### Step 1 — Verificar cimientos antes de producir activos
- **Action**: Confirmá que existan tres insumos previos: (1) frase de posicionamiento horizontal × vertical, (2) pitch 7P (versión corta y larga) con nombre de metodología propia, (3) avatar del cliente ideal. Si falta alguno, frená la skill y derivá al usuario a `skill_posicionamiento`.
- **Ask the user for**: frase de posicionamiento, pitch actual, nombre de metodología propia, avatar/buyer persona, link a perfiles y web actuales (si los hay).
- **Produce**: checklist de cimientos OK / faltantes + decisión de continuar o derivar.

### Step 2 — Diseñar el Hub (web mínima viable)
- **Action**: Definí la arquitectura de la web personal como centro de operaciones. Estructura obligatoria: Home con above-the-fold (foto + frase de posicionamiento + CTA al lead magnet), Servicios (con la escalera del consultor visible), Sobre mí (en primera persona, con historia + autoridad + CTA), Blog/Recursos, Casos de éxito, Legales, y píxeles de medición instalados antes de pautar.
- **Ask the user for**: dominio actual o disponible, lead magnet vigente (si no hay, definir uno: plantilla+ejemplo, estudio propio o tabla comparativa), 3-5 casos de éxito con métricas, fotos profesionales.
- **Produce**: wireframe textual de cada página con copy base, lista de píxeles a instalar (Meta, Google, LinkedIn) y checklist SEO on-page por sección.

### Step 3 — Armar el Press Kit multiusos
- **Action**: Generá una carpeta compartida (Drive) con todos los activos formales que prueban autoridad. Contenido obligatorio: bio en 4 formatos (500 / 150 / 50 palabras / 140 caracteres), CV de logros (no de tareas), 3-5 fotos oficiales en alta y baja, logo editable en SVG/PNG con fondo transparente, 3 case stories en PDF, video de venta de 60-90s, dossier multiusos de máximo 10 páginas.
- **Ask the user for**: bios existentes (aunque sean borradores), logros cuantificables, apariciones en medios, testimonios firmados, foto de sesión profesional reciente.
- **Produce**: estructura de carpeta lista para compartir + dossier PDF de 10 páginas + bios redactadas en los 4 formatos.

### Step 4 — Optimizar perfil LinkedIn (regla de los 7 segundos)
- **Action**: Auditá y reescribí el perfil aplicando: foto cuadrada 400x400 validada en Snappr, banner con frase de posicionamiento + CTA, URL personalizada, titular con palabras clave separadas por pipes (`Especialidad | Vertical | Diferenciador | Metodología propia`), sección "Acerca de" en primera persona con estructura gancho → historia → autoridad → email/CTA, destacados con lead magnets y casos, mínimo 5 recomendaciones dadas y 5 recibidas.
- **Ask the user for**: acceso visual al perfil actual (capturas o link), palabras clave que el avatar googlearía, lead magnet activo.
- **Produce**: nuevo titular, nuevo "Acerca de", lista de palabras clave a incrustar, plan de pedido de recomendaciones con guion, checklist final de validación.

### Step 5 — Optimizar perfil Instagram (buscador de marca)
- **Action**: Reconfigurá Name + Keyname con palabra clave de nicho (no el nombre repetido), bio de 3 líneas con estructura `qué hacés / qué te certifica / qué anhelás` + emoji funcional, link en bio que lleve al lead magnet (no a la home), highlights diseñados como menú navegable (Sobre mí / Servicios / Casos / Recursos / Prensa), carta de hashtags (3-4 principales + 10-20 secundarios + 5-6 branded).
- **Ask the user for**: usuario actual, highlights existentes, capturas de bio actual.
- **Produce**: nueva bio + estructura de highlights con portadas sugeridas + carta de hashtags + plantilla de moodboard visual.

### Step 6 — Construir el Dossier de Speaker
- **Action**: Creá un dossier ejecutivo de exactamente 3 páginas: (1) quién soy + frase de posicionamiento + foto de escenario, (2) conferencia base anual con título magnético, abstract, 5 takeaways y formato (keynote 45min / taller 90min / panel), (3) prueba social: logos de eventos previos, métricas de audiencia, testimonios de organizadores, fee y datos de contacto. Incluí filtros de aceptación: aforo mínimo, otros speakers del cartel, presupuesto, fecha.
- **Ask the user for**: experiencias previas como speaker (aunque sean charlas internas), tema en el que querés posicionarte como referente, fee deseado, eventos objetivo del próximo año.
- **Produce**: dossier de speaker en PDF de 3 páginas + checklist de filtrado pre-aceptación + guion de captación de leads en vivo durante la conferencia.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_marca_personal/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 8 — Plan de aterrizaje y coherencia omnicanal
- **Action**: Cruzá todos los activos producidos y verificá coherencia: ¿la frase de posicionamiento es idéntica en web, LinkedIn, Instagram y dossier? ¿La foto oficial es la misma en todos lados? ¿El CTA principal apunta siempre al mismo lead magnet? Definí cadencia de revisión trimestral y plan de aterrizaje 3 años / 1 año / 90 días / 7 días.
- **Ask the user for**: confirmación de cuál es el activo "fuente de verdad" (usualmente la web).
- **Produce**: tabla comparativa de coherencia (canal × elemento) con OK/ajustar + roadmap 90 días con hitos semanales.

## Output
Paquete de marca personal omnicanal entregado en una carpeta compartida que incluye:
- Hub web (wireframe + copy de cada página + checklist SEO + lista de píxeles)
- Press kit completo (bios x4, CV de logros, fotos, logo, case stories, video de venta, dossier 10 páginas)
- Perfil LinkedIn reescrito (titular, Acerca de, recomendaciones, palabras clave)
- Perfil Instagram reconfigurado (bio, highlights, hashtags, moodboard)
- Dossier de speaker (PDF 3 páginas + checklist de filtrado)
- Tabla de coherencia omnicanal + roadmap 90 días

## Key consulting principles applied
- **Equilibrio yo ↔ cliente**: la marca vive en la intersección, no en el ego ni en el complacer.
- **Show, don't tell**: la autoridad se prueba con hitos cuantificables, no con adjetivos.
- **Coherencia omnicanal**: un solo concepto, lenguajes adaptados; jamás mensajes contradictorios entre canales.
- **Educar antes de vender**: cada activo captura datos vía soborno ético (lead magnet), nunca con un genérico "contactame".
- **Especificidad gana**: el titular y la bio se escriben para el avatar específico, no para "todos".
- **Diferenciate o sé barato**: si la marca no comunica diferenciador horizontal claro, competirá por precio.
- **El hub es propio, las redes son alquiladas**: la web siempre es la fuente de verdad y destino final del tráfico.

## Chains with
- skill_posicionamiento: prerequisito obligatorio. Sin frase de posicionamiento horizontal × vertical y pitch 7P, esta skill no puede ejecutarse — derivar antes.
- skill_contenido: salida natural. Una vez que los perfiles y el hub están optimizados, encadenar para activar el MAC (Mínimo Asset Content) con las 9 piezas mínimas y el calendario editorial que alimenten esos canales.

## Templates used
- **ADC MOODBOARD.pptx** → ./skill_marca_personal/ADC MOODBOARD.pptx — Moodboard visual base para definir paleta, tipografía y referencias estéticas de la marca personal (usable en Step 5 para Instagram y Step 2 para el hub).
- **Plantilla _ Dossier de empresa.pptx** → ./skill_marca_personal/Plantilla _ Dossier de empresa.pptx — Dossier multiusos editable en PowerPoint para armar el press kit corporativo/personal de hasta 10 páginas (Step 3) y adaptar como dossier de speaker (Step 6).

## Source modules
modulo2, modulo4
