# Calidad de software

> **Primer parcial:** entran gestión, costos, deuda técnica, QA/QC, verificación/validación, pruebas, documentos y el concepto de Given–When–Then. Quedan fuera las cinco perspectivas, casos, herramientas y calidad con IA. Deuda técnica, sus cuadrantes, QC y QA están marcados como muy importantes. Ver [alcance detallado](../parcial-1-alcance.md#calidad). [N-2026-09-07-alcance-primer-parcial]

## Calidad como concepto multidimensional

La calidad no equivale solamente a ausencia de bugs: incluye objetivos funcionales y no funcionales, tiempo, costo y capacidad sostenible de mantenimiento y evolución. [CL06-A, p. 1] Puede observarse desde cinco perspectivas:

| Perspectiva | Pregunta central |
|---|---|
| Trascendental | ¿Se reconoce la excelencia aunque sea difícil definirla? |
| Usuario | ¿Satisface las metas y necesidades reales? |
| Fabricante/proceso | ¿Cumple especificaciones y estándares de producción? |
| Producto | ¿Qué atributos inherentes exhibe? |
| Valor | ¿La calidad obtenida justifica lo que el cliente paga? |

Las cinco visiones se presentan en [CL06-P, p. 3], [CL06-P, p. 4], [CL06-P, p. 5], [CL06-P, p. 6], [CL06-P, p. 7] y [CL06-P, p. 8]. Deben coexistir: satisfacer una especificación no garantiza utilidad, y satisfacer a un usuario no elimina restricciones de seguridad, mantenibilidad o costo.

## Gestión: planificación, QA y QC

La gestión de calidad integra planificación, aseguramiento y control dentro de un ciclo de mejora continua. [CL06-P, p. 15]

| Componente | Orientación | Objetivo | Ejemplos |
|---|---|---|---|
| Planificación | Estrategia | Definir objetivos, estándares, métricas, roles y actividades | Plan de calidad, presupuesto, criterios de aprobación |
| QA | Proceso y prevención | Evitar que aparezcan defectos | Políticas, estándares, auditorías, capacitación |
| QC | Producto y detección | Encontrar defectos existentes | Revisión de código, pruebas, verificación de requisitos |

QA actúa desde el inicio y compromete a toda la organización; QC inspecciona entregables durante y después del desarrollo. [CL06-P, p. 16]; [CL06-P, p. 17]; [CL06-P, p. 18]

**Verificación** comprueba que se construye correctamente según los requisitos; **validación** comprueba que lo construido satisface al cliente. [CL06-P, p. 19] Las revisiones son inspecciones generalmente informales de artefactos; las auditorías evalúan formalmente cumplimiento de estándares. [CL06-P, p. 20]

## Costo de calidad, no calidad y deuda técnica

El costo de calidad incluye prevención y evaluación. El costo de no calidad aparece como fallos internos antes de entregar y fallos externos en producción, donde se agregan soporte, compensaciones y daño reputacional. Invertir antes busca reducir fallos más costosos. [CL06-A, p. 2]

La deuda técnica es retrabajo futuro originado por decisiones rápidas, falta de conocimiento o degradación acumulada. El material la clasifica por intención —deliberada o inadvertida— y prudencia —prudente o imprudente—. [CL06-P, p. 10]; [CL06-P, p. 11]

No toda deuda deliberada es automáticamente irresponsable: puede ser una decisión temporal si el equipo conoce el costo, registra la deuda y dispone un plan realista de pago. Sin visibilidad, prioridad ni seguimiento, los “intereses” aparecen como cambios lentos, defectos y riesgo operativo. Las prácticas propuestas son registrarla en backlog, estimar esfuerzo y fecha, revisarla y pagarla incrementalmente. [CL06-P, p. 14]

## Pruebas como eje de QC

Las pruebas se clasifican desde varios ejes:

- **Nivel:** unitarias, integración, sistema, smoke y aceptación. [CL06-P, p. 21]
- **Ejecución:** estáticas —sin ejecutar código— o dinámicas.
- **Propósito:** funcionales o no funcionales; estas últimas cubren recuperación, seguridad, compatibilidad, rendimiento, usabilidad y escalabilidad. [CL06-P, p. 22]
- **Automatización:** manuales o automatizadas.
- **Conocimiento interno:** caja negra, blanca o híbrida. [CL06-P, p. 23]

La estrategia debe priorizar escenarios por impacto y probabilidad, usar partición de equivalencia y valores límite cuando corresponda, y combinar niveles: una prueba unitaria no sustituye una de aceptación ni una prueba funcional demuestra rendimiento. [CL06-P, p. 21]; [CL06-P, p. 22]; [CL06-P, p. 23]

## Documentación trazable

El plan de gestión de calidad define política, roles, estrategia, métricas, revisiones, actividades, presupuesto y aprobación. [CL06-P, p. 27] El plan de pruebas baja esa estrategia a alcance, ambientes, herramientas, cronograma, riesgos, incidentes e informes. [CL06-P, p. 28]

Un caso de prueba debe ser claro, atómico, trazable, observable, reproducible y mantenible; incluye precondiciones, datos, pasos y resultado esperado. [CL06-P, p. 29]; [CL06-P, p. 30] Given–When–Then expresa contexto, acción y resultado en lenguaje compartido por negocio, QA y desarrollo, y puede convertirse en criterio de aceptación ejecutable. [CL06-P, p. 31]; [CL06-P, p. 32]; [CL06-P, p. 34]

## Calidad en agilidad, DevOps e IA

Scrum y XP distribuyen calidad a lo largo de cada iteración mediante criterios de aceptación, revisiones, TDD, refactorización, integración continua y Definition of Done. DevOps profundiza el feedback automático mediante pipelines de pruebas, análisis y despliegue. [CL06-A, p. 3]

Cuando interviene IA, QA también debe revisar código y decisiones generadas, trazabilidad de prompts y degradación arquitectónica. [CL06-P, p. 35]; [CL06-P, p. 36]; [CL06-P, p. 38] Los sistemas con IA generativa añaden dimensiones de factualidad, toxicidad, estabilidad semántica, reproducibilidad parcial, alineación, robustez, grounding y drift; por su comportamiento probabilístico, el testing determinista tradicional no alcanza por sí solo. [CL06-P, p. 39]

## Cultura y métricas

La calidad requiere responsabilidad compartida, revisión entre pares, transparencia, documentación y apertura al feedback. PDCA, retrospectivas y gestión visual sostienen esa cultura. [CL06-A, p. 5]

Las métricas posibles incluyen densidad de defectos, tasa de errores, tiempo medio de corrección, cobertura, respuesta bajo carga, éxito de pruebas automatizadas e incidentes en producción. [CL06-A, p. 4] **Inferencia:** una métrica resulta útil cuando se vincula con una decisión o un objetivo de calidad, no como número aislado.

## Conexiones

- PDCA enlaza calidad con [mejora continua](fundamentos-procesos-y-ciclos-de-vida.md).
- XP, TDD, Scrum, Kanban y DoD integran calidad en las [metodologías](metodologias-clasicas-y-agiles.md).
- El costo de prevención, pruebas y deuda debe incluirse en la [estimación](estimacion-de-proyectos.md).
