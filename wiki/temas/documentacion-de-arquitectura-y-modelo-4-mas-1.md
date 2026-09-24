# Documentación de arquitectura y modelo 4+1

> **Alcance:** esta clase es posterior al recorte del primer parcial y no aparece en él. Ver [alcance del primer parcial](../parcial-1-alcance.md). Fuentes: primera mitad de la clase 8 (`CL08-P`, pp. 1–23), el paper de Kruchten (`B01`), indicado en clase como lectura para el hogar y como bibliografía recomendada [CL08-P, p. 5]; [CL08-P, p. 59], y el paper de Robal, Viies y Kruus (`B02`). Las páginas de `B01` y `B02` siguen la numeración del PDF: la página 1 de cada uno es una portada de ResearchGate.

## Para qué documentar una arquitectura

Una descripción de arquitectura es un conjunto de artefactos que permite a los stakeholders entender, validar y criticar la arquitectura, y proponer mejoras. [CL08-P, p. 2] Debe ayudar a responder preguntas como cuáles son los elementos funcionales principales, cómo interactúan, qué información se maneja, persiste y presenta, qué software y hardware hacen falta, qué capacidades operacionales se prevén y qué ambientes de desarrollo, prueba, soporte y capacitación se necesitan. [CL08-P, p. 3]

Describir una arquitectura implica documentar decisiones sobre código, performance, flujos de datos, estilo y funcionalidad, entre otras. [CL08-P, p. 9] El nivel de detalle debe ser el adecuado —visión general, detalle particular y suficiente para validar y desarrollar—, y conviene evitar una descripción que incluya todo. [CL08-P, p. 4] Kruchten ilustra el problema: un único diagrama de cajas y flechas suele mezclar programas en ejecución, código fuente, computadoras y agrupamientos lógicos, y sus flechas pueden ser dependencias, flujo de control o flujo de datos a la vez. [B01, p. 2] **Inferencia:** separar las preocupaciones en vistas es la respuesta a ese exceso de carga en un solo diagrama.

## Vistas, viewpoints y estándares

Existen varios «estándares» para documentar —views and viewpoints, Views and Beyond, el modelo 4+1 e IEEE 1471— y todos se parecen: usan distintas vistas y cada una tiene un foco distinto. [CL08-P, p. 5]

- **View:** representación de la arquitectura hecha con un objetivo y para un grupo de interés. **Viewpoint:** plantilla o «receta» que define cómo construir una vista: notación, elementos incluidos y destinatarios. Ejemplo: el diagrama de clases del sistema de ventas es una vista; «uso UML, muestro clases de dominio, omito infraestructura, destinado a desarrolladores» es el viewpoint. [CL08-P, p. 6]
- **Views and Beyond:** método práctico que propone tres categorías de vistas —módulo, componente y conector, y asignación— y agrega información más allá de las vistas: escenarios, decisiones arquitectónicas y justificaciones. [CL08-P, p. 7]
- **IEEE 1471:** primer estándar formal de descripción de arquitectura (año 2000); introdujo oficialmente views y viewpoints para documentar de forma consistente y comprensible para distintos stakeholders. Evolucionó a ISO/IEC/IEEE 42010, cuya primera versión es de 2011 y cuya segunda versión, vigente, es de 2022. [CL08-P, p. 8]

## Modelo 4+1 de Kruchten

Kruchten propone describir la arquitectura mediante varias vistas concurrentes, cada una dirigida a las preocupaciones de distintos stakeholders, para tratar por separado requerimientos funcionales y no funcionales. [B01, p. 2] Parte de la fórmula de Perry y Wolf, modificada por Boehm: **arquitectura = {elementos, formas, fundamento/restricciones}**, y la aplica de manera independiente en cada vista. [B01, p. 2]; [B01, p. 3] Como cada vista puede adoptar su propio estilo arquitectónico, un mismo sistema puede combinar varios estilos. [B01, p. 3]

Las decisiones se organizan en cuatro vistas y se ilustran con algunos casos de uso o escenarios, que forman la quinta vista: el «+1». [B01, p. 3]; [CL08-P, p. 10]; [CL08-P, p. 11]

| Vista | Pregunta que responde | Stakeholders | Preocupaciones principales |
|---|---|---|---|
| Lógica | ¿Cómo se organiza el sistema según su funcionalidad? | Usuario final | Funcionalidad |
| Procesos | ¿Cómo se comporta en tiempo de ejecución? | Integradores, diseñador del sistema | Performance, disponibilidad, tolerancia a fallos, integridad, escalabilidad, concurrencia y sincronización |
| Desarrollo | ¿Cómo se organiza el software en el entorno de desarrollo? | Programadores, gestión del software | Organización, reuso, portabilidad, línea de productos |
| Física | ¿Dónde y cómo se ejecuta sobre la infraestructura? | Ingenieros de sistemas | Topología, comunicaciones, escalabilidad, performance, disponibilidad |
| Escenarios (+1) | ¿Qué comportamientos clave muestran que las demás vistas funcionan juntas? | Usuario final, desarrollador | Comprensibilidad y validación |

