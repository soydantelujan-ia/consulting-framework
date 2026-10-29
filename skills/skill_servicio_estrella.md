# Skill: Diseñar servicio estrella y metodología propia

## What this does
Guía al consultor a empaquetar su core offer con nombre propio, transformación clara, fases de entrega sistematizadas y stack de valor (bundling), de modo que deje de "vender horas" y pase a vender una oferta irresistible y diferenciada.

## When to use it
**Activate this skill when the user:**
- Says: "quiero armar mi servicio estrella"
- Says: "necesito crear mi metodología propia"
- Says: "ayudame a empaquetar mi oferta"
- Asks to: "armar una oferta irresistible para vender mejor"
- Asks to: "ponerle nombre a lo que hago / nombrarle a mi servicio"
- Starts a situation like: "vendo horas sueltas y siempre me regatean el precio"
- Starts a situation like: "tengo 8 servicios distintos y no sé cuál es el principal"
- Starts a situation like: "los clientes no entienden qué me hace diferente del resto"

## How to execute

### Step 1 — Validar prerequisitos (nicho + avatar)
- **Action**: Antes de diseñar la oferta, confirmar que el consultor ya tiene definido nicho y avatar. Si no los tiene, frenar y derivar a `skill_nicho_avatar` (o pedir los datos mínimos: para quién, qué problema resuelve, qué transformación promete).
- **Ask the user for**: nicho actual declarado, avatar (1 cliente real como ancla), problema principal que resuelve, deseo más grande del cliente.
- **Produce**: Ficha resumen "Para quién + Qué problema + Qué transformación" en una sola frase. Si falta algo, no avanzar.

### Step 2 — Inventario y limpieza de servicios actuales
- **Action**: Listar todos los servicios que el consultor ofrece hoy con 3 datos por servicio: cantidad de contrataciones último año, ingresos generados, tiempo real invertido. Identificar cuáles eliminar, cuáles potenciar y cuál tiene madera de "estrella".
- **Ask the user for**: lista cruda de servicios actuales con esas 3 métricas (aunque sean estimadas).
- **Produce**: Tabla de servicios con marca de Eliminar / Mantener / Potenciar, y un candidato a servicio estrella señalado con justificación (rentabilidad, demanda, alineación con nicho).

### Step 3 — Propuesta de valor con Value Proposition Canvas
- **Action**: Aplicar VPC cruzando el lado del cliente (trabajos, frustraciones, alegrías) con el lado del servicio (productos/servicios, aliviadores de dolor, creadores de alegría). El objetivo es que el servicio estrella resuelva la frustración #1 y dispare la alegría #1 del avatar.
- **Ask the user for**: 3 frustraciones top y 3 alegrías top del avatar (con palabras del cliente, no jerga del consultor).
- **Produce**: VPC completo + frase única de propuesta de valor con la estructura "Ayudo a [avatar] a pasar de [estado A] a [estado B] en [plazo] mediante [método]".

### Step 4 — Nombre propio + transformación del servicio estrella
- **Action**: Bautizar el servicio con un nombre que sea memorable, evocador y propietario (no genérico tipo "Asesoría de marketing"). Validar que el nombre sugiera transformación o método. Redactar la transformación en una sola frase del tipo "antes/después".
- **Ask the user for**: 3-5 opciones de nombre que ya tenga en la cabeza (si no tiene, proponer 5 alternativas alineadas a la propuesta de valor).
- **Produce**: Nombre elegido + tagline de 1 línea + frase de transformación ("Pasás de X a Y en Z semanas").

### Step 5 — Metodología propia en 5 fases
- **Action**: Construir el delivery sistematizado adaptando las 5 fases base: Iniciación → Diagnóstico → Planificación → Aplicación → Terminación. Cada fase necesita: objetivo, entregable concreto, duración estimada y artefacto de soporte (checklist, plantilla, dossier, sesión).
- **Ask the user for**: cómo entrega hoy el servicio paso a paso (aunque sea desordenado), duración total típica, qué documentos ya usa.
- **Produce**: Tabla de 5 fases con columnas [Fase | Objetivo | Entregable | Duración | Materiales necesarios] + nombre propio para la metodología (ej: "Método [X] en 5 fases").

