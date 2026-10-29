# Skill: Sistema de captación multicanal

## What this does
Diseña y activa un sistema de captación de leads que combina networking estratégico, una red de embajadores con comisión fija y campañas de publicidad paga para alimentar el pipeline de forma constante.

## When to use it
**Activate this skill when the user:**
- Says: "necesito conseguir clientes"
- Says: "no me llegan leads" / "se me secó el pipeline"
- Asks to: "armar un sistema de captación"
- Asks to: "montar una red de embajadores o referidos"
- Asks to: "lanzar publicidad paga para mi consultoría"
- Starts a situation like: "tengo buen servicio pero nadie me conoce"
- Starts a situation like: "quiero dejar de depender del boca a boca aleatorio"
- Says: "cómo hago networking que sirva de verdad"

## How to execute

### Step 1 — Diagnóstico de canales actuales
- **Action**: Mapear de dónde vinieron los últimos 5-10 clientes del consultor para identificar qué canal ya funciona y cuál está dormido.
- **Ask the user for**: lista de últimos clientes y origen (referido, evento, contenido, ads, frío), tiempo semanal disponible para captación, presupuesto mensual para ads, nicho y ticket promedio.
- **Produce**: tabla de canales con estado actual (activo / dormido / inexistente) y canal prioritario a activar primero.

### Step 2 — Plan de networking estratégico
- **Action**: Definir 2-3 espacios concretos (eventos, comunidades, grupos, cámaras) donde está el cliente ideal y diseñar una rutina semanal de presencia con objetivo medible (conversaciones nuevas / mes, no "hacer contactos").
- **Ask the user for**: perfil exacto del cliente ideal y dónde se junta, ciudad/zona, disponibilidad para eventos presenciales vs virtuales.
- **Produce**: agenda de networking con espacios, frecuencia, mensaje de apertura y meta cuantitativa mensual.

### Step 3 — Red de embajadores con comisión fija
- **Action**: Identificar perfiles que ya tienen acceso al cliente ideal (contadores, abogados, agencias complementarias, ex-clientes) y diseñar un programa de embajadores con **comisión fija por cliente cerrado**, no porcentual, para simplificar la conversación y la operación.
- **Ask the user for**: 5-10 nombres de posibles embajadores, ticket promedio del servicio, margen disponible para comisionar.
- **Produce**: documento de programa de embajadores con: monto fijo por referido cerrado, condiciones de pago, materiales de presentación que el embajador puede reenviar, y script de invitación al programa.

### Step 4 — Setup de publicidad paga
- **Action**: Definir un único canal de ads para empezar (Meta o Google según donde esté el cliente), con un objetivo específico: generar conversaciones cualificadas, no "marca". Presupuesto mínimo de prueba: 30 días.
- **Ask the user for**: presupuesto mensual confirmado, lead magnet o oferta de entrada disponible, landing o destino del tráfico.
- **Produce**: plan de campaña con canal, presupuesto diario, oferta gancho, audiencia, KPI de éxito (CPL objetivo) y fecha de revisión.

### Step 5 — Tablero de captación unificado
- **Action**: Consolidar los tres canales en un solo tablero semanal de seguimiento para evitar que el consultor priorice solo uno y desbalancee el sistema.
- **Produce**: tablero con columnas Canal | Meta semanal | Real | Leads generados | Costo | Próxima acción.

### Step 6 — Secuencia de activación
- **Action**: Ordenar los canales en el tiempo según esfuerzo/retorno: primero embajadores (rápido y barato), luego networking (medio plazo), luego ads (requiere oferta y landing maduras).
- **Produce**: cronograma de 90 días con qué se activa cada semana.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_captacion/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

## Output
Un documento de **Sistema de Captación Multicanal** que incluye: diagnóstico de canales, plan de networking con agenda, programa de embajadores con comisión fija lista para presentar, plan de campaña de ads con presupuesto y KPI, tablero de seguimiento semanal y cronograma de activación a 90 días.

## Key consulting principles applied
- Diversificación: nunca depender de un solo canal de captación.
- Comisión fija por referido: simplifica la conversación con embajadores y elimina fricción matemática.
- Networking con meta cuantitativa, no "hacer contactos" difuso.
- Ads con objetivo de conversación cualificada, no vanity metrics.
- Activación secuencial: lo barato y rápido primero, lo costoso después.
- Tablero único: lo que no se mide no se sostiene.

## Chains with
- skill_contenido: el contenido alimenta tanto el networking (autoridad) como las ads (creatividades y retargeting). Encadenar cuando el consultor ya tiene canales activos pero falta material para nutrirlos.
- skill_lead_magnet: las campañas de ads y los embajadores necesitan una oferta gancho concreta para convertir; encadenar antes de activar Step 4.
- skill_prefiltro: una vez que entran leads, hace falta filtrar para no perder tiempo en no-cliente; encadenar inmediatamente después de que el sistema empiece a generar volumen.

## Templates used
- **Herramientas marketing.xlsx** → ./skill_captacion/Herramientas marketing.xlsx — planilla de herramientas y canales de marketing para apoyar la activación de captación (networking, embajadores y ads).

## Source modules
modulo5, modulo9
