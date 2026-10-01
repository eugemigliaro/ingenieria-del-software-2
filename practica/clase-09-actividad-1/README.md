# Clase 9 — Actividad 1: estilos de arquitectura para YOLO

## Consigna

> Cada grupo trabaja sobre su producto. Consigna:
> - Definir un pipeline dataflow interno.
> - Seleccionar un estilo distribuido (broker, pub-sub, etc.) para la comunicación.
> - Seleccionar manejo de eventos.
>
> [CL09-P, p. 2]

La diapositiva muestra junto a la consigna las tres familias entre las que hay que elegir: **dataflow** (batch secuencial, pipes & filters, capas jerárquicas), **sistemas distribuidos** (broker, publish–subscribe, forwarder–receiver, client–dispatcher–server) y **sistemas basados en eventos** (single, stream, complex y online event processing). [CL09-P, p. 2] La teoría de cada estilo está en la clase 8 y resumida en la wiki, en [estilos arquitectónicos](../../wiki/temas/estilos-arquitectonicos.md).

El producto es **YOLO**, la plataforma de exploración vocacional del grupo. Su business case está en [producto-yolo.md](producto-yolo.md); abajo se cita por sección, por ejemplo §1A.

## Respuesta en una tabla

| Consigna | Decisión | Por qué, en una línea |
|---|---|---|
| Pipeline dataflow interno | **Pipes & filters**: captura → validación → enriquecimiento → cálculo de tiempo → actualización del recorrido. Lo complementa una consolidación nocturna en **batch secuencial** para los reportes. | La actividad del alumno llega como un flujo continuo, y el alumno necesita ver su avance al instante para desbloquear el nivel siguiente. |
| Estilo distribuido | **Publish–subscribe** | Un mismo hecho («completó el nivel 2 de Medicina») les interesa a varios consumidores que el productor no tiene por qué conocer: el dashboard de los padres, los reportes del colegio, las notificaciones y las métricas de negocio. |
| Manejo de eventos | **Event Stream Processing** | El valor diferencial de YOLO —el recorrido con áreas, tiempo y profundidad— es una agregación en línea sobre un flujo continuo de interacciones. |

Las tres decisiones forman un mismo sistema basado en eventos. El pipeline transforma el flujo, pub-sub es el canal y el tipo de procesamiento es stream.

## Supuestos

El business case no fija estos puntos. Conviene validarlos con el grupo, porque si alguno cambia puede cambiar la decisión.

1. **Clientes:** una aplicación web para el alumno y un dashboard para padres y tutores (§8A menciona «utilización del dashboard»). Colegios y profesionales consultan reportes (§3A).
2. **Escala:** el piloto abarca uno o dos colegios, es decir, cientos de alumnos. En la expansión de los meses 10–12 se llega a algunos miles. Son órdenes de magnitud estimados, no datos del business case.
3. **Latencia:** el alumno necesita ver su progreso enseguida, porque los módulos «se profundizan progresivamente» (§1A). A los padres les alcanza con datos del día y a las métricas de negocio, con datos del mes (§3B).
4. **Equipo y costos:** el equipo es chico y el presupuesto de infraestructura, acotado. La infraestructura es un costo directo (§5A) y los «costos superiores a los previstos» son motivo de ajuste del proyecto (§7B).
5. **Pagos:** las suscripciones se cobran con un proveedor de pagos externo (conocimiento general; el business case solo dice que las familias pagan una mensualidad).
6. **Usuarios menores de edad:** los datos de exploración son de menores, así que la privacidad importa (conocimiento general).

## Requisitos que guían la elección

Un ASR es un requisito, funcional o de calidad, cuya satisfacción obliga a tomar decisiones arquitectónicas clave: si cambiara, probablemente cambiaría la arquitectura. [CL09-P, p. 7] En el business case aparecen estos:

| Requisito | Fuente | Qué decisión empuja |
|---|---|---|
| Registrar el recorrido de cada alumno: áreas exploradas, tiempo dedicado y profundidad alcanzada | §1A, §2B (es el «valor diferencial») | Hace falta un pipeline que convierta interacciones sueltas en un recorrido |
| Los módulos se profundizan progresivamente | §1A | El avance tiene que procesarse con baja latencia; descarta un batch como camino principal |
| La misma información la usan alumnos, padres, colegios y el equipo de YOLO | §3A, §3B, §8A | Varios consumidores desacoplados del productor: pub-sub |
| Métricas y contenido cambian según los resultados del piloto | §4B, §7B | Modificabilidad: poder agregar consumidores o filtros sin tocar lo existente |
| Pasar del piloto a la expansión en varios colegios | §5B | Escalabilidad |
| Costos de infraestructura acotados | §5A, §7B | Restricción: no sobredimensionar la infraestructura en el MVP |

## Decisión 1 — Pipeline dataflow interno: pipes & filters

### El pipeline

Es el **pipeline del recorrido de exploración**. Vive dentro del servicio de exploración y transforma cada interacción del alumno en un recorrido actualizado.

```
Interacción del alumno (abre un módulo, avanza, completa un nivel, sale)
        │
        ▼
[1] Captura ............... evento crudo {alumno, sesión, módulo, tipo, hora}
        │ pipe
        ▼
[2] Validación ............ descarta duplicados, alumnos sin suscripción activa,
        │ pipe              módulos inexistentes y horas incoherentes
        ▼
[3] Enriquecimiento ....... agrega área, carrera, nivel de profundidad del módulo,
        │ pipe              colegio y curso del alumno
        ▼
[4] Cálculo de tiempo ..... agrupa eventos en sesiones y descuenta la inactividad
        │ pipe              para obtener el tiempo efectivo por módulo y por área
        ▼
[5] Actualización ......... áreas exploradas, tiempo acumulado por área y profundidad
    del recorrido           máxima; si se completó un nivel, desbloquea el siguiente
        │
        ▼
Publica eventos de dominio en el canal publish–subscribe (decisión 2)
```

| Filtro | Entrada | Salida | Para qué sirve en YOLO |
|---|---|---|---|
| 1. Captura | Acción del alumno en la interfaz | Evento crudo | Registrar cada paso de la exploración sin frenar la experiencia |
| 2. Validación | Evento crudo | Evento válido | Que las métricas no se inflen con reintentos del navegador ni con usuarios sin acceso |
| 3. Enriquecimiento | Evento válido | Evento con contexto | Saber a qué área y a qué nivel de profundidad corresponde cada interacción |
| 4. Cálculo de tiempo | Evento con contexto | Tiempo efectivo de la sesión | Medir el «tiempo dedicado» (§1A) sin contar una pestaña abierta y abandonada |
| 5. Actualización del recorrido | Tiempo y evento con contexto | Recorrido actualizado y eventos de dominio | Mantener el recorrido que ven alumno y padres, y desbloquear niveles |

### Por qué pipes & filters

- **Los datos llegan como flujo.** Cada alumno genera interacciones continuas mientras usa la plataforma. La clase indica: ¿flujo continuo? → pipes & filters, con «flujo» como palabra clave. [CL08-P, p. 33] El estilo resuelve el procesamiento de datos en flujo continuo mediante filtros independientes conectados. [CL08-P, p. 27]
- **Cada filtro hace una sola transformación.** Validar, enriquecer, calcular tiempo y actualizar son exactamente las operaciones que la clase atribuye a los filtros del ejemplo con Kafka: validar, transformar, enriquecer o filtrar. [CL08-P, p. 33]
- **Flexibilidad para iterar después del piloto.** El trade-off del estilo es «más flexible, más complejo de coordinar». [CL08-P, p. 27] **Inferencia:** esa flexibilidad es la que pide el business case, que prevé ajustar métricas y contenido según el piloto (§4B, §7B). Si el piloto pide una métrica nueva, por ejemplo «áreas que el alumno revisitó», se agrega un filtro sin reescribir los demás.

### Complemento: consolidación nocturna en batch secuencial