### Step 6 — Stack de valor y bundling (oferta irresistible)
- **Action**: Aplicar Bundling/Unbundling. Construir un stack visible donde el servicio core va acompañado de add-ons que NO consuman tiempo del consultor (ebooks, plantillas, acceso a comunidad/academia, grabaciones, libro físico, bonus de terceros). Cada add-on debe tener valor monetario asignado para que el "valor total percibido" supere ampliamente el precio.
- **Ask the user for**: qué activos ya tiene producidos (PDFs, videos, plantillas, accesos) y qué podría sumar sin esfuerzo adicional.
- **Produce**: Stack visual tipo "Lo que recibís: [core] + [bonus 1] + [bonus 2] + ... = Valor total $X / Inversión hoy $Y".

### Step 7 — Versión troceada de respaldo (anti-objeción de precio)
- **Action**: Preparar de antemano una versión "desempaquetada" para usar como respuesta a objeciones de precio, sin hacer "carnicería" (sin perder coherencia ni valor). Definir qué se puede quitar y cuánto baja el precio en cada caso.
- **Ask the user for**: qué partes del servicio considera negociables y cuáles son innegociables.
- **Produce**: Mini-tabla "Si el cliente pide bajar precio → quito [X] → nuevo precio [Y]" con 2-3 escenarios.

### Step 8 — Validación de rentabilidad mínima
- **Action**: Calcular costos directos (horas propias × tarifa, herramientas, terceros) e indirectos (marketing, admin) del servicio estrella. Validar que el margen sea ≥30% (ideal 50%). Si no llega, ajustar precio o alcance ANTES de cerrar la oferta.
- **Ask the user for**: horas estimadas de delivery, costo/hora propio, costos de herramientas y terceros asociados.
- **Produce**: Cálculo de rentabilidad con [Precio - Costos = Margen %] y recomendación de ajuste si margen <30%.

### Step 9 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_servicio_estrella/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

## Output
Documento "Servicio Estrella + Metodología Propia" con:
1. Frase de posicionamiento (para quién + transformación).
2. Nombre del servicio estrella + tagline + frase antes/después.
3. Propuesta de valor (VPC resumido).
4. Metodología nombrada con las 5 fases tabuladas.
5. Stack de valor visual con valor total vs inversión.
6. Versión troceada de respaldo para objeciones.
7. Cálculo de rentabilidad validado (≥30%).
8. Pitch de venta de 30 segundos listo para usar en llamadas y propuestas.

## Key consulting principles applied
- **Vendé transformación, no características**: la oferta se redacta desde el "antes/después", no desde "17 plantillas y 5 sesiones".
- **Especialización antes que catálogo**: un solo servicio estrella, no un menú interminable.
- **Metodología propia = autoridad**: lo nombrado y sistematizado se cobra más caro y se delega mejor.
- **Rentabilidad mínima del 30%**: si no llega, se ajusta antes de enviar la propuesta, nunca después.
- **Nunca bajar precio sin desempaquetar**: la versión troceada protege el ticket sin perder al cliente.
- **Sembrá semillas desde el inicio**: la oferta debe insinuar el próximo escalón para habilitar upsells futuros.
- **Filtrá sin miedo**: la oferta se diseña para el avatar correcto, no para "todo el que pague".

## Chains with
- **skill_nicho_avatar**: prerequisito obligatorio. Sin nicho y avatar definidos, esta skill no puede ejecutarse con calidad.
- **skill_escalera_servicios**: encadenar inmediatamente después. El servicio estrella es el escalón 2 (core offer 200-1.000); falta diseñar el escalón inferior (lead magnet/tripwire) y los superiores (fee/formación + top tier).
- **skill_pricing**: encadenar para fijar el precio final del servicio estrella usando criterios de valor percibido + rentabilidad + posicionamiento competitivo.
- **skill_propuesta**: usar el output de esta skill como insumo directo para generar la propuesta comercial al cliente concreto.

## Templates used
- **Pre-plantilla para definición de programa.docx** → ./skill_servicio_estrella/Pre-plantilla para definición de programa.docx — Plantilla previa para delimitar alcance, objetivos y estructura base del programa antes de empaquetarlo como servicio estrella.
- **Workbook - Aterriza tu servicio estrella.doc** → ./skill_servicio_estrella/Workbook - Aterriza tu servicio estrella.doc — Workbook guiado para bajar a tierra el servicio estrella: transformación prometida, fases de delivery y nombre de la metodología propia.
- **Workbook - Crea una oferta para tu servicio estrella.doc** → ./skill_servicio_estrella/Workbook - Crea una oferta para tu servicio estrella.doc — Workbook para construir la oferta irresistible: stack de valor, bundling de bonus, precio y versión troceada de respaldo ante objeciones.

## Source modules
modulo2, modulo9, modulo12
