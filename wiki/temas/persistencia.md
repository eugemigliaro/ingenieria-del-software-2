# Persistencia

> **Alcance:** esta clase es posterior al recorte del primer parcial y no aparece en él. Ver [alcance del primer parcial](../parcial-1-alcance.md). Fuente principal: presentación de la clase 11, `CL11-P`. Varias diapositivas son solo imagen, así que se revisaron renderizadas.

## Qué es y por qué hace falta

La **persistencia** es la característica de los datos que sobreviven al programa que los genera. Hace falta porque la memoria es **volátil** y **acotada**. [CL11-P, p. 2]

Al elegir un mecanismo de persistencia hay que considerar tres factores: [CL11-P, p. 3]

- **Performance:** acceso al medio (memoria o disco) y búsquedas.
- **Transformación de datos:** cuánto hay que convertir los datos entre la forma en que los usa el programa y la forma en que se guardan.
- **Tolerancia a fallos.**

**Inferencia:** los tres factores son [atributos de calidad](arquitectura-y-atributos-de-calidad.md). Por eso la elección del mecanismo de persistencia es una decisión arquitectónica: fija trade-offs entre performance, interoperabilidad, consistencia y escalabilidad.

## Tipos de persistencia

La presentación anuncia tres grandes familias: archivos, prevalencia (como patrón de diseño) y bases de datos, relacionales y de objetos. [CL11-P, p. 4] Después desarrolla también las bases multidimensionales, las NoSQL y las vectoriales, y cierra con un resumen de nueve opciones. [CL11-P, p. 23]; [CL11-P, p. 24]; [CL11-P, p. 25]

### Archivos

La clase distingue tres tipos: [CL11-P, p. 5]

| Tipo | Variantes | Uso señalado |
|---|---|---|
| Planos | **Ancho fijo:** cada registro —fila lógica— ocupa una cantidad fija de caracteres, y cada campo dentro del registro tiene un tamaño predefinido. **Ancho variable:** por ejemplo, CSV. | Logs |
| Estructurados | XML, y también JSON | Intercambio de datos |
| Binarios | Archivos indexados y serialización | Rendimiento (indexados) y comunicación (serialización) |

Los **archivos binarios** no son directamente legibles por humanos: están pensados para que los lea un programa. Ejemplos: `.jpg`, `.mp3`, `.mp4`, `.dat` y `.sqlite`. [CL11-P, p. 6]

- **Archivos indexados:** permiten acceder rápido a ciertos registros mediante una clave o índice. La ventaja es la búsqueda rápida. La desventaja es que el índice debe mantenerse actualizado cuando cambian los registros. [CL11-P, p. 6]
- **Serialización:** convierte una estructura de datos, como un objeto, en una secuencia de bytes o texto para guardarla en un archivo o enviarla por red. Ejemplo: el formato Pickle de Python. [CL11-P, p. 6]

**Cuándo usarlos:** para intercambio simple de datos, backups o persistencia mínima en aplicaciones de escritorio o scripts. Por ejemplo, logs de auditoría, configuración o resultados de procesos batch. **Cuándo no:** si hay concurrencia o se necesitan integridad referencial o consultas complejas, porque los archivos no tienen atomicidad ni consistencia transaccional. [CL11-P, p. 23]

### Prevalencia

En la **prevalencia**, los datos se mantienen en memoria en su formato nativo. Las transacciones se registran y periódicamente se toman *snapshots* a disco. [CL11-P, p. 7] El diagrama de la diapositiva muestra este mecanismo: [CL11-P, p. 7]

1. El **dominio** vive en RAM, con colecciones, índices y grafos en memoria.
2. Cada mutación es un **comando** que se agrega a un *command log*, un archivo *append-only* en el sistema de archivos.
3. Un **snapshotter** hace un *dump* periódico del estado completo.

**Inferencia:** después de una caída, el sistema se recupera cargando el último snapshot y reaplicando los comandos registrados después de él. Así se cubre el factor de tolerancia a fallos sin abandonar la memoria como medio principal.

Implementaciones: Prevayler (Java), Madeleine (Ruby) y Bamboo (.NET). [CL11-P, p. 7]

**¿Redis es prevalencia?** «Más o menos». La prevalencia pura persiste el estado de **objetos**, mientras Redis persiste **estructuras de datos clave-valor**. Aun así, Redis implementa el mismo principio arquitectónico. [CL11-P, p. 7]

| Ventajas | Desventajas |
|---|---|
| No hay transformación: los datos se guardan en el formato en que los usa el programa | Toda la aplicación debe caber en memoria |
| Alto grado de transparencia | Interoperabilidad: los snapshots suelen ser serializaciones binarias del estado interno de los objetos, por ejemplo con `ObjectOutputStream` en Java o `pickle` en Python |
| Performance muchísimo más alta | |

