Análisis sustentado en el proyecto #42: [[Proyecto a resolver]]
Estos cuatro recursos cubren exactamente las tres capas que necesitas para la fase de "análisis y diagnóstico": **capítulo de metodología de requisitos** (Pressman & Sommerville), **capítulo de técnicas de modelado** (Sommerville + Kendall) y **capítulo de marco de arquitectura y stakeholders** (42010). Cada uno tiene un rol distinto, no se sustituyen entre sí.

## Fuentes de los libros:
* Roger S. Pressman, Ph.D. Bruce R. Maxim, Ph.D: **Ingeniería de software Un enfoque práctico** (Novena edición). <https://embed.gaboggamer.online/SnC8oA9c9tRSYnK.pdf>
* KENNETH E. KENDALL & JULIE E. KENDALL (2011): **Análisis y diseño de sistemas** (Octava edición). <https://ccie.com.mx/wp-content/uploads/2020/03/ld-Analisis-y-Diseno-de-Sistemas_Kendall-8va.pdf>
* Ian Sommerville (2016): **Software Engineering** (Décima edición). <https://dn790001.ca.archive.org/0/items/bme-vik-konyvek/Software%20Engineering%20-%20Ian%20Sommerville.pdf>
* **Estándar ISO/IEC/IEEE/42010-2022**: <https://cdn.standards.iteh.ai/samples/74393/fc7b7f103d8446a4b87a3261e31370d3/ISO-IEC-IEEE-42010-2022.pdf>

### 📘 Pressman & Maxim (9na ed.): Definen "qué es la ingeniería de requisitos"

Pressman & Maxim dividen la ingeniería de requisitos en **siete actividades**: concepción, levantamiento, elaboración, negociación, especificación, validación y gestión. Esto se corresponde casi perfectamente con las subpreguntas a-f del punto 5 de tu tarea.

**Cómo usarlo en tu proyecto**: No necesitas inventar el proceso. Al responder el punto 5, puedes escribir directamente: "Siguiendo el marco de siete actividades de Pressman & Maxim, la elicitación de este proyecto se basa principalmente en el análisis de documentos (PDF del Problema #42) y la simulación de escenarios; la especificación utiliza casos de uso formales para describir la lógica del 'algoritmo de sospecha' y la 'redistribución de topes'". También enfatizan la **trazabilidad y el control de versiones**, lo cual es muy útil cuando justificas "por qué los requisitos del motor de facturación pueden cambiar".

### 📗 Sommerville (10ma ed.): Te dan los "modelos" y el "puente hacia la arquitectura"

La estructura del libro de Sommerville es muy adecuada para tu tarea: **Capítulo 4 Ingeniería de requisitos** (corresponde al punto 5), **Capítulo 5 Modelado de sistemas** (corresponde al modelado de procesos de negocio), **Capítulo 6 Diseño arquitectónico** (corresponde al punto 6).

**Dos cosas que más te ayudarán**:
1. **Modelado de sistemas (Capítulo 5)**: Te enseña a usar modelos de contexto, modelos de interacción y modelos estructurales para describir el sistema. Para los cuatro subsistemas de tu centro comercial (contratos, auditoría, liquidación, cobranza), puedes usar el "modelo de interacción" para dibujar quién intercambia qué datos con quién, y luego derivar requisitos funcionales.
2. **Diseño arquitectónico (Capítulo 6)**: Introduce **decisiones de diseño arquitectónico, vistas arquitectónicas y patrones arquitectónicos**. Cuando respondas el punto 6, puedes citar los "patrones arquitectónicos" de Sommerville para explicar por qué el motor de liquidación debe separarse del resto del sistema (porque el patrón de cálculo del prorrateo es propenso a cambios y necesita bajo acoplamiento).

### 📙 Kendall & Kendall (8va ed.): Te dan las "técnicas de recolección" y "herramientas de modelado"

Kendall & Kendall no están en los resultados de búsqueda, pero según el marco que discutimos antes, su rol es **operativo**: te dicen cómo recolectar información (entrevistas, JAD, análisis de documentos), cómo dibujar DFD y diccionarios de datos, y cómo usar UML para modelado orientado a objetos.

