# Alcance del segundo parcial

Esta página registra el temario que presenta la cátedra en el repaso de la clase 12, titulado «Temas del Parcial». [CL12-REP, p. 1] A diferencia del primer parcial, no hay presentaciones depuradas ni una anotación que indique qué queda afuera: el repaso nombra temas por clase y muestra, como recordatorio, miniaturas de diapositivas de las clases 7 a 11. [CL12-REP, p. 2]; [CL12-REP, p. 11]

**Advertencias.**

- El repaso numera persistencia como **clase 10** y arquitecturas de integración como **clase 11**. [CL12-REP, p. 10]; [CL12-REP, p. 11] En el catálogo, las dos presentaciones tienen IDs `CL11-P` y `CL11-INT` por los nombres de archivo recibidos; los IDs no cambian.
- Los metadatos del PDF tienen fecha de creación 16/10/2025. **Inferencia:** puede ser el repaso del ciclo anterior reutilizado. Ver [Dudas y conflictos](dudas-y-conflictos.md).
- Que un tema no figure en el repaso **no confirma** que quede afuera. Las secciones «No aparece» de esta página son inferencias y no reemplazan una confirmación de la cátedra.

## Mapa del repaso

| Clase según el repaso | Qué nombra | Qué diapositivas muestra | Dónde estudiarlo |
|---|---|---|---|
| 7 — Atributos de calidad | Rol del arquitecto, requerimientos funcionales, requerimientos no funcionales y atributos de calidad [CL12-REP, p. 2] | Ninguna | [Arquitectura y atributos de calidad](temas/arquitectura-y-atributos-de-calidad.md) |
| 8 — Estilos de arquitectura | Modelo 4+1 con sus cinco vistas y los diagramas UML asociados [CL12-REP, p. 3] | Ninguna | [Documentación y modelo 4+1](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md) |
| 8 — Estilos de arquitectura | Dataflow, sistemas distribuidos, sistemas interactivos y sistemas basados en eventos [CL12-REP, p. 3] | `CL08-P`, pp. 26–28, 30–32, 35, 40, 42, 44 y 50, y una versión de la tabla de la p. 54 con otros ejemplos [CL12-REP, p. 4]; [CL12-REP, p. 5]; [CL12-REP, p. 6]; [CL12-REP, p. 7] | [Estilos arquitectónicos](temas/estilos-arquitectonicos.md) |
| 9 — Evaluación de arquitecturas | Sin lista de temas | `CL09-P`, pp. 14, 21, 24 y 25 [CL12-REP, p. 8]; [CL12-REP, p. 9] | [Técnicas de evaluación](temas/evaluacion-de-arquitecturas.md#técnicas-de-evaluación) y [el método ATAM](temas/evaluacion-de-arquitecturas.md#atam) |
| 10 — Persistencia | Sin lista de temas | `CL11-P`, pp. 7, 10, 11, 12, 15, 17 y 19 [CL12-REP, p. 10] | [Persistencia](temas/persistencia.md) |
| 11 — Arquitecturas de integración | Sin lista de temas | `CL11-INT`, pp. 10, 11 y 23 [CL12-REP, p. 11] | [Arquitecturas de integración](temas/arquitecturas-de-integracion.md) |

La correspondencia de las miniaturas se verificó renderizando las páginas de ambas fuentes. Las miniaturas son las diapositivas base, sin los globos y marcas que agregan las versiones 2026. Por ejemplo, las páginas 26–28 de `CL08-P` incrustan la diapositiva vieja de cada estilo dataflow junto a una síntesis nueva, y el repaso muestra solo la diapositiva vieja.

## Clase 7: atributos de calidad

**Entra.** Rol del arquitecto, requerimientos funcionales, requerimientos no funcionales y atributos de calidad. [CL12-REP, p. 2]

- **Rol del arquitecto.** La clase 7 no tiene una diapositiva dedicada. Lo más cercano es el Architecture Business Cycle: al arquitecto le llegan las influencias de stakeholders, organización, ambiente técnico y su propia experiencia; debe detectar expectativas contradictorias y buscar el mejor compromiso. [CL07-P, p. 4]; [CL07-P, p. 5]; [CL07-P, p. 7] En ATAM, el arquitecto integra con el PM los *decision makers*, que priorizan atributos y deciden el alcance. [CL09-P, p. 24] Ver [Architecture Business Cycle](temas/arquitectura-y-atributos-de-calidad.md#architecture-business-cycle).
- **Requerimientos funcionales y no funcionales.** La clase solo enuncia la distinción [CL07-P, p. 13] y ubica los atributos de calidad del lado no funcional. [CL07-P, p. 15] La clase 9 da ejemplos de los dos tipos cuando son arquitectónicamente significativos. [CL09-P, p. 7] Ver el [glosario](glosario.md).
- **Atributos de calidad.** Estudiar la clasificación en cuatro categorías de la clase 7 [CL07-P, p. 21] y el repaso de la clase 9, que la cátedra marcó con la nota «Esto implementa Parcializable». [CL09-P, p. 22] Las dos listas no coinciden del todo: ver [Repaso de atributos de calidad](temas/evaluacion-de-arquitecturas.md#repaso-de-atributos-de-calidad).

**No aparece (inferencia).** El modelo de calidad ISO, ADD, las restricciones de negocio y de arquitectura, y la tabla de trade-offs no se nombran por separado. Pueden caber dentro de «atributos de calidad».

## Clase 8: modelo 4+1 y estilos

**Entra.** El modelo 4+1 —vistas lógica, de procesos, de desarrollo, física y de escenarios— con los diagramas UML asociados, y los cuatro dominios de estilos. [CL12-REP, p. 3]

- **Diagramas UML por vista.** El repaso los pide expresamente, pero las fuentes no asignan de forma uniforme los diagramas de secuencia y comunicación. Al responder, justificar cada diagrama según la pregunta de la vista. Ver la tabla del [modelo 4+1](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md#modelo-41-de-kruchten) y [Dudas y conflictos](dudas-y-conflictos.md).
- **Dataflow.** Batch secuencial, pipes & filters y capas jerárquicas, con las variantes de dos, tres y cuatro capas. [CL12-REP, p. 4]
- **Sistemas distribuidos.** Broker, publish–subscribe, forwarder–receiver y client–dispatcher–server. [CL12-REP, p. 5]
- **Sistemas interactivos.** Solo MVC. [CL12-REP, p. 6]
- **Sistemas basados en eventos.** Los cuatro tipos de procesamiento, con ejemplos distintos de los de la clase. [CL12-REP, p. 7] Ver [Sistemas basados en eventos](temas/estilos-arquitectonicos.md#sistemas-basados-en-eventos).

**No aparece (inferencia).** Views and viewpoints, Views and Beyond, IEEE 1471/42010, la correspondencia entre vistas, el proceso guiado por escenarios y los otros estilos de cierre (repositorios, intérpretes, reglas).

## Clase 9: evaluación de arquitecturas

**Entra.** La clasificación de técnicas de evaluación en cualitativas —escenarios, checklists, cuestionarios— y cuantitativas —métricas, prototipos, simulaciones, experimentos y modelos matemáticos—. [CL12-REP, p. 8] ATAM: qué es, sus entradas y salidas, los roles de la fase 0 y el contenido de las fases 1, 2 y 3, incluida la generación del árbol de utilidad. [CL12-REP, p. 9]

**No aparece (inferencia).** BDUF, YAGNI y el sweet spot; los momentos en Scrum; ASR; SAFe y el architectural runway; las métricas SLI/SLO/SLA; SAAM; la diapositiva del árbol de utilidad con su ejemplo; los hallazgos de la fase 2; Lightweight ATAM; y los casos de Hariharan y HealthCare.gov. **Advertencia:** el árbol de utilidad y los hallazgos —riesgos, no riesgos y trade-offs— son exactamente lo que piden el ejercicio `EJ-2013` y el Cross Challenge. Conviene estudiarlos aunque el repaso no muestre esas diapositivas. [EJ-2013, p. 1]; [CROSS-2026-05, p. 2]

## Clase 10: persistencia

**Entra.** Prevalencia; bases de datos relacionales, multidimensionales y de objetos; y NoSQL por columnas, clave/valor y documentos. [CL12-REP, p. 10]

**No aparece (inferencia).** Archivos, las ventajas generales de las bases de datos, ACID, ORM, las bases vectoriales y la comparación final de la clase.

## Clase 11: arquitecturas de integración

**Entra.** Arquitectura con integraciones punto a punto, arquitectura con integración SOA —ESB, BPM, registry, governance y monitoreo de actividad— y el patrón API gateway. [CL12-REP, p. 11]

**No aparece (inferencia).** Integration hub, la evolución hacia las APIs, los principios de SOA, los microservicios —salvo el API gateway, que la clase presenta como uno de sus patrones—, las métricas de entrega, el despliegue y las lecturas de Clark (`B05`, `B06` y `B07`).

## Formato de ejercicio esperable

**Inferencia:** el ejercicio `EJ-2013` tiene formato de examen —«[6 ptos]»— y comparte la estructura del Cross Challenge. Los dos recorren la misma secuencia de la unidad de arquitectura, así que sirven como modelo de lo que puede pedir un ejercicio integrador. [EJ-2013, p. 1]; [CROSS-2026-05, p. 1]; [CROSS-2026-05, p. 2]

| Paso | `EJ-2013` | Cross Challenge | Dónde estudiarlo |
|---|---|---|---|
| Necesidad del cliente en menos de 40 palabras | a | 1.a | Ninguna fuente define cómo formularla; ver [Consignas de práctica](consignas-de-practica.md) |
| Funcionalidades de alto nivel | b (al menos 5) | 1.b (al menos 6) | Requerimientos funcionales |
| Árbol de utilidad, dos primeros niveles | c | 2.a | [Árbol de utilidad](temas/evaluacion-de-arquitecturas.md#fase-1-árbol-de-utilidad) |
| Arquitectura candidata justificada | d | 3.a y 3.b (dos vistas 4+1 y tres estilos) | [Modelo 4+1](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md) y [estilos](temas/estilos-arquitectonicos.md) |
| Cómo resuelve la arquitectura cada atributo | e | — | [Estilos y atributos de calidad](temas/estilos-arquitectonicos.md#estilos-y-atributos-de-calidad) |
| Riesgos, no riesgos, supuestos y trade-offs | f | 2.b | [Hallazgos de ATAM](temas/evaluacion-de-arquitecturas.md#fase-2-análisis-de-los-enfoques-arquitectónicos) |

Los *supuestos* no figuran entre las salidas de ATAM de la clase. [CL09-P, p. 28] Los dos ejercicios los piden aparte, así que hay que distinguirlos de los riesgos.

## Bibliografía y casos

El repaso no menciona la bibliografía (`B01` a `B07`), el caso de estudio ATAM de Hariharan ni el caso HealthCare.gov. **Inferencia:** sirven para profundizar los temas que sí entran, pero no hay confirmación de que sean evaluables.
