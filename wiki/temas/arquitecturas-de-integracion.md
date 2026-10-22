# Arquitecturas de integración

> **Alcance:** esta clase es posterior al recorte del primer parcial y no aparece en él. Ver [alcance del primer parcial](../parcial-1-alcance.md). Sí entra en el segundo parcial: ver [alcance del segundo parcial](../parcial-2-alcance.md). Fuente principal: presentación de arquitecturas de integración, `CL11-INT`. Casi todas sus diapositivas son solo imagen, así que se revisaron renderizadas. Lecturas complementarias de la misma clase, las tres de Kim J. Clark, arquitecto de integración de IBM: la serie *The benefits of agile integration*, partes 1 y 2 (`B05` y `B06`, 2018), y la presentación *Microservices: how they relate to ESB, APIs and messaging* (`B07`).
>
> **Advertencia (inferencia):** las tres lecturas son de un proveedor de productos de integración y mencionan productos de IBM. Sirven para entender los patrones, no como evaluación neutral de herramientas. Ante una diferencia con la presentación, prima la clase; ver [Dudas y conflictos](../dudas-y-conflictos.md).

## El problema

Una empresa tiene muchos sistemas independientes —ERP, CRM, facturación, BI, sistemas legados— que necesitan intercambiar datos y funciones. La clase recorre cómo cambió la forma de conectarlos, de las integraciones punto a punto a los microservicios. [CL11-INT, p. 2]; [CL11-INT, p. 10]; [CL11-INT, p. 25]

Clark agrega una aclaración de vocabulario: los **sistemas de registro** (*systems of record*) ejecutan las transacciones críticas del negocio y suelen ser antiguos. Los **sistemas de interacción** (*systems of engagement*) son los nuevos canales hacia los consumidores, donde la innovación es rápida. [B05, p. 9] Gran parte de la integración consiste en exponer los primeros a los segundos. **Inferencia.**

## Evolución de las arquitecturas de integración

| Época | Arquitectura | Qué aporta | Qué cuesta | Evidencia |
|---|---|---|---|---|
| Principios de los 90 | **Punto a punto:** cada aplicación tiene código de integración específico contra cada otra | Simple | Desorden | [CL11-INT, p. 2] |
| Fines de los 90 | **Integration hub (middleware):** un intermediario con adaptadores entre todos los sistemas | Evita la maraña punto a punto; desacopla las aplicaciones | — | [CL11-INT, p. 3] |
| Principios de los 2000 | **ESB:** un gateway de exposición de servicios sobre el hub | Reutilización, bajo acoplamiento y gestión centralizada de servicios | — | [CL11-INT, p. 4] |
| Cerca de 2010 | **SOA como capa interna + APIs REST hacia afuera** | Apertura a la web y a los móviles; integraciones más chicas y rápidas | — | [CL11-INT, p. 5] |
| Después de 2010 | **APIs como interfaces de negocio** | La empresa se vuelve una plataforma abierta: se pasa de conectar sistemas a conectar ecosistemas | — | [CL11-INT, p. 6] |

Los casilleros vacíos no implican que no haya costos: la clase los trata más adelante, en las conclusiones de SOA. [CL11-INT, p. 12]

### Punto a punto

Cada sistema tiene interfaces específicas contra cada otro sistema. La ventaja es la simplicidad; la desventaja, el desorden. [CL11-INT, p. 2] Con muchos sistemas —BI, ERP, CRM, Billing, SCM y Legacy en el ejemplo— aparecen dependencias entre sistemas, alto acoplamiento, dificultad de mantenimiento y responsabilidades poco claras. **Cada sistema nuevo obliga a tocar medio mapa.** [CL11-INT, p. 10]

Según Clark, antes del 2000 la integración era casi exclusivamente asíncrona, mediante archivos y mensajes. Escribir código para cada integración punto a punto era caro y producía una red compleja de interacciones. [B05, p. 2]

**Inferencia:** con *n* sistemas conectados todos con todos hay hasta *n*(*n*−1)/2 integraciones; con un intermediario, alcanza con *n* conexiones.

### Integration hub

Para evitar la maraña de integraciones punto a punto se introduce un **intermediario que «rutea»**: hace transformación de datos, mediación de protocolos, orquestación simple y desacoplamiento entre aplicaciones. Es el **middleware**, que se conecta con las aplicaciones mediante **adaptadores** sobre colas, HTTP/SOAP, RMI, JDBC y otros protocolos. [CL11-INT, p. 3]

El diagrama separa dos grupos de capacidades del hub: [CL11-INT, p. 3]

- **Integración canónica:** traducción de datos, ruteo y distribución, y composición.
- **Adaptación:** manejo de datos, *framework* de interacción, gestión de conexiones, API de bajo nivel, conversión de protocolos y comunicación de transporte.