**Cómo usarlo en tu proyecto**: En la elicitación del punto 5, puedes justificar: "Dado que no hay un cliente real, se utilizan **métodos no intrusivos** (análisis de documentos) y **métodos interactivos simulados** (talleres JAD para modelar las reglas de negocio de los cuatro subsistemas)". Al mismo tiempo, usa DFD o diagramas de casos de uso UML para expresar la "lógica de negocio" de los cuatro subsistemas del PDF; esto te dará una base más sólida al derivar requisitos.

### 📕 ISO/IEC/IEEE 42010: Te da el "discurso de arquitectura" y la "perspectiva de stakeholders"

El estándar 42010 **no te enseña a recolectar requisitos**, especifica claramente que no especifica procesos, métodos o herramientas para crear descripciones arquitectónicas. Su valor está en: te obliga a **identificar stakeholders → identificar sus preocupaciones → decidir qué vistas arquitectónicas usar para responder a esas preocupaciones**.

**Cómo usarlo en tu proyecto**:
- **Stakeholders**: administración del centro comercial (preocupada por la auditabilidad del prorrateo de gastos), locatarios (preocupados por la transparencia en el cálculo de renta variable), auditores (preocupados por la trazabilidad de las "compras misteriosas"), cobranza (preocupada por la exactitud de los intereses por mora).
- **Preocupaciones → decisiones arquitectónicas**: "La administración está preocupada por la auditabilidad del cálculo de prorrateo", por lo tanto el motor de liquidación se diseña como un **módulo separado y registrable**. Esta es una forma de escribir que se ajusta a la lógica del estándar 42010.

### 💡 Así se combinan (lista para usar directamente)

| Paso de tu tarea                          | Qué usar                                                                             | Qué extraer específicamente                                                                                                                              |
| ----------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Punto 5.a Elicitación**                 | Kendall (análisis de documentos) + Pressman (marco de siete pasos)                   | Justificar: fuente de información = PDF + simulación de escenarios                                                                                       |
| **Punto 5.b-c Elaboración/negociación**   | Sommerville Cap.5 (modelado de sistemas)                                             | Usar modelos de interacción para dibujar el flujo de datos entre los cuatro subsistemas                                                                  |
| **Punto 5.d-e Especificación/validación** | Pressman (casos de uso formales) + Sommerville Cap.4                                 | Escribir precondiciones y excepciones para "algoritmo de sospecha" y "redistribución de topes"; validar mediante trazabilidad al PDF                     |
| **Punto 6 Arquitectura**                  | Sommerville Cap.6 (patrones arquitectónicos) + 42010 (stakeholders y preocupaciones) | Explicar por qué se separan motor de liquidación, algoritmo de sospecha y gestión de cobranza; cada módulo responde a una preocupación de un stakeholder |

Si quieres, en el próximo paso podemos aplicar directamente este marco y comenzar a escribir **el punto 5.a (Elicitación) + 5.d (Especificación)**, usando el subsistema de auditoría (compras misteriosas) como ejemplo, para que veas cómo se ven estos cuatro recursos aterrizados en tu proyecto.

### Sustento Metodológico del Proyecto: Marco Teórico Integrado de Autores y Estándares

El desarrollo riguroso de proyectos de ingeniería de software requiere fundamentar las decisiones de análisis, diagnóstico, diseño y gestión en marcos teóricos consolidados. Este documento organiza y sintetiza la doctrina técnica contenida en las obras de  **Roger S. Pressman & Bruce R. Maxim** ,  **Ian Sommerville** ,  **Kenneth E. Kendall & Julie E. Kendall** , así como en el  **Estándar Internacional ISO/IEC/IEEE 42010:2022** .

#### 1\. Visión General: Articulación y Roles de las Fuentes

