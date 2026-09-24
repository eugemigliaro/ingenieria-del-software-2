# Estilos arquitectónicos

> **Alcance:** esta clase es posterior al recorte del primer parcial y no aparece en él. Ver [alcance del primer parcial](../parcial-1-alcance.md). Fuente principal: segunda mitad de la clase 8 (`CL08-P`, pp. 23–59).

## De describir a diseñar

El modelo 4+1 describe la arquitectura mediante cuatro vistas técnicas y escenarios que las validan; para diseñarla se recurre a estilos. [CL08-P, p. 23] Un **estilo arquitectónico** es un conjunto de decisiones de diseño, aplicables en un contexto particular, que restringen el diseño en pos de un beneficio particular. Seguir un estilo aporta consistencia y previsibilidad, y un mismo sistema puede combinar varios estilos si se aplican en contextos distintos. [CL08-P, p. 24] Kruchten llega a la misma idea desde las vistas: cada vista puede adoptar su propio estilo, por lo que varios estilos conviven en un sistema. [B01, p. 3]

La clase agrupa los estilos en cuatro dominios: dataflow, sistemas distribuidos, sistemas interactivos y sistemas basados en eventos. [CL08-P, p. 25]; [CL08-P, p. 34]; [CL08-P, p. 48]; [CL08-P, p. 52]

## Dataflow

Dominio que define cómo fluyen los datos por el sistema y cómo son procesados o transformados. Incluye batch secuencial, pipes & filters y capas jerárquicas. [CL08-P, p. 25]

| Estilo | Problema | Cómo | Cuándo usarlo | Trade-off | Ejemplo |
|---|---|---|---|---|---|
| Batch secuencial | Procesar grandes volúmenes de datos offline | Etapas una detrás de otra; cada fase consume la salida completa de la anterior | ETL, procesamiento nocturno, pipelines donde no importa la latencia | Simple pero lento: alta latencia | Compiladores: análisis léxico → sintáctico → semántico → optimización → generación de código |
| Pipes & filters | Procesar datos en flujo continuo | Filtros independientes conectados | Streaming, necesidad de paralelismo; Apache Camel, Spring Integration | Más flexible, pero más complejo de coordinar | Edición de imagen o video con filtros encadenados que muestran resultados parciales |
| Capas jerárquicas | Organizar la complejidad | Cada capa abstrae a la inferior | Sistemas grandes, arquitecturas enterprise, separación de responsabilidades | Claridad vs. posible impacto en performance | Protocolos de red OSI o TCP/IP |

La tabla sintetiza [CL08-P, p. 26], [CL08-P, p. 27] y [CL08-P, p. 28].

**Capas: ventajas y desventajas.** Dividen un sistema complejo mediante abstracción; las mejoras en una capa impactan en todo el sistema, y las capas suponen reusabilidad y fácil intercambio. Por otro lado, no todos los sistemas pueden estructurarse así, muchas capas pueden deteriorar la performance y los cambios suelen tener que replicarse en todas las capas. [CL08-P, p. 29] El material muestra variantes de dos capas (cliente/servidor), tres capas (presentación, negocio y datos) y cuatro capas (cliente, web/servicios, lógica de negocio y base de datos). [CL08-P, p. 30]; [CL08-P, p. 31]; [CL08-P, p. 32] Kruchten recomienda el estilo en capas para la vista de desarrollo, con la regla de que un subsistema solo depende de su misma capa o de capas inferiores. [B01, p. 8]

**Cómo elegir** según la palabra clave del problema: [CL08-P, p. 33]

- **«Volumen»** → batch: facturación y sistemas bancarios, liquidaciones, cierres diarios, cálculo de intereses y motores de recomendación offline.
- **«Flujo»** → pipes & filters: en Apache Kafka, los filtros son servicios de procesamiento de streams que validan, transforman, enriquecen o filtran mensajes, y los pipes son los topics, que transportan el flujo de forma desacoplada y persistente.
- **«Organización»** → capas: hardware → kernel → servicios → aplicaciones; aplicaciones web con Django o Spring; la pila de Android.

## Sistemas distribuidos

Dominio que define cómo se descubren los miembros de la red y cómo se comunican. Incluye broker, publish–subscribe, forwarder–receiver y client–dispatcher–server. [CL08-P, p. 34] Todos buscan lo mismo: desacoplar, escalar y distribuir. [CL08-P, p. 47]

