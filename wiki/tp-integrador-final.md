# Trabajo práctico integrador final (TPIF)

El TPIF es el trabajo grupal de cierre del segundo cuatrimestre de 2026. Se mantienen los grupos y la idea de producto trabajada en el primer tramo del cuatrimestre. [TPIF-2026, p. 2] Tiene entrega y defensa, así que no es una consigna de práctica: el trabajo del grupo va en `entregas/`, no en `practica/`.

## Cronograma

| Fecha | Actividad |
|---|---|
| 5/11 | Enunciado del TP |
| 12/11 | Sin clase: visita al datacenter |
| 19/11 | Entrega del TP y recuperatorios |
| 26/11 | Defensa del TP |

[TPIF-2026, p. 2]

## Objetivo

El enunciado pide tres cosas: [TPIF-2026, p. 3]

- Investigar una tecnología e implementarla en una prueba de concepto (PoC).
- Presentar un tema entre los propuestos por la cátedra.
- Hacerlo con el enfoque de la materia: decisiones orientadas al negocio, el **eje funcional**, que consideran los atributos de calidad, el **eje técnico**.

## Eje técnico

Hay que explicar la herramienta o tecnología con un nivel de detalle que muestre la investigación realizada, y armar una PoC con un caso de uso o historia de usuario **no trivial** del producto. [TPIF-2026, p. 4] Se elige uno de estos temas:

| Opción | Tecnologías | Rótulo del enunciado | Dónde está en la materia (inferencia) |
|---|---|---|---|
| 1 | Airflow o Prefect | Dataflow, orquestación de datos | [Dataflow](temas/estilos-arquitectonicos.md#dataflow): batch secuencial y pipes & filters |
| 2 | Kafka o RabbitMQ | Sistemas distribuidos, pub/sub | [Publish–subscribe](temas/estilos-arquitectonicos.md#sistemas-distribuidos) y [comunicación entre microservicios](temas/arquitecturas-de-integracion.md#comunicación-entre-microservicios) |
| 3 | N8N o Flink | N8N: eventos, genérico. Flink: *single event processing* | [Sistemas basados en eventos](temas/estilos-arquitectonicos.md#sistemas-basados-en-eventos) |
| 4 | Otras | Previa validación | — |

Las tres primeras columnas siguen [TPIF-2026, p. 4].

**Qué dice el material sobre estas tecnologías.** De las seis, solo Kafka aparece en las clases. La clase 8 lo usa como ejemplo de pipes & filters: los filtros son servicios de procesamiento de streams que validan, transforman, enriquecen o filtran mensajes, y los pipes son los topics. [CL08-P, p. 33] También lo nombra como tecnología típica de *event stream processing*. [CL08-P, p. 54] Clark recomienda comunicar los microservicios con mensajería liviana, «como AMQP o Kafka». [B07, p. 22]

**Inferencia:** las tres primeras opciones repiten los tres dominios que la Actividad 1 de la clase 9 pedía elegir para el producto del grupo: un pipeline dataflow, un estilo distribuido y el manejo de eventos. [CL09-P, p. 2] La PoC puede implementar con una tecnología real una de las decisiones de esa actividad.

**Conocimiento general, ausente del material.** Sirve como orientación inicial para elegir; conviene verificarla en la documentación oficial de cada herramienta.

- **Airflow y Prefect** orquestan workflows definidos en Python: programan, reintentan y monitorean tareas encadenadas. Airflow los modela como grafos acíclicos dirigidos (DAG). Están pensados sobre todo para procesos programados o por lotes, más cerca de «volumen» que de «flujo».
- **Kafka** es una plataforma de streaming de eventos: guarda los mensajes en un log particionado y persistente, y cada consumidor lee a su ritmo y puede releer. **RabbitMQ** es un *message broker* que implementa AMQP: enruta los mensajes a colas y los descarta cuando el consumidor confirma la recepción.
- **n8n** automatiza workflows de bajo código con nodos y disparadores, como webhooks, tareas programadas o eventos de otros servicios. **Flink** es un motor distribuido de procesamiento de streams con estado, ventanas de tiempo y una biblioteca de *complex event processing*.

El rótulo de Flink como *single event processing* no coincide del todo con esa descripción. Ver [Dudas y conflictos](dudas-y-conflictos.md).

## Eje funcional

Hay que explicar el concepto, mostrar con ejemplos la utilidad del eje técnico elegido y comparar alternativas con pros y contras. La comparativa debe mostrar cómo las decisiones técnicas benefician a una o varias necesidades de negocio del producto. [TPIF-2026, p. 5]

**Inferencia:** cada opción ya trae dos alternativas —Airflow o Prefect, Kafka o RabbitMQ, N8N o Flink—, que son un punto de partida natural para la comparativa. Los criterios pueden salir de los atributos de calidad y los trade-offs de la materia: ver [Estilos y atributos de calidad](temas/estilos-arquitectonicos.md#estilos-y-atributos-de-calidad) y [Arquitectura y atributos de calidad](temas/arquitectura-y-atributos-de-calidad.md).

## Entregables (19/11)

[TPIF-2026, p. 6]

- **White paper:** documento funcional y técnico que presenta un problema complejo y propone una solución, el producto. Máximo cinco páginas, sin contar portada, índice y anexos.
- **PoC:** proyecto funcional que se levante con `docker compose up` y contenga todos los servicios necesarios para ejecutarla, como bases, orquestador y servicios. Debe incluir un `README.md` con una descripción breve del flujo implementado, los comandos de ejecución, qué endpoints o eventos probar, los datos de prueba y los resultados esperados, entre otras cosas.
- **Despliegue en la nube:** el proyecto también debe estar desplegado en la nube. El enunciado agrega «se requieren credenciales», sin aclarar de quién ni para qué.

## Defensa (26/11)

| Bloque | Duración |
|---|---|
| Setup y exposición, integrando ambos ejes | 10 min |
| Demo | 10 min |
| Preguntas y respuestas | 10 min |

La exposición debe cubrir la presentación y la justificación del producto, la enumeración de las funcionalidades principales, la arquitectura con diagramas y narración, el stack de tecnologías y lo que hace falta para llevar adelante el proyecto: tiempo, recursos humanos y recursos técnicos. [TPIF-2026, p. 7]

## Qué temas de la materia integra

Toda la tabla es **inferencia**: el enunciado no remite a ninguna clase.

| Pedido del TPIF | Tema de la materia |
|---|---|
| Justificar el producto y su necesidad de negocio | [Productos digitales](temas/productos-digitales.md): Lean Startup, Design Thinking y Canvas |
| Enumerar las funcionalidades principales | Las «funcionalidades de alto nivel» que piden `EJ-2013` y el Cross Challenge: ver [Consignas de práctica](consignas-de-practica.md) |
| Eje técnico guiado por atributos de calidad | [Atributos de calidad](temas/arquitectura-y-atributos-de-calidad.md) y [árbol de utilidad](temas/evaluacion-de-arquitecturas.md#fase-1-árbol-de-utilidad) |
| Arquitectura con diagramas y narración | [Modelo 4+1](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md) y [estilos arquitectónicos](temas/estilos-arquitectonicos.md) |
| Comparativa con pros y contras | Trade-offs y [hallazgos de ATAM](temas/evaluacion-de-arquitecturas.md#atam) |
| PoC | El experimento y el prototipo de las [técnicas cuantitativas de evaluación](temas/evaluacion-de-arquitecturas.md#prototipos-simulaciones-y-experimentos): el experimento prueba una hipótesis sobre el comportamiento de la arquitectura; el prototipo es una versión preliminar que puede evolucionar. [CL09-P, p. 18] |
| `docker compose` y despliegue en la nube | [Vista física](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md#vista-física) del modelo 4+1 |
| Tiempo y recursos humanos y técnicos | [Estimación](temas/estimacion-de-proyectos.md): tamaño, esfuerzo, complejidad y duración [CL05-P, p. 22] |
| Servicios que se comunican dentro de la PoC | [Arquitecturas de integración](temas/arquitecturas-de-integracion.md) |

## Punto de partida para el producto del grupo

**Inferencia.** El producto que usó el grupo en las actividades de la clase 9 es YOLO, una plataforma de exploración vocacional. Su business case es material del grupo, no de la cátedra: ver [producto-yolo.md](../practica/clase-09-actividad-1/producto-yolo.md). La [Actividad 1](../practica/clase-09-actividad-1/README.md) eligió pipes & filters con una consolidación nocturna en batch, publish–subscribe y *event stream processing*. Cada opción técnica tiene un lugar posible en esa arquitectura:

- **Airflow o Prefect:** la consolidación nocturna para los reportes.
- **Kafka o RabbitMQ:** el canal publish–subscribe por el que circulan los eventos del recorrido.
- **N8N o Flink:** N8N, las automatizaciones disparadas por eventos, como las notificaciones; Flink, el procesamiento en línea del flujo de interacciones.

La elección de la opción y del caso de uso de la PoC le corresponde al grupo.

## Dudas abiertas

- Qué significa «se requieren credenciales» en el despliegue en la nube. [TPIF-2026, p. 6]
- Si Flink debe usarse como *single event processing*, según el rótulo del enunciado. [TPIF-2026, p. 4]
- El enunciado no indica criterios de evaluación, peso en la nota, medio ni hora de entrega, ni quién valida la opción «Otros» y hasta cuándo. [TPIF-2026, p. 4]; [TPIF-2026, p. 6]

Las tres están registradas en [Dudas y conflictos](dudas-y-conflictos.md).