El desarrollo de software exige un enfoque multidisciplinario donde cada obra y estándar cumple una función metodológica complementaria y no redundante:  
Fuente / Autor,Rol Metodológico Principal,Aporte Específico al Proyecto  
Pressman & Maxim,Marco de Proceso e Ingeniería de Requisitos,"Define las 7 actividades estructurales de la ingeniería de requerimientos, la gestión de la agilidad y los modelos de proceso prescriptivos y evolutivos."  
Sommerville,Modelado de Sistemas y Patrones Arquitectónicos,"Proporciona las abstracciones de modelado de sistemas (interacción, contexto, estructura y comportamiento) y los patrones arquitectónicos clásicos."  
Kendall & Kendall,"Análisis Estructurado, TGS, SDLC y Viabilidad","Aporta los métodos operativos de recolección de información (JAD, entrevistas), el análisis estructurado (DFD, diccionario de datos), los principios de la Teoría General de Sistemas (TGS) y la evaluación formal de viabilidad."  
ISO/IEC/IEEE 42010:2022,Ontología de Descripción Arquitectónica,Define el marco conceptual para conectar formalmente a las partes interesadas ( Stakeholders ) y sus preocupaciones ( Concerns ) con las vistas y puntos de vista de la arquitectura.

#### 2\. Ingeniería de Requerimientos y Técnicas de Obtención

La ingeniería de requerimientos es el conjunto de tareas y técnicas que conducen a una comprensión profunda de las necesidades del cliente y del dominio del problema, sirviendo de puente entre la comunicación inicial y el diseño técnico.

##### Roger S. Pressman & Bruce R. Maxim: El Marco de 7 Actividades

Pressman & Maxim conciben la ingeniería de requerimientos como un proceso adaptable e iterativo compuesto por siete actividades principales:

1. **Concepción (**  ***Inception***  **):**  Establece el entendimiento inicial del problema, identifica las partes interesadas primarias, define el alcance básico y las restricciones presupuestarias o tecnológicas.  
2. **Indagación / Elicitación (**  ***Elicitation***  **):**  Recopilación activa de requerimientos mediante la interacción con las partes interesadas para descubrir los objetivos del negocio y los escenarios de uso.  
3. **Elaboración (**  ***Elaboration***  **):**  Refinamiento y modelado de la información obtenida mediante la creación de modelos de análisis basados en escenarios, clases, funciones y comportamiento.  
4. **Negociación (**  ***Negotiation***  **):**  Resolución de conflictos entre prioridades, restricciones y costos competitivos expresados por diferentes partes interesadas, buscando una condición de "todos ganan".  
5. **Especificación (**  ***Specification***  **):**  Creación de la representación formal del sistema (documentos de requerimientos, casos de uso formales o historias de usuario).  
6. **Validación (**  ***Validation***  **):**  Evaluación de la calidad del modelo de requerimientos para garantizar la ausencia de ambigüedades, inconsistencias u omisiones frente a los estándares.  
7. **Gestión / Administración de Requerimientos (**  ***Management***  **):**  Conjunto de actividades para rastrear la trazabilidad, controlar los cambios y mantener el versionado de requerimientos a lo largo del ciclo de vida.

##### Ian Sommerville: Tipología y Proceso de Requisitos

Sommerville clasifica los requerimientos en dos niveles fundamentales:

* **Requerimientos Funcionales:**  Describen los servicios que el sistema debe proporcionar, cómo debe reaccionar ante entradas particulares y cómo debe comportarse en situaciones específicas.  
* **Requerimientos No Funcionales:**  Restricciones sobre los servicios o funciones ofrecidas por el sistema, tales como propiedades de rendimiento, seguridad, disponibilidad, fiabilidad y estándares de desarrollo.

##### Kenneth E. Kendall & Julie E. Kendall: Métodos de Recolección

Kendall & Kendall dividen las técnicas de obtención en dos grandes categorías operativas:

* **Métodos Interactivos:**  
* *Entrevistas:*  Conversaciones estructuradas o no estructuradas para explorar opiniones y sentimientos de los usuarios clave.  
* *Cuestionarios:*  Instrumentos cuantitativos para muestrear posturas y comportamientos en grandes grupos de usuarios.  
* *Talleres JAD (Joint Application Development):*  Sesiones de trabajo intensivas y facilitadas que reúnen a usuarios y analistas para definir requerimientos en conjunto de manera acelerada.  
* **Métodos Discretos (No Intrusivos):**  
* *Análisis de Documentación:*  Revisión de formularios, informes, manuales de procedimiento y contratos vigentes.  
* *Observación Directa (STROBE):*  Evaluación sistemática del entorno de toma de decisiones y del comportamiento de los empleados.

