# Caso HealthCare.gov

> **Fuentes:** la consigna y presentación del caso, `CASO-HCG`, y el informe oficial de la Oficina del Inspector General del HHS, `B04`, que la consigna señala como punto de partida. [CASO-HCG, p. 8] Las páginas de `B04` se citan según el PDF. En el cuerpo del informe, el número impreso es el del PDF menos 8; por ejemplo, la página impresa 1 es [B04, p. 9]. La infografía y el diagrama de `CASO-HCG` son imágenes y se revisaron renderizadas.

## Para qué se usa el caso

La consigna ubica al estudiante en un equipo de arquitectos que, tras el fracaso del lanzamiento, debe evaluar la arquitectura con **ATAM**. La evaluación servirá como entrada para una nueva versión del sistema. [CASO-HCG, p. 8]

La clase se divide en dos grupos y cada grupo simula las **fases 0 y 1** de ATAM: [CASO-HCG, p. 9]

- **Fase 0:** revisar qué debe hacerse y simularlo.
- **Fase 1:** revisar y simular. Hay que evaluar la situación, crear escenarios, crear el árbol de utilidad y presentar, incluyendo la utilidad.
- Luego, presentar a la clase.

El método está desarrollado en [Evaluación de arquitecturas](evaluacion-de-arquitecturas.md#atam) y en el [caso de estudio ATAM de Hariharan](evaluacion-de-arquitecturas.md#atam-en-la-práctica-caso-de-estudio-de-hariharan).

## Contexto

- En marzo de 2010, Obama firmó la *Affordable Care Act* (ACA). [CASO-HCG, p. 2] La ley se promulgó el 23 de marzo de 2010 y exigió un mercado de seguros de salud (*marketplace*) en cada estado, operativo antes del 1 de enero de 2014. Para los estados que no crearan el suyo, el gobierno federal debía operarlo. [B04, p. 9]
- HealthCare.gov es el sitio de ese mercado federal, presentado como un sitio de compra «todo en uno» de seguros de salud. La CBO pronosticó 7 millones de usuarios en el primer año. [CASO-HCG, p. 2]
- Los contratos de desarrollo se adjudicaron en septiembre de 2011. [CASO-HCG, p. 2] El 30 de septiembre de 2011, CMS contrató a CGI Federal para construir el FFM y a QSSI para el Hub; el EIDM se contrató a QSSI en junio de 2012. [B04, p. 76]
- El sitio se lanzó el 1 de octubre de 2013, con serios problemas tecnológicos. [CASO-HCG, p. 2]

## Arquitectura

### Componentes según el informe oficial

El informe identifica cuatro piezas clave: [B04, p. 10]

| Componente | Función | Contratista |
|---|---|---|
| **EIDM** (*Enterprise Identity Management*) | Crear cuentas y verificar la identidad de los consumidores. Se construyó para varios sistemas de CMS, incluido Medicare | QSSI [B04, p. 21] |
| **FFM** (*Federally-facilitated Marketplace*) | Núcleo del sistema, con tres subcomponentes: *Eligibility and Enrollment*, que determina la elegibilidad y gestiona las inscripciones con las aseguradoras; *Plan Management*, que coordina con las aseguradoras la cobertura; y *Financial Management*, que registra inscripciones efectivas y gestiona pagos | CGI Federal, que también desarrolló la interfaz web y la solicitud online [B04, p. 21] |
| **Data Services Hub** | Enrutar consultas entre los mercados federal y estatales, las agencias de Medicaid/CHIP y otras agencias federales, como el IRS y la SSA | QSSI [B04, p. 21] |
| Infraestructura | Capacidad de cómputo y hosting de grandes componentes | Terremark [B04, p. 37] |

### Diagrama de funciones del exchange

El diagrama de la consigna organiza el sistema en cinco grupos: [CASO-HCG, p. 4]

- **Arriba:** un portal web conectado con el programa de navegadores (*guidance*) y con brokers.
- **Federal, a la izquierda:** el **Federal Data Services Hub & APTC/CSR** se comunica con IRS, Tesoro, Seguridad Social, Homeland Security y HHS. Verifica ingresos, créditos fiscales, subsidios, reducción de costos, ciudadanía y residencia, y envía reportes.
- **Centro:** una **interfaz de inscripción y elegibilidad** vinculada con los sistemas estatales de Medicaid.
- **Debajo:** una **interfaz de comparación de planes** con los planes de salud y una calculadora online de costos totales; una **interfaz de administración** con eventos de vida y servicio al cliente; y una **interfaz de comunicación** con las aseguradoras (*carriers*) y la gestión de planes SERFF.
- **Otros servicios:** servicios financieros (facturación de primas) y ajuste de riesgo.

La leyenda distingue cuatro tipos de componente: federales, de proveedores tecnológicos, de aseguradoras y estatales. [CASO-HCG, p. 4]

### Flujo funcional

Un segundo diagrama ordena las funciones como un flujo de arriba abajo: [CASO-HCG, p. 5]

1. Difusión (*outreach*).
2. Portal web.
3. **Elegibilidad**, conectada en ambos sentidos con:
   - CCIIO, que verifica ciudadanía e ingresos con Seguridad Social y Homeland Security;
   - reportes al Secretario del HHS;
   - el IRS, por los créditos fiscales;
   - las reglas de elegibilidad de Medicaid/CHIP;
   - derivaciones a agencias estatales;
   - el Tesoro, por los subsidios.
4. **Comparar y elegir planes**, con una calculadora online.
5. **Inscripción**, que también alimenta el MMIS.
6. **Servicios administrativos y facturación consolidada**, conectados con servicios al empleador (notificaciones, suscripción, facturación y atención al cliente).
7. **Interfaces**, vinculadas con la agencia estatal de seguros que certifica los planes.
8. **Aseguradoras** (*health plan carriers*).

La página 6 de la consigna está en blanco: solo contiene el fondo decorativo.

**Inferencia:** el Hub funciona como un *broker* o integrador entre el mercado y muchas agencias externas. El acceso y la verificación de identidad son una única puerta de entrada por la que pasan todos los usuarios. Esa centralización se volvió decisiva en el lanzamiento.

### Proceso y problemas

La infografía recorre ocho pasos del flujo del consumidor y señala un problema en varios de ellos: [CASO-HCG, p. 3]

| Paso | Qué hace el sistema | Problema |
|---|---|---|
| 1. Entrada | El portal de login permite elegir un estado y crear una cuenta (CGI) | A fines de septiembre se excluyó la función que permitía ver planes sin crear cuenta. Más gente de la prevista tuvo que registrarse y eso generó un cuello de botella |
| 2. Registro | Datos básicos, pregunta de seguridad y verificación por e-mail | La comunicación entre algunos sistemas fallaba y muchos usuarios no podían crear la cuenta |
| 3. Prueba de identidad | Herramienta de registro de QSSI, con verificación a través de Experian | — |
| 4. Elegibilidad | El Data Hub de QSSI consulta decenas de agencias federales y estatales, y a Equifax para verificar ingresos | — |
| 5. Compra de un plan | El consumidor compara planes y su costo menos los subsidios | Personas de bajos ingresos recibían respuestas erróneas: que no calificaban para subsidios o Medicaid |
| 6. Traducción | El formulario del plan elegido pasa por el Data Hub y se convierte a un formato electrónico para las aseguradoras | — |
| 7. Inscripción | Se envía a cada aseguradora un reporte diario de inscriptos | Los reportes (*834s*) eran confusos o duplicados, y las aseguradoras no sabían quiénes eran sus nuevos clientes |
| 8. Cobertura | — | Se reportaron más de 700.000 solicitudes, pero no cuántas personas se inscribieron efectivamente |

## Problemas del lanzamiento

La consigna resume los problemas en siete métricas: [CASO-HCG, p. 7]

| Aspecto | Síntoma |
|---|---|
| Performance | Tiempo de respuesta de la página de inicio mayor a 8 s |
| Navegación | Interfaz rota |
| Estabilidad | Caídas intermitentes; disponibilidad de alrededor del 43 % |
| Funcionalidad | Datos incorrectos e incompletos |
| Tasa de error | Alrededor del 6 % por página |
| Escalabilidad | Menos de 1.100 usuarios concurrentes |
| Completitud | Menos del 30 % de inscripciones completadas |

El informe oficial aporta estos datos:

- El 1 de octubre de 2013 hubo 250.000 usuarios concurrentes, mucho más que la capacidad planificada. Las caídas empezaron dentro de las dos horas, y solo seis consumidores pudieron enviar una solicitud y elegir un plan ese día. El problema no era solo el volumen: había problemas de fondo en la performance del sitio. [B04, p. 40]
- El primer cuello de botella fue el **EIDM**: «como una rampa de acceso de un solo carril a una autopista». QSSI no sabía que todos los visitantes entrarían por el EIDM y subestimó la capacidad necesaria. Además, el EIDM impedía que los desarrolladores entraran al sitio para ver los demás errores, aunque el problema mayor era el FFM. [B04, p. 41]
- No había monitoreo integrado. Cada contratista monitoreaba su propio sistema sin ver los demás, aunque los sistemas trabajaban juntos, y había varios «centros de comando» separados. [B04, p. 42]
- El sitio funcionaba el 42 % del tiempo a principios de noviembre y más del 90 % a fines de ese mes. [B04, p. 47]

## Causas técnicas según el informe

| Causa | Evidencia |
|---|---|
| Requisitos inestables | CMS seguía tomando decisiones regulatorias y de política mientras se construía. Los requisitos de negocio y las especificaciones técnicas no estaban cerrados. [B04, p. 23] |
| Agile mal aplicado | El método ágil facilitó cambios frecuentes y tardíos. CMS no definía los requisitos al inicio de cada sprint y los cambiaba durante el sprint. [B04, p. 24] |
| Persistencia sin experiencia disponible | CMS impuso la plataforma NoSQL de MarkLogic pese a las advertencias del contratista sobre su falta de experiencia. [B04, p. 24]; [B04, p. 25] Ver [Persistencia](persistencia.md#un-caso-real-nosql-en-healthcaregov). |
| Código autogenerado | El código *Model-Driven Architecture* cubría quizás el 60–70 % del desarrollo, se coordinaba mal con el código manual y era difícil de modificar ante cambios tardíos. [B04, p. 25]; [B04, p. 26] |
| Gestión de cambios débil | El *Change Control Board* cancelaba reuniones y no registraba los cambios en el repositorio central. A veces se lo eludía por completo. [B04, p. 26] |
| Advertencias ignoradas | Hubo 18 advertencias documentadas entre julio de 2011 y julio de 2013. Entre los diez riesgos principales que listó TurningPoint en abril de 2013 figuraban la planificación inadecuada de la capacidad y el desvío de los estándares de arquitectura de TI. [B04, p. 29] |
| Sin integrador de sistemas | CMS creía cumplir ese rol, pero tenía poca experiencia en integrar un proyecto de ese tamaño. [B04, p. 30] |
| Calidad de código | Había muchos defectos y cambios sin documentar ni analizar su impacto en otras partes. Se desplegaban versiones incorrectas, y el FFM consultaba la base más de 100 veces por operación con un «modelo de datos inflado». [B04, p. 30]; [B04, p. 31] |
| Pruebas insuficientes | Se priorizó la fecha sobre las pruebas. Nunca se completaron las pruebas *end-to-end*, porque los componentes llegaron tarde, y faltaban entornos de prueba. [B04, p. 35] |
| Capacidad tardía | El 26 de septiembre de 2013, una prueba de performance limitada mostró que el sistema soportaba muchos menos usuarios concurrentes de lo planificado, en parte porque el código requería más infraestructura de la prevista. Se pidió duplicar la capacidad en 72 horas. [B04, p. 37] |
| Seguridad sin probar | El FFM salió con una autorización interina de 6 meses, condicionada a completar las pruebas de seguridad. [B04, p. 37] |
| Recorte de alcance | Se postergó la herramienta *anonymous shopper*, que permitía ver planes antes de completar la solicitud, porque daba información incorrecta. [B04, p. 35] Según QSSI, esa postergación aumentó el tráfico del EIDM. CMS aclaró que la herramienta tampoco habría sido anónima. [B04, p. 41] |

El informe resume los factores de la caída en **liderazgo** poco claro, **gestión deficiente del contrato** clave, **resistencia a las malas noticias**, **dependencia del camino** —seguir el mismo plan pese a los problemas— y correcciones débiles y tardías. [B04, p. 5]

## Recuperación

Las decisiones técnicas de la recuperación fueron estas:

- **Refactorizar en vez de reescribir:** se corrigió y simplificó el código existente, por el enorme tiempo que exigía empezar de cero. [B04, p. 44]
- **Redundancia:** se construyeron sistemas de respaldo para tres componentes clave. El *Scalable Log-In System* (SLS) es un sistema de cuentas exclusivo de HealthCare.gov, a diferencia del EIDM, compartido por toda CMS. App 2.0 es una solicitud simplificada, y Plan Compare 2.0 permite comparar planes sin crear cuenta. [B04, p. 44]
- **Distribución:** tres empresas operaron centros de datos con distintas funciones, para «no poner todos los huevos en la misma canasta». [B04, p. 44]
- **Monitoreo:** se incorporaron herramientas para el tráfico, el uso de capacidad, la velocidad de transferencia a los estados y la seguridad, con dashboards de performance. [B04, p. 44]
- **Integrador:** se contrató a QSSI como integrador técnico de sistemas. [B04, p. 44]
- **Salas de espera:** ante una sobrecarga, se enviaba a los consumidores a «salas de espera» con aviso por e-mail. A fines de noviembre de 2013, el sitio soportaba más de 35.000 usuarios concurrentes. [B04, p. 47]
- **Segunda inscripción:** no hubo caídas. La mediana del tiempo de login bajó de 18,46 s a 3,21 s, y el sitio soportó 250.000 usuarios concurrentes. [B04, p. 59]; [B04, p. 60]

Los factores organizacionales fueron una cultura *badgeless*, en la que personal de CMS y contratistas trabajaban como un solo equipo; **priorización despiadada** (*ruthless prioritization*) del alcance; **calidad por encima de la entrega a tiempo**; simplificación de procesos; y aprendizaje continuo. [B04, p. 6]

## Lecciones del informe

El OIG formula diez lecciones: [B04, p. 4]

1. **Liderazgo:** asignar un liderazgo de proyecto claro, con visión integral del progreso.
2. **Alineación:** alinear estrategias con los recursos y la experiencia disponibles.
3. **Cultura:** identificar y abordar los factores culturales que afectan al proyecto.
4. **Simplificación:** simplificar procesos, sobre todo en proyectos de alto riesgo de fracaso.
5. **Integración:** integrar el trabajo de política con el tecnológico.
6. **Comunicación:** aceptar las malas noticias y alentar a reportar problemas.
7. **Ejecución:** diseñar estrategias de ejecución disciplinada y medir el progreso continuamente.
8. **Supervisión:** asegurar la efectividad de los contratos de TI mediante innovación, integración y supervisión rigurosa.
9. **Planificación:** preparar planes de contingencia rápidamente aplicables, como sistemas redundantes y escalables.
10. **Aprendizaje:** promover el aprendizaje continuo para poder cambiar de rumbo rápido.

## Insumos del caso para ATAM

**Inferencia:** esta sección no resuelve la consigna. Solo ordena los hechos del material según las entradas de ATAM. Para resolverla, usar `$resolver-practica`.

| Entrada de ATAM | Material del caso |
|---|---|
| Business drivers | Mercado federal obligatorio por ley, con fecha fija; 7 millones de usuarios previstos el primer año; compra «todo en uno» [CASO-HCG, p. 2]; [B04, p. 9] |
| Atributos de calidad en juego | Performance, disponibilidad, escalabilidad, usabilidad o navegación, corrección funcional [CASO-HCG, p. 7]; seguridad [B04, p. 37]; integrabilidad con agencias y aseguradoras [CASO-HCG, p. 4] |
| Enfoques arquitectónicos | Hub de integración, punto único de identidad compartido con otros programas, combinación de bases relacional y NoSQL, generación de código MDA [B04, p. 10]; [B04, p. 24]; [B04, p. 25] |
| Candidatos a riesgo | El EIDM como cuello de botella y punto único de entrada [B04, p. 41]; dependencia de muchas agencias externas [CASO-HCG, p. 3]; falta de pruebas *end-to-end* y de monitoreo integrado [B04, p. 35]; [B04, p. 42] |

## Conexiones

- [Evaluación de arquitecturas](evaluacion-de-arquitecturas.md): ATAM, árbol de utilidad, riesgos, puntos sensibles y trade-offs.
- [Persistencia](persistencia.md): la elección de MarkLogic y el modelo de datos inflado.
- [Metodologías clásicas y ágiles](metodologias-clasicas-y-agiles.md): el informe muestra un ágil aplicado sin requisitos estables por sprint ni gestión disciplinada de cambios. [B04, p. 24]; [B04, p. 26]
- [Calidad de software](calidad-de-software.md): pruebas *end-to-end*, defectos, deuda técnica y la decisión de refactorizar en vez de reescribir. [B04, p. 35]; [B04, p. 44]
- [Estilos arquitectónicos](estilos-arquitectonicos.md): el Hub como broker y la distribución en varios centros de datos. **Inferencia.**
- [Arquitecturas de integración](arquitecturas-de-integracion.md): el Data Services Hub como hub de integración entre el mercado y las agencias. [B04, p. 10] **Inferencia.**