Clark llama a este patrón **hub-and-spoke**: un hub con conectores reutilizables entre todos los sistemas, que simplifica la conectividad y permite reutilizar parte del trabajo. Insiste en que es **anterior al ESB y distinto de él**, aunque se implemente con el mismo producto: es asíncrono y basado en eventos, y todavía no expone servicios. [B05, p. 2]

### ESB (Enterprise Service Bus)

A principios del 2000, la clase muestra el ESB como la combinación de un **Service Exposure Gateway** y el **Integration Hub**, entre los consumidores y los sistemas operacionales —Cobol, aplicaciones legadas, ERP, CRM—. [CL11-INT, p. 4]

- **Lo nuevo:** gestiona la exposición de servicios internos y aplica políticas de seguridad, visibilidad y virtualización. Las capacidades de exposición del diagrama son virtualización, visibilidad, gestión de tráfico y seguridad. [CL11-INT, p. 4]
- Un **service registry** se usa en tiempo de diseño y en tiempo de ejecución. [CL11-INT, p. 4]
- **Tendencia EAI:** elimina silos de datos, automatiza workflows y unifica datos. [CL11-INT, p. 4]

Clark reconstruye el origen del término. Con HTTP, XML y SOAP surgió la promesa de que cualquier sistema pudiera descubrir a otro y hablarle mediante llamadas sincrónicas, y así nació SOA. Pero los sistemas de registro tenían protocolos y formatos antiguos, y algo tenía que mediar. [B05, p. 3] El término ESB se acuñó para ese **patrón de exposición sincrónica** vía web services: un «bus» centralizado que expone «servicios» a toda la «empresa». [B05, p. 4] Como al principio un solo componente —el *integration runtime*— implementaba los dos patrones, el hub y la exposición, ese componente pasó a llamarse ESB sin distinción. [B05, p. 4] Ver la discrepancia de vocabulario en [Dudas y conflictos](../dudas-y-conflictos.md).

### APIs, apertura al exterior y economía de APIs

**Cerca de 2010.** Con la madurez de la Web 2.0, AJAX, JSON y las primeras APIs REST, los servicios SOA quedan como **capa de integración interna**. Hacia afuera se agrega una exposición de grano fino, con APIs RESTful por aplicación, en una DMZ. [CL11-INT, p. 5] El cambio implica: [CL11-INT, p. 5]

- apertura hacia el exterior, a la web y los móviles;
- integraciones más chicas y rápidas, sin tanta infraestructura;
- mayor granularidad: ya no se exponen «servicios empresariales enormes», sino funcionalidades específicas.

**Después de 2010.** Las APIs dejan de ser conectores y se vuelven **interfaces de negocio**. La empresa se convierte en una plataforma abierta, capaz de escalar gracias a integraciones externas. El diagrama distingue pocos consumidores internos bien conocidos, decenas de aplicaciones externas y cientos de «experimentadores» externos. El diferencial: la API es una interfaz pública y otros construyen valor alrededor de ella; no es solo un integrador interno. [CL11-INT, p. 6]

Clark explica cómo se llegó ahí:

- Las interfaces SOAP resultaron complejas, y los servicios RESTful con JSON/HTTP se volvieron el mecanismo popular de exposición. [B05, p. 6]
- Exponer no alcanza: el servicio tiene que poder descubrirse y aprenderse a usar, y el proveedor necesita controlar el tráfico y la seguridad. Esas capacidades se separaron en un **gateway de exposición** y evolucionaron hacia la **gestión de APIs** (*API management*): limitación de tráfico, cifrado, seguridad, portales para autosuscribirse y analíticas de uso. [B05, p. 6]; [B05, p. 7]
- Muchos sistemas modernos ya ofrecen una interfaz HTTP y solo necesitan exposición controlada. El *integration runtime* queda para lo complejo: protocolos o formatos poco usuales, composición de varios pedidos o transaccionalidad. [B05, p. 7]
- Las APIs salieron de la empresa, primero con el patrón **back-end-for-front-end** (BFF): APIs hechas a medida de una aplicación móvil o de una SPA. Después, para que cualquier socio pudiera escribir aplicaciones. [B05, p. 8]
- Las APIs externas apuntan menos a la reutilización y más a nichos de negocio nuevos; de ahí la **economía de APIs**. [B05, p. 9]

## SOA (Service Oriented Architecture)

### Definición

Según la clase, SOA: [CL11-INT, p. 8]

- es un **estilo arquitectónico**;
- implementa las funcionalidades de negocio como **servicios independientes**;
- exige **interfaces bien definidas** y contratos públicos;
- permite que los servicios sean **descubiertos**, invocados y reutilizados por otros sistemas, dentro o fuera de la organización.