#### 3\. Modelos y Tipos de Procesos de Software (Enfoque en Ágiles)

El modelo de proceso determina la secuencia, relación y ritmo con que se ejecutan las actividades de ingeniería de software.

##### Modelos Prescriptivos y Tradicionales (Pressman, Sommerville, Kendall)

* **Modelo en Cascada (Secuencial Lineal):**  Flujo de trabajo sistemático y ordenado donde cada fase (requerimientos, análisis, diseño, código, pruebas) debe completarse totalmente antes de pasar a la siguiente. Adecuado únicamente para proyectos con requerimientos fijos y perfectamente comprendidos.  
* **Modelo Incremental:**  Entrega el software en pequeñas partes funcionales (incrementos) a lo largo del tiempo. El primer incremento suele ser el producto núcleo que satisface los requerimientos básicos.  
* **Modelo Evolutivo / Espiral (Boehm):**  Acopla la naturaleza iterativa de los prototipos con el control del modelo en cascada, incorporando el análisis y evaluación formal de riesgos en cada ciclo alrededor de la espiral.

##### Marcos de Desarrollo Ágil

Los modelos ágiles se fundamentan en el Manifiesto Ágil y están diseñados para gestionar la imprevisibilidad mediante la adaptación continua y entregas incrementales cortas.

* **Scrum (Pressman & Maxim / Kendall & Kendall):**  
* *Filosofía:*  Trabajo en equipo de alta intensidad que organiza el desarrollo en ciclos temporales fijos de 2 a 4 semanas denominados  **Sprints** .  
* *Roles:*   **Product Owner**  (representa la voz del cliente y gestiona las prioridades),  **Scrum Master**  (facilita el proceso y remueve obstáculos) y  **Equipo de Desarrollo**  (equipo autoorganizado e interdisciplinario).  
* *Artefactos:*   **Product Backlog**  (lista priorizada de historias de usuario/objetivos),  **Sprint Backlog**  (tareas seleccionadas para el sprint actual) e  **Incremento**  (software funcional liberable).  
* *Ceremonias:*  Sprint Planning (planeación), Daily Scrum (reunión diaria de 15 minutos), Sprint Review (demostración al cliente) y Sprint Retrospective (mejora continua del proceso).  
* **Extreme Programming (XP):**  Enfocado en la excelencia técnica mediante prácticas como programación en parejas, desarrollo guiado por pruebas (TDD) e integración continua.  
* **Kanban:**  Marco centrado en la visualización del flujo de trabajo mediante tableros y la limitación estricta del trabajo en proceso (WIP \-  *Work In Progress* ) para evitar cuellos de botella.  
* **DevOps:**  Extensión de la agilidad que integra los equipos de desarrollo ( *Dev* ) y operaciones ( *Ops* ) para automatizar la cadena de entrega continua.

#### 4\. Modelado de Sistemas

El modelado de sistemas representa la estructura, el comportamiento y el contexto de una aplicación a diferentes niveles de abstracción.

##### Ian Sommerville: Perspectivas de Modelado UML

Sommerville organiza el modelado de sistemas según cuatro perspectivas clave:

1. **Modelos de Contexto:**  Muestran los límites del sistema y su relación con otras entidades del entorno.  
2. **Modelos de Interacción:**  Describen la comunicación entre los usuarios y el sistema (Diagramas de Casos de Uso) o entre los componentes internos (Diagramas de Secuencia y Comunicación).  
3. **Modelos Estructurales:**  Muestran la organización estática del sistema y las relaciones entre sus componentes (Diagramas de Clases y Paquetes).  
4. **Modelos de Comportamiento:**  Describen la respuesta dinámica del sistema ante eventos internos o externos (Diagramas de Estado y Diagramas de Actividad).

##### Kenneth E. Kendall & Julie E. Kendall: Análisis Estructurado y Orientado a Objetos

