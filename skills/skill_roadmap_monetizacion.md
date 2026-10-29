# Skill: Roadmap de monetización a 12 meses

## What this does
Construye un plan anual escalonado mes a mes que define cuándo lanzar cada servicio, mentoring, producto digital o evento, con proyección de facturación realista y secuencia lógica de monetización.

## When to use it
**Activate this skill when the user:**
- Says: "necesito un plan anual para mi negocio"
- Says: "no sé cuándo lanzar cada cosa"
- Asks to: "armar un roadmap de lanzamientos para los próximos 12 meses"
- Asks to: "hacer una proyección de facturación mensual"
- Starts a situation like: "tengo varias ideas de servicios y productos pero no sé en qué orden sacarlos"
- Says: "quiero escalar mi consultoría pero no tengo claro el plan"
- Says: "cuándo me conviene lanzar mi mentoring/curso/evento"
- Asks to: "ordenar mis lanzamientos del año"

## How to execute

### Step 1 — Diagnóstico de punto de partida
- **Action**: Mapear el estado actual del negocio antes de proyectar.
- **Ask the user for**:
  - Servicios activos hoy y facturación promedio mensual
  - Capacidad operativa actual (horas disponibles, equipo, tiempo de delivery)
  - Audiencia/comunidad existente (tamaño de lista, redes, clientes activos)
  - Productos o ideas en bandeja (mentoring, cursos, eventos pendientes)
  - Ingreso objetivo a 12 meses
- **Produce**: Snapshot inicial con baseline de facturación y assets disponibles.

### Step 2 — Definir el servicio estrella como ancla
- **Action**: Identificar el servicio principal (alta ticket, alta margen) que sostiene el año.
- **Ask the user for**: Cuál es el servicio con mejor ratio precio/esfuerzo y demanda probada.
- **Produce**: Servicio estrella definido con meta de ventas mensuales y trimestrales que cubran el piso de facturación.

### Step 3 — Secuenciar la escalera de monetización
- **Action**: Ordenar los lanzamientos según lógica de madurez de audiencia y carga operativa. Regla general:
  - **Q1 (mes 1-3)**: Consolidar servicio estrella + ordenar oferta base
  - **Q2 (mes 4-6)**: Lanzar mentoring grupal o programa intermedio (apalanca servicio 1:1)
  - **Q3 (mes 7-9)**: Producto digital escalable (curso, template, membresía)
  - **Q4 (mes 10-12)**: Evento, lanzamiento premium o ticket alto que cierre el año
- **Ask the user for**: Restricciones de calendario (vacaciones, temporadas bajas del rubro, fechas no negociables).
- **Produce**: Calendario trimestral con un "lanzamiento ancla" por trimestre.

### Step 4 — Detallar mes a mes con foco único
- **Action**: Para cada mes asignar UN foco principal (lanzamiento, build, nurturing o descanso). Evitar superponer lanzamientos.
- **Produce**: Tabla de 12 meses con columnas: Foco del mes | Lanzamiento activo | Build en preparación | Acción comercial | Meta de facturación.

### Step 5 — Proyección de facturación realista
- **Action**: Calcular ingresos mes a mes combinando:
  - Servicio estrella (recurrente)
  - Lanzamientos puntuales (ingreso pico)
  - Productos pasivos (ingreso acumulativo)
- Aplicar factor de conservadurismo: tomar 60-70% de la meta optimista para el escenario base.
- **Produce**: Proyección con tres escenarios (conservador, base, optimista) y total anual.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_roadmap_monetizacion/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Definir hitos de revisión
- **Action**: Marcar checkpoints trimestrales para revisar y ajustar el plan.
- **Produce**: 4 fechas de revisión con preguntas guía: ¿se cumplió la meta?, ¿el lanzamiento validó hipótesis?, ¿hay que mover el siguiente?

## Output
Documento con:
1. **Snapshot inicial** (baseline + assets)
2. **Servicio estrella y meta anual**
3. **Calendario trimestral** con lanzamientos ancla
4. **Tabla mensual 12 meses** con foco único por mes
5. **Proyección de facturación** en 3 escenarios
6. **Calendario de revisión** con checkpoints trimestrales

## Key consulting principles applied
- Un solo lanzamiento ancla por trimestre — evitar dispersión.
- El servicio estrella sostiene el piso; los lanzamientos suman picos.
- Secuencia: primero monetizar lo que ya tenés, después construir lo nuevo.
- Proyectar siempre en escenarios — el plan único miente.
- Cada producto nuevo debe apalancar la audiencia que dejó el anterior.
- Meses de build no facturan menos: preparan el siguiente pico.

## Chains with
- skill_escalera_servicios: definir antes la escalera completa de oferta para saber qué se está secuenciando en el roadmap.
- skill_finanzas: cruzar la proyección con costos fijos, punto de equilibrio y flujo de caja real.
- skill_productizar: cuando un trimestre requiere lanzar un producto digital o mentoring, ejecutar el detalle de productización ahí.

## Templates used
- **PLANTILLA ADC - Plan de monetización .xlsx** → ./skill_roadmap_monetizacion/PLANTILLA ADC - Plan de monetización .xlsx — planilla maestra para volcar el plan anual de monetización con calendario de lanzamientos y proyección de facturación mes a mes.

## Source modules
modulo8, modulo9
