# Skill: Finanzas del consultor (CIMER)

## What this does
Guía al consultor a montar un sistema financiero defensivo (colchón de 18-20 meses, semáforo de cobros, mix 50/50 de ingresos recurrentes vs proyecto, poda trimestral de gastos y uso inteligente de palanca crediticia) para que las decisiones del negocio se tomen con caja real, no con facturación proyectada.

## When to use it
**Activate this skill when the user:**
- Says: "tengo que ordenar las finanzas del negocio" / "no sé cuánta plata tengo realmente"
- Asks to: "armarme un colchón de tesorería" / "calcular cuántos meses aguanto si dejo de facturar"
- Says: "los clientes me pagan tarde y estoy ahogado" / "necesito un sistema para cobrar mejor"
- Asks to: "revisar gastos y ver qué puedo cortar" / "hacer una poda trimestral"
- Starts a situation like: "facturo bien pero no me queda nada" o "vivo del próximo proyecto"
- Says: "quiero más ingresos recurrentes y menos depender de proyectos puntuales"
- Asks about: "si me conviene pedir un préstamo / línea de crédito para X"
- Says: "no separo la plata personal de la del negocio y es un quilombo"

## How to execute

### Step 1 — Foto de caja real y colchón objetivo
- **Action**: Calcular cuánto efectivo líquido tiene hoy el negocio y a cuántos meses de gastos fijos equivale. Definir el colchón objetivo de 18-20 meses como meta defensiva.
- **Ask the user for**: saldo actual de la cuenta del negocio (separada de la personal), gastos fijos mensuales del negocio + sueldo fijo que el consultor se paga, deudas vigentes y vencimientos próximos.
- **Produce**: ratio "meses de runway actuales" (caja ÷ gasto fijo mensual) + brecha hasta el colchón de 18-20 meses + alerta si no hay cuenta separada o sueldo fijo asignado.

### Step 2 — Semáforo de cobros
- **Action**: Clasificar a cada cliente activo en verde / amarillo / rojo según comportamiento de pago, y definir acción concreta para cada uno.
- **Ask the user for**: lista de clientes activos con monto facturado pendiente, días promedio de pago real vs lo pactado, condiciones contractuales (anticipo, hitos, vencimiento).
- **Produce**: tabla con columnas Cliente / Monto pendiente / Días de atraso / Color del semáforo / Acción (recordatorio, recargo, pausa de servicio, reestructurar contrato, cortar). Verde = paga ≤ vencimiento. Amarillo = atrasos puntuales. Rojo = atrasos sistemáticos o + 30 días.
- **Action complementaria**: proponer cláusulas estándar para futuros contratos (50% anticipo, intereses por mora, pausa automática del servicio).

### Step 3 — Mix de ingresos 50/50
- **Action**: Auditar la facturación de los últimos 3-6 meses y separarla en Recurrente (retainer, mentoring, suscripción, mantenimiento) vs Proyecto puntual. Apuntar al objetivo 50/50.
- **Ask the user for**: facturación mensual desglosada por tipo de servicio y cliente.
- **Produce**: % actual recurrente vs proyecto + brecha contra el 50/50 + lista priorizada de palancas para subir lo recurrente (productizar el core offer en retainer, escalón de mentoring, comunidad paga, mantenimiento post-entrega). Cruzar con `skill_pricing` y `skill_roadmap_monetizacion` si corresponde diseñar nuevos escalones.

### Step 4 — Poda trimestral de gastos
- **Action**: Listar todos los gastos del negocio y clasificarlos en Esenciales / Productivos / Cortables, y eliminar los cortables ya mismo.
- **Ask the user for**: extractos o lista de suscripciones, herramientas SaaS, freelancers fijos, oficina, gastos de marketing, otros.
- **Produce**: tabla con Gasto / Monto mensual / Categoría / ¿Mueve la aguja del ingreso? / Decisión (mantener, renegociar, cortar) + monto total ahorrado por trimestre + fecha de la próxima poda agendada.

### Step 5 — Palanca crediticia (defensiva, no compulsiva)
- **Action**: Evaluar si tiene sentido tomar deuda y bajo qué reglas. La palanca se usa para acelerar ingreso comprobado, no para tapar agujeros de caja.
- **Ask the user for**: líneas de crédito disponibles (tarjeta, banco, cuenta corriente), tasa, plazo, propósito que evalúa.
- **Produce**: checklist de aprobación: (1) ¿el destino tiene ROI medible y horizonte ≤ 12 meses?, (2) ¿la cuota cabe sin tocar el sueldo fijo del consultor?, (3) ¿el colchón sigue ≥ 6 meses después de tomarla?, (4) ¿hay plan B si el ROI no aparece?. Si falla cualquiera → no tomar.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_finanzas/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow). Para el semáforo de cobros del Step 2 usar `PLANTILLA ADC- Gestión de Cobros.xlsx`; para el mix de ingresos del Step 3 usar `PLANTILLA ADC- Reporte de facturación.xlsx`.
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Tablero mensual y ritual de revisión
- **Action**: Consolidar todo en un tablero financiero mensual de 1 hora (alineado con la Auditoría del módulo 2) que el consultor revise el mismo día de cada mes.
- **Produce**: tablero con bloques: (a) Caja y meses de runway, (b) Semáforo de cobros del mes, (c) Mix recurrente/proyecto, (d) Top 3 gastos a podar el próximo trimestre, (e) Estado de deuda, (f) Decisión accionable del mes. Recordar al usuario agendar la siguiente revisión.

## Output
Un **Plan financiero del consultor** entregable con:
1. Foto de caja + meses de runway + brecha al colchón 18-20 meses.
2. Semáforo de cobros con acción por cliente.
3. % actual de mix recurrente vs proyecto y palancas para llegar a 50/50.
4. Lista de poda trimestral con monto ahorrado.
5. Reglas de uso de palanca crediticia (4 checks).
6. Tablero mensual + fecha del próximo review.

## Key consulting principles applied
- **Datos sobre intuición**: lo único cierto es lo que hay en el banco.
- **Cuenta separada y sueldo fijo del consultor**: facturación ≠ ganancia.
- **Rentabilidad mínima 30%, ideal 50%**: si no llega, ajustar antes de firmar.
- **Nunca todos los huevos en una canasta**: mix 50/50 protege contra la pérdida del cliente ancla.
- **Filtrar sin miedo**: cliente que paga mal se pausa o se corta, no se subsidia.
- **Defensa antes que ataque**: primero colchón y cobros, después crecimiento e inversión.
- **Lo que no se mide se autoengaña**: ritual mensual fijo, no "cuando me acuerde".

## Chains with
- **skill_pricing**: cuando el mix 50/50 exige rediseñar tickets, retainers o subir precio para cerrar la brecha de runway.
- **skill_roadmap_monetizacion**: cuando para llegar al 50/50 hay que crear nuevos escalones de ingreso recurrente (mentoring, comunidad, mantenimiento, productos digitales).

## Templates used
- **PLANTILLA ADC- Gestión de Cobros.xlsx** → ./skill_finanzas/PLANTILLA ADC- Gestión de Cobros.xlsx — Planilla de seguimiento de cobros por cliente con semáforo (monto pendiente, días de atraso, acción a ejecutar) para alimentar el Step 2.
- **PLANTILLA ADC- Reporte de facturación.xlsx** → ./skill_finanzas/PLANTILLA ADC- Reporte de facturación.xlsx — Reporte mensual de facturación desglosado por cliente y tipo de servicio para auditar el mix recurrente vs proyecto del Step 3 y trackear evolución de ingresos.

## Source modules
modulo8, modulo2
