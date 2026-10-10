# Evaluación de arquitecturas

> **Alcance:** esta clase es posterior al recorte del primer parcial y no aparece en él. Ver [alcance del primer parcial](../parcial-1-alcance.md). Fuente principal: presentación de la clase 9 `CL09-P`. La mayoría de sus diapositivas son imagen y el texto extraído está incompleto. Por eso las páginas se revisaron renderizadas y esta síntesis cubre también ese contenido. La sección [ATAM en la práctica](#atam-en-la-práctica-caso-de-estudio-de-hariharan) suma la presentación de Hariharan, `B03`, entregada por la cátedra como bibliografía.

## Cuándo definir la arquitectura: anticipar o adaptarse

La clase abre con dos posturas extremas: [CL09-P, p. 3]

- **Waterfall — BDUF (*big design up front*):** inversión significativa en las etapas iniciales (*blueprint*, *phase 0*).
- **Agile — YAGNI (*you are not gonna need it*):** refactorizar para que la arquitectura evolucione con los problemas y eliminar la deuda técnica que generan las iteraciones.

Entre ambas hay un **trade-off entre adaptación y anticipación**. [CL09-P, p. 3] La diapositiva cita «Krutchen, 2010». **Inferencia:** probablemente se refiere a Philippe Kruchten, pero no al paper de 1995 de la bibliografía (`B01`).

### El sweet spot de Boehm y Turner

El gráfico «¿Cuándo definir la arquitectura?» proviene de Boehm y Turner, *Balancing Agility and Discipline* (2003). [CL09-P, p. 4]

- **Eje horizontal:** porcentaje de tiempo que se agrega al principio para arquitectura y resolución de riesgos.
- **Eje vertical:** porcentaje de tiempo que se agrega al cronograma total, es decir, cuánto más se tarda respecto de lo estimado inicialmente.
- **Línea roja punteada:** porcentaje del cronograma dedicado a arquitectura inicial y resolución de riesgos. Crece con la inversión.
- **Curvas negras:** tiempo agregado por *rework*, según el factor RESL de COCOMO II. Bajan a medida que se invierte más al principio.
- **Curvas verdes:** total agregado. El mínimo de cada curva es el **sweet spot**.
- **Desplazamiento del sweet spot:** el cambio rápido lo corre hacia la izquierda y la necesidad de alta garantía (*high assurance*), hacia la derecha.

El gráfico muestra tres tamaños de proyecto, interpretados así: [CL09-P, p. 5]

| Tamaño | Sweet spot | Recomendación | Razón |
|---|---|---|---|
| 10 KSLOC (10.000 LOC) | Muy a la izquierda | Dedicar poco tiempo a arquitectura | El proyecto es chico y los riesgos son manejables |
| 100 KSLOC | Punto intermedio | Dedicar una proporción moderada de tiempo *upfront* | Hay que balancear |
| 10.000 KSLOC (10 millones de LOC) | Muy a la derecha | Invertir bastante tiempo inicial en arquitectura y gestión de riesgos | El *rework* sería carísimo |

**Lectura aproximada del gráfico:** los puntos verdes caen cerca del 5 %, del 25 % y del 40 % del eje horizontal, respectivamente. [CL09-P, p. 4]

**Conclusión de la clase:** el momento y el esfuerzo para definir la arquitectura dependen del tamaño del proyecto y del nivel de certeza requerido. Los proyectos chicos admiten más agilidad y menos arquitectura *upfront*. Los grandes o críticos piden más inversión inicial en arquitectura y en resolución de riesgos. [CL09-P, p. 5]

### Cuatro momentos posibles en Scrum

| Opción | Cuándo se define | Quién la elabora | Cuándo se evalúa |
|---|---|---|---|
| Big up-front | Antes de los sprints; durante los sprints solo hay cambios menores | Típicamente un arquitecto | Antes de los sprints |
| Sprint-zero | Durante el primer sprint (2 a 4 semanas) | Típicamente el equipo de desarrollo | Al final del sprint |
| In-sprints | Se diseña y refactoriza según la necesidad | Un equipo maduro, con mucha experiencia en el dominio | Después de refactorizaciones significativas |
| Separate architecture team | Para cada release, a partir del análisis de los ASR | Un equipo de arquitectura separado | Después de cada release significativo |

La tabla sintetiza [CL09-P, p. 6]. **Inferencia:** las cuatro opciones recorren el mismo eje de anticipación y adaptación. La primera se acerca a BDUF y la tercera a YAGNI.

## Requisitos arquitectónicamente significativos (ASR)

Un **ASR** es cualquier requisito, funcional o de calidad, cuya satisfacción obliga a tomar decisiones arquitectónicas clave, con un impacto directo y medible en el diseño. [CL09-P, p. 6]; [CL09-P, p. 7] **Prueba práctica:** si cambiara ese requisito, probablemente cambiaría la arquitectura del sistema. [CL09-P, p. 7]

| Tipo | Ejemplos del material |
|---|---|
| De calidad (no funcionales) | Escalabilidad: «soportar 1 millón de usuarios concurrentes». Seguridad: «cumplir con GDPR y encriptar datos sensibles en tránsito y en reposo». Disponibilidad: «99,999 % de uptime». |
| Funcionales que afectan la arquitectura | «Integrarse en tiempo real con sistemas externos de pago». «Permitir plug-ins de terceros sin redeployar el core». |

La tabla sintetiza [CL09-P, p. 7]. **Inferencia:** los ASR se parecen a los [drivers de arquitectura](arquitectura-y-atributos-de-calidad.md#attribute-driven-design-restricciones-y-drivers) de la clase 7, que son escenarios críticos y significativos. [CL07-P, p. 24] La diferencia es de formulación: el ASR se expresa como requisito y el driver, como escenario.

## Agile Architecture en SAFe

SAFe (*Scaled Agile Framework*) está pensado para desarrollos grandes, típicamente corporativos, con alta complejidad y muchos equipos. Su concepto de *Agile Architecture* intenta balancear BDUF y YAGNI combinando dos componentes: [CL09-P, p. 8]

- **Intentional architecture:** estrategias de arquitectura planeadas, alineadas con los atributos de calidad elegidos, que dan guías para sincronizar a los distintos equipos.
- **Emergent design:** evolución incremental de la implementación, que permite a los desarrolladores responder de inmediato a las necesidades de los usuarios.

### Architectural runway

El **architectural runway** está formado por los componentes, el código y la infraestructura necesarios para implementar las features del corto plazo sin rediseño adicional. Se diseña en un conjunto reducido de iteraciones, con el arquitecto de sistema como *product owner* de un equipo dedicado a la nueva iniciativa tecnológica. [CL09-P, p. 9] Durante las iteraciones, los *feature teams* —cada uno con su propio product owner y scrum master— construyen sobre el runway. Con el tiempo, la evolución de los requerimientos lo consume, por lo que hay que mantenerlo y renovarlo periódicamente. [CL09-P, p. 10]

Características que destaca la clase: [CL09-P, p. 11]

- Incluye **arquitectura emergente**, que se construye sprint a sprint, y **arquitectura intencional**, que se planifica a propósito para soportar el crecimiento.
- Architectural runway ≠ diseñar todo al inicio. Se trata de anticipar lo necesario a corto y mediano plazo para no frenar el desarrollo, sin intentar adivinar todo el futuro del sistema.
- Lo componen componentes reutilizables, servicios compartidos, infraestructura de integración y despliegue, APIs y tecnologías ya adoptadas.
- No es estático: se amplía y ajusta continuamente al ritmo de los *Product Increments* (PIs).

**Ejemplo del material:** si una empresa sabe que el próximo trimestre deberá habilitar pagos internacionales, puede diseñar e implementar por adelantado servicios de seguridad, escalabilidad y compliance. Cuando esas features se prioricen, ya habrá una base que las soporte sin frenar el delivery. [CL09-P, p. 10]

**Advertencia (conocimiento general):** en SAFe, PI suele significar *Program Increment*, rebautizado *Planning Interval* en versiones recientes. La diapositiva lo expande como *Product Increments*. Ver [Dudas y conflictos](../dudas-y-conflictos.md).

## Por qué evaluar y qué debe responder la evaluación

Evaluar sirve para asegurar la **robustez** del diseño. Una evaluación permite: [CL09-P, p. 12]

- usar **métodos repetibles** y bien estructurados, que reducen o mitigan los riesgos técnicos del producto en forma temprana;
- asegurar que la arquitectura es **correcta**, es decir, que está alineada con los requerimientos no funcionales.

Se espera que el resultado responda: [CL09-P, p. 13]

1. si la arquitectura es **apropiada** para los requerimientos planteados;
2. si hay **más de una** arquitectura candidata, cuál es la adecuada;
3. en qué grado se **cumplen los atributos de calidad**;
4. qué **riesgos** potenciales hay.

## Técnicas de evaluación

La clase clasifica las técnicas en dos ramas: [CL09-P, p. 14]

| Rama | Técnicas |
|---|---|
| Cualitativas | Escenarios, checklists, cuestionarios |
| Cuantitativas | Métricas, prototipos, simulaciones, experimentos, modelos matemáticos |

### Escenarios

Un **escenario** es una breve narrativa de una situación potencial que el sistema debe enfrentar, desde el punto de vista de un stakeholder: usuario final, desarrollador, devops, etc. Se formula como «¿qué pasa si…?». Por ejemplo: dos usuarios quieren comprar el mismo ítem, 5000 usuarios se conectan a la vez o se corta internet. La diapositiva lo rotula «modelo de escenarios liviano» y remite a *Scenario-Based Analysis of Software Architecture*, de Kazman et al. [CL09-P, p. 15]

### Checklists y cuestionarios

Son listas de **criterios** que la arquitectura debe cumplir: un evaluador los califica (checklist) o los responde (cuestionario). [CL09-P, p. 16] El ejemplo es el *EA Design Review Checklist* de Harvard. Sus criterios de seguridad y de experiencia de usuario se marcan con MUST o SHOULD y se aplican según el tipo de solución: desarrollada, licenciada en la nube propia, alojada por el proveedor o SaaS. Algunos ejemplos: integrarse con el single sign-on institucional, autorizar por roles según el principio de menor privilegio y cumplir la política de accesibilidad. [CL09-P, p. 16] **Conocimiento general:** MUST indica un requisito obligatorio y SHOULD, uno recomendado.

### Métricas

| Atributo | Métricas propuestas |
|---|---|
| Availability | SLA, SLO, SLI |
| Reliability, fault tolerance | Cantidad de fallas, MTBF, MTTR |
| Performance | Tiempo de respuesta |
| Scalability | Cantidad de usuarios concurrentes |
| Maintainability | *Lead time for changes*, MTTR |
| Security | Cantidad de incidentes de seguridad |

La tabla reproduce [CL09-P, p. 17]. Las siglas de disponibilidad se encadenan: [CL09-P, p. 17]

- **SLI (Service Level Indicator):** métrica concreta y cuantificable.
- **SLO (Service Level Objective):** objetivo o meta que se fija para un SLI.
- **SLA (Service Level Agreement):** acuerdo formal y contractual entre proveedor y cliente; es un SLO más penalidades.

**Conocimiento general:** MTBF es el tiempo medio entre fallas y MTTR, el tiempo medio de reparación o recuperación. Un ejemplo de la cadena: el SLI es el porcentaje de requests exitosos; el SLO, «99,9 % mensual»; y el SLA, ese mismo compromiso firmado con una bonificación si no se cumple.

### Prototipos, simulaciones y experimentos

La diapositiva los marca como «CARO ++». [CL09-P, p. 18]

- **Simulación:** software que permite diseñar la arquitectura, típicamente en un DSL, y evaluar su comportamiento frente a distintos escenarios. Ejemplo: Palladio.
- **Experimento:** software diseñado para probar una **hipótesis** específica sobre el comportamiento de la arquitectura.
- **Prototipo:** software que constituye una versión preliminar de la arquitectura y que puede **evolucionar** hacia versiones posteriores.

### Modelos matemáticos

La diapositiva los marca como «CARO ++++». [CL09-P, p. 19]

- **Software reliability growth models (SRGM):** modelos de fallas y recuperación basados en análisis probabilístico de fallas y en distintos esquemas de interacción entre componentes.
- **Software Architecture-based Performance Analysis:** analiza la respuesta en throughput, uso de recursos o tiempo de respuesta.
- Su complejidad y esfuerzo justifican usarlos solo en casos de **alta criticidad**: sistemas médicos, aviones, misiones espaciales.

**Inferencia:** el material no rotula el costo de escenarios, checklists ni métricas. Las marcas «CARO» sugieren una escala de costo que crece desde las técnicas cualitativas hacia los modelos matemáticos, en paralelo con la criticidad del sistema.

## Metodologías basadas en escenarios

| Método | Año | Foco | Esfuerzo |
|---|---|---|---|
| SAAM (*Scenario-based Software Architecture Analysis Method*) | 1993 | Verificar supuestos básicos de la arquitectura contra los documentos principales que describen las propiedades deseadas | — |
| ATAM (*Architecture Tradeoff Analysis Method*) | 2000 | Cómo compiten distintos atributos para lograr la arquitectura deseada; es el «gold standard» | 20 a 30 días/hombre |
| Lightweight ATAM | — | Similar a ATAM, en versión recortada | Un día o medio día |

La tabla sintetiza [CL09-P, p. 20]. No son las únicas: existen numerosas instancias de revisión, según la metodología usada. La diapositiva agrupa estos métodos bajo el rótulo «modelo de escenarios pesado». [CL09-P, p. 20] **Inferencia:** el contraste con el «modelo liviano» de la página 15 distingue el escenario suelto, una técnica rápida, del método estructurado que organiza a stakeholders, escenarios y análisis.

## ATAM

ATAM fue diseñado por el SEI (*Software Engineering Institute*, Carnegie Mellon University). Usa **cuestionarios y escenarios**, se enfoca en los **atributos de calidad** y es esencialmente **cualitativo**: genera tendencias. [CL09-P, p. 21] Su diagrama resume el análisis así: [CL09-P, p. 21]

- **Entradas:** escenarios de alta prioridad, preguntas específicas por atributo y enfoques arquitectónicos.
- **Salidas:** puntos de sensibilidad, puntos de trade-off y riesgos.

### Repaso de atributos de calidad

Antes de las fases, la clase repasa los atributos agrupados en cuatro categorías. La diapositiva lleva la nota «Ojo: Esto implementa Parcializable». **Inferencia:** la cátedra lo señala como contenido evaluable. [CL09-P, p. 22]

| Categoría | Atributo | Qué abarca |
|---|---|---|
| Funcionamiento | Rendimiento (*performance*) | Tiempo de respuesta, throughput, latencia |
| Funcionamiento | Disponibilidad (*availability*) | Tiempo en línea, tolerancia a fallos, redundancia |
| Funcionamiento | Seguridad (*security*) | Confidencialidad, integridad, autenticación, autorización |
| Funcionamiento | Escalabilidad (*scalability*) | Capacidad de crecer en volumen de usuarios o datos |
| Funcionamiento | Interoperabilidad (*interoperability*) | Integración con otros sistemas |
| Funcionamiento | Administrabilidad (*manageability*) | Facilidad para configurar, monitorear y operar el sistema en producción |
| Funcionamiento | Confiabilidad (*reliability*) | Funcionar de manera consistente y recuperarse de fallos sin pérdida de datos ni interrupciones críticas |
| Usuario | Usabilidad (*usability*) | Facilidad de aprendizaje, eficiencia de uso |
| Diseño | Modificabilidad / mantenibilidad (*modifiability*) | Facilidad para cambiar, reparar o evolucionar el sistema |
| Diseño | Portabilidad (*portability*) | Facilidad para mover el sistema a otro entorno tecnológico |
| Diseño | Reusabilidad (*reusability*) | Aprovechar componentes en otros contextos |
| Sistema | Testabilidad (*testability*) | Facilidad para validar requisitos |

La tabla reproduce [CL09-P, p. 22]. **Advertencia:** este repaso es un subconjunto de la clasificación de la clase 7, con algunas diferencias. [CL07-P, p. 21]

- La categoría *run-time* se llama «Funcionamiento».
- Gestionabilidad aparece como «administrabilidad».
- La tolerancia a fallos se incluye dentro de disponibilidad, en vez de figurar como atributo propio.
- No aparecen customizabilidad, precisión, auditabilidad, integridad conceptual, soportabilidad ni accesibilidad.

Ver [atributos de calidad](arquitectura-y-atributos-de-calidad.md#atributos-de-calidad) y [Dudas y conflictos](../dudas-y-conflictos.md).

### Fases

| Fase | Nombre | Momento | Contenido |
|---|---|---|---|
| 0 | Presentación | Kickoff | Se acuerda la evaluación y se presenta el equipo |
| 1 | Evaluación inicial | Ejecución | Presentación (ATAM, drivers del negocio, arquitectura); investigación y análisis (identificación de enfoques arquitectónicos, generación del árbol de utilidad, análisis de los enfoques) |
| 2 | Evaluación completa | Ejecución | *Testing*: brainstorming y priorización de escenarios; análisis de los enfoques arquitectónicos |
| 3 | Resultados | Ejecución | *Reporting*: presentación de resultados |

La tabla combina [CL09-P, p. 23]; [CL09-P, p. 24]; [CL09-P, p. 25].

**Inferencia:** las fases 1 y 2 contienen los nueve pasos que enumera la tabla de Lightweight ATAM: [CL09-P, p. 25]; [CL09-P, p. 31]

1. Presentar ATAM.
2. Presentar los business drivers.
3. Presentar la arquitectura.
4. Identificar los enfoques de arquitectura.
5. Generar el árbol de utilidad.
6. Analizar los enfoques de arquitectura.
7. Hacer brainstorming y priorizar escenarios.
8. Volver a analizar los enfoques de arquitectura.
9. Presentar los resultados.

El análisis aparece dos veces: primero sobre los escenarios del árbol de utilidad y después sobre los que surgen del brainstorming.

### Fase 0: roles del equipo

| Rol | Responsabilidad |
|---|---|
| Evaluadores | Equipo de expertos en arquitectura que conduce la evaluación |
| Redactores | Documentar todo lo que surge en la sesión: notas, actas, escenarios y resultados |
| Inquisidor | Hacer preguntas difíciles y profundas |
| Moderador (*process enforcer*) | Facilitar la sesión para que sea productiva y ordenada |
| Decision makers (PM y arquitecto) | Priorizar atributos de calidad y tomar decisiones sobre el alcance |
| Stakeholders | Aportar perspectivas diversas sobre el sistema |

La tabla sintetiza [CL09-P, p. 24].

### Fase 1: árbol de utilidad

El **árbol de utilidad** sirve para enfocar el trabajo. [CL09-P, p. 26] Su estructura es esta:

- **Raíz:** *Utility*.
- **Nodos de alto nivel:** atributos de calidad.
- **Nodos intermedios:** características (*features*) que contribuyen al atributo.
- **Hojas:** escenarios.

Cada hoja se anota con el par **[importancia, dificultad]**, y cada valor puede ser alto, medio o bajo (H, M, L). La importancia es para los stakeholders; la dificultad, para lograr el objetivo. [CL09-P, p. 26]

| Atributo | Nodos intermedios | Hoja (escenario) | [I, D] |
|---|---|---|---|
| Performance | Data latency; transaction throughput | Minimizar la latencia de almacenamiento en la base de clientes a 200 ms | (M, L) |
| Performance | | Entregar video en tiempo real | (H, M) |
| Modifiability | New product categories; change COTS | Agregar middleware CORBA en menos de 20 persona-mes | (L, H) |
| Modifiability | | Cambiar la interfaz web en menos de 4 persona-semana | (H, L) |
| Availability | H/W failure; COTS S/W failures | Ante un corte de energía en el sitio 1, redirigir el tráfico al sitio 2 en menos de 3 s | (L, H) |
| Availability | | Reiniciar tras una falla de disco en menos de 5 min | (M, M) |
| Availability | | Detectar y recuperar una falla de red en menos de 1,5 min | (H, M) |
| Security | Data confidentiality; data integrity | Transacciones con tarjeta de crédito seguras el 99,999 % del tiempo | (L, H) |
| Security | | Autorización de la base de clientes funcionando el 99,999 % del tiempo | (L, H) |

La tabla traduce el ejemplo en inglés de [CL09-P, p. 26]. En la figura, las hojas de cada atributo cuelgan de un solo nodo intermedio: data latency, change COTS, H/W failure y data confidentiality. Los demás nodos intermedios no muestran hojas.

**Inferencia:** los pares sirven para priorizar. Un escenario (H, H) o (H, M) es muy importante y difícil, así que conviene analizarlo primero. Uno (H, L) es importante pero fácil de lograr. Uno (L, H) es caro y aporta poco valor, por lo que conviene revisar si justifica su costo. Las hojas son escenarios medibles —con umbrales en ms, minutos o persona-mes—, no deseos vagos.

### Fase 2: brainstorming y priorización de escenarios

Participan los stakeholders, que generan nuevos escenarios por brainstorming; la diapositiva lo vincula con el «modelo de escenarios liviano». Después los escenarios se priorizan por votación: cada stakeholder vota con un número fijo de votos. [CL09-P, p. 27]

### Fase 2: análisis de los enfoques arquitectónicos

El análisis identifica el enfoque, recorre los escenarios del árbol de utilidad y reporta cuatro tipos de hallazgo: [CL09-P, p. 28]

| Hallazgo | Pista del material | Definición (conocimiento general, SEI) |
|---|---|---|
| Riesgo | — | Decisión arquitectónica potencialmente problemática respecto de algún atributo de calidad |
| No riesgo | Frases como «no requiere…», «alcanza con…», «se podrán cambiar…» | Decisión adecuada y considerada segura para el atributo analizado |
| Punto sensible | — | Propiedad de uno o más componentes que es crítica para lograr la respuesta de un atributo |
| Trade-off | Entre atributos de calidad | Punto sensible que afecta a más de un atributo: mejora uno y empeora otro |

La columna de pistas reproduce [CL09-P, p. 28]. Las definiciones no están en la diapositiva y se marcan como conocimiento general. La bibliografía de la cátedra las respalda: los riesgos son decisiones arquitectónicas que pueden tener consecuencias indeseadas, y los puntos sensibles y trade-offs son decisiones con un efecto marcado sobre uno o más atributos de calidad. [B03, p. 39]

**Ejemplo (inferencia):** «cifrar todas las comunicaciones entre servicios» es un punto sensible para la seguridad. También es un trade-off, porque agrega latencia y empeora la performance. «El volumen previsto alcanza con una sola instancia de base de datos» se formula como un no riesgo.

### Fase 3: resultados

Se genera un **reporte final** con estas partes: [CL09-P, p. 29]

- resumen;
- descripción de ATAM;
- descripción de los business drivers y de la arquitectura;
- lista de escenarios de las fases 1 y 2;
- árbol de utilidad;
- análisis de las fases 1 y 2: enfoques arquitectónicos, decisiones, riesgos y no riesgos, puntos sensibles y trade-offs.

## ATAM en la práctica: caso de estudio de Hariharan

La cátedra entregó una presentación de V. Hariharan (BITS Pilani) que aplica ATAM a casos reales, `B03`. Complementa la clase 9 con ejemplos concretos de cada salida del método.

### Qué tipo de revisión corresponde

Los proyectos de software tienen distintos «colores y formas», y la técnica de revisión se ajusta a cada uno: [B03, p. 2]; [B03, p. 3]

| Proyecto | Ejemplo | Revisión |
|---|---|---|
| Mejora chica | Mejorar el tiempo de respuesta | Autoevaluación |
| Mejoras funcionales | Agregar un módulo de fidelización | Revisión de pares |
| Sistema complejo de misión crítica | Construir un sistema satelital | Revisión externa |

En ATAM, los revisores son **externos**, de otra organización, para aportar una opinión imparcial y una perspectiva independiente. [B03, p. 5] El método supone que los revisores no conocen los objetivos de negocio ni la arquitectura del sistema, y sirve para dominios como finanzas, defensa o automotriz. [B03, p. 33]

### Tres momentos del proceso

| Momento | Duración | Participantes | Contenido |
|---|---|---|---|
| Vista macro (*macro view*) | 1–2 días | Sponsor, arquitecto y equipo evaluador | Objetivos y funciones de negocio, enfoque arquitectónico, árbol de utilidad |
| Vista detallada (*detailed view*) | 2 días | Lo anterior más todos los stakeholders | Escenarios detallados, priorización por votación, tácticas usadas |
| Hallazgos (*findings*) | 1 semana | Equipo evaluador | Riesgos, puntos sensibles, trade-offs |

La tabla combina [B03, p. 6]; [B03, p. 7]; [B03, p. 9].

Los ejemplos de hallazgos son estos: [B03, p. 10]

- **Riesgo:** ciertos servicios de acceso a datos no son suficientemente seguros, y un atacante podría obtener datos privados como la fecha de nacimiento.
- **Punto sensible:** la interfaz de un sistema de comercio electrónico con un gateway de telecomunicaciones es sensible a cambios en la interfaz del gateway.
- **Trade-off:** varios niveles de seguridad, como contraseña de usuario, contraseña de transacción y OTP, pueden perjudicar la usabilidad.

El ejemplo de la vista macro es un **sistema judicial**. Su objetivo es mejorar la eficiencia de los tribunales. Sus funciones son presentar una causa, tramitar los procedimientos y dictar sentencia, y sus atributos de calidad son la seguridad de la información y la usabilidad. Su árbol de utilidad anota cada escenario con **valor de negocio** e **impacto en la arquitectura** (alto, medio o bajo). [B03, p. 8] **Inferencia:** es el mismo par que la clase llama [importancia, dificultad]. [CL09-P, p. 26]

### Fases, participantes y salidas

| Fase | Actividad | Participantes | Duración |
|---|---|---|---|
| 0 | Asociación y preparación | Equipo evaluador y decisores del proyecto | Pocas semanas |
| 1 | Evaluación | Lo anterior más el arquitecto | 1–2 días |
| 2 | Evaluación | Lo anterior más los stakeholders | 2 días |
| 3 | Seguimiento: preparar el reporte | Equipo evaluador | 1 semana |

La tabla traduce [B03, p. 36]. Los pasos se reparten así: 1 a 6 en la fase 1, 7 y 8 en la fase 2 y el paso 9, presentar resultados, en la fase 3. [B03, p. 37] Esto coincide con la secuencia de la clase. [CL09-P, p. 25]

Participan cinco roles: [B03, p. 34]

- el equipo evaluador;
- los decisores del proyecto, como el stakeholder de negocio o el project manager;
- los stakeholders de la arquitectura: usuarios, desarrolladores, testers y mantenimiento;
- un **escriba de escenarios**, que anota los escenarios discutidos;
- un **escriba de actas**, que registra objetivos, enfoque arquitectónico y observaciones.

Las salidas de ATAM son estas: [B03, p. 35]; [B03, p. 39]

- una presentación concisa de la arquitectura y los objetivos de negocio;
- los escenarios de atributos de calidad priorizados;
- los riesgos y no riesgos;
- los **temas de riesgo** (*risk themes*), es decir, debilidades sistémicas de la arquitectura;
- el mapeo de decisiones arquitectónicas a escenarios;
- los puntos sensibles y trade-offs.

El flujo conceptual del SEI une los *business drivers* con los atributos de calidad y los escenarios, y la arquitectura con los enfoques y las decisiones. Ambas ramas entran al **análisis**, que produce trade-offs, puntos sensibles, no riesgos y riesgos. Los riesgos se destilan en temas de riesgo, que vuelven a impactar sobre los drivers y la arquitectura. [B03, p. 38]

### Caso CAAS: aviónica de Rockwell Collins

El *Common Avionics Architecture System* (CAAS) integra en la cabina varios subsistemas: comunicaciones, navegación, armas y sensores de misión. Debe servir a distintos tipos de helicóptero. [B03, p. 13]; [B03, p. 14] Antes había dos sistemas propietarios distintos, y eso exigía más esfuerzo para mejorarlos y mantenerlos. [B03, p. 15]

- **Objetivo:** un sistema escalable para las cabinas de varios helicópteros, más fácil de mantener, que admita mejoras de terceros y ofrezca una apariencia común. [B03, p. 16]
- **Enfoque:** una única arquitectura de aviónica abierta y común para todas las plataformas, que reduzca el costo total de propiedad. [B03, p. 17]
- **Atributos de calidad:** disponibilidad, performance y mantenibilidad. [B03, p. 18]

Los enfoques arquitectónicos identificados fueron cinco, cada uno con los atributos que favorece: [B03, p. 41]

| Enfoque | Descripción | Atributos |
|---|---|---|
| Particionado | Memoria y tiempo de CPU asignados por partición | Disponibilidad, safety, modificabilidad, testabilidad, mantenibilidad |
| Encapsulamiento | Aísla particiones; entre ellas solo se comparte estado por la red, mediante RSI y RSP | Modificabilidad, disponibilidad |
| Estrategia de interfaces | Acceso a componentes solo por sus interfaces | Modificabilidad, mantenibilidad |
| Capas | Aíslan los servicios gráficos de alto nivel | Portabilidad, modificabilidad |
| Procesamiento distribuido | Cliente-servidor para desacoplar partes, más broadcast periódico | Mantenibilidad, modificabilidad |

Los diagramas muestran tres particiones —gráficos, aplicación y comunicación— conectadas por interfaces, sobre capas en un sistema POSIX. Varias de esas estructuras se distribuyen con **transparencia de ubicación** y **software redundante maestro-esclavo**. [B03, p. 19]; [B03, p. 20]

El **árbol de utilidad** de disponibilidad baja a tres preocupaciones: [B03, p. 21]

- que el software no se caiga, incluso ante datos inválidos o un corte de energía de 1,9 s;
- una degradación elegante ante fallas, como la pérdida del Doppler o la caída de una partición;
- ninguna degradación ante fallas con componentes redundantes.

En la fase 2, los stakeholders generaron escenarios y los votaron. Los más votados fueron dos: [B03, p. 22]

- que ningún punto único de falla afecte la seguridad o la performance (10 votos);
- que el 75 % del CAAS se construya con componentes reutilizados (9 votos).

Las observaciones del análisis fueron estas: [B03, p. 23]; [B03, p. 24]

- **Riesgo:** no hay *hooks* para conectar simuladores, así que el software no puede manejar a la vez el simulador y el helicóptero real.
- **Punto sensible:** aislar las dependencias del sistema operativo mejora la portabilidad.
- **Trade-off:** dejar que el piloto fije parámetros, como el límite de temperatura de la turbina, aumenta la flexibilidad pero reduce la seguridad.
- **Tema de riesgo:** varios escenarios trataban sobre performance, pero los requisitos de performance no estaban explicitados.

### Caso Battlefield Control System

La revisión externa también puede revelar riesgos no imaginados. [B03, p. 25] Un sistema de control de batalla coordina en tiempo real a un comandante con varios soldados y con sistemas externos de comando y control. [B03, p. 26] Durante la evaluación se descubrió que el nodo de control y su respaldo intercambiaban mucho más datos que el resto. Ese patrón de comunicación distintivo permitiría al enemigo detectarlos y atacarlos. [B03, p. 27]

**Conclusión del autor:** en sistemas grandes, complejos y de misión crítica, la revisión externa aporta mucho valor y reúne a todos los stakeholders. Además de identificar riesgos, deja artefactos útiles: árbol de utilidad, escenarios y diagramas de arquitectura. [B03, p. 28]

### Autoevaluación: checklists y modelos

Para revisiones chicas, la presentación propone **checklists**: [B03, p. 30]

- **Disponibilidad:** ¿hay mecanismos para detectar fallas, conmutar a un respaldo, informar al cliente y guardar el estado periódicamente?
- **Performance:** ¿cómo se agregan y quitan recursos dinámicamente? ¿Cómo se evita el cuello de botella de un recurso común?

También propone **modelos** simples, que funcionan como técnicas cuantitativas: [B03, p. 31]; [B03, p. 32]

- **Disponibilidad con respaldo en caliente:** si cada servidor falla con probabilidad 0,01, la probabilidad de que fallen ambos es 0,01 × 0,01 = 0,0001. La disponibilidad sube del 99 % al 99,99 %.
- **Latencia en serie:** la latencia que percibe el cliente es la suma de los módulos que atraviesa la solicitud, por ejemplo 0,1 + 0,2 + 0,3 = 0,6 ms. La figura usa 1, 2 y 3 s, con un total de 6 s. Ver [Dudas y conflictos](../dudas-y-conflictos.md).

**Inferencia:** el modelo de disponibilidad supone fallas independientes. Si ambos servidores comparten una causa de falla, como el mismo centro de datos, la disponibilidad real es menor.

Para aplicar ATAM a un caso completo, ver el [caso HealthCare.gov](caso-healthcare-gov.md).

## Lightweight ATAM

Lo desarrollaron los mismos autores de ATAM, como una alternativa con una relación costo/beneficio razonable. Es útil para revisiones intermedias de QA y puede realizarse íntegramente con el equipo del proyecto, lo que acelera el arranque. No produce un reporte final, sino solo una minuta. Sus contras son un análisis menos profundo, menos ideas innovadoras y menor objetividad. [CL09-P, p. 30]

| Paso | Tiempo | Descripción |
|---|---|---|
| Presentar ATAM | 0 h | Omitido |
| Presentar business drivers | 0,25 h | Los participantes conocen el contexto |
| Presentar arquitectura | 0,5 h | Vistas básicas, con uno o dos escenarios ejecutados sobre ellas |
| Identificar enfoques de arquitectura | 0,25 h | Solo se analizan enfoques relacionados con atributos de calidad específicos |
| Generar árbol de utilidad | 0,5 a 1,5 h | Debería existir un árbol y escenarios previos; si no, puede llevar más tiempo |
| Analizar enfoques de arquitectura | 2 a 3 h | Mapear en la arquitectura los escenarios de mayor prioridad; es la tarea más importante |
| Brainstorming y priorización de escenarios | 0 h | Omitido: los escenarios se analizan al generar el árbol de utilidad |
| Analizar enfoques de arquitectura | 0 h | Omitido |
| Presentar resultados | 0,5 h | Enfoque resumido, sin reporte formal |
| **Total** | **4 a 6 h** | |

La tabla reproduce [CL09-P, p. 31]. Es consistente con el «día o medio día» de [CL09-P, p. 20].

| Aspecto | ATAM | Lightweight ATAM |
|---|---|---|
| Esfuerzo | 20 a 30 días/hombre [CL09-P, p. 20] | 4 a 6 horas [CL09-P, p. 31] |
| Quién evalúa | Equipo de evaluadores expertos, con roles definidos [CL09-P, p. 24] | Puede hacerlo íntegramente el equipo del proyecto [CL09-P, p. 30] |
| Brainstorming de stakeholders | Sí, en la fase 2 [CL09-P, p. 27] | Omitido [CL09-P, p. 31] |
| Resultado | Reporte final [CL09-P, p. 29] | Minuta [CL09-P, p. 30] |
| Costo de la reducción | — | Menor profundidad, menos ideas innovadoras, menor objetividad [CL09-P, p. 30] |

## Reflexión final

La clase cierra con cinco ideas: [CL09-P, p. 32]

- YAGNI vs. BDUF es un trade-off.
- La arquitectura **debe** evaluarse.
- El momento y la técnica de evaluación se eligen según el proyecto y la metodología.
- ATAM sigue siendo la técnica de referencia.
- Las metodologías ágiles usan ceremonias y técnicas más ligeras para evaluar arquitecturas emergentes.

## Actividades de clase

- **Actividad 1:** cada grupo trabaja sobre su producto. Debe definir un pipeline dataflow interno, seleccionar un estilo distribuido para la comunicación —broker, pub-sub, etc.— y seleccionar el manejo de eventos. [CL09-P, p. 2]
- **Actividad 2 (definiciones de arquitectura):** documentar los atributos de calidad prioritarios en un árbol de utilidad, con atributos y escenarios. Documentar al menos dos vistas del modelo 4+1, con uno o dos diagramas por vista. Incorporar los estilos definidos en la Actividad 1, que la diapositiva ubica en «la clase pasada». [CL09-P, p. 33]

**Inferencia:** la Actividad 2 integra las clases 7, 8 y 9:

- atributos de calidad → árbol de utilidad;
- modelo 4+1 → vistas;
- estilos → decisiones que se evalúan.

## Conexiones

- El árbol de utilidad baja a escenarios medibles los [atributos de calidad](arquitectura-y-atributos-de-calidad.md) y sus trade-offs. Los ASR y los escenarios de alta prioridad cumplen un papel análogo al de los drivers de ADD. **Inferencia.**
- Los escenarios de ATAM retoman la vista «+1» del [modelo 4+1](documentacion-de-arquitectura-y-modelo-4-mas-1.md), que Kruchten usa para descubrir y validar la arquitectura. [B01, p. 10]
- Los enfoques arquitectónicos que ATAM analiza incluyen los [estilos arquitectónicos](estilos-arquitectonicos.md) elegidos. **Inferencia.**
- BDUF, YAGNI, sprint-zero y SAFe ubican la arquitectura dentro de las [metodologías clásicas y ágiles](metodologias-clasicas-y-agiles.md).
- El gráfico de Boehm y Turner usa el factor RESL de COCOMO II; conecta la inversión en arquitectura con la [estimación](estimacion-de-proyectos.md). [CL09-P, p. 4]
- YAGNI se apoya en refactorizar para eliminar [deuda técnica](calidad-de-software.md) [CL09-P, p. 3], y Lightweight ATAM funciona como revisión intermedia de QA. [CL09-P, p. 30]
- El [caso HealthCare.gov](caso-healthcare-gov.md) es la consigna para simular las fases 0 y 1 de ATAM sobre un sistema real que falló en su lanzamiento. [CASO-HCG, p. 8]; [CASO-HCG, p. 9]
- La elección del mecanismo de [persistencia](persistencia.md) es una decisión arquitectónica con trade-offs evaluables. **Inferencia.**
