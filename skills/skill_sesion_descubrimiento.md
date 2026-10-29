# Skill: Sesión de descubrimiento y escucha activa

## What this does
Diseña y conduce la primera reunión con el prospecto: arma un cuestionario por categorías, identifica USP, deal makers/breakers y cierra con mini-compromisos que destraban la siguiente etapa del proceso comercial.

## When to use it
**Activate this skill when the user:**
- Says: "tengo una primera reunión con un prospecto, ¿cómo la encaro?"
- Says: "necesito armar las preguntas para la call de mañana con [cliente]"
- Asks to: "ayudame a preparar la sesión de descubrimiento"
- Asks to: "armame el guion del kick-off comercial"
- Starts a situation like: "me contactó un lead nuevo y quiero llegar preparado a la primera llamada"
- Starts a situation like: "ya tuve la call pero siento que no saqué la info que necesitaba, ¿cómo la rescato?"
- Says: "qué preguntas le hago para entender si vale la pena avanzar"
- Says: "no sé si este prospecto califica, ayudame a descubrirlo en la próxima reunión"

## How to execute
Conducí al usuario paso a paso. No le entregues todo de golpe: trabajá una etapa, validá, y avanzá.

### Step 1 — Contexto del prospecto
- **Action**: Pedí al usuario los datos mínimos para personalizar el cuestionario. No avances sin esto.
- **Ask the user for**:
  - Nombre de la empresa, industria y tamaño aproximado
  - Cargo y nombre del interlocutor en la reunión
  - Cómo llegó el lead (referido, inbound, outbound, evento)
  - Qué se sabe ya del dolor o necesidad (aunque sea una hipótesis)
  - Servicio/oferta que el usuario tiene en mente proponerle
  - Duración estimada de la reunión y formato (call, presencial, video)
- **Produce**: Mini-resumen de 4-6 líneas con el perfil del prospecto y la hipótesis inicial de fit.

### Step 2 — Definición del objetivo de la reunión
- **Action**: Aclará con el usuario cuál es el outcome concreto que busca de esta call.
- **Ask the user for**: ¿Qué tiene que pasar para considerar exitosa la reunión? (calificar, agendar diagnóstico, conseguir acceso a un decisor, etc.)
- **Produce**: Una sola frase: "El éxito de esta reunión es lograr ___".

### Step 3 — Cuestionario por categorías
- **Action**: Construí el guion de preguntas agrupadas en 5 bloques. Adaptá las preguntas al contexto del Step 1, no uses plantilla genérica.
- **Bloques obligatorios**:
  1. **Situación actual**: cómo opera hoy, herramientas, equipo, procesos
  2. **Dolor / problema**: qué no funciona, qué ya intentaron, costo de no resolverlo
  3. **Visión deseada**: cómo se vería el éxito, qué cambiaría si se resuelve
  4. **Decisión y proceso de compra**: quién decide, quién influye, presupuesto, timing, otras opciones evaluadas
  5. **Criterios de éxito y riesgos**: cómo medirían el resultado, qué podría hacer fracasar el proyecto
- **Produce**: 3-5 preguntas abiertas por bloque, ordenadas de menos a más sensible.

### Step 4 — USP, deal makers y deal breakers
- **Action**: Identificá con el usuario qué de su oferta puede resonar con este prospecto y qué condiciones harían inviable el deal.
- **Ask the user for**:
  - 1-2 USPs de su servicio relevantes para esta industria/dolor
  - Deal makers: condiciones que, si se cumplen, hacen que valga la pena avanzar (presupuesto mínimo, acceso a decisor, urgencia real)
  - Deal breakers: condiciones que descalifican al prospecto (sin presupuesto, sin autoridad, timing >6 meses, expectativa irreal)
- **Produce**: Tabla corta con USP relevantes + checklist de deal makers/breakers a validar durante la call.

### Step 5 — Mini-compromisos y cierre
- **Action**: Diseñá la salida de la reunión. Toda call de descubrimiento debe terminar con un próximo paso concreto y aceptado por el prospecto.
- **Produce**:
  - 2-3 mini-compromisos posibles según cómo evolucione la conversación (ej: "agendar diagnóstico de 90 min con tu equipo técnico el martes", "compartir acceso a [dato] antes del viernes", "presentar propuesta el [fecha]")
  - Frase de cierre sugerida que pida el compromiso de forma directa pero no presionante.

### Step 6 — Recordatorios de escucha activa
- **Action**: Antes de entregar el guion final, recordale al usuario las reglas de oro de la sesión.
- **Produce**: Bullet list breve:
  - 80/20: el prospecto habla 80%, el consultor 20%
  - Repreguntar siempre con "¿por qué?" o "¿cómo así?" cuando aparezca un dolor
  - Tomar nota literal de las palabras que usa el prospecto (sirven para la propuesta)
  - No vender en esta reunión: validar fit
  - Silencios = oro, no llenarlos

## Output
Documento estructurado con:
1. Resumen del prospecto (4-6 líneas)
2. Objetivo de la reunión (una frase)
3. Cuestionario por 5 bloques con preguntas listas para usar
4. Tabla de USP + checklist de deal makers/breakers
5. Opciones de mini-compromisos de cierre
6. Recordatorios de escucha activa

Formato listo para imprimir o llevar abierto en una segunda pantalla durante la call.

## Key consulting principles applied
- **Diagnosticar antes de prescribir**: ninguna propuesta sin entender la situación real.
- **Calificar agresivamente, vender suavemente**: la primera call sirve para decidir si vale la pena avanzar, no para cerrar.
- **El prospecto define el problema con sus palabras**: capturar lenguaje literal para usarlo en propuesta y negociación.
- **Toda reunión termina con un próximo paso concreto**: sin mini-compromiso, la oportunidad muere.
- **Deal breakers tempranos ahorran semanas**: mejor descalificar en la call 1 que en la propuesta 3.

## Chains with
- skill_diagnostico: cuando la sesión de descubrimiento confirma fit, encadenar con diagnóstico profundo del problema y mapeo de procesos/stakeholders.
- skill_propuesta: usar las palabras literales, dolores y criterios de éxito capturados aquí como insumo directo de la propuesta comercial.
- skill_negociacion: los deal makers/breakers identificados se convierten en los pisos y techos de la negociación posterior.

## Templates used
- Cuestionario por categorías (5 bloques) → `templates/cuestionario_descubrimiento.md`
- Checklist deal makers/breakers → `templates/checklist_calificacion.md`
- Guion de mini-compromisos de cierre → `templates/cierre_compromisos.md`

## Source modules
modulo5, modulo6