* **Análisis Estructurado (DFD):**  
* *Diagrama de Flujo de Datos a Nivel de Contexto:*  Representa el sistema completo como un único proceso central delimitado por sus entidades externas y los flujos de datos de entrada/salida.  
* *Diagrama Nivel 0 y Diagramas Hijo:*  Explotación descendente ( *top-down* ) que desglosa el sistema en subprocesos, almacenes de datos y flujos detallados.  
* *Diccionario de Datos:*  Catálogo centralizado que define de forma unívoca la composición de cada flujo y almacén de datos.  
* **Análisis Orientado a Objetos (UML):**  
* Definición de clases a partir de sustantivos en escenarios, estableciendo atributos, métodos y relaciones (asociación, agregación, composición y herencia gen/spec).

#### 5\. Diseño Arquitectónico y Selección de la Arquitectura

El diseño arquitectónico representa la estructura de alto nivel del software, los componentes que la integran, sus propiedades observables y las relaciones entre ellos.

##### Estándar ISO/IEC/IEEE 42010:2022 (Arquitectura de Software)

El estándar establece la ontología formal para la  **Descripción Arquitectónica (AD)**  de una Entidad de Interés ( *Entity of Interest \- EoI* ):

* **Stakeholders:**  Partes interesadas que influyen, controlan o son impactadas por la entidad.  
* **Concerns (Preocupaciones):**  Asuntos de importancia clave para las partes interesadas (ej. rendimiento, auditabilidad, modificabilidad, costo, seguridad).  
* **Viewpoints (Puntos de Vista):**  Patrones o convenciones que establecen las reglas para construir una vista que aborde un conjunto de preocupaciones.  
* **Views (Vistas):**  Representaciones tangibles de la arquitectura completa o parcial construidas para responder a las preocupaciones de un grupo específico de partes interesadas.

##### Ian Sommerville: Patrones Arquitectónicos

Sommerville define patrones arquitectónicos como soluciones probadas a problemas recurrentes de diseño de infraestructura:

* **Arquitectura en Capas (**  ***Layered Architecture***  **):**  Organiza el sistema en capas independientes (presentación, lógica de negocio, acceso a datos), promoviendo la modificabilidad y el aislamiento de cambios.  
* **Cliente-Servidor:**  Distribuye el procesamiento entre proveedores de servicios (servidores) y solicitantes (clientes).  
* **Modelo-Vista-Controlador (MVC):**  Desacopla los datos de la aplicación ( *Modelo* ), la interfaz gráfica ( *Vista* ) y la lógica de control de usuario ( *Controlador* ).  
* **Arquitectura Basada en Eventos / Servicios:**  Permite la comunicación asíncrona mediante mensajes, garantizando bajo acoplamiento y alta escalabilidad.

##### Roger S. Pressman & Bruce R. Maxim: Evaluación Arquitectónica

Pressman & Maxim enfatizan que la selección arquitectónica debe evaluarse frente a los requerimientos no funcionales mediante revisiones técnicas formales como la  **Revisión Arquitectónica Basada en Patrones (PBAR)**  o el método  **ATAM (Architectural Tradeoff Analysis Method)** .

#### 6\. Análisis Sistémico: Entradas, Procesos, Salidas y Retroalimentación

Basado en los fundamentos de la  **Teoría General de Sistemas (TGS)**  recopilados por  **Kendall & Kendall** , una organización o software se comprende como un sistema abierto delimitado por sus fronteras organizacionales.

* **Entradas (**  ***Inputs***  **):**  Datos, materias primas, transacciones o recursos que cruzan el límite del sistema provenientes del entorno externo.  
* **Procesos (**  ***Processes***  **):**  Funciones o algoritmos internos que transforman, calculan, verifican o actualizan las entradas.  
* **Salidas (**  ***Outputs***  **):**  Información, productos o servicios terminados expedidos de regreso hacia el entorno externo.  
* **Retroalimentación (**  ***Feedback***  **):**  Mecanismo de control y autorregulación del sistema. Compara las salidas producidas con los objetivos predeterminados para ajustar continuamente las entradas o los procesos.  
* **Bucles de Retroalimentación Balanceadores:**  En la dinámica de sistemas, son ciclos estabilizadores que detectan desviaciones y aplican correcciones automáticamente para mantener el equilibrio financiero y operacional del sistema.

#### 7\. Ciclo de Vida del Software (SDLC)