> SOA organiza una o varias aplicaciones como un **ecosistema de servicios autónomos** que colaboran entre sí mediante **mensajes estandarizados**. [CL11-INT, p. 8]

El **service registry** funciona como un catálogo donde buscar qué hace cada servicio, cómo se llama y cómo invocarlo. [CL11-INT, p. 8]

### Principios de diseño

| Principio | Significado |
|---|---|
| Contratos estandarizados | Los servicios de un mismo inventario siguen los mismos principios de diseño de contratos |
| Bajo acoplamiento | Del servicio respecto de su entorno, y a su vez bajo acoplamiento impuesto a sus consumidores |
| Abstracción | Los contratos contienen solo lo esencial; no hay más información que la publicada en ellos |
| Reutilización | Contenedores de lógica agnóstica, fácilmente reutilizable en distintos contextos |
| Autonomía | Alto control sobre el entorno de ejecución subyacente |
| Ausencia de estado | El servicio no conserva información entre una invocación y la siguiente |
| Capacidad de ser descubiertos | Metadatos que permiten descubrirlos e interpretarlos |
| Capacidad de ser combinados | Se componen para formar lógicas más complejas |

La tabla resume [CL11-INT, p. 9]. **Conocimiento general:** coinciden con los ocho principios de orientación a servicios de Thomas Erl.

La **ausencia de estado** habilita tres beneficios: escalabilidad horizontal, porque el servicio puede ejecutarse en varios nodos; confiabilidad y tolerancia a fallos, porque si un nodo cae otro puede continuar; y desacoplamiento. [CL11-INT, p. 9]

### Arquitectura con integración SOA

El diagrama del caso **Telecom–IBM, «Súper Integración»**, conecta BI, Billing, CRM, ERP, SCM y Legacy a un **Enterprise Service Bus**, y sobre él ubica a los consumidores: *service consumers*, un portal y aplicaciones compuestas. [CL11-INT, p. 11] Sus componentes:

| Componente | Función |
|---|---|
| ESB | Middleware que actúa como canal central de comunicación entre servicios; permite que sistemas y servicios se hablen sin conectarse directamente |
| BPM (*Business Process Management*) | Orquesta y coordina los servicios para ejecutar procesos de negocio de punta a punta |
| Governance y Registry | Seguridad, políticas de acceso, control de versiones, monitoreo y auditoría, gestión de tráfico y cumplimiento de contratos |
| Business Activity Monitoring | Aparece en el diagrama, sin descripción en la diapositiva |

La tabla resume [CL11-INT, p. 11].

### Conclusiones de la clase

- SOA sigue siendo el modelo más usado en las empresas para integrar sus aplicaciones corporativas.
- Resuelve los problemas clásicos de integración en forma satisfactoria.
- Necesita un **governance centralizado**: es apta para ciertas organizaciones y contextos, no para todos.
- Tiene limitaciones en escalabilidad, tolerancia a fallos, desarrollo rápido y deployments frecuentes.

Integra las aplicaciones de manera más ordenada y centralizada, pero puede volverse pesada: requiere gobierno, control de contratos, versionado y monitoreo. [CL11-INT, p. 12]

### Qué falló en el ESB centralizado

Clark explica por qué el patrón ganó mala fama. Casi siempre se implementó **una sola infraestructura para toda la empresa**, con decenas o cientos de integraciones en el mismo clúster. Al principio había buenas razones: se compartían costos de hardware y software, se aprovisionaba una vez y había un solo equipo especializado. [B05, p. 4]; [B05, p. 5] Además, era difícil financiar un programa transversal que solo se justificaba si los servicios se reutilizaban. [B05, p. 5] Los problemas: [B05, p. 5]; [B05, p. 6]

- Un cambio en una interfaz podía desestabilizar otras no relacionadas, y obligaba a extensas pruebas de regresión.
- Los runtimes eran tan grandes que no se querían reiniciar; se parchaban en vivo, y eso hacía difícil replicar ambientes y generaba resistencia a los cambios.
- La alta disponibilidad y la recuperación ante desastres eran caras, y escalar requería planificación previa.
- Actualizar el middleware era riesgoso, así que los servidores quedaban varias versiones atrás.
- Los especialistas conocían la herramienta de integración, pero no las aplicaciones que exponían.
- Se formaban equipos «SOA» separados, que recibían trabajo en cascada y agregaban una dependencia a cada proyecto.
- El descubrimiento de servicios era inmaduro, y la documentación quedaba desactualizada o directamente no existía.

El resultado fue que el equipo SOA se volvió un **cuello de botella** en lugar de un habilitador. [B05, p. 6]