La tabla sintetiza [CL11-P, p. 8].

**Cuándo usarla:** en sistemas financieros o de simulación con datos complejos que deben responder rápido, con baja latencia y pocos usuarios. **Cuándo no:** si el conjunto de datos excede la memoria, si hay muchos usuarios concurrentes o si se necesitan consultas ad hoc, porque la prevalencia no está optimizada para búsquedas. [CL11-P, p. 23]

### Bases de datos: ventajas generales

Frente a los mecanismos anteriores, una base de datos ofrece seis ventajas: [CL11-P, p. 9]

- independencia respecto de cómo se guardan físicamente los datos;
- posibilidad de compartir la base entre varios programas;
- mecanismos para recuperarse si algo falla;
- reglas de integridad;
- performance y escalabilidad;
- posibilidad de ejecutar lógica dentro de la base.

### Bases de datos relacionales

Organizan los datos en **tablas**, es decir, relaciones de filas y columnas. Se basan en el álgebra relacional y la teoría de conjuntos, tienen tablas, constraints y claves, y **se deben normalizar**. [CL11-P, p. 10]

**Cuándo usarlas:** en sistemas transaccionales, ERP, CRM y sistemas bancarios. Ejemplos: PostgreSQL, MySQL y SQL Server. **Cuándo no:** con datos no estructurados, grandes volúmenes distribuidos o alta variabilidad de esquema. [CL11-P, p. 23]

#### ACID

La clase define las cuatro propiedades transaccionales con un ejemplo cada una: [CL11-P, p. 14]

| Propiedad | Definición | Ejemplo |
|---|---|---|
| **Atomicidad** | Una transacción es una unidad de trabajo indivisible | Al transferir $100 de A a B, hay que completar las dos operaciones: restar de A y sumar a B |
| **Consistencia** | Una transacción lleva la base de un estado válido a otro estado válido | Si una regla dice que el saldo no puede ser negativo, ninguna transacción puede violarla |
| **Aislamiento** | Las transacciones concurrentes se ejecutan aisladas, como si fueran secuenciales | Si dos personas compran a la vez el último producto disponible, solo una transacción debe tener éxito |
| **Durabilidad** | Una vez confirmada (*commit*), la transacción es permanente aunque haya fallos | Un pago confirmado persiste aunque el servidor se reinicie inmediatamente después |

#### Mapeo objeto-relacional (ORM)

Los **ORM** son frameworks que mapean objetos, que existen en el software, a tablas relacionales, que existen en la base. Automatizan las operaciones más comunes (CRUD) y facilitan la programación a costa de performance y complejidad. [CL11-P, p. 13]

**Inferencia:** el ORM resuelve la distancia entre el paradigma de objetos y el relacional, el mismo problema que eliminan la prevalencia y las bases de objetos al guardar los datos en el formato del programa.

### Bases de datos multidimensionales

En estas bases: [CL11-P, p. 11]

- se almacenan grandes volúmenes **históricos**;
- los datos se guardan **desnormalizados**, para no hacer joins;
- se **precalculan** posibles agregaciones;
- se usan **solo para reportes**.

El caso típico es el **data warehouse (DWH)**. Los datos se extraen de sistemas transaccionales, se transforman y agregan, y se almacenan en estructuras multidimensionales optimizadas para lectura. [CL11-P, p. 11] El diagrama muestra un modelo con una tabla de hechos, `Hechos_Ventas` (ids de tiempo, provincia y producto, más cantidad e importe), y tres dimensiones: `Dim_Tiempo`, `Dim_Provincia` y `Dim_Producto`. [CL11-P, p. 11] **Conocimiento general:** esta forma, con una tabla de hechos en el centro y dimensiones alrededor, se llama esquema estrella.

**Cuándo usarlas:** en BI, dashboards, análisis histórico y reportes agregados (OLAP). Ejemplos: Microsoft Analysis Services y Apache Kylin. **Cuándo no:** para transacciones online (OLTP), actualizaciones frecuentes o escritura intensiva. [CL11-P, p. 24]

### Bases de datos de objetos (OODB)

Guardan objetos complejos, no simples tablas. Tienen las relaciones del paradigma de objetos, como la herencia, y soportan relaciones de muchos a muchos. [CL11-P, p. 12] En OO hay herencia, encapsulamiento y referencias; en SQL, tablas, claves y joins. Con una base de objetos no hace falta mapear ni usar un ORM como Hibernate o SQLAlchemy. [CL11-P, p. 12]

Ejemplos: ZODB (Python), Objectivity/DB (C++, Java, Python) y db4o (Java y .NET) [CL11-P, p. 12]; el resumen agrega ObjectDB y Versant. [CL11-P, p. 24]

