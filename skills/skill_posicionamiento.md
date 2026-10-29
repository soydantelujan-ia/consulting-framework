# Skill: Definir posicionamiento y nicho

## What this does
Guía al consultor a aterrizar su nicho, avatar, eje horizontal × vertical y propuesta de valor en una frase única, con un plan de aterrizaje a 3 años / 1 año / 90 días / 7 días.

## When to use it
**Activate this skill when the user:**
- Says: "necesito definir mi nicho"
- Says: "quiero posicionarme como consultor en…"
- Asks to: "ayudame a armar mi propuesta de valor"
- Asks to: "quién es mi cliente ideal / mi avatar"
- Starts a situation like: "soy consultor de marketing pero me presento como todólogo y no cierro clientes"
- Starts a situation like: "quiero especializarme en [industria/vertical] pero no sé cómo aterrizarlo"
- Says: "compito por precio, no logro diferenciarme"
- Says: "estoy en transición desde freelance/empleo y arranco mi consultoría desde cero"

## How to execute
Ejecutar los pasos en orden. No avanzar al siguiente sin tener el output del anterior por escrito. El consultor tiende a saltar al pitch sin haber elegido nicho — bloquear ese atajo.

### Step 1 — Inventario de talento y diagnóstico de partida
- **Action**: Auditar honestamente conocimientos, habilidades y experiencia actuales del consultor antes de elegir hacia dónde apuntar.
- **Ask the user for**: 3 columnas (Conocimientos formales / Habilidades prácticas / Experiencias y proyectos cobrados), años de trayectoria, industrias en las que ya trabajó, último cliente que lo recomendaría.
- **Produce**: Tabla de inventario + lista de 2-3 áreas donde tiene tracción real (no solo interés).

### Step 2 — Eje horizontal: nicho → especialización → diferenciador
- **Action**: Aterrizar capa por capa el QUÉ hace, evitando el "consultor de marketing" genérico. Forzar al menos 3 niveles de profundidad.
- **Ask the user for**: Categoría amplia (ej: marketing) → especialización (ej: captación de leads) → sub-especialización (ej: leads inmobiliarios B2C) → diferenciador propio (metodología, herramienta o ángulo único).
- **Produce**: Frase del eje horizontal con 4 capas encadenadas.

### Step 3 — Eje vertical: a quién sirve (avatar único)
- **Action**: Definir UN tipo de cliente concreto, anclado a una persona real que conozca, no a un segmento abstracto.
- **Ask the user for**: Una persona real que califique como cliente ideal (nombre, rol, industria, tamaño de empresa, momento de negocio), su problema externo, su problema interno (lo que no se anima a decir en voz alta), su deseo más grande, los errores que comete repetidamente, la transformación esperada en una frase.
- **Produce**: Ficha de avatar + criterios de descalificación (a quién decir "no" aunque pague).

### Step 4 — Cruce horizontal × vertical en una frase
- **Action**: Fusionar los ejes en la fórmula: "Ayudo a [audiencia vertical] a [éxito concreto] mediante [diferenciador horizontal]".
- **Ask the user for**: Validar con el test del niño de 10 años y de la abuela: ¿lo entienden sin jerga? Si no, reescribir.
- **Produce**: Frase única de posicionamiento, sin tecnicismos, con verbo potente y resultado medible.

### Step 5 — Propuesta de valor (transformación, no características)
- **Action**: Articular el "antes y después" del cliente — no las plantillas, sesiones ni horas. Validar contra las 3 necesidades de Alan Weiss (existentes / creadas / anticipadas).
- **Ask the user for**: Punto A real del cliente (situación dolorosa medible), punto B deseado (con cifras y plazo), qué pasa si no resuelve el problema (la "tragedia"), por qué él y no otro consultor (autoridad demostrable).
- **Produce**: Bloque de propuesta de valor: transformación + plazo + diferenciador + prueba de autoridad.

### Step 6 — Plan de aterrizaje 3 años / 1 año / 90 días / 7 días
- **Action**: Convertir el posicionamiento en hitos progresivos para que no quede en una frase de PowerPoint.
- **Ask the user for**: Visión a 3 años (cómo se ve la marca consolidada), objetivo a 1 año (facturación, casos, autoridad), entregables concretos a 90 días (web, dossier, primer caso publicado), acciones de los próximos 7 días (publicar bio nueva, mandar mensaje a 5 prospectos del avatar, etc.).
- **Produce**: Plan en 4 horizontes con outcomes medibles por tramo.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_posicionamiento/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 8 — Validación y test de calle
- **Action**: Romper el supuesto de "ya sé qué funciona". Validar el posicionamiento con audiencia real antes de invertir en branding/web.
- **Ask the user for**: 5 conversaciones (DM, café, llamada) con personas que califiquen como avatar, mostrando la frase y midiendo: ¿la entienden?, ¿se sienten identificados?, ¿preguntarían precio?
- **Produce**: Reporte de validación + ajustes finales a la frase y al avatar antes de pasar a marca/pitch/oferta.

## Output
Documento "Posicionamiento del Consultor" con:
- Inventario de talento (3 columnas)
- Ficha de avatar (con criterios de descalificación)
- Eje horizontal × vertical
- Frase única de posicionamiento (validada con test del niño/abuela)
- Bloque de propuesta de valor (transformación + autoridad)
- Plan de aterrizaje 3 años / 1 año / 90 días / 7 días
- Reporte de validación con 5 prospectos reales

## Key consulting principles applied
- Especialización antes que catálogo: "ayudo a captar leads para Realtors" vende más que "marketing digital".
- Equilibrio yo ↔ cliente: la marca vive en la intersección entre quién sos y qué necesita tu cliente ideal.
- Vendé transformación, no características: el cliente compra el antes/después, no las horas.
- Diferenciate o sé barato (Kawasaki): sin diferenciador horizontal claro, se compite por precio.
- A menor tiempo entre punto A y punto B del cliente, mayor el fee.
- El cliente sabe lo que quiere, pero no lo que necesita: ahí está el valor real que se cobra.
- Datos sobre intuición: validar con audiencia real antes de imprimir tarjetas.

## Chains with
- skill_pitch: una vez fijado el posicionamiento, traducirlo al pitch 7P (corto + largo) con la metodología propia nombrada.
- skill_servicio_estrella: con nicho y avatar definidos, recién ahí tiene sentido diseñar el core offer y la escalera de servicios.
- skill_marca_personal: con la frase única validada, montar la base de credibilidad (web, dossier, press kit, perfiles magnéticos).

## Templates used
- **PLANTILLA - Aterrizaje de posicionamiento.xlsx** → ./skill_posicionamiento/PLANTILLA - Aterrizaje de posicionamiento.xlsx — Workbook integral para aterrizar nicho, avatar, ejes horizontal × vertical, frase única de posicionamiento y plan 3 años / 1 año / 90 días / 7 días.

## Source modules
modulo1, modulo2, modulo4