**Inferencia:** esto explica una aparente tensión de la clase. Los principios de SOA prometen escalabilidad horizontal y tolerancia a fallos [CL11-INT, p. 9], pero las conclusiones le atribuyen limitaciones en esos mismos atributos [CL11-INT, p. 12]. Los servicios sin estado escalan; lo que no escala es la **infraestructura centralizada del ESB**, cara de replicar y de escalar. [B05, p. 5]

## Microservicios

### El desafío: moverse rápido sin romper nada

El desafío actual es entregar cambios rápido sin destruir producción. Para eso hacen falta CI/CD, tests automáticos, despliegues automatizados y *feature flags*. [CL11-INT, p. 14] La clase muestra cuatro métricas de desempeño de la entrega de software, con cuatro niveles: [CL11-INT, p. 14]

| Métrica | Elite | High | Medium | Low |
|---|---|---|---|---|
| Frecuencia de despliegue | A demanda, varios por día | Entre una vez por semana y una por mes | Entre una vez por mes y una cada seis meses | Menos de una vez cada seis meses |
| *Lead time* de cambios (de commit a producción) | Menos de una hora | Entre un día y una semana | Entre un mes y seis meses | Más de seis meses |
| Tiempo de restauración del servicio | Menos de una hora | Menos de un día | Entre un día y una semana | Más de seis meses |
| Tasa de fallas por cambio | 0–15 % | 16–30 % | 16–30 % | 16–30 % |

**Conocimiento general:** son las cuatro métricas DORA. Los valores coinciden con el informe *Accelerate State of DevOps* de 2021; la diapositiva no cita la fuente.

### Qué se necesita

La clase arma un triángulo con tres vértices: **procesos** (DevOps y continuous delivery/deployment, rotulado «Prácticas»), **organización** (equipos pequeños y autónomos, rotulado «Agilidad») y **arquitectura**, con un signo de pregunta. Junto a la arquitectura aparece la nota «No es suficiente». [CL11-INT, p. 15] **Inferencia:** prácticas y agilidad no alcanzan si la arquitectura no acompaña; la diapositiva siguiente presenta el monolito como enfoque tradicional.

### Enfoque tradicional: el monolito

La aplicación se despliega como un **único `.jar`**. El ejemplo es FTGO, una aplicación de pedidos de comida con módulos de gestión de restaurantes, pedidos, entregas, pagos, notificaciones y facturación. La usan repartidores, consumidores y restaurantes mediante una API REST y una UI web, y se conecta a Twilio, Amazon SES, Stripe y MySQL mediante adaptadores. [CL11-INT, p. 16] **Conocimiento general:** FTGO es el ejemplo del libro *Microservices Patterns*, de Chris Richardson; los diagramas de las pp. 16–17 y 21–23 siguen ese libro.

**Con el tiempo, el monolito se vuelve una limitación.** Una organización de desarrollo grande trabaja sobre una sola base de código, lo que genera sobrecarga de comunicación y coordinación. Además, el camino del commit a producción es arduo: los cambios esperan en cola hasta que se prueban manualmente. [CL11-INT, p. 17] Consecuencias: [CL11-INT, p. 17]

- código complejo;
- lento pasaje de commit a deploy;
- dificultades para escalar;
- problemas de tolerancia a fallos;
- cautividad en un stack tecnológico potencialmente obsoleto.

### Microservicios: la propuesta

Con microservicios, el triángulo se completa: la **arquitectura de microservicios** permite equipos pequeños y autónomos, y procesos DevOps de entrega continua. Los tres juntos habilitan la **entrega rápida y confiable de software**. [CL11-INT, p. 18]

Clark define la arquitectura de microservicios como **un conjunto de principios** que guían la división de componentes grandes en otros más pequeños y autocontenidos. Persigue más agilidad, escalabilidad más elástica y resiliencia diferenciada. [B07, p. 2]

- **Principios fundamentales:** maximizar el aislamiento y el desacoplamiento entre componentes, **incluidos sus datos**; hacerlos lo más *stateless* posible y evitar afinidades. [B07, p. 2]
- **Requisitos de soporte:** pipelines DevOps totalmente automatizados y buena cobertura de tests automatizados. [B07, p. 2]

| Beneficio | Cómo se manifiesta |
|---|---|
| Agilidad | Ciclos de iteración más rápidos; contexto acotado (*bounded context*) |
| Escalabilidad | Escalado elástico; orquestación de cargas de trabajo |
| Resiliencia | Menos dependencias; *fail fast* |

La tabla resume [B07, p. 3]. Los componentes pequeños se pueden cambiar y escalar de forma independiente, y gestionarse sin contemplaciones —«*cattle not pets*»— para lograr la resiliencia de un servicio 24/7. [B05, p. 10]

Clark sugiere preguntarse si realmente se hacen microservicios o solo se adoptan algunos de sus principios. Cita como referencias las nueve características de Martin Fowler y James Lewis y los doce factores de las *twelve-factor apps*. [B07, p. 4]

