# Banco de preguntas y respuestas — Primer parcial

Banco de recuperación activa organizado en **cuatro ciclos de dificultad creciente**, con **tres preguntas por tema** en cada ciclo (60 en total). La idea del formato es barrer los cinco temas rápido en el primer ciclo y volver a pasar por todos ellos con más profundidad en cada vuelta, en lugar de agotar un tema antes de tocar el siguiente.

**Alcance.** Todas las preguntas se restringen al recorte oficial documentado en [Alcance del primer parcial](../parcial-1-alcance.md): las selecciones `P1-CL01`, `P1-CL02`, `P1-CL04`, `P1-CL05` y `P1-CL06`, más la **Ley de Parkinson** como excepción confirmada ([CL05-P, p. 5] y [CL05-P, p. 6]). [N-2026-09-07-alcance-primer-parcial] [N-2026-09-07-parkinson-primer-parcial]

**Estilo.** El parcial anterior tuvo cinco preguntas **abiertas y relacionales** ("¿qué relación hay entre X e Y?"), 2 puntos por respuesta correcta, **1 punto por respuesta incompleta**, 0 por incorrecta, y admitía ejemplos y justificaciones como complemento. [PARCIAL1, p. 1] Por eso los ciclos 3 y 4 están redactados con esa forma; los ciclos 1 y 2 construyen la base que esas preguntas presuponen. Las preguntas marcadas **[PARCIAL1]** son las cinco del examen anterior.

**Convenciones.** Las respuestas citan la fuente y la página. Lo que no proviene del material oficial está marcado como *(inferencia)* o *(conocimiento general)*. Las láminas que la cátedra marcó **"DIAPOSITIVA MUY IMPORTANTE!!"** llevan ⚠️.

