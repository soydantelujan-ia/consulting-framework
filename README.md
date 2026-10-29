# Consulting Framework — Sistema Operativo de Consultoría Digital

Framework operativo integral de consultoría de negocios digitales y servicios estratégicos. Diseñado para transformar agentes de IA (Claude Code, Gemini CLI, Cursor, GPT, etc.) o equipos de consultoría en un colaborador experimentado con 27 skills ejecutables, 52 plantillas profesionales listas para usar y workflows punta a punta para adquisición, propuesta, entrega y escala.

## Arquitectura y Modelo de Uso

El framework funciona como un **sistema operativo base** (read-only):

```
mi-proyecto/
├── consulting-framework/        ← Sistema operativo del framework (este repositorio)
└── workspace/                   ← Carpeta generada automáticamente para el trabajo real
    ├── clientes/<slug>/         ← Un subdirectorio por cliente (diagnósticos, propuestas, contratos)
    ├── personal/                ← Estrategia interna (posicionamiento, OKRs, pricing, planes)
    └── plantillas_propias/      ← Variantes y documentos adaptados
```

### Reglas de Operación:
1. **Separación de entregables:** Todo entregable final o trabajo con clientes se genera en `workspace/clientes/<slug>/` o `workspace/personal/`.
2. **Uso de plantillas:** Las plantillas de `skills/<skill>/` se copian al `workspace/` correspondiente antes de ser completadas; los originales permanecen intactos.
3. **Orden secuencial:** Los archivos se estructuran cronológicamente (`01_discovery.md`, `02_diagnostico.md`, `03_propuesta.xlsx`, etc.).

---

## Cómo Utilizarlo

### 1. Con Claude Code o Gemini CLI (Recomendado)
1. Clona o copia el repositorio dentro del proyecto de trabajo.
2. Abre la terminal en el proyecto y ejecuta tu CLI de agente (`claude`, `gemini`, etc.).
3. El archivo `CLAUDE.md` actúa como system prompt maestro con todas las directrices operativas.
4. Usa triggers naturales en la conversación:
   - *"Tengo una llamada inicial con un cliente nuevo el viernes"* → Activa `skill_sesion_descubrimiento`.
   - *"Necesito definir el pricing para un servicio recurrente"* → Activa `skill_pricing`.
   - *"Armemos la propuesta comercial"* → Activa `skill_propuesta`.

### 2. Con Otros Modelos y Plataformas (ChatGPT, Cursor, n8n, etc.)
Carga el contenido de `CLAUDE.md` como instrucción de sistema (System Instructions) e incluye `skills/00_INDEX.md` para proveer el mapa completo de triggers y flujos.

---

## Estructura del Repositorio

```
consulting-framework/
├── CLAUDE.md                       ← System prompt principal para agentes de IA
├── GLOSSARY.md                     ← Glosario metodológico y principios transversales
├── README.md                       ← Documentación general del framework
│
├── skills/                         ← 27 skills operativas con metodología paso a paso
│   ├── 00_INDEX.md                 ← Matriz maestra de skills, triggers y cadenas
│   ├── skill_posicionamiento.md
│   ├── skill_propuesta.md
│   ├── skill_pricing.md
│   ├── ... (24 skills adicionales)
│   └── skill_<slug>/               ← Plantillas profesionales asociadas (.xlsx, .docx, .pptx)
│
└── templates/
    └── TEMPLATES_INDEX.md          ← Catálogo consolidado de las 52 plantillas editables
```

---

## Las 27 Skills por Etapa

| Etapa | Skills Clave |
|-------|--------------|
| **Estrategia** | `skill_posicionamiento` · `skill_mindset_objetivos` · `skill_servicio_estrella` · `skill_escalera_servicios` · `skill_pricing` |
| **Comercial** | `skill_pitch` · `skill_sesion_descubrimiento` · `skill_diagnostico` · `skill_propuesta` · `skill_negociacion` · `skill_contrato` · `skill_followup` |
| **Marketing** | `skill_marca_personal` · `skill_contenido` · `skill_lead_magnet` · `skill_prefiltro` · `skill_captacion` |
| **Delivery** | `skill_onboarding` · `skill_planificacion_proyecto` · `skill_delivery` · `skill_cierre_proyecto` |
| **Operaciones** | `skill_equipo_proveedores` · `skill_finanzas` · `skill_productividad` · `skill_medicion` |
| **Escala** | `skill_roadmap_monetizacion` · `skill_productizar` |

Consulta la guía completa de disparadores verbales y entregables en [`skills/00_INDEX.md`](./skills/00_INDEX.md).

---

## Workflows Multi-Skill (Cadenas Operativas)

- **Ciclo Comercial Completo:**  
  `skill_sesion_descubrimiento` → `skill_diagnostico` → `skill_propuesta` → `skill_negociacion` → `skill_contrato`

- **Onboarding e Implementación:**  
  `skill_contrato` → `skill_onboarding` → `skill_planificacion_proyecto` → `skill_delivery` → `skill_cierre_proyecto`

- **Planificación Estratégica y Control:**  
  `skill_roadmap_monetizacion` → `skill_medicion` → Revisión y optimización de KPIs
