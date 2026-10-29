# Skill: Sistema de medición y OKRs

## What this does
Guía al agente para diseñar (o auditar) el sistema de medición de un cliente: define preguntas de decisión, traduce a OKRs trimestrales con KRs binarios, configura GA correctamente, suma investigación cualitativa y benchmark externo, y cierra el loop trimestral de aprendizaje.

## When to use it
**Activate this skill when the user:**
- Says: "necesito definir KPIs para mi cliente"
- Says: "armemos los OKRs del trimestre"
- Asks to: "auditar Google Analytics de la cuenta"
- Asks to: "armar un plan de medición"
- Starts a situation like: "el cliente no sabe qué métricas mirar / mira 30 métricas y no decide nada"
- Says: "quiero hacer un benchmark contra la competencia"
- Says: "no tengo claro si los datos que veo son confiables"
- Asks to: "diseñar una encuesta o investigación para entender el porqué"

## How to execute

### Step 1 — Definir la pregunta de decisión
- **Action**: Antes de tocar herramientas, forzar la conversación hacia qué decisión de negocio depende del dato. Recorrer el negocio del cliente como usuario promedio y listar macro y micro conversiones.
- **Ask the user for**: ¿Qué decisión vas a tomar con esta información? ¿Quién la usa? ¿Para cuándo la necesitás? ¿El beneficio de medirlo supera el costo?
- **Produce**: Documento de Necesidad de Medición (pregunta de decisión, audiencia, deadline, criterio costo/beneficio, macro y micro conversiones).

### Step 2 — Diseñar OKRs trimestrales y Plan de Medición
- **Action**: Traducir las preguntas de decisión a 3-5 Objetivos trimestrales con hasta 5 Resultados Clave binarios (se cumplen o no) cada uno, mezclando cuantitativo y cualitativo. Mapear cada KR a su fuente: primaria (encuestas, entrevistas, focus, experimentos), secundaria (GA, Search Console, industria) o de visibilidad (SSI, búsquedas en LinkedIn).
- **Ask the user for**: prioridades estratégicas del trimestre, equipo involucrado, fuentes ya disponibles, herramientas contratadas.
- **Produce**: Plan de Medición con OKRs en cascada (empresa → equipo → individuo), KPIs asociados, fuentes asignadas, frecuencia de revisión y reportes/alertas previstos.

### Step 3 — Auditar y configurar el sistema de captura
- **Action**: Revisar la cuenta de GA y montar las 3 vistas estándar: 01-Máster, 02-Sin Modificar (red de seguridad), 03-Pruebas. Configurar filtros de IPs internas, normalización de mayúsculas, slash final y UTMs. Validar el tag con GAChecker / Tag Assistant. Para métricas volátiles (apariciones en búsquedas de LinkedIn, SSI), montar plantilla semanal antes de que se borren.
- **Ask the user for**: accesos de GA / GTM / LinkedIn, IPs a excluir, dominios y subdominios involucrados.
- **Produce**: Entorno analítico configurado + plantilla semanal de captura + Auditoría GA con plan de acciones correctivas.

### Step 4 — Investigar el porqué (cualitativo)
- **Action**: Complementar lo cuantitativo con el proceso de 5 pasos (identificar → diseñar → ejecutar → analizar → reportar). Bosquejar primero el reporte final, recién después redactar preguntas aplicando las 10 reglas. Sumar entrevistas, focus groups, mapas de calor y grabaciones de sesión cuando aplique.
- **Ask the user for**: hipótesis a validar, perfil de respondentes, canal de contacto, plazo.
- **Produce**: Insights validados con evidencia mixta (qué + por qué) listos para sustentar recomendaciones.

### Step 5 — Benchmark y referencia externa
- **Action**: Elegir tipo de benchmark (interno, funcional, competitivo o cooperativo) según el problema. Identificar al nº1 del proceso clave (no necesariamente del sector), recolectar datos públicos/técnicos y analizar con flujos u organigramas. Comparar SSI contra promedio del sector y red.
- **Ask the user for**: proceso o capacidad a comparar, competidores y referentes admirados (dentro y fuera del sector).
- **Produce**: Informe de Benchmark con brechas detectadas y oportunidades de diferenciación (no de imitación).

### Step 6 — Generar el deliverable a partir de la plantilla
- **Action**: Identificá la plantilla más adecuada (ver "Templates used" abajo). Si hay varias, elegí la que mejor calce con el caso (ej. .pptx para presentaciones a cliente, .xlsx para cálculos/tablas, .docx para textos largos).
- **Stack técnico**:
  - `.pptx` → `python-pptx` (`from pptx import Presentation`)
  - `.xlsx` → `openpyxl` (`from openpyxl import load_workbook`)
  - `.docx` → `python-docx` (`from docx import Document`)
  - Si las libs faltan: `pip install python-pptx openpyxl python-docx pypdf`
