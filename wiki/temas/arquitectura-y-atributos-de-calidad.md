# Arquitectura y atributos de calidad

> **Alcance:** esta clase es posterior al recorte del primer parcial y no aparece en él. Ver [alcance del primer parcial](../parcial-1-alcance.md). Fuente principal: presentación de la clase 7 `CL07-P`.

## Qué se entiende por arquitectura

Según IEEE 1471/ISO 42010, la arquitectura de software es la organización fundamental de un sistema, expresada en sus componentes, las relaciones entre ellos y con el entorno, y los principios y lineamientos que gobiernan su diseño y evolución. [CL07-P, p. 3]

| Elemento | Significado en la definición | Ejemplos del material |
|---|---|---|
| Organización fundamental | Estructura de alto nivel del sistema | — |
| Componentes | Piezas del sistema | Módulos, servicios, capas, bases de datos |
| Relaciones | Formas de interacción | Interfaces, protocolos, dependencias |
| Entorno | Otros sistemas con los que se comunica | Sistemas propios o de terceros |
| Principios | Decisiones que orientan construcción y mantenimiento | Microservicios, separación en capas, stack tecnológico |

La tabla sintetiza [CL07-P, p. 3]. La definición no se limita a un diagrama de cajas: incluye los principios que justifican la estructura y que deben sostenerse mientras el sistema evoluciona.

## Architecture Business Cycle

Los requerimientos no determinan del todo la arquitectura. Esta resulta de influencias técnicas, sociales, culturales y de negocio, y a su vez influye sobre esos mismos aspectos en arquitecturas futuras. [CL07-P, p. 2] El diagrama del Architecture Business Cycle (ABC) muestra que stakeholders y organización desarrolladora producen requerimientos de calidad; junto con el entorno técnico y la experiencia del arquitecto, esas influencias llegan al arquitecto, que define una arquitectura, y de ella surge el sistema. [CL07-P, p. 4]

| Influencia | Cómo actúa sobre la arquitectura |
|---|---|
| Stakeholders | Tienen expectativas y restricciones diversas, a veces contradictorias; el arquitecto debe detectarlas y buscar el mejor compromiso posible. [CL07-P, p. 5] |
| Organización desarrolladora | El negocio inmediato busca aprovechar inversiones en sistemas existentes; el negocio a largo plazo invierte en infraestructura; la estructura organizacional aporta conocimientos previos, metodologías y herramientas. [CL07-P, p. 6] |
| Experiencia del arquitecto | Tiende a reutilizar estilos y patrones que tuvieron éxito, a aplicar conocimientos recién adquiridos y a decidir según su formación. [CL07-P, p. 7] |
| Ambiente tecnológico | La tecnología disponible, los estándares de la industria y las técnicas de ingeniería de software condicionan las decisiones. [CL07-P, p. 8] |

**El ciclo se cierra:** una vez creada la arquitectura y desarrollado el sistema, ambos afectan la estructura y los objetivos de la organización, los requerimientos de los clientes y la experiencia de los arquitectos en sistemas posteriores, y generan tecnología que se aprovecha en proyectos futuros. [CL07-P, p. 9]; [CL07-P, p. 10]

**Inferencia:** el ABC explica por qué dos equipos con los mismos requerimientos pueden llegar a arquitecturas distintas: cambian la organización, la experiencia y el entorno técnico, no solo la especificación.

## La arquitectura dentro del proceso

El material ordena la creación de software alrededor de la arquitectura: caso de negocio, entendimiento de requerimientos, creación o selección de la arquitectura, representación y comunicación, análisis y evaluación, implementación basada en la arquitectura y validación del sistema contra ella. [CL07-P, p. 12]

Los requerimientos se distinguen en dos ejes: de usuario o de sistema, y funcionales o no funcionales. [CL07-P, p. 13] Los atributos de calidad se ubican del lado no funcional: son aspectos que, en general, no afectan directamente la funcionalidad, pero definen la calidad y las características que el sistema debe soportar. [CL07-P, p. 15]

El desarrollo iterativo permite entender el problema de forma incremental mediante refinamientos sucesivos, facilita la retroalimentación del usuario, fija metas específicas para el equipo y mide el progreso según avanzan las implementaciones. [CL07-P, p. 23]

## Modelo de calidad ISO

