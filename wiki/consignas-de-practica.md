# Consignas de práctica

Índice de consignas oficiales de práctica. Para cada una se indica qué pide y qué páginas de la wiki hacen falta. Las resoluciones van en `practica/` y se trabajan con `$resolver-practica`.

| Consigna | Fuente | Qué integra | Resolución |
|---|---|---|---|
| Clase 9 — Actividad 1: estilos para el producto del grupo | [CL09-P, p. 2] | [Estilos arquitectónicos](temas/estilos-arquitectonicos.md) | [practica/clase-09-actividad-1](../practica/clase-09-actividad-1/README.md) |
| Clase 9 — Actividad 2: definiciones de arquitectura | [CL09-P, p. 33] | Árbol de utilidad, 4+1 y estilos | [practica/clase-09-actividad-2](../practica/clase-09-actividad-2/README.md) |
| Caso HealthCare.gov: simular las fases 0 y 1 de ATAM | [CASO-HCG, p. 8]; [CASO-HCG, p. 9] | [Evaluación de arquitecturas](temas/evaluacion-de-arquitecturas.md#atam) y [Caso HealthCare.gov](temas/caso-healthcare-gov.md) | Pendiente |
| Cross Challenge, mayo de 2026: tres casos | [CROSS-2026-05, p. 1]; [CROSS-2026-05, p. 2] | Necesidad y funcionalidades, árbol de utilidad, hallazgos de ATAM, 4+1 y estilos | Pendiente |
| Ejercicio de parcial rotulado 2013: control de una fábrica | [EJ-2013, p. 1] | Necesidad y funcionalidades, árbol de utilidad, arquitectura candidata, resolución de atributos y hallazgos | Pendiente |
| Trabajo práctico general: cinco casos | [TP-GRAL, p. 1]; [TP-GRAL, p. 6] | Casos para definir una arquitectura; el documento no trae consignas | Pendiente |

**Inferencia:** el ejercicio de 2013 y el Cross Challenge recorren la misma secuencia, que es el formato esperable de un ejercicio del segundo parcial. Ver [Alcance del segundo parcial](parcial-2-alcance.md#formato-de-ejercicio-esperable).

## Cross Challenge, mayo de 2026

El documento plantea tres casos, cada uno con dos consignas. No indica si es evaluativo ni a qué instancia corresponde. Ver [Dudas y conflictos](dudas-y-conflictos.md).

### Caso 1: minitiendas para cuentas PYME

**Situación.** Un banco quiere que sus cuentas PYME armen minitiendas virtuales, sin programar, a partir de templates con personalización limitada de colores, fuentes y gráficos. Las tiendas cobran con los servicios de pago del banco y envían con servicios logísticos de terceros. [CROSS-2026-05, p. 1]

- Cada PYME tiene un administrador que mantiene productos y clientes registrados y obtiene reportes analíticos predefinidos.
- Los clientes deben registrarse y loguearse para pagar.
- El banco consulta las tiendas y transacciones sin acceder a los datos confidenciales de cada minitienda.
- El sistema debe estar disponible 24×7, con tiempos de respuesta aceptables en las compras. Debe soportar hasta 100.000 tiendas, con un promedio de 500 productos y unas 100 transacciones diarias por tienda, y fuertes picos estacionales.

**Consignas.** [CROSS-2026-05, p. 1]

- 1.a. Formular la necesidad del cliente en menos de 40 palabras.
- 1.b. Listar al menos seis funcionalidades de alto nivel.

**Temas involucrados (inferencia).** Ninguna fuente de la wiki define cómo formular la necesidad del cliente; lo más cercano es el foco en necesidades reales de Design Thinking y Canvas, en [Productos digitales](temas/productos-digitales.md). Los volúmenes y picos son insumos de escenarios de escalabilidad y disponibilidad: ver [Atributos de calidad](temas/arquitectura-y-atributos-de-calidad.md). Los reportes analíticos se relacionan con [Persistencia](temas/persistencia.md#bases-de-datos-multidimensionales).

### Caso 2: portal corporativo de viajes de negocio

**Situación.** Una compañía de turismo ofrece viajes de negocio con tarifas especiales y facturas A y B. Cada empresa se registra con su CUIT y personaliza su portal. [CROSS-2026-05, p. 1]; [CROSS-2026-05, p. 2]

- Los hoteles y vuelos llegan de varios canales agregadores, como Sabre o Booking.com. Podrían sumarse otros en el futuro.
- El sistema debe unificar, ordenar y priorizar la oferta sin que la complejidad de esos servicios perjudique la experiencia de búsqueda.
- Cada empresa define políticas de viaje: compañías predilectas, costo máximo por noche y categorías por nivel jerárquico.
- Hay que asegurar que se respeten esas políticas, que no entren personas ajenas y que los precios promocionales no se usen para viajes personales.

**Consignas.** [CROSS-2026-05, p. 2]

- 2.a. Construir un árbol de utilidad con los dos primeros niveles: atributos de calidad relevantes y, para cada uno, subatributos o escenarios generales.
- 2.b. Indicar riesgos, no riesgos, supuestos y trade-offs, distinguiéndolos claramente y vinculándolos con el caso.

**Temas involucrados (inferencia).** [Árbol de utilidad y hallazgos de ATAM](temas/evaluacion-de-arquitecturas.md#atam). Los *supuestos* no son una de las salidas de ATAM que lista la clase [CL09-P, p. 28]; la consigna los pide aparte. Unificar varios agregadores, con otros por sumarse, es un problema de [arquitecturas de integración](temas/arquitecturas-de-integracion.md): conviene aislar cada proveedor detrás de un adaptador o de un hub, en lugar de integrarlo punto a punto. [CROSS-2026-05, p. 1]; [CL11-INT, p. 3]

### Caso 3: cotizador y emisor online de pólizas

**Situación.** Una compañía quiere cotizar y emitir pólizas de autos online, comparando presupuestos de varias aseguradoras según DNI, marca, modelo y año del vehículo, entre otros datos. Debe garantizar la mejor oferta considerando también condiciones como la franquicia. [CROSS-2026-05, p. 2]

- El mantenimiento anual de marcas y modelos debe ser sencillo.
- Se planea expandirse a pólizas de incendio y robo, y a comparar líneas de crédito, tarjetas y otros productos financieros.
- Se espera un crecimiento rápido en líneas de servicio y en países de la región.

**Consignas.** [CROSS-2026-05, p. 2]

- 3.a. Documentar dos vistas del modelo 4+1. Como mínimo, una vista lógica o de módulos que separe dominio, integración con proveedores, reglas de comparación y emisión, y una vista de procesos o escenarios con el flujo principal de cotización automotor.
- 3.b. Indicar al menos tres estilos arquitectónicos, dónde se aplican y qué problema resuelve cada uno, justificados en el caso.

**Temas involucrados (inferencia).** [Modelo 4+1](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md) y [estilos arquitectónicos](temas/estilos-arquitectonicos.md). La expansión a nuevos rubros y países apunta a la modificabilidad y la escalabilidad. La «integración con proveedores» que pide la vista lógica se relaciona con las [arquitecturas de integración](temas/arquitecturas-de-integracion.md). [CROSS-2026-05, p. 2]

**Inferencia general:** los tres casos recorren la secuencia de la unidad de arquitectura: necesidad y funcionalidades, atributos de calidad y evaluación, y documentación con estilos. Sirven como práctica integradora.

## Ejercicio de parcial rotulado 2013: control de una fábrica

El documento es un único ejercicio numerado 1 y valuado en 6 puntos, sin encabezado de institución ni fecha. El año 2013 figura solo en el nombre del archivo recibido. [EJ-2013, p. 1]

**Situación.** Un sistema de control para una fábrica toma datos de sensores distribuidos por la planta. [EJ-2013, p. 1]

- La comunicación es por una interfaz serie de velocidad bastante limitada y por *polling*: el sistema pide el valor y el sensor responde con lo que mide en ese momento. Solo se puede hablar con un sensor por vez.
- Las métricas que importan no siempre son las sensadas: hay que integrarlas en el tiempo o combinarlas. Por ejemplo, volumen a partir de un caudalímetro, o consumo eléctrico a partir de voltímetros y amperímetros. Estos cómputos no siempre son sencillos.
- Como es un sistema de control, la frecuencia de sensado debe ser lo más alta posible para disparar alertas cuando un parámetro sale del rango aceptable.
- Se guardan datos para reportes de tendencia, que no necesitan tiempo real sino datos agregados: alcanza con un punto por hora y por métrica. No todos los reportes son accesibles a todos los usuarios, así que hace falta un ACL.
- El sistema debe funcionar varios años. Los sensores se romperán y los reemplazos serán probablemente de otras marcas, modelos y prestaciones.

**Consignas.** [EJ-2013, p. 1]

- Analizar: a. la necesidad del cliente en menos de 40 palabras; b. al menos cinco funcionalidades de alto nivel; c. los atributos de calidad prioritarios en un árbol de utilidad, con sus dos primeros niveles.
- Definir: d. una arquitectura candidata justificada, con texto o gráficos; e. cómo resuelve los atributos del punto c; f. riesgos, no riesgos, supuestos y trade-offs.

**Temas involucrados (inferencia).**

- La adquisición secuencial por una interfaz lenta compite con la frecuencia de sensado: la performance es un atributo prioritario y el cuello de botella está en el acceso a los sensores, no en el cómputo. Ver [atributos de calidad](temas/arquitectura-y-atributos-de-calidad.md#atributos-de-calidad).
- El cálculo de métricas derivadas encaja con [pipes & filters](temas/estilos-arquitectonicos.md#dataflow), y las alertas con [eventos](temas/estilos-arquitectonicos.md#sistemas-basados-en-eventos). El repaso del parcial usa justamente una alarma de temperatura como ejemplo de *single event processing*. [CL08-P, p. 27]; [CL12-REP, p. 7]
- Los reportes de tendencia con un punto por hora describen datos agregados y precalculados: ver [bases multidimensionales](temas/persistencia.md#bases-de-datos-multidimensionales) y [batch secuencial](temas/estilos-arquitectonicos.md#dataflow). [CL11-P, p. 11]; [CL08-P, p. 26]
- El reemplazo de sensores durante años apunta a la modificabilidad: conviene aislar cada modelo detrás de una interfaz común, como hacen los adaptadores del [integration hub](temas/arquitecturas-de-integracion.md#integration-hub). [CL11-INT, p. 3]
- El ACL corresponde a la seguridad (autorización).

## Trabajo práctico general: cinco casos

El documento se titula «Ingeniería de software II – Trabajo Práctico» y describe cinco sistemas, pero no dice qué hay que entregar sobre cada uno. [TP-GRAL, p. 1] Sus metadatos lo fechan en 2012. **Inferencia:** por su forma, son enunciados para definir y justificar una arquitectura, como en los ejercicios anteriores. Algunas referencias tecnológicas están datadas —web 2.0, PDA, solo Android—, pero los drivers siguen sirviendo para practicar.

### Caso 1: administración de cuentas para una empresa de logística

**Situación.** Herramienta de apoyo a la toma de decisiones para distintos niveles ejecutivos, con estadísticas y reportes y resguardo de los datos. [TP-GRAL, p. 1]

- Administración general de los datos tipificados que usan los reportes.
- Importación mensual y automática de 15 archivos de sistemas y formatos distintos, con logs de auditoría de los errores. Ante una falla, la importación debe retomarse desde el punto de detención.
- La función principal es integrar esos datos y generar informes mensuales.
- Módulo de seguridad con usuarios y grupos: cada usuario ve datos según su nivel jerárquico, y solo los reportes de los ejecutivos de cuenta a su cargo.

**Temas involucrados (inferencia).** Importación periódica de lotes: [batch secuencial](temas/estilos-arquitectonicos.md#dataflow). Retomar desde el punto de falla: tolerancia a fallos. Logs: auditabilidad. Reportes sobre datos integrados: [bases multidimensionales](temas/persistencia.md#bases-de-datos-multidimensionales).

### Caso 2: cartilla online de una empresa de salud

**Situación.** La cartilla actual es estática y tiene pocas opciones de búsqueda. La nueva debe acercar a la empresa con sus asociados. [TP-GRAL, p. 2]

- Acceso web multibrowser y desde dispositivos Android. La cartilla es de libre acceso, pero votar prestadores, guardar favoritos y usar el calendario de citas requiere autenticación.
- Búsqueda por zona, plan o tipo de prestación. La geolocalización de prestadores cercanos solo está en el móvil, y el mapa, solo en la web.
- La información de prestadores debe actualizarse constantemente desde el sistema de prestadores. El sistema accede también al sistema de contratos, que administra las prestaciones por plan y tipo.
- Se irá convirtiendo en un centro de comunicación con los asociados, con funcionalidad creciente.

**Temas involucrados (inferencia).** Dos sistemas existentes que integrar: [arquitecturas de integración](temas/arquitecturas-de-integracion.md). Dos clientes con funciones distintas: [API gateway y BFF](temas/arquitecturas-de-integracion.md#api-gateway). Crecimiento de funcionalidad: modificabilidad.

### Caso 3: red de compensación bancaria

**Situación.** Un grupo bancario crea una empresa para explotar un sistema compensador de redes bancarias. [TP-GRAL, p. 3]

- Cada banco aporta un monto antes de las 10, porque el sistema opera en horario bancario, de 10 a 15.
- Una transferencia del banco A al B se aprueba si A tiene garantías suficientes; si no, se rechaza y se notifica a A. La operación es sincrónica online, debe tardar siempre menos de 5 segundos y también hay una interfaz asincrónica. Se admiten saldos negativos hasta un porcentaje del aporte.
- Al final del día se compensa la red: se acreditan los saldos positivos o se pide un depósito para dejar los saldos en cero. El proceso empieza entre las 18 y las 19.
- Solo operan bancos de la red; la autenticación del remitente y la confidencialidad se logran con criptografía asimétrica.
- Los bancos gestionan sus datos, monitorean su aporte y hacen depósitos desde una interfaz web.
- Debe poder implantarse en varios países de la región y adaptarse a sus culturas, leyes y reglamentaciones.

**Temas involucrados (inferencia).** Límite de 5 s: performance. Consistencia de saldos: [transacciones ACID](temas/persistencia.md#acid). Compensación diaria: [batch secuencial](temas/estilos-arquitectonicos.md#dataflow). Interfaz asincrónica: [publish–subscribe o mensajería](temas/estilos-arquitectonicos.md#sistemas-distribuidos). Despliegue por país: portabilidad y modificabilidad. El horario de cierre del enunciado es contradictorio: ver [Dudas y conflictos](dudas-y-conflictos.md).

### Caso 4: sistema tintométrico

**Situación.** Una fábrica de pinturas administra las fórmulas de color de sus productos para hogar y obra, industria y automotor. Cada línea tiene un laboratorio que registra sus fórmulas. Los productos base y sus precios se importan al sistema. [TP-GRAL, p. 4]

- Las pinturerías ingresan producto y color, y obtienen la fórmula con las cantidades según el producto de aplicación y los litros.
- El sistema calcula el precio con el costo del producto base y de los colorantes; cada pinturería aplica su porcentaje de ganancia.
- Cada pinturería puede crear sus propias fórmulas sin afectar las de fábrica y sin que otras pinturerías las vean.
- Permisos de acceso por rol.

**Temas involucrados (inferencia).** Aislamiento de las fórmulas propias: seguridad (confidencialidad). Importación de productos y precios: integración. Muchas pinturerías consultando: escalabilidad y disponibilidad.

### Caso 5: gestor de documentos distribuido

**Situación.** Un grupo de personas trabaja en forma colaborativa sobre una red P2P, elegida por su tolerancia a fallos. Cada estación es a la vez consumidora y proveedora de documentos. [TP-GRAL, p. 5]

- Se pueden listar y buscar documentos según permisos, sin conocer su ubicación física, y por creador, fechas, grupo y a veces contenido.
- Se puede editar sin conexión y sincronizar después. Los administradores, y quienes tengan ese permiso, pueden deshacer cambios.
- Permisos por grupos de documentos y roles, con un rol de administración general.
- Las estaciones pueden ser PC o dispositivos móviles con conectividad intermitente; el trabajo no debe verse afectado por cortes ni por estaciones fuera de servicio.
- Una modificación publicada debe quedar disponible para todos dentro de cierto período umbral.
- El historial de operaciones, con fecha y usuario, siempre debe estar accesible.
- Hay que detectar adulteraciones de alguien no registrado y evitar que se propaguen.
- Debe rendir razonablemente en redes privadas y abiertas, y servir en el futuro como plataforma de almacenamiento para otras aplicaciones. [TP-GRAL, p. 6]

**Temas involucrados (inferencia).** Búsqueda sin conocer la ubicación: transparencia de ubicación, como en [client–dispatcher–server](temas/estilos-arquitectonicos.md#sistemas-distribuidos) y [broker](temas/estilos-arquitectonicos.md#sistemas-distribuidos). Trabajo desconectado frente a «todos ven los mismos datos»: trade-off entre disponibilidad y consistencia. Historial: auditabilidad. Adulteración: seguridad (integridad). Plataforma para otras aplicaciones: interoperabilidad. El documento termina con un enlace a un producto comercial de referencia, que no se consultó. [TP-GRAL, p. 6]