| Ciclo | Foco | Preguntas |
|---|---|---|
| [1](#ciclo-1--base) | Definiciones y enumeraciones | 15 |
| [2](#ciclo-2--comparación-y-aplicación) | Comparaciones y aplicación | 15 |
| [3](#ciclo-3--integración) | Integración, estilo parcial | 15 |
| [4](#ciclo-4--profundización-y-cruces) | Cruces entre temas y matices finos | 15 |

Temas: **A** Fundamentos y ciclos de vida · **B** Metodologías · **C** Productos digitales · **D** Estimación · **E** Calidad.

---

# Ciclo 1 — Base

## A. Fundamentos y ciclos de vida

### A1. Definiciones de Ingeniería de Software de Sommerville, Pressman y Jacobson: ¿qué enfatiza cada una y en qué se diferencian?

**Sommerville — el alcance.** "Disciplina de la ingeniería que se ocupa de **todos los aspectos de la producción de software**, desde las primeras etapas de la especificación del sistema hasta el **mantenimiento** del sistema después de que ha entrado en uso." [P1-CL01, p. 1]

Dos expresiones cargan el sentido: *disciplina de la ingeniería* (método sistemático y responsabilidad profesional, no artesanía) y *todos los aspectos* (no solo programar). El límite que fija es explícito: la ingeniería de software **no termina con la entrega**.

**Pressman — la estructura y el objetivo.** "**Tecnología en capas** compuesta de un **proceso, métodos y herramientas**, cuyo objetivo es la producción de software de **alta calidad**, entregado **a tiempo**, **dentro del presupuesto** y que **cumpla con los requisitos** establecidos." [P1-CL01, p. 2]

Tiene dos mitades. *De qué está hecha*: **proceso** (marco que ordena qué se hace y en qué orden — el nivel donde viven ciclos de vida y metodologías), **métodos** (el cómo técnico de cada actividad) y **herramientas** (soporte automatizado de los métodos). La palabra *capas* importa: cada nivel se apoya en el anterior, y una herramienta sin método detrás no compensa un proceso malo. *Para qué sirve*: calidad + plazo + presupuesto + requisitos, la tensión clásica que reaparece en estimación y calidad.

**Jacobson — los medios y la complejidad.** "Conjunto de **métodos y técnicas** que se utilizan para construir **software complejo**." Destaca la **orientación a objetos** y los **casos de uso** como parte fundamental del desarrollo. [P1-CL01, p. 3]

Es la más estrecha y concreta: no habla de disciplina ni de objetivos de negocio, sino de herramientas conceptuales específicas. Define el problema por su naturaleza — el software es **complejo** — y propone dos respuestas: objetos (modularidad, reutilización) y casos de uso (el requisito visto desde quien lo usa).

**En común.** Las tres sostienen que desarrollar software no es solo programar: hace falta un enfoque sistemático, con métodos explícitos, ante un problema demasiado complejo para resolverse de forma improvisada.

**En qué difieren.** Cada una contesta una pregunta distinta:

| | Pregunta que responde | Palabra clave |
|---|---|---|
| Sommerville | ¿Hasta dónde llega? | *todos los aspectos*, hasta el mantenimiento |
| Pressman | ¿De qué está hecha y para qué? | *capas* + calidad, tiempo, presupuesto |
| Jacobson | ¿Con qué se construye? | *objetos y casos de uso* frente a la complejidad |

Sommerville define por **cobertura**, Pressman por **estructura y resultado**, Jacobson por **técnica**. Los dos primeros son descriptivos y generales; el tercero es prescriptivo y comprometido con un paradigma.

**Ganchos.** Que la calidad esté en la definición misma (Pressman) implica que QA/QC no son un agregado opcional → ver [pregunta A10](#a10-pressman-define-la-ingeniería-de-software-como-tecnología-en-capas-proceso-métodos-y-herramientas-mapeá-esas-capas-a-qa-y-qc). Los casos de uso de Jacobson son lo que RUP formaliza con UML y lo que PCU usa como unidad de estimación → ver [pregunta A12](#a12-jacobson-pone-los-casos-de-uso-en-el-centro-conectalo-con-ruporientación-a-objetos-y-con-puntos-de-caso-de-uso).

### A2. ¿Qué es un ciclo de vida del software y cuáles son las fases típicas del modelo en cascada?

**Ciclo de vida.** "Modelos que describen las **fases y actividades desde la concepción hasta el retiro** del software. Estos modelos ayudan a **organizar y estructurar** el desarrollo." [P1-CL01, p. 4]

Tres cosas: (1) es un **modelo**, o sea una simplificación para razonar y comunicar, no el proceso real; (2) cubre **concepción → retiro**, el mismo alcance amplio de Sommerville; (3) sirve para **organizar y estructurar** — sin ciclo de vida no hay hitos, y sin hitos no hay planificación, estimación ni control.

**Cascada.** "Enfoque **secuencial** donde **cada fase debe completarse antes de que la siguiente comience**. Las fases típicas incluyen: requisitos, diseño, implementación, pruebas, despliegue y mantenimiento." [P1-CL01, p. 5]

El diagrama de la lámina siguiente desdobla esa lista en **siete pasos**, que es la versión clásica y la más completa para responder [P1-CL01, p. 6]:

```
A. Requisitos del sistema
  └─ A. Requisitos software
      └─ Diseño preliminar
          └─ Diseño detallado
              └─ Codificación
                  └─ Pruebas
                      └─ Operación y mantenimiento
```

Dos detalles del dibujo que conviene mencionar: los **requisitos se parten en dos** (los del *sistema*, que incluyen el contexto y el hardware, y los del *software*) y el **diseño también** (preliminar = arquitectura, detallado = módulos). Y las cajas bajan en escalera, cada una apoyada en la anterior: el agua no sube.

**La consecuencia.** Un error de requisitos se descubre recién en la fase de pruebas, cuando corregirlo es carísimo. Ese es el argumento central contra cascada y el que reaparece en calidad como *costo de no calidad* y *fallos internos* → [pregunta E4](#e4-costo-de-calidad-vs-costo-de-no-calidad-fallos-internos-vs-externos).

*Nota de alcance:* la distinción explícita entre ciclo de vida y metodología está en [CL01-P, p. 12] y **quedó fuera del recorte**. Como intuición sirve (el ciclo de vida dice *qué se obtiene y en qué orden*; la metodología, *cómo*), pero no debe presentarse como contenido evaluado. [N-2026-09-07-alcance-primer-parcial]

### A3. Describí el modelo en espiral: ¿en qué se centra y por qué es iterativo?

"Combina elementos de **diseño y prototipado** en un esfuerzo **iterativo** para construir un sistema. Se centra en la **identificación y reducción de riesgos** a través de iteraciones sucesivas." [P1-CL01, p. 11]

**En qué se centra: el riesgo.** Es la palabra que no puede faltar. Los otros tres modelos se organizan alrededor de *fases* (cascada), *feedback del usuario* (prototipo) o *entrega de valor* (incremental). La espiral se organiza alrededor de: ¿qué es lo que más puede hacer fracasar este proyecto, y cómo lo resuelvo ahora en vez de después?

**Por qué es iterativo.** El diagrama parte el plano en **cuatro cuadrantes** que la espiral recorre una y otra vez [P1-CL01, p. 12]:

| Cuadrante | Actividad |
|---|---|
| Superior izquierdo | Determinar **objetivos, alternativas y restricciones** |
| Superior derecho | **Evaluar alternativas, identificar y resolver los riesgos** (análisis de riesgos; prototipos 1, 2, 3, operativo) |
| Inferior derecho | **Desarrollar y verificar** el producto del siguiente nivel |
| Inferior izquierdo | **Planificar las fases siguientes** |

Cada vuelta pasa por los cuatro, y entre vuelta y vuelta cambian tres cosas:

- **El radio crece** = costo y esfuerzo acumulados. No se vuelve al mismo punto: cada giro está más afuera.
- **Los entregables se concretan.** En el cuadrante de riesgos: *Análisis de riesgos → Prototipo 1 → Prototipo 2 → Prototipo 3 → Prototipo operativo*. En el de desarrollo: *Concepto de operación → Requisitos SW → Diseño del producto SW → Diseño detallado → Código → Pruebas unitarias → Integración y prueba → Prueba de aceptación*.
- **Los planes se refinan**: *Plan de requisitos y del ciclo de vida → Plan de desarrollo → Plan de integración y pruebas*.

O sea: **una cascada completa vive dentro del cuadrante inferior derecho**, pero se ejecuta varias veces, y cada ejecución está precedida por un análisis de riesgos que decide si seguir, cambiar de alternativa o abortar.

**El punto que vale.** En cascada el prototipado sería un desvío; en la espiral el prototipo es una **herramienta de gestión de riesgo**, construida para responder la pregunta más incierta antes de comprometer presupuesto. Por eso "combina diseño y prototipado" no significa dos modelos pegados, sino prototipado *al servicio de* la reducción de incertidumbre.

**Límite.** Es más costosa de gestionar y de estimar, porque no se sabe de antemano cuántas vueltas se van a dar, y exige criterio para evaluar riesgos. En proyectos chicos el overhead no se justifica. *(inferencia a partir de la definición; la lámina no lista desventajas)*

## B. Metodologías

### B1. ¿Qué tres criterios de selección de metodología plantea la cátedra y hacia dónde inclina cada uno?

[P1-CL02, p. 1]

| Criterio | Qué dice la lámina | Inclina hacia |
|---|---|---|
| **Tamaño del proyecto** | Proyectos pequeños pueden beneficiarse de metodologías ágiles; los grandes y complejos pueden requerir enfoques más estructurados | chico → ágil · grande → estructurado |
| **Equipo y habilidades** | La experiencia y las habilidades influyen en la elección: *equipos experimentados pueden manejar metodologías ágiles más flexibles* | senior → ágil · junior → estructurado |
| **Requisitos del cliente** | La **claridad y estabilidad** de los requisitos determinan la adaptabilidad necesaria | estables → estructurado · cambiantes → ágil |

**El criterio de equipo es el que más se pregunta**, porque es contraintuitivo. La lógica: ágil **no tiene red de contención**. Al quitar documentación previa, especificación cerrada y jerarquía de decisión, el marco delega el criterio en el equipo; un equipo sin experiencia se ahoga en esa libertad, mientras que un enfoque estructurado le da barandas. *(inferencia; la lámina afirma la relación pero no la explica)*

**Cómo responder si piden justificar una elección:** cruzar los tres criterios y **nombrar la tensión**. Un proyecto grande, con equipo senior y requisitos cambiantes no tiene respuesta única — lo que se evalúa es reconocer el conflicto y decidir con argumento, no acertar una etiqueta.

### B2. RUP: definición, sus cuatro fases y su notación estándar

**Definición.** "Modelo de desarrollo de software **iterativo e incremental** que busca mejorar la **productividad y la calidad** de los proyectos. Fue desarrollado por **Rational Software**, más tarde adquirida por **IBM**." Utiliza **UML** como notación estándar. [P1-CL02, p. 5]

**Las cuatro fases.** **Inicio (Inception) → Elaboración (Elaboration) → Construcción (Construction) → Transición (Transition)**, cada una con objetivos y actividades específicas [P1-CL02, p. 5].

Las láminas siguientes son gráficas y contienen lo más preguntable [P1-CL02, pp. 6–7]:

**Distribución de esfuerzo y tiempo:**

| | Inicio | Elaboración | Construcción | Transición |
|---|---|---|---|---|
| **Esfuerzo** | 5 % | 20 % | 65 % | 10 % |
| **Tiempo dedicado** | 10 % | 30 % | 50 % | 10 % |

Inicio consume **10 % del calendario pero solo 5 % del esfuerzo** (poca gente pensando mucho); Construcción se invierte, **50 % del tiempo y 65 % del esfuerzo**, porque el equipo está completo. El histograma de recursos de la lámina dibuja exactamente esa meseta que sube y baja.

**La curva de arquitectura.** Una franja *Architecture* crece durante Inicio, se dispara en **Elaboración** y se estabiliza: RUP resuelve la arquitectura **temprano**, antes de escalar el equipo. Ese es el corazón del modelo — reducir el riesgo arquitectónico primero.

**Las cuatro vistas + 1.** Vista Lógica, de Procesos, Física y de Desarrollo, con la **Vista de Casos de Uso en el centro**. Es el modelo "4+1" y conecta con Jacobson (A1): los casos de uso unifican las demás perspectivas.

**Cadena de trazabilidad.** `Caso de Uso —«trace»→ Realización de Análisis —«trace»→ Realización de Diseño —«trace»→ Caso de Prueba`, con el caso de uso trazando además hacia **Pruebas Funcionales** y el diseño hacia **Pruebas Unitarias**. Es verificación y validación **trazables desde el requisito**: el mejor puente hacia el tema de calidad.

**Iterativo e incremental son dos cosas distintas.** *Iterativo*: dentro de cada fase se dan varias vueltas, y el diagrama muestra que **una iteración** contiene *Requisitos → Análisis → Diseño → Implementación → Prueba e integración*, más la planificación y el análisis de la propia iteración — una mini-cascada repetida. *Incremental*: cada iteración **agrega** funcionalidad; no se rehace, se acumula.

Frase de cierre: *RUP no elimina las fases de cascada, las recorre muchas veces y cambia el peso relativo de cada disciplina según la fase del proyecto.*

### B3. Scrum: roles, artefactos y ceremonias, con la función de cada uno

"Marco de trabajo ágil que facilita el desarrollo y la entrega de **productos complejos** a través de iteraciones cortas llamadas **sprints**." Creado por **Jeff Sutherland**, proceso de Scrum en **1993**. Componentes: **Organización (Sprints), Roles, Artefactos y Eventos ("ceremonias")**. [P1-CL02, pp. 17–18]

**Sprint** [P1-CL02, p. 19]

- Sprint = **iteración**, con duración **fija para todos**: **de una a cuatro semanas**.
- Se ejecutan **uno tras otro sin tiempo muerto** entre el que termina y el que empieza.
- Objetivo: transformar un conjunto acordado de ítems del Backlog de Producto en un **Incremento de Funcionalidad de Producto Potencialmente Deployable**.

Esa duración fija es el **timebox**, y es la defensa estructural de Scrum contra la Ley de Parkinson → [pregunta D8](#d8-parcial1-cómo-abordan-las-técnicas-de-estimación-ágiles-el-impacto-de-la-ley-de-parkinson-frente-a-los-enfoques-predictivos-especialmente-con-requisitos-cambiantes).

**Roles**

| Rol | Función |
|---|---|
| **Dueño del Producto** | **Voz del cliente**. Establece la visión del producto, **prioriza continuamente** los requisitos, canaliza las necesidades del negocio, **maximiza el valor respecto de la inversión**, inspecciona y adapta. Es **autoridad final** y es parte del equipo. [P1-CL02, p. 20] |
| **Scrum Master** | **Facilitador y agente de cambio** para la aplicación adecuada de Scrum. *Coaching* al equipo para ser más productivo y generar productos de mejor calidad, **eliminar impedimentos** y **proteger al equipo** de interferencias de la organización. [P1-CL02, p. 21] |
| **Equipo** | Grupo **auto-organizado, multidisciplinario** (programación, pruebas, análisis funcional, arquitectura, interfaz gráfica, base de datos) y **con autonomía**. Transforma el Backlog de Producto en incrementos potencialmente entregables y promueve el aprendizaje de todos sus miembros. [P1-CL02, p. 22] |

Dos datos textuales de la lámina del Equipo [P1-CL02, p. 22]:

- **Auto-gestión:** *"de ninguna manera el Scrum Master o el Dueño de Producto le explica al equipo cómo transformar el Backlog de Producto en incrementos de funcionalidad potencialmente entregable"*.
- **Tamaño recomendado: 7 personas ± 2** (sin contar PO ni SM). Con menos de cinco hay menos interacciones y menos productividad; con más de nueve se requiere demasiada coordinación y se genera demasiada complejidad en las actividades grupales.

El reparto de decisión: el PO decide el **qué** y el orden, el Equipo decide el **cómo**, el SM no decide sobre el producto y cuida el **proceso**.

**Artefactos**

| Artefacto | Definición |
|---|---|
| **Backlog de Producto** | Lista **única, pública, dinámica y priorizada** de requerimientos. Algunos tienen estimación de alto nivel de esfuerzo o complejidad. Representa el **"qué"** esperado, sin ocuparse del **"cómo"**. [P1-CL02, p. 23] |
| **Backlog de Sprint** | Conjunto reducido **negociado** de ítems que el equipo **se compromete** a completar en el sprint. Cada ítem se divide en tareas con estimación **que no supere un día de esfuerzo**. Se **actualiza diariamente** por el equipo (pendientes, en curso, terminadas; esfuerzo restante y asignación). Se visualiza en un **Tablero de Sprint**. [P1-CL02, p. 24] |
| **Diagrama de Burndown** | Forma gráfica de mostrar el **avance del sprint**. El ejemplo de la lámina: sprint de **20 días** con **190 horas** de esfuerzo restante estimado inicial; se grafica la curva real contra la línea ideal. [P1-CL02, p. 25] |
| **Estimaciones de Alto Nivel** | El equipo estima cada ítem del Backlog de Producto, pudiendo requerir decisiones iniciales de diseño y preguntas al PO. Técnicas: **Planning Poker, T-Shirt Sizing, Wideband Delphi**. [P1-CL02, p. 26] |

Dentro del Backlog de Producto viven las **Historias de Usuario**: *Como **[un usuario]**, puedo **[una funcionalidad]** para **[un beneficio]***. Ejemplo de la cátedra: *"Como usuario no registrado, puedo consultar los precios de los vuelos para calcular el presupuesto de mi viaje"*. Y la **Épica**: historia que **no puede entregarse dentro de una sola iteración**, o que es lo bastante grande como para partirse en historias menores. [P1-CL02, p. 23]

**Ceremonias**

| Ceremonia | Cuándo | Participantes | Duración | Objetivo | Artefactos |
|---|---|---|---|---|---|
| **Planificación** | Primera actividad del sprint | PO + SM + Equipo | 2–8 h | Entender los ítems más prioritarios, acordar el Sprint Backlog, definir las tareas | Backlog de Producto y de Sprint |
| **Reunión diaria** | 1 vez/día, horario fijo (se recomienda la primera hora) | SM + Equipo (+ PO opcional) | **< 15 min** | Sincronizar tareas, comunicar avances, **reportar impedimentos** | Backlog de Sprint |
| **Revisión** | Último día del sprint | SM + Equipo + PO + **otros interesados** | 1–2 h | Que los interesados vean/experimenten lo construido y el **PO acepte o rechace** | Incremento potencialmente deployable |
| **Retrospectiva** | Última actividad del sprint | SM + Equipo (+ PO opcional) | 1–3 h | Inspeccionar **procesos e interacciones**, acordar pocas acciones concretas de mejora | **No aplica** |
| **Refinamiento** (*optativa*) | Durante el sprint | — | — | Revisión, ordenamiento, unión de HU, **reestimación** | Backlog de Producto |

[P1-CL02, pp. 27–30]

Las **tres preguntas de la diaria**: *¿Qué hiciste desde la última reunión diaria? ¿Qué vas a hacer hasta la próxima? ¿Hay algún obstáculo que frena o bloquea tu trabajo?* Al final el SM suele actualizar el Burndown [P1-CL02, p. 28]. Las **dos de la retro**: *¿Qué mecanismos, procedimientos o interacciones funcionaron bien? ¿Cuáles hay que mejorar?* [P1-CL02, p. 30]

**La distinción más preguntada: Revisión vs. Retrospectiva.** La Revisión inspecciona el **producto** y su audiencia incluye interesados externos; la Retrospectiva inspecciona el **proceso y las interacciones** y es puertas adentro. Por eso la Revisión tiene como artefacto el Incremento y la Retrospectiva **no aplica ninguno**.

## C. Productos digitales

### C1. Lean Startup: qué es, quién lo popularizó y en qué consiste el ciclo Build–Measure–Learn

**Qué es.** "Enfoque para construir negocios y productos de manera **eficiente**. Popularizado por **Eric Ries (2011)**, se centra en **validar ideas rápidamente con los clientes**. **Reduce el riesgo** y fomenta la iteración rápida." [P1-CL04, p. 2]

**El ciclo, en dos niveles** [P1-CL04, p. 3]. Las tres palabras: **Construir** (crear prototipos rápidos o MVPs), **Medir** (recopilar datos de los clientes), **Aprender** (ajustar el producto basándose en los datos). Y el ciclo completo en seis pasos, que es la versión que conviene citar:

```
1. Formular hipótesis
2. Construir PMV
3. Lanzar a clientes
4. Medir comportamiento
5. Analizar resultados
6. Aprender y decidir: próximo experimento o pivot
```

**La meta —— el punto fino.** "Acortar el **tiempo total de la vuelta** al mínimo posible." [P1-CL04, p. 3]

La meta **no** es construir el producto correcto de una, ni siquiera "validar la idea": es **minimizar la duración de cada vuelta del bucle**. La lógica: como no se sabe de antemano qué hipótesis son ciertas, la ventaja competitiva no está en acertar sino en **aprender más rápido**. Si la vuelta dura tres meses se aprenden cuatro cosas por año; si dura una semana, cincuenta. Todo lo demás se deduce de ahí: el MVP es chico *porque construir rápido acorta la vuelta*, y las métricas se instrumentan de antemano *porque medir lento la alarga*. No es minimalismo por ahorro, es velocidad de aprendizaje. *(la lectura de la meta como principio organizador es inferencia; el enunciado es textual)*

**La hipótesis va primero.** La lámina de Construir lo refuerza: *plantear hipótesis de valor y de crecimiento **antes de codificar**; diseñar experimentos rápidos; minimizar desperdicio y tiempo de ciclo*. Herramientas: **prototipos rápidos** (maquetas o versiones simplificadas, a veces solo un boceto interactivo, en horas o pocos días) y **feature flags** (interruptores en el código que activan o desactivan funcionalidades). [P1-CL04, p. 4] Construir sin hipótesis previa no es Lean Startup.

### C2. Qué es un MVP y por qué el video de Dropbox califica como tal

**Definición.** "Producto con las **características mínimas necesarias para probar una hipótesis**. Permite ahorrar tiempo y recursos mientras se valida la idea." [P1-CL04, p. 5]

La palabra decisiva es **hipótesis**. Un MVP no es "la versión 0.1" ni "el producto sin lo que no llegamos a hacer": es un **instrumento de medición**, y se diseña hacia atrás desde la pregunta que se quiere responder. Por eso un MVP puede incluso no tener código.

De ahí sale la respuesta a *¿por qué un MVP es un experimento y no una versión incompleta?*: una versión incompleta se define por lo que **le falta** respecto del producto final; un MVP se define por lo que **prueba**.

**El caso Dropbox** [P1-CL04, p. 5]:

| Elemento | Dropbox |
|---|---|
| Hipótesis | ¿Hay demanda real de sincronización de archivos sin fricción? |
| MVP | Un **video animado** que mostraba la experiencia de uso |
| Métrica | La lista de espera creció de **5.000 a 75.000** suscriptores |
| Aprendizaje | Alta demanda → invertir en desarrollo completo |
| Resultado | Redujo el riesgo **antes** de construir infraestructura costosa |

Es el ejemplo canónico precisamente porque **el MVP no era software**. Construir la sincronización real habría costado meses de ingeniería difícil; el video costó días y respondía la misma pregunta, porque la hipótesis en juego era **de demanda, no técnica**.

**El criterio general:** el MVP debe atacar **la hipótesis más riesgosa** con **el medio más barato que la responda**. Si la hipótesis riesgosa hubiera sido "¿es técnicamente posible sincronizar en tiempo real?", el video no habría servido y habría hecho falta un prototipo funcional. *(inferencia)*

Al responder, conviene enumerar los cinco elementos en orden — **hipótesis → MVP → métrica → aprendizaje → decisión** — y señalar que son el ciclo BML de C1 instanciado en un caso. Esa correspondencia vale más que la anécdota.

### C3. Las cinco etapas de Design Thinking y sus tres principios fundamentales

**Qué es.** "Enfoque **centrado en las personas** para resolver problemas de manera creativa. Se utiliza ampliamente en el diseño de productos, servicios y estrategias empresariales. Fomenta la innovación mediante la combinación de **empatía, ideación y experimentación**." [P1-CL04, p. 13]

**Origen.** Surgió en la **década de 1960** como enfoque formalizado para resolver problemas; popularizado por firmas de diseño como **IDEO** (el Palm V, el mouse de Apple). [P1-CL04, p. 14]

**Los tres principios fundamentales** [P1-CL04, p. 15]:

- **Empatía**: comprender profundamente las necesidades de las personas.
- **Colaboración**: trabajar con equipos multidisciplinarios.
- **Iteración**: probar, aprender y ajustar continuamente.

La lámina agrega: *"Disclaimer: cualquier parecido con el **Plan-Do-Check-Act** de W. Edwards Deming NO es coincidencia."* PDCA como tema propio **quedó fuera del recorte**, así que sirve como observación lateral, no como contenido central. [N-2026-09-07-alcance-primer-parcial]

**Las cinco etapas** [P1-CL04, pp. 13, 16–21]:

| Etapa | Propósito | Herramientas |
|---|---|---|
| **Empatizar** | Entender cómo piensan los usuarios, sus necesidades y lo que es realmente importante para ellos; descubrir necesidades ocultas, contexto y emociones | Entrevistas; **observación** (registrar lo que la gente **A**ctúa, el **E**ntorno, las **I**nteracciones, los **O**bjetos y los **U**suarios); **mapas de empatía** (lo que la persona *dice, hace, piensa y siente*) |
| **Definir** | Sintetizar la información para identificar patrones, construyendo un punto de partida desde un **dolor significativo**; formular un **reto de diseño** que sirva de norte | Síntesis de patrones |
| **Idear** | Generar múltiples propuestas **sin censura**, valorando tanto lo realista como lo arriesgado, para obtener un abanico amplio | **Brainstorming**, mapas mentales, lluvias de ideas enfocadas, **mapas de viaje**, **Crazy 8s**, **Dot Voting** |
| **Prototipar** | Crear representaciones simples de las ideas más prometedoras, para materializar conceptos y **detectar fallos temprano** a bajo costo | **Mockups** (apariencia), **wireframes** (estructura), prototipos funcionales, storyboards |
| **Testear** | Evaluar los prototipos con usuarios, recoger opiniones y afinar antes de implementar | Pruebas de usuario, entrevistas, prototipos interactivos, **prueba piloto / "marcha blanca"** |

**Por qué no es una secuencia rígida.** El principio de **iteración** está en el núcleo: testear no cierra el proceso, **realimenta**. Los propios ejemplos de la cátedra lo muestran: en la app de turnos médicos, el piloto de dos semanas midió **42 % menos llamadas** y **4,6/5** de satisfacción, pero detectó que los adultos mayores necesitaban **tipografía más grande → nueva iteración**; en el sistema de vasos, la recuperación fue del **72 %** la primera semana y las entrevistas revelaron **miedo a las multas**, lo que obligó a rediseñar (recordatorio push 24 h antes). [P1-CL04, p. 21]

Los hallazgos de Testear pueden devolver a **Prototipar** (ajustar la solución), a **Idear** (la solución no servía) o incluso a **Definir** (el problema estaba mal planteado). Esa última vuelta es la más valiosa y la más incómoda. *(inferencia)*

**Detalles útiles de Idear** [P1-CL04, p. 19]: **Crazy 8s** — ideación exprés surgida en Google Ventures; cada participante dobla una hoja A4 tres veces (8 secciones) y en 8 minutos dibuja 8 ideas, una por minuto, para forzar cantidad sobre calidad y romper bloqueos. **Dot Voting** — cada persona recibe X adhesivos y los coloca sobre las propuestas más valiosas; las más votadas pasan a la ronda siguiente. **Mapas de viaje** — visualizan paso a paso cómo una persona interactúa con el producto a lo largo del tiempo, para descubrir puntos de dolor y momentos de verdad; componentes típicos: fases, acciones, emociones, puntos de contacto, métricas y oportunidades.

## D. Estimación

### D1. Diferenciá tamaño, esfuerzo, complejidad y duración

[P1-CL05, p. 10]

| Concepto | Definición | Se mide en |
|---|---|---|
| **Tamaño** | Cantidad de **trabajo requerido** para completar el proyecto | Líneas de código, puntos de función |
| **Esfuerzo** | Cantidad de **recursos** necesarios. **Depende del tamaño y la complejidad** | Horas de trabajo, personas |
| **Complejidad** | Grado de **dificultad técnica y organizativa**. **Afecta directamente al esfuerzo y al tiempo** | — |
| **Duración** | Tiempo **"calendarizado"** que lleva resolver un requerimiento o serie de requerimientos | Días, semanas de calendario |

**No son cuatro etiquetas paralelas: hay una cadena causal**, y las propias definiciones la explicitan.

```
Tamaño ──────┐
             ├──► Esfuerzo ──► Duración
Complejidad ─┘
```

- **Tamaño y complejidad son propiedades del problema**: existen antes de decidir quién lo hace.
- **El esfuerzo ya es propiedad de la solución con un equipo dado**: un equipo experto resuelve el mismo tamaño con menos esfuerzo.
- **La duración depende del esfuerzo pero no es proporcional a él.**

**Esfuerzo ≠ duración** es lo que separa una respuesta completa de una incompleta, y la palabra elegida por la cátedra lo señala: **"calendarizado"**. *(ejemplo propio)* Una tarea de 40 horas-persona: con 1 persona full-time → 1 semana; con 2 personas y trabajo paralelizable → ~3 días; con 2 personas pero dependencia secuencial → sigue siendo 1 semana y ahora se gastaron 80 horas; con 1 persona al 50 % → 2 semanas. El esfuerzo no cambia, la duración sí. La duración incorpora asignación, paralelismo, dependencias, esperas y disponibilidad real. Ahí entra la Ley de Parkinson, que **no ataca el esfuerzo sino la duración**.

**Tamaño ≠ complejidad** es la otra confusión: un CRUD de 50 pantallas es **grande pero simple**; un motor de reglas fiscales de 3 pantallas es **chico pero complejo**. Por eso los **Story Points** mezclan deliberadamente complejidad + cantidad de trabajo + riesgo en una sola escala relativa → [pregunta D6](#d6-story-points-qué-miden-y-por-qué-no-se-traducen-directamente-a-horas).

**Por qué se estima:** *"Estimamos porque necesitamos tener una noción del **tamaño de la solución del requerimiento**."* [CL05-P, p. 5]

### D2. Ley de Parkinson: enunciado, origen y las tres leyes fundamentales

*Estatuto especial:* sus dos diapositivas **no están en el PDF recortado**, pero la cátedra **confirmó expresamente que el tema entra**, y fue la pregunta 1 del parcial anterior. [N-2026-09-07-parkinson-primer-parcial] [PARCIAL1, p. 1]

**Enunciado.** **Cyril Parkinson (1957)**: *"el trabajo se expande hasta llenar el tiempo disponible para su realización"*. [CL05-P, p. 5]

**Origen.** No salió de la gestión de software sino de la observación de una burocracia [CL05-P, p. 5]:

- **Servicio Civil Británico**: a pesar de la **decadencia del Imperio Británico** —es decir, con menos colonias que administrar— la **cantidad de empleados aumentaba continuamente**.
- **Burocracia**: los funcionarios **multiplican subordinados** y **se crean trabajo entre sí**.
- **Crecimiento administrativo**: el número de empleados aumenta alrededor de un **5–7 % por año**, **independientemente de la carga de trabajo real**.

Ese *"independientemente de la carga de trabajo real"* es la clave: Parkinson describió un sistema donde **el trabajo aparente crecía sin que creciera el trabajo verdadero**. Trasladado a software: si a una tarea de 3 días se le asignan 2 semanas, tardará 2 semanas — por *gold plating*, refinamientos innecesarios, dilación inicial y el efecto "todavía hay tiempo". *(la traslación a software es inferencia)*

**Las tres leyes fundamentales** [CL05-P, p. 6]:

1. **El trabajo se expande hasta llenar el tiempo disponible.**
2. **Los gastos aumentan hasta cubrir todos los ingresos.**
3. **"El tiempo dedicado a un tema es inversamente proporcional a su importancia"** — la **Ley de la trivialidad**, también de C. Parkinson.

Más la variante informática que da la lámina como ejemplo: *"los datos se expanden hasta llenar el espacio disponible para su almacenamiento"*.

Las tres tienen **la misma forma lógica**: un recurso disponible se consume por completo, sin relación con la necesidad real. Si preguntan por qué son "la misma ley", esa es la respuesta.

**La Ley de la trivialidad** es la más fácil de olvidar y la más citable: los equipos discuten horas el color de un botón y aprueban en cinco minutos una decisión de arquitectura, **porque sobre lo trivial todos tienen opinión**. En estimación se traduce en reuniones que se consumen en los ítems chicos mientras los grandes —donde está el riesgo— pasan sin discusión. *(ejemplo propio)*

### D3. PERT: qué es, fórmula, y cálculo con O = 4, M = 7, P = 16

**Qué es.** "Método que utiliza **tres estimaciones (optimista, pesimista y más probable)** para calcular una **estimación ponderada** y **reducir la incertidumbre**." **PERT = Program Evaluation and Review Technique**. **Ventaja:** "proporciona una visión más completa de los posibles resultados y ayuda a **gestionar el riesgo** asociado con las estimaciones". [P1-CL05, p. 7]

**La fórmula.** "(Optimista + (4 × Más Probable) + Pesimista) / 6" [P1-CL05, p. 7]

```
E = (O + 4M + P) / 6
```

Los pesos no son arbitrarios: hay **6 unidades repartidas** y **4 de las 6 (el 67 %) van al escenario más probable**; optimista y pesimista aportan 1 cada uno. El método **ancla en lo más probable pero deja que los extremos lo corrijan**, y como el pesimista suele estar más lejos del centro que el optimista (las cosas salen mal de más maneras de las que salen bien), el resultado tiende a quedar **por encima del más probable**. Esa asimetría es el aporte real. *(inferencia)*

**El cálculo.**

```
E = (4 + 4×7 + 16) / 6 = (4 + 28 + 16) / 6 = 48 / 6 = 8 días
```

**Lo que hay que decir además del número:**

- El más probable era **7** y PERT da **8**: **se corrió hacia arriba**, porque el pesimista está a **+9** del más probable mientras el optimista está a **−3**. La cola larga del riesgo empuja.
- El **rango 4–16 es enorme** (el pesimista cuadruplica al optimista): eso ya es información, y señala que **la tarea está mal entendida o mal acotada**. Antes de aceptar los 8 días conviene descomponerla o investigar qué la haría durar 16.
- **8 días es esfuerzo estimado, no una promesa de calendario** (ver D1). La conversión formal vía factor de productividad **quedó fuera del recorte**. [N-2026-09-07-alcance-primer-parcial]

## E. Calidad

### E1. ¿Qué busca la gestión de calidad, por qué importa y cuáles son sus métricas? Explicá "la calidad no sucede, se gestiona"

**Qué busca.** "La gestión de calidad en software busca **asegurar que los procesos de desarrollo cumplan con estándares definidos** para **garantizar la calidad del producto final**." Es un "concepto complejo y de **aristas múltiples (puntos de vista)**". [P1-CL06, p. 2]

La estructura de esa primera frase adelanta toda la clase: **se actúa sobre el proceso para obtener un resultado en el producto**. Ese salto proceso → producto es exactamente la relación QA → QC de E2.

*Nota de alcance:* lo de "aristas múltiples" remite a las cinco perspectivas de calidad, que **quedaron fuera del recorte** [CL06-P, p. 3]. La frase está en la selección; el desarrollo de las cinco perspectivas, no. [N-2026-09-07-alcance-primer-parcial]

**Por qué importa** [P1-CL06, p. 2]:

- **Reduce errores en etapas tempranas** del desarrollo.
- **Mejora la satisfacción del cliente.**
- **Incrementa la eficiencia y la sostenibilidad** del software.

La primera es la de fondo: el valor no está en encontrar errores sino en encontrarlos **temprano**, cuando corregirlos es barato. Es el mismo argumento que hace caer a cascada (A2) y el que fundamenta el costo de no calidad (E4).

**Las tres métricas** [P1-CL06, p. 2]: **densidad de defectos**; **tasa de errores por usuario**; **tiempo medio para la resolución de problemas**.

No son intercambiables: la primera mide el **producto** (defectos por unidad de tamaño), la segunda el **impacto real en el usuario** (defectos que efectivamente se manifiestan en uso), la tercera la **capacidad de respuesta del equipo** — es de proceso, no de producto. Entre las tres cubren producto, usuario y organización. *(inferencia)*

**"LA CALIDAD NO SUCEDE, SE GESTIONA"** es el cierre en mayúsculas de la lámina, y es una consigna [P1-CL06, p. 2].

Lo que niega: que la calidad sea un **subproducto** de tener buenos programadores, o algo que se agrega al final con una tanda de testing. Lo que afirma: que requiere **objetivos definidos, actividades planificadas, responsables asignados, métricas y corrección** — el ciclo de gestión completo.

Dicho de otro modo: si nadie la gestiona, **la variable que se degrada primero bajo presión de plazo es siempre la calidad**, porque es la única de las cuatro (alcance, plazo, costo, calidad) que **no se ve el día de la entrega**: se ve seis meses después, como deuda técnica y fallos externos. Por eso hace falta gestionarla explícitamente: es la que no se defiende sola. *(inferencia)* Conecta con Pressman (A1), donde la calidad está en la definición misma de la disciplina.

### E2. ⚠️ QC vs QA: enfoque, objetivo, momento, responsabilidad y resultado

**Encuadre.** Son dos de las **tres fases** del proceso de gestión de calidad: **planificación de calidad** (incluirla en el plan), **control de calidad (QC)** y **aseguramiento de calidad (QA)**. Herramientas: **diagramas de causa-efecto (Ishikawa o "fishbone")**, **auditorías internas** e **indicadores clave de rendimiento (KPIs)**. Ciclo de mejora continua: **PDCA**. [P1-CL06, p. 7]

**La comparación completa** [P1-CL06, pp. 8, 9, 10]:

| Dimensión | **QC — Control de Calidad** | **QA — Aseguramiento de Calidad** |
|---|---|---|
| **Enfoque / Perspectiva** | **Producto** y entregables concretos | **Procesos** y metodologías de desarrollo |
| **Objetivo** | **Detectar** defectos existentes | **Prevenir** defectos |
| **Momento** | **Durante y después** del desarrollo | **Desde el inicio y durante todo el ciclo** |
| **Responsabilidad** | Equipo de **testing / inspección** | **Toda la organización** (el equipo SQA *facilita*) |
| **Actividades** | Revisiones de código · Pruebas (unitarias, integración, sistema) · Verificación de requisitos | Definición de políticas y estándares (**ISO/IEC 25010**, **CMMI**) · Auditorías de proceso · Capacitación y mejora continua |
| **Resultado** | Lista de defectos e incidencias · Métricas (*defect density*, severidad) | Procesos documentados y validados · **Confianza** en la calidad durante todo el ciclo de vida |

**Cómo retenerlo: QC detecta, QA previene.** Todo lo demás se deduce. Si detectás, necesitás algo ya construido → QC es *durante y después* y mira el **producto**. Si prevenís, tenés que actuar antes de que el defecto exista → QA es *desde el inicio* y actúa sobre el **proceso**. Si actuás sobre el producto, alcanza un equipo especializado → **testing**. Si actuás sobre el proceso, **nadie queda afuera** → toda la organización, con el equipo SQA que **facilita**, no que ejecuta en soledad (ese matiz del verbo es preguntable).

El resultado también se sigue: QC produce **una lista** (concreta y contable), QA produce **confianza** (no directamente medible). Por eso QA es más difícil de justificar ante la gerencia y lo primero que se recorta — y por eso hacía falta la consigna de E1. *(inferencia)*

**El error clásico:** confundir **QA con testing**. En la industria se llama "QA" a quien prueba, pero según esta tabla eso es **QC**. Escribir "el equipo de QA ejecuta las pruebas" contradice la lámina marcada como muy importante.

**No confundir con verificación y validación**, que es otro eje [P1-CL06, p. 11]:

- **Verificación**: asegura que el producto **se esté construyendo correctamente** según los requisitos especificados → *¿lo construimos bien?* Ej.: revisiones de código, inspecciones.
- **Validación**: comprueba que el producto final **cumple con las necesidades del cliente** → *¿construimos lo correcto?* Ej.: pruebas funcionales, pruebas de usuario.
- Técnicas comunes: revisiones técnicas, pruebas de integración, simulaciones.

Ambas son actividades de **QC** (miran el producto). QA/QC responde *sobre qué actúo*; V&V responde *contra qué contrasto* — el requisito o la necesidad. *(inferencia)*

### E3. ⚠️ Deuda técnica: definición, origen, analogía financiera y los cuatro cuadrantes de Fowler

**Dónde se ubica.** La cátedra la presenta como **"caso especial de No Calidad"** [P1-CL06, p. 4]: no es una categoría aparte sino una forma particular del costo de no calidad, en la que el costo **no se paga ahora sino que se acumula**.

**Definición.** "La deuda técnica es el **costo de retrabajo** que aparece cuando **se prioriza una solución rápida por sobre la más efectiva**." [P1-CL06, p. 4]

Dos precisiones: es **costo de retrabajo** (no "código feo" ni "bugs") y nace de **una priorización**, algo que alguien eligió explícita o implícitamente.

**Origen y analogía** [P1-CL06, p. 4]:

- El término lo acuñó **Cunningham (1992)** — la lámina aclara: **Howard Cunningham: XP, Manifiesto Ágil, Wiki**.
- Se compara con la **deuda financiera**: puede ser **"buena" si se gestiona**, o **"mala" si se ignora**.
- **Origen**: puede ser **funcional o tecnológica**.

La analogía es más precisa de lo que parece: hay un **principal** (lo que cuesta arreglarlo hoy) e **intereses** (lo que cada nueva funcionalidad cuesta de más por convivir con esa solución). Los intereses son lo que mata, porque se pagan en **cada** cambio futuro. Y como toda deuda, **endeudarse puede ser racional** — se toma deuda para llegar antes al mercado, igual que un negocio toma un crédito para capturar una oportunidad. Lo irracional no es endeudarse: es **no registrar la deuda y no tener plan de pago**. *(desarrollo de la analogía: inferencia)*

**Los cuatro cuadrantes de Fowler.** Dos ejes: **prudente / imprudente** (calidad de la decisión) × **deliberada / inadvertida** (¿lo sabíamos?). "Sirven para **calibrar intención y nivel de riesgo**." [P1-CL06, pp. 4, 5]

| Cuadrante | Qué lo caracteriza | Ejemplo de la cátedra |
|---|---|---|
| **Prudente + Deliberada**<br>*"decisión estratégica"* | El equipo **sabe** que genera deuda y **planea cómo y cuándo pagarla** | Sprint de lanzamiento: para llegar a la demo se omite la capa de validaciones complejas y **se documenta una tarjeta de backlog con el refactor previsto** para el próximo ciclo |
| **Imprudente + Deliberada**<br>*"lo hacemos rápido y después vemos"* | Se **conoce el riesgo** pero se acepta **sin plan de pago**; prima la presión de negocio | Parche de producción a las 3 a. m.: código hardcodeado con credenciales para reactivar un servicio crítico; *"mañana lo limpiamos"*… y pasa un año |
| **Prudente + Inadvertida**<br>*"nadie podía preverlo"* | Se trabajó con **buenas prácticas** pero **apareció información nueva** | Cambio de normativa: se construye un módulo fiscal según la ley vigente y tres meses después una nueva resolución impositiva obliga a reescribir gran parte de la lógica |
| **Imprudente + Inadvertida**<br>*"no sabíamos que era tan grave"* | **Falta de conocimiento o control**; la deuda surge **sin que el equipo se dé cuenta** | Onboarding apurado: juniors copian y pegan código de internet sin tests ni revisión; meses después aparecen bugs y duplicación masiva de lógica |

**Lo que hay que entender del esquema:** el eje que decide si la deuda es tolerable **no es deliberada/inadvertida sino prudente/imprudente**. Prudente + deliberada es *buena gestión*; prudente + inadvertida es *mala suerte*, inevitable y aceptable. Los dos imprudentes son los problemáticos, y el peor es **imprudente + inadvertida**, porque no se puede planificar el pago de una deuda que no figura en ningún lado. *(inferencia)*

Para clasificar un caso, dos preguntas: *¿alguien lo decidió sabiendo?* → eje deliberada/inadvertida. *¿había justificación razonable y plan de pago?* → eje prudente/imprudente.

**Clasificación complementaria de McConnell** (autor de *Code Complete*) [P1-CL06, p. 6]:

- **Intencionada**: decisión consciente de optimizar el presente, a corto o largo plazo. Ej.: elegir un framework rápido pero de bajo rendimiento para llegar a un deadline, sabiendo que requerirá reescritura.
- **No intencionada**: errores, falta de conocimiento o diseño defectuoso. Ej.: liberar código escrito por juniors sin revisión suficiente.

Es **un solo eje**, y coincide con el eje deliberada/inadvertida de Fowler; Fowler agrega el eje de la prudencia → ver [pregunta E11](#e11-tipos-de-deuda-de-mcconnell-vs-cuadrantes-de-fowler-se-solapan-qué-agrega-cada-clasificación).

**Buenas prácticas de control** [P1-CL06, p. 6]:

- **Registrar** cada deuda en un sistema de seguimiento/backlog, **con esfuerzo y fecha estimada**.
- **Tratarla como historias de usuario** (en enfoques ágiles); **si supera 90 días, marcarla como crítica**.
- Fomentar **transparencia y comunicación**: pagar la deuda en **incrementos pequeños y visibles** para todo el equipo.

El dato de los **90 días** se pregunta textual. Y notar lo que hacen las tres juntas: **convierten deuda inadvertida en deliberada** (registrándola) y **deuda imprudente en prudente** (dándole plan de pago). Son literalmente **una máquina de mover casos hacia el cuadrante prudente + deliberada**. *(inferencia)*

---

# Ciclo 2 — Comparación y aplicación

## A. Fundamentos y ciclos de vida

### A4. Cascada vs incremental frente al cambio, la entrega de valor y el riesgo

**Incremental.** "Los modelos incrementales implican desarrollar el software en **pequeños incrementos funcionales**. **Cada incremento es una versión completa del producto**, permitiendo la **entrega rápida de funcionalidades esenciales**." [P1-CL01, p. 9]

El diagrama muestra algo que el texto no dice y que conviene mencionar [P1-CL01, p. 10]: *Análisis de Requisitos del Sistema → Análisis de Requisitos Software → **Diseño Preliminar*** se hacen **una sola vez y son comunes a todos los incrementos**. A partir de ahí, cada **Incremento 1, 2, … n** repite su propio *Diseño Detallado → Codificación y Pruebas → Explotación y Mantenimiento*, con flechas de retorno hacia el Diseño Preliminar.

| Dimensión | **Cascada** | **Incremental** |
|---|---|---|
| **Ante el cambio** | Lo tolera mal: cada fase debe cerrarse antes de la siguiente, y volver atrás cuesta caro | Lo absorbe entre incrementos; lo que no absorbe es un cambio en los requisitos generales o en la arquitectura, que son comunes |
| **Entrega de valor** | **Al final**: no hay nada usable hasta el despliegue | **Temprana y progresiva**: cada incremento es una *versión completa*, y las funcionalidades esenciales salen primero |
| **Riesgo** | Concentrado al final: el error de requisitos se descubre en pruebas | Distribuido: cada incremento es una oportunidad de detectar el error, y el feedback del incremento 1 corrige el 2 |

**El punto fino.** Incremental **no elimina** la fase de requisitos ni la de arquitectura: las hace una vez, por adelantado, y las comparte. Por eso reduce el riesgo de *construcción* pero **no el riesgo arquitectónico ni el de requisitos globales** — si el Diseño Preliminar estaba mal, todos los incrementos heredan el error. Ese es justamente el hueco que viene a llenar la espiral, que **revisa objetivos y riesgos en cada vuelta**. *(inferencia a partir de la comparación de los diagramas de las pp. 10 y 12)*

La frase que sintetiza: *cascada apuesta a acertar una vez; incremental apuesta a corregir seguido dentro de un marco fijo; la espiral apuesta a cuestionar el marco en cada vuelta.*

### A5. Modelo de prototipo: qué valida y qué riesgo aparece si el prototipo se convierte en el producto

**Definición.** "Se centra en la **creación rápida de un prototipo funcional** que pueda ser **evaluado por los usuarios**. Este enfoque permite **identificar y solucionar problemas desde etapas tempranas**." [P1-CL01, p. 7]

**Qué valida: los requisitos, no la técnica.** El destinatario del prototipo es **el usuario**, y lo que devuelve es *"esto no era lo que yo quería"* o *"faltaría que además…"*. Sirve cuando el problema no es *cómo* construirlo sino *qué* construir — cuando el cliente no puede especificar en abstracto lo que necesita pero lo reconoce al verlo. *(inferencia)*

El diagrama lo muestra bien [P1-CL01, p. 8]: sobre la misma escalera de cascada aparecen **tres puntos marcados PROTOTIPO**, colgando a la altura de *Requisitos Software*, de *Diseño Preliminar* y de *Codificación*. Es decir, el prototipo **no es una fase** sino una actividad que se inserta en distintos momentos y **realimenta la fase correspondiente**.

**El riesgo de que el prototipo se vuelva producto.** Es el riesgo característico del modelo. El prototipo se construye optimizando **velocidad**, no calidad: sin arquitectura pensada, sin manejo de errores, sin pruebas, sin seguridad. Cuando el cliente lo ve funcionando, la presión para "terminarlo" en vez de rehacerlo es enorme — *"si ya funciona, ¿para qué empezar de nuevo?"*. Lo que se entrega entonces es un producto con **deuda técnica imprudente**, y frecuentemente **inadvertida**, porque nadie registró que ese código nació descartable. *(inferencia; el cruce con los cuadrantes de Fowler es propio)*

Riesgo secundario: **expectativas irreales de plazo**. Si el cliente vio algo funcionando en dos semanas, difícilmente acepte que el producto real lleve seis meses.

La mitigación es decidir **de antemano y por escrito** si el prototipo es *desechable* o *evolutivo*, y en el primer caso tirarlo de verdad. Ese compromiso explícito es lo que separa deuda deliberada + prudente de deuda imprudente (ver [pregunta E3](#e3--deuda-técnica-definición-origen-analogía-financiera-y-los-cuatro-cuadrantes-de-fowler)). *(inferencia)*

### A6. Proyecto con requisitos poco claros y alto riesgo técnico: ¿qué modelo elegís y por qué descartás los otros?

**Respuesta: espiral.** El enunciado nombra las **dos** incertidumbres que la espiral está diseñada para atacar, y ningún otro modelo del recorte cubre ambas.

**Por qué la espiral.** Se centra en la **identificación y reducción de riesgos a través de iteraciones sucesivas**, y **combina diseño y prototipado** [P1-CL01, p. 11]. Eso da las dos respuestas: el cuadrante de *evaluar alternativas, identificar y resolver los riesgos* con su serie de **prototipos 1 → 2 → 3 → operativo** ataca la incertidumbre técnica; y el cuadrante de *determinar objetivos, alternativas y restricciones*, que se recorre **en cada vuelta**, permite que los requisitos se vayan aclarando en lugar de tener que estar cerrados al inicio [P1-CL01, p. 12].

**Por qué se descartan los otros:**

| Modelo | Por qué no |
|---|---|
| **Cascada** | Exige **cerrar los requisitos antes de empezar** — es precisamente lo que no se puede hacer. Y concentra el descubrimiento de problemas técnicos en la fase de pruebas, al final |
| **Prototipo** | Resuelve **la mitad** del problema: aclara requisitos con el usuario, pero no ofrece ningún mecanismo sistemático para gestionar el riesgo técnico ni para decidir si conviene seguir |
| **Incremental** | Entrega valor temprano, pero **fija requisitos generales y Diseño Preliminar una sola vez, al principio** [P1-CL01, p. 10]. Con requisitos poco claros, ese marco común se construye sobre arena y todos los incrementos heredan el error |

**El matiz que suma:** la espiral **contiene** a los otros tres. Ejecuta cascadas en su cuadrante inferior derecho, usa prototipos en el superior derecho, y entrega productos de nivel creciente como el incremental. Elegirla no es descartar los demás sino **subordinarlos a un ciclo de decisión guiado por riesgo**. *(inferencia)*

**Y la contracara**, que conviene mencionar para que la respuesta no parezca una venta: la espiral es **más cara de gestionar y de estimar** — no se sabe cuántas vueltas habrá — y exige gente con criterio para evaluar riesgos. Si el proyecto fuera chico, el overhead no se justificaría. *(inferencia)*

## B. Metodologías

### B4. Los 5 valores y las 12 prácticas de XP: ¿cómo se refuerzan entre sí?

**Definición.** "XP es una metodología ágil que se enfoca en **mejorar la calidad del software** y la **capacidad de respuesta a los cambios** a través de **ciclos de desarrollo cortos** y **feedback continuo**." Prácticas clave que la lámina destaca: **programación en pareja, TDD, integración continua y refactorización constante**. Ventajas: comunicación constante, calidad del código y flexibilidad ante cambios del cliente. [P1-CL02, p. 11]

**Los 5 valores** [P1-CL02, p. 12]: **1. Comunicación · 2. Simplicidad · 3. Feedback · 4. Respeto · 5. Coraje**

**Las 12 prácticas** [P1-CL02, p. 13]:

| | | |
|---|---|---|
| 1. Cliente In-Situ | 5. Refactoring | 9. Estándares de Código |
| 2. Semana de 40 Horas | 6. Pair Programming | 10. Propiedad Colectiva |
| 3. Uso de Metáforas | 7. Entregas Cortas | 11. Integración Continua |
| 4. Diseño Simple | 8. Pruebas | 12. Juego de Planificación |

**Cómo se refuerzan.** La clave de la respuesta es que **los valores no son adornos motivacionales: cada práctica es un valor vuelto rutina diaria**, y las prácticas se sostienen unas a otras — quitar una debilita varias. *(el mapeo valor↔práctica es inferencia; la cátedra lista ambas cosas sin vincularlas explícitamente)*

| Práctica | Valor que encarna | Cómo lo vuelve concreto |
|---|---|---|
| **Cliente In-Situ** | **Comunicación** | En lugar de especificar por documento, se pregunta y se responde en el momento. Elimina el ciclo "duda → ticket → respuesta en tres días" |
| **Pair Programming** | **Comunicación** + **Respeto** | Revisión de código continua, en vivo; el conocimiento se difunde en lugar de concentrarse |
| **Pruebas** (y TDD) | **Feedback** + **Coraje** | Sin batería de pruebas nadie se anima a tocar código ajeno. Las pruebas son lo que **hace posible** el coraje |
| **Refactoring** | **Simplicidad** + **Coraje** | Mejora la estructura sin agregar función; solo es sensato si las pruebas avisan cuando algo se rompe |
| **Diseño Simple** | **Simplicidad** | No construir hoy lo que quizá se necesite mañana; el refactoring garantiza que agregarlo después será posible |
| **Integración Continua** | **Feedback** | Acorta el lazo entre escribir y saber si funciona, de semanas a minutos |
| **Entregas Cortas** | **Feedback** | El mismo acortamiento, pero del lado del cliente |
| **Propiedad Colectiva** | **Respeto** + **Coraje** | Cualquiera puede mejorar cualquier parte; requiere estándares de código y pruebas para no ser un caos |
| **Estándares de Código** | **Comunicación** | El código se lee como escrito por una sola persona; habilita la propiedad colectiva y el pairing |
| **Semana de 40 Horas** | **Respeto** | El equipo sostenible comete menos errores; el cansancio genera defectos y deuda |
| **Uso de Metáforas** | **Comunicación** | Vocabulario compartido entre negocio y técnica |
| **Juego de Planificación** | **Comunicación** + **Feedback** | Negocio y equipo deciden juntos, con estimación del equipo y prioridad del cliente |

**Los tres trípodes que conviene nombrar** *(inferencia)*:

- **Pruebas → Refactoring → Diseño Simple.** Diseño simple solo es responsable si se puede cambiar después; se puede cambiar gracias al refactoring; el refactoring es seguro gracias a las pruebas. **Sacá las pruebas y las otras dos se vuelven imprudentes.**
- **Estándares de Código → Propiedad Colectiva → Pair Programming.** Nadie toca código ajeno si no lo entiende; el estándar lo hace legible; el pairing lo hace familiar.
- **Integración Continua → Entregas Cortas → Cliente In-Situ.** Tres escalas del mismo lazo de feedback: minutos, semanas, permanente.

Ese entramado es lo que explica el eslogan: XP **mejora la calidad** no con una actividad de control al final, sino con prácticas de prevención permanentes. Es el gancho directo con [pregunta B12](#b12-parcial1-ciclo-de-tdd-y-cómo-se-relacionan-las-prácticas-de-xp-con-la-planificación-el-aseguramiento-y-el-control-de-la-calidad).

### B5. PRINCE2: características, procesos principales y qué significa "justificación continua del negocio"

**Origen y definición.** "**PRINCE2 (PRojects IN Controlled Environments)** es una metodología de **gestión de proyectos** desarrollada en el **Reino Unido**, ampliamente adoptada a nivel mundial. Su enfoque se centra en la **organización, gestión y control** de proyectos." [P1-CL02, p. 8]

**Características principales.** Define **roles y responsabilidades claros**, **procesos estructurados** y la importancia de la **justificación continua del negocio durante todo el ciclo de vida del proyecto**. [P1-CL02, p. 8]

Ojo con la primera línea: PRINCE2 es una metodología de **gestión de proyectos**, no de desarrollo de software. No dice cómo construir el producto; dice cómo gobernar el proyecto que lo construye. Eso la distingue de RUP, XP o Scrum. *(inferencia)*

**Los procesos** [P1-CL02, p. 9]:

| Proceso | Qué implica |
|---|---|
| **Inicio de Proyecto** | Definición de objetivos, equipo y organización. **Se crea el acta de constitución del proyecto** |
| **Dirección de Proyecto** | Tomar **decisiones estratégicas**, **aprobar fases** y resolver problemas **escalados**. Se mantiene la justificación del negocio |
| **Control de Fase** | **Monitoreo y control** de la ejecución de una fase. Se **gestionan riesgos y problemas** |

**Los temas transversales** [P1-CL02, p. 10]:

- **Justificación Continua del Negocio**: asegura que el proyecto **sigue siendo viable y rentable a lo largo de su ciclo de vida**.
- **Gestión de Riesgos**: identificación, evaluación y control de riesgos que puedan afectar al proyecto.
- **Calidad**: definición y control de los **estándares de calidad requeridos** para cumplir con los objetivos.

**Qué significa la justificación continua del negocio.** Es el principio distintivo de PRINCE2 y lo que más se pregunta. La palabra que hace el trabajo es **continua**: el caso de negocio no se aprueba una vez al comienzo y se archiva, sino que **se revalida en cada punto de control**, y si deja de cerrar, **el proyecto se cancela aunque esté en tiempo y presupuesto**.

Eso invierte el criterio de éxito habitual. Un proyecto que cumple plazo, costo y alcance pero cuya justificación desapareció —cambió el mercado, apareció un competidor, la regulación lo volvió inútil— es un proyecto que **debe detenerse**, y detenerlo a tiempo es un éxito de gestión, no un fracaso. Por eso la estructura tiene **fases con aprobación explícita** ("Dirección de Proyecto: aprobar fases"): cada límite de fase es una oportunidad institucional de decir que no. *(inferencia)*

**El paralelo que suma puntos:** es la misma lógica del **"pivotar o perseverar"** de Lean Startup ([pregunta C6](#c6-qué-evidencia-justifica-pivotar-y-cuál-perseverar-qué-no-significa-pivotar)) y del cuadrante de **evaluación de riesgos** de la espiral ([pregunta A3](#a3-describí-el-modelo-en-espiral-en-qué-se-centra-y-por-qué-es-iterativo)): puntos de decisión periódicos donde se puede abortar. Cambia el vocabulario y el ámbito —gobernanza corporativa, producto, ingeniería— pero el mecanismo es el mismo: **no dejar que el compromiso previo decida por la evidencia nueva**. *(inferencia)*

### B6. Kanban vs Scrum: flujo continuo vs iteración. ¿Qué problema resuelve limitar el WIP?

**Kanban.** "Metodología ágil que utiliza **tarjetas visuales en un tablero** para gestionar y optimizar el **flujo de trabajo**, permitiendo ver el estado de las tareas **en tiempo real**." **Principios**: visualización del trabajo, **limitación del trabajo en progreso**, gestión del flujo y mejora continua. **Ventajas**: facilita la identificación de **cuellos de botella**, mejora la comunicación y **aumenta la flexibilidad para adaptarse a cambios en las prioridades**. [P1-CL02, p. 16]

**La comparación** *(contraste propio a partir de [P1-CL02, pp. 16] y [P1-CL02, pp. 17–19])*:

| | **Scrum** | **Kanban** |
|---|---|---|
| **Unidad de ritmo** | El **sprint**: caja de tiempo fija de 1 a 4 semanas | **Flujo continuo**: no hay iteración |
| **Compromiso** | El equipo se **compromete** con un Sprint Backlog negociado | No hay compromiso por lote; se toma la siguiente tarjeta cuando hay capacidad |
| **Cambio de prioridad** | Entre sprints; durante el sprint el alcance está acordado | **En cualquier momento** — de ahí la "flexibilidad para adaptarse a cambios en las prioridades" |
| **Límite** | La **cantidad de tiempo** está fija | La **cantidad de trabajo simultáneo** está fija (WIP) |
| **Roles** | Tres roles definidos (PO, SM, Equipo) | No prescribe roles |
| **Métrica de avance** | **Burndown** del sprint | Flujo y cuellos de botella en el tablero |

**La diferencia de fondo, en una línea:** **Scrum fija el tiempo y pregunta cuánto trabajo entra; Kanban fija el trabajo simultáneo y deja que el tiempo sea la variable.** Son dos maneras distintas de imponer un límite, y ninguna de las dos deja el sistema sin límite. *(inferencia)*

**Qué problema resuelve limitar el WIP.** La lámina lo enuncia como principio y nombra su beneficio —identificar **cuellos de botella**—, pero el mecanismo merece desarrollarse:

- **Sin límite de WIP, el trabajo se acumula en la etapa más lenta y nadie lo nota.** Todos están ocupados, el tablero está lleno, y sin embargo casi nada llega a "terminado". La ocupación individual es alta y el **throughput** es bajo.
- **Con límite de WIP, la columna saturada se bloquea** y deja de admitir tarjetas. Eso **obliga a mirar el cuello de botella** en lugar de rodearlo empezando otra cosa: el equipo tiene que ir a ayudar donde está la traba, porque no puede seguir arrancando trabajo nuevo.
- **Reduce el multitasking y el tiempo de ciclo.** Cada ítem empezado y no terminado es inventario: cuesta memoria, cuesta contexto, y no entrega valor hasta que termina.
- **Hace visible la capacidad real.** El límite convierte una intuición ("estamos al límite") en una regla observable en el tablero. *(desarrollo del mecanismo: inferencia)*

**El puente con Lean** ([pregunta B9](#b9-lean-qué-es-el-desperdicio-en-software-y-cómo-lo-atacan-kanban-y-el-mvp)): el trabajo en progreso es **inventario**, y el inventario es uno de los desperdicios clásicos. Limitar el WIP es aplicar la idea Lean de **crear flujo continuo** eliminando acumulaciones.

## C. Productos digitales

### C4. Componentes y proceso de un A/B test, más buenas prácticas

**Definición.** "Técnica de experimentación que consiste en **comparar dos versiones (A y B)** de un elemento (página web, producto, funcionalidad, anuncio) para **medir cuál obtiene mejores resultados en función de una métrica definida** (conversión, clics, ventas)." [P1-CL04, p. 7]

**Características** [P1-CL04, p. 8]. Objetivo principal: **validar hipótesis** y mejorar la experiencia del usuario o los resultados de negocio.

- **Comparación directa**: muestra dos variantes de un mismo elemento a **grupos de usuarios similares**.
- **Basado en datos**: las decisiones se fundamentan en métricas objetivas, no en suposiciones.
- **Iterativo**: se repite varias veces para refinar y optimizar de forma continua.

**Los cinco componentes** [P1-CL04, p. 9]:

| Componente | Qué es |
|---|---|
| **Hipótesis** | Definir el cambio que se quiere probar **y el objetivo** de ese cambio |
| **Población y muestra** | Seleccionar los usuarios o el tráfico que participará |
| **Variante A** | Versión de **control** (la actual o la más estable) |
| **Variante B** | Versión **experimental** (con la modificación propuesta) |
| **Métricas** | Definir qué se va a medir (tasa de clics, conversión, etc.) |

**El proceso, en seis pasos** [P1-CL04, p. 9]:

```
1. Planteamiento de la hipótesis — qué se espera mejorar y por qué
2. Diseño del experimento — variantes, % de tráfico asignado, herramientas de medición
3. Ejecución — mostrar simultáneamente A y B a distintos usuarios
4. Recolección de datos — interacciones, conversión, tiempo de permanencia
5. Análisis de resultados — comparar métricas y evaluar si la diferencia es
   estadísticamente significativa
6. Conclusión y acción — adoptar la versión ganadora o diseñar un nuevo experimento
```

**Buenas prácticas** [P1-CL04, p. 10]:

- **Definir las métricas claras antes de iniciar** la prueba.
- **Una sola variable de cambio por prueba**, para aislar el efecto.
- Usar herramientas de análisis y seguimiento para garantizar exactitud en los datos.
- **Mantener la prueba el tiempo suficiente** para obtener resultados estadísticamente significativos.
- **Documentar todo el proceso** (hipótesis, resultados, conclusiones) para reutilizar el aprendizaje.

Las dos primeras son las que más se preguntan y las dos que más se violan. *Métricas antes de empezar*: si se eligen después, siempre aparece alguna métrica en la que B ganó, y eso ya no es un experimento. *Una sola variable*: si B cambia el color **y** el texto **y** la posición, un resultado positivo no dice cuál de los tres funcionó, y ni siquiera descarta que uno haya sido dañino y otro muy bueno. *(inferencia)*

Y la tercera —*el tiempo suficiente*— es la que conecta con el ciclo BML: hay una **tensión real** entre "acortar la vuelta al mínimo" ([pregunta C1](#c1-lean-startup-qué-es-quién-lo-popularizó-y-en-qué-consiste-el-ciclo-buildmeasurelearn)) y "esperar lo necesario para tener significancia". Cortar un test apenas se ve una diferencia favorable es la forma más común de aprender algo falso. *(inferencia)*

**Casos de uso y ejemplos de la cátedra** [P1-CL04, p. 11]: optimización de landing pages; mejora de funnels de compra (reducir carritos abandonados); campañas de email marketing (asuntos, contenidos, CTA); diseño de interfaces. Ejemplos concretos: e-commerce que cambia el color del botón "Comprar ahora" (A azul, B verde) para medir impacto en ventas; app de reservas que prueba distintos textos o iconos en el botón "Reservar" midiendo reservas confirmadas; sitio de noticias que compara portada con imagen principal grande (A) contra titulares en texto (B) midiendo tiempo de permanencia.

### C5. Métricas accionables vs vanidosas; qué aportan analytics, logging y tracking de funnels

**El principio.** La lámina de *Medir* abre con: "Definir **métricas accionables y comparables (evitar métricas vanidosas)**", usar **experimentos controlados (A/B testing, cohortes)** y capturar **datos cuantitativos y cualitativos en tiempo real**. [P1-CL04, p. 6]

**Accionable vs vanidosa.** *(la lámina nombra la distinción sin desarrollarla; lo que sigue es inferencia)* Una métrica es **vanidosa** cuando sube siempre, no distingue entre hipótesis y no indica qué hacer a continuación: usuarios registrados acumulados, descargas totales, page views. Suben con el tiempo y con el gasto en marketing, así que confirman cualquier cosa que uno quiera creer.

Una métrica es **accionable** cuando cumple tres condiciones: (1) **distingue** — cambia de manera distinta según la hipótesis sea cierta o falsa; (2) es **comparable** —la palabra está en la lámina— porque permite contrastar A contra B, o una cohorte contra otra; (3) **indica una decisión**: si sube, se hace X; si baja, se hace Y. Tasa de retención a 30 días, conversión por etapa del funnel y porcentaje de usuarios activos son accionables; el acumulado de registros, no.

Por eso la lámina las asocia a **experimentos controlados y cohortes**: el control y la cohorte son exactamente los mecanismos que convierten un número en una comparación.

**La instrumentación** [P1-CL04, p. 6]:

| Herramienta | Qué hace | Para qué sirve |
|---|---|---|
| **Analytics** (analítica de producto) | Plataformas que **recopilan y visualizan métricas de uso** (tiempo de sesión, tasa de retención) | **Traducir el comportamiento real de los usuarios en indicadores accionables** para validar hipótesis de valor o de crecimiento |
| **Logging** (registro de eventos y errores) | Registro **estructurado y con marcas de tiempo** de lo que sucede en la aplicación: interacciones, estados, fallos | Detectar patrones, **diagnosticar problemas rápidamente** y **medir el impacto técnico de cada experimento sin adivinar** |
| **Tracking de funnels** (embudos) | Instrumentación que **mapea los pasos clave del usuario** (visitar → registrarse → activar → pagar) y calcula las **tasas de conversión entre etapas** | **Revelar dónde se "caen" los usuarios**, priorizando qué hipótesis probar o qué mejoras lanzar primero |

Las tres cubren planos distintos y se complementan: **analytics** mide *qué* hacen los usuarios, **logging** explica *qué pasó por dentro* cuando lo hicieron (incluido el plano técnico, que es el que suele faltar), y **funnels** localiza **dónde** se pierde el valor. La última es la que prioriza: un embudo con 90 % de caída entre "registrarse" y "activar" dice, sin ambigüedad, cuál es el próximo experimento. *(inferencia)*

### C6. ¿Qué evidencia justifica pivotar y cuál perseverar? ¿Qué NO significa pivotar?

**La lámina de Aprender** [P1-CL04, p. 12]:

- **Convertir datos en aprendizaje validado.**
- **Decidir "pivotar o perseverar" basados en evidencia.**
- **Documentar hallazgos y actualizar el backlog / hoja de ruta.**
- **Comunicación transparente** para alinear al equipo e inversores.

**Pivotar.** "Cambiar de rumbo —ajustar la **propuesta de valor**, el **segmento de clientes**, el **modelo de ingresos** o la **tecnología**— porque **la evidencia muestra que la hipótesis principal no se confirma**."

**Perseverar.** "Seguir por el mismo camino porque **los datos indican tracción**, **las métricas clave mejoran de forma consistente** y el **problema-cliente parece bien encajado con la solución**."

**Qué evidencia justifica cada uno:**

| | Evidencia |
|---|---|
| **Perseverar** | **Tracción** en los datos; **mejora consistente** de las métricas clave (consistente = sostenida en el tiempo, no un pico); indicios de **encaje problema-solución** |
| **Pivotar** | La **hipótesis principal no se confirma**: las métricas accionables no se mueven pese a varias iteraciones, o se mueven en la dirección equivocada |

Lo que hace comparable a ambas es que se apoyan en **métricas accionables** (C5): si la métrica es vanidosa, siempre va a parecer que hay que perseverar, porque los números acumulados siempre suben. *(inferencia)*

**Qué NO significa pivotar** — la lámina es explícita y es la parte más preguntable:

> "**No es 'empezar de cero'**; es **redirigir la energía hacia una oportunidad mejor fundamentada**."

El pivot **conserva el aprendizaje validado**. Se cambia **uno** de los elementos —propuesta de valor, segmento, modelo de ingresos o tecnología— manteniendo el resto y, sobre todo, manteniendo lo que ya se aprendió sobre el cliente. Un equipo que descubre que su solución no sirve a las PyMEs pero sí a las grandes cuentas pivota el **segmento**; no tira el producto. *(ejemplo propio)*

Los **cuatro ejes de pivot** que nombra la lámina son, no por casualidad, **cuatro bloques del Business Model Canvas**: propuesta de valor, segmentos de clientes, fuentes de ingresos y (vía recursos clave) tecnología. Pivotar es cambiar una celda del Canvas manteniendo las demás → ver [pregunta C9](#c9-cómo-se-complementan-design-thinking-business-model-canvas-y-lean-startup-en-un-mismo-proyecto). *(inferencia)*

Los dos últimos puntos de la lámina cierran el ciclo y suelen olvidarse: **documentar y actualizar el backlog** (el aprendizaje tiene que volverse trabajo priorizado, si no se pierde) y **comunicación transparente con equipo e inversores** (un pivot no comunicado se lee como fracaso o como capricho).

## D. Estimación

### D4. Puntos de Caso de Uso: definición, proceso, qué se pondera y ventajas

**Definición.** "Método de estimación **basado en la complejidad y número de casos de uso** en un proyecto. Ayuda a evaluar el **tamaño del software y el esfuerzo necesario**." [P1-CL05, p. 2]

**Proceso.** "Se asigna una **ponderación a cada caso de uso según su complejidad**, sumando estos valores para obtener la estimación total del proyecto." [P1-CL05, p. 2]

**Ventajas.** "Proporciona una **visión clara del alcance** del proyecto y **facilita la comunicación entre desarrolladores y stakeholders**." [P1-CL05, p. 2]

Esa segunda ventaja no es menor: a diferencia de las líneas de código, **el caso de uso es una unidad que el negocio entiende**. Se puede discutir con un stakeholder si un caso de uso es simple o complejo; no se puede discutir con él cuántas líneas va a tener. *(inferencia)*

**Qué se pondera.** Las dos láminas siguientes son tablas [P1-CL05, pp. 3–4]. *Advertencia de fuente: en el texto extraído estas tablas aparecen vacías porque son objetos embebidos; los valores que siguen se leyeron renderizando la presentación original.*

**a) Ponderación de Casos de Uso** — *Unadjusted Use Case Points*, por cantidad de transacciones:

| Tipo | Multiplicador | Criterio |
|---|---|---|
| **Simple** | **5** | Hasta 3 transacciones |
| **Average** | **10** | De 4 a 7 transacciones |
| **Complex** | **15** | Más de 7 transacciones |

**b) Ponderación de Actores** — *Actor Weight*, por tipo de interlocutor:

| Tipo | Multiplicador | Criterio |
|---|---|---|
| **Simple** | **1** | Otro sistema que se comunica por una **API predefinida** (dll, REST, SOAP, RPC) |
| **Average** | **2** | Sistemas que interactúan por una **API más compleja o flexible**, o humanos vía un protocolo bien definido |
| **Complex** | **3** | **Usuarios que interactúan por interfaz gráfica** |

Notar el criterio: **cuanto más impredecible el interlocutor, más pesa**. Una API responde siempre igual; una persona frente a una pantalla, no.

**c) Factores Ambientales** (8) — características del **equipo y el entorno**, cada uno valuado de 0 a 5 y multiplicado por:

| # | Factor | Mult. | # | Factor | Mult. |
|---|---|---|---|---|---|
| 1 | Familiaridad con el proyecto | **1,5** | 5 | Motivación | 1 |
| 2 | Experiencia en la aplicación | 0,5 | 6 | Requisitos estables | **2** |
| 3 | Experiencia en programación OO | 1 | 7 | Personal part-time | **−1** |
| 4 | Capacidad del analista líder | 0,5 | 8 | Lenguaje de programación difícil | **−1** |

**d) Factores Técnicos** (13) — características del **sistema a construir**, también de 0 a 5:

| # | Factor | Mult. | # | Factor | Mult. |
|---|---|---|---|---|---|
| 1 | Sistema distribuido | **2** | 8 | Soporte multiplataforma | **2** |
| 2 | Tiempo de respuesta importante | 1 | 9 | Facilidad de cambio | 1 |
| 3 | Eficiencia del usuario final | 1 | 10 | Alta concurrencia | 1 |
| 4 | Procesamiento interno complejo | 1 | 11 | Seguridad a medida | 1 |
| 5 | Foco en código reutilizable | 1 | 12 | Dependencia de código de terceros | 1 |
| 6 | Facilidad de instalación | 0,5 | 13 | Capacitación de usuarios | 1 |
| 7 | Usabilidad | 0,5 | | | |

**Los dos detalles preguntables:**

1. **Hay multiplicadores negativos** — *Personal part-time* y *Lenguaje de programación difícil*, ambos **−1**. Son los únicos dos factores que, cuanto más presentes, **empeoran** la estimación en lugar de mejorarla. Eso hace explícito algo que las estimaciones informales suelen ignorar: **la gente compartida entre proyectos y una tecnología hostil no son neutras, restan**.
2. **Los pesos más altos marcan qué le importa al método**: en lo ambiental, *requisitos estables* (2) y *familiaridad con el proyecto* (1,5); en lo técnico, *sistema distribuido* (2) y *multiplataforma* (2). Es decir, el método considera que **la inestabilidad de requisitos y la distribución son los mayores multiplicadores de esfuerzo**. Coincide con el criterio de selección de metodología de [pregunta B1](#b1-qué-tres-criterios-de-selección-de-metodología-plantea-la-cátedra-y-hacia-dónde-inclina-cada-uno). *(inferencia)*

**Lo que el método logra conceptualmente**: PCU separa lo que [pregunta D1](#d1-diferenciá-tamaño-esfuerzo-complejidad-y-duración) distingue. Los casos de uso y actores dan el **tamaño**; los factores técnicos ajustan por **complejidad del producto**; los ambientales ajustan por **capacidad del equipo**, que es lo que convierte tamaño en **esfuerzo**. *(inferencia)*

*Alcance:* el **cálculo final de PCU** y la **consulta sobre factor de productividad** **quedaron fuera del recorte**, así que no hay que memorizar la fórmula de cierre ni la conversión a horas. Lo que entra es **qué se pondera y con qué criterio**. [N-2026-09-07-alcance-primer-parcial]

### D5. Planning Poker: proceso, por qué el voto es secreto y simultáneo, y qué revela la divergencia

**Definición.** "Método de **estimación colaborativa** en el que los miembros del equipo usan **cartas para votar sobre el tamaño relativo** de las tareas del proyecto." [P1-CL05, p. 5]

**Proceso.** "Cada miembro selecciona una carta **en secreto** y **todas las cartas se revelan al mismo tiempo**. **Las discusiones se centran en las diferencias de estimaciones** hasta alcanzar un **consenso**." [P1-CL05, p. 5]

**Ventajas.** "Fomenta la **participación de todo el equipo**, mejora la **precisión** de las estimaciones y ayuda a **identificar riesgos y dependencias tempranas**." [P1-CL05, p. 5]

**Por qué secreto y simultáneo.** Los dos adjetivos atacan el mismo problema: el **anclaje** y la **influencia jerárquica**. *(la lámina describe el mecanismo; la explicación del porqué es inferencia, apoyada en lo que la cátedra dice de Wideband Delphi)*

Si las estimaciones se dijeran en voz alta y por turnos, la primera cifra **ancla** a todas las demás: el resto ajusta alrededor de ese número en lugar de pensar de cero. Y si el primero en hablar es el más senior o el líder técnico, nadie contradice. El resultado sería una estimación con apariencia de consenso que en realidad es **la opinión de una persona repetida por el grupo**.

El secreto obliga a que cada uno forme su juicio **independientemente**; la simultaneidad garantiza que nadie pueda ajustar el suyo después de ver los demás. Es exactamente el mismo objetivo que la cátedra atribuye al **Método Delphi**: *"reduce la influencia de jerarquías o liderazgos fuertes (al ser anónimo)"* [P1-CL05, p. 8].

**Qué revela la divergencia** — y esta es la parte que da el punto entero. **El valor de Planning Poker no está en el número final sino en el desacuerdo**, porque la lámina dice que *las discusiones se centran en las diferencias*. Una divergencia grande —uno vota 2 y otro 13— casi nunca significa que uno estimó mal. Significa que **están estimando cosas distintas**:

- **Entienden el alcance de manera diferente.** Uno incluyó la migración de datos, el otro no.
- **Alguien sabe algo que los demás no.** El que votó 13 conoce una dependencia con un sistema legado, o ya se quemó con eso antes. Ahí aparecen los **riesgos y dependencias tempranas** que la lámina menciona como ventaja.
- **La historia está mal escrita o es demasiado grande**, y admite lecturas distintas. Es señal de que hay que partirla.

Por eso el proceso correcto ante una divergencia no es promediar —promediar **destruye** la información— sino **hacer hablar a los extremos**: que el más alto y el más bajo expliquen su razonamiento, y volver a votar. La convergencia posterior es valiosa porque llegó después de compartir el conocimiento que estaba disperso.

Conecta con la **participación de todo el equipo**: quien estima es quien va a hacer el trabajo, lo que aumenta el compromiso con el número y evita la estimación impuesta desde afuera. *(inferencia)*

### D6. Story Points: ¿qué miden y por qué no se traducen directamente a horas?

**Definición.** "**Unidad de medida** utilizada en metodologías ágiles para estimar el **esfuerzo relativo** necesario para implementar una **historia de usuario**." [P1-CL05, p. 6]

**Proceso.** "Los equipos asignan puntos a cada historia basándose en su **complejidad**, **cantidad de trabajo** y **riesgos involucrados**, usando técnicas como **Planning Poker**." [P1-CL05, p. 6]

**Ventajas.** "Facilita la **planificación y priorización**, promueve la **colaboración del equipo** y permite un **seguimiento más preciso del progreso**." [P1-CL05, p. 6]

**Qué miden: tres cosas a la vez.** La definición es explícita —complejidad + cantidad de trabajo + riesgo— y esa **mezcla deliberada** es el rasgo distintivo. Volviendo a [pregunta D1](#d1-diferenciá-tamaño-esfuerzo-complejidad-y-duración): los Story Points **no son tamaño puro** (como las líneas de código) ni esfuerzo puro; combinan el tamaño con la dificultad y con la incertidumbre en una sola escala. Una historia chica pero muy riesgosa puede valer más puntos que una grande y rutinaria.

**Por qué no se traducen a horas.** Cuatro razones, en orden de peso:

1. **Son relativos, no absolutos.** La palabra está en la definición: *esfuerzo **relativo***. Un punto no es una cantidad, es una **referencia**: esta historia es el doble de aquella. Las personas somos malísimas estimando duraciones absolutas y bastante buenas comparando tamaños — pedir "¿cuánto tarda?" activa el sesgo de optimismo; pedir "¿es más grande que aquella?" no. *(inferencia)*
2. **Los puntos incluyen riesgo, y las horas no.** Si 1 punto = 4 horas, ¿cuántas horas son el riesgo? La conversión obliga a descartar justamente la dimensión que los puntos agregaron.
3. **El mismo punto significa esfuerzos distintos según quién lo haga.** Los puntos describen **la historia**; las horas describen **una persona haciendo la historia**. Por eso los puntos sobreviven a los cambios de asignación y las horas no.
4. **Y la razón de gestión: convertir a horas reabre la puerta a la Ley de Parkinson y al control por tiempo.** Si el equipo declara 40 horas, el equipo queda comprometido con un reloj; si declara 8 puntos, queda comprometido con un **tamaño**, y cuánto se entrega por sprint lo determina la **velocidad observada**, no una promesa. El progreso se mide con hechos —lo efectivamente terminado, visible en el burndown ([pregunta B3](#b3-scrum-roles-artefactos-y-ceremonias-con-la-función-de-cada-uno))— en lugar de con una conversión teórica. Eso es lo que la lámina llama "seguimiento más preciso del progreso". *(inferencia)*

**El matiz honesto que conviene agregar:** los puntos sí se convierten en previsión de plazo, pero **a nivel de equipo y estadísticamente**, vía velocidad promedio de varios sprints — no ítem por ítem con un tipo de cambio fijo. La diferencia es que la velocidad **se mide**, mientras que el factor de conversión **se inventa**. *(inferencia)*

## E. Calidad

### E4. Costo de calidad vs costo de no calidad; fallos internos vs externos

[P1-CL06, p. 3]

- **Costo de calidad (CoQ)**: "Gastos **necesarios para prevenir defectos** y garantizar un producto de alta calidad." Ejemplos: **entrenamiento, revisiones, auditorías**.
- **Costo de "no calidad"**: "Gastos **derivados de errores o fallos** en el producto."
  - **Fallos internos**: **reparaciones previas al lanzamiento**.
  - **Fallos externos**: **reclamos de clientes, pérdidas de reputación**.
- **Conclusión de la lámina**: "**Invertir en calidad reduce significativamente los costos de no calidad**."

**Cómo se relacionan las cuatro categorías** *(el encadenamiento es inferencia; las definiciones son textuales)*:

```
   ┌──── Costo de CALIDAD (inversión, voluntaria) ────┐
   │  Prevención          Evaluación                  │
   │  (entrenamiento,     (revisiones,                │
   │   estándares)         auditorías, pruebas)       │
   └──────────────────────────────────────────────────┘
                        ↓ lo que se escapa
   ┌──── Costo de NO CALIDAD (consecuencia, forzosa) ─┐
   │  Fallos INTERNOS          Fallos EXTERNOS        │
   │  (detectados antes        (detectados por        │
   │   del lanzamiento)         el cliente)           │
   └──────────────────────────────────────────────────┘
```

Las dos primeras son **inversión decidida**; las dos últimas son **consecuencia sufrida**. Y hay una relación de sustitución: **cuanto más se gasta arriba, menos se paga abajo** — que es exactamente la conclusión de la lámina.

**El punto clave: el costo crece en cada escalón.** Un defecto prevenido cuesta casi nada; detectado en una revisión cuesta poco; encontrado antes del lanzamiento cuesta una corrección más un retesteo; y llegado al cliente cuesta la corrección, el despliegue de emergencia, el soporte, la compensación y —lo peor, porque **no se recupera**— la reputación. La lámina lo señala al listar entre los fallos externos las *"pérdidas de reputación"*: es la única partida de las cuatro que **no se puede pagar con dinero para volver al estado anterior**. *(inferencia)*

**La diferencia entre fallo interno y externo no es de gravedad técnica sino de quién lo encontró.** El mismo bug, con el mismo código, es interno si lo halla el equipo y externo si lo halla el usuario. Por eso todo el aparato de QC —pruebas, revisiones, smoke tests— se entiende como una **máquina de convertir fallos externos en internos**, que es el mismo tipo de movimiento que las buenas prácticas de deuda técnica hacen sobre los cuadrantes de Fowler ([pregunta E3](#e3--deuda-técnica-definición-origen-analogía-financiera-y-los-cuatro-cuadrantes-de-fowler)). *(inferencia)*

**Y el enlace con deuda técnica**, que la cátedra hace explícito al presentarla como *"caso especial de No Calidad"* [P1-CL06, p. 4]: la deuda técnica es un costo de no calidad **diferido y con intereses**. No aparece como fallo interno ni externo el día de la entrega; aparece como sobrecosto en **cada cambio futuro**. Es la partida que no figura en ninguna de las cuatro casillas y que por eso se ignora — hasta que domina el presupuesto. *(inferencia)*

### E5. Verificación vs validación, con una técnica concreta para cada una

[P1-CL06, p. 11]

- **Verificación**: "Asegura que el producto **se esté construyendo correctamente según los requisitos especificados**." Ejemplo: **revisiones de código, inspecciones**.
- **Validación**: "Comprueba que el **producto final cumple con las necesidades del cliente**." Ejemplo: **pruebas funcionales, pruebas de usuario**.
- **Técnicas comunes** que la lámina agrupa: **revisiones técnicas, pruebas de integración, simulaciones**.

**La formulación que conviene memorizar** *(conocimiento general, consistente con la lámina)*:

| | Pregunta | Contrasta contra | Ejemplo de la cátedra |
|---|---|---|---|
| **Verificación** | ¿Estamos construyendo **el producto correctamente**? | La **especificación** | Revisiones de código, inspecciones |
| **Validación** | ¿Estamos construyendo **el producto correcto**? | La **necesidad del cliente** | Pruebas funcionales, pruebas de usuario |

**Por qué la distinción importa: se puede verificar con éxito un producto inválido.** Un sistema puede cumplir la especificación al pie de la letra —cero defectos, todas las revisiones pasadas— y aun así no servirle a nadie, porque **la especificación estaba mal**. La verificación nunca detecta ese caso: mide contra el documento, y el documento es el que está equivocado. Solo la validación, que contrasta contra la necesidad real, puede descubrirlo. *(inferencia)*

De ahí se siguen dos consecuencias:

- **La validación no puede posponerse al final.** Si se valida recién en aceptación, un error de especificación se descubre cuando ya está todo construido — es exactamente el fallo de cascada ([pregunta A2](#a2-qué-es-un-ciclo-de-vida-del-software-y-cuáles-son-las-fases-típicas-del-modelo-en-cascada)). Por eso los modelos con feedback temprano —prototipo, incremental, espiral— y las ceremonias de **Revisión** de Scrum, donde el PO acepta o rechaza cada sprint, son en el fondo **mecanismos de validación anticipada**.
- **Se relaciona con QA/QC pero es otro eje.** Ambas son actividades de **QC** —miran el producto—. QA/QC responde *sobre qué actúo* (proceso o producto); V&V responde *contra qué contrasto* (la especificación o la necesidad). *(inferencia)*

Y un detalle de la lámina que puede confundir: las **revisiones de código** aparecen como ejemplo de verificación acá y como actividad de **QC** en la lámina de control de calidad [P1-CL06, p. 8]. No es contradicción: una revisión de código es una actividad de QC (mira el producto) de tipo verificación (contrasta contra la especificación) y **estática** (no ejecuta el código, ver [pregunta E6](#e6-clasificación-de-las-pruebas-por-nivel-técnica-alcance-y-automatización-qué-es-un-smoke-test)). Las tres clasificaciones son **ejes independientes** que se aplican a la vez.

### E6. Clasificación de las pruebas por nivel, técnica, alcance y automatización. ¿Qué es un smoke test?

La cátedra clasifica en **cuatro ejes independientes**, que se aplican simultáneamente a una misma prueba [P1-CL06, pp. 12–13].

**1) Según el nivel**

| Nivel | Qué valida |
|---|---|
| **Pruebas unitarias** | **Componentes individuales** |
| **Pruebas de integración** | Que los **módulos funcionan juntos** |
| **Pruebas del sistema** | El **software completo** |
| **Smoke test** | **Conjunto reducido de pruebas de sistema** |
| **Pruebas de aceptación** | Realizadas **por el cliente** para **validar requisitos** |

**Smoke test**: "Se la llama así porque es **'ver si sale humo' apenas se enciende el sistema**: si falla, **no vale la pena seguir probando**." [P1-CL06, p. 12]

Su función no es encontrar defectos sino **decidir si tiene sentido ejecutar la batería completa**. Es un filtro barato que se corre primero: si el sistema no arranca o las funciones críticas están rotas, ejecutar dos horas de pruebas detalladas es desperdicio. *(inferencia)*

Notar además que el nivel **de aceptación es el único que cambia de responsable**: lo hace **el cliente**, y por eso es el único que **valida** en lugar de verificar (ver [pregunta E5](#e5-verificación-vs-validación-con-una-técnica-concreta-para-cada-una)). Los otros contrastan contra la especificación; este, contra la necesidad. *(inferencia)*

**2) Según la técnica**

- **Pruebas estáticas**: evaluación **sin ejecutar el código** (revisiones, inspecciones).
- **Pruebas dinámicas**: **ejecución activa** para detectar defectos.

**3) Según el alcance**

- **Funcionales**: validan funcionalidades específicas.
- **No funcionales**: evalúan rendimiento, seguridad, usabilidad, etc.

La cátedra desglosa las **no funcionales de sistema** [P1-CL06, p. 13]:

| Tipo | Qué comprueba |
|---|---|
| **Recuperación** | Que el sistema pueda **recuperarse de fallas y reanudar el procesamiento** |
| **Seguridad** | Que funcionen los mecanismos de protección (**pentest**) |
| **Compatibilidad / despliegue** | Varias plataformas y más de un entorno de sistema operativo |
| **Esfuerzo / rendimiento** | Demanda de recursos en **cantidad, frecuencia o volumen anormales** |
| **Usabilidad** | La **experiencia del usuario** |
| **Escalabilidad** | Cómo responde el sistema **al crecimiento**: **vertical** (aumentar recursos de un solo servidor — más CPU, memoria) u **horizontal** (agregar más servidores para compartir la carga) |

**4) Según la automatización**

- **Manuales**: realizadas por testers.
- **Automatizadas**: usan scripts y herramientas.

**Cómo usar esto en una respuesta.** El error típico es tratar los cuatro ejes como una sola lista. Lo correcto es mostrar que **se combinan**: una prueba de carga es *de sistema* (nivel), *dinámica* (técnica), *no funcional* (alcance) y normalmente *automatizada*. Una revisión de código es *estática*, no tiene nivel en este esquema, y es una actividad de **QC** de tipo **verificación**. Poder ubicar un ejemplo en los cuatro ejes a la vez es lo que distingue una respuesta completa. *(inferencia)*

**Técnicas y estrategias** que la lámina siguiente agrega [P1-CL06, p. 14] y que se desarrollan en [pregunta E9](#e9-caja-negra-vs-caja-blanca-partición-de-equivalencia-y-análisis-de-valores-límite): **caja negra**, **caja blanca**, **técnicas híbridas**, generación de casos efectivos (identificar escenarios clave, partición de equivalencia, análisis de valores límite) y **gestión de riesgos** (priorización según impacto y probabilidad de fallos).

---

# Ciclo 3 — Integración

## A. Fundamentos y ciclos de vida

### A7. [PARCIAL1] ¿Qué relación hay entre los modelos de ciclo de vida del software y la deuda técnica?

Pregunta 2 del parcial anterior. [PARCIAL1, p. 1] Es relacional pura: hay que construir el puente entre dos temas que el material presenta por separado. La respuesta tiene tres movimientos.

**1) El ciclo de vida determina cuándo se puede corregir — y por lo tanto cuánta deuda se acumula.**

La deuda técnica es el **costo de retrabajo que aparece cuando se prioriza una solución rápida por sobre la más efectiva** [P1-CL06, p. 4]. Esa priorización ocurre bajo presión, y **el ciclo de vida decide cuándo y con qué frecuencia llega esa presión**:

| Modelo | Cuándo aprieta la presión | Efecto sobre la deuda |
|---|---|---|
| **Cascada** | En un único hito final, con las fases previas ya cerradas | Concentra la presión al máximo: lo que se descubre tarde se parcha, porque volver a la fase de diseño es inviable. Y no existe un momento institucional posterior para pagar |
| **Prototipo** | Cuando el prototipo se muestra funcionando | Riesgo característico: el prototipo, construido para velocidad y no para calidad, se convierte en producto y **nace como deuda imprudente e inadvertida** ([pregunta A5](#a5-modelo-de-prototipo-qué-valida-y-qué-riesgo-aparece-si-el-prototipo-se-convierte-en-el-producto)) |
| **Incremental** | En cada entrega, pero con menor intensidad | Cada incremento abre una ventana para pagar deuda. Pero **el Diseño Preliminar se hace una sola vez** [P1-CL01, p. 10]: la deuda **arquitectónica** queda fijada al inicio y ningún incremento la corrige |
| **Espiral** | Se anticipa: el riesgo se evalúa **antes** de comprometerse | Es el modelo que menos deuda inadvertida genera, porque el análisis de riesgos por vuelta **la vuelve visible antes de contraerla** |

**2) La deuda cambia de cuadrante según el modelo.** Usando a Fowler [P1-CL06, p. 5]:

- Un modelo **iterativo con retrospectiva y backlog** convierte deuda en **deliberada** (queda registrada) y **prudente** (tiene plan y ciclo donde pagarse). Es exactamente lo que hacen las buenas prácticas de control: *registrar con esfuerzo y fecha, tratarla como historias de usuario, pagarla en incrementos pequeños y visibles* [P1-CL06, p. 6].
- Un modelo **secuencial sin vuelta atrás** empuja hacia **imprudente**: no porque el equipo sea peor, sino porque **no hay ningún momento previsto para pagar**. Sin ciclo siguiente, "lo arreglamos después" no tiene un "después" institucionalizado.

**3) La relación es en los dos sentidos.** Esta es la parte que suele faltar y la que completa la respuesta:

- **El ciclo de vida influye sobre la deuda** (los dos puntos anteriores).
- **La deuda acumulada condiciona el ciclo de vida que se puede usar.** Un sistema con deuda alta no tolera iteraciones cortas: si integrar y desplegar duele, si no hay pruebas que avisen cuando algo se rompe, los sprints de dos semanas se vuelven imposibles y el equipo termina forzado a ciclos largos, que a su vez generan más deuda. **Es un lazo de realimentación positiva**, y por eso la deuda no crece de forma lineal. *(inferencia)*

**Cierre sugerido:** ningún modelo elimina la deuda técnica, porque la deuda nace de una decisión de priorización, no de un proceso. Lo que el modelo determina es si esa decisión se toma **a la vista y con plan de pago** —lo que la vuelve una herramienta legítima de gestión— o **a ciegas y sin fecha**, que es cuando se vuelve el costo de no calidad que termina dominando el presupuesto.

### A8. ¿Cómo interactúa la Ley de Parkinson con un plan en cascada?

El punto de contacto es el que quedó establecido en [pregunta D1](#d1-diferenciá-tamaño-esfuerzo-complejidad-y-duración): **Parkinson no ataca el esfuerzo, ataca la duración** — *"el trabajo se expande hasta llenar el tiempo disponible para su realización"* [CL05-P, p. 5]. Y cascada es el modelo que más superficie le ofrece, por cuatro razones.

**1) Cascada estima todo por adelantado, cuando menos se sabe.** Como cada fase debe completarse antes de que empiece la siguiente [P1-CL01, p. 5], el cronograma completo se arma al inicio, con la máxima incertidumbre. Frente a esa incertidumbre, la respuesta racional de cada responsable es **agregar colchón**. Y cada colchón es, por definición de Parkinson, **tiempo disponible que el trabajo va a llenar**. *(inferencia)*

**2) El tiempo que sobra no se recupera.** Esta es la asimetría decisiva. Si una fase se atrasa, el atraso **se propaga** a todas las siguientes porque son secuenciales. Pero si una fase termina antes, el tiempo ganado **no se propaga**: la fase siguiente no puede empezar antes si sus recursos están comprometidos para otra fecha, y sobre todo, **el que terminó antes no lo reporta** — porque reportarlo significa que la próxima vez le darán menos tiempo. *(inferencia)* Los atrasos se acumulan, los adelantos se evaporan.

**3) Las fases largas esconden la expansión.** Una fase de diseño de tres meses no tiene puntos de control intermedios obligatorios. Dentro de ese bloque, la expansión del trabajo es invisible hasta el hito final, momento en el cual ya es tarde para corregir.

**4) La Ley de la trivialidad agrava lo anterior.** *"El tiempo dedicado a un tema es inversamente proporcional a su importancia"* [CL05-P, p. 6]. En una revisión formal de documentos de diseño —el mecanismo de control típico de cascada— se discuten a fondo los detalles opinables y se aprueban rápido las decisiones estructurales, sobre las que pocos se sienten autorizados a opinar. *(inferencia)*

**El contraste que cierra la respuesta.** Los mecanismos ágiles invierten cada uno de estos puntos: el **sprint de 1 a 4 semanas sin tiempo muerto entre uno y otro** [P1-CL02, p. 19] impide que el tiempo se estire; las **tareas de menos de un día** en el Sprint Backlog [P1-CL02, p. 24] hacen visible la expansión casi de inmediato; y el **burndown actualizado a diario** [P1-CL02, p. 28] expone la desviación mientras todavía se puede reaccionar. Desarrollado en [pregunta D8](#d8-parcial1-cómo-abordan-las-técnicas-de-estimación-ágiles-el-impacto-de-la-ley-de-parkinson-frente-a-los-enfoques-predictivos-especialmente-con-requisitos-cambiantes).

**Matiz para no exagerar:** Parkinson no implica que cascada siempre se atrase. Implica que cascada **rara vez se adelanta**, y que su duración tiende a igualar lo planificado sea cual sea el trabajo real. El síntoma no es el retraso, es que **el plan siempre parece cumplirse justo** — hasta que no. *(inferencia)*

### A9. ¿Cómo cambia el momento y el tipo de pruebas (QC) según el ciclo de vida elegido?

La constante es la definición: **QC detecta defectos, mira el producto y ocurre durante y después del desarrollo** [P1-CL06, pp. 8, 10]. Lo que cambia entre modelos es **cuántas veces ocurre ese "durante y después"** y, en consecuencia, qué tipo de prueba resulta practicable.

| Modelo | Cuándo se prueba | Qué predomina | Consecuencia |
|---|---|---|---|
| **Cascada** | **Una vez**, en la fase de Pruebas, entre Codificación y Operación [P1-CL01, p. 6] | Pruebas de **sistema** y de **aceptación**, en un "big bang" final | La validación llega tardísimo; un error de requisitos se paga como **fallo interno caro** o directamente como **externo** |
| **Prototipo** | Continuamente, pero **informalmente**: el prototipo se evalúa con usuarios [P1-CL01, p. 7] | **Validación** temprana con usuarios; poca verificación formal | Excelente para detectar el error de requisitos; **no cubre** el plano técnico, y el código del prototipo llega sin pruebas |
| **Incremental** | **Una vez por incremento**: cada uno tiene su *Codificación y Pruebas* [P1-CL01, p. 10] | Niveles completos por incremento + **pruebas de regresión** crecientes | Aparece un problema nuevo: cada incremento debe verificar que **no rompió lo anterior**, y eso vuelve la automatización casi obligatoria |
| **Espiral** | **Por vuelta**, y la lámina lo enumera explícitamente | *V&V del diseño → Pruebas unitarias → Integración y prueba → Prueba de aceptación* [P1-CL01, p. 12] | Es el único modelo del recorte donde **la V&V aparece dibujada como parte del ciclo**, no como una fase posterior |
| **Scrum** *(marco ágil)* | **Por sprint**, con criterio de cierre explícito | Todo el incremento debe cumplir la **DoD**, y el PO **acepta o rechaza** en la Revisión [P1-CL02, pp. 29, 32] | La aceptación se ejecuta cada 1–4 semanas en lugar de una vez al final |

**Las tres tendencias que conviene enunciar** *(inferencia a partir del cruce de las láminas citadas)*:

1. **A más iteraciones, más peso de la automatización.** Probar todo a mano una vez es caro pero posible; probarlo a mano veinte veces no lo es. Por eso el eje *manual / automatizado* [P1-CL06, p. 13] no es una preferencia técnica sino una **consecuencia del ciclo de vida elegido**. Y de ahí que la **integración continua** sea una práctica de XP y no de cascada [P1-CL02, p. 11].
2. **A más iteraciones, más temprana la validación.** En cascada la validación es un evento terminal; en incremental, espiral y Scrum es **recurrente**. Eso mueve defectos desde la casilla de *fallos externos* hacia la de *fallos internos*, que es donde son baratos ([pregunta E4](#e4-costo-de-calidad-vs-costo-de-no-calidad-fallos-internos-vs-externos)).
3. **A más iteraciones, más importa la regresión.** Es el costo que el modelo iterativo introduce: hay que reverificar lo ya construido. Sin suite automatizada, la regresión se vuelve el cuello de botella y termina alargando los ciclos — o, peor, se omite y se convierte en deuda.

**El cierre que une los tres temas:** el ciclo de vida no cambia *qué es* el control de calidad, pero sí **cuánto cuesta ejercerlo**. Modelos iterativos exigen más infraestructura de pruebas por adelantado —costo de calidad, en el sentido de [pregunta E4](#e4-costo-de-calidad-vs-costo-de-no-calidad-fallos-internos-vs-externos)— y a cambio reducen fuertemente el costo de no calidad. Cascada invierte poco en esa infraestructura y paga la diferencia al final, en una sola cuota.

## B. Metodologías

### B7. Metodología estructurada (SSADM) vs orientada a objetos: ventajas, desventajas y cuándo cada una

**Estructurada** [P1-CL02, p. 2]

- **Definición**: "Metodología que divide el desarrollo en **fases secuenciales y bien definidas**, como análisis, diseño, implementación y pruebas."
- **Ventajas**: "Proporciona un **marco claro y estructurado**, facilita la **gestión de proyectos grandes** y la **estimación de tiempos y costos**."
- **Desventajas**: "**Poca flexibilidad para cambios** durante el desarrollo y puede no ser adecuada para proyectos con **requisitos no bien definidos desde el inicio**."

**SSADM** — *Structured Systems Analysis and Design Method* [P1-CL02, p. 3]. El diagrama muestra la cadena completa y merece describirse, porque es puramente gráfico:

```
Planificación Estratégica
   │
   ├─► ┌──────────────── SSADM ────────────────┐
   │   │ Estudio de Viabilidad                 │
   │   │ ┌── Estudio completo ──────────────┐  │
   │   │ │ Análisis de Requisitos           │  │
   │   │ │ Especificación de Requisitos     │  │
   │   │ │ Especificación Lógica del Sistema│  │
   │   │ └──────────────────────────────────┘  │
   │   │ Diseño Físico  ── Desarrollo ──       │
   │   └───────────────────────────────────────┘
   │        │ Construcción y Pruebas
   │        ▼
   │     Producción
   │
   └─► ┌── Administración y Control (transversal a todo) ──┐
```

Tres cosas del dibujo: (1) SSADM **no cubre todo el proyecto** — la Planificación Estratégica queda antes y la Producción después; (2) separa con claridad la **especificación lógica** del **diseño físico**, es decir, el *qué* del *cómo técnico*, que es el aporte conceptual de la escuela estructurada; (3) hay una banda de **Administración y Control** que atraviesa todas las etapas de punta a punta.

**Orientada a objetos** [P1-CL02, p. 4]

- **Definición**: "Se basa en el concepto de **'objetos'** que representan **entidades del mundo real con atributos y comportamientos**, facilitando la **reutilización y modularidad** del código."
- **Ventajas**: "Promueve la **reutilización de código**, facilita el **mantenimiento y la escalabilidad**, y **mejora la gestión de la complejidad**."
- **Desventajas**: "Puede ser **más compleja de aprender y aplicar**, y **requiere una buena planificación y diseño** para aprovechar sus beneficios."

**La comparación**

| | **Estructurada / SSADM** | **Orientada a objetos** |
|---|---|---|
| **Unidad de descomposición** | La **función / el proceso**: el sistema se parte por lo que hace | El **objeto**: el sistema se parte por las entidades del mundo real |
| **Fortaleza declarada** | Marco claro; **gestión de proyectos grandes**; **estimación de tiempos y costos** | **Reutilización**, mantenimiento, escalabilidad, gestión de la complejidad |
| **Debilidad declarada** | **Poca flexibilidad ante el cambio**; requiere requisitos definidos desde el inicio | **Curva de aprendizaje**; exige buena planificación y diseño previos |
| **Cuándo** | Requisitos estables y bien comprendidos; proyecto grande donde importa el control formal y la previsibilidad de costos | Dominio complejo que se espera **evolucione**; se busca reutilizar y mantener a largo plazo; equipo con experiencia en el paradigma |

**El punto no obvio.** Las dos desventajas **no son del mismo tipo**, y decirlo da profundidad a la respuesta: la de la estructurada es **estructural e insalvable** —la rigidez viene de la secuencialidad misma, no se puede entrenar para eliminarla—, mientras que la de OO es **de capacidad y de inversión inicial**: se resuelve con experiencia y con tiempo de diseño. Por eso la OO se combina bien con criterios de selección donde el equipo tiene experiencia ([pregunta B1](#b1-qué-tres-criterios-de-selección-de-metodología-plantea-la-cátedra-y-hacia-dónde-inclina-cada-uno)). *(inferencia)*

**Y el gancho hacia RUP:** la orientación a objetos es el paradigma; **RUP es el proceso que la industrializa**, con UML como notación, casos de uso como eje y las cuatro fases como estructura ([pregunta B2](#b2-rup-definición-sus-cuatro-fases-y-su-notación-estándar)). Esa cadena —Jacobson ([pregunta A1](#a1-definiciones-de-ingeniería-de-software-de-sommerville-pressman-y-jacobson-qué-enfatiza-cada-una-y-en-qué-se-diferencian)) → OO → RUP → PCU ([pregunta D4](#d4-puntos-de-caso-de-uso-definición-proceso-qué-se-pondera-y-ventajas))— atraviesa tres temas del parcial y es la que desarrolla [pregunta A12](#a12-jacobson-pone-los-casos-de-uso-en-el-centro-conectalo-con-ruporientación-a-objetos-y-con-puntos-de-caso-de-uso).

### B8. DoR vs DoD: qué evalúa cada una, quién participa y qué falla si no existen

**Definition of Ready (DoR)** — "definición de **listo**" [P1-CL02, p. 31]

- "Sirve para **evaluar el trabajo antes de que el equipo comience a desarrollarlo**."
- "Define una tarea, historia de usuario o punto de historia, y permite **actuar de inmediato** si se trabaja con Scrum."
- Evalúa: **a qué clientes se dirige** (motivaciones, problemas y necesidades); **las tareas requeridas** (si aportan valor para el negocio y el usuario, y si son claras y factibles); **los requisitos técnicos** (recursos disponibles, enfoque o solución técnica y **capacidad de prueba**); **las estimaciones de tiempo** (plazos y acuerdo con los interesados).

**Definition of Done (DoD)** — "definición de **terminado**" [P1-CL02, p. 32]

- "**Conjunto de criterios** que definen **cuándo un incremento de producto se considera completo y listo para su entrega** a los clientes."
- "**Entendimiento común** entre todos los miembros del equipo."
- "Tener criterios claros ayuda a **enfocarse en la entrega de valor** en cada sprint y a **minimizar retrabajos**."
- "**Toda la organización participa en la creación de la DoD**, incluidos desarrolladores, testers, product owners y demás interesados."
- "Se garantiza que todos utilicen **la misma guía y checklist** antes de marcar una tarea como finalizada."

**La comparación**

| | **DoR** | **DoD** |
|---|---|---|
| **Momento** | **Antes** de empezar (puerta de entrada al sprint) | **Al terminar** (puerta de salida del incremento) |
| **Objeto** | Una **historia o ítem** del backlog | El **incremento de producto** |
| **Pregunta** | ¿Está lo bastante clara como para empezar? | ¿Está lo bastante completa como para entregarse? |
| **Quién** | Se negocia entre PO y equipo, típicamente en Planificación o Refinamiento | **Toda la organización** participa en crearla — el texto es explícito |
| **Ceremonia** | **Planificación** y **Refinamiento del Backlog** | **Revisión**, donde el PO acepta o rechaza |

**Qué falla si no existen** *(inferencia; la lámina enuncia los beneficios, no los fracasos)*:

**Sin DoR**, el equipo se compromete en la Planificación con historias que todavía no entiende. Durante el sprint aparecen las preguntas que debieron responderse antes, el ítem se bloquea esperando al PO, y el sprint termina con trabajo a medias. La DoR existe precisamente porque el Sprint Backlog es un **compromiso** [P1-CL02, p. 24]: no se puede comprometer lo que no se comprende. Notar que la DoR pide explícitamente **capacidad de prueba**, o sea que si no se sabe cómo se va a verificar la historia, la historia no está lista — calidad entrando por la puerta de entrada.

**Sin DoD**, "terminado" significa cosas distintas para cada persona: para el desarrollador, que el código compila; para el tester, que pasó las pruebas; para el PO, que está en producción. El resultado son incrementos que se declaran terminados y vuelven — exactamente el **retrabajo** que la lámina dice que la DoD minimiza. Y sin criterio común, el **burndown miente**: bajar tareas que en realidad no están terminadas produce el patrón clásico de la curva que cae limpio durante todo el sprint y se estanca en el último día.

**El punto que integra:** la DoD es el lugar donde **el aseguramiento de calidad se vuelve operativo dentro de Scrum**. Es un checklist acordado por toda la organización que define el estándar mínimo del proceso — o sea, **QA** ([pregunta E2](#e2--qc-vs-qa-enfoque-objetivo-momento-responsabilidad-y-resultado)), no QC — aplicado antes de que nada pueda declararse hecho. Que la lámina insista en que *toda la organización participa en su creación* es coherente con que la responsabilidad de QA sea de toda la organización. Y también es el mecanismo que **impide acumular deuda técnica en silencio**: si la DoD incluye pruebas y revisión, no se puede entregar sin ellas. *(inferencia)*

### B9. Lean: ¿qué es el desperdicio en software y cómo lo atacan Kanban y el MVP?

**Lean** [P1-CL02, p. 14]

- **Definición**: "Metodología que busca **maximizar el valor para el cliente** y **minimizar el desperdicio** a través de la **mejora continua** y la eficiencia en los procesos."
- **Principios**: "**Identificación y eliminación del desperdicio**, **creación de flujo continuo**, y **mejora continua mediante ciclos de retroalimentación**."
- **Aplicación en software**: "Se enfoca en **entregar valor rápidamente**, **reducir tiempos de espera** y **evitar tareas que no aporten directamente al objetivo** del proyecto."

**Qué es el desperdicio.** La definición operativa sale de la propia lámina: **todo aquello que no aporta directamente al objetivo**. Y la aplicación en software nombra dos formas concretas: los **tiempos de espera** y las **tareas sin aporte**. *(la taxonomía que sigue es inferencia sobre esa base; la cátedra no enumera los siete desperdicios)*

Las formas más caras en software:

- **Funcionalidad no usada.** Se construye algo que nadie pidió o que nadie usa. Es el desperdicio más caro porque además hay que **mantenerlo para siempre**.
- **Trabajo en progreso acumulado.** Código escrito pero no integrado, no probado o no desplegado. Consumió esfuerzo y no entrega nada hasta que termina.
- **Esperas.** Aguardar una aprobación, un ambiente, una respuesta del cliente, el turno del tester.
- **Retrabajo.** Rehacer lo que se hizo mal — es el costo de no calidad de [pregunta E4](#e4-costo-de-calidad-vs-costo-de-no-calidad-fallos-internos-vs-externos) mirado desde Lean.
- **Cambios de contexto.** El costo de tener cinco tareas a medias en lugar de una terminada.

**Cómo lo ataca Kanban.** Directamente y sobre los principios: **visualizar el trabajo** hace visible el desperdicio (una tarjeta parada tres días en "en revisión" es tiempo de espera que nadie habría notado); **limitar el WIP** ataca el inventario y los cambios de contexto; **gestionar el flujo** ataca las esperas identificando **cuellos de botella**; y la **mejora continua** cierra el ciclo [P1-CL02, p. 16].

La correspondencia con los principios Lean es casi uno a uno, y conviene decirlo: **"crear flujo continuo"** (Lean) es literalmente **"gestión del flujo"** (Kanban), y **"eliminar desperdicio"** se implementa como **límite de WIP**. Kanban es la operacionalización de Lean en el tablero. *(inferencia)*

**Cómo lo ataca el MVP.** Sobre el desperdicio más caro de todos, el de **construir lo que nadie necesita**. Un MVP es "un producto con las **características mínimas necesarias para probar una hipótesis**" [P1-CL04, p. 5]: todo lo que exceda ese mínimo es, por definición Lean, **desperdicio potencial**, porque se construyó antes de saber si hacía falta.

Y la lámina de *Construir* lo dice con vocabulario Lean explícito: *"diseñar experimentos rápidos; **minimizar desperdicio y tiempo de ciclo**"* [P1-CL04, p. 4]. **"Tiempo de ciclo"** es terminología Lean pura, y es la misma idea que la meta del bucle BML —acortar la vuelta al mínimo— y que el límite de WIP de Kanban.

**El cierre que integra los tres:** Lean, Kanban y Lean Startup atacan **el mismo desperdicio en tres escalas distintas**. Kanban reduce el inventario **dentro del sprint** (tareas a medias); el MVP reduce el inventario **dentro del producto** (funcionalidad no validada); y Lean da el principio común: **nada que no aporte valor debe existir, y nada empezado debe quedarse quieto**. Notar que Eric Ries eligió el nombre *Lean* Startup precisamente por esa filiación. *(inferencia)*

## C. Productos digitales

### C7. Los nueve bloques del Business Model Canvas y las dependencias entre ellos

**Qué es.** "Herramienta **visual** para **diseñar modelos de negocio**. Creado por **Alexander Osterwalder en 2008**. Permite entender y analizar los **componentes clave de un negocio**." [P1-CL04, p. 22]

**Los nueve bloques** [P1-CL04, pp. 23–31], con los ejemplos recurrentes de la cátedra (app de turnos médicos / vasos reutilizables en el campus):

| # | Bloque | Qué describe | Herramientas y tipos que da la lámina |
|---|---|---|---|
| **1** | **Segmentos de Clientes** | Los **grupos específicos** de personas o empresas que se quieren atender; sus necesidades, comportamientos y características demográficas | Encuestas, entrevistas, análisis de datos |
| **2** | **Propuesta de Valor** | Cómo el producto **resuelve problemas o satisface necesidades**; algo **único o mejor que la competencia** | Benchmarking, desarrollo de prototipos |
| **3** | **Canales** | Cómo se **entrega la propuesta de valor** a los clientes | **Directos** (ventas propias) e **indirectos** (distribuidores, socios) |
| **4** | **Relaciones con Clientes** | Cómo se **interactúa durante el ciclo de vida** del producto | Autoservicio, asistencia personalizada, comunidades de usuarios |
| **5** | **Fuentes de Ingresos** | Cómo se **genera ingreso por cada segmento** | Venta, **suscripciones**, licencias, publicidad (Netflix, Google Ads) |
| **6** | **Recursos Clave** | **Activos esenciales** para funcionar | Infraestructura, talento humano, tecnología |
| **7** | **Actividades Clave** | **Procesos esenciales** para el éxito | Producción, distribución, desarrollo de productos |
| **8** | **Socios Clave** | **Alianzas estratégicas** necesarias | Proveedores, socios tecnológicos, colaboraciones comerciales |
| **9** | **Estructura de Costos** | Gastos ligados a **actividades y recursos clave** | Costos **fijos, variables** y **economías de escala** |

**Las dependencias.** El Canvas no es una lista de nueve casillas independientes: tiene una estructura de **dos mitades unidas por el centro**. *(la lectura estructural es inferencia; la vista panorámica de los nueve bloques quedó fuera del recorte* [CL04-P, p. 29]*, así que conviene fundarla en el contenido de cada bloque)*

```
   ─── EFICIENCIA ───────────── │ ───────────── VALOR ───
   Socios    │ Actividades      │  Relaciones │
   Clave (8) │ Clave (7)        │  Clientes(4)│ Segmentos
             ├──────────  PROPUESTA DE VALOR (2) ──────── de
             │ Recursos         │  Canales (3)│ Clientes(1)
             │ Clave (6)        │             │
   ──────────┴──────────────────┼─────────────┴───────────
        Estructura de Costos(9) │ Fuentes de Ingresos (5)
```

- **La Propuesta de Valor (2) es el eje**, y su par obligado es el **Segmento de Clientes (1)**: una propuesta de valor solo tiene sentido *para alguien*. Cambiar el segmento obliga a revisar la propuesta, y viceversa. Son los dos bloques que se definen primero.
- **La mitad derecha es el mercado**: segmentos, canales y relaciones describen **cómo se llega y se vincula** con el cliente, y **desembocan en las Fuentes de Ingresos (5)**. Los tres bloques deben ser coherentes entre sí: un segmento B2B corporativo no se atiende con un canal de autoservicio anónimo.
- **La mitad izquierda es la infraestructura**: actividades, recursos y socios describen **qué hace falta para producir y entregar** la propuesta, y **desembocan en la Estructura de Costos (9)**. También encadenados: las **actividades clave determinan qué recursos** hacen falta, y lo que no se puede o no conviene tener propio **se resuelve con socios**.
- **El piso es la ecuación económica**: Ingresos (5) − Costos (9). El modelo cierra o no cierra ahí, y esa es la validación final de todo lo de arriba.

Ejemplo de encadenamiento con el caso de la cátedra: la propuesta *"tomá tu café sin generar basura"* exige la actividad clave **logística de limpieza y redistribución de vasos**, que exige el recurso **stock de vasos con QR durables** y el socio **lavandería industrial**, lo que aparece en costos como **operación del lavado y logística**. Cambiar cualquiera de esos eslabones repercute en los demás. [P1-CL04, pp. 24, 28, 29, 30, 31]

**Puntos clave del cierre** [P1-CL04, p. 32]:

- Cada bloque **se puede profundizar con métricas**: **CAC** (cuánto se gasta para lograr un nuevo cliente), **LTV** (valor total que un cliente aportará durante toda su relación comercial), % de usuarios activos, tasa de devolución de vasos.
- Funciona como base para **talleres**: **validar (o refutar) los supuestos de cada celda con datos reales o entrevistas**.
- Armar **indicadores clave**: reducción de llamadas en la clínica, toneladas de residuos evitadas en el campus.

Esa segunda viñeta es el puente con Lean Startup: **cada celda del Canvas es una hipótesis**, y eso es lo que desarrolla [pregunta C9](#c9-cómo-se-complementan-design-thinking-business-model-canvas-y-lean-startup-en-un-mismo-proyecto).

### C8. Empatizar y Definir: herramientas de cada etapa y qué entregable produce cada una

**Empatizar** [P1-CL04, p. 16]

- "Se **observa y se conversa** con los usuarios para entender sus **motivaciones y problemas reales**."
- "Se profundiza en sus **experiencias cotidianas** para descubrir **necesidades ocultas**."
- "El objetivo es obtener una **visión clara de su contexto y emociones**."

**Herramientas**: **entrevistas**; **observación**, entendida como registrar lo que la gente **A**ctúa, el **E**ntorno, las **I**nteracciones, los **O**bjetos y los **U**suarios; y **mapas de empatía**, que capturan lo que la persona **dice, hace, piensa y siente** tras las entrevistas y observaciones.

**Aplicación** de la cátedra: *shadowing* en recepciones de clínicas y entrevistas con pacientes y personal administrativo, para descubrir frustraciones —colas, llamados que se pierden, retrabajo manual—; y observación en cafeterías del campus registrando cuántos vasos descartables se usan por hora, con encuestas rápidas sobre las barreras para llevar un vaso propio.

**Entregable**: **evidencia cualitativa cruda y organizada** — notas de observación, transcripciones, mapas de empatía. Todavía **no hay conclusión**: hay material. *(inferencia)*

**Definir** [P1-CL04, p. 17]

- "Se **sintetiza toda la información** recopilada para **identificar patrones y problemáticas clave**."
- "Se formula un **reto de diseño** que refleje las **necesidades esenciales** del usuario."
- "Esta definición sirve como **norte para orientar las soluciones posteriores**."

**Entregable**: **el reto de diseño**, una sola frase. Los dos ejemplos de la cátedra son el modelo exacto a imitar:

> *"Pacientes y recepcionistas **necesitan** un modo de reservar, confirmar y reprogramar turnos **que reduzca esperas y llamadas fallidas**, **porque** la experiencia actual les hace perder tiempo y genera **ausentismo del 18 %**."*

> *"Los estudiantes y el personal **desean** consumir bebidas calientes sin generar residuos; **sin embargo**, la falta de incentivos y logística de devolución produce **4000 vasos descartables al día**."*

**La estructura del reto de diseño**, leída de los ejemplos *(inferencia)*: **quién** (pacientes y recepcionistas / estudiantes y personal) + **qué necesita** (reservar y reprogramar sin esperas / consumir sin residuos) + **por qué / con qué evidencia cuantificada** (18 % de ausentismo / 4000 vasos por día). Los tres elementos importan, y el tercero es el que separa un reto de diseño de un deseo genérico: **lleva un número que salió de Empatizar**.

**La diferencia entre las dos etapas, y por qué son dos.** Empatizar es **divergente**: acumula material sin filtrar, con la disciplina de no sacar conclusiones todavía. Definir es **convergente**: descarta casi todo para quedarse con un problema. Separarlas evita el error más común del diseño de producto — **saltar de la primera anécdota a la solución**, tomando un caso aislado como si fuera el patrón. *(inferencia)*

**Y el detalle decisivo: el reto de diseño no nombra la solución.** "Un modo de reservar que reduzca esperas" no dice *app*, ni *chatbot*, ni *kiosco*. Si el reto nombrara la solución, la etapa de Idear no tendría nada que hacer. Ese es el error que más se penaliza: definir el problema como "los usuarios necesitan una app". *(inferencia)*

**El vínculo con el resto:** Definir produce lo que Lean Startup convierte en **hipótesis**, y ambas se anclan en el bloque **Segmentos de Clientes + Propuesta de Valor** del Canvas ([pregunta C7](#c7-los-nueve-bloques-del-business-model-canvas-y-las-dependencias-entre-ellos)). El ausentismo del 18 % es, simultáneamente, el hallazgo de Empatizar, la justificación del reto de diseño y **la métrica base contra la cual se va a medir el MVP**.

### C9. ¿Cómo se complementan Design Thinking, Business Model Canvas y Lean Startup en un mismo proyecto?

El título de la clase ya los presenta juntos: *"Productos digitales con **Design Thinking + Canvas + Lean Startup**"* [P1-CL04, p. 1]. La respuesta no es describir los tres por separado, sino mostrar **qué pregunta responde cada uno y cómo se pasan el trabajo entre sí**. *(el encuadre integrador es inferencia; el material los presenta secuencialmente sin unificarlos explícitamente)*

**Cada uno responde una pregunta distinta:**

| Enfoque | Pregunta | Salida |
|---|---|---|
| **Design Thinking** | ¿Cuál es **el problema que vale la pena resolver**? | Un **reto de diseño** anclado en evidencia de usuarios |
| **Business Model Canvas** | ¿**Cierra como negocio** resolverlo? | Nueve bloques, cada uno con **supuestos explícitos** |
| **Lean Startup** | ¿Es **cierto** lo que supusimos? | **Aprendizaje validado** y la decisión de pivotar o perseverar |

**El flujo, y los puntos exactos de conexión:**

**1) Design Thinking → Canvas.** Empatizar y Definir producen conocimiento del usuario y un reto de diseño ([pregunta C8](#c8-empatizar-y-definir-herramientas-de-cada-etapa-y-qué-entregable-produce-cada-una)); eso alimenta directamente los dos bloques centrales del Canvas: **Segmentos de Clientes (1)** y **Propuesta de Valor (2)**. Se ve en el material mismo: el reto *"reservá, confirmá o reprogramá turnos"* reaparece textualmente como propuesta de valor en el Canvas [P1-CL04, pp. 17, 24].

**2) Canvas → Lean Startup.** El Canvas hace explícito lo que se está suponiendo en cada celda, y la propia lámina lo dice: sirve de base para talleres donde se busca **"validar (o refutar) supuestos de cada celda con datos reales o entrevistas"** [P1-CL04, p. 32]. Ahí está la bisagra: **cada celda del Canvas es una hipótesis**, y una hipótesis es exactamente lo que el paso 1 del ciclo BML necesita para arrancar [P1-CL04, p. 3]. El Canvas no valida nada; **organiza qué hay que validar y en qué orden**.

**3) Lean Startup → los dos anteriores.** El ciclo BML mide y devuelve aprendizaje, y la decisión de **pivotar** consiste en cambiar *la propuesta de valor, el segmento de clientes, el modelo de ingresos o la tecnología* [P1-CL04, p. 12] — es decir, **modificar una celda del Canvas**. Si lo que falla es más profundo —el problema estaba mal planteado— la vuelta es más larga: hay que **volver a Definir, o incluso a Empatizar**.

```
   Design Thinking          Canvas               Lean Startup
   (¿qué problema?)    (¿cierra el negocio?)    (¿es verdad?)

   Empatizar ─► Definir ─► Segmentos + Prop. ─► Hipótesis ─► MVP
        ▲                   de Valor  + 7          │          │
        │                   bloques más            │       Medir
        │                        ▲                 │          │
        │                        │              Aprender ◄────┘
        │                        │                 │
        │                  PIVOTAR (cambia ◄───────┤
        │                   una celda)             │
        └───── el problema estaba mal ◄────────────┘
```

**Las tres razones por las que se necesitan mutuamente** — esta es la parte que da el punto entero:

- **Design Thinking sin Lean Startup** produce soluciones deseables que **nadie compra**. Valida con usuarios en entrevistas y prototipos, pero la entrevista mide lo que la gente **dice**; el experimento mide lo que **hace**. Es la diferencia entre una encuesta favorable y una conversión real.
- **Lean Startup sin Design Thinking** itera rápido **sobre el problema equivocado**. El bucle BML optimiza una solución, pero no cuestiona si el problema estaba bien planteado: se puede llegar velozmente a un óptimo local que a nadie le importa.
- **Canvas sin ninguno de los dos** es un documento de planificación que **parece riguroso y no está verificado**: nueve casillas llenas de afirmaciones plausibles. Su valor no está en completarlo, sino en **señalar qué celda es la más riesgosa** para mandarla a validar primero.

**El principio común.** Los tres comparten la misma estructura: **iterar contra evidencia real en lugar de planificar contra supuestos**. Design Thinking lo llama *iteración*, Lean Startup *ciclo Build-Measure-Learn*, y la cátedra señala el parentesco de ambos con el **PDCA de Deming** [P1-CL04, p. 15]. Cambia la escala —la experiencia del usuario, el modelo de negocio, el producto— pero el mecanismo es el mismo, y es el mismo que aparece en la espiral con el riesgo ([pregunta A3](#a3-describí-el-modelo-en-espiral-en-qué-se-centra-y-por-qué-es-iterativo)) y en PRINCE2 con la justificación continua del negocio ([pregunta B5](#b5-prince2-características-procesos-principales-y-qué-significa-justificación-continua-del-negocio)).

## D. Estimación

### D7. Estimadores no formales: ventaja y desventaja de cada uno

[P1-CL05, pp. 8–9]

| Técnica | En qué consiste | Ventaja | Desventaja |
|---|---|---|---|
| **Juicio experto** | Un experto revisa la información disponible y emite una estimación basada en su conocimiento y experiencia | **Rápido y fácil** de aplicar cuando no hay datos formales o históricos | **Subjetivo** y susceptible a **sesgos personales o de grupo** |
| **Método Delphi / Wideband Delphi** | Se consulta a **varios expertos de manera iterativa y anónima**; cada ronda resume las estimaciones y los expertos **ajustan sus respuestas** según la información recibida | **Reduce la influencia de jerarquías o liderazgos fuertes** (al ser anónimo) y **fomenta la convergencia** de opiniones | **Costoso en tiempo** si se requieren varias rondas; **depende de la selección de expertos** |
| **Analogía con proyectos similares** | Comparar el proyecto con otros previamente realizados, aprovechando la experiencia previa | **Fácil de comprender**; se basa en **ejemplos reales**, no en suposiciones teóricas | *(la lámina no la enuncia)* Requiere que exista un proyecto realmente comparable y registro de lo que costó |
| **T-Shirt Sizing** | Asignar a cada elemento una **talla (XS, S, M, L, XL)** según criterios subjetivos de complejidad, alcance, riesgo | **Muy simple e intuitivo**; bueno para **estimaciones rápidas al inicio** de un proyecto | **Discrepancias grandes** si no se definen adecuadamente los criterios de cada talla |
| **Estimación "a ojo"** (*guesstimate*) | Valor aproximado obtenido rápidamente por experiencia, lógica elemental o información del momento, **sin método estructurado** | **Muy veloz** cuando se necesita un número urgente | **Precisión muy baja**; depende en exceso de la experiencia de quien estima |

**Las tres líneas que ordenan el conjunto** *(inferencia)*:

**1) Todas comparten la misma debilidad de base: la subjetividad.** Se llaman "no formales" precisamente porque no hay un procedimiento de cálculo sobre atributos medibles del producto — a diferencia de PCU, que pondera casos de uso, actores y factores ([pregunta D4](#d4-puntos-de-caso-de-uso-definición-proceso-qué-se-pondera-y-ventajas)). Lo que cambia entre ellas es **cuánto trabajan para mitigar esa subjetividad**.

**2) El eje que las ordena es cuánto invierten en controlar el sesgo:**

```
  guesstimate  <  juicio experto  <  T-shirt  <  analogía  <  Delphi
  ─────────────────────────────────────────────────────────────────►
  más rápido, menos confiable          más lento, menos sesgado
```

- El **guesstimate** no controla nada.
- El **juicio experto** aporta conocimiento, pero de **una sola cabeza**, con sus sesgos.
- El **T-shirt sizing** aporta una **escala común** — el control es que todos usen las mismas categorías, y por eso su desventaja declarada es exactamente que **los criterios de cada talla no estén definidos**.
- La **analogía** ancla en **evidencia real** en vez de opinión, que es su ventaja declarada.
- **Wideband Delphi** es la única que ataca el sesgo **estructuralmente**: anonimato contra la jerarquía, iteración contra el anclaje. Paga ese control con tiempo.

**3) Planning Poker es Delphi comprimido.** Tiene el mismo mecanismo —juicio independiente, revelación simultánea, discusión de las diferencias, nueva ronda hasta consenso [P1-CL05, p. 5]— pero en minutos en lugar de rondas por escrito. No por casualidad, la lámina de Scrum lista **Planning Poker, T-Shirt Sizing y Wideband Delphi** juntas como técnicas de estimación de alto nivel [P1-CL02, p. 26].

**Cuándo son legítimas.** No son un atajo vergonzante: la ventaja del juicio experto está enunciada como *"cuando no se tienen datos formales o históricos"*, y la del T-shirt como *"al inicio de un proyecto"*. En etapas tempranas **no existe la información que un método formal necesita** — no hay casos de uso escritos, ni requisitos estables. Estimar con precisión falsa sobre datos inexistentes es peor que estimar con una talla honesta. La regla es **que el método sea proporcional a la información disponible**, que es lo que desarrolla [pregunta D9](#d9-qué-técnica-de-estimación-usarías-en-cada-momento-del-proyecto-y-por-qué). *(inferencia)*

### D8. [PARCIAL1] ¿Cómo abordan las técnicas de estimación ágiles el impacto de la Ley de Parkinson frente a los enfoques predictivos, especialmente con requisitos cambiantes?

Pregunta 1 del parcial anterior. [PARCIAL1, p. 1] Notar que el enunciado original agrega *"de manera más efectiva **(o no)**"*: **admite explícitamente que la respuesta sea matizada**, y una respuesta que solo elogia lo ágil desaprovecha esa apertura. [N-2026-09-07-parkinson-primer-parcial]

**El mecanismo a explicar primero.** *"El trabajo se expande hasta llenar el tiempo disponible para su realización"* [CL05-P, p. 5]. Parkinson opera sobre la **duración**, no sobre el esfuerzo ([pregunta D1](#d1-diferenciá-tamaño-esfuerzo-complejidad-y-duración)): dado un plazo holgado, el trabajo lo consume igual. Por lo tanto, **toda defensa contra Parkinson consiste en no dejar tiempo disponible sin control**.

**Cómo lo aborda el enfoque predictivo — y por qué se le escapa**

| Práctica predictiva | Por qué Parkinson la vence |
|---|---|
| Estimar todo por adelantado, con la máxima incertidumbre | La respuesta racional al riesgo es **agregar colchón**; cada colchón es tiempo disponible |
| Colchones **ocultos dentro de cada tarea** | Al estar escondidos, no se pueden administrar de forma centralizada: se consumen localmente, siempre |
| Fases largas sin control intermedio | La expansión es **invisible** hasta el hito final |
| Asimetría de reporte | El atraso **se propaga** por ser fases secuenciales; el adelanto **no se reporta**, porque reportarlo significa recibir menos tiempo la próxima vez |

*(el análisis de la asimetría es inferencia)*

**Cómo lo abordan las técnicas ágiles — cuatro mecanismos concretos, cada uno con su cita**

1. **Timebox fijo en lugar de plazo por tarea.** El sprint dura **de una a cuatro semanas**, la duración es **fija para todos** y los sprints **se ejecutan uno tras otro sin tiempo muerto** entre uno y el siguiente [P1-CL02, p. 19]. Se invierte la relación: en vez de darle tiempo al trabajo, **se le da al tiempo una cantidad de trabajo**. El tiempo deja de ser la variable de ajuste.
2. **Granularidad que impide esconder holgura.** Cada ítem del Sprint Backlog se divide en tareas cuya estimación **no supere un día de esfuerzo** [P1-CL02, p. 24]. Una tarea de un día no tiene lugar donde alojar un colchón; una de tres semanas, sí.
3. **Visibilidad diaria.** El Sprint Backlog **se actualiza diariamente** con el esfuerzo pendiente [P1-CL02, p. 24], la reunión diaria pregunta expresamente por **obstáculos** y dura **menos de quince minutos** [P1-CL02, p. 28], y el **burndown** muestra la desviación mientras todavía hay sprint para reaccionar [P1-CL02, p. 25]. La expansión se vuelve observable casi en el acto.
4. **Estimación relativa en lugar de compromiso horario.** Los Story Points miden **esfuerzo relativo** —complejidad, cantidad de trabajo y riesgo— [P1-CL05, p. 6], y no se convierten a horas ([pregunta D6](#d6-story-points-qué-miden-y-por-qué-no-se-traducen-directamente-a-horas)). Si nadie declaró "esto lleva 40 horas", no hay un reloj de 40 horas que llenar; lo que se observa es **cuántos puntos se completan por sprint**, medido, no prometido. Y **Planning Poker** ataca de paso los sesgos que inflan las estimaciones individuales [P1-CL05, p. 5].

**El papel de los requisitos cambiantes** — es la parte del enunciado que más se olvida:

- En el enfoque predictivo, requisitos cambiantes **multiplican el efecto Parkinson**. Como cambiar es caro, la respuesta es **estimar aún más conservadoramente** — más colchón, más tiempo disponible, más expansión. Y el plan detallado que se elaboró por adelantado queda obsoleto, de modo que el esfuerzo invertido en construirlo fue desperdicio. **La incertidumbre se gestiona con tiempo, y el tiempo es precisamente lo que Parkinson consume.**
- En el enfoque ágil, el requisito cambiante **no obliga a inflar la estimación** porque el compromiso es **de a un sprint**. Lo que cambia se reordena en el Backlog de Producto —**lista dinámica y priorizada** [P1-CL02, p. 23]— y entra en el sprint siguiente, con **refinamiento y reestimación** disponibles [P1-CL02, p. 30]. La incertidumbre se gestiona **acortando el horizonte de compromiso**, no agregando colchón.

**El "(o no)": los límites de la respuesta ágil** *(inferencia)* — mencionarlos es lo que distingue una respuesta de 2 puntos:

- **El timebox puede desplazar el problema hacia la calidad.** Si el alcance del sprint fue demasiado ambicioso, la presión del cierre se descarga en lo que no se ve: se saltean pruebas y revisiones. Ahí Parkinson no se venció, **se cambió por deuda técnica** ([pregunta E3](#e3--deuda-técnica-definición-origen-analogía-financiera-y-los-cuatro-cuadrantes-de-fowler)). La **DoD** existe justamente para cerrar esa puerta ([pregunta B8](#b8-dor-vs-dod-qué-evalúa-cada-una-quién-participa-y-qué-falla-si-no-existen)).
- **La velocidad también se puede inflar.** Si el equipo se acostumbra a estimar generoso, los puntos se agrandan y la velocidad se mantiene estable mientras se entrega menos. Es Parkinson operando sobre la unidad de medida en vez de sobre el reloj.
- **Ágil no elimina Parkinson: lo acota.** Reduce la ventana de expansión de meses a días y la vuelve visible. La ley sigue operando dentro del sprint.
- **Y hay contextos donde lo predictivo es obligatorio**: un contrato a precio fijo, una certificación regulatoria, una fecha externa inamovible. Ahí la mitigación no es el timebox sino **gestionar el colchón de forma centralizada y explícita** en lugar de dejarlo escondido en cada tarea.

**Cierre sugerido:** las técnicas ágiles son más efectivas contra Parkinson no porque estimen mejor, sino porque **cambian qué variable se fija**. Lo predictivo fija el alcance y deja flotar el tiempo — que es justo lo que Parkinson devora. Lo ágil fija el tiempo y deja flotar el alcance, con la condición de que la **DoD** impida que lo que flote sea la calidad.

### D9. ¿Qué técnica de estimación usarías en cada momento del proyecto y por qué?

**El principio ordenador:** la técnica debe ser **proporcional a la información disponible**. Estimar con precisión falsa sobre datos inexistentes no reduce la incertidumbre, la disfraza. *(inferencia; la cátedra sugiere esto al declarar que el T-shirt sizing es "bueno para estimaciones rápidas al inicio" y el juicio experto "cuando no se tienen datos formales o históricos"* [P1-CL05, pp. 8–9]*)*

| Momento | Qué se sabe | Técnica | Por qué |
|---|---|---|---|
| **Idea / Canvas** | Casi nada: un segmento, una propuesta de valor | **T-Shirt Sizing**, **guesstimate**, **analogía** | Solo hace falta separar "esto es S" de "esto es XL" para decidir si vale la pena seguir. La analogía sirve si hubo algo parecido antes |
| **Anteproyecto / propuesta** | Hay alcance grueso y casos de uso identificables | **Juicio experto** y **Wideband Delphi**; **PCU** si los casos de uso están escritos | Hay que dar un número defendible ante terceros. Delphi aporta convergencia sin jerarquía; PCU aporta trazabilidad al alcance y **facilita la comunicación con stakeholders** [P1-CL05, p. 2] |
| **Planificación de release** | Backlog de Producto poblado y priorizado | **Planning Poker** + **Story Points** | Estima quien va a hacer el trabajo; la escala es relativa y no compromete horas |
| **Planificación de sprint** | Historias refinadas, cumpliendo la DoR | **Story Points** en la historia y **descomposición en tareas de menos de un día** | El detalle fino ya no es estimación sino diseño del trabajo [P1-CL02, p. 24] |
| **Tarea individual riesgosa** | Se conoce la tarea pero no su variabilidad | **PERT** (3 puntos) | Explicita el rango y obliga a pensar el escenario pesimista; el **spread** revela si la tarea está mal entendida ([pregunta D3](#d3-pert-qué-es-fórmula-y-cálculo-con-o--4-m--7-p--16)) |
| **Durante el sprint** | Información nueva | **Refinamiento del Backlog**: revisión, unión de HU, **reestimación** | La cátedra lo prevé como ceremonia optativa [P1-CL02, p. 30] |

**Los tres criterios que deciden, si la pregunta pide justificar** *(inferencia)*:

1. **¿Cuánta información hay?** Poca → técnicas relativas y gruesas. Mucha → técnicas que ponderan atributos (PCU).
2. **¿Para quién es la estimación?** Interna y de equipo → Story Points, que no se convierten a horas. Externa —cliente, contrato, comité— → hace falta algo trazable y explicable: PCU, PERT, Delphi documentado.
3. **¿Cuánto cuesta equivocarse?** Bajo → guesstimate. Alto → invertir en controlar el sesgo, aunque tarde más: Delphi, PERT, varias fuentes cruzadas.

**Dos advertencias que conviene agregar** *(inferencia)*:

- **Nunca se convierte una estimación gruesa en una precisa cambiándole el nombre.** Una talla L no se vuelve "6 semanas" porque alguien escriba 6 en una planilla. La precisión aparente es peor que la imprecisión declarada, porque compromete a un número que nadie calculó.
- **Reestimar no es admitir un error.** El alcance vigente excluye el detalle de la descomposición, pero la lógica está en el material: el Refinamiento existe para **reestimar** con información nueva [P1-CL02, p. 30], y el ciclo BML entero consiste en decidir con evidencia y no con el plan previo. Sostener una estimación vieja cuando ya se sabe más es lo contrario de gestionar.

## E. Calidad

### E7. Formato Given-When-Then: estructura, buenas prácticas, y un caso positivo y uno negativo

**Qué es.** "**Plantilla de Behavior-Driven Development** que **conecta requisitos de negocio con pruebas ejecutables**. Favorece **lenguaje comprensible para negocio, QA y desarrollo**." [P1-CL06, p. 18]

**Estructura** [P1-CL06, p. 18]:

| Cláusula | Qué expresa |
|---|---|
| **Given** (contexto) | **Estado previo del sistema y datos iniciales** |
| **When** (acción) | **Evento o disparo** que el usuario o el sistema realiza |
| **Then** (resultado) | **Salida observable o cambio esperado** |

**Buenas prácticas** [P1-CL06, p. 18]:

- **Una sola acción principal por escenario.**
- **Evitar condicionales**: usar **escenarios separados** para ramas positivas y negativas.
- Mantener las frases en **tiempo presente y voz activa** (el sujeto realiza la acción).

**Ejemplo** — regla de negocio: *un turno médico puede cancelarse sin cargo hasta 24 horas antes; dentro de las 24 horas se aplica una penalización*.

**Caso positivo**

```
Escenario: Cancelación sin cargo con más de 24 horas de anticipación
  Given un paciente con un turno confirmado para dentro de 48 horas
  When el paciente cancela el turno
  Then el turno queda cancelado
   And no se registra penalización
   And el horario vuelve a estar disponible para otros pacientes
```

**Caso negativo**

```
Escenario: Cancelación con penalización dentro de las 24 horas
  Given un paciente con un turno confirmado para dentro de 6 horas
  When el paciente cancela el turno
  Then el turno queda cancelado
   And se registra una penalización en la cuenta del paciente
   And el paciente recibe la notificación del cargo aplicado
```

**Por qué están escritos así** — vale explicarlo, porque es donde se evalúa la comprensión:

- **Son dos escenarios, no uno con condicional.** Es la segunda buena práctica: en lugar de *"Then, si faltan menos de 24 horas, se aplica penalización"*, se escriben dos escenarios con un **Given distinto**. La rama de negocio se expresa **en el contexto**, no en el resultado.
- **Una sola acción en el When**: *cancela el turno*. Todo lo demás es contexto o consecuencia.
- **Los Then son observables**: "queda cancelado", "se registra una penalización", "recibe la notificación". Cumple la buena práctica de redacción de casos de prueba: **resultados observables — definir salidas medibles (UI, API response, BD, logs)** [P1-CL06, p. 17].
- **Presente y voz activa**: *el paciente cancela*, no *el turno es cancelado*.
- **El "caso negativo" no es un caso de error**, y conviene aclararlo: es la **rama no feliz de la regla de negocio**, que el sistema maneja correctamente. La penalización es comportamiento esperado, no un fallo.

**Por qué importa el formato.** Su valor está en la primera línea de la definición: **conecta requisitos de negocio con pruebas ejecutables**. Un escenario GWT es simultáneamente (a) un requisito que el PO entiende y puede aprobar, (b) un criterio de aceptación que puede entrar en la **DoD** ([pregunta B8](#b8-dor-vs-dod-qué-evalúa-cada-una-quién-participa-y-qué-falla-si-no-existen)) y (c) una prueba automatizable. Un solo artefacto que sirve a negocio, QA y desarrollo — de ahí lo de *"lenguaje comprensible"* para los tres. *(inferencia)*

Y conecta con la **DoR**, que exige **capacidad de prueba** antes de empezar [P1-CL02, p. 31]: escribir los GWT de una historia **antes** de desarrollarla es la forma más directa de verificar que la historia es testeable. Es la misma inversión de orden que propone **TDD** ([pregunta B12](#b12-parcial1-ciclo-de-tdd-y-cómo-se-relacionan-las-prácticas-de-xp-con-la-planificación-el-aseguramiento-y-el-control-de-la-calidad)), un nivel más arriba. *(inferencia)*

*Alcance:* el **ejemplo y los usos detallados** de Given-When-Then quedaron **fuera del recorte** [CL06-P, pp. 34–35]; lo que entra es **el concepto, la estructura y las buenas prácticas** [P1-CL06, p. 18]. [N-2026-09-07-alcance-primer-parcial]

### E8. Buenas prácticas de control de deuda técnica

**Las tres prácticas** [P1-CL06, p. 6]:

1. **Registrar cada deuda** en un sistema de seguimiento/backlog, **con esfuerzo y fecha estimada**.
2. **Tratarla como historias de usuario** (en enfoques ágiles); **si supera 90 días, marcarla como crítica**.
3. **Fomentar transparencia y comunicación**: pagar la deuda en **incrementos pequeños y visibles** para todo el equipo.

**Qué hace cada una, leída contra los cuadrantes de Fowler** *(inferencia; la cátedra enuncia las prácticas y los cuadrantes por separado)*:

**Registrar con esfuerzo y fecha** convierte deuda **inadvertida en deliberada**. Una deuda que no está anotada no existe para la planificación: nadie la prioriza, nadie la presupuesta, y su costo aparece disperso como "las cosas acá tardan mucho". Y el registro no es solo una nota: pide **esfuerzo estimado y fecha**, o sea, la convierte en **trabajo estimable** en lugar de una queja.

**Tratarla como historia de usuario** la pone a competir por capacidad **en el mismo backlog** que las funcionalidades. Ese es el punto: mientras la deuda viva en una lista aparte de "cosas técnicas pendientes", siempre pierde contra una funcionalidad visible. En el backlog único —recordar que el Backlog de Producto es *lista **única**, pública y dinámica priorizada* [P1-CL02, p. 23]— el PO tiene que decidir explícitamente entre las dos, y esa decisión queda registrada.

**El umbral de los 90 días** introduce un **criterio objetivo de escalamiento**, y es el dato que más se pregunta textual. Su función es impedir la postergación indefinida: sin umbral, cada sprint individual tiene razones para posponer el pago, y la suma de decisiones localmente razonables produce el resultado global peor. El plazo convierte el juicio ("esto ya es grave") en una **regla observable**.

**Pagar en incrementos pequeños y visibles** ataca dos problemas a la vez. Uno técnico: un refactor grande es riesgoso y difícil de revisar, mientras que uno pequeño se integra sin frenar la entrega. Y otro político, que es el decisivo: si el pago es **visible**, el equipo y el negocio ven que la inversión produce resultados, y la próxima vez es más fácil justificarla. La deuda pagada en silencio parece tiempo perdido.

**El patrón común, que es la respuesta de fondo:** las tres prácticas **mueven la deuda hacia el cuadrante prudente + deliberada** [P1-CL06, p. 5]. Registrar la vuelve deliberada; estimarla, priorizarla y ponerle plazo la vuelve prudente. La cátedra **no propone eliminar la deuda técnica** —sería irreal, y además la analogía financiera admite deuda "buena si se gestiona"—: propone **mantenerla siempre en el único cuadrante que es gestionable**.

**Qué falta y conviene mencionar** *(inferencia)*: las tres prácticas son de **QC en sentido amplio** —detectan y administran deuda ya existente—. La prevención es **QA**: estándares de código, revisiones, pruebas automatizadas, DoD exigente. Una respuesta completa señala los dos planos, porque controlar la deuda sin prevenirla es achicar el pasivo mientras se sigue tomando crédito.

### E9. Caja negra vs caja blanca; partición de equivalencia y análisis de valores límite

**Las técnicas** [P1-CL06, p. 14]:

- **Caja negra**: "Basada en **especificaciones sin conocer el código**."
- **Caja blanca**: "Basada en la **estructura del código**."
- **Técnicas híbridas**: "Combinan caja negra y caja blanca."

**La diferencia es qué se usa para diseñar los casos**, no qué se ejecuta. En ambas se corre el software; lo que cambia es la fuente del diseño de la prueba. *(inferencia)*

| | **Caja negra** | **Caja blanca** |
|---|---|---|
| **Fuente del caso** | La **especificación**: entradas, salidas y reglas de negocio | La **estructura del código**: caminos, ramas, condiciones |
| **Qué detecta bien** | Funcionalidad faltante, reglas mal implementadas, comportamiento incorrecto ante entradas previstas | Caminos no ejercitados, ramas muertas, casos límite internos que la especificación no anticipó |
| **Qué se le escapa** | Caminos internos que ninguna entrada obvia alcanza | **Lo que no está escrito**: si falta un requisito entero, no hay código que cubrir |
| **Quién la ejercita** | Puede hacerla alguien ajeno al desarrollo | Requiere acceso y comprensión del código |

**La complementariedad, que es el punto de la pregunta:** son **opuestas en su punto ciego**. La caja blanca puede alcanzar cobertura total del código escrito y **no detectar nunca un requisito omitido**, porque no hay código que ejercitar. La caja negra puede cubrir toda la especificación y **no tocar jamás** una rama de manejo de errores que el código tiene. Por eso la lámina menciona **técnicas híbridas**: no es una elección entre dos escuelas, es cubrir dos huecos distintos. *(inferencia)*

**Generación de casos de prueba efectivos** [P1-CL06, p. 14]: **identificar escenarios clave** y usar técnicas como **partición de equivalencia** y **análisis de valores límite**.

**Partición de equivalencia.** Dividir el dominio de entrada en **clases donde se espera que el sistema se comporte igual**, y probar **un representante de cada clase** en lugar de todos los valores. Si el sistema trata igual a todo número entre 1 y 100, probar 7, 42 y 93 no agrega información sobre probar solo 42. *(conocimiento general; la cátedra nombra la técnica sin definirla)*

**Análisis de valores límite.** Probar **los bordes de cada clase**, no su interior, porque ahí se concentran los errores: confusiones entre `<` y `<=`, off-by-one, desbordamientos. *(conocimiento general)*

**Aplicadas al ejemplo de la cancelación de turnos** de [pregunta E7](#e7-formato-given-when-then-estructura-buenas-prácticas-y-un-caso-positivo-y-uno-negativo) — la regla de las 24 horas:

- **Clases de equivalencia**: (a) más de 24 h → sin cargo; (b) menos de 24 h → con penalización; (c) turno ya pasado → clase inválida.
- **Valores límite**: **24 h exactas** (¿de qué lado cae?), **23:59** y **24:01**. El caso de las 24 horas exactas es justamente el que la especificación suele no aclarar, y el que el desarrollador resuelve con el operador que le pareció.

Notar el orden correcto: **primero partición** para no probar de más, **después valores límite** para no probar de menos en los bordes. Y que las dos son técnicas de **caja negra** —salen de la especificación, no del código—, aunque la caja blanca las complementa asegurando que ningún camino quede sin ejercitar. *(inferencia)*

**Gestión de riesgos** [P1-CL06, p. 14]: la lámina cierra con **priorización según impacto y probabilidad de fallos**. Es el criterio que decide **dónde** aplicar todo lo anterior: no se prueba todo con la misma intensidad, se prueba más donde fallar duele más. Enunciarlo conecta la respuesta con la idea de que la calidad **se gestiona** ([pregunta E1](#e1-qué-busca-la-gestión-de-calidad-por-qué-importa-y-cuáles-son-sus-métricas-explicá-la-calidad-no-sucede-se-gestiona)).

---

# Ciclo 4 — Profundización y cruces

## A. Fundamentos y ciclos de vida

### A10. Pressman define la ingeniería de software como "tecnología en capas" (proceso, métodos y herramientas): mapeá esas capas a QA y QC

**El punto de partida.** Pressman define la disciplina como una **tecnología en capas compuesta de proceso, métodos y herramientas**, cuyo objetivo es producir software de **alta calidad**, a tiempo, dentro del presupuesto y cumpliendo los requisitos [P1-CL01, p. 2]. Y la gestión de calidad se divide en **planificación de calidad, QC y QA** [P1-CL06, p. 7], donde **QA se orienta al proceso y QC al producto** [P1-CL06, p. 10].

**El mapeo** *(la correspondencia es inferencia; las dos láminas no se refieren una a la otra)*:

| Capa de Pressman | Función de calidad | Correspondencia |
|---|---|---|
| **Proceso** | **QA** | Ambos se ocupan de *cómo se trabaja*. QA define **políticas y estándares (ISO/IEC 25010, CMMI)**, hace **auditorías de proceso** y **capacitación** [P1-CL06, p. 9] — eso **es** trabajar sobre la capa de proceso |
| **Métodos** | **QC** en su plano de diseño | Los métodos determinan **cómo se verifica**: revisiones, inspecciones, diseño de casos de prueba con partición de equivalencia y valores límite [P1-CL06, p. 14] |
| **Herramientas** | **QC** en su plano de ejecución | Las herramientas ejecutan y miden: pruebas automatizadas, y el plan de pruebas nombra **Postman, Selenium, JIRA, SonarQube** [P1-CL06, p. 16] |

**Las tres consecuencias que dan profundidad a la respuesta:**

**1) El orden de las capas explica por qué QA precede a QC.** Pressman dice **capas**, no lista: cada nivel se apoya en el anterior. Si el proceso no exige pruebas, ningún método las incorpora; si el método no está definido, la herramienta automatiza una práctica inexistente. Por eso QA es *"desde el inicio y durante todo el ciclo"* mientras QC es *"durante y después"* [P1-CL06, p. 10]: **no es una preferencia metodológica, es la estructura de la tecnología**.

**2) Explica por qué comprar herramientas no mejora la calidad.** Es el error más frecuente de la industria y el más fácil de argumentar con este esquema: instalar SonarQube sin un proceso que obligue a mirar sus reportes, ni un método que defina el umbral aceptable, es agregar la capa superior sobre el vacío. La herramienta **amplifica** el método; no lo reemplaza. Igualmente, un equipo de testing excelente (QC impecable) no compensa un proceso que permite que los requisitos lleguen ambiguos — la ambigüedad es un problema de la capa de proceso, y se ataca con **DoR** ([pregunta B8](#b8-dor-vs-dod-qué-evalúa-cada-una-quién-participa-y-qué-falla-si-no-existen)), que es QA.

**3) Explica la responsabilidad.** QC es del **equipo de testing/inspección**, QA es de **toda la organización** (con el equipo SQA facilitando) [P1-CL06, p. 10]. Coincide exactamente con las capas: los métodos y herramientas los aplica quien ejecuta la actividad, pero **el proceso es una decisión organizacional** — nadie puede cambiar solo el proceso con el que trabaja el resto.

**El cierre.** La definición de Pressman ya contiene la teoría de la calidad de la materia: si la calidad está **en la definición misma** de la ingeniería de software y la disciplina está hecha de capas, entonces la calidad **no puede ser una actividad agregada al final** — tiene que estar en las tres capas a la vez. Es la fundamentación de *"la calidad no sucede, se gestiona"* [P1-CL06, p. 2].

### A11. Incremental vs espiral: ¿"iterativo" e "incremental" son sinónimos? ¿Dónde está la diferencia real?

**No son sinónimos**, y el material permite mostrarlo con precisión porque **RUP se define como "iterativo *e* incremental"** [P1-CL02, p. 5] — la conjunción sería redundante si significaran lo mismo.

**Las dos definiciones**

- **Incremental**: desarrollar en **pequeños incrementos funcionales**, donde **cada incremento es una versión completa del producto**, permitiendo la entrega rápida de funcionalidades esenciales [P1-CL01, p. 9]. El eje es **cuánto producto hay**: se **agrega**.
- **Iterativo**: repetir el ciclo de trabajo sobre lo mismo para **refinarlo**. La espiral lo ejemplifica: *análisis de riesgos → prototipo 1 → prototipo 2 → prototipo 3 → prototipo operativo* [P1-CL01, p. 12] — el mismo objeto, cada vez mejor entendido. El eje es **cuánto se sabe**: se **revisa**.

**En una línea:** *incremental agrega partes nuevas; iterativo mejora lo que ya hay.* Se puede ser uno sin el otro, y por eso RUP necesita nombrar los dos.

**Dónde está la diferencia real: en qué se rehace.** Acá los diagramas son decisivos.

**Incremental** [P1-CL01, p. 10]: *Análisis de Requisitos del Sistema → Análisis de Requisitos Software → **Diseño Preliminar*** se ejecutan **una sola vez** y son **comunes a todos los incrementos**. Recién a partir del **Diseño Detallado** cada incremento tiene lo suyo: *Diseño Detallado → Codificación y Pruebas → Explotación y Mantenimiento*.

**Espiral** [P1-CL01, p. 12]: **cada vuelta vuelve a pasar por el cuadrante de "determinar objetivos, alternativas y restricciones"** y por el de análisis de riesgos. Los requisitos y el marco **se reconsideran en cada giro**, y de hecho la lámina muestra *Plan de requisitos → Plan de desarrollo → Plan de integración y pruebas* como planes que se van refinando.

```
INCREMENTAL                          ESPIRAL (iterativo)
 Requisitos + Diseño Preliminar       ┌─► Objetivos y restricciones
        (una sola vez)                │        ↓
              │                       │   Análisis de riesgos
    ┌─────────┼─────────┐             │        ↓
    ▼         ▼         ▼             │   Desarrollar y verificar
  Incr.1    Incr.2    Incr.n          │        ↓
  (agrega)  (agrega)  (agrega)        └── Planificar la vuelta siguiente
                                           (se revisa TODO otra vez)
```

**La consecuencia práctica, que es la respuesta de fondo:**

- **Incremental reduce el riesgo de construcción, no el de concepción.** Entrega valor temprano y distribuye el riesgo de implementación, pero **si el Diseño Preliminar o los requisitos generales estaban mal, todos los incrementos heredan el error** y ninguno lo corrige. Es un modelo que asume que **el marco es correcto** y solo ejecuta por partes.
- **Iterativo ataca justamente el riesgo de concepción**, porque somete el marco a revisión en cada vuelta. Paga por eso: es más caro de gestionar y más difícil de estimar, porque no se sabe de antemano cuántas vueltas harán falta. *(inferencia)*

**Por qué RUP es las dos cosas.** Sus iteraciones **refinan** (cada fase da varias vueltas por *Requisitos → Análisis → Diseño → Implementación → Prueba e integración* [P1-CL02, p. 7]) y a la vez **acumulan** producto. Y su reparto de esfuerzo muestra el balance: **Elaboración** —donde se resuelve la arquitectura, según la curva del diagrama— se lleva 20 % del esfuerzo y 30 % del tiempo antes de que **Construcción** consuma el 65 % [P1-CL02, pp. 6–7]. Es decir: **itera sobre la concepción primero, incrementa sobre la construcción después**.

**El cierre.** Un proyecto solo incremental entrega rápido pero puede estar construyendo eficientemente lo equivocado. Uno solo iterativo entiende cada vez mejor el problema pero puede no entregar nada. **La combinación es lo que buscan tanto RUP como Scrum**: el sprint itera —revisión y retrospectiva ajustan producto y proceso— mientras cada incremento es *potencialmente deployable* [P1-CL02, p. 19]. *(inferencia)*

### A12. Jacobson pone los casos de uso en el centro: conectalo con RUP/orientación a objetos y con Puntos de Caso de Uso

Esta es la cadena conceptual más larga del parcial: atraviesa **tres temas** y cuatro láminas de distintas clases. *(la conexión completa es inferencia; cada eslabón es textual)*

**Eslabón 1 — La definición.** Jacobson define la ingeniería de software como un conjunto de métodos y técnicas para construir **software complejo**, y destaca la importancia de la **orientación a objetos** y **el uso de casos de uso como parte fundamental del desarrollo** [P1-CL01, p. 3]. Es la única de las tres definiciones que nombra artefactos concretos.

**Eslabón 2 — El paradigma.** La metodología **orientada a objetos** se basa en objetos que **representan entidades del mundo real con atributos y comportamientos**, y su beneficio declarado incluye **mejorar la gestión de la complejidad** [P1-CL02, p. 4] — exactamente el problema que Jacobson había identificado.

**Eslabón 3 — El proceso.** **RUP** es el proceso que industrializa ese paradigma: **iterativo e incremental**, con **UML** como notación estándar [P1-CL02, p. 5]. Y el caso de uso no es un artefacto más dentro de RUP, es **el eje**, lo que se ve en dos diagramas:

- **El modelo 4+1**: Vista Lógica, de Procesos, Física y de Desarrollo, con la **Vista de Casos de Uso en el centro**, articulando a las otras cuatro [P1-CL02, p. 6].
- **La cadena de trazabilidad**: `Caso de Uso —«trace»→ Realización de Análisis —«trace»→ Realización de Diseño —«trace»→ Caso de Prueba`, con trazas adicionales del caso de uso hacia **Pruebas Funcionales** y del diseño hacia **Pruebas Unitarias** [P1-CL02, p. 6].

**Eslabón 4 — La estimación.** **Puntos de Caso de Uso** es un "método de estimación basado en la **complejidad y número de casos de uso**", que pondera cada caso según complejidad para evaluar **tamaño y esfuerzo** [P1-CL05, p. 2], usando las escalas de **Simple (5) / Average (10) / Complex (15)** por cantidad de transacciones y **actores Simple (1) / Average (2) / Complex (3)** [P1-CL05, pp. 3–4].

**Qué muestra la cadena completa**

```
Jacobson        →  el problema es la COMPLEJIDAD
   ↓               y los casos de uso son el instrumento
Orientación      →  cómo se estructura el código (objetos)
a objetos
   ↓
RUP + UML        →  cómo se organiza el proceso alrededor
                    del caso de uso (4+1, trazabilidad)
   ↓
PCU              →  cómo se MIDE el proyecto usando la
                    misma unidad
```

**Las tres conclusiones que hacen valiosa la respuesta:**

**1) El caso de uso es una unidad que sirve simultáneamente para especificar, diseñar, probar y estimar.** Eso es raro y es el punto: la mayoría de los artefactos sirven para una sola de esas cosas. La trazabilidad de RUP muestra las tres primeras; PCU agrega la cuarta. **Un cambio en un caso de uso se propaga de forma rastreable al análisis, al diseño, a las pruebas y a la estimación.**

**2) Por eso PCU "facilita la comunicación entre desarrolladores y stakeholders"** [P1-CL05, p. 2]: estima en una unidad que el negocio ya usa para describir lo que quiere. Es la diferencia con las líneas de código, que solo el equipo técnico entiende y que además nadie puede discutir antes de escribirlas.

**3) Y explica una limitación de PCU que conviene mencionar** *(inferencia)*: PCU **presupone que existen casos de uso escritos**. En un proyecto ágil, donde el backlog está poblado por **historias de usuario** y muchas todavía son **épicas** sin descomponer [P1-CL02, p. 23], el insumo del método no está disponible. Por eso PCU pertenece a la familia de estimación de proyectos con especificación previa, y Story Points + Planning Poker a la familia de estimación con backlog evolutivo. **No compiten: presuponen procesos distintos** ([pregunta D9](#d9-qué-técnica-de-estimación-usarías-en-cada-momento-del-proyecto-y-por-qué)).

**Y la conexión con calidad**, si la pregunta la habilita: la cadena de trazabilidad de RUP **es verificación y validación estructural** ([pregunta E5](#e5-verificación-vs-validación-con-una-técnica-concreta-para-cada-una)). El caso de uso traza hacia **pruebas funcionales** (validación: ¿satisface la necesidad?) y el diseño hacia **pruebas unitarias** (verificación: ¿está bien construido?). RUP dibuja en su modelo lo que la clase de calidad define en abstracto.

## B. Metodologías

### B10. Recorré un sprint completo: qué artefacto entra y sale de cada ceremonia, y qué rol lidera

**El recorrido** [P1-CL02, pp. 19, 23–30]:

| # | Momento | Entra | Sale | Quién lidera |
|---|---|---|---|---|
| 0 | **Antes del sprint** | Necesidades del negocio | **Backlog de Producto** priorizado, con estimaciones de alto nivel | **Dueño de Producto** (prioriza continuamente) |
| 1 | **Planificación**<br>2–8 h | Backlog de Producto | **Backlog de Sprint**: ítems negociados + tareas de **≤ 1 día** | PO explica el *qué*; **el Equipo define el *cómo*** y las tareas |
| 2 | **Ejecución del sprint**<br>1–4 semanas | Backlog de Sprint | Incremento en construcción | **Equipo** (auto-organizado) |
| 3 | **Reunión diaria**<br>< 15 min, todos los días | Backlog de Sprint | Backlog de Sprint actualizado + **Burndown** actualizado + lista de impedimentos | **Scrum Master** facilita y remueve impedimentos |
| 3b | **Refinamiento** *(optativo, durante el sprint)* | Backlog de Producto | Backlog de Producto revisado, HU unidas, **reestimado** | PO + Equipo |
| 4 | **Revisión**<br>1–2 h, último día | **Incremento Potencialmente Deployable** | Funcionalidades **aceptadas o rechazadas**; ideas de mejora de los interesados | **Dueño de Producto** (acepta o rechaza); SM anuncia la próxima |
| 5 | **Retrospectiva**<br>1–3 h, última actividad | **No aplica artefacto** | **Pocas acciones concretas de mejora** para el próximo sprint | **Scrum Master** facilita |
| 6 | **Sprint siguiente** | Sin tiempo muerto entre uno y otro | | |

**Las cinco observaciones que conviene hacer** *(la lectura transversal es inferencia; los datos son textuales)*:

1. **El Backlog de Producto es el único artefacto que sobrevive a todos los sprints.** Es *único, público y dinámico* [P1-CL02, p. 23]: el Backlog de Sprint muere con el sprint, el Incremento se entrega, el Burndown se reinicia. Es la memoria del producto.

2. **La Retrospectiva es la única ceremonia sin artefacto de entrada** — la lámina lo dice expresamente: *"Artefactos Involucrados: No aplica"* [P1-CL02, p. 30]. Tiene sentido: inspecciona **procesos e interacciones**, no producto. Es la diferencia estructural con la Revisión.

3. **El liderazgo rota según lo que se inspecciona.** Producto → **PO** (Planificación y Revisión). Proceso → **Scrum Master** (Diaria y Retrospectiva). Ejecución → **Equipo**. El SM **nunca decide sobre el producto**, y el PO **nunca decide cómo se construye**.

4. **La Revisión es el punto de validación y la Retrospectiva el de mejora del proceso.** En términos de calidad: la Revisión es **QC** —se inspecciona el producto y el PO detecta lo que no cumple— y la Retrospectiva es **QA** —se inspecciona y ajusta el proceso para prevenir— ([pregunta E2](#e2--qc-vs-qa-enfoque-objetivo-momento-responsabilidad-y-resultado)). **Scrum tiene las dos funciones de calidad institucionalizadas en dos ceremonias distintas del mismo sprint.**

5. **El sprint es un PDCA completo.** Planificación = *Plan*, ejecución = *Do*, Revisión = *Check* del producto, Retrospectiva = *Act* sobre el proceso. *(PDCA quedó fuera del recorte como tema propio* [N-2026-09-07-alcance-primer-parcial]*; sirve como observación, no como contenido evaluado.)*

**Dónde se conectan DoR y DoD** ([pregunta B8](#b8-dor-vs-dod-qué-evalúa-cada-una-quién-participa-y-qué-falla-si-no-existen)): la **DoR** es la puerta de entrada a la **Planificación** —un ítem que no la cumple no debería entrar al sprint— y la **DoD** es el criterio con el que se presenta el incremento en la **Revisión**. Ambas rodean el sprint por sus dos extremos.

### B11. Historias de usuario: formato, por qué expresan el "qué" y no el "cómo", y qué es una épica

**Dónde viven.** Son la forma de escribir un ítem del **Backlog de Producto**, que es una *lista única, pública y dinámica priorizada de requerimientos* que **"representa el 'qué' esperado del producto, sin preocuparse por el 'cómo'"** [P1-CL02, p. 23].

**Qué son.** "Forma de escribir un ítem del Backlog de Producto que **se enfoca en la necesidad de los involucrados de entender cómo la funcionalidad se va a usar**. Permite al equipo **entender la perspectiva del usuario antes de elegir una forma de implementarlo**." [P1-CL02, p. 23]

**El formato**

```
Como [un usuario], puedo [una funcionalidad] para [un beneficio].
```

Ejemplo de la cátedra: *"Como usuario no registrado, puedo consultar los precios de los vuelos para calcular el presupuesto de mi viaje."*

**Qué aporta cada parte** *(inferencia sobre el formato dado)*:

| Parte | Qué aporta | Qué falla si falta |
|---|---|---|
| **Como [un usuario]** | El **rol**, que no es lo mismo que "el usuario" genérico — notar que el ejemplo dice *no registrado*, y eso ya define reglas de acceso | Sin rol, no se sabe para quién se optimiza ni qué permisos aplican |
| **puedo [una funcionalidad]** | La **capacidad** que se habilita, en términos del usuario | — |
| **para [un beneficio]** | El **porqué**, que es la parte que más se omite y la más valiosa | Sin beneficio no se puede **priorizar** (el PO no sabe cuánto vale), ni **negociar el alcance**, ni **validar** si la solución sirvió |

**Por qué el "qué" y no el "cómo".** Tres razones, encadenadas:

1. **Porque el Backlog de Producto es del PO y la implementación es del Equipo.** La regla es explícita: *"de ninguna manera el Scrum Master o el Dueño de Producto le explica al equipo cómo transformar el Backlog de Producto en incrementos"* [P1-CL02, p. 22]. Una historia que dice *"agregar un botón azul en el header"* **invade la autonomía del equipo** y además pierde la información de por qué hacía falta.
2. **Porque preserva el espacio de solución.** La lámina lo dice: permite entender la perspectiva del usuario **antes de elegir una forma de implementarlo**. Si la historia ya trae la solución, el equipo no puede proponer una mejor, más barata o más simple — y **Diseño Simple** es una práctica de XP ([pregunta B4](#b4-los-5-valores-y-las-12-prácticas-de-xp-cómo-se-refuerzan-entre-sí)).
3. **Porque el "para" es lo que permite validar.** Con el beneficio explícito se puede medir si la funcionalidad efectivamente lo produjo — es el enganche con las **métricas accionables** de Lean Startup ([pregunta C5](#c5-métricas-accionables-vs-vanidosas-qué-aportan-analytics-logging-y-tracking-de-funnels)) y con los **criterios de aceptación** en Given-When-Then ([pregunta E7](#e7-formato-given-when-then-estructura-buenas-prácticas-y-un-caso-positivo-y-uno-negativo)). *(inferencia)*

**Épica.** "Historia de usuario que **no puede ser entregada tal y como se ha definido dentro de una sola iteración**, o que es **suficientemente grande como para ser partida en historias de usuario más pequeñas**." [P1-CL02, p. 23]

Dos precisiones sobre la definición:

- **El criterio es relativo al sprint, no absoluto.** "Épica" no significa "muy grande" en abstracto: significa **que no entra en una iteración**. La misma historia puede ser épica para un sprint de una semana y no serlo para uno de cuatro. *(inferencia)*
- **Una épica no es un defecto del backlog.** Es normal y esperable que los ítems lejanos del backlog sean épicas: todavía no hace falta el detalle. Lo que hay que evitar es que una épica **entre a la Planificación sin partir** — y ese es justamente uno de los filtros de la **DoR**, que exige tareas *claras y factibles* con estimaciones acordadas [P1-CL02, p. 31]. El **Refinamiento del Backlog**, con su *revisión, ordenamiento, unión de HU y reestimación* [P1-CL02, p. 30], es la ceremonia donde las épicas se descomponen antes de tiempo. *(inferencia)*

**El cierre que conecta con estimación:** que el backlog contenga épicas sin descomponer es exactamente la razón por la que se estima con **Story Points y técnicas relativas** en vez de con PCU ([pregunta A12](#a12-jacobson-pone-los-casos-de-uso-en-el-centro-conectalo-con-ruporientación-a-objetos-y-con-puntos-de-caso-de-uso)): no hay especificación suficiente para ponderar, pero sí la hay para comparar tamaños. Y por eso la **T-Shirt Sizing** aparece entre las técnicas de estimación de alto nivel de Scrum [P1-CL02, p. 26].

### B12. [PARCIAL1] Ciclo de TDD y cómo se relacionan las prácticas de XP con la planificación, el aseguramiento y el control de la calidad

Pregunta 3 del parcial anterior. [PARCIAL1, p. 1] El enunciado nombra **las tres fases del proceso de gestión de calidad** —planificación, QA y QC [P1-CL06, p. 7]—, así que la respuesta debe organizarse alrededor de esas tres, no alrededor de las prácticas.

**TDD primero** [P1-CL02, p. 15]

- **Definición**: "Metodología de desarrollo en la que **las pruebas se escriben antes del código**, guiando el desarrollo y asegurando que el software cumpla con los requisitos especificados."
- **Ciclo, tres etapas**: **escribir una prueba que falle** → **escribir el código mínimo necesario para pasar la prueba** → **refactorizar el código para mejorar su estructura manteniendo las pruebas verdes**.
- **Ventajas**: "Ayuda a **prevenir errores**, facilita el **diseño modular**, **mejora la calidad del código** y proporciona **documentación actualizada del comportamiento esperado**."

Notar que la primera ventaja declarada es **prevenir**, no detectar: eso ya ubica a TDD del lado de **QA**, aunque produzca pruebas, que son instrumento de QC. Es el punto más fino de toda la pregunta. *(inferencia)*

**El mapeo de las 12 prácticas a las tres funciones** [P1-CL02, pp. 11–13] *(la asignación es inferencia; la cátedra lista las prácticas sin clasificarlas)*:

**Planificación de la calidad** — decidir *por adelantado* qué nivel de calidad se va a sostener y reservarle capacidad:

| Práctica | Cómo planifica calidad |
|---|---|
| **Juego de Planificación** | Negocio y equipo acuerdan alcance por entrega; el equipo estima, el cliente prioriza. Es donde se decide **cuánto entra**, y por lo tanto si hay espacio para hacer las cosas bien |
| **Entregas Cortas** | Fija de antemano un ritmo que **obliga** a que el software esté siempre en estado entregable |
| **Semana de 40 Horas** | Planifica capacidad **sostenible**: el cansancio produce defectos y deuda. Es planificación de calidad disfrazada de política laboral |
| **Cliente In-Situ** | Garantiza que el criterio de aceptación esté disponible **cuando se lo necesita**, no tres días después |

**Aseguramiento (QA) — prevenir, actuar sobre el proceso:**

| Práctica | Cómo previene |
|---|---|
| **TDD** | La prueba **antes** del código: el defecto no llega a existir. Además fuerza **diseño modular** — código difícil de testear es código mal acoplado, y TDD lo revela en el momento |
| **Diseño Simple** | Menos complejidad accidental = menos superficie de defecto |
| **Refactoring** | Mantiene la estructura sana de forma continua; es **pago permanente de deuda técnica** ([pregunta E3](#e3--deuda-técnica-definición-origen-analogía-financiera-y-los-cuatro-cuadrantes-de-fowler)) |
| **Estándares de Código** | Es literalmente *"definición de políticas y estándares"*, la actividad que la lámina asigna a QA [P1-CL06, p. 9] |
| **Metáforas** | Vocabulario común: previene el defecto por malentendido entre negocio y técnica |
| **Semana de 40 Horas** | También previene: menos error humano |

**Control (QC) — detectar, actuar sobre el producto:**

| Práctica | Cómo detecta |
|---|---|
| **Pruebas** | Es la actividad de QC por excelencia: *"pruebas (unitarias, integración, sistema)"* [P1-CL06, p. 8] |
| **Pair Programming** | **Revisión de código continua y en vivo** — la lámina de QC lista *"revisiones de código"* como su primera actividad |
| **Integración Continua** | Detecta el defecto de integración en minutos en lugar de semanas |
| **Cliente In-Situ** | **Validación** permanente: el cliente detecta la desviación respecto de la necesidad, no de la especificación ([pregunta E5](#e5-verificación-vs-validación-con-una-técnica-concreta-para-cada-una)) |
| **Propiedad Colectiva** | Más ojos sobre cada parte del código |

**Las tres conclusiones que el enunciado busca** *(inferencia)*:

**1) XP corre las tres funciones en paralelo y de forma continua, no en fases.** En un proceso tradicional la planificación va primero, QA define estándares y QC prueba al final. En XP las tres ocurren **todos los días**: se replanifica por entrega corta, se previene con TDD y refactoring al escribir cada línea, y se controla con pruebas, pairing e integración continua en el momento. Eso es lo que hace que la definición diga que XP **"se enfoca en mejorar la calidad del software"** [P1-CL02, p. 11] — la calidad no es una etapa del proceso, es la forma del proceso.

**2) Varias prácticas cumplen dos funciones a la vez, y eso no es ambigüedad sino el diseño.** El **Pair Programming** detecta defectos (QC) **y** difunde conocimiento y estándares, previniendo los siguientes (QA). El **Cliente In-Situ** valida (QC) **y** evita que el malentendido nazca (QA). **TDD** es QA por intención y QC por producto. El entramado de [pregunta B4](#b4-los-5-valores-y-las-12-prácticas-de-xp-cómo-se-refuerzan-entre-sí) es justamente esta superposición.

**3) La respuesta al "costo de no calidad".** Todas las prácticas de QC de XP tienen el mismo efecto: **acortan el tiempo entre introducir un defecto y detectarlo**. Eso mueve los defectos desde la casilla de **fallos externos** hacia la de **fallos internos**, y dentro de los internos, hacia los más baratos ([pregunta E4](#e4-costo-de-calidad-vs-costo-de-no-calidad-fallos-internos-vs-externos)). XP es una apuesta explícita a **gastar más en costo de calidad para pagar mucho menos de no calidad**, que es exactamente la conclusión de la lámina: *"invertir en calidad reduce significativamente los costos de no calidad"* [P1-CL06, p. 3].

## C. Productos digitales

### C10. CAC y LTV: qué miden y qué bloques del Canvas tensiona cada uno

**Las definiciones de la cátedra** [P1-CL04, p. 32]. La lámina de cierre del Canvas señala que **cada bloque se puede profundizar con métricas** y nombra:

- **CAC**: "cuánto se gasta para **lograr un nuevo cliente**".
- **LTV**: "**valor total que un cliente aportará a la empresa durante toda su relación comercial**".
- Más: **% de usuarios activos**, **tasa de devolución de vasos**.

**Qué miden, y por qué van juntas** *(el análisis siguiente es inferencia; la lámina define ambas sin desarrollar la relación)*:

- **CAC** es un **costo de adquisición**: marketing, ventas, promociones, todo lo que hizo falta para convertir a un desconocido en cliente.
- **LTV** es un **ingreso acumulado a lo largo del tiempo**: cuánto deja ese cliente antes de irse.

La relación entre ambas es el test elemental de viabilidad de un modelo de negocio: **si CAC > LTV, cada cliente nuevo genera pérdida**, y crecer empeora las cosas. Es la trampa clásica de una startup con métricas vanidosas ([pregunta C5](#c5-métricas-accionables-vs-vanidosas-qué-aportan-analytics-logging-y-tracking-de-funnels)): los usuarios acumulados suben, se celebra, y cada uno de esos usuarios cuesta más de lo que deja.

**Qué bloques tensiona cada una**

**CAC vive en la mitad derecha y se paga en la izquierda:**

| Bloque | Cómo lo tensiona el CAC |
|---|---|
| **Canales (3)** | Es el principal determinante: un canal directo con venta consultiva tiene CAC alto; uno de autoservicio digital, bajo |
| **Segmentos de Clientes (1)** | Distintos segmentos cuestan distinto adquirir. El CAC de las clínicas B2B no es el de un paciente individual |
| **Relaciones con Clientes (4)** | Un *onboarding asistido* [P1-CL04, p. 26] captura mejor pero encarece cada alta |
| **Estructura de Costos (9)** | Es donde el CAC aparece contablemente: *marketing B2B y ventas consultivas* [P1-CL04, p. 31] |

**LTV vive en el eje de la retención:**

| Bloque | Cómo lo tensiona el LTV |
|---|---|
| **Fuentes de Ingresos (5)** | El **modelo** decide el perfil: la **suscripción SaaS** [P1-CL04, p. 27] acumula LTV mes a mes; una venta única lo concentra y lo agota |
| **Propuesta de Valor (2)** | Determina cuánto tiempo el cliente sigue pagando: si deja de resolver el problema, se va |
| **Relaciones con Clientes (4)** | Aparece **de nuevo**, ahora del otro lado: retención, comunidad, fidelización. Es el bloque que ambas métricas tocan |
| **Actividades y Recursos Clave (7, 6)** | Sostener el valor cuesta: *soporte a clínicas, monitoreo de uptime* [P1-CL04, p. 29] |

**La tensión central, que es lo que la pregunta busca:** **Relaciones con Clientes (4) es el bloque donde CAC y LTV chocan.** Invertir ahí sube el CAC —cuesta más cada alta— y a la vez sube el LTV —el cliente se queda más—. Decidir cuánto invertir en ese bloque **es** decidir el balance entre ambas métricas, y no hay respuesta correcta en abstracto: depende del modelo de ingresos. En suscripción, invertir en retención casi siempre paga; en venta única, casi nunca.

**El vínculo con Lean Startup**, que cierra la respuesta: Eric Ries pide **hipótesis de valor y de crecimiento** antes de codificar [P1-CL04, p. 4]. **LTV es la métrica de la hipótesis de valor** —¿el producto entrega suficiente para que el cliente se quede y pague?— y **CAC es la de la hipótesis de crecimiento** —¿se puede conseguir clientes a un costo sostenible?—. Y los dos primeros ejes de **pivot** —propuesta de valor y segmento de clientes [P1-CL04, p. 12]— son exactamente los bloques que se cambian cuando esa relación no cierra.

### C11. Diseñá un experimento completo para la app de turnos médicos: hipótesis, MVP, métrica y criterio de decisión

Se usan los cinco componentes de un A/B test [P1-CL04, p. 9] y el ciclo BML [P1-CL04, p. 3], aplicados al caso de la cátedra. *(el experimento es de elaboración propia sobre los datos que da el material)*

**Contexto — de dónde sale la hipótesis.** Design Thinking ya produjo el reto de diseño: *"Pacientes y recepcionistas necesitan un modo de reservar, confirmar y reprogramar turnos que reduzca esperas y llamadas fallidas, porque la experiencia actual les hace perder tiempo y genera **ausentismo del 18 %**"* [P1-CL04, p. 17]. Y entre las ideas surgidas en Idear estaban los **recordatorios vía WhatsApp**, la cola virtual y los kioscos de auto-check-in [P1-CL04, p. 18].

**1) Hipótesis** — *definir el cambio y su objetivo*:

> Enviar un **recordatorio automático por WhatsApp 24 horas antes del turno, con opción de confirmar o reprogramar en un toque**, reducirá el **ausentismo** del 18 % a **12 % o menos**, porque una parte de las ausencias no proviene de desinterés sino de **olvido y de la fricción de llamar para reprogramar**.

Cumple lo que pide la lámina: dice **qué se cambia** y **qué se espera mejorar y por qué** [P1-CL04, p. 9]. Y es una **hipótesis de valor** en el sentido de [pregunta C10](#c10-cac-y-ltv-qué-miden-y-qué-bloques-del-canvas-tensiona-cada-uno).

**2) MVP** — *lo mínimo necesario para probar la hipótesis* [P1-CL04, p. 5]:

No hace falta construir el módulo de mensajería integrado al sistema de turnos, ni el flujo completo de reprogramación. Alcanza con: **un envío programado desde una cuenta de WhatsApp Business, alimentado por una exportación diaria de la agenda, con un link a un formulario simple de confirmar/reprogramar**. Incluso podría operarse **manualmente** las primeras semanas.

Ese es el criterio de Dropbox aplicado ([pregunta C2](#c2-qué-es-un-mvp-y-por-qué-el-video-de-dropbox-califica-como-tal)): la hipótesis riesgosa es **de comportamiento** (¿la gente responde al recordatorio y reprograma?), **no técnica** (nadie duda de que se puede enviar un mensaje). Construir la integración completa antes de saberlo sería el desperdicio que Lean busca evitar ([pregunta B9](#b9-lean-qué-es-el-desperdicio-en-software-y-cómo-lo-atacan-kanban-y-el-mvp)).

**3) Población y variantes** [P1-CL04, p. 9]:

- **Población**: todos los turnos agendados en las dos clínicas del piloto durante 4 semanas, asignados aleatoriamente.
- **Variante A (control)**: el proceso actual, sin recordatorio.
- **Variante B (experimental)**: recordatorio por WhatsApp 24 h antes con confirmar/reprogramar.
- **Una sola variable de cambio**, como pide la buena práctica: **no** se cambia además el horario de envío, ni el canal, ni el texto. Si se quisieran probar dos textos, sería un experimento posterior.

**4) Métricas** — accionables y comparables ([pregunta C5](#c5-métricas-accionables-vs-vanidosas-qué-aportan-analytics-logging-y-tracking-de-funnels)):

| Tipo | Métrica |
|---|---|
| **Primaria** | **Tasa de ausentismo** (turnos no asistidos / turnos agendados), A vs B |
| **Secundarias** | Tasa de reprogramación anticipada; **llamadas entrantes a recepción** (el material midió una reducción del 42 % en el piloto [P1-CL04, p. 21]); tasa de respuesta al mensaje |
| **De contrapeso** | Quejas o bajas por considerar el mensaje invasivo, y **ocupación efectiva de agenda** — porque reprogramar mucho podría bajar el ausentismo sin mejorar la ocupación, que es lo que en realidad importa a la clínica |

La métrica de contrapeso es la que suele faltar y la que más valor agrega: evita **ganar la métrica y perder el objetivo**.

**5) Criterio de decisión** — *"conclusión y acción"* [P1-CL04, p. 9] y *"pivotar o perseverar"* [P1-CL04, p. 12]:

| Resultado | Decisión |
|---|---|
| Ausentismo de B **≤ 12 %** y diferencia **estadísticamente significativa**, sin deterioro en las de contrapeso | **Perseverar**: adoptar la variante B e invertir en la integración real |
| Mejora existe pero **menor a la esperada** (p. ej. 15 %) | **Perseverar iterando**: el canal funciona; el próximo experimento cambia una sola variable (momento del envío, o el texto) |
| **Sin diferencia significativa** | **Aprendizaje validado negativo**: el olvido no era la causa. Volver a **Definir**: reabrir la investigación de por qué faltan los pacientes |
| Mejora el ausentismo pero **empeora la ocupación** o aparecen quejas | Rediseñar la solución, no el canal |

**Dos condiciones de validez** que hay que enunciar [P1-CL04, p. 10]: **las métricas se definen antes de empezar** —si se eligen después, siempre hay alguna en la que B ganó— y **la prueba se mantiene el tiempo suficiente** para tener significancia estadística: cuatro semanas, no cuatro días, porque el ausentismo tiene estacionalidad semanal y el volumen de turnos por día es bajo.

**Y el cierre del ciclo**: documentar hallazgos y **actualizar el backlog / hoja de ruta** [P1-CL04, p. 12]. Si el experimento sale bien, la integración real entra como historia priorizada; si sale mal, lo que entra es una nueva ronda de investigación.

### C12. [PARCIAL1] ¿Cómo se conectan las técnicas de estimación informales con el Business Model Canvas en etapas iniciales de un proyecto?

Pregunta 4 del parcial anterior. [PARCIAL1, p. 1] Cruza dos temas que el material nunca vincula, así que la respuesta debe construir el puente explícitamente. La clave está en **qué información hay disponible en una etapa inicial**. *(el vínculo es inferencia; cada componente es textual)*

**1) El punto de encuentro: ambos operan con incertidumbre alta y buscan decidir, no precisar.**

El Canvas es una **herramienta visual para diseñar modelos de negocio** que sirve de base para **talleres donde se validan o refutan los supuestos de cada celda** [P1-CL04, pp. 22, 32]: en ese momento **no hay requisitos escritos, ni casos de uso, ni backlog**. Y las técnicas informales están declaradas exactamente para ese contexto: el juicio experto es útil *"cuando no se tienen datos formales o históricos"*, y el T-Shirt Sizing es *"bueno para estimaciones rápidas **al inicio de un proyecto**"* [P1-CL05, pp. 8–9].

Ninguna técnica formal es aplicable ahí: **PCU necesita casos de uso escritos** [P1-CL05, p. 2] y **Story Points necesitan un backlog con historias** [P1-CL05, p. 6]. En la etapa del Canvas ninguno de los dos insumos existe.

**2) Qué se estima exactamente: los bloques del Canvas, no funcionalidades.**

Esto es lo que hace específica a la respuesta. Las celdas que **consumen recursos** son estimables de forma gruesa:

| Bloque | Qué se estima informalmente | Técnica natural |
|---|---|---|
| **Actividades Clave (7)** | El tamaño del esfuerzo de construcción: *"desarrollo y mantenimiento del software"*, *"logística de limpieza y redistribución"* [P1-CL04, p. 29] | **T-Shirt Sizing** por actividad |
| **Recursos Clave (6)** | Equipo, plataforma cloud, stock de vasos [P1-CL04, p. 28] | **Analogía** con proyectos similares |
| **Estructura de Costos (9)** | El agregado: *infraestructura cloud, sueldos del equipo tech, operación del lavado* [P1-CL04, p. 31] | **Juicio experto** o **Wideband Delphi** |
| **Canales (3)** | Cuánto cuesta construir cada canal: app móvil, portal web, **kioscos de auto-check-in** [P1-CL04, p. 25] | **T-Shirt Sizing** comparativo entre canales |

**3) Para qué sirve la estimación ahí: para decidir la viabilidad, no el cronograma.**

El Canvas cierra con la ecuación **Ingresos (5) − Costos (9)** ([pregunta C7](#c7-los-nueve-bloques-del-business-model-canvas-y-las-dependencias-entre-ellos)), y esa resta **necesita un número del lado de los costos**. La estimación informal es lo que permite completarla. Pero la pregunta que responde no es *"¿cuándo estará?"* sino **"¿este modelo puede cerrar?"** y **"¿cuál de estas alternativas es viable?"**.

Ahí la imprecisión es tolerable: para decidir entre construir una app nativa (talla L) y un formulario web (talla S), no hace falta saber si L son 14 o 19 semanas. **Basta el orden de magnitud**, que es exactamente lo que el T-shirt sizing entrega.

**4) La retroalimentación, que es el punto que completa la respuesta.**

La conexión funciona **en los dos sentidos**:

- **Del Canvas hacia la estimación**: el Canvas provee el alcance grueso a estimar. Sin él no se sabe **qué** hay que construir.
- **De la estimación hacia el Canvas**: un bloque que resulta **XL** obliga a **rediseñar la celda**. Si la logística de lavado de vasos sale XL, la respuesta no es aceptar el costo sino cambiar el modelo: tercerizar en un **socio clave (8)** —la *lavandería industrial* que el propio material lista [P1-CL04, p. 30]— o reducir el alcance de la propuesta de valor. **La estimación no solo informa el Canvas: lo modifica.**

**5) Y el enganche con Lean Startup**, que es lo que hace que todo esto no sea planificación tradicional:

La estimación informal también sirve para **priorizar qué hipótesis validar primero**. Combinando dos cosas que el material da por separado — *"validar o refutar los supuestos de cada celda"* [P1-CL04, p. 32] y la **gestión de riesgos** como *priorización según impacto y probabilidad* [P1-CL06, p. 14] — el criterio es: **validar primero la celda más cara y más incierta**. Si el bloque más caro descansa sobre el supuesto menos verificado, ahí va el primer MVP.

**6) El límite que hay que declarar.**

Una estimación informal **no debe convertirse en compromiso**. Su desventaja está enunciada: el juicio experto es *"subjetivo y susceptible a sesgos"*, el T-shirt produce *"discrepancias grandes si no se definen adecuadamente los criterios"*, y el guesstimate tiene *"precisión muy baja"* [P1-CL05, pp. 8–9]. El riesgo real y frecuente es que **la talla L del taller de Canvas se convierta en "seis meses" en el contrato**, sin que nadie haya agregado información nueva en el medio. Y ahí entra la **Ley de Parkinson**: una fecha nacida de una talla se vuelve tiempo disponible que el trabajo llenará igual ([pregunta D8](#d8-parcial1-cómo-abordan-las-técnicas-de-estimación-ágiles-el-impacto-de-la-ley-de-parkinson-frente-a-los-enfoques-predictivos-especialmente-con-requisitos-cambiantes)).

**Cierre sugerido:** Canvas y estimación informal se conectan porque comparten el mismo estatuto epistémico — **son herramientas para decidir con poca información, no para comprometerse**. El Canvas organiza los supuestos; la estimación informal les pone orden de magnitud; y ambos existen para que la validación empiece por donde más se arriesga.

## D. Estimación

### D10. Ley de la trivialidad y sesgos de grupo: ¿cómo los mitigan Wideband Delphi y Planning Poker?

**La ley.** Tercera de las leyes de Parkinson: *"El tiempo dedicado a un tema es **inversamente proporcional a su importancia**"* — la **Ley de la trivialidad** [CL05-P, p. 6].

**Por qué ocurre** *(inferencia)*: sobre lo trivial **todos pueden opinar**, porque no requiere conocimiento especializado ni asumir riesgo reputacional. Sobre lo estructural opinan pocos, y los demás callan por no exponer su falta de criterio. El resultado es que **el tiempo de discusión se reparte según cuánta gente puede participar, no según lo que está en juego**.

**En una sesión de estimación**, se manifiesta así: se consumen veinte minutos debatiendo si una tarea rutinaria es 2 o 3 puntos, y se aprueba en dos minutos un ítem de 13 puntos que nadie entiende del todo — justamente el que concentra el riesgo del sprint.

**Los sesgos de grupo que la cátedra nombra.** La desventaja del **juicio experto** es ser *"subjetivo y susceptible a sesgos **personales o de grupo**"*, y la ventaja declarada de **Delphi** es que *"**reduce la influencia de jerarquías o liderazgos fuertes (al ser anónimo)** y fomenta la convergencia de opiniones"* [P1-CL05, p. 8]. Los dos sesgos implicados son:

- **Anclaje**: la primera cifra pronunciada condiciona todas las siguientes; el resto ajusta alrededor de ella en lugar de pensar de cero.
- **Deferencia jerárquica**: si el primero en hablar es el líder técnico o el senior, nadie contradice. El resultado parece consenso y es **la opinión de una persona repetida por el grupo**.

**Cómo los mitiga Wideband Delphi** [P1-CL05, p. 8]:

| Mecanismo | Sesgo que ataca |
|---|---|
| **Anonimato** | La **deferencia jerárquica** — la lámina lo dice textualmente |
| **Consulta a varios expertos** | El sesgo **personal** de un único estimador |
| **Iteración por rondas**, resumiendo y permitiendo ajustar | El **anclaje**: nadie ve un número antes de producir el suyo, y el ajuste posterior se hace sobre el **resumen del grupo**, no sobre la voz de alguien |

Su costo declarado: *"puede ser costoso en tiempo si se requieren varias rondas"* y *"depende de la selección de expertos"* — el anonimato neutraliza la jerarquía **dentro** del panel, pero **quién entra al panel** sigue siendo una decisión no anónima.

**Cómo los mitiga Planning Poker** [P1-CL05, p. 5]:

| Mecanismo | Sesgo que ataca |
|---|---|
| **Carta elegida en secreto** | Anclaje y deferencia: obliga a formar juicio **independiente** |
| **Revelación simultánea** | Impide ajustar el propio número después de ver los ajenos |
| **Discusión centrada en las diferencias** | **La Ley de la trivialidad** — este es el punto |
| **Repetir hasta el consenso** | Convergencia con información compartida, no por cansancio |

**El mecanismo anti-trivialidad, que es la parte más interesante de la respuesta** *(inferencia)*:

La lámina dice que *"las discusiones se centran en **las diferencias** de estimaciones"*. Eso convierte a la **divergencia en el criterio de asignación del tiempo de discusión**, y la divergencia correlaciona con la incertidumbre real: los ítems que todos entienden igual reciben votos parecidos y **se despachan rápido**; los que esconden un riesgo, una dependencia o una ambigüedad producen votos dispersos y **se discuten**.

Es decir: **Planning Poker invierte la Ley de la trivialidad**. En vez de dedicar tiempo según cuánta gente puede opinar, lo dedica según **cuánto desacuerdo hay** — que es un buen proxy de cuánto está en juego. La ley opera cuando la agenda la fija la conversación; el poker le quita esa facultad a la conversación y se la da a las cartas.

**La relación entre ambas técnicas.** Planning Poker es **Wideband Delphi comprimido**: mismo mecanismo —juicio independiente, revelación, discusión de diferencias, nueva ronda— pero en minutos y cara a cara en lugar de rondas escritas. Por eso Scrum lista **Planning Poker, T-Shirt Sizing y Wideband Delphi** juntas [P1-CL02, p. 26]. Lo que Delphi gana en rigor (anonimato completo, expertos externos), Poker lo gana en velocidad y en **compromiso del equipo**: estima quien va a hacer el trabajo, y eso es lo que la lámina llama *"fomenta la participación de todo el equipo"*. *(inferencia)*

### D11. Estimación de alto nivel en Scrum: dónde ocurre, qué artefactos toca, cómo se ve en el burndown y cuándo se reestima

**Dónde ocurre y qué es** [P1-CL02, p. 26]. "El Equipo determina una **estimación de alto nivel de cada uno de los elementos del Backlog de Producto** presentados. Para eso puede ser necesario **tomar algunas decisiones iniciales de diseño y hacer preguntas adicionales al Dueño de Producto** para asegurar un buen entendimiento del ítem." Técnicas: **Planning Poker, T-Shirt Sizing, Wideband Delphi**.

Tres cosas de esa lámina: **estima el Equipo** (no el PO, no el SM); se estima **el Backlog de Producto**, no el de Sprint; y estimar **exige entender**, al punto de requerir decisiones de diseño y preguntas al PO. Esto último explica por qué la estimación es también un mecanismo de detección de ambigüedad, y por qué la **DoR** pide *estimaciones de tiempo con acuerdo de los interesados* [P1-CL02, p. 31].

**Los dos niveles de estimación, que hay que distinguir:**

| | **Alto nivel** | **Fino** |
|---|---|---|
| **Objeto** | Ítems del **Backlog de Producto** | Tareas del **Backlog de Sprint** |
| **Unidad** | Esfuerzo relativo: **Story Points**, tallas | **Esfuerzo que no supere un día** [P1-CL02, p. 24] |
| **Cuándo** | Al presentarse el ítem; se refina después | En la **Planificación**, al descomponer |
| **Para qué** | Priorizar y planificar releases | Organizar y seguir el sprint |
| **Quién** | El Equipo | El Equipo |

Notar el cambio de unidad: el Backlog de Producto se estima en **relativo** ([pregunta D6](#d6-story-points-qué-miden-y-por-qué-no-se-traducen-directamente-a-horas)), pero el Backlog de Sprint se descompone en tareas con **estimación de duración menor a un día** y se lleva el **esfuerzo pendiente** de cada tarea no terminada [P1-CL02, p. 24]. Son dos monedas distintas para dos propósitos distintos, y confundirlas es el error habitual.

**Cómo se ve en el burndown** [P1-CL02, p. 25]. El diagrama grafica un sprint de **20 días** con **190 horas** de esfuerzo restante estimado inicial, y muestra **dos curvas**: la **línea ideal**, recta desde el total hasta cero, y la **curva real**, escalonada. Lecturas:

| Patrón | Qué indica |
|---|---|
| Real **por debajo** de la ideal | El equipo va adelantado respecto del ritmo lineal |
| Real **por encima** | Va atrasado; queda sprint para reaccionar — ese es el valor del gráfico |
| **Mesetas horizontales** | Días sin completar tareas: bloqueo, o tareas demasiado grandes para cerrarse en un día |
| **Caída brusca al final** | Señal de alerta: sugiere que se declaró "terminado" en bloque el último día, típicamente sin **DoD** exigente |
| Sube | Se agregó trabajo o se descubrió que lo estimado estaba mal |

Y el punto de proceso: el burndown **lo actualiza el Scrum Master al final de la reunión diaria** [P1-CL02, p. 28], sobre el Backlog de Sprint que **el equipo actualiza diariamente** [P1-CL02, p. 24]. Es decir, **la estimación se revisa todos los días**, no una vez por sprint.

**Cuándo se reestima** [P1-CL02, pp. 24, 30]:

1. **A diario, dentro del sprint**: el Backlog de Sprint lleva *"una estimación del esfuerzo pendiente de cada tarea no terminada"* — eso **es** reestimación continua del remanente.
2. **En el Refinamiento del Backlog** (ceremonia optativa, durante el sprint): *"revisión, ordenamiento, unión de HU, **reestimación**"*. Es el lugar formal para reestimar ítems del Backlog de Producto con información nueva.
3. **Al descomponer una épica**: partir en historias menores obliga a estimar las partes, y la suma rara vez coincide con la estimación original de la épica ([pregunta B11](#b11-historias-de-usuario-formato-por-qué-expresan-el-qué-y-no-el-cómo-y-qué-es-una-épica)). *(inferencia)*

**Lo que no se reestima:** los ítems **ya terminados**. Si una historia estimada en 5 costó 13, **no se corrige el 5 hacia atrás** — porque entonces la velocidad dejaría de reflejar la realidad y se perdería la información. El error se absorbe en la **velocidad observada**, que es justamente la métrica que se quiere honesta. *(inferencia)*

**El cierre que conecta con Parkinson:** el par *estimación relativa + burndown diario* es lo que permite detectar la expansión del trabajo mientras todavía se puede actuar ([pregunta D8](#d8-parcial1-cómo-abordan-las-técnicas-de-estimación-ágiles-el-impacto-de-la-ley-de-parkinson-frente-a-los-enfoques-predictivos-especialmente-con-requisitos-cambiantes)). Sin el gráfico diario, el sprint sería una caja negra de dos a cuatro semanas, con el mismo problema de visibilidad que una fase larga de cascada.

### D12. Caso PERT con varios ítems: calculá y explicá qué NO permite concluir el resultado

**La fórmula** [P1-CL05, p. 7]: `E = (O + 4M + P) / 6`

**Los datos** *(caso de elaboración propia)*. Tres historias de un sprint, estimadas en días:

| Ítem | O | M | P | Cálculo | **E** | Spread (P−O) |
|---|---|---|---|---|---|---|
| **H1** — Formulario de reserva | 2 | 3 | 4 | (2 + 12 + 4)/6 = 18/6 | **3,0** | 3 |
| **H2** — Integración con WhatsApp | 3 | 5 | 19 | (3 + 20 + 19)/6 = 42/6 | **7,0** | **16** |
| **H3** — Reporte de ausentismo | 4 | 6 | 8 | (4 + 24 + 8)/6 = 36/6 | **6,0** | 4 |
| | | | | **Total** | **16,0 días** | |

**Lo que sí se puede leer:**

- **H1 y H3 están bien entendidas**: el más probable y el esperado casi coinciden (3 y 3; 6 y 6), y los rangos son estrechos.
- **H2 es el problema**. Su más probable era **5** y PERT devuelve **7** — un corrimiento del 40 %, que viene enteramente de la cola pesimista. Con **O = 3 y P = 19**, el pesimista es **seis veces** el optimista: eso no es una estimación, es una declaración de que **el equipo no sabe qué va a encontrar**. Probablemente hay una dependencia externa (la API de WhatsApp, una aprobación, un entorno) que alguien conoce y otros no.
- **El spread es la información más útil de la tabla**, más que los valores esperados. Ordenar por `P−O` es una forma directa de **ordenar por riesgo**, y coincide con lo que la lámina declara como ventaja del método: *"ayuda a **gestionar el riesgo** asociado con las estimaciones"*.
- **Acción sugerida**: antes de comprometer H2, descomponerla o hacer un *spike* para reducir la incertidumbre. Y notar que una divergencia así es exactamente lo que **Planning Poker** habría hecho visible ([pregunta D5](#d5-planning-poker-proceso-por-qué-el-voto-es-secreto-y-simultáneo-y-qué-revela-la-divergencia)).

**Lo que NO permite concluir** — el núcleo de la pregunta *(inferencia; el material da la fórmula sin discutir sus límites, y el cálculo final de PCU y el factor de productividad quedaron fuera del recorte* [N-2026-09-07-alcance-primer-parcial]*)*:

**1) No dice que el trabajo vaya a tardar 16 días de calendario.** Son **16 días de esfuerzo**, y esfuerzo ≠ duración ([pregunta D1](#d1-diferenciá-tamaño-esfuerzo-complejidad-y-duración)). Falta saber cuánta gente, con qué disponibilidad, con qué paralelismo y con qué dependencias entre los ítems. Si H3 necesita que H1 esté lista, no hay paralelización posible por más gente que se agregue.

**2) No dice que 16 sea el resultado más probable.** Es un **valor esperado ponderado**, no una moda ni una garantía. De hecho, la suma de los *más probables* es 3 + 5 + 6 = **14**, dos días menos. Ninguno de los dos números es "el que va a pasar".

**3) No da una probabilidad de cumplimiento.** PERT, tal como lo presenta la cátedra, devuelve **un número, no una distribución ni un intervalo de confianza**. Decir "hay 80 % de chances de terminar en 16 días" es una afirmación que **este cálculo no respalda**.

**4) No valida las tres estimaciones de entrada.** La fórmula es aritmética: si O, M y P están sesgados, el resultado está sesgado con apariencia de método. **PERT no corrige el optimismo, lo promedia.** Si el equipo sistemáticamente subestima, los tres valores estarán bajos y E también.

**5) La suma de valores esperados oculta el riesgo individual.** Y este es el punto más fino: **16 días parece tan confiable como 16 días de tres ítems bien entendidos**, pero acá **H2 concentra casi toda la varianza**. Dos carteras con el mismo total no tienen el mismo riesgo. Presentar solo el total **destruye justamente la información que PERT produjo**.

**6) No dice nada sobre el orden ni la ruta crítica.** El total es una suma de esfuerzos; no es un cronograma.

**Cómo cerrar la respuesta.** El valor de PERT no está en el número que devuelve sino en **obligar a explicitar el escenario pesimista**. La pregunta "¿qué tendría que pasar para que esto tarde 19 días?" es la que hace aflorar dependencias, supuestos y riesgos — y esa conversación vale más que el 7,0. Reportar solo el valor esperado, sin el rango, **desperdicia el método**.

## E. Calidad

### E10. Plan de gestión de calidad, plan de pruebas y casos de prueba: qué contiene cada uno y quién lo usa

La cátedra los agrupa bajo el título irónico de *Documentos """importantes"""* [P1-CL06, pp. 15–17]. Van de lo general a lo particular.

**1) Plan de Gestión de Calidad de Software** [P1-CL06, p. 15]

"**Cómo se asegura y controla la calidad durante todo el ciclo de vida** del software. Incluye estrategias, métricas, responsabilidades y actividades para garantizar que el producto cumpla con los estándares establecidos."

Contenidos: **1.** Introducción (objetivo, alcance) · **2.** Política de Calidad (principios y objetivos) · **3.** Roles y responsabilidades (Gerente de Calidad, Equipo de Desarrollo, Equipo de Pruebas) · **4.** Estrategia de Calidad (requisitos, métricas, revisiones y auditorías) · **5.** Actividades de Control de Calidad (revisiones de código, pruebas automatizadas y manuales, V&V) · **6.** **Cronograma y Presupuesto** · **7.** Procedimientos de Aprobación.

**2) Plan de Pruebas de Software** [P1-CL06, p. 16]

"**Enfoque, alcance, recursos y cronograma para realizar las pruebas.** Describe los tipos de pruebas, los criterios de aceptación y finalización, el ambiente de pruebas y las herramientas."

Contenidos: **1.** Introducción · **2.** Estrategia de Pruebas (tipos y ambiente) · **3.** Gestión de Riesgos de Calidad · **4.** **Herramientas** (Postman, Selenium, JIRA, SonarQube) · **5.** Planificación de Actividades · **6.** Gestión de Incidentes · **7.** Informe de Resultados.

**3) Casos de Prueba de Software** [P1-CL06, p. 17]

"**Pasos específicos para probar una funcionalidad.** Incluye **precondiciones, datos de entrada, resultados esperados y obtenidos**, para garantizar que cada componente funcione como se espera. Incluye el **registro y trazabilidad** de las pruebas."

**Objetivo**: verificar que cada requisito de negocio se cumpla sin errores; **detectar defectos antes de la puesta en producción, reduciendo costo de corrección**; y servir como **documentación viva** que facilita mantenimiento y regresión.

**Buenas prácticas de redacción**: **Claridad** (una sola verificación por caso) · **Trazabilidad** (referencia al ID del requisito o user story) · **Atomicidad** (los casos no dependen unos de otros) · **Datos realistas** (entradas representativas, evitando información sensible) · **Resultados observables** (salidas medibles: UI, API response, BD, logs) · **Mantenibilidad** (nombres descriptivos, versionados junto al código).

**La comparación**

| | **Plan de Calidad** | **Plan de Pruebas** | **Casos de Prueba** |
|---|---|---|---|
| **Alcance** | **Todo el ciclo de vida**; toda la función de calidad | **Solo las pruebas** | **Una funcionalidad** |
| **Función QA/QC** | Ambas: *asegura **y** controla* | Sobre todo **QC**, planificado | **QC** en ejecución |
| **Nivel** | Política y gobierno | Táctico | Operativo |
| **Quién lo usa** | Gerente de Calidad, dirección, auditores | Líder de QA, equipo de pruebas | Testers, desarrolladores, automatización |
| **Cada cuánto cambia** | Por proyecto o por organización | Por release | Permanentemente, junto al código |

**Las tres observaciones que dan profundidad** *(inferencia)*:

**1) Hay anidamiento, no repetición.** El Plan de Calidad contiene una sección de *Actividades de Control de Calidad*; el Plan de Pruebas **desarrolla esa sección**; los Casos de Prueba **instancian el Plan de Pruebas**. Por eso el Plan de Calidad es el único que incluye **presupuesto**: es el que decide **cuánto se invierte** en calidad — o sea, el que fija el **costo de calidad** de [pregunta E4](#e4-costo-de-calidad-vs-costo-de-no-calidad-fallos-internos-vs-externos).

**2) La trazabilidad es lo que une los tres niveles con el requisito.** La buena práctica pide *"referencia al ID del requisito o user story"*, y el caso de prueba registra *"resultados esperados **y obtenidos**"*. Eso permite responder, para cualquier requisito, si fue probado y con qué resultado. Es la misma idea que RUP dibuja en su cadena `Caso de Uso → … → Caso de Prueba` ([pregunta A12](#a12-jacobson-pone-los-casos-de-uso-en-el-centro-conectalo-con-ruporientación-a-objetos-y-con-puntos-de-caso-de-uso)).

**3) "Documentación viva" es la clave del tercer documento.** Un caso de prueba versionado junto al código y ejecutado en cada build **no se desactualiza**, porque si el comportamiento cambia el caso falla. Es la única documentación que se autodenuncia cuando miente — la misma propiedad que la lámina de TDD atribuye a las pruebas escritas primero: *"proporciona documentación actualizada del comportamiento esperado"* [P1-CL02, p. 15]. Y **Given-When-Then** es el formato que lleva esa idea al límite, porque el mismo texto sirve de requisito, de criterio de aceptación y de prueba ejecutable ([pregunta E7](#e7-formato-given-when-then-estructura-buenas-prácticas-y-un-caso-positivo-y-uno-negativo)).

*Alcance:* la **plantilla y las sugerencias de casos de prueba**, las **herramientas de pruebas** en detalle y las **revisiones y auditorías** quedaron **fuera del recorte** [CL06-P, pp. 12, 13, 24, 30, 31]. Entra **qué es cada documento y qué contiene**. [N-2026-09-07-alcance-primer-parcial]

### E11. Tipos de deuda de McConnell vs cuadrantes de Fowler: ¿se solapan? ¿Qué agrega cada clasificación?

**Las dos clasificaciones** [P1-CL06, pp. 4, 5, 6]:

**McConnell** (*Code Complete*) — un eje, dos categorías:

- **Intencionada**: "decisión consciente de **optimizar el presente**" (a corto o largo plazo). Ej.: elegir un framework rápido pero de bajo rendimiento para llegar a un deadline; requerirá reescritura posterior.
- **No intencionada**: "**errores, falta de conocimiento o diseño defectuoso**". Ej.: liberar código de juniors sin revisión suficiente, generando errores que aparecen tras el lanzamiento.

**Fowler** — dos ejes, cuatro cuadrantes: **prudente/imprudente** × **deliberada/inadvertida**, que "sirven para **calibrar intención y nivel de riesgo**".

**¿Se solapan? Sí, en un eje.** El eje **intencionada/no intencionada** de McConnell es el mismo que **deliberada/inadvertida** de Fowler: ambos preguntan **si el equipo sabía**. La correspondencia es directa:

| McConnell | Fowler |
|---|---|
| **Intencionada** | Prudente + **Deliberada** · Imprudente + **Deliberada** |
| **No intencionada** | Prudente + **Inadvertida** · Imprudente + **Inadvertida** |

**Qué agrega Fowler: el eje de la prudencia — el que sirve para decidir.**

Y acá está el argumento central de la respuesta *(inferencia)*. Con McConnell solo se puede preguntar *¿lo sabíamos?*, y esa pregunta **no basta para actuar**, porque **la intención no determina la gravedad**:

- Los dos ejemplos de deuda **deliberada** de Fowler son moralmente opuestos: la *tarjeta de backlog con el refactor previsto* antes de la demo es **buena gestión**; el *parche hardcodeado con credenciales a las 3 a. m. sin plan de pago* es **irresponsabilidad**. **McConnell los pone en la misma casilla** — ambos son "intencionados".
- Lo mismo del otro lado: el *cambio de normativa que obliga a reescribir el módulo fiscal* es **inevitable y aceptable**; el *onboarding apurado con juniors copiando código sin revisión* es **negligencia**. Ambos son "no intencionados" para McConnell.

Es decir: **el eje de McConnell describe el origen; el eje de la prudencia evalúa la decisión**. Y la decisión es lo que se puede cambiar.

**Qué agrega McConnell: la vía de remediación.**

No es una clasificación redundante, y conviene decirlo para que la respuesta no parezca un ranking. El origen **indica qué hacer para que no se repita** *(inferencia)*:

- La deuda **intencionada** se ataca con **gestión**: registrarla, estimarla, priorizarla, ponerle fecha — las tres buenas prácticas de [pregunta E8](#e8-buenas-prácticas-de-control-de-deuda-técnica). El problema no es que se genere, es que se pierda de vista.
- La deuda **no intencionada** se ataca con **capacidad y proceso**: capacitación, estándares de código, revisiones, pruebas automatizadas. Registrarla no sirve de nada si el equipo **no puede verla**. Y eso es exactamente **QA**: *"definición de políticas y estándares, auditorías de proceso, **capacitación** y mejora continua"* [P1-CL06, p. 9].

**La síntesis, que es la mejor forma de cerrar:**

| | Qué pregunta | Para qué sirve |
|---|---|---|
| **Eje intención** (McConnell y Fowler) | ¿Lo sabíamos? | Decide **cómo prevenirla**: gestión (si se sabía) o capacidad y proceso (si no) |
| **Eje prudencia** (solo Fowler) | ¿Estaba justificada y tiene plan de pago? | Decide **si es tolerable** y con qué urgencia se paga |

**Y por qué las buenas prácticas de la cátedra funcionan sobre los dos ejes a la vez**: *registrar con esfuerzo y fecha* mueve de **inadvertida a deliberada** (eje McConnell/intención), y *tratarla como historia de usuario con umbral de 90 días* mueve de **imprudente a prudente** (eje Fowler). Por eso hacen falta las dos clasificaciones: **sin la de McConnell no se sabe qué cambiar; sin la de Fowler no se sabe cuánto importa.**

### E12. [PARCIAL1] ¿Cómo contribuyen Scrum, XP, TDD y Kanban a la calidad, cómo abordan el "costo de la no calidad" y contribuyen o no a mitigar la deuda técnica?

Pregunta 5 del parcial anterior, y la más integradora de todo el examen. [PARCIAL1, p. 1] Pide **tres cosas distintas** —calidad, costo de no calidad, deuda técnica— sobre **cuatro prácticas**, y el enunciado incluye un **"o no"** que habilita explícitamente el matiz. Conviene responder por los tres ejes, no por las cuatro metodologías.

**Eje 1 — Contribución a la calidad**

| | Mecanismo | Función |
|---|---|---|
| **Scrum** | **DoD**: criterios que definen cuándo un incremento está completo, creados por **toda la organización**, usados como *misma guía y checklist* [P1-CL02, p. 32]. **Revisión**: el PO acepta o rechaza [P1-CL02, p. 29]. **Retrospectiva**: inspecciona procesos e interacciones [P1-CL02, p. 30] | DoD y Retrospectiva = **QA** (proceso, prevención). Revisión = **QC** (producto, detección) |
| **XP** | Doce prácticas que corren en paralelo: pruebas, pairing, integración continua, refactoring, estándares ([pregunta B12](#b12-parcial1-ciclo-de-tdd-y-cómo-se-relacionan-las-prácticas-de-xp-con-la-planificación-el-aseguramiento-y-el-control-de-la-calidad)) | Las tres funciones —planificación, QA y QC— **todos los días**, no en fases |
| **TDD** | Prueba **antes** del código; código mínimo; refactor en verde [P1-CL02, p. 15] | **QA por intención** (previene: el defecto no llega a existir) y **QC por producto** (deja una suite ejecutable) |
| **Kanban** | Visualización, **límite de WIP**, gestión del flujo, mejora continua [P1-CL02, p. 16] | Indirecta pero real: menos trabajo simultáneo = menos cambios de contexto = menos errores |

El hilo común: **las cuatro adelantan el momento en que un problema se vuelve visible.**

**Eje 2 — El costo de la no calidad**

Recordar la estructura [P1-CL06, p. 3]: costo de calidad (prevención y evaluación) vs. costo de no calidad (**fallos internos**, previos al lanzamiento, y **fallos externos**, reclamos y reputación), con la conclusión de que *invertir en calidad reduce significativamente los costos de no calidad*.

Las cuatro prácticas hacen **el mismo movimiento**: acortan el tiempo entre **introducir** un defecto y **detectarlo**, y así lo mueven hacia la izquierda del esquema de costos:

```
prevenido  <  detectado en revisión  <  fallo interno  <  fallo externo
   TDD          pairing, GWT            pruebas de        (lo que se
   estándares   revisión de código      sprint, DoD        evita)
◄──────────────── cada paso a la izquierda es más barato ────────────
```

- **TDD** es el caso extremo: el defecto **no llega a existir**, así que no aparece en ninguna casilla de no calidad. Es **prevención pura**.
- **XP** con integración continua y pairing detecta en minutos lo que una revisión formal detectaría en semanas.
- **Scrum** con la **Revisión** convierte en **fallo interno** lo que sin ella sería **externo**: el PO rechaza el incremento antes de que llegue al cliente. Cada 1–4 semanas, no una vez al final.
- **Kanban** ataca otro componente: las **esperas** y el retrabajo por acumulación, que son desperdicio Lean ([pregunta B9](#b9-lean-qué-es-el-desperdicio-en-software-y-cómo-lo-atacan-kanban-y-el-mvp)).

**Todas aumentan deliberadamente el costo de calidad** —escribir pruebas primero, programar de a dos, mantener suites automatizadas cuesta tiempo— **para reducir mucho más el de no calidad**. Es la tesis de la lámina, implementada.

**Eje 3 — Deuda técnica: contribuyen… y también pueden generarla**

**Cómo la mitigan:**

- **Refactoring** (XP) y la tercera etapa de **TDD** son **pago continuo de deuda**: se mejora la estructura manteniendo las pruebas verdes [P1-CL02, p. 15]. No es un proyecto de saneamiento, es una rutina.
- Las pruebas de TDD/XP son **lo que hace posible refactorizar**. Sin red, refactorizar es temerario, y la deuda se vuelve impagable ([pregunta B4](#b4-los-5-valores-y-las-12-prácticas-de-xp-cómo-se-refuerzan-entre-sí)).
- El **Backlog de Producto**, *lista única, pública y dinámica priorizada* [P1-CL02, p. 23], es el lugar donde la cátedra pide registrar la deuda **tratándola como historias de usuario** [P1-CL06, p. 6]. Scrum provee el contenedor que esa buena práctica necesita.
- La **Retrospectiva** detecta causas de deuda a nivel de proceso; el **umbral de 90 días** le da criterio de escalamiento.
- El **límite de WIP** de Kanban impide la acumulación de trabajo a medias, que es una forma de deuda en sí misma.
- Y en conjunto: estas prácticas **mueven la deuda al cuadrante prudente + deliberada** [P1-CL06, p. 5] — la registran (deliberada) y le dan plan de pago dentro del ciclo (prudente).

**Cómo pueden generarla — el "o no" del enunciado** *(inferencia; es la parte que distingue una respuesta completa)*:

- **La presión del timebox se descarga sobre lo invisible.** Si el sprint se sobrecomprometió, lo primero que se sacrifica son las pruebas y el refactor, porque son lo único que el PO no ve en la demo. El sprint "cierra" y la deuda queda. **La DoD existe precisamente para impedirlo**, y un equipo con DoD débil usa Scrum para *acelerar* la acumulación de deuda.
- **Scrum sin prácticas técnicas no protege nada.** Scrum es un **marco de gestión**: define roles, artefactos y ceremonias, pero **no prescribe ninguna práctica de ingeniería**. Nada en Scrum obliga a escribir pruebas ni a refactorizar. Por eso se lo combina con XP y TDD — y por eso el enunciado del parcial dice *"complementadas por TDD y Kanban"*.
- **La entrega incremental permanente puede postergar la arquitectura.** Optimizar cada sprint para valor demostrable tiende a diferir el trabajo estructural, que nunca es el ítem más prioritario para el PO. Es deuda **deliberada** que se vuelve imprudente por acumulación.
- **Kanban sin límites reales es un tablero decorativo.** Si el WIP no se respeta, la visualización muestra el problema y nadie actúa.
- **Y la velocidad puede inflarse**, sosteniendo la apariencia de ritmo mientras se entrega menos ([pregunta D8](#d8-parcial1-cómo-abordan-las-técnicas-de-estimación-ágiles-el-impacto-de-la-ley-de-parkinson-frente-a-los-enfoques-predictivos-especialmente-con-requisitos-cambiantes)).

**Cierre sugerido.** Las cuatro contribuyen a la calidad por el mismo mecanismo —**acortar los lazos de feedback**— y eso desplaza los defectos hacia donde son baratos, reduciendo el costo de no calidad. Pero la contribución **no es automática**: depende de que existan los mecanismos que las hacen exigibles —**DoD** rigurosa, prácticas técnicas efectivamente aplicadas, límites de WIP respetados, deuda registrada en el backlog con su umbral de 90 días—. Sin eso, el mismo marco que acelera la entrega acelera también la acumulación de deuda, y la iteración rápida se vuelve una forma eficiente de empeorar el sistema. Que es, en el fondo, la tesis de toda la clase de calidad: **la calidad no sucede, se gestiona** [P1-CL06, p. 2].

---

## Cómo seguir

- Volver a [las preguntas sin respuesta](preguntas.md) para recuperación activa sin ayuda.
- Revisar el [alcance detallado](../parcial-1-alcance.md) antes de estudiar cualquier tema, para no invertir tiempo en material excluido.
- Las cinco preguntas del parcial anterior están respondidas en [pregunta A7](#a7-parcial1-qué-relación-hay-entre-los-modelos-de-ciclo-de-vida-del-software-y-la-deuda-técnica), [pregunta B12](#b12-parcial1-ciclo-de-tdd-y-cómo-se-relacionan-las-prácticas-de-xp-con-la-planificación-el-aseguramiento-y-el-control-de-la-calidad), [pregunta C12](#c12-parcial1-cómo-se-conectan-las-técnicas-de-estimación-informales-con-el-business-model-canvas-en-etapas-iniciales-de-un-proyecto), [pregunta D8](#d8-parcial1-cómo-abordan-las-técnicas-de-estimación-ágiles-el-impacto-de-la-ley-de-parkinson-frente-a-los-enfoques-predictivos-especialmente-con-requisitos-cambiantes) y [pregunta E12](#e12-parcial1-cómo-contribuyen-scrum-xp-tdd-y-kanban-a-la-calidad-cómo-abordan-el-costo-de-la-no-calidad-y-contribuyen-o-no-a-mitigar-la-deuda-técnica).