- **Fowler y Lewis:** componentización; organización en torno a capacidades de negocio; productos, no proyectos; *smart endpoints and dumb pipes*; gobierno descentralizado; gestión de datos descentralizada; automatización de infraestructura; diseño para la falla; diseño evolutivo. [B07, p. 4]
- **Doce factores:** una sola base de código versionada con muchos despliegues; dependencias declaradas y aisladas; configuración en el entorno; servicios de respaldo como recursos adjuntos; separación estricta de build, release y run; procesos sin estado; exportar servicios por *port binding*; escalar con el modelo de procesos; arranque rápido y apagado ordenado; paridad entre desarrollo y producción; logs como flujos de eventos; tareas administrativas como procesos aislados. [B07, p. 16]

Como SOA, XP, ágil o DevOps, los microservicios suelen venderse como «todo o nada», y conviene preguntarse si se puede adoptar el paquete completo. [B07, p. 4]

### Desventajas y cuándo no usarlos

**No todo son ventajas.** Según la clase: [CL11-INT, p. 19]

- No es fácil definir correctamente los servicios.
- Con varias bases de datos, ¿cómo se coordina la transaccionalidad?
- Los microservicios forman un sistema distribuido, con complejidades propias de desarrollo, testeo y deployment.
- El deployment de features que impactan en varios servicios debe coordinarse con cuidado.

Hay que decidir con prudencia cuándo usarlos, porque implementarlos es complejo. [CL11-INT, p. 19]

**Microservicios ≠ magia.** Agregan complejidad distribuida, problemas de datos, trazabilidad, latencia y coordinación. **No conviene usarlos si:** [CL11-INT, p. 20]

- el dominio es simple;
- el equipo es chico;
- no hay madurez DevOps;
- no se necesita escalar partes por separado.

Clark agrega desafíos: [B07, p. 3]

- **Madurez:** cambio radical de métodos, habilidades, infraestructura y operaciones, y automatización suficiente.
- **Mantenimiento:** sostener en el tiempo las habilidades necesarias.
- **Latencia y serialización:** cada salto de red y cada serialización agregan latencia y CPU.
- **Datos compartidos:** no todos los datos se dividen en funciones independientes.
- **Dependencias en tiempo real:** las llamadas sincrónicas entre microservicios tienden a encadenarse y exigen mensajería o patrones de disponibilidad, como el *circuit breaker*.
- **Gestionabilidad:** monitorear y diagnosticar una red distribuida.
- **Persistencia:** concurrencia pesimista u optimista, objetos compartidos, relacional o NoSQL, ACID, BASE, CQRS o event sourcing.

Elegir el tamaño de los componentes es solo una parte: también hay que decidir cuánto desacoplarlos, y el desacoplamiento total no siempre es buen diseño. **Una aplicación de microservicios es tan ágil y escalable como bueno sea su diseño y madura su metodología.** [B05, p. 11]

### Patrones de microservicios

Un **lenguaje de patrones** ayuda a resolver problemas típicos de arquitectura, diseño, desarrollo y operación de microservicios. Se organiza en tres niveles: [CL11-INT, p. 21]

| Nivel | Patrones |
|---|---|
| De aplicación | Decomposition, database architecture, querying, maintaining data consistency, testing |
| De infraestructura de aplicación | Cross-cutting concerns, security, transactional messaging, communication style, reliability, observability |
| De infraestructura | Deployment, discovery, external API |

Transactional messaging, communication style, reliability, discovery y external API forman el grupo de **patrones de comunicación**. La clase resalta tres patrones, que desarrolla en las diapositivas siguientes: decomposition, deployment y external API. [CL11-INT, p. 21]

#### Descomposición por subdominio

El dominio FTGO se divide en subdominios: toma de pedidos, entregas, cocina y contabilidad. Cada uno **se mapea a un servicio** con su propio modelo de dominio. [CL11-INT, p. 22] Es la idea de **Domain-Driven Design**: no se separa por capas técnicas, sino por capacidades del negocio. En una banca digital, por ejemplo: accounts, transfers, loans, cards, fraud-detection y notifications. [CL11-INT, p. 22]

#### API gateway

El **API gateway** concentra el acceso externo, enruta los requests a los servicios internos y aplica autenticación, logging y otras funciones transversales. [CL11-INT, p. 23] En el diagrama, el navegador, las apps de iPhone y Android y las aplicaciones de terceros envían requests de API a través del firewall hacia el gateway, que los reenvía a los servicios internos: pedidos, consumidores y entregas. Las páginas web, en cambio, las sirve una aplicación web. [CL11-INT, p. 23]