Los reportes no necesitan inmediatez: un resumen para tutores, un reporte por curso para el colegio y las métricas mensuales de alumnos activos, frecuencia de uso, suscripciones e ingresos (§3B, §8A). Para ellos se agrega un proceso **batch secuencial** nocturno que lee los recorridos acumulados y genera los reportes en etapas: extraer, agregar por alumno, agregar por curso y colegio, y publicar. Es el caso de uso que la clase asigna al batch: procesamiento nocturno en pipelines donde no importa la latencia. [CL08-P, p. 26] Combinar estilos es válido porque se aplican en contextos distintos. [CL08-P, p. 24]

### Estilos descartados

- **Batch secuencial como pipeline principal:** su trade-off es «simple pero lento (alta latencia)». [CL08-P, p. 26] Si el recorrido se actualizara una vez por noche, el alumno que termina un nivel tendría que esperar al día siguiente para desbloquear el próximo. Eso contradice la experiencia progresiva de §1A. Queda solo para los reportes.
- **Capas jerárquicas:** resuelven otro problema, «organizar complejidad» (palabra clave «organización»), y no describen cómo se transforma un flujo de datos. [CL08-P, p. 28]; [CL08-P, p. 33] **Inferencia:** la aplicación sí puede organizarse en capas (presentación, lógica de negocio y datos), pero esa decisión corresponde a la vista de desarrollo de la Actividad 2, donde Kruchten recomienda el estilo en capas. [B01, p. 8]

## Decisión 2 — Estilo distribuido: publish–subscribe

### Componentes y canal

```
 Servicio de exploración   Servicio de suscripciones   Gestión de contenidos
 (contiene el pipeline)    (proveedor de pagos)        (equipo YOLO)
          │ publica                 │ publica                │ publica
          ▼                         ▼                        ▼
 ═══════════════════════ Canal publish–subscribe ═══════════════════════
     nivel.completado · recorrido.actualizado · sesion.finalizada
     suscripcion.activada · suscripcion.vencida · contenido.publicado
          │                │                 │                 │
          ▼                ▼                 ▼                 ▼
    Dashboard de      Reportes del      Notificaciones     Métricas de
   padres/tutores       colegio           a tutores          negocio
```

| Tópico | Lo publica | Se suscriben | Para qué |
|---|---|---|---|
| `nivel.completado` | Servicio de exploración (filtro 5) | Notificaciones, reportes, métricas | Avisar al tutor de un hito; contar profundidad alcanzada |
| `recorrido.actualizado` | Servicio de exploración (filtro 5) | Dashboard de padres y tutores, reportes del colegio | Mantener la vista que consultan las familias y los profesionales |
| `sesion.finalizada` | Servicio de exploración (filtro 4) | Métricas de negocio | Tiempo de uso y frecuencia (§3B) |
| `suscripcion.activada` / `suscripcion.vencida` | Servicio de suscripciones | Servicio de exploración, métricas de negocio | Habilitar o bloquear el acceso (lo usa el filtro de validación); suscripciones e ingresos (§3B) |
| `contenido.publicado` | Gestión de contenidos | Servicio de exploración | Actualizar el catálogo de áreas y niveles que usa el filtro de enriquecimiento |

Las consultas que el usuario hace y espera ver al instante —el alumno abre un módulo, el padre abre el dashboard— siguen siendo pedidos HTTP de cliente a servidor. Pub-sub se usa para **propagar hechos** entre componentes, no para cada consulta. La clase admite ambas formas de canal: conexiones directas sobre HTTP o un bus con PubSub. [CL08-P, p. 52]

### Por qué publish–subscribe

- **Un productor, muchos interesados que no se conocen.** En pub-sub, los productores publican eventos, los consumidores se suscriben y no se conocen entre sí. [CL08-P, p. 39] El servicio de exploración no debería saber que existen el dashboard, las notificaciones o las métricas.
- **Resuelve los dos ASR principales.** Pub-sub resuelve «desacoplamiento total + escalabilidad». [CL08-P, p. 39] El desacoplamiento cubre la modificabilidad posterior al piloto: un consumidor nuevo, como un reporte para orientadores, se suscribe sin tocar al productor. La escalabilidad cubre la expansión de los meses 10–12 (§5B).
- **Es el mismo patrón que el ejemplo IoT de la clase.** Allí los sensores publican datos en un tópico y distintas aplicaciones —monitoreo, control, dashboards— se suscriben. [CL08-P, p. 41] En YOLO, la actividad del alumno cumple el papel del sensor, y el dashboard de los padres, los reportes y las métricas son los suscriptores.

