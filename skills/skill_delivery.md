# Skill: Ejecutar entrega con SOPs y reportes

## What this does
Estructura la operación del proyecto con carpetas estándar, SOPs por proceso, tablero de seguimiento y un sistema de reportes que separa la comunicación estratégica (con el sponsor/decisor) de la operativa (con el equipo de implementación).

## When to use it
**Activate this skill when the user:**
- Says: "necesito armar la estructura de carpetas del proyecto con [cliente]"
- Says: "¿cómo le reporto avance al cliente esta semana?"
- Asks to: "armar un SOP para el proceso de [onboarding / publicación / QA / etc.]"
- Asks to: "definir un tablero de proyecto para que el cliente vea el avance"
- Starts a situation like: "el cliente me escribe por mil canales y se me mezclan temas estratégicos con operativos"
- Starts a situation like: "arranco la implementación con un cliente nuevo y quiero dejar todo prolijo desde el día uno"
- Says: "quiero estandarizar cómo entregamos para no reinventar la rueda en cada cliente"
- Asks to: "redactar el reporte semanal / mensual del proyecto"

## How to execute

### Step 1 — Diagnóstico del estado actual de delivery
- **Action**: Identificar en qué fase está el proyecto (kick-off, ejecución temprana, ejecución avanzada, cierre) y qué activos de delivery ya existen vs. faltan.
- **Ask the user for**:
  - Nombre del cliente y tipo de proyecto (consultoría, implementación, retainer mensual)
  - Duración estimada y entregables ya comprometidos
  - Canales actuales de comunicación con el cliente (WhatsApp, mail, Slack, reuniones)
  - Si ya existe carpeta compartida, tablero o documento de scope
- **Produce**: Lista corta de gaps a cubrir en delivery (ej: "falta carpeta compartida", "no hay separación estratégico/operativo", "no hay SOP del proceso X").

### Step 2 — Estructura estándar de carpetas
- **Action**: Proponer y crear la estructura de carpetas del proyecto siguiendo el estándar del consultor.
- **Ask the user for**: Dónde vivirá (Google Drive, Notion, etc.) y si hay convención de nombres previa.
- **Produce**: Árbol de carpetas con esta lógica base (adaptable):
  - `00_Kickoff` (propuesta firmada, scope, contactos, accesos)
  - `01_Estrategia` (decisiones, frameworks aplicados, north star)
  - `02_Ejecución` (entregables vivos, assets, drafts)
  - `03_SOPs` (procesos documentados de este proyecto)
  - `04_Reportes` (semanales y mensuales)
  - `05_Reuniones` (agendas, minutas, grabaciones)
  - `06_Cierre` (handover, lecciones aprendidas)
- **Sugerir**: que el consultor mantenga visibilidad total para el cliente solo en `01`, `02`, `04`, `05`. El resto es interno.

### Step 3 — SOPs por proceso crítico
- **Action**: Identificar 2-4 procesos repetibles del proyecto y redactar un SOP corto para cada uno.
- **Ask the user for**: ¿Qué procesos se repiten semanalmente o mensualmente? (ej: publicación de contenido, generación de leads, QA de campañas, reporting interno).
- **Produce**: Por cada proceso, un SOP con esta estructura:
  - **Objetivo** (en una frase)
  - **Responsable** (quién ejecuta, quién aprueba)
  - **Frecuencia / trigger**
  - **Pasos** (numerados, accionables, con herramientas concretas)
  - **Criterio de "hecho"** (definition of done)
  - **Qué hacer si falla** (escalamiento)

### Step 4 — Separar comunicación estratégica vs operativa
- **Action**: Definir dos canales/cadencias diferenciadas y comunicárselo al cliente.
- **Produce**:
  - **Canal estratégico** (con sponsor/decisor): reunión quincenal o mensual + reporte ejecutivo. Temas: decisiones, riesgos, ROI, cambios de scope.
  - **Canal operativo** (con equipo de implementación): Slack/WhatsApp de proyecto + standup semanal. Temas: tareas, bloqueos, dudas tácticas.
  - **Mensaje sugerido al cliente** explicando el porqué de la separación (evita que el decisor se sature de detalle y que lo táctico se trabe esperando al sponsor).

### Step 5 — Tablero de proyecto visible al cliente
- **Action**: Definir un tablero único (Notion, Trello, Asana, ClickUp) con vista compartida al cliente.
- **Produce**: Estructura mínima del tablero:
  - Columnas: `Backlog` → `En curso` → `Esperando cliente` → `En revisión` → `Hecho`
  - Cada tarea con: responsable, fecha objetivo, entregable asociado, link a carpeta
  - Vista filtrada "Lo que necesitamos del cliente" para destrabar pendientes del lado del cliente.

### Step 6 — Sistema de reportes
- **Action**: Definir cadencia y plantillas de reporte.
- **Produce**:
  - **Reporte semanal operativo** (al equipo del cliente, viernes): 1) Hecho esta semana, 2) En curso, 3) Próxima semana, 4) Bloqueos / pedidos al cliente.
  - **Reporte mensual ejecutivo** (al sponsor): 1) Avance vs objetivos del north star, 2) Métricas clave del mes, 3) Decisiones tomadas, 4) Riesgos abiertos, 5) Foco del próximo mes.
  - Ambos breves, escaneables, con un solo CTA claro al final.

### Step 7 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_delivery/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 8 — Validación con el consultor
- **Action**: Antes de cerrar, mostrar el set completo (estructura + SOPs + canales + tablero + reportes) y pedir ajustes según el cliente puntual.

## Output
Un paquete de delivery listo para implementar:
1. Árbol de carpetas creado (o instrucciones para crearlo)
2. 2-4 SOPs redactados
3. Definición clara de canales estratégico/operativo + mensaje para el cliente
4. Estructura del tablero de proyecto
5. Plantillas de reporte semanal y mensual

Todo entregado en formato markdown copiable, listo para pegar en Notion/Drive.

## Key consulting principles applied
- **Estandarización antes que creatividad operativa**: cada cliente nuevo arranca sobre la misma base; la creatividad va en la estrategia, no en cómo se guarda un archivo.
- **Separar el "qué" del "cómo"**: el sponsor decide el qué (estratégico), el equipo ejecuta el cómo (operativo). Mezclarlos genera ruido y traba decisiones.
- **Visibilidad asimétrica intencional**: el cliente ve lo que necesita ver para confiar y decidir; no todo el detrás de escena.
- **Reportes como producto**: un buen reporte vende el siguiente mes de retainer.
- **SOPs hacen el negocio escalable**: sin SOPs, el consultor es el cuello de botella.

## Chains with
- **skill_planificacion_proyecto**: cuando arranca un proyecto nuevo, primero se planifica el scope y luego se monta la estructura de delivery con esta skill.
- **skill_medicion**: los reportes mensuales ejecutivos consumen las métricas y north star definidos en la skill de medición.
- **skill_cierre_proyecto**: al final del proyecto, la carpeta `06_Cierre` y los SOPs alimentan el handover y las lecciones aprendidas.

## Templates used
- **PLANTILLA ADC- Reporte de proyecto.xlsx** → ./skill_delivery/PLANTILLA ADC- Reporte de proyecto.xlsx — Planilla de reporte ejecutivo del proyecto (avance, hitos, riesgos) para el sponsor/decisor.
- **PLANTILLA ADC- Reporte de tareas.xlsx** → ./skill_delivery/PLANTILLA ADC- Reporte de tareas.xlsx — Planilla operativa de seguimiento de tareas (estado, responsable, fechas) para el equipo de implementación.

## Source modules
modulo6, modulo11