**Cuándo usarlas:** en aplicaciones con jerarquías y grafos complejos. **Cuándo no:** si hay que integrarse con sistemas externos o hacer consultas SQL. Además tienen baja adopción y soporte limitado. [CL11-P, p. 24]

### Bases de datos NoSQL

Surgen en parte para suplir limitaciones del modelo relacional: [CL11-P, p. 14]

- escalabilidad;
- distribución «por diseño»;
- volumen de datos;
- esquemas flexibles.

**Pueden implementar ACID o no.** [CL11-P, p. 14] La clase presenta tres tipos: columnas, clave/valor y documentos. [CL11-P, p. 14]

#### Columnas

Los datos se guardan ordenados **por columna** en lugar de por registro. Esto tiene tres consecuencias: [CL11-P, p. 15]

- las búsquedas son mucho más rápidas;
- es más fácil calcular proyecciones relativas a una o pocas columnas;
- es más difícil hacer escrituras o consultas de muchas columnas.

Se usan principalmente para analizar grandes volúmenes de datos: Big Data, BI, IoT, métricas y logs. Ejemplos: BigTable (Google), Hypertable y Apache Cassandra. [CL11-P, p. 15]

La comparación gráfica muestra la misma tabla con `id`, `Name`, `Age` e `Interests`. En el modelo por filas (RDBMS), un campo puede quedar `null` o contener varios valores. En el modelo por columnas (*multi-value sorted map*), cada columna se guarda aparte con su `id`: un valor ausente no ocupa lugar y un multivalor se reparte en varias entradas. [CL11-P, p. 16]

**Cuándo usarlas:** con grandes volúmenes distribuidos, telemetría y analítica en tiempo real. **Cuándo no:** si se requieren transacciones fuertes o estructuras relacionales complejas. [CL11-P, p. 24]

#### Clave/valor

La información se guarda como pares clave/valor. [CL11-P, p. 17]

- Tiene alta flexibilidad: no hace falta modificar estructuras para agregar atributos.
- No es necesario lidiar con tipos de datos.
- Es complicado buscar por más de un campo (AND y OR).

Ejemplos: Redis y Dynamo. [CL11-P, p. 17] El diagrama de Redis muestra que una clave puede apuntar a un *hash* de campos, un *sorted set* ordenado por puntaje, un *set*, una *list* ordenada por inserción o un *string*. [CL11-P, p. 18]

**Cuándo usarlas:** para caché, sesiones de usuario y colas de mensajes. **Cuándo no:** si hay que buscar por atributos o relaciones, porque solo se accede por clave. [CL11-P, p. 25]

#### Documentos

Guardan cualquier «documento» arbitrario: [CL11-P, p. 19]

- es más fácil guardar estructuras que varían;
- suelen usar XML, YAML o JSON para devolver los datos por REST;
- no es tan fácil hacer consultas complejas, como las **proyecciones**, es decir, elegir qué columnas de una tabla obtener.

Ejemplos: MongoDB y CouchDB. [CL11-P, p. 19] El ejemplo gráfico relaciona un `user document` con un `contact document` y un `access document` mediante un campo `user_id` que referencia el `_id` del usuario. [CL11-P, p. 20]

**Cuándo usarlas:** para catálogos de productos, APIs y apps móviles; el resumen suma Firestore a los ejemplos. **Cuándo no:** si se requiere consistencia transaccional fuerte o hay relaciones complejas. [CL11-P, p. 25]

### Bases de datos vectoriales

Almacenan y gestionan vectores multidimensionales: los **embeddings**, representaciones numéricas de texto, imágenes, audio u otros datos generadas por modelos de IA. Su objetivo principal es buscar **similitud semántica** entre elementos, no coincidencias exactas. Ejemplos: Pinecone, Qdrant y Chroma. [CL11-P, p. 21]

No reemplazan a las relacionales: se integran con ellas para ofrecer búsquedas semánticas, y son fundamentales en los sistemas modernos de IA generativa. [CL11-P, p. 21] Funcionan en cuatro pasos: [CL11-P, p. 21]

1. **Codificación:** un modelo, como BERT u OpenAI Embeddings, transforma el dato en un vector.
2. **Almacenamiento:** los vectores se guardan junto con metadatos.
3. **Consulta:** el sistema calcula la distancia (coseno, euclidiana, etc.) entre el vector de consulta y los almacenados.
4. **Resultado:** devuelve los elementos semánticamente más parecidos.

Como analogía, la base es un mapa 3D de palabras: guarda la posición de cada palabra, busca las más cercanas a la consultada y devuelve las más parecidas. [CL11-P, p. 22] Una tabla histórica en la misma diapositiva traza cuatro etapas: [CL11-P, p. 22]