### Estilos descartados

- **Broker:** resuelve «desacoplar y enrutar»: el intermediario recibe una solicitud, busca un proveedor disponible y le reenvía la tarea, como en Uber o Rappi. [CL08-P, p. 36]; [CL08-P, p. 37] YOLO no tiene que emparejar pedidos con proveedores; su patrón dominante es un hecho con muchos interesados. **Conocimiento general:** en la implementación, pub-sub suele montarse sobre un *message broker* (un servicio de mensajería gestionado). La decisión de estilo sigue siendo pub-sub, porque la comunicación es de uno a muchos y anónima.
- **Client–dispatcher–server:** resuelve distribución y disponibilidad balanceando la carga entre servidores. [CL08-P, p. 45] Con el volumen del piloto no hace falta. Si la expansión lo requiere, el balanceador del hosting lo provee sin cambiar el diseño, en línea con YAGNI. [CL09-P, p. 3]
- **Forwarder–receiver:** resuelve la transparencia en la comunicación directa entre pares. [CL08-P, p. 43] En YOLO no hay pares que se hablen directamente, y el estilo acoplaría a cada emisor con su receptor, que es justo lo que pub-sub evita.

### Cómo implementarlo sin sobredimensionar

La clase concluye que el esfuerzo de arquitectura inicial depende del tamaño del proyecto: los proyectos chicos admiten más agilidad y menos arquitectura *upfront*. [CL09-P, p. 5] **Recomendación (inferencia):**

- **MVP y piloto (meses 1–6):** una sola aplicación organizada en módulos, con un bus de eventos interno que respete la semántica pub-sub: los mismos tópicos y los mismos contratos de evento. Es barato y lo mantiene un equipo chico.
- **Implementación y expansión (meses 7–12):** si la carga o el equipo crecen, el bus interno se reemplaza por un servicio pub-sub gestionado sin cambiar productores ni consumidores. Si un filtro del pipeline necesita escalar por separado, su pipe pasa a ser un tópico del mismo canal, como en el ejemplo de Kafka, donde los pipes son los topics. [CL08-P, p. 33]

Esto es *architectural runway*: anticipar lo necesario a corto y mediano plazo para no frenar el desarrollo, sin intentar adivinar todo el futuro. [CL09-P, p. 11] También respeta la restricción de costos del business case (§5A, §7B).

## Decisión 3 — Manejo de eventos: Event Stream Processing

### Por qué stream

Event Stream Processing procesa un flujo continuo de eventos aplicando transformaciones, agregaciones o filtros en línea. El ejemplo de la clase es Google Analytics en tiempo real, con los clicks en vivo. [CL08-P, p. 54] El registro del recorrido de YOLO es analítica de producto aplicada a la exploración, del mismo tipo:

- **Transformaciones y filtros en línea:** los filtros 1 a 3 del pipeline.
- **Agregaciones en línea:** el filtro 4 calcula el tiempo efectivo por sesión y el filtro 5 acumula el tiempo por área, las áreas exploradas y la profundidad máxima. Ninguna de estas métricas sale de un evento aislado: todas requieren mirar el flujo.
- **Coherencia con las otras dos decisiones:** pipes & filters es la forma natural de implementar stream processing, y pub-sub es el canal por el que circula el flujo. La clase usa Apache Kafka como ejemplo de ambos. [CL08-P, p. 33]; [CL08-P, p. 54]

### Tipos descartados o complementarios

