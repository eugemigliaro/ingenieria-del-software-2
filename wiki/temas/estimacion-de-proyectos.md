# Estimación de proyectos de software

> **Primer parcial:** entran Ley de Parkinson, PCU —sin la lámina de cálculo final—, Planning Poker, Story Points, PERT, juicio experto, T-Shirt Sizing y conceptos clave. Quedan fuera Puntos de Función, COCOMO y estimadores personalizados. Parkinson es una excepción confirmada al recorte del PDF. Ver [alcance detallado](../parcial-1-alcance.md#estimación). [N-2026-09-07-parkinson-primer-parcial]

## Qué se intenta estimar

Estimar sostiene decisiones de alcance, presupuesto, recursos, riesgo y viabilidad; una cifra deficiente puede producir sobrecostos, retrasos, mala asignación y problemas de calidad. [CL05-A, p. 1]; [CL05-A, p. 2] Antes de elegir una técnica hay que separar:

| Variable | Significado |
|---|---|
| Tamaño | Magnitud del trabajo o producto. |
| Esfuerzo | Recursos humanos requeridos, como horas o persona-meses. |
| Complejidad | Dificultad técnica y organizativa, riesgo e incertidumbre. |
| Duración | Tiempo calendario, condicionado por esfuerzo, capacidad y restricciones. |

El material distingue explícitamente estas cuatro variables. [CL05-P, p. 22]; [CL05-A, p. 6] No crecen necesariamente de forma lineal: agregar personas no convierte automáticamente esfuerzo en menor duración. [CL05-A, p. 5]

## Incertidumbre y Ley de Parkinson

La Ley de Parkinson sostiene que el trabajo tiende a expandirse hasta ocupar el tiempo disponible. En planificación, alerta contra plazos arbitrariamente holgados y contra confundir una fecha impuesta con una estimación realista. El tema entra en el primer parcial aunque sus diapositivas no aparezcan en `P1-CL05`. [CL05-P, p. 5]; [CL05-P, p. 6]; [CL05-A, p. 1]; [N-2026-09-07-parkinson-primer-parcial]

La actividad inicial de la cátedra remarca dos buenas prácticas: expresar rangos y supuestos, y admitir cuando falta información en lugar de fabricar precisión. [CL05-P, p. 2]; [CL05-P, p. 4]

## Técnicas

| Técnica | Base | Aporte principal | Dependencia o límite |
|---|---|---|---|
| PCU | Actores y casos de uso ponderados, factores técnicos/ambientales y productividad | Vincula alcance funcional con esfuerzo | Requiere casos de uso y criterios de complejidad consistentes |
| PF | Entradas, salidas, consultas, archivos e interfaces | Compara funcionalidad sin depender del lenguaje | Exige experiencia de conteo y requisitos suficientemente conocidos |
| Planning Poker | Votación simultánea y discusión del equipo | Expone supuestos, riesgos y diferencias de interpretación | El resultado depende del conocimiento compartido |
| Story Points | Tamaño relativo de historias | Planifica capacidad sin prometer horas exactas | La escala pertenece al equipo y no es una medida universal |
| PERT | Escenarios optimista, más probable y pesimista | Hace visible la incertidumbre | La salida depende de la calidad de los tres escenarios |
| COCOMO | KLOC, tipo de proyecto y factores de ajuste | Relaciona tamaño con esfuerzo mediante datos/modelo | Necesita calibración, tamaño y contexto comparables |
| Informales | Expertos, analogías, Delphi, tallas o estimación rápida | Velocidad y utilidad temprana | Sesgos, referencias pobres o criterios vagos reducen precisión |

### PCU y PF

PCU clasifica casos de uso y actores, obtiene puntos sin ajustar, aplica factores técnicos y ambientales y convierte el resultado a esfuerzo mediante productividad. Su valor depende de la calidad de requisitos y del criterio de ponderación. [CL05-A, p. 2] PF contabiliza cinco componentes —entradas, salidas, consultas, archivos internos e interfaces externas— y los pondera por complejidad. [CL05-A, p. 2]; [CL05-A, p. 3]

### Planning Poker y Story Points

En Planning Poker cada integrante estima en secreto, se revelan los valores a la vez y se discuten las diferencias hasta converger. La divergencia no es un error: permite descubrir riesgos, dependencias y supuestos que una estimación individual ocultaría. [CL05-P, p. 13]; [CL05-A, p. 3]

Los Story Points comparan historias por complejidad, trabajo, riesgo e incertidumbre. Una historia de 5 puntos es mayor que una de 2 dentro de la escala del equipo, pero no implica una proporción fija de horas. [CL05-A, p. 4]

### PERT

PERT usa tres estimaciones y pondera más la considerada probable:

`Estimación = (Optimista + 4 × Más probable + Pesimista) / 6`

La técnica integra escenarios extremos y permite razonar sobre contingencia en trabajo incierto. [CL05-P, p. 16]; [CL05-A, p. 4]

### COCOMO

COCOMO expresa el esfuerzo mediante `a × KLOC^b × F`; `a` y `b` dependen del tipo de proyecto y `F` ajusta producto, hardware, personal y proyecto. El procedimiento clasifica el proyecto, estima KLOC, aplica coeficientes y calcula esfuerzo, tiempo y personal. [CL05-P, p. 17]; [CL05-P, p. 18]

### Técnicas informales

Juicio experto es rápido pero susceptible a sesgos; Delphi itera estimaciones anónimas para reducir influencia jerárquica; analogía exige antecedentes realmente similares; T-Shirt Sizing sirve para ordenar rápidamente si el equipo comparte criterios; la estimación “a ojo” es veloz pero poco confiable. [CL05-P, p. 19]; [CL05-P, p. 20]

## Práctica recomendada

1. Definir qué variable se necesita y para qué decisión.
2. Escribir supuestos, faltantes y un rango inicial.
3. Elegir la técnica según requisitos disponibles, datos históricos, experiencia y etapa del producto.
4. Descomponer hasta unidades manejables sin perder costos de integración ni crear burocracia excesiva. [CL05-A, p. 5]; [CL05-A, p. 6]
5. Incluir perspectivas de desarrollo, análisis, pruebas y negocio.
6. Medir resultados y reestimar en cada iteración o hito porque el conocimiento cambia. [CL05-A, p. 7]

Ningún método produce certeza ni es universalmente superior. La meta es una estimación realista, trazable y actualizable; tanto subestimar como sobreestimar tiene costos. [CL05-A, p. 5]; [CL05-A, p. 7]

## Conexiones

- Las estimaciones alimentan backlogs y planificación en [Scrum](metodologias-clasicas-y-agiles.md).
- Canvas y experimentos reducen incertidumbre antes de comprometer una [solución de producto](productos-digitales.md).
- Esfuerzo de pruebas, prevención y deuda deben formar parte del cálculo de [calidad](calidad-de-software.md).
