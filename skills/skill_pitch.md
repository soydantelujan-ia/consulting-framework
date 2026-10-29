# Skill: Construir pitch y mensaje de venta

## What this does
Genera un pitch corto y largo del consultor (o de su cliente) usando la fórmula 7P, con variantes adaptadas por audiencia y un nombre propio para la metodología, listo para usar en web, redes, eventos y reuniones de venta.

## When to use it
**Activate this skill when the user:**
- Says: "ayudame a armar mi pitch"
- Says: "no sé cómo me presento cuando me preguntan qué hago"
- Asks to: "escribir mi elevator pitch para un evento"
- Asks to: "armar el mensaje de venta para la home / bio de LinkedIn"
- Starts a situation like: "tengo una reunión con un cliente y no sé cómo explicarle lo que hago"
- Says: "mi mensaje actual no engancha, la gente no entiende a qué me dedico"
- Says: "necesito una versión de mi pitch para inversores / para corporativo / para networking"
- Asks to: "ponerle nombre a mi metodología"

## How to execute
Trabajá en español (LATAM), tono cercano y directo. No le pidas todo al usuario de golpe: avanzá paso a paso confirmando cada bloque antes de pasar al siguiente. Si la skill `skill_posicionamiento` no se ejecutó antes, hacé un mini-diagnóstico exprés (audiencia + diferenciador) antes del Step 1.

### Step 1 — Anclar audiencia y transformación
- **Action**: Confirmar a quién le habla el pitch y cuál es la transformación (punto A → punto B) que entrega. Si hay varias audiencias posibles, elegí UNA como principal y dejá las otras para variantes (Step 5).
- **Ask the user for**:
  - Cliente ideal vertical (rol + sector + tamaño): "¿a quién específicamente?"
  - Punto A del cliente (dolor concreto y medible)
  - Punto B deseado (resultado concreto y medible, idealmente con cifra o plazo)
  - Tiempo aproximado en que lo logra con tu metodología
- **Produce**: Una línea base "Ayudo a [audiencia vertical] a [resultado medible] en [plazo]".

### Step 2 — Completar los 7P
- **Action**: Llenar los 7 ingredientes uno por uno. No avances al siguiente sin tener el anterior cerrado en una frase.
- **Ask the user for** (en este orden):
  1. **Quieren**: ¿qué dice el cliente que quiere? (sus palabras, no las tuyas)
  2. **Problema externo**: ¿qué problema visible/tangible tiene?
  3. **Problema interno**: ¿qué emoción o miedo hay detrás? (frustración, vergüenza, urgencia, sensación de estancamiento)
  4. **Empatía**: ¿cómo demostrás que lo entendés? (frase tipo "sé lo que se siente cuando…")
  5. **Autoridad**: 2-3 pruebas concretas (años, clientes atendidos, hitos, medios, certificaciones, casos con cifra)
  6. **Plan**: tu metodología en 3 pasos máximo + nombre propio (ej: "Método AUTORIDAD 360", "Sistema P3")
  7. **Éxito + Tragedia**: cómo se ve la vida del cliente si lo hace con vos / qué pierde si no lo hace
- **Produce**: Tabla con los 7P completos en una sola pasada.

### Step 3 — Bautizar la metodología
- **Action**: Si en el Step 2 no surgió un nombre fuerte, proponé 3-5 opciones de nombre para la metodología propia. Criterios: corto (1-3 palabras), evocador del resultado, registrable, fácil de pronunciar en español. Evitá siglas vacías.
- **Ask the user for**: cuál resuena más, o si quiere mezclar elementos.
- **Produce**: Nombre definitivo de la metodología + tagline de 1 línea ("[Nombre]: el sistema para [resultado] en [plazo]").

### Step 4 — Redactar versión corta y versión larga
- **Action**: Escribir dos versiones limpias.
  - **Pitch corto (15-20 segundos / 1-2 frases)**: fórmula "Ayudo a [audiencia] a [éxito] mediante [diferenciador / nombre del método]". Test del niño de 10 años: si una persona ajena al rubro no lo entiende, reescribir.
  - **Pitch largo (60-90 segundos)**: hilar los 7P en este orden — gancho con lo que el cliente *quiere* → nombrar problema externo + interno → empatía → autoridad (1-2 pruebas) → presentar el plan con nombre propio → cerrar con éxito vs tragedia + CTA suave.