La diapositiva rotulada «ISO 25000 - Calidad en el Software» presenta la calidad interna/externa en seis características, cada una con subcaracterísticas: [CL07-P, p. 14]

| Característica | Subcaracterísticas |
|---|---|
| Funcionalidad | Idoneidad, precisión, interoperabilidad, seguridad, cumplimiento de la funcionalidad |
| Fiabilidad | Madurez, tolerancia a fallos, capacidad de recuperación, cumplimiento de la fiabilidad |
| Usabilidad | Inteligibilidad, facilidad de aprendizaje, operabilidad, atractividad, cumplimiento de la usabilidad |
| Eficiencia | Comportamiento en el tiempo, utilización de recursos, cumplimiento de la eficiencia |
| Mantenibilidad | Analizabilidad, cambiabilidad, estabilidad, capacidad de ser probado, cumplimiento de la mantenibilidad |
| Portabilidad | Adaptabilidad, facilidad de instalación, coexistencia, intercambiabilidad, cumplimiento de la portabilidad |

**Advertencia:** los apuntes de la clase 6 atribuyen a ISO/IEC 25010 ocho características, que suman seguridad y compatibilidad. [CL06-A, p. 1] En el diagrama de la clase 7, la seguridad aparece solo como subcaracterística de funcionalidad y no figura compatibilidad. **Conocimiento general:** las seis características del diagrama coinciden con ISO/IEC 9126, la norma que precedió a la familia ISO/IEC 25000. La incompatibilidad está registrada en [Dudas y conflictos](../dudas-y-conflictos.md).

## Atributos de calidad

La clase define seis atributos en castellano: [CL07-P, p. 17]

- **Disponibilidad:** porcentaje de tiempo en el que el sistema está funcionando.
- **Modificabilidad:** costo de modificar o agregar funcionalidades.
- **Performance:** grado en que el sistema realiza una funcionalidad específica dentro de una restricción de tiempo.
- **Seguridad:** capacidad del sistema para prevenir usos no autorizados.
- **Verificabilidad:** facilidad con que el sistema puede probarse de forma completa.
- **Usabilidad:** eficacia de la interfaz humana del software.

Después agrupa los atributos en cuatro categorías: [CL07-P, p. 18]; [CL07-P, p. 19]; [CL07-P, p. 20]; [CL07-P, p. 21]

| Categoría | Atributo | Idea central |
|---|---|---|
| Run-time | Disponibilidad | Proporción del tiempo en que el sistema funciona |
| Run-time | Tolerancia a fallos | Seguir respondiendo ante fallas de componentes, aunque sea de forma degradada |
| Run-time | Interoperabilidad | Operar comunicándose e intercambiando información con sistemas externos de terceros |
| Run-time | Gestionabilidad | Facilidad de administración mediante instrumentación para monitoreo, depuración y ajuste de performance |
| Run-time | Customizabilidad | Posibilidad de que el usuario cambie apariencia o comportamiento hasta cierto grado |
| Run-time | Performance | Capacidad de respuesta para ejecutar una acción en un intervalo de tiempo |
| Run-time | Precisión | Obtener resultados numéricos con el nivel de detalle suficiente |
| Run-time | Confiabilidad | Permanecer operativo a lo largo del tiempo |
| Run-time | Escalabilidad | Absorber aumentos de carga sin perder performance, o poder ampliarse fácilmente |
| Run-time | Auditabilidad | Revisar registros y actividades para comprobar seguridad e integridad de datos |
| Run-time | Seguridad | Prevenir acciones maliciosas o accidentales fuera del uso previsto, y la divulgación o pérdida de información |
| Diseño | Integridad conceptual | Consistencia y coherencia del diseño global |
| Diseño | Mantenibilidad | Facilidad con que el sistema admite cambios |
| Diseño | Portabilidad | Usar el mismo sistema en distintos entornos |
| Diseño | Reusabilidad | Que componentes y subsistemas sirvan en otras aplicaciones y escenarios |
| Sistema | Soportabilidad | Brindar información útil para identificar y resolver problemas cuando falla |
| Sistema | Testeabilidad | Facilidad para crear criterios de prueba y ejecutarlos para verificar si se cumplen |
| Usuario | Accesibilidad | Que el sistema sea usable por la mayor cantidad posible de personas |
| Usuario | Usabilidad | Que la aplicación sea intuitiva y brinde una buena experiencia general |