Para Clark, cada componente no debería cargar con la exposición fuera de la aplicación. Esa exposición se delega en una capacidad aparte, con al menos un gateway, un portal para desarrolladores y una gestión de APIs: [B07, p. 10]

| Pieza | Funciones |
|---|---|
| API Gateway | Desacoplamiento y ruteo, gestión de tráfico, seguridad, traducción |
| Developer Portal | Descubrimiento de APIs, autosuscripción y autoadministración, analíticas de uso por cuenta |
| API Manager | Diseño de planes y productos, gestión de acceso, administración de políticas, analíticas de uso por plan |

Los gateways **definen y hacen cumplir las fronteras** entre aplicaciones, y eso hace manejables los entornos complejos. Lo mismo vale para las interfaces basadas en mensajería. [B07, p. 9]

#### Deployment: cómo evolucionó la infraestructura

| Año | Hito | Unidad de despliegue |
|---|---|---|
| 1990s | — | Aplicación sobre máquina física, en un formato específico del lenguaje: lo tradicional |
| 2006 | Lanzamiento de AWS EC2 | Servicio en una máquina virtual, que encapsula el stack tecnológico de la aplicación |
| 2013 | Primera versión de Docker | Servicio en un contenedor: similar a una VM, pero liviano |
| 2014 | Presentación de AWS Lambda | *Serverless*: desaparece el concepto de máquina, virtual o contenedor; es el modelo serverless de Amazon |

La tabla resume [CL11-INT, p. 24]. El eje va de lo pesado, permanente y manual a lo liviano, efímero y automatizado. [CL11-INT, p. 24]

### Comunicación entre microservicios

El objetivo es el **desacoplamiento para ganar robustez**: [B07, p. 22]

- **Mensajería donde sea posible:** mensajería liviana, como AMQP o Kafka; publish/subscribe; consistencia eventual.
- **Llamadas directas donde haga falta:** protocolos livianos, como JSON/HTTP; balanceo y escalado mediante descubrimiento de servicios; *circuit breaker*; caché.

Clark distingue dos niveles de comunicación: [B07, p. 11]

| | Entre microservicios de una aplicación | Entre aplicaciones |
|---|---|---|
| Protocolos | Livianos: HTTP, mensajería de aplicación | Empresariales: gateways de API gestionados, mensajería empresarial |
| Descubrimiento | Registro de componentes en tiempo de ejecución | Portales para desarrolladores en tiempo de diseño |
| Balanceo | Del lado del cliente, con *circuit breaker* | En el gateway, con *throttling* |

Ambos niveles pueden usar JSON/HTTP RESTful, pero su implementación puede ser radicalmente distinta. [B07, p. 11]

### Conclusión de la clase

Los microservicios permiten una entrega rápida y confiable de software **en los contextos adecuados**: solo si hay DevOps, equipos autónomos y buena arquitectura. [CL11-INT, p. 25]

## SOA y microservicios: ¿sucesión o escalas distintas?

La clase presenta los microservicios después de SOA: SOA tiene limitaciones en escalabilidad, desarrollo rápido y deployments frecuentes [CL11-INT, p. 12], y los microservicios responden al desafío de moverse rápido sin romper nada. [CL11-INT, p. 14]; [CL11-INT, p. 18]

Clark advierte que compararlos directamente es engañoso, porque aplican a **alcances distintos**: [B05, p. 11]; [B05, p. 12]

- **SOA tiene alcance empresarial.** Es una iniciativa para crear servicios y APIs reutilizables, disponibles en forma sincrónica, de modo que las aplicaciones nuevas se construyan más rápido. Mira cómo se integran las aplicaciones entre sí.
- **Los microservicios tienen alcance de aplicación.** Son una opción para escribir una aplicación individual de forma más ágil, escalable y resiliente. Miran cómo se construye su interior.

Algunos principios son **incompatibles si se aplican al mismo alcance**:

| Aspecto | SOA, entre aplicaciones | Microservicios, dentro de una aplicación |
|---|---|---|
| Reutilización | Es el objetivo principal | Se desalienta, porque crea dependencias en tiempo de ejecución; se prefiere reutilizar copiando |
| Llamadas sincrónicas | Predominan, por ejemplo con APIs RESTful | Crean dependencias en tiempo real, con pérdida de resiliencia y latencia; se prefiere la mensajería |
| Datos | Cada aplicación accede a la fuente primaria y evita la sincronización | Se acepta la duplicación, por ejemplo con event sourcing; igual hace falta una fuente de verdad acordada para cada tipo de dato |
| Balanceo de carga | En el gateway | Del lado del cliente, porque los componentes se asumen volátiles |

La tabla resume [B05, p. 11]; [B05, p. 12]; [B07, p. 6]; [B07, p. 11].

La discusión también depende de qué se entienda por SOA: [B07, p. 7]