- fundamentos teóricos de búsqueda por similitud (1970–2000);
- embeddings y deep learning, con Word2Vec, FAISS y Annoy (2013–2017);
- bases vectoriales dedicadas, como Milvus, Weaviate, Pinecone y Qdrant (2019–2021);
- expansión masiva con la integración a LLM y RAG (desde 2022).

**Cuándo usarlas:** para búsqueda semántica, recomendadores, RAG (*Retrieval-Augmented Generation*) e IA generativa. Ejemplos del resumen: Pinecone y FAISS. **Cuándo no:** con datos estructurados, operaciones transaccionales o reportes agregados. [CL11-P, p. 25]

## Resumen comparativo

| Mecanismo | Casos típicos | No recomendado cuando… |
|---|---|---|
| Prevalencia | Sistemas financieros o de simulación de baja latencia y pocos usuarios | Los datos no caben en memoria, hay mucha concurrencia o se necesitan consultas ad hoc |
| Archivos | Intercambio simple, backups, configuración, logs, resultados batch | Hay concurrencia, integridad referencial o consultas complejas |
| Relacional | Sistemas transaccionales, ERP, CRM, bancos | Hay datos no estructurados, grandes volúmenes distribuidos o esquemas muy variables |
| Multidimensional | BI, dashboards, análisis histórico (OLAP) | Hay OLTP, actualizaciones frecuentes o escritura intensiva |
| Objetos (OODB) | Jerarquías y grafos complejos | Hay que integrarse con sistemas externos o usar SQL |
| NoSQL columnar | Grandes volúmenes distribuidos, telemetría, analítica en tiempo real | Se requieren transacciones fuertes o relaciones complejas |
| NoSQL clave/valor | Caché, sesiones, colas de mensajes | Hay que buscar por atributos o relaciones |
| NoSQL documental | Catálogos, APIs, apps móviles | Se requiere consistencia fuerte o hay relaciones complejas |
| Vectorial | Búsqueda semántica, recomendadores, RAG | Hay datos estructurados, transacciones o reportes agregados |

La tabla resume [CL11-P, p. 23]; [CL11-P, p. 24]; [CL11-P, p. 25].

## Un caso real: NoSQL en HealthCare.gov

El informe oficial del caso HealthCare.gov muestra que elegir un mecanismo de persistencia también depende del equipo. [B04, p. 24]; [B04, p. 25]

- La propuesta de CGI Federal combinaba una base relacional tradicional, como Oracle, con una plataforma NoSQL orientada a documentos. La relacional tenía la ventaja de su amplia adopción. La NoSQL podía transferir más datos por vez y crecer con facilidad en datos o usuarios, pero pocos desarrolladores tenían experiencia en ella. [B04, p. 24]
- En enero de 2012, CMS impuso por una carta de dirección técnica la plataforma de MarkLogic, pese a las advertencias del contratista sobre su falta de experiencia. Ese contratista nunca retuvo suficientes expertos, y la plataforma causó problemas durante el resto del desarrollo del FFM. QSSI, en cambio, contrató personal de MarkLogic suficiente para el Hub y no reportó los mismos problemas. [B04, p. 25]
- Después del lanzamiento se encontró que el sistema consultaba la base del FFM más de 100 veces en operaciones que requerían 1 o 2 accesos. Además, un «modelo de datos inflado» devolvía registros diez veces más grandes de lo ideal. [B04, p. 31]

**Inferencia:** el caso muestra que la elección de persistencia es un trade-off entre la escalabilidad técnica y la mantenibilidad o el riesgo del proyecto, que dependen de la experiencia disponible. Ver [Caso HealthCare.gov](caso-healthcare-gov.md).

## Conexiones

- Los factores de selección —performance, transformación y tolerancia a fallos— son [atributos de calidad](arquitectura-y-atributos-de-calidad.md), y la elección produce trade-offs que se pueden analizar en una [evaluación con ATAM](evaluacion-de-arquitecturas.md#atam). **Inferencia.**
- En el [modelo 4+1](documentacion-de-arquitectura-y-modelo-4-mas-1.md), Kruchten analiza la persistencia de las clases —si los objetos son transitorios o permanentes y si sobreviven a la falla de un proceso— al pasar de la vista lógica a la de procesos. [B01, p. 11]
- El command log de la prevalencia es un archivo *append-only* de eventos, una idea cercana a los [sistemas basados en eventos](estilos-arquitectonicos.md). Los DWH se alimentan con procesos de extracción y transformación análogos al estilo batch secuencial. **Inferencia.**
- Las bases multidimensionales y columnares sostienen métricas y dashboards como los SLI de la [evaluación de arquitecturas](evaluacion-de-arquitecturas.md). **Inferencia.**