- **Single Event Processing** procesa eventos de a uno, en forma aislada. [CL08-P, p. 54] Sirve para reacciones puntuales y YOLO lo usa en esos casos: `suscripcion.activada` habilita el acceso y `nivel.completado` desbloquea el nivel siguiente. Pero no alcanza como enfoque principal, porque el tiempo dedicado y la profundidad acumulada necesitan muchos eventos de una sesión.
- **Complex Event Processing** detecta patrones complejos a partir de varios eventos simples correlacionados en tiempo y espacio. [CL08-P, p. 54] Ataca directamente los riesgos del business case (§4A). Por ejemplo, «abandonó tres módulos seguidos en menos de un minuto» señala contenido poco atractivo, y «catorce días sin actividad» señala baja adopción, algo que conviene avisar al colegio. Sin embargo, los patrones se pueden definir recién cuando el piloto muestre datos reales. **Se posterga como evolución planificada** después del piloto (meses 4–6), sobre el mismo flujo de eventos (YAGNI y *architectural runway*). [CL09-P, p. 3]; [CL09-P, p. 11]
- **Online Event Processing** reacciona casi sin latencia, como en el trading en milisegundos. [CL08-P, p. 54] Nada en YOLO necesita reaccionar en milisegundos; elegirlo subiría el costo sin un beneficio.

## Trade-offs y mitigaciones

| Riesgo | Origen | Mitigación |
|---|---|---|
| Coordinar los filtros es más complejo | Pipes & filters [CL08-P, p. 27] | Contratos de evento definidos desde el principio; en el MVP, todos los filtros en un mismo proceso |
| Cuesta reproducir situaciones, encontrar la causa raíz o rastrear una operación de punta a punta | Sistemas basados en eventos [CL08-P, p. 56] | Un identificador de sesión en cada evento; guardar los eventos crudos para poder reprocesarlos si un filtro tenía un error |
| Eventos duplicados o perdidos | Canal asincrónico (conocimiento general) | Consumidores idempotentes; el filtro de validación descarta duplicados |
| El dashboard de los padres muestra datos con algo de demora | Comunicación asincrónica (conocimiento general) | Aceptable según el supuesto 3; mostrar «actualizado a las HH:MM» |
| Costo de infraestructura | Restricción del business case (§5A, §7B) | Bus interno en el MVP; servicio gestionado recién en la expansión |
| Datos de menores circulando entre componentes | Supuesto 6 (conocimiento general) | Los eventos llevan un identificador seudonimizado del alumno; los datos personales se resuelven solo en el dashboard, con control de acceso por tutor |

**Ventaja que compensa:** en un sistema basado en eventos, los subsistemas son altamente independientes y se desarrollan, escalan y ponen en producción por separado. [CL08-P, p. 56] Para un equipo que va a iterar sobre el producto después de cada revisión del business case (§7A), esa independencia vale más que la complejidad agregada.

## Vínculo con la Actividad 2

La Actividad 2 pide un árbol de utilidad, al menos dos vistas del modelo 4+1 e incorporar estos estilos. [CL09-P, p. 33] **Inferencia:** de esta resolución salen insumos directos:

- **Árbol de utilidad:** modificabilidad (agregar un consumidor sin tocar al productor), escalabilidad (del piloto a la expansión), rendimiento (latencia del recorrido para el alumno), confiabilidad (no perder eventos de exploración) y seguridad (acceso de cada tutor solo a los datos de su hijo).
- **Vista de procesos:** el pipeline de la decisión 1 y el canal pub-sub de la decisión 2.
- **Vista de desarrollo:** la organización en capas descartada como pipeline vuelve a aparecer acá.

La resolución está en [Actividad 2](../clase-09-actividad-2/README.md). Allí el bus interno del MVP se precisa como un bus apoyado en la base de datos, para no perder eventos ante una caída.

## Dudas abiertas

- **Si la actividad es evaluada.** Se guardó en `practica/` porque la consigna no indica entrega. Si la cátedra la evalúa, conviene moverla a `entregas/`.
- **Escala real del piloto.** Cantidad de colegios y de alumnos. Con volúmenes mucho mayores convendría el servicio pub-sub gestionado desde el MVP.
- **Qué ven colegios y profesionales.** Si ven datos individuales o solo agregados. Cambia los suscriptores, el control de acceso y el tratamiento de datos de menores.
- **Si los padres quieren alertas inmediatas.** En ese caso, las notificaciones pasarían a single event processing o a CEP antes de lo previsto.
- **Ubicación de la actividad.** La Actividad 2 se refiere a esta como «de la clase pasada». Ya está registrado en [dudas y conflictos](../../wiki/dudas-y-conflictos.md).