Las preguntas provienen de [CL08-P, p. 14], [CL08-P, p. 15] y [CL08-P, p. 16]; los stakeholders y preocupaciones, de [CL08-P, p. 11], [B01, p. 3] y [B01, p. 16].

| Vista | Componentes | Conectores | Contenedores | Diagramas UML indicados en clase |
|---|---|---|---|---|
| Lógica | Clase | Asociación, herencia, contención | Categoría de clases | Clases; modelo de dominio o DER |
| Procesos | Tarea | Rendezvous, mensaje, broadcast, RPC | Proceso | Actividad, y según otra diapositiva también secuencia y comunicación |
| Desarrollo | Módulo, subsistema | Dependencia de compilación, cláusulas `with`/`include` | Subsistema (biblioteca) | Paquetes y componentes |
| Física | Nodo | Medio de comunicación: LAN, WAN, bus | Subsistema físico | Despliegue |
| Escenarios | Paso, script | — | — | Casos de uso o secuencia |

Los elementos de notación resumen la tabla de Kruchten [B01, p. 15]; [B01, p. 16]. La columna de diagramas combina [CL08-P, p. 10], [CL08-P, p. 12], [CL08-P, p. 14], [CL08-P, p. 15] y [CL08-P, p. 16]. **Advertencia:** la asignación de diagramas de secuencia y comunicación no es uniforme entre fuentes; ver [Dudas y conflictos](../dudas-y-conflictos.md).

### Vista lógica

Sostiene principalmente los requerimientos funcionales. Descompone el sistema en abstracciones clave del dominio, en forma de objetos o clases, aplicando abstracción, encapsulamiento y herencia; también sirve para detectar mecanismos y elementos comunes. Kruchten la representa con diagramas y plantillas de clases, usa diagramas de estados cuando importa el comportamiento interno de un objeto y admite diagramas entidad-relación en aplicaciones muy orientadas a datos. [B01, p. 4] Su estilo es orientado a objetos, y la regla principal es mantener un único modelo de objetos coherente en todo el sistema, sin especializaciones prematuras por sitio o procesador. [B01, p. 4]

### Vista de procesos

Atiende requerimientos no funcionales como performance y disponibilidad: concurrencia, distribución, integridad, tolerancia a fallos y en qué hilo de control se ejecuta cada operación de un objeto. [B01, p. 5] Un **proceso** agrupa tareas que forman una unidad ejecutable; es el nivel que se inicia, recupera, reconfigura y detiene, y puede replicarse para repartir carga o mejorar disponibilidad. [B01, p. 5]; [B01, p. 6] Las **tareas principales** son elementos arquitectónicos que se comunican mediante mecanismos bien definidos —mensajes síncronos o asíncronos, RPC, broadcast de eventos—; las **tareas menores** se agregan localmente por razones de implementación, como buffers o timeouts. [B01, p. 6] Sobre esta vista pueden estimarse flujos de mensajes y cargas, e incluso probarse una arquitectura «hueca» con cargas simuladas. Pipes and filters y cliente/servidor son estilos posibles. [B01, p. 6]

### Vista de desarrollo

Muestra la organización real de los módulos en el entorno de desarrollo: bibliotecas o subsistemas que puede desarrollar una persona o un grupo pequeño, organizados en capas con interfaces estrechas y bien definidas. [B01, p. 7] Responde a requerimientos internos —facilidad de desarrollo, gestión del software, reuso, restricciones de lenguaje y herramientas— y es la base para asignar requerimientos y trabajo a equipos, estimar costos, planificar, seguir el avance y razonar sobre reuso, portabilidad y seguridad. [B01, p. 7] Kruchten recomienda un estilo en capas, con cuatro a seis capas de subsistemas: un subsistema solo depende de subsistemas de su misma capa o de capas inferiores. [B01, p. 8]

### Vista física

Atiende sobre todo requerimientos no funcionales: disponibilidad, confiabilidad (tolerancia a fallos), performance (throughput) y escalabilidad. Asigna redes, procesos, tareas y objetos a nodos de procesamiento. Como habrá configuraciones distintas para desarrollo, pruebas y despliegue en cada cliente o sitio, esa asignación debe ser flexible e impactar lo menos posible en el código fuente. [B01, p. 9]

### Escenarios: el «+1»

