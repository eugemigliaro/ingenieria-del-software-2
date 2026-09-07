# Fundamentos, procesos y ciclos de vida

> **Primer parcial:** entran las tres definiciones de Ingeniería de Software y los modelos cascada, prototipo, incremental y espiral. Quedan fuera SWEBOK, vocabulario operativo, crisis del software, Deming/PDCA, ética y *No Silver Bullet*. Ver [alcance detallado](../parcial-1-alcance.md#introducción-y-ciclos-de-vida). [N-2026-09-07-alcance-primer-parcial]

## Ingeniería de Software

La Ingeniería de Software abarca todos los aspectos de producción de software, desde la especificación inicial hasta el mantenimiento. El material reúne tres énfasis complementarios: Sommerville pone el foco en el ciclo completo; Pressman, en la combinación de proceso, métodos y herramientas para entregar calidad bajo restricciones; Jacobson, en métodos para construir software complejo, orientación a objetos y casos de uso. [CL01-P, p. 2]; [CL01-P, p. 3]; [CL01-P, p. 4]

No es sinónimo de programar. Incluye requisitos, diseño, construcción, pruebas, mantenimiento, configuración, gestión de proyectos, procesos, herramientas y calidad, áreas que SWEBOK organiza como cuerpo común de conocimiento. [CL01-A, p. 2]; [CL01-A, p. 3]

## Vocabulario operativo

| Concepto | Idea central |
|---|---|
| Proceso | Fases sucesivas y actividades asociadas: el **qué**. |
| Procedimiento | Acciones u operaciones que indican el **cómo**. |
| Tarea | Trabajo acotado que debe realizarse en un tiempo limitado. |
| Proyecto | Actividades relacionadas para producir un resultado dentro de tiempo y presupuesto. |
| Metodología | Marco para estructurar, planificar y controlar el proceso. |

Estas distinciones aparecen explícitamente en la introducción de la cátedra. [CL01-P, p. 8] En particular, el ciclo de vida expresa qué se obtiene y la metodología cómo se lo obtiene. [CL01-P, p. 12]

## Proceso de software

Un proceso de software guía la creación y evolución del producto. Sus objetivos son ordenar el trabajo, facilitar la comunicación, crear hitos de seguimiento y sostener calidad mediante verificación, validación y control de cambios. [CL01-A, p. 3]; [CL01-A, p. 4]

Las fases generales son planificación, análisis de requisitos, diseño, implementación, pruebas, despliegue y mantenimiento. No todos los modelos las encadenan igual: pueden ejecutarse de forma secuencial, iterativa o incremental. [CL01-A, p. 4]

## PDCA y mejora continua

PDCA repite cuatro acciones: **Plan** define objetivos, acciones y métricas; **Do** ejecuta y recoge datos; **Check** contrasta resultados con objetivos; **Act** corrige o estandariza y abre un nuevo ciclo. [CL01-A, p. 9]; [CL01-A, p. 10]

La relación con agilidad es directa: en un sprint se planifica el trabajo, se construye, se revisan producto y proceso y se ajustan backlog y prácticas para el siguiente ciclo. Las métricas hacen que la verificación sea objetiva y permiten aprender. [CL01-A, p. 10]

## Modelos de ciclo de vida

| Modelo | Organización | Fortaleza | Riesgo o límite | Contexto orientativo |
|---|---|---|---|---|
| Cascada | Fases secuenciales cerradas | Hitos, documentación y control claros | Tolera mal cambios y detecta tarde algunos errores | Requisitos estables y alto control formal |
| Prototipo | Construcción rápida, feedback y refinamiento | Aclara requisitos y descubre necesidades | Confundir prototipo con producto o generar expectativas irreales | Alta interacción o necesidad incierta |
| Incremental | Entregas funcionales sucesivas | Valor y retroalimentación tempranos | Exige priorización e integración continua | Entrega progresiva y adaptación |
| Espiral | Iteraciones guiadas por análisis de riesgos | Reduce incertidumbre técnica y de negocio | Gestión y estimación más complejas | Proyectos grandes, complejos o riesgosos |

La secuencia y los compromisos de cascada se describen en [CL01-A, p. 5]; prototipado y sus riesgos, en [CL01-A, p. 5] y [CL01-A, p. 6]; el valor incremental, en [CL01-A, p. 6]; y las vueltas de planificación, riesgo, desarrollo y evaluación de la espiral, en [CL01-A, p. 6] y [CL01-A, p. 7].

La elección no es ideológica: depende de estabilidad de requisitos, riesgo, cultura, tamaño, capacidades y restricciones del proyecto. El propio material pregunta qué modelo conviene para un problema bien comprendido y estructurado, destacando la necesidad de justificar la decisión. [CL01-P, p. 24]

## Ética, impacto social y complejidad esencial

La responsabilidad profesional comprende al público, al cliente, al empleador y a la profesión. Privacidad, seguridad, accesibilidad, propiedad intelectual, transparencia en riesgos y estimaciones, y consecuencias sociales deben tratarse como decisiones de ingeniería. [CL01-P, p. 25]; [CL01-A, p. 7]; [CL01-A, p. 8]; [CL01-A, p. 9]

“No Silver Bullet” advierte que ningún avance aislado elimina la complejidad esencial del software. Es una invitación a desconfiar de soluciones universales y evaluar herramientas y métodos dentro de su contexto. [CL01-P, p. 26]; [CL01-P, p. 27]

## Conexiones

- Los [métodos clásicos y ágiles](metodologias-clasicas-y-agiles.md) concretan distintas maneras de recorrer el proceso.
- La [estimación](estimacion-de-proyectos.md) informa planificación, presupuesto y riesgo.
- La [calidad](calidad-de-software.md) atraviesa todas las fases y reutiliza PDCA como estructura de mejora.