| Estilo | Idea | Problema que resuelve | Ejemplos |
|---|---|---|---|
| Broker | Un intermediario central coordina la comunicación entre clientes y servidores, que usan proxies para hablar con él | Desacoplar y enrutar; la distribución es transparente para quien implementa | WhatsApp, Telegram, Slack, Discord; Uber, Rappi, PedidosYa; correo con SMTP/IMAP |
| Publish–subscribe | Un publisher notifica a muchos subscribers suscriptos; productores y consumidores no se conocen | Desacoplamiento total y escalabilidad | Seguir cuentas en redes sociales; MQTT en IoT; repartidores suscriptos a pedidos de su zona |
| Forwarder–receiver | Cada peer delega el envío en un forwarder, que serializa, y la recepción en un receiver, que deserializa | Transparencia en sistemas distribuidos con comunicación directa entre pares | — |
| Client–dispatcher–server | Un dispatcher decide a qué servidor ir y balancea carga | Distribución y disponibilidad; transparencia de ubicación | JNDI, Skype; Nginx, HAProxy, AWS ELB; Oracle RAC, MongoDB con sharding |

La tabla sintetiza [CL08-P, p. 35], [CL08-P, p. 36], [CL08-P, p. 37], [CL08-P, p. 38], [CL08-P, p. 39], [CL08-P, p. 41], [CL08-P, p. 42], [CL08-P, p. 43], [CL08-P, p. 44], [CL08-P, p. 45] y [CL08-P, p. 46].

Algunos detalles de los diagramas ayudan a distinguirlos:

- En **broker**, el diagrama ubica proxy-cliente, broker y proxy-servidor entre cliente y servidor, más un componente puente. [CL08-P, p. 35]
- **Publish–subscribe** mantiene la sincronización entre componentes cooperativos y es análogo al patrón de diseño Observer; el publisher envía el mensaje a un topic y el topic lo distribuye a cada suscriptor. [CL08-P, p. 38]; [CL08-P, p. 40]
- **Forwarder–receiver** encapsula la comunicación: los peers no saben cómo viaja la información. Cada peer tiene su propio forwarder (marshal, deliver, sendMsg) y su propio receiver (receive, unmarshal, receiveMsg) a ambos lados del límite entre procesos. [CL08-P, p. 42]; [CL08-P, p. 43]
- En **client–dispatcher–server**, el servidor se registra en el dispatcher y este establece la conexión; luego el cliente pide el servicio al servidor y recibe el resultado. [CL08-P, p. 44]

**Inferencia a partir de los diagramas:** en broker el intermediario sigue en el camino de cada mensaje; en client–dispatcher–server, el dispatcher localiza el servidor y establece la conexión, pero no transporta cada pedido. En publish–subscribe, el emisor ni siquiera sabe quién recibirá el evento.

## Sistemas interactivos y MVC

La mayoría del software interactúa con el usuario; el objetivo de estos estilos es separar la funcionalidad principal de las vistas de presentación. Los principales son MVC, PAC, MVP y VIPER; la clase desarrolla solo MVC. [CL08-P, p. 48]

MVC se originó a principios de los años 80 en Smalltalk y divide la aplicación en tres tipos de componentes: el **modelo** contiene la funcionalidad principal y la información; la **vista** muestra información al usuario; el **controlador** maneja las entradas del usuario. [CL08-P, p. 49] En el diagrama, la vista envía eventos de entrada al controlador, el controlador modifica el modelo y también la vista, y el modelo actualiza la vista. [CL08-P, p. 50]

- **Ventajas:** múltiples vistas del mismo modelo, vistas sincronizadas y una base potencial para construir un framework. [CL08-P, p. 51]
- **Desventajas:** un número de actualizaciones potencialmente alto y alto acoplamiento entre los tres componentes. [CL08-P, p. 51]

## Sistemas basados en eventos

El sistema se subdivide en componentes individuales que se comunican entre sí. Conceptualmente hay tres tipos: **productores de eventos**, **canal** y **consumidores de eventos**. El canal puede ser una conexión directa sobre HTTP, TCP/IP u otro protocolo, un bus o PubSub, entre otras formas. [CL08-P, p. 52]

