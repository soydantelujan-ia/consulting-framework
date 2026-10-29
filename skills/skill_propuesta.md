# Skill: Crear propuestas de cliente

## What this does
Guía al agente para construir una propuesta vertical estilo americano que vende transformación antes que precio, con diagnóstico medible, objetivos SMART, plan mes 1-2-3, KPIs y tarifa defendida por valor.

## When to use it
**Activate this skill when the user:**
- Says: "armame una propuesta para [cliente]"
- Says: "tengo que mandar la oferta a [prospecto]"
- Asks to: "preparar una cotización para esta reunión"
- Asks to: "armar la PPT comercial para presentar mañana"
- Starts a situation like: "el cliente quedó interesado en la call, ahora qué le mando"
- Starts a situation like: "tengo el briefing listo y quiero pasar a propuesta"
- Says: "necesito empaquetar este servicio para venderlo"
- Says: "el cliente me pidió que le pase algo por escrito"

## How to execute

### Step 1 — Recuperar briefing y diagnóstico
- **Action**: Verificar si ya existe un diagnóstico previo (skill_diagnostico). Si no hay, pedir el briefing mínimo antes de avanzar. No improvisar la propuesta sin diagnóstico medible.
- **Ask the user for**: nombre y rubro del cliente, dolor principal con sus propias palabras, objetivo de negocio del cliente, audiencia, competencia, presupuesto tentativo si lo blanqueó, plazos esperados, resultado del diagnóstico puntuado (si existe).
- **Produce**: ficha cliente + diagnóstico con score visual (estrellas o puntaje por eje) que muestra el "antes".

### Step 2 — Definir objetivos SMART en tres niveles
- **Action**: Traducir el objetivo de negocio del cliente a objetivo del área (en formato S.M.A.R.T., usando verbos como "aumentar") y a 2-3 objetivos secundarios. Asociar a cada uno entregables y un KPI con línea base medida hoy. La fórmula completa del KPI no se revela.
- **Ask the user for**: métricas actuales del cliente (línea base) si están disponibles; si no, marcarlas como "a medir en semana 1".
- **Produce**: tabla objetivos × estrategias × tácticas × KPIs (formato one-page).

### Step 3 — Construir el precio (fórmula 3 patas + RVR)
- **Action**: Invocar skill_pricing si está disponible. Si no, calcular: delivery cost (software + horas propias y de equipo) × 2 a 3 como piso. Validar que el retorno proyectado al cliente sea ≥ x10. Cruzar con tolerancia de mercado. Aplicar autoevaluación RVR (Recursos / Valor comunicado / Retorno justifica precio). Armar **dos opciones con gap amplio** (mínimo viable vs. all-in), nunca tres planes parecidos.
- **Ask the user for**: costos internos estimados, horas propias, software involucrado, referencia de mercado si la tiene.
- **Produce**: precio defendido con racional escrito + 2 paquetes con gap amplio + presupuesto en hoja aparte.

### Step 4 — Empaquetar la propuesta vertical (estructura americana)
- **Action**: Generar documento vertical de ~10 páginas con 6-8 bloques en este orden estricto:
  1. Intro personalizada (usar las palabras clave del cliente)
  2. Diagnóstico con score visual
  3. Objetivos (máx. 5)
  4. Propuesta estratégica (separar asesoría vs. implementación)
  5. Plan de trabajo en **mes 1 / mes 2 / mes 3** (regla del edificio: base → construcción → resultados; NUNCA fechas de calendario)
  6. Inversión (al final, no antes)
  7. Requerimientos al cliente
  8. Condiciones (anticipo mínimo 30%, mora por atrasos, revisión periódica de tarifas, permanencia)
- **Action adicional**: Sumar 10-15% de colchón a plazos. Reemplazar negaciones por positivos. Incluir 1-2 metáforas educativas (árbol/frutos, edificio, tienda pop-up).
- **Produce**: propuesta vertical (~10 páginas) + diapositiva one-page resumen + presupuesto separado.

### Step 5 — Preparar entrega y stack de cobro
- **Action**: Definir canal de entrega:
  - Si es **reunión presencial/sincrónica**: entregar el mismo día. Mostrar precio solo al final, después de vender transformación.
  - Si es **asincrónico**: preparar guion Loom de 7-10 min (saltando intro, yendo a objetivos → plan → cronograma → KPIs jugosos → precio). El PDF nunca se adjunta al email; el link va como comentario.
