# Skill: Diagnóstico inicial y briefing

## What this does
Conduce el levantamiento inicial de información del cliente y devuelve un diagnóstico puntuable (auditoría 360 con ejes y score visual) que evidencia el "antes" y posiciona la metodología del consultor antes de proponer cualquier solución.

## When to use it
**Activate this skill when the user:**
- Says: "necesito hacer un diagnóstico de este cliente"
- Says: "armame el briefing inicial para la reunión de mañana"
- Asks to: "auditar al cliente antes de mandar propuesta"
- Asks to: "levantar información de [marca/cliente] para arrancar"
- Starts a situation like: "tengo primera reunión con un prospecto y quiero llegar con algo en la mano"
- Starts a situation like: "el cliente me pidió propuesta pero todavía no sé bien qué tiene"
- Says: "quiero mostrarle al cliente cómo está hoy con un score"
- Asks to: "aplicar la metodología 360 a este caso"

## How to execute

### Step 1 — Encuadre del caso
- **Action**: Entender qué tipo de cliente es, en qué industria opera, qué servicio se está evaluando ofrecer y en qué etapa del proceso comercial está (primera reunión / segunda visita / pidió propuesta directo).
- **Ask the user for**: nombre del cliente, industria/vertical, servicio que el consultor cree que va a ofrecer (asesoría, implementación, mixto), si ya hubo reunión previa o es la primera, y canal de la próxima interacción (presencial, Zoom, asincrónico).
- **Produce**: ficha de encuadre de 4-6 líneas que define alcance del diagnóstico y profundidad esperada.

### Step 2 — Pre-carga del briefing
- **Action**: Completar todo lo que ya se pueda saber del cliente sin preguntarle (web, redes, posicionamiento aparente, competencia visible, palabras clave que usa públicamente). Esto demuestra preparación en la reunión.
- **Ask the user for**: links a web, redes y cualquier material que ya tenga del cliente (deck previo, último plan, métricas que haya compartido).
- **Produce**: plantilla de briefing pre-llenada con secciones: negocio, oferta actual, audiencia declarada, presencia digital observada, competidores, tono de comunicación, dolores hipotéticos, palabras clave del cliente.

### Step 3 — Guion de preguntas para la reunión
- **Action**: Generar el set de preguntas que cierran los huecos del briefing y, sobre todo, capturan dolores y palabras textuales del cliente (van a reutilizarse después en la propuesta).
- **Ask the user for**: tiempo disponible en la reunión y si va a ser presencial (lleva la plantilla impresa) o remoto.
- **Produce**: guion de 10-15 preguntas agrupadas en bloques (negocio y objetivos / audiencia y oferta / historia digital / expectativa y presupuesto / decisión y plazos), con instrucción explícita de anotar frases textuales del cliente.

### Step 4 — Definición de los ejes de la auditoría 360
- **Action**: Elegir 5 ejes puntuables relevantes al servicio. Default: colorimetría, proporción, practicidad, originalidad, memorabilidad. Ajustar al vertical si corresponde (ej. para e-commerce: identidad visual, UX de fichas, copy de oferta, prueba social, fricción de checkout).
- **Ask the user for**: si quiere usar los 5 ejes default o adaptarlos al caso.
- **Produce**: lista de 5 ejes con definición de una línea cada uno y criterio de qué se evalúa.

### Step 5 — Puntuación y score visual
- **Action**: Asignar puntuación 1-5 (estrellas) por eje con justificación corta (1-2 líneas con evidencia observable: link, captura, frase). Calcular score global.
- **Ask the user for**: confirmación de la puntuación si hay dudas en algún eje.
- **Produce**: tabla de auditoría 360 con eje × score × evidencia + score global y lectura ("memorable pero poco práctico", "fuerte en originalidad, débil en proporción", etc.).

### Step 6 — Síntesis: dolores, palabras clave y "antes" del cliente
- **Action**: Consolidar los 3-5 dolores principales detectados, las palabras textuales que usó el cliente (o las que se infieren de su comunicación pública) y formular el "antes" que se va a mostrar como punto de partida.
- **Ask the user for**: nada nuevo — se trabaja sobre lo capturado en steps 1-5.
- **Produce**: bloque de síntesis con: 3-5 dolores priorizados, glosario de palabras clave del cliente, párrafo del "antes" listo para abrir la propuesta.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_diagnostico/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 8 — Handoff a propuesta
- **Action**: Marcar qué piezas del diagnóstico van directo a la propuesta (diagnóstico puntuado, dolores, palabras clave, score visual) y qué queda como insumo interno.
- **Ask the user for**: confirmación de avanzar a `skill_propuesta` o si quiere primero validar el diagnóstico con el cliente en una sesión de descubrimiento (`skill_sesion_descubrimiento`).
- **Produce**: paquete de diagnóstico cerrado + recomendación de siguiente paso.

## Output
Un documento de diagnóstico que contiene:
1. Ficha de encuadre del caso (4-6 líneas).
2. Briefing completo (pre-cargado + completado en reunión).
3. Tabla de auditoría 360 con 5 ejes, score por eje (estrellas 1-5), evidencia y score global.
4. Síntesis de 3-5 dolores priorizados y glosario de palabras clave del cliente.
5. Párrafo del "antes" listo para abrir la propuesta.
6. Indicación de siguiente paso (propuesta directa o sesión de descubrimiento previa).

## Key consulting principles applied
- El cliente compra al consultor cuando ve el método, no cuando ve la respuesta: por eso la metodología puntuable va antes que la solución.
- Mostrar el "antes" con un score medible posiciona la transformación que se va a vender después.
- Capturar las palabras textuales del cliente en el briefing es lo que después hace que la propuesta "le hable" y no suene genérica.
- Llevar la plantilla impresa/pre-cargada a la primera reunión transmite preparación y acelera el ratio de cierre.
- Diagnóstico medible hoy = línea base para demostrar mejora al cierre del servicio.

## Chains with
- skill_sesion_descubrimiento: cuando el diagnóstico inicial detecta que falta profundidad o que el cliente todavía no verbalizó bien el dolor — se agenda sesión de descubrimiento antes de cotizar.
- skill_propuesta: cuando el diagnóstico ya está cerrado con score, dolores y palabras clave — se pasa el paquete completo como input para armar la propuesta vertical y fijar precio por valor.

## Templates used
- **PLANTILLA - Auto-evaluación de capacidades.xlsx** → ./skill_diagnostico/PLANTILLA - Auto-evaluación de capacidades.xlsx — matriz puntuable para auto-evaluar capacidades del cliente y alimentar los ejes de la auditoría 360.
- **PLANTILLA ADC_ Briefing de marketing.docx** → ./skill_diagnostico/PLANTILLA ADC_ Briefing de marketing.docx — briefing de marketing pre-cargable e imprimible para usar en la primera reunión de diagnóstico.

## Source modules
modulo3, modulo5, modulo6