- **SOA como integración:** cómo exponer servicios desde sistemas legados complejos. En ese caso es un problema de conectividad, a otra escala que los microservicios.
- **SOA como componentes:** refactorizar el panorama de TI en componentes alineados con el negocio. En ese caso los microservicios pueden verse como «SOA más granular» o «SOA bien hecha».

Por eso las opiniones se dividen: en una **gran empresa madura**, los microservicios son un estilo de aplicación más, y exponer servicios es un desafío de integración y de datos. En una **startup nueva**, casi todo el panorama puede ser de microservicios, y el panorama *es* una arquitectura orientada a (micro)servicios. [B07, p. 8]

Clark cierra con un aviso sobre comparaciones confusas. «Microservicios vs. SOA» compara componentes con una arquitectura; lo comparable es arquitectura de microservicios con SOA. «Microservicios vs. APIs» compara un componente con una interfaz. Y «servicio» significa cosas distintas para distintas personas, así que hay que precisar el término. [B07, p. 13]

**Inferencia para responder en evaluaciones:** seguir la narrativa de la clase —microservicios como respuesta a las limitaciones de SOA para entregar rápido— y aclarar que, según Clark, SOA y microservicios operan a escalas distintas y pueden convivir: microservicios dentro de cada aplicación y exposición estandarizada entre aplicaciones.

## Arquitectura de integración ágil

Clark propone aplicar a la integración los mismos principios de los microservicios. Llama a esto **arquitectura de integración ágil**, antes conocida como integración liviana. [B05, p. 12]; [B06, p. 3] Describe tres enfoques: [B06, p. 8]

| Enfoque | Idea | Beneficio | Evidencia |
|---|---|---|---|
| Despliegue de integración de grano fino | Partir el ESB centralizado en componentes chicos, cada uno con unas pocas integraciones, en contenedores orquestados, por ejemplo, con Kubernetes | Cambiar, versionar y escalar cada integración sin desestabilizar a las demás | [B06, p. 2]; [B06, p. 3]; [B07, p. 19] |
| Propiedad descentralizada de la integración | Los equipos de aplicación crean y mantienen sus integraciones y administran la exposición de sus APIs | Menos equipos involucrados; quien integra conoce las estructuras de datos de su aplicación | [B06, p. 3]; [B06, p. 4]; [B06, p. 5]; [B07, p. 20] |
| Infraestructura de integración *cloud-native* | Usar un *integration runtime* liviano como un componente más dentro de una aplicación de microservicios | Resolver composición, mapeo de datos o ingesta de eventos con conectores y configuración en lugar de mucho código | [B06, p. 6]; [B06, p. 7]; [B07, p. 21] |

Detalles y advertencias:

- **Runtimes modernos:** no dependen de bases de datos ni colas; se instalan copiándolos al sistema de archivos; se configuran con archivos de propiedades y CLI; arrancan en segundos y los administra un orquestador. [B06, p. 3]
- **Costos:** más piezas móviles y la curva de aprendizaje de contenedores y orquestación. [B06, p. 3]
- **La descentralización es un cambio organizacional, no técnico.** No sirve para todos: puede faltar experiencia en los equipos de aplicaciones antiguas, y algunas organizaciones preferirán seguir con un equipo central. [B06, p. 5]
- Descentralizar la propiedad no implica descentralizar la infraestructura: los equipos pueden administrar sus APIs sobre un gateway compartido, *multi-tenant*. [B06, p. 5]; [B07, p. 20]
- **Riesgo de la autonomía: la divergencia.** Si cada equipo diseña sus APIs con su propio estilo, se complica reutilizarlas. En SOA se intentó imponer estándares rígidos; con REST es más común converger en convenciones. [B06, p. 5]
- **No se recrea un ESB dentro de la aplicación.** Un *integration runtime* no es un ESB: el ESB es un patrón centralizado de alcance empresarial, y el runtime es solo una herramienta que puede participar en distintos patrones. [B06, p. 7]; [B06, p. 8]
- Los tres enfoques son **decisiones arquitectónicas independientes** y pueden adoptarse en cualquier orden. Si cada equipo tiene su propio bus, se habla de un *application service bus* o *domain service bus*. Lo habitual son arquitecturas híbridas: un ESB estable para lo que no conviene refactorizar y runtimes livianos para lo nuevo. [B06, p. 8]; [B06, p. 9]

**¿Volvimos al punto a punto?** No. El problema original era que los protocolos eran muchos y variados y que cada integración exigía código complejo en el consumidor y en el proveedor. Hoy los proveedores ofrecen APIs RESTful, las herramientas de integración resuelven mapeo, ruteo, resiliencia y seguridad por configuración, y la gestión de APIs permite descubrirlas, suscribirse, medir el uso, exponerlas afuera e incluso monetizarlas. [B06, p. 9]; [B06, p. 10]