- **Ask the user for**: leerlo en voz alta y marcar qué frases le cuelgan o suenan a otro.
- **Produce**: Pitch corto + pitch largo, en bloques copiables.

### Step 5 — Generar variantes por audiencia
- **Action**: A partir del pitch base, producir 3-4 variantes manteniendo el mismo concepto y cambiando solo lenguaje, ejemplos y nivel de jerga. Variantes típicas:
  - **Corporativo / directivo** (foco en ROI, riesgo, eficiencia)
  - **Emprendedor / infoproductor** (foco en escala, libertad, sistemas)
  - **Networking informal / familia** (lenguaje cero técnico, analogía cotidiana)
  - **Speaker / escenario** (con apertura provocadora y cierre con frase memorable)
- **Ask the user for**: en cuáles audiencias se mueve más para priorizar el orden.
- **Produce**: Bloque por audiencia con pitch corto + 1 frase de apertura específica.

### Step 6 — Test del niño de 10 años + ajuste final
- **Action**: Releer cada variante y marcar palabras técnicas, anglicismos innecesarios o frases largas. Reescribir hasta que cualquier persona ajena al rubro lo entienda. Confirmar que cada pitch contiene: a quién, qué transformación, por qué con vos, qué hacer ahora.
- **Ask the user for**: probar el pitch corto con alguien fuera del nicho (familiar, amigo) y reportar si lo entendió a la primera.
- **Produce**: Versión final validada + lista de palabras prohibidas (jerga propia a evitar).

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_pitch/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 8 — Mapear dónde se usa cada versión
- **Action**: Asignar cada variante a un canal/touchpoint concreto.
- **Produce**: Tabla "Versión → Dónde se usa":
  - Pitch corto → bio LinkedIn, bio Instagram, home above-the-fold, tarjeta de visita
  - Pitch largo → "Sobre mí", video de venta, dossier, intro de webinar
  - Variante corporativa → reuniones de venta, propuestas
  - Variante networking → eventos, presentaciones cara a cara
  - Variante speaker → apertura de conferencia

## Output
Documento entregable con:
1. Frase base de posicionamiento ("Ayudo a X a Y en Z")
2. Tabla 7P completa
3. Nombre de la metodología + tagline
4. **Pitch corto** (copiable, ≤20 segundos)
5. **Pitch largo** (copiable, 60-90 segundos)
6. 3-4 **variantes por audiencia**
7. Tabla de uso por canal/touchpoint
8. Lista de palabras prohibidas (jerga a evitar)

Formato sugerido: Google Doc o markdown con bloques claramente separados y listos para copy-paste.

## Key consulting principles applied
- **Educar antes de vender**: el pitch abre conversación, no cierra venta — un cliente educado compra solo.
- **Especificidad gana**: "ayudo a captar leads para Realtors" vende más que "hago marketing digital".
- **Show, don't tell**: la autoridad se prueba con cifras, casos y hitos, no con adjetivos ("experto", "líder").
- **Test del niño de 10 años**: si una abuela o un niño no lo entienden, no sirve.
- **Diferenciate o sé barato (Kawasaki)**: sin diferenciador horizontal claro en el pitch, competís por precio.
- **Coherencia omnicanal**: un solo concepto, lenguajes adaptados — nunca mensajes contradictorios entre canales.
- **A menor tiempo entre A y B, mayor el fee**: el plazo de la transformación es parte del pitch, no un detalle.
- **Metodología con nombre propio**: convierte servicio en producto y eleva el valor percibido.

## Chains with
- **skill_posicionamiento**: ejecutarla ANTES si el usuario aún no tiene definido el eje horizontal × vertical. Sin posicionamiento aterrizado, el pitch sale genérico.
- **skill_propuesta**: ejecutarla DESPUÉS — el pitch largo y el nombre de la metodología alimentan directamente la sección "enfoque" y "qué incluye" de la propuesta comercial.

## Templates used
- **PLANTILLA - Pitch de tu negocio.xlsx** → ./skill_pitch/PLANTILLA - Pitch de tu negocio.xlsx — planilla guía para completar los 7P y construir el pitch corto y largo del negocio paso a paso.

## Source modules
modulo1, modulo4
