# Skill: Fijar precio y validar margen

## What this does
Guía al agente para construir el precio de un servicio de consultoría usando la fórmula de tres patas + autoevaluación RVR, validar que el margen sea ≥30% y dejar armado el tarifario interno (costo / precio cliente / % margen) listo para cotizar ágil.

## When to use it
**Activate this skill when the user:**
- Says: "no sé cuánto cobrar por esto"
- Says: "tengo que subir la tarifa pero no sé cuánto"
- Asks to: "calculá el margen de este servicio"
- Asks to: "armame el tarifario interno"
- Asks to: "validá si este precio cierra"
- Starts a situation like: "el cliente me pidió presupuesto y quiero cotizar por valor, no por hora"
- Starts a situation like: "estoy armando un nuevo paquete y necesito ponerle precio"
- Says: "quiero aplicar la fórmula de pricing / RVR"

## How to execute

### Step 1 — Mapear delivery cost real
- **Action**: Listar TODO lo que cuesta entregar el servicio una vez: software/licencias, horas propias valuadas, horas de equipo/freelancers, gastos de representación, comisiones de pasarela, colchón del 10-15%.
- **Ask the user for**: alcance del servicio (qué entrega), duración estimada en horas, herramientas que usa, si delega parte del trabajo y a qué costo.
- **Produce**: número único de delivery cost con desglose visible (no se muestra al cliente).

### Step 2 — Calcular precio piso por fórmula de tres patas
- **Action**: Aplicar las tres patas en simultáneo y tomar el MAYOR como piso defendible:
  1. **Pata costo**: delivery cost × 2 a × 3 (margen mínimo objetivo).
  2. **Pata valor/retorno**: el retorno proyectado al cliente debe ser ≥ 10× el precio. Si no llega, replantear el alcance o el target.
  3. **Pata mercado**: comparar contra Fiverr, Upwork, competencia directa local. Ubicar el precio en el tercio superior si la metodología lo justifica.
- **Ask the user for**: retorno esperado del cliente (ingresos extra, ahorro, conversiones), 2-3 referencias de competencia.
- **Produce**: precio piso + rango sugerido (piso a techo de mercado).

### Step 3 — Autoevaluación RVR
- **Action**: Validar el precio con tres preguntas. Si alguna falla, NO avanzar:
  - **R (Recursos)**: ¿tengo el tiempo, equipo y herramientas para entregar a este precio sin quemarme?
  - **V (Valor)**: ¿la propuesta comunica claramente la transformación, o el cliente solo va a ver el número?
  - **R (Retorno)**: ¿el retorno proyectado al cliente justifica este precio sin que tenga que "creerme"?
- **Ask the user for**: confirmación honesta de cada pata; si alguna es "no", recortar alcance o subir precio antes de seguir.
- **Produce**: precio validado o ajuste de alcance.

### Step 4 — Validar margen ≥30%
- **Action**: Calcular `margen % = (precio cliente − delivery cost) / precio cliente`. Si <30%, alertar y ofrecer dos caminos: subir precio o recortar alcance (nunca aceptar margen bajo "para entrar").
- **Ask the user for**: nada nuevo — usar Step 1 y Step 2.
- **Produce**: margen % numérico + semáforo (verde ≥40%, amarillo 30-40%, rojo <30%).

### Step 5 — Armar dos opciones con gap amplio
- **Action**: Generar SOLO dos versiones con diferencia clara: mínimo viable vs. all-in. Nunca tres planes parecidos. La diferencia debe ser de alcance, no de "más sesiones del mismo".
- **Ask the user for**: qué se puede sacar sin romper la promesa central, qué add-ons agregan retorno exponencial.
- **Produce**: tabla de dos opciones con precio, alcance, entregables y KPI asociado.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_pricing/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Volcar al tarifario interno
- **Action**: Agregar/actualizar fila en el tarifario interno con columnas: servicio | delivery cost | precio cliente | margen % | retorno esperado x | condiciones (anticipo mínimo 30-50%, permanencia, mora). Generar también la versión simplificada para el cliente (solo servicio + precio + entregables).
- **Ask the user for**: confirmación del precio final elegido entre las dos opciones de Step 5.
- **Produce**: dos vistas del tarifario — interna (con costos y margen) y cliente (sin costos).

## Output
Documento con:
1. Delivery cost desglosado.
2. Precio piso justificado por las tres patas.
3. Autoevaluación RVR (3 checks).
4. Margen % con semáforo.
5. Dos opciones con gap amplio (mínimo viable vs. all-in).
6. Fila lista para pegar en el tarifario interno + versión cliente.
7. Racional escrito de una frase para defender el precio en negociación.

## Key consulting principles applied
- El cliente compra transformación, no horas: el precio se construye por valor.
- El precio se justifica ANTES de mostrarse; no se improvisa.
- Si bajás el precio, bajás el alcance — siempre van juntos.
- Margen <30% es una alarma, no una decisión válida.
- Dos opciones con gap amplio convierten más que tres planes parecidos.
- El tarifario interno nunca se comparte con el cliente.
- "Tiene que dolernos a los dos": anticipo del 30-50% es innegociable.

## Chains with
- skill_propuesta: una vez validado el precio y el margen, encadenar para empaquetar la propuesta vertical, anclar el valor antes del número y dejar los enlaces de pago listos.
- skill_negociacion: si el cliente objeta el precio, usar esta skill para defender el racional y recortar alcance sin tocar la tarifa.

## Templates used
- **PLANTILLA ADC - CALCULADORA - CUÁNTO CUESTA TU HORA.xlsx** → ./skill_pricing/PLANTILLA ADC - CALCULADORA - CUÁNTO CUESTA TU HORA.xlsx — calculadora para valuar la hora propia y alimentar el delivery cost del Step 1.
- **Tarifario proveedores.xlsx** → ./skill_pricing/Tarifario proveedores.xlsx — referencia de costos de equipo/freelancers/herramientas para sumar al delivery cost.
- **calculadora Rentabilidad servicios y oferta.xlsx** → ./skill_pricing/calculadora Rentabilidad servicios y oferta.xlsx — calculadora de precio cliente, margen % y armado de las dos opciones de oferta (Steps 4-6).

## Source modules
modulo3, modulo7, modulo8
