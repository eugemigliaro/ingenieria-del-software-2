# Metodologías clásicas y ágiles

> **Primer parcial:** entran criterios de selección, enfoque estructurado/SSADM, orientación a objetos, RUP, PRINCE2, XP, Lean, TDD, Kanban y Scrum. Quedan fuera la introducción general a agilidad, Manifiesto Ágil, variantes, críticas e IA. Ver [alcance detallado](../parcial-1-alcance.md#metodologías). [N-2026-09-07-alcance-primer-parcial]

## Elegir según el contexto

La gestión de proyectos busca controlar alcance, tiempo, costo y calidad para satisfacer necesidades de cliente y negocio. La selección metodológica depende, entre otros factores, del tamaño y complejidad, la experiencia del equipo y la claridad o estabilidad de los requisitos. [CL02-P, p. 2]; [CL02-P, p. 3]

## Enfoques clásicos y orientados a objetos

El enfoque estructurado divide el desarrollo en fases definidas y facilita planificación y control, pero ofrece poca flexibilidad cuando los requisitos cambian. [CL02-P, p. 5] Yourdon/Constantine emplea DFD para análisis y diagramas de estructura para diseño; SSADM amplía análisis y diseño con viabilidad, especificación lógica y diseño físico. [CL02-P, p. 6]; [CL02-P, p. 7]; [CL02-A, p. 2]; [CL02-A, p. 3]

El desarrollo orientado a objetos modela el dominio como objetos que encapsulan estado y comportamiento. Sus principios de abstracción, encapsulamiento y modularidad favorecen reutilización y mantenimiento, aunque requieren experiencia y diseño cuidadoso. [CL02-P, p. 8]; [CL02-A, p. 3]

RUP es iterativo e incremental, usa UML y organiza el proyecto en inicio, elaboración, construcción y transición. Está dirigido por casos de uso, centrado en arquitectura y atento a riesgos. [CL02-P, p. 9]; [CL02-P, p. 10]; [CL02-A, p. 7] PRINCE2 se concentra en organización, gestión y control, con roles claros, fases controladas, justificación continua del negocio, riesgos y calidad. [CL02-P, p. 13]; [CL02-P, p. 14]; [CL02-P, p. 15]

## Enfoque ágil

La agilidad prioriza flexibilidad, colaboración, adaptación al cambio y entrega continua de incrementos funcionales. [CL02-P, p. 16]; [CL02-P, p. 18] No elimina planificación ni disciplina: cambia la escala y frecuencia con las que se decide, construye y obtiene feedback.

### XP y TDD

XP combina ciclos cortos y feedback continuo con cinco valores —comunicación, simplicidad, feedback, respeto y coraje— y doce prácticas: cliente in situ, ritmo sostenible, metáforas, diseño simple, refactorización, programación en pareja, entregas cortas, pruebas, estándares, propiedad colectiva, integración continua y juego de planificación. [CL02-P, p. 20]; [CL02-P, p. 21]; [CL02-P, p. 22]

TDD operacionaliza parte de esa búsqueda de calidad mediante **rojo–verde–refactor**: primero una prueba que falla, luego el código mínimo que la satisface y finalmente una mejora estructural sin romper el comportamiento. [CL02-P, p. 24]

### Lean y Kanban

Lean busca maximizar valor y minimizar desperdicio mediante flujo y mejora continua. [CL02-P, p. 23] Kanban hace visible el trabajo, limita el trabajo en progreso, gestiona el flujo y ayuda a detectar cuellos de botella; es especialmente útil cuando las prioridades o llegadas de trabajo cambian de forma continua. [CL02-P, p. 25]; [CL02-P, p. 26]

## Scrum como sistema conectado

Scrum organiza la entrega en sprints consecutivos de una a cuatro semanas. Cada sprint transforma ítems acordados del Backlog de Producto en un incremento potencialmente desplegable. [CL02-P, p. 27]; [CL02-P, p. 29]

| Componente | Responsabilidad o propósito |
|---|---|
| Product Owner | Sostiene visión, prioriza el backlog, representa necesidades de negocio y maximiza valor. |
| Scrum Master | Facilita Scrum, acompaña al equipo, remueve impedimentos y lo protege de interferencias. |
| Equipo | Multidisciplinario y autogestionado; decide cómo convertir el backlog en incremento. |
| Backlog de Producto | Lista dinámica y priorizada de necesidades; expresa el qué. |
| Backlog de Sprint | Trabajo negociado para el sprint, descompuesto y actualizado diariamente. |
| Burndown | Visualiza cómo disminuye el esfuerzo restante durante el sprint. |

Los roles se detallan en [CL02-P, p. 30], [CL02-P, p. 31] y [CL02-P, p. 32]; los artefactos, en [CL02-P, p. 33], [CL02-P, p. 34], [CL02-P, p. 35] y [CL02-P, p. 36].

El flujo de eventos es:

1. **Planning:** equipo, Product Owner y Scrum Master comprenden y seleccionan ítems y construyen el Sprint Backlog. [CL02-P, p. 37]
2. **Daily:** el equipo sincroniza trabajo y explicita impedimentos en una reunión breve. [CL02-P, p. 38]
3. **Review:** se inspecciona el incremento con interesados y se obtiene feedback sobre el producto. [CL02-P, p. 39]
4. **Retrospective:** se inspeccionan proceso e interacciones y se acuerdan mejoras concretas. [CL02-P, p. 40]

La **Definition of Ready** evalúa si el trabajo está suficientemente entendido y es factible antes de iniciarlo; la **Definition of Done** establece criterios compartidos para considerar completo y entregable un incremento. [CL02-P, p. 42]; [CL02-P, p. 43]; [CL02-P, p. 44]

## Comparación útil

| Pregunta | Predictivo/estructurado | Adaptativo/ágil |
|---|---|---|
| ¿Cuándo se decide? | Más al inicio y por fase | Repetidamente, por iteración |
| ¿Cómo trata el cambio? | Como excepción que debe controlarse | Como información para repriorizar |
| ¿Cómo demuestra avance? | Documentos, hitos y cierre de fases | Incrementos funcionando y feedback |
| ¿Dónde se gestiona calidad? | Actividades y controles definidos por fase | Integrada en cada ciclo mediante pruebas, DoD, revisión y mejora |

Esta comparación es una síntesis de los rasgos de metodología estructurada [CL02-P, p. 5], agilidad [CL02-P, p. 16] y Scrum [CL02-P, p. 27]; [CL02-P, p. 44]. No implica que todo proyecto real sea puramente predictivo o ágil.

## Conexiones

- Los sprints y retrospectivas realizan ciclos de [mejora PDCA](fundamentos-procesos-y-ciclos-de-vida.md).
- Backlogs, Planning Poker y burndown conectan Scrum con [estimación](estimacion-de-proyectos.md).
- TDD, integración continua y DoD conectan las metodologías con [calidad](calidad-de-software.md).