- **Action**: Listar 3 enlaces de pago (único / fraccionado / reserva) listos antes de presentar.
- **Ask the user for**: canal preferido del cliente, fecha de presentación, si ya tiene los enlaces armados en Thrivecart u otro.
- **Produce**: plan de entrega + guion Loom (si aplica) + checklist de enlaces de pago.

### Step 6 — Checklist pre-envío
- **Action**: Antes de marcar la propuesta como lista, correr este checklist:
  - Buscar el nombre del cliente anterior (no debe quedar nada de otra propuesta)
  - Ortografía y números coherentes
  - Tablas que sumen
  - Cotejo punto por punto contra el brief
  - Datos de contacto del consultor correctos
  - Numeración de páginas
  - Que el precio aparezca solo al final
- **Produce**: propuesta validada lista para enviar.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos). Para propuestas a cliente la opción default es la plantilla v3 editable (.pptx); si el cliente pidió algo más simple, usar la plantilla one-page; si es específicamente redes sociales, usar la de redes sociales; si necesitás referencia de un caso completo, mirá el ejemplo de propuesta de marketing online.
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_propuesta/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 8 — Anticipar negociación y registrar el ratio
- **Action**: Preparar al consultor para objeciones: si el cliente pide rebaja, **bajar alcance, nunca tarifa**. Sugerir guion: silencio breve → mantener postura → recortar entregables (de A,B,C,D a solo A,B) → cotizar el resto como add-on. En modelos fee + comisión: ceder en fee diluido en más meses, nunca en comisión. Encadenar con skill_negociacion.
- **Action**: Recordar al consultor registrar la propuesta en su tracker de ratio (benchmark: 3 de 7 = 42%). Si <42%, ajustar audiencia → oferta → precio en ese orden.
- **Produce**: mini-guion de objeciones + recordatorio de tracking.

## Output
Un paquete completo:
1. **Propuesta vertical** ~10 páginas (Doc/PDF/PPT) con diagnóstico, objetivos SMART, plan mes 1-2-3, inversión y condiciones
2. **One-page resumen** (tabla objetivos × estrategias × tácticas × KPIs, imprimible A3)
3. **Presupuesto en hoja aparte** con 2 opciones de gap amplio
4. **Plan de entrega** (presencial / Loom) con 3 enlaces de pago listos
5. **Checklist pre-envío** corrido y validado
6. **Mini-guion de negociación** para defender precio bajando alcance

## Key consulting principles applied
- El cliente compra transformación y velocidad, no horas: precio por valor.
- Mostrar metodología antes que solución: se vende el método, no la respuesta.
- El precio se construye, se justifica y se ancla al valor antes de mostrarse.
- Si bajás el precio, bajás el alcance — siempre van juntos.
- Rapidez (mismo día + enlaces listos) multiplica el ratio de cierre.
- Educar con metáforas convierte mejor que enumerar features.
- La validación del servicio es un número (3/7 = 42%), no una sensación.
- "Tiene que dolernos a los dos": anticipo + permanencia + recurrencia alinean compromiso.
- Nunca adjuntar PDF al email: el cliente salta al precio y mata la venta.
- Dos opciones con gap amplio, nunca tres planes parecidos.

## Chains with
- skill_diagnostico: ejecutar antes para tener el "antes" puntuado que abre la propuesta.
- skill_pricing: invocar en Step 3 para construir y defender la tarifa.
- skill_negociacion: encadenar después de presentar, cuando aparezcan objeciones de precio.
- skill_contrato: encadenar al cierre, una vez aceptada la propuesta y cobrado el anticipo.

## Templates used
- **Palabras a utilizar durante la presentación de una propuesta.docx** → ./skill_propuesta/Palabras a utilizar durante la presentación de una propuesta.docx — Glosario de palabras y frases recomendadas para usar al presentar la propuesta y vender transformación antes que precio.
- **Plantilla+editable+para+hacer+propuestas+Marketing+v3+(Keynote-Mac).pptx** → ./skill_propuesta/Plantilla+editable+para+hacer+propuestas+Marketing+v3+(Keynote-Mac).pptx — Plantilla v3 editable de propuesta de marketing en PowerPoint para armar la propuesta vertical estilo americano (~10 páginas, 6-8 bloques).

## Source modules
modulo3, modulo9