- **Pasos concretos**:
  1. Confirmá con el usuario el slug del cliente (kebab-case, sin acentos). Crealo en `workspace/clientes/<slug>/` si no existe.
  2. Copiá la plantilla elegida desde `consulting-framework/skills/skill_medicion/<archivo>` a `workspace/clientes/<slug>/NN_<nombre>.<ext>` (NN según el orden del workflow).
  3. Abrí la copia con la lib correspondiente, recorré la estructura (slides/hojas/párrafos), y reemplazá texto/datos con la info recolectada en los steps anteriores. NO recrees el archivo desde cero — preservá diseño, fuentes y colores de la plantilla.
  4. Guardá. Reportá la ruta absoluta al usuario.
- **Output**: archivo binario listo para revisar/enviar, en `workspace/clientes/<slug>/`.
- **Si no se puede generar el binario** (libs no instalables, etc.): generá el contenido en markdown estructurado siguiendo la misma estructura de la plantilla y avisá al usuario que tiene que pasarlo a la plantilla manualmente.

### Step 7 — Cerrar el ciclo: revisión, CFR y ajuste
- **Action**: Definir cadencia de revisión: semanal mínimo para LinkedIn, mensual para GA y OKRs. Instalar 1:1 semanales y revisiones de equipo. Al cierre del trimestre: autoevaluación + puntuación + Conversaciones, Feedback y Reconocimiento (CFR). Agregar/eliminar OKRs según evidencia. Mantener OKRs separados de bonos.
- **Ask the user for**: ritmo de reuniones actuales, sistema de compensación, herramientas de OKRs disponibles (Betterworks, Gtmhub, Monday).
- **Produce**: Bitácora de evolución, OKRs ajustados para el próximo trimestre y decisiones tomadas con trazabilidad al dato.

## Output
Un paquete entregable que incluye: (1) Documento de Necesidad de Medición, (2) Plan de Medición + OKRs trimestrales en cascada, (3) Auditoría GA con plan de acciones correctivas y vistas estandarizadas, (4) plantilla semanal de captura de métricas volátiles, (5) Informe de Benchmark, y (6) cadencia de revisión + CFR para cerrar el loop trimestral.

## Key consulting principles applied
- Lo que no se mide no se mejora, pero medir sin pregunta de decisión es parálisis por análisis.
- Configurar bien vence a configurar rápido: la calidad del dato determina la calidad de la decisión.
- Cuantitativo + cualitativo siempre: el número dice qué, la investigación dice por qué.
- Diseñar con el fin en mente: bosquejar el reporte antes de definir métricas o redactar preguntas.
- KRs binarios: se cumplen o no, nada de "casi".
- El benchmark es punto de partida para diferenciarse, no para imitar.
- La Vista Sin Modificar de GA es la red de seguridad innegociable del consultor.
- OKRs separados de bonos para que el equipo se anime a metas ambiciosas.

## Chains with
- skill_diagnostico: el diagnóstico inicial define las preguntas de decisión que alimentan el Plan de Medición de esta skill.
- skill_delivery: los OKRs y KPIs definidos acá se convierten en los criterios de éxito y reporting del delivery del proyecto.

## Templates used
- **MEGA PLANTILLA - Plan de Marketing (Cuentas, gráficas y tablas).xlsx** → ./skill_medicion/MEGA PLANTILLA - Plan de Marketing (Cuentas, gráficas y tablas).xlsx — Plan de marketing integral con cuentas, gráficas y tablas para consolidar métricas, presupuestos y seguimiento del plan.
- **PLANTILLA - Benchmark.xlsx** → ./skill_medicion/PLANTILLA - Benchmark.xlsx — Matriz de benchmark para comparar al cliente contra competidores y referentes, detectar brechas y oportunidades de diferenciación.
- **PLANTILLA ADC - Informe Facebook Ads [Leads y ventas].xlsx** → ./skill_medicion/PLANTILLA ADC - Informe Facebook Ads [Leads y ventas].xlsx — Reporte de campañas de Facebook Ads enfocado en leads y ventas, con KPIs de performance y costos.
- **PLANTILLA ADC- Reporte de funnels.xlsx** → ./skill_medicion/PLANTILLA ADC- Reporte de funnels.xlsx — Reporte de funnels de conversión para medir caídas entre etapas y priorizar puntos de optimización.

## Source modules
modulo10, modulo12
