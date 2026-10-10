# Consignas de práctica

Índice de consignas oficiales de práctica. Para cada una se indica qué pide y qué páginas de la wiki hacen falta. Las resoluciones van en `practica/` y se trabajan con `$resolver-practica`.

| Consigna | Fuente | Qué integra | Resolución |
|---|---|---|---|
| Clase 9 — Actividad 1: estilos para el producto del grupo | [CL09-P, p. 2] | [Estilos arquitectónicos](temas/estilos-arquitectonicos.md) | [practica/clase-09-actividad-1](../practica/clase-09-actividad-1/README.md) |
| Clase 9 — Actividad 2: definiciones de arquitectura | [CL09-P, p. 33] | Árbol de utilidad, 4+1 y estilos | [practica/clase-09-actividad-2](../practica/clase-09-actividad-2/README.md) |
| Caso HealthCare.gov: simular las fases 0 y 1 de ATAM | [CASO-HCG, p. 8]; [CASO-HCG, p. 9] | [Evaluación de arquitecturas](temas/evaluacion-de-arquitecturas.md#atam) y [Caso HealthCare.gov](temas/caso-healthcare-gov.md) | Pendiente |
| Cross Challenge, mayo de 2026: tres casos | [CROSS-2026-05, p. 1]; [CROSS-2026-05, p. 2] | Necesidad y funcionalidades, árbol de utilidad, hallazgos de ATAM, 4+1 y estilos | Pendiente |

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

**Temas involucrados (inferencia).** [Árbol de utilidad y hallazgos de ATAM](temas/evaluacion-de-arquitecturas.md#atam). Los *supuestos* no son una de las salidas de ATAM que lista la clase [CL09-P, p. 28]; la consigna los pide aparte.

### Caso 3: cotizador y emisor online de pólizas

**Situación.** Una compañía quiere cotizar y emitir pólizas de autos online, comparando presupuestos de varias aseguradoras según DNI, marca, modelo y año del vehículo, entre otros datos. Debe garantizar la mejor oferta considerando también condiciones como la franquicia. [CROSS-2026-05, p. 2]

- El mantenimiento anual de marcas y modelos debe ser sencillo.
- Se planea expandirse a pólizas de incendio y robo, y a comparar líneas de crédito, tarjetas y otros productos financieros.
- Se espera un crecimiento rápido en líneas de servicio y en países de la región.

**Consignas.** [CROSS-2026-05, p. 2]

- 3.a. Documentar dos vistas del modelo 4+1. Como mínimo, una vista lógica o de módulos que separe dominio, integración con proveedores, reglas de comparación y emisión, y una vista de procesos o escenarios con el flujo principal de cotización automotor.
- 3.b. Indicar al menos tres estilos arquitectónicos, dónde se aplican y qué problema resuelve cada uno, justificados en el caso.

**Temas involucrados (inferencia).** [Modelo 4+1](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md) y [estilos arquitectónicos](temas/estilos-arquitectonicos.md). La expansión a nuevos rubros y países apunta a la modificabilidad y la escalabilidad.

**Inferencia general:** los tres casos recorren la secuencia de la unidad de arquitectura: necesidad y funcionalidades, atributos de calidad y evaluación, y documentación con estilos. Sirven como práctica integradora.
