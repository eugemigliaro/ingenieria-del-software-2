# Wiki de la materia

Este es el índice del conocimiento canónico compilado para Ingeniería del Software II. Las páginas sintetizan el material oficial y mantienen citas al PDF y a la página exacta.

## Navegación

- [Glosario](glosario.md)
- [Dudas y conflictos](dudas-y-conflictos.md)
- [Preguntas de repaso](repaso/preguntas.md)
- [Banco de preguntas y respuestas del primer parcial](repaso/parcial-1-banco.md): 60 preguntas en cuatro ciclos de dificultad creciente, con respuestas desarrolladas y citadas.
- [Alcance del primer parcial](parcial-1-alcance.md): detalle de qué diapositivas y temas entran y cuáles quedaron fuera.
- [Alcance del segundo parcial](parcial-2-alcance.md): temario del repaso de la clase 12 por clase (7 a 11), qué diapositivas muestra, qué no aparece y el formato de ejercicio esperable.
- [Consignas de práctica](consignas-de-practica.md): actividades de la clase 9, caso HealthCare.gov, Cross Challenge, ejercicio de parcial rotulado 2013 y los cinco casos del TP general, con los temas que integra cada uno.

## Temas

- [Fundamentos, procesos y ciclos de vida](temas/fundamentos-procesos-y-ciclos-de-vida.md): definiciones de la disciplina, proceso de software, PDCA, modelos de ciclo de vida, ética e impacto social.
- [Metodologías clásicas y ágiles](temas/metodologias-clasicas-y-agiles.md): enfoques estructurados y orientados a objetos, RUP, PRINCE2, XP, Lean, TDD, Kanban y Scrum.
- [Desarrollo de productos digitales](temas/productos-digitales.md): Lean Startup, Design Thinking y Business Model Canvas como enfoques complementarios.
- [Estimación de proyectos de software](temas/estimacion-de-proyectos.md): tamaño, esfuerzo, complejidad y duración; PCU, PF, Planning Poker, Story Points, PERT, COCOMO y técnicas informales.
- [Calidad de software](temas/calidad-de-software.md): perspectivas de calidad, QA/QC, costo de no calidad, deuda técnica, pruebas, documentación y calidad con IA.
- [Arquitectura y atributos de calidad](temas/arquitectura-y-atributos-de-calidad.md): definición de arquitectura, Architecture Business Cycle, modelo de calidad ISO, atributos por categoría, ADD, restricciones, drivers y trade-offs.
- [Documentación de arquitectura y modelo 4+1](temas/documentacion-de-arquitectura-y-modelo-4-mas-1.md): views y viewpoints, Views and Beyond, IEEE 1471/42010, las cinco vistas de Kruchten, su correspondencia, adaptación, proceso guiado por escenarios y aplicación con RUP a la web.
- [Estilos arquitectónicos](temas/estilos-arquitectonicos.md): dataflow (batch, pipes & filters, capas), sistemas distribuidos (broker, publish–subscribe, forwarder–receiver, client–dispatcher–server), MVC y sistemas basados en eventos.
- [Evaluación de arquitecturas](temas/evaluacion-de-arquitecturas.md): cuándo definir la arquitectura (BDUF, YAGNI, sweet spot, Scrum y architectural runway de SAFe), ASR, técnicas de evaluación cualitativas y cuantitativas, métricas SLI/SLO/SLA, SAAM, ATAM con árbol de utilidad y Lightweight ATAM; ATAM en la práctica con los casos CAAS y Battlefield Control System, temas de riesgo y modelos de autoevaluación.
- [Caso HealthCare.gov](temas/caso-healthcare-gov.md): componentes, flujo y problemas del lanzamiento de 2013, causas técnicas y organizacionales según el informe oficial, recuperación, lecciones e insumos para simular ATAM.
- [Persistencia](temas/persistencia.md): archivos, prevalencia, bases relacionales (ACID y ORM), multidimensionales, de objetos, NoSQL por columnas, clave/valor y documentos, y vectoriales, con criterios de cuándo usar cada una.
- [Arquitecturas de integración](temas/arquitecturas-de-integracion.md): del punto a punto al integration hub, el ESB y las APIs; SOA y sus principios; microservicios, métricas de entrega, patrones (subdominio, API gateway, despliegue) y cuándo no usarlos; SOA frente a microservicios y arquitectura de integración ágil según Clark.

## Recorrido sugerido

1. Empezar por fundamentos para distinguir proceso, ciclo de vida y metodología.
2. Continuar con metodologías y luego con productos digitales.
3. Estudiar estimación y calidad como capacidades transversales de planificación, seguimiento y mejora.
4. Seguir con arquitectura: primero atributos de calidad —qué debe lograr el sistema—, después el modelo 4+1 —cómo se describe—, luego los estilos —cómo se diseña— y por último la evaluación —cómo se comprueba que cumple—. Practicar la evaluación con el [caso HealthCare.gov](temas/caso-healthcare-gov.md).
5. Estudiar [persistencia](temas/persistencia.md) y [arquitecturas de integración](temas/arquitecturas-de-integracion.md) como decisiones arquitectónicas con sus propios trade-offs: cómo guardar los datos y cómo conectar los sistemas.
6. Usar el [glosario](glosario.md) para recuperación rápida y las [preguntas](repaso/preguntas.md) para práctica activa.
7. Para preparar el primer parcial, recorrer el [banco de preguntas y respuestas](repaso/parcial-1-banco.md) ciclo por ciclo: el primero cubre los cinco temas con definiciones, y cada ciclo siguiente vuelve sobre los mismos temas con mayor profundidad.
8. Para preparar el segundo parcial, partir del [alcance del segundo parcial](parcial-2-alcance.md), repasar cada tema listado y practicar el formato de ejercicio con el ejercicio de 2013, el Cross Challenge y los casos del TP general, en las [consignas de práctica](consignas-de-practica.md).

## Cobertura del material

La wiki cubre las clases 1, 2, 4, 5, 6, 7, 8, 9, 11 y 12, el Parcial 1 del primer cuatrimestre de 2026 y la bibliografía entregada por la cátedra: el paper de Kruchten (`B01`) y el de Robal, Viies y Kruus (`B02`) sobre el modelo 4+1, el caso de estudio ATAM de Hariharan (`B03`), el informe oficial del OIG sobre HealthCare.gov (`B04`) y las tres lecturas complementarias de Kim J. Clark sobre integración y microservicios (`B05`, `B06` y `B07`). Hay dos presentaciones rotuladas como clase 11: persistencia (`CL11-P`) y arquitecturas de integración (`CL11-INT`). La clase 12 es el repaso de los temas del segundo parcial (`CL12-REP`), que numera persistencia como clase 10 e integración como clase 11. También incluye cuatro consignas de práctica: el caso HealthCare.gov (`CASO-HCG`), el Cross Challenge de mayo de 2026 (`CROSS-2026-05`), un ejercicio de parcial rotulado 2013 (`EJ-2013`) y un trabajo práctico general con cinco casos (`TP-GRAL`). No se recibió ningún archivo rotulado como clase 10. La selección vigente para estudiar el primer parcial está documentada aparte en [Alcance del primer parcial](parcial-1-alcance.md); algunas secciones de las páginas temáticas se conservan como conocimiento de la materia aunque estén fuera de ese recorte. La numeración fue normalizada por contenido: productos digitales corresponde a la clase 4, estimación a la clase 5 y calidad a la clase 6. Los nombres originales se conservan en `material/catalogo.tsv`; los desajustes y cuestiones abiertas están documentados en [Dudas y conflictos](dudas-y-conflictos.md).