Un conjunto reducido de escenarios importantes —instancias de casos de uso más generales— muestra que los elementos de las cuatro vistas trabajan juntos; para cada escenario se describe un script de interacciones entre objetos y entre procesos. [B01, p. 10] La vista es redundante respecto de las otras —de ahí el «+1»—, pero cumple dos propósitos: **guiar el descubrimiento** de elementos arquitectónicos durante el diseño y **validar e ilustrar** la arquitectura una vez diseñada, como punto de partida de las pruebas del prototipo. [B01, p. 10] En la clase se resume así: usa, por ejemplo, casos de uso, valida la arquitectura y explica cómo interactúan objetos y procesos en un caso típico. [CL08-P, p. 13]

### Correspondencia entre vistas

Las vistas no son ortogonales: los elementos de una se conectan con los de otras mediante reglas y heurísticas de diseño. [B01, p. 11]

- **Lógica → procesos:** se analiza la autonomía (objetos activos, pasivos o protegidos), la persistencia, la subordinación y la distribución de las clases. Para decidir cuánta concurrencia hace falta, se combinan dos estrategias: *inside-out*, que agrupa objetos lógicos en tareas agentes hasta obtener pocos procesos, y *outside-in*, que parte de los estímulos externos y define procesos cliente y servidor. Llegar a un compromiso aceptable requiere varias iteraciones. [B01, p. 11]; [B01, p. 12]
- **Lógica → desarrollo:** una clase suele implementarse como módulo y las categorías de clases se agrupan en subsistemas, pero también pesan la organización de equipos, el tamaño esperado del código, el reuso, el layering y la política de releases. Por eso no hay correspondencia uno a uno, y cuanto mayor es el proyecto, más se distancian ambas vistas. [B01, p. 13]
- **Procesos → física:** procesos y grupos de procesos se asignan al hardware en distintas configuraciones de prueba o despliegue. [B01, p. 13]
- **Escenarios:** se relacionan sobre todo con la vista lógica y con la de procesos cuando la interacción involucra más de un hilo de control. [B01, p. 13]

### Adaptación del modelo

No toda arquitectura necesita las cinco vistas. Puede omitirse la vista física si hay un solo procesador, y la de procesos si hay un solo proceso; en sistemas muy pequeños, la vista lógica y la de desarrollo pueden coincidir. Los escenarios son útiles siempre. [B01, p. 14] La clase agrega que el modelo se adapta a cada caso suprimiendo o combinando vistas y usando distintos diagramas, que la descripción evoluciona junto con la arquitectura y que las vistas, complejas e interrelacionadas, no deben contradecirse. [CL08-P, p. 17]

### Proceso iterativo guiado por escenarios

Kruchten considera demasiado lineal un diseño arquitectónico en fases sucesivas y propone prototipar, probar, medir, analizar y refinar la arquitectura en iteraciones. El prototipo es evolutivo: crece hasta convertirse en el sistema, no se descarta. [B01, p. 14]

1. **Inicio:** elegir pocos escenarios por riesgo y criticidad; montar una arquitectura preliminar; hacer el script de los escenarios para identificar abstracciones principales; volcarlas en los cuatro blueprints; implementar, probar, medir y registrar lecciones. [B01, p. 14]
2. **Ciclo:** reevaluar riesgos, ampliar la paleta de escenarios, hacer el script de los nuevos, descubrir elementos o cambios, actualizar los blueprints y el prototipo, probar bajo carga, revisar los cinco blueprints buscando simplificación y reuso, y actualizar guías y fundamentos. [B01, p. 14]
3. **Estabilización:** tras dos o tres iteraciones la arquitectura debería estabilizarse, sin nuevas abstracciones, subsistemas, procesos ni interfaces importantes. Una iteración puede durar de 2–3 semanas en un proyecto chico hasta 6–9 meses en un gran sistema de comando y control. [B01, p. 14]; [B01, p. 15]