Sobre el término ESB, Clark sostiene que el **único componente obligatorio del patrón es el gateway de exposición**. Administrar la exposición de una API debería poder hacerlo el equipo de la aplicación, sin un equipo de especialistas. El hub de integración se reserva para lo que lo necesita: conectividad profunda, composición compleja, mapeo detallado, transaccionalidad o transportes asíncronos. Si solo hay que exponer y rutear una API sincrónica, alcanza con un gateway. [B07, p. 18] Como el uso del término está «suficientemente roto», propone abandonarlo. [B07, p. 19]

La **arquitectura de referencia de integración híbrida** resume el panorama en capas: canales externos —móvil, socios, economía de APIs, IoT y SaaS—; un gateway de APIs y eventos; sistemas de interacción con conectividad «digital» —composición de APIs, eventos y sincronización de datos—; otro gateway; y conectividad «de bajo nivel» hacia los sistemas de registro de las operaciones centrales. Un eje de afinidad con la nube va de *on-premise* a XaaS. [B07, p. 17]

## Atributos de calidad y trade-offs

**Síntesis entre fuentes:**

| Enfoque | Favorece | Cuesta | Evidencia |
|---|---|---|---|
| Punto a punto | Simplicidad inicial | Acoplamiento, mantenibilidad; cada sistema nuevo toca medio mapa | [CL11-INT, p. 2]; [CL11-INT, p. 10] |
| Hub / ESB / SOA | Reutilización, bajo acoplamiento, gestión centralizada, interoperabilidad con legados | Peso del gobierno; escalabilidad y tolerancia a fallos de la infraestructura central; velocidad de entrega | [CL11-INT, p. 4]; [CL11-INT, p. 12]; [B05, p. 5] |
| Microservicios | Velocidad de entrega, escalado independiente, resiliencia | Complejidad distribuida, datos, trazabilidad, latencia, coordinación | [CL11-INT, p. 18]; [CL11-INT, p. 20]; [B07, p. 3] |
| Integración ágil | Agilidad, escalado y resiliencia de cada integración | Más piezas móviles; riesgo de divergencia entre equipos | [B06, p. 2]; [B06, p. 3]; [B06, p. 5] |

**Inferencia:** la **interoperabilidad**, definida en la clase 9 como integración con otros sistemas [CL09-P, p. 22], es el atributo que motiva toda la unidad. Cada arquitectura la resuelve con otro equilibrio entre acoplamiento, gobierno y velocidad de cambio.

## Conexiones

- **[Estilos arquitectónicos](estilos-arquitectonicos.md).** El integration hub y el ESB funcionan como un *broker*: un intermediario central que desacopla y enruta. La mensajería entre microservicios usa publish–subscribe, y el event sourcing es una forma de [sistema basado en eventos](estilos-arquitectonicos.md#sistemas-basados-en-eventos). La descomposición por subdominio se opone a la división en capas técnicas. [CL08-P, p. 35]; [CL08-P, p. 38]; [CL11-INT, p. 22]; [B07, p. 22] **Inferencia.**
- **[Persistencia](persistencia.md).** Cada microservicio tiene sus propios datos, y eso plantea cómo coordinar transacciones entre varias bases. Clark menciona ACID, BASE, CQRS y event sourcing como opciones. [CL11-INT, p. 19]; [B07, p. 2]; [B07, p. 3]
- **[Atributos de calidad](arquitectura-y-atributos-de-calidad.md).** La interoperabilidad es un atributo run-time propio en la clase 7. [CL07-P, p. 21]
- **[Evaluación de arquitecturas](evaluacion-de-arquitecturas.md).** Las métricas DORA miden el proceso de entrega; los SLI y SLO, el servicio en producción. Las dos clases de métricas sirven para formular escenarios medibles. **Inferencia.**
- **[Metodologías](metodologias-clasicas-y-agiles.md) y [calidad](calidad-de-software.md).** DevOps, integración y entrega continuas, tests automatizados y equipos pequeños y autónomos son condición para que los microservicios funcionen. [CL11-INT, p. 18]; [CL11-INT, p. 25]; [B07, p. 2]
- **[Caso HealthCare.gov](caso-healthcare-gov.md).** El Data Services Hub enruta consultas entre los mercados federal y estatales y las agencias que verifican la información, como un hub de integración. [B04, p. 10]; [B04, p. 21] **Inferencia:** su rol central lo vuelve un punto crítico de disponibilidad y performance.
- **[Consignas de práctica](../consignas-de-practica.md).** Los casos 2 y 3 del Cross Challenge integran agregadores de viajes y aseguradoras externos. [CROSS-2026-05, p. 1]; [CROSS-2026-05, p. 2]