El ciclo de vida abarca el marco de trabajo completo desde la concepción inicial hasta el retiro del sistema.

##### Kenneth E. Kendall & Julie E. Kendall: Las 7 Fases del SDLC

1. **Identificación de Problemas, Oportunidades y Objetivos:**  Reconocimiento inicial de las fallas del negocio o posibilidades de mejora.  
2. **Determinación de los Requerimientos de Información:**  Recolección de datos sobre la operación mediante entrevistas, muestreo e inspección.  
3. **Análisis de las Necesidades del Sistema:**  Modelado de los flujos de datos, diseño del diccionario de datos y preparación de la propuesta de sistemas.  
4. **Diseño del Sistema Recomendado:**  Diseño de la interfaz de usuario, bases de datos, salidas, entradas y controles del sistema.  
5. **Desarrollo y Documentación del Software:**  Codificación de los módulos, redacción de manuales e instructivos de usuario.  
6. **Prueba y Mantenimiento del Sistema:**  Verificación técnica y corrección de errores antes y durante la producción.  
7. **Implementación y Evaluación del Sistema:**  Instalación del software, capacitación de personal y auditoría posterior a la entrega.

##### Pressman & Maxim: Actividades Estructurales Genéricas

Pressman reduce el ciclo de vida a cinco actividades genéricas del marco de trabajo:  **Comunicación, Planeación, Modelado, Construcción y Despliegue** , las cuales pueden ejecutarse en flujos de proceso lineales, iterativos, evolutivos o paralelos.

#### 8\. Definición del Proyecto: Problemas, Necesidades, Stakeholders, Visión y Alcance

Para iniciar un proyecto con éxito se debe estructurar la fase de concepción mediante la definición precisa de sus elementos constitutivos.

* **Identificación de Problemas y Necesidades (Kendall):**  Los problemas se identifican observando síntomas como errores en salidas, comportamientos disfuncionales en empleados o quejas en la retroalimentación externa de clientes y proveedores.  
* **Stakeholders / Partes Interesadas (ISO 42010):**  Personas, grupos u organizaciones que tienen un interés directo o indirecto en el sistema, ejerciendo control o siendo impactados por él. Sus intereses se traducen en preocupaciones ( *Concerns* ).  
* **Visión y Alcance del Proyecto (Pressman):**  La  *Visión*  establece la meta estratégica a largo plazo que el software debe cumplir, mientras que el  *Alcance*  delimita expresamente las funciones, módulos y fronteras operativas que el proyecto construirá (así como aquello que queda excluido).

#### 9\. Estudio de Viabilidad (Técnica, Económica y Operacional)

El estudio de viabilidad es una recopilación inicial de datos que permite a la alta gerencia decidir si debe invertirse dinero y tiempo en un proyecto de sistemas completo.

##### Kenneth E. Kendall & Julie E. Kendall: Los Tres Pilares de Viabilidad

* **Viabilidad Técnica:**  
* Evalúa si los recursos tecnológicos actuales de la organización son suficientes o si la tecnología necesaria existe en el mercado.  
* Analiza si el equipo de desarrollo posee las habilidades técnicas requeridas o si se requiere contratación/subcontratación.  
* **Viabilidad Económica:**  
* Compara los costos de desarrollo, adquisición de hardware/software y operación contra los beneficios tangibles e intangibles esperados.  
* **Técnicas de Evaluación Financiera:**  
* *Análisis de Punto de Equilibrio (*  *Break-even*  *):*  Determina el momento en que los costos acumulados del sistema propuesto igualan a los del sistema actual.  
* *Periodo de Retribución (*  *Payback*  *):*  Mide el tiempo necesario para recuperar la inversión inicial mediante los beneficios netos.  
* *Análisis del Valor Presente Neto (VPN):*  Evalúa la rentabilidad descontando los flujos de efectivo futuros según una tasa de interés o costo de capital.  
* **Viabilidad Operacional:**  
* Pronostica si el sistema será aceptado y utilizado efectivamente por los usuarios una vez instalado.  
* Evalúa la resistencia humana al cambio, el compromiso de los usuarios y la compatibilidad con la cultura organizacional.