| Tipo de procesamiento | Definición | Ejemplos del material |
|---|---|---|
| Single Event Processing | Procesa eventos de a uno, en forma aislada | Sensor IoT que dispara una alarma; cajero automático que valida saldo y entrega dinero |
| Event Stream Processing | Procesa un flujo continuo de eventos aplicando transformaciones, agregaciones o filtros en línea | Google Analytics en tiempo real; timeline de Twitter; tracking de Uber; Apache Kafka |
| Complex Event Processing | Detecta patrones complejos a partir de múltiples eventos simples correlacionados en tiempo y espacio | Detección de fraude bancario; bloqueo tras varios intentos de login fallidos |
| Online Event Processing | Procesa eventos en tiempo real, casi sin latencia, para reaccionar de inmediato | Carrito de Amazon; trading en milisegundos |

La tabla resume [CL08-P, p. 53] y [CL08-P, p. 54]. El procesamiento de eventos aparece hoy en microservicios, sistemas de tiempo real, plataformas de streaming —play, pausa y skip como eventos— e IoT, con ejemplos como Netflix, Amazon, Uber y Spotify. [CL08-P, p. 55]

- **Ventaja:** los subsistemas son altamente independientes y pueden desarrollarse, escalarse y ponerse en producción por separado. [CL08-P, p. 56]
- **Desventajas:** reproducir situaciones particulares o determinar la causa raíz de un problema puede ser complejo; rastrear una operación de punta a punta o garantizar tiempos de procesamiento también exige esfuerzo. La última oración de la diapositiva está incompleta. [CL08-P, p. 56]

## Otros estilos y cierre

Existen muchos otros estilos: repositorios y blackboards, máquinas virtuales e intérpretes, sistemas basados en reglas, patrones de servidores web y patrones de concurrencia. [CL08-P, p. 57] La bibliografía recomendada es el paper del 4+1 de Kruchten y *Patterns of Enterprise Application Architecture* de Martin Fowler (Addison-Wesley, 2002). [CL08-P, p. 59]

El cierre de la clase resume: **arquitectura de software = vistas + estilos**. Las vistas dicen cómo *describir* el sistema: son perspectivas distintas y cada una responde a una pregunta. Los estilos dicen cómo *diseñarlo*: son decisiones de alto nivel que restringen y guían el diseño. Sobre un mismo sistema, preguntas distintas llevan a vistas distintas, y decisiones distintas llevan a diseños distintos. [CL08-P, p. 58]

## Estilos y atributos de calidad

**Síntesis entre clases:** cada estilo favorece algunos atributos de calidad de la [clase 7](arquitectura-y-atributos-de-calidad.md) y penaliza otros.

| Estilo | Favorece | Cuesta | Evidencia |
|---|---|---|---|
| Batch secuencial | Simplicidad | Latencia | [CL08-P, p. 26] |
| Pipes & filters | Flexibilidad, paralelismo | Coordinación | [CL08-P, p. 27] |
| Capas | Reusabilidad, intercambio, separación de responsabilidades | Performance; cambios replicados entre capas | [CL08-P, p. 29] |
| Publish–subscribe | Desacoplamiento y escalabilidad | — | [CL08-P, p. 39] |
| Client–dispatcher–server | Distribución y disponibilidad | — | [CL08-P, p. 45] |
| MVC | Vistas múltiples y sincronizadas | Muchas actualizaciones, acoplamiento | [CL08-P, p. 51] |
| Basado en eventos | Independencia de desarrollo, escalado y despliegue | Trazabilidad y diagnóstico | [CL08-P, p. 56] |

**Inferencia:** los casilleros vacíos no significan que el estilo no tenga costo, sino que la presentación no lo explicita. Por ejemplo, un broker central concentra el tráfico y conviene evaluar su disponibilidad (conocimiento general).

## Conexiones

- Cómo documentar la arquitectura resultante: [modelo 4+1](documentacion-de-arquitectura-y-modelo-4-mas-1.md).
- Por qué elegir un estilo u otro: drivers y trade-offs en [atributos de calidad](arquitectura-y-atributos-de-calidad.md).
- La degradación arquitectónica mencionada en [calidad de software](calidad-de-software.md) es, en parte, la erosión de estas decisiones de estilo. **Inferencia.**
