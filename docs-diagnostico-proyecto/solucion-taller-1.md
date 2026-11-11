Análisis preliminar del proyecto [[Proyecto a resolver]]
# Solución Desarrollada — Taller 1: Ingeniería de Software
**Proyecto:** Plataforma de Administración de Centros Comerciales (Problema #42)  
**Marco Metodológico:** Teoría General de Sistemas (TGS), Kendall & Kendall, Pressman & Maxim, Ian Sommerville, e ISO/IEC/IEEE 42010-2022.

---

## Punto 1. Análisis Sistémico del Proyecto (Problema #42)

Fundamentado en los principios de la **Teoría General de Sistemas (TGS)**, el proyecto se concibe como un sistema abierto en constante interacción con su entorno inmobiliario y comercial. Para su representación detallada se emplean las herramientas de análisis estructurado de **Kendall & Kendall**.

```text
               ┌────────────────────────────────────────────────────────┐
               │                        ENTRADAS                        │
               │  • Datos contractuales (VMA, %, caps, m²)              │
               │  • Cierres Z diarios y transacciones POS               │
               │  • Gastos comunes y flujo peatonal                     │
               │  • Informes de auditoría de campo                      │
               └───────────────────┬────────────────────────────────────┘
                                   │
                                   ▼
               ┌────────────────────────────────────────────────────────┐
               │                        PROCESOS                        │
               │  • Facturación Dual: MAX(VMA, Ventas × %)              │
               │  • Algoritmo de Detección Estadística (Z-Score)        │
               │  • Prorrateo Iterativo de Expensas con Topes (Caps)     │
               │  • Gestión de Cobranzas e Intereses                    │
               └───────────────────┬────────────────────────────────────┘
                                   │
                                   ▼
               ┌────────────────────────────────────────────────────────┐
               │                        SALIDAS                         │
               │  • Liquidaciones mensuales por local                   │
               │  • Órdenes de auditoría y sanciones                    │
               │  • Reportes de ocupación y Tenant Mix                  │
               └───────────────────┬────────────────────────────────────┘
                                   │
                                   ▼
               ┌────────────────────────────────────────────────────────┐
               │         RETROALIMENTACIÓN (BUCLE BALANCEADOR)          │
               │  • Corrección de omisiones y ajustes de sospechas      │
               │  • Conciliación anual de expensas (True-Up)            │
               │  • Estabilización de la recaudación e historial moroso │
               └────────────────────────────────────────────────────────┘
```

### Componentes Sistémicos

* **Entradas:**
  * **Contractuales:** Coeficiente por m², plazo de locación, **Valor Mínimo Mensual Asegurado (VMA)**, porcentaje de renta variable por rubro, topes de expensas (*caps*) de tiendas ancla y periodos de gracia.
  * **Ventas:** Cierres Z fiscales diarios, datos de procesamiento POS y ventas omnicanal (*click & collect*).
  * **Operativas:** Facturas de gastos comunes (limpieza, seguridad, energía), lecturas de sensores de flujo peatonal e índices de ajuste por inflación.
  * **Auditoría:** Reportes presenciales de compras misteriosas y controles de punto fijo.

* **Procesos:**
  * **Motor de Facturación Dual:** Evaluación mensual del canon de arrendamiento determinando `MAX(VMA, Ventas Brutas Auditadas × %)`.
  * **Algoritmo de Detección de Anomalías (Sospecha):** Evaluación mediante *Z-Score robusto* o *Isolation Forest* que cruza ventas/m² contra flujo peatonal y rubro comercial para identificar subdeclaración de ingresos.
  * **Algoritmo Iterativo de Prorrateo de Expensas:** Reparto ponderado de gastos comunes con ciclo de convergencia para redistribuir entre los locales menores el exceso no cubierto por los topes (*caps*) de las tiendas ancla.
  * **Gestión Operativa:** Emisión de permisos de remodelación nocturna, administración del fondo de promoción y liquidación de intereses punitorios por mora.

* **Salidas:**
  * Liquidaciones mensuales consolidadas por local (alquiler base/variable, expensas, marketing y punitorios).
  * Órdenes de inspección de campo y notificaciones automáticas de multas contractuales.
  * Planos interactivos de ocupación (*Tenant Mix*), reportes de vacancia y resúmenes de recaudo publicitario.

* **Retroalimentación (Bucle de Retroalimentación Balanceador):**
  En términos de la Dinámica de Sistemas (Forrester/Meadows), la retroalimentación opera como un **bucle balanceador o estabilizador**: las auditorías de campo y la conciliación anual (*true-up*) detectan desviaciones (ventas omitidas o desfases de gastos), aplicando correcciones que contrarrestan la fuga de ingresos y estabilizan el equilibrio financiero de la organización inmobiliaria.

---

## Punto 4. Ciclo de Vida del Software para el Proyecto

Basado en el marco metodológico de **Pressman & Maxim** y **Sommerville** para la selección del modelo de proceso, se evalúa y fundamenta la estrategia de desarrollo.

### Justificación del Modelo de Proceso (Incremental / Scrum vs. Cascada)
Un modelo tradicional en cascada exige requerimientos estables y completamente definidos desde el inicio. **Se adopta un modelo de proceso incremental, materializado operativamente mediante el marco ágil Scrum**; esta elección responde a que los requisitos del motor de liquidación y del algoritmo de sospecha son propensos a evolucionar a medida que se descubren patrones reales de ventas y excepciones contractuales en el centro comercial, algo que un modelo cascada no permitiría adaptar.

### 4.1. Identificación del Problema
Pérdida de ingresos inmobiliarios por subdeclaración de ventas en esquemas de renta variable y complejidad matemática/legal en el prorrateo manual de expensas cuando existen topes contractuales (*caps*) en tiendas ancla.

### 4.2. Necesidad
Desarrollar una plataforma centralizada que automatice la ingestión de ventas, ejecute analítica avanzada de sospechas y calcule la facturación dual y el prorrateo de expensas con total auditabilidad contable.

### 4.3. Stakeholders (Identificados bajo la ontología ISO/IEC/IEEE 42010)
* **Operadora / Gerencia General:** Interesada en la rentabilidad global del inmueble.
* **Departamento Comercial / Leasing:** Enfocado en el plano de distribución, ocupación y condiciones contractuales (**Modificabilidad**).
* **Administración y Finanzas:** Exigencia de exactitud contable e integridad en el cobro (**Auditabilidad Inmutable y Consistencia Transaccional**).
* **Auditores de Campo y Operaciones:** Exigencia de alertas en tiempo real y alta disponibilidad en dispositivos móviles (**Rendimiento, Alta Disponibilidad y Alertas en Tiempo Real**, y **Trazabilidad de Inspecciones**).
* **Locatarios (Tiendas Ancla y Comercios Menores):** Exigencia de transparencia en el reparto de cargas y renta variable.

### 4.4. Usuarios Directos e Indirectos
* **Directos:** Analistas de leasing, contadores de liquidación, administradores de finanzas y auditores de campo.
* **Indirectos:** Encargados de tienda (ingreso de Cierres Z) y Junta Directiva del Fondo Inmobiliario.

### 4.5. Visión del Proyecto
Ser la solución tecnológica estándar que garantice la máxima recaudación por renta variable, erradique la omisión de ingresos y automatice la facturación inmobiliaria compleja con total transparencia legal.

### 4.6. Alcance del Proyecto
Desarrollo de los 4 subsistemas (Tenant Mix & Leasing, Control de Ventas/Auditoría, Motor de Liquidación/Expensas y Gestión Operativa/Cobranzas). *Se excluye la integración física con hardware POS, priorizando interfaces de archivo estándar (XML/CSV).*

### 4.7. Estudio de Viabilidad
* **Técnica:** Viable mediante arquitectura Web de 3 capas con motor relacional (PostgreSQL) para consistencia ACID en transacciones financieras y módulos analíticos en Python/Pandas.
* **Operativa:** Altamente viable al sustituir hojas de cálculo propensas a errores por un flujo automatizado de trabajo.
* **Económica:** ROI ampliamente justificado por la recuperación de ventas no declaradas y la eliminación de disputas legales por expensas.

### 4.8. Fases del Ciclo de Vida (SDLC) y su materialización por incrementos

Las **7 fases del SDLC de Kendall & Kendall** se usan como checklist de madurez y se articulan con las **5 actividades genéricas de Pressman** (comunicación, planeación, modelado, construcción, despliegue), que se repiten en cada sprint:

| Fase (Kendall & Kendall) | Actividad (Pressman) | Artefacto / entregable en este proyecto |
| :--- | :--- | :--- |
| 1. Identificación de problemas, oportunidades y objetivos | Comunicación | Definición del problema, necesidad y visión (4.1, 4.2, 4.5) |
| 2. Determinación de los requerimientos de información | Comunicación / Elicitación | Elicitación documental, glosario, decisiones D-01..D-10 y riesgos R-01..R-05 |
| 3. Análisis de las necesidades del sistema | Modelado | Modelos de interacción UML, reglas RN-01..RN-16 y matriz de trazabilidad (sección 5.6) |
| 4. Diseño del sistema recomendado | Modelado / Diseño | Arquitectura (Punto 6), modelo de datos y endpoints |
| 5. Desarrollo y documentación del software | Construcción | Incrementos Scrum, código y documentación técnica |
| 6. Prueba y mantenimiento del sistema | Construcción / Despliegue | Casos de prueba por regla RN, validación (5.e) y correcciones |
| 7. Implementación y evaluación del sistema | Despliegue | Despliegue, capacitación, piloto y auditoría post-entrega |

El ciclo **no** se ejecuta en cascada: se recorre completo dentro de cada incremento Scrum. Secuencia propuesta de incrementos: **I1** Contratos + canon dual (RN-01..RN-03, RN-09); **I2** Auditoría y anomalías (RN-04..RN-06); **I3** Prorrateo y caps (RN-07..RN-08); **I4** Cobranza, garantías y fondo (RN-10..RN-12). Las reglas transversales (RN-13..RN-16) se incorporan desde I1 por su carácter estructural.

---

## Punto 5. Fases de la Ingeniería de Requisitos

Estructurado bajo las **7 actividades del marco de Ingeniería de Requisitos de Pressman & Maxim**, integrando la recolección estructurada de **Kendall & Kendall** y el modelado de interacción de **Sommerville**:

```text
  [Concepción] ─── (Abordada previamente en el Punto 4: Problema y Necesidad)
       │
       ▼
 [Elicitación]  ◄─── (Análisis documental del Problema #42 + JAD Simulado)
       │
       ▼
 [Elaboración]  ◄─── (Sommerville: Casos de Uso y Modelación de Reglas D-01 a D-10)
       │
       ▼
 [Negociación]  ◄─── (Pressman: Balance de conflictos entre Stakeholders)
       │
       ▼
[Especificación]◄─── (Requisitos Funcionales, No Funcionales y Audit Trail)
       │
       ▼
  [Validación]  ◄─── (Listas de chequeo y Matriz de Trazabilidad)
       │
       ▼
   [Gestión]    ◄─── (Control de versiones y adendas contractuales)
```

*(Nota de alcance metodológico: La fase inicial de **Concepción / Inception** del marco de Pressman & Maxim quedó establecida en el **Punto 4** mediante la identificación del problema, la necesidad, la visión y el alcance del proyecto. A continuación se desarrollan detalladamente las actividades **a-f** requeridas en el taller).*

* **5.a. Elicitación (Indagación):**
  Dado que el trabajo se desarrolla en un contexto académico sin acceso a stakeholders reales en vivo, la elicitación se fundamenta en el **análisis documental** del PDF del Problema #42 y en la **simulación de talleres JAD (Joint Application Development)** construida a partir del análisis de las decisiones de negocio D-01 a D-10.
* **5.b. Elaboración:**
  Transformación de las necesidades en modelos de interacción UML y escenarios de uso. En esta etapa se modelan formalmente las decisiones de negocio (D-01 a D-10), definiendo la lógica matemática de `MAX(VMA, Ventas × %)` y la convergencia del prorrateo iterativo.
* **5.c. Negociación:**
  Resolución de conflictos entre partes interesadas; por ejemplo, conciliar la postura rigurosa de los auditores (sanciones inmediatas) con la flexibilidad comercial requerida por el área de leasing para preservar relaciones con marcas estratégicas.
* **5.d. Especificación:**
  Documentación formal de requisitos funcionales y no funcionales (precisión decimal contable de 2 a 4 dígitos y registro inmutable *Audit Trail* para validez jurídica).
* **5.e. Validación:**
  Revisión técnica mediante listas de comprobación y matriz de trazabilidad para verificar que las fórmulas no presenten ambigüedades.
* **5.f. Administración de Requisitos:**
  Se gestiona el ciclo de vida de cada requisito mediante los siguientes mecanismos:
  - **Trazabilidad:** cada requisito se identifica (`D-01..D-10`, `RN-01..RN-16`, `R-01..R-05`) y se vincula a su fuente, a su regla de negocio y a su prueba, usando la matriz de trazabilidad de la sección 5.6 de [[Desglose del problema]].
  - **Control de cambios:** toda adenda contractual o reforma fiscal se registra como solicitud de cambio; se evalúa su impacto sobre las reglas afectadas y se aprueba antes de modificar el backlog.
  - **Versionado:** los requisitos y los contratos se versionan con vigencia; un cambio no sobrescribe la versión anterior, habilitando recálculos retroactivos correctos (RN-15).
  - **Estados del requisito:** `propuesto → aprobado → en desarrollo → validado → obsoleto`, visibles en el Product Backlog.
  - **Análisis de impacto:** cada cambio se traza a las reglas, pantallas, endpoints y pruebas afectadas antes de implementarse.
  - **Registro y evidencia:** el Product Backlog y la matriz de trazabilidad son el registro maestro; el historial de cambios se conserva en el audit trail (RN-14).

---

## Punto 6. Arquitectura del Proyecto

Para estructurar la arquitectura se aplica el marco del **Estándar ISO/IEC/IEEE 42010-2022** para mapear **Stakeholders y Preocupaciones (*Concerns*) hacia Vistas Arquitectónicas y Atributos de Calidad**, mientras que la estructuración técnica se define mediante los **Patrones Arquitectónicos de Sommerville**.

### 1. Mapeo de Stakeholders, Preocupaciones y Atributos de Calidad (ISO 42010)
* **Administración y Finanzas:** Preocupadas por la **Auditabilidad Inmutable y Consistencia Transaccional** (evitar registros alterados o liquidaciones erróneas).
* **Auditores de Campo y Operaciones:** Preocupados por el **Rendimiento, Alta Disponibilidad y Alertas en Tiempo Real** (respuesta inmediata en dispositivos móviles durante inspecciones y sin degradación durante el cierre mensual) y por la **Trazabilidad de Inspecciones**.
* **Equipo de Leasing y Mantenimiento:** Preocupados por la **Modificabilidad** (capacidad de adaptar clausulados, esquemas de VMA o porcentajes por rubro sin rehacer el sistema).

### 2. Decisiones Arquitectónicas Justificadas por Atributos de Calidad
* **Arquitectura en Capas / Layered Architecture (Satisface Modificabilidad - Leasing):** La separación estricta entre presentación, lógica de negocio y datos permite que las reglas de prorrateo o el cálculo de VMA cambien en la capa de negocio sin afectar la interfaz del usuario ni la estructura de datos. (se complementa con la arquitectura cliente-servidor)

Una arquitectura Web/Móvil de 3 capas es una evolución directa del patrón Cliente-Servidor (Kendall & Kendall / Sommerville).
	- Los **Clientes** son los navegadores web de los administradores y la App Móvil de los auditores de campo.
	- Los **Servidores** son el motor backend de aplicación y la base de datos relacional (PostgreSQL).
	- No hay contradicción: _Cliente-Servidor_ describe la distribución física en la red, mientras que _Capas_ describe la organización lógica del código.
* **Procesamiento Asíncrono / Servicios Batch Desacoplados (Satisface Rendimiento, Alta Disponibilidad y Alertas en Tiempo Real - Auditores y Operaciones):** Aísla el Motor de Liquidación y el Algoritmo de Detección de Sospechas en servicios de segundo plano, evitando bloquear el rendimiento de las pantallas web y de la App Móvil durante los picos de procesamiento del cierre mensual.
* **Persistencia Relacional ACID y Audit Trail Inmutable (Satisface Auditabilidad Inmutable y Consistencia Transaccional - Finanzas, y Trazabilidad de Inspecciones - Auditores):** Uso de PostgreSQL para asegurar consistencia estricta en montos cobrados, complementado con un log de auditoría apendizado (*write-only*) que garantiza la validez jurídica de los registros financieros ante revisiones contables y la trazabilidad inalterable de los comprobantes y multas aplicadas por los auditores.

### 3. Diagrama de Arquitectura del Sistema

```text
┌────────────────────────────────────────────────────────────────────────┐
│                   CAPA DE PRESENTACIÓN (FRONTEND)                      │
│   • Dashboard Web Administrativo (Leasing/Finanzas)                    │
│   • App Móvil de Auditores de Campo (Punto Fijo / Mistery Shopper)     │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ HTTP / REST APIs
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│               CAPA DE LÓGICA DE NEGOCIO (BACKEND SERVICES)             │
│  ┌──────────────────────┐  ┌────────────────────────────────────────┐  │
│  │ Servicio de Leasing  │  │ Servicio de Auditoría y Detección      │  │
│  └──────────────────────┘  └────────────────────────────────────────┘  │
│  ┌──────────────────────┐  ┌────────────────────────────────────────┐  │
│  │ Motor de Liquidación │  │ Servicio de Cobranzas y Operaciones    │  │
│  └──────────────────────┘  └────────────────────────────────────────┘  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ SQL / ACID Transactions
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                    CAPA DE PERSISTENCIA Y DATOS                        │
│   • Base de Datos Relacional (PostgreSQL - Tablas Contractuales/Ventas)│
│   • Audit Trail Inmutable (Log de Auditoría de Solo Lectura)           │
└────────────────────────────────────────────────────────────────────────┘
```