Los escenarios críticos son las funciones más importantes, las de mayor frecuencia de uso o las que presentan riesgo técnico significativo. [B01, p. 14] **Inferencia:** coinciden con lo que la clase 7 llama drivers de arquitectura; ver [atributos de calidad](arquitectura-y-atributos-de-calidad.md#attribute-driven-design-restricciones-y-drivers).

### Documento de arquitectura

El diseño arquitectónico produce dos documentos: el **Software Architecture Document**, organizado según las vistas 4+1, y las **Software Design Guidelines**, que registran las decisiones que deben respetarse para mantener la integridad arquitectónica. [B01, p. 15] El esqueleto propuesto incluye alcance, referencias, arquitectura, objetivos y restricciones arquitectónicas, una sección por cada vista, escenarios, tamaño y performance, calidad y apéndices. [B01, p. 15]; [CL08-P, p. 18]

Otros conjuntos de vistas suelen poder plegarse sobre estas cuatro: una vista de costos y cronograma cabe en la de desarrollo, una de datos en la lógica y una de ejecución en la combinación de procesos y física. [B01, p. 15]

## Ejemplos de clase

- **Netflix:** la vista lógica muestra usuarios, catálogo, reproducción, recomendaciones y pagos; la de procesos sigue qué pasa al apretar «Play» —cliente, autenticación, catálogo, streaming por CDN y registro de eventos para recomendaciones— atendiendo concurrencia, comunicación y latencia; la física ubica apps en dispositivos, backend en múltiples regiones, CDN global y bases de datos replicadas. [CL08-P, p. 19] Un diagrama de componentes UML de la vista de procesos distingue comunicación síncrona y asíncrona. [CL08-P, p. 20]
- **Sistema de neutralización de minas:** la actividad pide clasificar diez figuras de un caso publicado en las cinco vistas, con este resumen: lógica = estructura funcional; procesos = ejecución dinámica; desarrollo = organización del código; física = despliegue en hardware; escenarios = validación de las anteriores. [CL08-P, p. 21] La resolución asigna a la vista lógica los componentes principales, la vista conceptual MVC, el modelo de dominio y los diseños de alto nivel del sonar y del controlador; a desarrollo, el estilo star-controller; a procesos, el diagrama de estados del control del vehículo; y a escenarios, los casos de uso. Los subsistemas del vehículo (lógica o desarrollo) y la arquitectura en capas (lógica o procesos) quedan marcados como dudosos por la propia cátedra. [CL08-P, p. 22] El paper del caso no está incorporado al repositorio.

## RUP y 4+1 en aplicaciones web

La clase 2 ya presentaba el 4+1 como la forma en que RUP representa su arquitectura centrada en vistas. [CL02-A, p. 6]; [CL02-A, p. 7] Robal, Viies y Kruus aplican esa combinación al sitio web de un departamento universitario. [B02, p. 2]

- **Por qué RUP:** desarrollo iterativo ante requerimientos web inestables, gestión de requerimientos con casos de uso, arquitectura basada en componentes, modelado visual con UML, verificación de calidad y control de cambios. [B02, p. 3]; [B02, p. 4]
- **Vistas aplicadas a la web:** en la vista lógica ubican casos de uso, clases y estados, requerimientos no funcionales, glosario, brief creativo y mapa de navegación. [B02, p. 6] En la de desarrollo, la plataforma de realización (Apache con PHP4), el reuso, las restricciones, el modelo lógico de datos y los elementos de diseño visual. [B02, p. 7] En la de procesos, clases y métodos que realizan la funcionalidad, requerimientos no funcionales de implementación y prototipos de interfaz. En la física, la integración de los elementos anteriores bajo requerimientos de confiabilidad, performance y escalabilidad, las configuraciones y el modelo físico de datos. Los escenarios se expresan con diagramas de interacción, como el inicio de sesión. [B02, p. 8]; [B02, p. 9]
- **Interfaz y navegación:** el desarrollo de la interfaz sigue siete pasos, del brief creativo al mapa de navegación completo; se comparan navegación superior, vertical, superior-vertical y dividida. [B02, p. 9]; [B02, p. 10]; [B02, p. 11] Un análisis de logs del sitio encontró que en el 79 % de las sesiones hubo una sola operación y que la información buscada se alcanzaba en unos 22 segundos en promedio; los autores concluyen que la navegación no necesitaba reorganizarse. [B02, p. 12]; [B02, p. 13]
- **Datos:** el modelo lógico se deriva de la vista lógica y se normaliza; el modelo físico lo adapta al gestor elegido, con claves, índices, restricciones, vistas y triggers, y puede desnormalizarse por performance. [B02, p. 14]; [B02, p. 15]

**Advertencia:** este paper difiere de Kruchten y de la clase en varios puntos. Agrega una quinta fase a RUP (Evolution), asocia la vista física al punto de vista del usuario final y ubica los casos de uso en la vista lógica. [B02, p. 4]; [B02, p. 5]; [B02, p. 6] Ver [Dudas y conflictos](../dudas-y-conflictos.md). **Inferencia:** conviene leerlo como un ejemplo de adaptación (*tailoring*) del modelo, no como su definición.

## Conexiones

- La vista describe *cómo es* la arquitectura; los [estilos arquitectónicos](estilos-arquitectonicos.md) guían *cómo diseñarla*. [CL08-P, p. 23]; [CL08-P, p. 58]
- Los escenarios y drivers conectan el 4+1 con los [atributos de calidad](arquitectura-y-atributos-de-calidad.md).
- RUP y su arquitectura en vistas aparecen en [metodologías](metodologias-clasicas-y-agiles.md).