Las definiciones de las páginas 18–20 están en inglés; la tabla las sintetiza en castellano.

**Distinción útil:** la disponibilidad mide *cuánto tiempo* el sistema está operativo; la tolerancia a fallos, *cómo se comporta* cuando falla un componente; la confiabilidad, *si se mantiene operativo* a lo largo del tiempo. [CL07-P, p. 18]; [CL07-P, p. 19]

## Attribute Driven Design, restricciones y drivers

En Attribute Driven Design (ADD), los requerimientos —alimentados por escenarios generales— entran al proceso junto con restricciones, requerimientos funcionales y requerimientos de calidad, cada uno en forma abstracta y concreta. El resultado es una arquitectura conceptual. [CL07-P, p. 16] **Inferencia:** el nombre indica que las decisiones de diseño se guían por los atributos de calidad y no solamente por la funcionalidad.

Las restricciones se dividen en dos grupos: [CL07-P, p. 22]

- **De negocio:** time to market, costo y ROI, tiempo del sistema en producción, mercado destino, plan de rollout e integración con sistemas legados.
- **De arquitectura:** integridad conceptual, correctitud y completitud, constructibilidad y robustez.

Los **drivers** de arquitectura son los escenarios funcionales y de atributos de calidad críticos y significativos que permiten modelar, comunicar y evaluar la arquitectura. [CL07-P, p. 24]

## Recomendaciones

Una diapositiva de tips propone comenzar con requerimientos funcionales, un acuerdo articulado, buena documentación, circulación entre los stakeholders, análisis de medidas cuantitativas aplicables y apertura a una implementación incremental. [CL07-P, p. 25] Otra recomienda módulos de características bien definidos, interfaces bien definidas por módulo, atributos de calidad logrados mediante tácticas conocidas, independencia de la especificación comercial de cada versión, separación entre módulos que producen datos y los que los consumen, diseño preparado para cambios en los procesos y un patrón simple de interacción. [CL07-P, p. 26]

## Todo es trade-off

La clase cierra con compromisos entre atributos: [CL07-P, p. 28]

| Tensión | Ejemplo del material | Pregunta de decisión |
|---|---|---|
| Seguridad vs. usabilidad | La autenticación de dos factores protege más, pero complica el ingreso | ¿Máxima seguridad o rapidez en una app bancaria? |
| Performance vs. mantenibilidad | El código optimizado al extremo cuesta entenderlo y mantenerlo | ¿Conviene exprimir la performance si después nadie puede tocar el código? |
| Disponibilidad vs. costo | «24/7 sin caídas» exige redundancia e infraestructura cara | ¿Vale la pena duplicar servidores para ganar 0,1 % de uptime? |
| Portabilidad vs. eficiencia | Correr en cualquier sistema operativo puede sacrificar optimizaciones | ¿Mejor que corra en todos lados aunque sea algo más lento? |
| Escalabilidad vs. complejidad | Diseñar para millones de usuarios desde el día uno puede ser innecesariamente caro | ¿Diseñar para el futuro hipotético o resolver el presente y refactorizar? |

Las actividades de clase piden detectar problemas asociados a la «sensación de mala calidad» en una aplicación conocida, clasificarlos en las categorías de atributos y argumentar por qué un atributo —tolerancia a fallos, mantenibilidad, testeabilidad o accesibilidad— sería el más crítico. [CL07-P, p. 11]; [CL07-P, p. 21]; [CL07-P, p. 27] **Inferencia:** el ejercicio muestra que ningún atributo es críticamente superior en abstracto; su prioridad depende de los drivers del sistema concreto.

## Conexiones

- Los atributos de calidad llevan al diseño la visión de producto de la [calidad de software](calidad-de-software.md), y la deuda técnica aparece cuando la mantenibilidad se sacrifica sin plan.
- La arquitectura se describe mediante vistas, como las del [modelo 4+1](documentacion-de-arquitectura-y-modelo-4-mas-1.md), y se diseña con [estilos arquitectónicos](estilos-arquitectonicos.md) que favorecen unos atributos a costa de otros.
- **Inferencia:** los trade-offs de disponibilidad o escalabilidad tienen costo directo, por lo que conviene hacerlos explícitos durante la [estimación](estimacion-de-proyectos.md).
