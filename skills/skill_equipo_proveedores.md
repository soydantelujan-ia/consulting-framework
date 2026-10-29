# Skill: Construir equipo y banco de proveedores

## What this does
Guía al consultor para resolver cada tarea con el nivel mínimo de apalancamiento necesario (software → proveedor → empleado) y construir un banco de proveedores con plan A/B y acuerdos básicos antes de delegar.

## When to use it
**Activate this skill when the user:**
- Says: "necesito delegar esto, no llego"
- Says: "estoy pensando en contratar a alguien"
- Asks to: "ayudame a armar mi equipo"
- Asks to: "armemos un banco de freelancers / proveedores"
- Starts a situation like: "tengo que subcontratar diseño/edición/dev para este proyecto"
- Says: "no sé si contratar empleado o tercerizar"
- Says: "se me cayó el proveedor X y no tengo backup"
- Says: "quiero escalar pero soy cuello de botella"

## How to execute

### Step 1 — Inventario de tareas a delegar
- **Action**: Listar todas las tareas que el consultor está haciendo y que considera candidatas a delegar. Para cada una, pedir frecuencia (única / recurrente), criticidad (core del servicio / soporte) y horas/mes estimadas.
- **Ask the user for**: lista de tareas, contexto de cada una, qué pasa hoy si no las hace él.
- **Produce**: tabla `tarea | frecuencia | criticidad | horas/mes | costo de oportunidad`.

### Step 2 — Test de nivel de apalancamiento
- **Action**: Para cada tarea, aplicar la escalera en orden y quedarse en el primer nivel que resuelva:
  1. **Eliminar** — ¿es necesaria?
  2. **Automatizar con software** — ¿hay una herramienta/plantilla/IA que lo resuelva?
  3. **Proveedor / freelancer** — ¿se puede comprar por proyecto u hora?
  4. **Empleado part-time / full-time** — solo si es recurrente, core, y justifica costo fijo.
- **Ask the user for**: validación de cada decisión y restricciones (presupuesto, urgencia).
- **Produce**: tabla con la decisión de nivel por tarea y justificación de una línea.

### Step 3 — Definir perfiles a buscar
- **Action**: Para cada tarea que requiera proveedor o empleado, redactar un mini-perfil: skill concreta, entregable esperado, nivel de seniority, rango de tarifa de mercado, modalidad (proyecto / fee mensual / hora).
- **Ask the user for**: referencias de tarifas que conoce, casos previos buenos/malos.
- **Produce**: ficha de perfil por rol.

### Step 4 — Armar banco con plan A y plan B
- **Action**: Para cada perfil, identificar mínimo 2 candidatos (plan A titular + plan B backup). Si el usuario no tiene contactos, sugerir canales de búsqueda (referidos, comunidades, Workana/Upwork/Malt, LinkedIn) y un proceso corto de prueba pagada.
- **Ask the user for**: nombres y contactos que ya tenga; bloqueos para conseguir backup.
- **Produce**: banco de proveedores con `rol | plan A | plan B | tarifa | estado (probado/sin probar) | última colaboración`.

### Step 5 — Acuerdo mínimo y forma de trabajo
- **Action**: Para cada proveedor activo, dejar por escrito: alcance, entregables, plazo, forma y momento de pago, propiedad intelectual, NDA si aplica, canal de comunicación, SLA de respuesta. Usar plantilla de orden de trabajo / contrato simple.
- **Ask the user for**: condiciones que ya pactó verbalmente y huecos que tiene.
- **Produce**: orden de trabajo o contrato corto firmado por proveedor.

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_equipo_proveedores/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Protocolo de delegación y control
- **Action**: Definir cómo entrega el brief, cómo revisa, qué KPIs mira (calidad, tiempo, retrabajo), y umbral para activar plan B. Proponer revisión trimestral del banco.
- **Produce**: checklist de delegación + criterio de reemplazo.

## Output
Un documento "Banco de equipo y proveedores" con:
1. Tabla de tareas con nivel de apalancamiento decidido.
2. Fichas de perfiles requeridos.
3. Banco con plan A/B por rol, tarifas y estado.
4. Plantilla de orden de trabajo / contrato corto.
5. Checklist de delegación y criterio para activar el backup.

## Key consulting principles applied
- Subir un nivel de apalancamiento solo cuando el anterior no alcanza — no contratar empleado si un software o un freelancer resuelve.
- Nunca depender de un único proveedor en tareas críticas: siempre plan A + plan B.
- Delegar requiere brief, acuerdo escrito y KPI; sin eso no es delegar, es esperar.
- El costo real de una tarea propia es el costo de oportunidad de no estar vendiendo o entregando.
- Probar con un encargo chico pagado antes de adjudicar volumen.

## Chains with
- skill_planificacion_proyecto: cuando el banco se arma para ejecutar un proyecto concreto, los proveedores se cargan como recursos del plan.
- skill_finanzas: para validar que el costo de proveedores/empleados entra en la estructura de márgenes y pricing del servicio.

## Templates used
- **Tarifario proveedores.xlsx** → ./skill_equipo_proveedores/Tarifario proveedores.xlsx — planilla maestra para registrar proveedores y freelancers con sus tarifas, modalidad de contratación y datos de contacto; base operativa del banco con plan A/B.

## Source modules
modulo7
