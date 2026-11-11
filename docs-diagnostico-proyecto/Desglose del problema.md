Intenta explicar el proyecyo #42: [[Proyecto a resolver]].
# Problema #42: Plataforma de Administración de Centros Comerciales (Shopping Malls), Renta Variable por Ventas y Gastos Comunes Ponderados

## Anexo A — Guía de Lectura de las Secciones 1 y 2

> **Propósito de este anexo:** traducir la jerga inmobiliaria de las secciones 1 y 2 a lenguaje llano, y explicitar el flujo completo que el texto da por sabido. **No agrega funcionalidades nuevas**: solo interpreta lo que ya está escrito. Útil para que todo el equipo parta de la misma comprensión antes de completar el Glosario (sección 3) y las Decisiones (sección 4).

### A.1 La idea central en una frase

> **Es un sistema para calcular cuánto dinero debe pagar cada local de un shopping a fin de mes, y para vigilar que los locales no mientan sobre cuánto vendieron.**

Los cuatro subsistemas son cuatro partes de ese mismo problema.

### A.2 Analogía: el shopping como un edificio de apartamentos con reglas raras

Imaginá un edificio de apartamentos donde:

- Cada departamento es un **local** (una tienda, un cine, un restaurante).
- El dueño del edificio es la **operadora del shopping**.
- Cada inquilino firma un **contrato de alquiler**, pero con una regla extraña: **no paga un alquiler fijo, sino una mezcla**.
- Además del alquiler, todos comparten gastos del edificio (limpieza, seguridad, aire acondicionado), pero **no en partes iguales**: el que más consume o el que está en mejor ubicación paga más.
- Y como el dueño sospecha que algunos inquilinos le mienten sobre cuánto ganan, tiene **inspectores** que van a espiarlos.

Ese es el problema. Ahora veamos cada parte.

### A.3 Sección 1 — Descripción general

#### A.3.1 El esquema híbrido de alquiler

El texto dice: *"no pagan un alquiler fijo simple, sino un esquema híbrido compuesto por un Valor Mínimo Mensual Asegurado (VMA) más un porcentaje variable sobre sus ventas"*.

**Traducción:** el local no paga $1000 fijos por mes. Paga así:

- **VMA (Valor Mínimo Mensual Asegurado):** un piso. Aunque venda cero, paga al menos eso. Es la seguridad del dueño.
- **Porcentaje variable:** si al local le va bien y vende mucho, además del VMA paga un % de esas ventas. Es la parte donde el dueño se beneficia del éxito del inquilino.

Ejemplo concreto:

| Local | VMA | % variable | Ventas del mes | ¿Qué paga? |
| :--- | :--- | :--- | :--- | :--- |
| Joyería | $1.000 | 9% | $20.000 | VMA ($1.000) + 9% de $20.000 ($1.800) = **$2.800** |
| Electrónica | $1.000 | 4% | $20.000 | VMA ($1.000) + 4% de $20.000 ($800) = **$1.800** |

La joyería paga más porque su rubro tiene márgenes altos y el dueño del shopping quiere capturar más de esa ganancia. Por eso el texto dice *"porcentajes de renta variable diferenciados por rubro"*.

#### A.3.2 Fondos de promoción y expensas

El texto dice: *"además de fondos de promoción y expensas prorrateadas por coeficientes compuestos"*.

**Traducción:** además del alquiler, el local paga dos cosas más:

- **Fondo de promoción:** una cuota para que el shopping haga publicidad y eventos (Navidad, liquidaciones, etc.). Es plata que todos ponen para atraer más gente al shopping.
- **Expensas:** los gastos de mantener el edificio funcionando (limpieza, seguridad, aire acondicionado). Se reparten **"prorrateadas por coeficientes compuestos"**, que significa: no en partes iguales, sino según reglas (metros cuadrados, ubicación, cuánto consume).

### A.4 Sección 1.1 — Primer subsistema: Locales y Contratos

El texto dice: *"el área comercial gestiona el plano interactivo de locales (Tenant Mix y Leasing) y la estructuración de contratos de locación"*.

**Traducción:** esta parte es el **"administrador de contratos"**. Antes de que el sistema pueda calcular nada, alguien tiene que cargar:

- Qué locales existen (el "plano" del shopping).
- Quién alquila cada uno.
- Bajo qué condiciones (VMA, %, fechas, etc.).

El texto menciona tres cosas específicas del contrato:

- **Llave de ingreso:** cuando un local nuevo entra al shopping, paga una suma de entrada (como la "llave" de un alquiler). Puede pagarla en cuotas.
- **Período de gracia:** si el local va a hacer obras de remodelación, el shopping le perdona el alquiler unos meses mientras no puede vender.
- **Escalonamiento del VMA:** el VMA no es fijo para siempre. Cada año sube según la inflación o el tipo de cambio. El sistema tiene que saber aplicar ese ajuste.

Y sobre el porcentaje: *"porcentajes de renta variable diferenciados por rubro o escalas de facturación mensual"*.

**Traducción:** el % no es el mismo para todos. La joyería paga 9%, la electrónica 4%. Y además puede haber **escalas**: si vendés poco, pagás 4%; si vendés mucho, pagás 5% sobre el excedente.

**En resumen:** este subsistema es el "ABM de contratos" (alta, baja, modificación). Sin esto cargado, nada más funciona.

### A.5 Sección 1.2 — Segundo subsistema: Auditoría de Ventas

El texto dice: *"los comercios reportan sus cierres diarios de caja (cierres Z fiscales y liquidaciones de tarjetas de crédito/débito)"*.

**Traducción:** para calcular el % variable, el sistema necesita saber **cuánto vendió cada local**. Esa información la reporta el propio local, todos los días, de dos formas:

- **Cierre Z:** el resumen que emite la caja registradora al cerrar el día (es un documento fiscal).
- **Liquidación de tarjetas:** el resumen de cuánto cobró con tarjeta.

Es decir: **el local declara sus ventas**. El sistema las recibe y las guarda.

El texto dice: *"simultáneamente, los auditores de campo... realizan 'puntos fijos y compras misteriosas' en locales seleccionados por algoritmo de sospecha"*.

**Traducción:** como el dueño del shopping sabe que el local podría **mentir** (declarar menos ventas para pagar menos %), tiene inspectores que van al local a controlar:

- **Punto fijo:** el inspector va, se queda un rato, cuenta cuánta gente entra y sale, estima ventas.
- **Compra misteriosa:** el inspector compra algo como cliente normal y verifica que la venta se registre. Si compra y no le dan factura, o la venta no aparece declarada, hay fraude.

El texto dice: *"en locales seleccionados por algoritmo de sospecha (cuando las ventas por metro cuadrado de un local caen anormalmente respecto al promedio de su mismo rubro o respecto al conteo de flujo peatonal del pasillo)"*.

**Traducción:** no se auditan todos los locales (sería carísimo). Se auditan los **sospechosos**. ¿Cómo se detecta un sospechoso? Comparando:

- **Contra su rubro:** si todas las joyerías del shopping venden $X por m², y una joyería vende mucho menos, es sospechosa.
- **Contra el flujo peatonal:** si por el pasillo de ese local pasa mucha gente, pero el local vende poco, es sospechoso.

Ahí entra el **"algoritmo de sospecha"**: una fórmula estadística que marca locales como "revisar".

El texto dice: *"aplicando multas contractuales severas si detectan ventas omitidas sin facturar"*.

**Traducción:** si el inspector descubre que el local no declaró ventas, se le aplica una **multa**.

**En resumen:** este subsistema es el "control de ventas": recibir las declaraciones diarias + detectar sospechosos + registrar auditorías y multas.

### A.6 Sección 1.3 — Tercer subsistema: Liquidación y Expensas

Este es el **corazón del sistema**. Todo lo anterior alimenta esto.

El texto dice: *"el motor de liquidación mensual calcula para cada local si en ese mes debe pagar solo el VMA o el VMA más el excedente porcentual sobre sus ventas netas de impuestos"*.

**Traducción:** a fin de mes, el sistema calcula para cada local:

- ¿Vendió poco? → Paga solo el VMA.
- ¿Vendió mucho? → Paga el VMA **más** el % sobre el excedente.

Es la fórmula que ya vimos en el ejemplo de la joyería y la electrónica.

El texto dice: *"ejecuta el complejo prorrateo de Gastos Comunes Ordinarios y Extraordinarios (seguridad, climatización central, limpieza, seguros): pondera los metros cuadrados de cada local por coeficientes correctores según su ubicación (planta baja vs. tercer nivel), consumo energético"*.

**Traducción:** repartir los gastos del edificio entre todos los locales, pero **no en partes iguales**. Se usa una fórmula que combina:

- **Metros cuadrados:** local más grande, paga más.
- **Ubicación:** planta baja (mejor ubicación, más tráfico) paga más que tercer nivel.
- **Consumo energético:** un restaurante que usa mucho aire acondicionado paga más que una joyería.

Ese "coeficiente corrector" es un número que ajusta el reparto.

El texto dice: *"y si es 'tienda ancla' con tope contractual de expensas (cuyo diferencial no cubierto debe redistribuirse proporcionalmente entre el resto de los locales menores)"*.

**Traducción:** esto es lo más complejo. Hay un tipo especial de local llamado **"tienda ancla"** (un supermercado, un cine, una tienda departamental grande). Las anclas son las que **atraen gente al shopping**, y por eso tienen poder de negociación. En su contrato, logran un **tope (cap)** de expensas: "yo pago como máximo $5.000 de expensas, aunque me correspondan $8.000".

**El problema:** esos $3.000 de diferencia no desaparecen. Alguien tiene que pagarlos. El sistema debe **redistribuirlos entre los locales menores**, proporcionalmente. Pero al redistribuir, puede que otro local también supere su tope, y hay que volver a redistribuir... y así hasta que converja. Eso es el **"algoritmo iterativo"** que menciona el documento.

**En resumen:** este subsistema es el "calculador de la factura mensual": alquiler + expensas + redistribución de caps.

### A.7 Sección 1.4 — Cuarto subsistema: Obras, Marketing y Cobranza

El texto dice: *"administra los permisos de obra nocturna para remodelación de vidrieras"*.

**Traducción:** si un local quiere hacer obras (romper paredes, cambiar vidrieras), necesita pedir permiso al shopping. Generalmente se hacen de noche para no molestar a los clientes. El sistema gestiona esas solicitudes.

El texto dice: *"el fondo colectivo de marketing para campañas navideñas"*.

**Traducción:** administrar la plata que todos los locales ponen para publicidad. ¿Cuánto se recaudó? ¿En qué se gastó? ¿Cómo se rinde cuentas?

El texto dice: *"y la gestión de cobranza, intereses punitorios y garantías de caución"*.

**Traducción:** qué pasa cuando un local **no paga**:

- **Cobranza:** el proceso de reclamar la deuda.
- **Intereses punitorios:** un recargo por pagar tarde.
- **Garantías de caución:** el local dejó un seguro o una póliza como respaldo. Si no paga, se ejecuta la garantía.

**En resumen:** este subsistema es el "administrativo": permisos, marketing y cobranza.

### A.8 Sección 2 — El desafío técnico

El texto dice: *"Motor de facturación inmobiliaria dual... con liquidaciones provisorias y ajustes anuales"*.

**Traducción:** el sistema tiene que calcular dos tipos de alquiler (VMA vs. %) y manejar **liquidaciones provisorias** (un cálculo estimado a fin de mes) que después se **ajustan** cuando llegan los datos definitivos (por ejemplo, cuando se publica la inflación o cuando termina la auditoría).

El texto dice: *"algoritmo de prorrateo de expensas con coeficientes ponderados y redistribución iterativa de topes contractuales de tiendas ancla (caps)"*.

**Traducción:** lo que ya explicamos: repartir gastos con coeficientes + redistribuir los topes de las anclas hasta que converja.

El texto dice: *"detección estadística de anomalías en declaraciones de ventas de locatarios"*.

**Traducción:** el "algoritmo de sospecha" del subsistema 2, pero dicho en lenguaje técnico: usar estadística para detectar locales que probablemente mienten.

### A.9 El flujo completo, de principio a fin

Para que se vea cómo encajan los cuatro subsistemas:
```
[Mes 1]  
↓
1. El gestor carga el local y el contrato (VMA, %, caps) ← Subsistema 1  
    ↓
2. Todos los días, el local declara sus ventas (cierre Z) ← Subsistema 2  
    ↓
3. El algoritmo marca locales sospechosos ← Subsistema 2  
4. El auditor va, audita, aplica multa si corresponde ← Subsistema 2  
    ↓
5. A fin de mes, el motor calcula:
    - Alquiler: ¿VMA solo o VMA + %? ← Subsistema 3  
    - Expensas: reparto con coeficientes ← Subsistema 3 
    - Redistribución de caps de anclas ← Subsistema 3
    - Fondo de promoción ← Subsistema 4  
        ↓
6. Se emite la liquidación al local ← Subsistema 3  
    ↓
7. Si el local no paga: cobranza, intereses, garantía ← Subsistema 4
```



## 3. Glosario del Dominio
> Instrucciones para el equipo: cada término debe completarse con definición, fuente y relevancia (qué subsistema lo usa). Un término sin fuente no está investigado, solo mencionado. Los checkboxes indican el estado de la investigación: [x] investigado y citado.

### 3.1 Conceptos base del negocio inmobiliario

- [x] Alquiler fijo simple
  - **Definición:** Modalidad de contratación de arrendamiento en la cual el inquilino paga una suma de dinero predeterminada y constante cada período mensual, independientemente del volumen de ventas o rendimiento comercial que obtenga en el local.
  - **Fuente:** Ros, I. (2022). *Renta Variable Centro Comercial: Guía y Negociación*. Recuperado de [https://www.ignacioros.com/renta-variable-centro-commercial/](https://www.ignacioros.com/renta-variable-centro-commercial/)
  - **Relevancia:** Utilizado como base de ingresos previsibles para la administración del centro comercial; gestionado por el **Subsistema 1 (Locales y Contratos)** y el **Subsistema 3 (Liquidación y Expensas)**.

- [x] Valor Mínimo Mensual Asegurado (VMA)
  - **Definición:** Monto base o piso monetario obligatorio que el locatario se compromete a pagar mensualmente al propietario o centro comercial, el cual funciona como salvaguarda ante bajas ventas y sirve como umbral para el cálculo de rentas variables.
  - **Fuente:** Bellhaven Real Estate. (2024). *Understanding Overage Rent in Retail Lease Agreements*. Recuperado de [https://www.bellhaven.org/learn/Overage-Rent](https://www.bellhaven.org/learn/Overage-Rent)
  - **Relevancia:** Es el componente fijo fundamental de los contratos mixtos en centros comerciales; procesado por el **Subsistema 1** y **Subsistema 3**.

- [x] Renta variable (% sobre ventas brutas declaradas y auditadas)
  - **Definición:** Porcentaje acordado contractualmente sobre las ventas brutas mensuales del locatario que se abona al centro comercial, diseñado para alinear los intereses del propietario con el éxito comercial del locatario.
  - **Fuente:** Asesores VE Global. (2024). *¿Qué ley regula los alquileres de locales comerciales en Venezuela?* Recuperado de [https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/](https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/)
  - **Fórmula de cálculo:**
    ```text
    Renta_Variable = Ventas_Brutas_Auditadas * Porcentaje_Rubro
    ```
  - **Relevancia:** Nuclea la operación del **Subsistema 2 (Auditoría de Ventas)** y su integración con la facturación en el **Subsistema 3**.

- [x] Overage rent (renta complementaria sobre el VMA)
  - **Definición:** Renta adicional que paga el arrendatario cuando sus ventas superan un determinado punto de corte (*breakpoint*), calculándose como un porcentaje del excedente sobre dicho umbral.
  - **Fuente:** Bellhaven Real Estate. (2024). *Understanding Overage Rent in Retail Lease Agreements*. Recuperado de [https://www.bellhaven.org/learn/Overage-Rent](https://www.bellhaven.org/learn/Overage-Rent)
  - **Fórmula de cálculo:**
    ```text
    Overage_Rent = MAX(0, (Ventas_Brutas - Breakpoint) * Porcentaje_Acordado)
    ```
  - **Relevancia:** Representa el incentivo financiero del centro comercial en locaciones de alto rendimiento; clave para el **Subsistema 2** y **Subsistema 3**.

- [x] Fondos de promoción
  - **Definición:** Aportes monetarios periódicos exigidos a los locatarios destinados de forma exclusiva a financiar campañas de marketing institucional, eventos masivos y publicidad colectiva del centro comercial.
  - **Fuente:** Ley de Regulación del Arrendamiento Inmobiliario para el Uso Comercial. Gaceta Oficial N° 40.418 de Venezuela (2014). Recuperado de [https://es.scribd.com/document/554202934/LEY-DE-ARRENDAMIENTOS-Comerciales](https://es.scribd.com/document/554202934/LEY-DE-ARRENDAMIENTOS-Comerciales)
  - **Relevancia:** Administrados de manera segregada por el **Subsistema 4 (Obras, Marketing y Cobranza)**.

- [x] Expensas prorrateadas por coeficientes compuestos
  - **Definición:** Sistema de distribución de los gastos comunes del centro comercial entre los locales, basado en factores ponderados que combinan la superficie en metros cuadrados, la ubicación estratégica (frente, nivel, flujo de tráfico) y la categoría del comercio.
  - **Fuente:** Avarbitraje. (2024). *La regulación del monto de los alquileres comerciales y el arbitraje*. Recuperado de [https://avarbitraje.com/wp-content/uploads/2024/04/ANAVI-Nro4-A6-pp-111-127.pdf](https://avarbitraje.com/wp-content/uploads/2024/04/ANAVI-Nro4-A6-pp-111-127.pdf)
  - **Fórmula de cálculo:**
    ```text
    Expensa_Local = Gasto_Total_Comun * (Coeficiente_Compuesto_Local / Suma_Total_Coeficientes)
    ```
  - **Relevancia:** Núcleo de cálculo automático del **Subsistema 3 (Liquidación y Expensas)**.

- [x] Tienda ancla vs. local menor
  - **Definición:** Las tiendas ancla son grandes superficies comerciales (como departamentales o supermercados) que traccionan tráfico masivo hacia el centro comercial, mientras que los locales menores son comercios de menor tamaño que se benefician de dicho flujo circulatorio.
  - **Fuente:** International Council of Shopping Centers [ICSC]. (2023). *Glossary of Shopping Center Terms*. Recuperado de [https://www.icsc.com](https://www.icsc.com)
  - **Relevancia:** Define la parametrización de condiciones comerciales preferenciales en el **Subsistema 1 (Locales y Contratos)**.

- [x] Tope contractual de expensas (cap)
  - **Definición:** Límite máximo establecido por contrato (ya sea en porcentaje de incremento o monto fijo) que el centro comercial puede trasladar al locatario en concepto de gastos comunes, asumiendo el centro comercial el remanente si los gastos superan dicho tope.
  - **Fuente:** Abog. Luis Marcano. (2016). *Arrendamiento de Locales y Centros Comerciales: gastos y sobrealquileres*. Recuperado de [https://abogluismarcano.wordpress.com/2016/07/31/arrendamiento-de-locales-y-centros-comerciales-gastos-y-sobrealquileres/](https://abogluismarcano.wordpress.com/2016/07/31/arrendamiento-de-locales-y-centros-comerciales-gastos-y-sobrealquileres/)
  - **Relevancia:** Requerido para la lógica de redistribución en el **Subsistema 3 (Liquidación y Expensas)**.

- [x] Coeficiente de reparto
  - **Definición:** Factor matemático o alícuota porcentual asignada a cada local en función de su superficie y ponderadores, que determina su proporción exacta frente al total de los costos comunes del inmueble.
  - **Fuente:** Asesores VE Global. (2024). *¿Qué ley regula los alquileres de locales comerciales en Venezuela?* Recuperado de [https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/](https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/)
  - **Fórmula de cálculo:**
    ```text
    Coeficiente_Reparto = Superficie_Local / Superficie_Total_Locales_Habilitados
    ```
  - **Relevancia:** Variable primaria consumida por el **Subsistema 3**.

- [x] Service charge y true-up (provisión mensual + ajuste anual)
  - **Definición:** Mecanismo financiero donde los locatarios pagan una estimación mensual provisoria por los gastos operativos (service charge), la cual es sometida a una conciliación y regularización anual (*true-up*) contra los gastos reales auditados.
  - **Fuente:** Bellhaven Real Estate. (2024). *Understanding Overage Rent in Retail Lease Agreements*. Recuperado de [https://www.bellhaven.org/learn/Overage-Rent](https://www.bellhaven.org/learn/Overage-Rent)
  - **Fórmula de cálculo:**
    ```text
    Saldo_True_Up = Gasto_Real_Anual_Asignado - Suma_Provisiones_Mensuales_Pagadas
    ```
  - **Relevancia:** Gestionado íntegramente por el **Subsistema 3 (Liquidación y Expensas)**.


### 3.2 Conceptos por subsistema

#### Subsistema 1 — Locales y Contratos
- [x] Plano interactivo de locales (Tenant Mix y Leasing)
  - **Definición:** Representación gráfica digital y georreferenciada de la planimetría del centro comercial que muestra el estado de ocupación, tipología y mezcla comercial (*tenant mix*) de cada local.
  - **Fuente:** International Council of Shopping Centers [ICSC]. (2023). *Retail Real Estate Leasing Strategies*. Recuperado de [https://www.icsc.com](https://www.icsc.com)
  - **Relevancia:** Interfaz central del **Subsistema 1** para la gestión comercial y vacantes.

- [x] Contrato de locación
  - **Definición:** Acuerdo legal vinculante entre el administrador del centro comercial (arrendador) y el locatario, donde se estipulan plazos, cánones, garantías, destinos comerciales y obligaciones recíprocas.
  - **Fuente:** Asesores VE Global. (2024). *¿Qué ley regula los alquileres de locales comerciales en Venezuela?* Recuperado de [https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/](https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/)
  - **Relevancia:** Documento maestro que alimenta todas las reglas de negocio del **Subsistema 1** y motor de cálculo del **Subsistema 3**.

- [x] Llaves de ingreso pagaderas en cuotas
  - **Definición:** Derecho de llave o contraprestación por la incorporación a una ubicación comercial consolidada, fraccionada para su pago en plazos convenidos al inicio de la relación contractual.
  - **Fuente:** Cámara Inmobiliaria Venezolana. (2023). *Manual de Buenas Prácticas en Arrendamientos Comerciales*. Recuperado de [https://www.camarainmobiliaria.org.ve](https://www.camarainmobiliaria.org.ve)
  - **Relevancia:** Administrado por el **Subsistema 1** en conjunto con la cuenta corriente del **Subsistema 4**.

- [x] Períodos de gracia por remodelación
  - **Definición:** Plazo inicial exento total o parcialmente del pago de alquiler fijo, otorgado al locatario para que ejecute las obras de acondicionamiento e instalación de su local comercial.
  - **Fuente:** Bellhaven Real Estate. (2024). *Understanding Overage Rent in Retail Lease Agreements*. Recuperado de [https://www.bellhaven.org/learn/Overage-Rent](https://www.bellhaven.org/learn/Overage-Rent)
  - **Relevancia:** Parametrización contractual crítica en el **Subsistema 1** que condiciona la facturación del **Subsistema 3**.

- [x] Escalonamientos anuales del VMA (indexación a inflación o moneda dura)
  - **Definición:** Cláusulas de reajuste periódico programadas para actualizar el Valor Mínimo Mensual Asegurado en función de índices inflacionarios oficiales o tasas de referencia en moneda extranjera.
  - **Fuente:** Avarbitraje. (2024). *La regulación del monto de los alquileres comerciales y el arbitraje*. Recuperado de [https://avarbitraje.com/wp-content/uploads/2024/04/ANAVI-Nro4-A6-pp-111-127.pdf](https://avarbitraje.com/wp-content/uploads/2024/04/ANAVI-Nro4-A6-pp-111-127.pdf)
  - **Relevancia:** Automatizado en el **Subsistema 1** para la actualización de contratos vigentes.

- [x] Porcentajes de renta variable diferenciados por rubro o escala de facturación
  - **Definición:** Tasas porcentuales variables aplicadas sobre las ventas según la actividad comercial (ej. gastronomía, indumentaria, entretenimiento) o mediante tramos progresivos de facturación.
  - **Fuente:** Asesores VE Global. (2024). *¿Qué ley regula los alquileres de locales comerciales en Venezuela?* Recuperado de [https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/](https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/)
  - **Relevancia:** Configurado en el **Subsistema 1** y evaluado por el **Subsistema 2**.

- [x] Adendas y novaciones contractuales (retroactividad de facturación)
  - **Definición:** Modificaciones formales posteriores al contrato original que alteran condiciones financieras o plazos, requiriendo en ocasiones capacidad de recálculo retroactivo en la facturación.
  - **Fuente:** Asesores VE Global. (2024). *¿Qué ley regula los alquileres de locales comerciales en Venezuela?* Recuperado de [https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/](https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/)
  - **Relevancia:** Controlado mediante versionado de contratos en el **Subsistema 1** y aplicado en el **Subsistema 3**.


#### Subsistema 2 — Auditoría de Ventas
- [x] Cierre Z fiscal
  - **Definición:** Reporte diario emitido por las impresoras fiscales o sistemas de facturación autorizados que consolida el total de las operaciones de venta gravadas, exentas e impuestos de una jornada comercial.
  - **Fuente:** Servicio Nacional Integrado de Administración Aduanera y Tributaria [SENIAT]. (2020). *Providencia Administrativa sobre Normas de Emisión de Facturas*. Recuperado de [http://www.seniat.gob.ve](http://www.seniat.gob.ve)
  - **Relevancia:** Fuente primaria de validación de ingresos en el **Subsistema 2 (Auditoría de Ventas)**.

- [x] Liquidación de tarjetas de crédito/débito
  - **Definición:** Reportes de procesamiento y acreditación bancaria emitidos por los operadores de puntos de venta (*POS*), utilizados para contrastar y auditar la veracidad de las ventas declaradas por los locatarios.
  - **Fuente:** Superintendencia de las Instituciones del Sector Bancario [SUDEBAN]. (2023). *Normativas sobre Sistemas de Pago y POS*. Recuperado de [http://www.sudeban.gob.ve](http://www.sudeban.gob.ve)
  - **Relevancia:** Insumo de validación cruzada para el **Subsistema 2**.

- [x] Definición contractual de "ventas" (qué incluye y qué excluye)
  - **Definición:** Cláusula que delimita de forma estricta los ingresos netos computables para el cálculo de la renta variable, excluyendo explícitamente devoluciones, impuestos indirectos (IVA), ventas online no retiradas en tienda o consumos de empleados.
  - **Fuente:** Bellhaven Real Estate. (2024). *Understanding Overage Rent in Retail Lease Agreements*. Recuperado de [https://www.bellhaven.org/learn/Overage-Rent](https://www.bellhaven.org/learn/Overage-Rent)
  - **Relevancia:** Regla de negocio ejecutada en el motor de validación del **Subsistema 2**.

- [x] Atribución omnicanal de ventas
  - **Definición:** Criterio metodológico para asignar ventas originadas en plataformas digitales (e-commerce) pero retiradas (*click & collect*) o gestionadas físicamente dentro del local del centro comercial.
  - **Fuente:** International Council of Shopping Centers [ICSC]. (2022). *Omnichannel Retail Metrics in Shopping Centers*. Recuperado de [https://www.icsc.com](https://www.icsc.com)
  - **Relevancia:** Gestionado por el **Subsistema 2** para evitar distorsiones en la renta variable.

- [x] Algoritmo de sospecha (detección de anomalías)
  - **Definición:** Rutina automatizada que analiza patrones históricos de ventas y detecta desviaciones estadísticas significativas que sugieran subdeclaración de ingresos o errores de reporte.
  - **Fuente:** Chandola, V., Banerjee, A., & Kumar, V. (2009). *Anomaly detection: A survey*. ACM Computing Surveys (CSUR), 41(3), 1-58. Recuperado de [https://dl.acm.org/doi/10.1145/1541880.1541882](https://dl.acm.org/doi/10.1145/1541880.1541882)
  - **Relevancia:** Componente analítico central del **Subsistema 2 (Auditoría de Ventas)**.

- [x] Multas contractuales por ventas omitidas
  - **Definición:** Sanción económica estipulada en el contrato de locación aplicable cuando se comprueban, mediante auditoría, omisiones o inexactitudes deliberadas en las declaraciones de ventas.
  - **Fuente:** Asesores VE Global. (2024). *¿Qué ley regula los alquileres de locales comerciales en Venezuela?* Recuperado de [https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/](https://asesoresveglobal.com/alquiler-y-ventas-de-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/)
  - **Relevancia:** Generadas automáticamente por el **Subsistema 2** e integradas al **Subsistema 4** para su cobranza.


#### Subsistema 3 — Liquidación y Expensas
- [x] Motor de liquidación mensual
  - **Definición:** Componente de software centralizado que ejecuta de forma masiva y automatizada el cálculo mensual de alquileres fijos, variables, expensas, fondos de promoción y penalidades para todos los contratos activos.
  - **Fuente:** Fowler, M. (2002). *Patterns of Enterprise Application Architecture*. Addison-Wesley.
  - **Relevancia:** El núcleo operativo del **Subsistema 3 (Liquidación y Expensas)**.

- [x] Gastos Comunes Ordinarios y Extraordinarios
  - **Definición:** Clasificación de los egresos operativos del centro comercial; los ordinarios corresponden al mantenimiento corriente y administración, mientras que los extraordinarios cubren mejoras estructurales o reparaciones mayores.
  - **Fuente:** Ley de Regulación del Arrendamiento Inmobiliario para el Uso Comercial. Gaceta Oficial N° 40.418 de Venezuela (2014). Recuperado de [https://es.scribd.com/document/554202934/LEY-DE-ARRENDAMIENTOS-Comerciales](https://es.scribd.com/document/554202934/LEY-DE-ARRENDAMIENTOS-Comerciales)
  - **Relevancia:** Procesados y prorrateados en el **Subsistema 3**.

- [x] Redistribución iterativa de caps
  - **Definición:** Proceso matemático mediante el cual, al aplicar un tope máximo de expensas (*cap*) a determinados locales, el saldo excedente no facturable a dichos locales se recalcula y redistribuye de forma equitativa entre los restantes copropietarios o locatarios no encasillados en el tope.
  - **Fórmula de cálculo (Método iterativo de convergencia):**
    ```text
    Excedente_Total = Suma(MAX(0, Expensa_Calculada_i - Cap_i))
    Expensa_Parcial_i = MIN(Expensa_Calculada_i, Cap_i) + Excedente_Total * (Coeficiente_i / Suma_Coeficientes_Sin_Cap)
    ```
  - **Fuente:** Brueggeman, W. B., & Fisher, J. D. (2011). *Real Estate Finance and Investments*. McGraw-Hill/Irwin.
  - **Relevancia:** Algoritmo complejo ejecutado en el **Subsistema 3**.

- [x] Liquidación provisoria vs. definitiva
  - **Definición:** Estado de cuenta emitido mensualmente bajo estimaciones (*provisoria*) frente a la liquidación cerrada con base en comprobantes reales y auditorías (*definitiva*).
  - **Fuente:** Avarbitraje. (2024). *La regulación del monto de los alquileres comerciales y el arbitraje*. Recuperado de [https://avarbitraje.com/wp-content/uploads/2024/04/ANAVI-Nro4-A6-pp-111-127.pdf](https://avarbitraje.com/wp-content/uploads/2024/04/ANAVI-Nro4-A6-pp-111-127.pdf)
  - **Relevancia:** Gestionado por los ciclos de cierre del **Subsistema 3**.


#### Subsistema 4 — Obras, Marketing y Cobranza
- [x] Permisos de obra nocturna
  - **Definición:** Autorizaciones administrativas y operativas otorgadas a los locatarios para realizar trabajos de remodelación, decoración o mantenimiento dentro del centro comercial en horarios fuera de la atención al público.
  - **Fuente:** International Council of Shopping Centers [ICSC]. (2023). *Shopping Center Operations and Tenant Guidelines*. Recuperado de [https://icsc.com](https://icsc.com)
  - **Relevancia:** Controlado por el **Subsistema 4 (Obras, Marketing y Cobranza)**.

- [x] Fondo colectivo de marketing
  - **Definición:** Pool financiero acumulado mediante cuotas específicas de los locatarios para financiar la estrategia publicitaria global del centro comercial.
  - **Fuente:** Ley de Regulación del Arrendamiento Inmobiliario para el Uso Comercial. Gaceta Oficial N° 40.418 de Venezuela (2014). Recuperado de [https://es.scribd.com/document/554202934/LEY-DE-ARRENDAMIENTOS-Comerciales](https://es.scribd.com/document/554202934/LEY-DE-ARRENDAMIENTOS-Comerciales)
  - **Relevancia:** Administrado en el módulo de marketing del **Subsistema 4**.

- [x] Intereses punitorios
  - **Definición:** Cargos financieros adicionales aplicados por mora en el pago de las obligaciones de alquiler, expensas o servicios fuera de los plazos estipulados.
  - **Fórmula de cálculo:**
    ```text
    Interes_Punitorio = Monto_Vencido * Tasa_Diaria_Punitoria * Dias_De_Retraso
    ```
  - **Fuente:** Código Civil de Venezuela. (1982). Gaceta Oficial N° 2.990 Extraordinaria. Recuperado de [http://www.asambleanacional.gob.ve](http://www.asambleanacional.gob.ve)
  - **Relevancia:** Calculados y gestionados por el **Subsistema 4**.

- [x] Garantías de caución y pólizas de seguro de cumplimiento
  - **Definición:** Instrumentos financieros o fianzas bancarias/de seguros exigidas al locatario para garantizar el cumplimiento de las obligaciones contractuales y el pago de cánones y expensas.
  - **Fuente:** Asesores VE Global. (2024). *¿Qué ley regula los alquileres de locales comerciales en Venezuela?* Recuperado de [https://asesoresveglobal.com/alquiler-y-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/](https://asesoresveglobal.com/alquiler-y-propiedades-en-venezuela/que-ley-regula-el-arrendamiento-de-local-comercial-en-venezuela/)
  - **Relevancia:** Monitoreado en el **Subsistema 4** ante vencimientos o ejecuciones.


### 3.3 Conceptos técnicos de ingeniería

- [x] Idempotencia en el motor de facturación
  - **Definición:** Propiedad de una operación que permite que pueda aplicarse múltiples veces sin cambiar el resultado más allá de la aplicación inicial, garantizando que reintentos de peticiones de facturación no dupliquen cobros.
  - **Fuente:** Newman, S. (2015). *Building Microservices*. O'Reilly Media.
  - **Por qué aplica a este proyecto:** Es indispensable en el motor de facturación de los subsistemas de liquidación para evitar cobros duplicados ante fallas de red o reintentos de transacciones financieras.

- [x] Arquitectura orientada a eventos (Event-Driven Architecture)
  - **Definición:** Patrón de diseño de software basado en la producción, detección, consumo y reacción a eventos asíncronos entre servicios desacoplados.
  - **Fuente:** Richards, M., & Ford, N. (2020). *Fundamentals of Software Architecture*. O'Reilly Media.
  - **Por qué aplica a este proyecto:** Permite desacoplar los subsistemas (ej. que una venta registrada en Auditoría dispare de inmediato eventos de cálculo en el motor de liquidación sin acoplamiento rígido).

- [x] Algoritmo iterativo de punto fijo
  - **Definición:** Método numérico para encontrar soluciones a ecuaciones mediante aproximaciones sucesivas que convergen hacia un valor estable (punto fijo).
  - **Fórmula de cálculo:**
    ```text
    x_{n+1} = g(x_n)
    ```
  - **Fuente:** Burden, R. L., & Faires, J. D. (2010). *Numerical Analysis*. Cengage Learning.
  - **Por qué aplica a este proyecto:** Se utiliza en el motor de liquidación para resolver el cálculo interdependiente de los topes (*caps*) de expensas y los recálculos iterativos de alícuotas.

- [x] Z-Score robusto (mediana + MAD)
  - **Definición:** Método estadístico para la detección de valores atípicos (*outliers*) basado en la mediana y la Desviación Absoluta Mediana (MAD), altamente resistente a la distorsión causada por valores extremos.
  - **Fórmula de cálculo:**
    ```text
    Z_Robust = 0.6745 * (x_i - Mediana(X)) / MAD(X)
    ```
  - **Fuente:** Leys, C., Ley, C., Klein, O., Bernard, P., & Licata, L. (2013). *Detecting outliers: Do not use standard deviation around the mean, use absolute deviation around the median*. Journal of Experimental Social Psychology, 49(4), 764-766.
  - **Por qué aplica a este proyecto:** Es el núcleo del algoritmo de sospecha en el **Subsistema 2** para identificar ventas atípicas o erróneas sin que valores muy altos legítimos sesguen la detección.

- [x] Isolation Forest (alternativa para detección de anomalías)
  - **Definición:** Algoritmo de aprendizaje automático no supervisado basado en árboles de decisión que aísla anomalías en lugar de perfilar puntos de datos normales, eficiente para conjuntos de datos multidimensionales.
  - **Fuente:** Liu, F. T., Ting, K. M., & Zhou, Z. H. (2008). *Isolation forest*. In 2008 Eighth IEEE International Conference on Data Mining (pp. 413-422). IEEE.
  - **Por qué aplica a este proyecto:** Representa una alternativa avanzada de Machine Learning en el **Subsistema 2** para detectar patrones complejos de fraude o subdeclaración cruzando múltiples variables de ventas.

- [x] Audit Trail inmutable
  - **Definición:** Registro cronológico seguro y de solo lectura de todas las transacciones, modificaciones de contratos y accesos al sistema, garantizando trazabilidad y cumplimiento legal.
  - **Fuente:** Anderson, R. (2020). *Security Engineering: A Guide to Building Dependable Distributed Systems*. Wiley.
  - **Por qué aplica a este proyecto:** Garantiza la transparencia legal y fiscal ante auditorías externas en todos los subsistemas, impidiendo alteraciones no autorizadas de registros contables.

- [x] Control de versiones de contratos
  - **Definición:** Sistema de almacenamiento y gestión de cambios contractuales que mantiene un historial completo de adendas, modificaciones de tasas, cambios de VMA y estados anteriores de cada contrato.
  - **Fuente:** Evans, E. (2003). *Domain-Driven Design: Tackling Complexity in the Heart of Software*. Addison-Wesley.
  - **Por qué aplica a este proyecto:** Vital para el **Subsistema 1** y **Subsistema 3**, permitiendo recalcular facturaciones pasadas con exactitud histórica ante novaciones contractuales o disputas legales.

## 4. Preguntas Abiertas de Negocio

> **Instrucciones para el equipo:** esta sección no se llena con definiciones, se llena con **decisiones**. Cada pregunta debe cerrarse con una opción elegida y una justificación breve. Las decisiones cerradas alimentan la sección 5 (Lógica del Negocio).

### 4.1 Decisiones de lógica de negocio pendientes

| ID | Pregunta | Opciones | Decisión | Justificación |
| :--- | :--- | :--- | :--- | :--- |
| D-01 | ¿Cómo se combina el VMA con la renta variable? | (a) `MAX(VMA, Ventas × %)` (b) `VMA + MAX(0, (Ventas × %) − VMA)` | | |
| D-02 | ¿El porcentaje escalonado se aplica sobre el total de ventas o solo sobre el excedente del tramo? | (a) Sobre total (b) Por tramos sobre excedente | | |
| D-03 | Si el auditor detecta ventas omitidas, ¿se rehace la liquidación sobre la venta auditada o solo se aplica multa? | (a) Rehacer + multa (b) Solo multa | | |
| D-04 | ¿Qué atributo define "local menor" en el modelo? | (a) Booleano `es_ancla` (b) Rango de m² (c) Categoría contractual | | |
| D-05 | ¿La redistribución del excedente de caps se hace en una pasada o iterativamente? | (a) Una pasada (b) Iterativa hasta convergencia | | |
| D-06 | ¿Qué pasa si la redistribución no converge? | (a) Se corta en N iteraciones y alerta (b) Se fuerza el último valor (c) Otro | | |
| D-07 | ¿El fondo de promoción se calcula como % de ventas, monto fijo por m², o combinación? | (a) % ventas (b) Fijo por m² (c) Combinación | | |
| D-08 | ¿Qué mecanismo de rendición de cuentas debe tener el fondo de promoción? | (a) Reporte descargable (b) Vista por locatario (c) Ambos | | |
| D-09 | ¿La liquidación mensual es definitiva o provisional con ajuste anual (true-up)? | (a) Definitiva (b) Provisional + ajuste | | |
| D-10 | ¿Cómo se maneja la indexación si el índice se publica a destiempo? | (a) Nota de débito/crédito retroactiva (b) Se espera al mes siguiente | | |

### 4.2 Profundizaciones técnicas opcionales (no bloquean el análisis)

| Tema | Opciones | Recomendación preliminar | Estado |
| :--- | :--- | :--- | :--- |
| Algoritmo de expensas | (a) Punto fijo iterativo (b) Fórmula matricial cerrada | (a) Punto fijo con criterio de parada $0.01 y máx. iteraciones configurable | [ ] |
| Detección de anomalías | (a) Z-Score robusto por rubro (b) Regresión flujo vs. ventas (c) Isolation Forest | (a) Z-Score robusto para el MVP; (c) como mejora futura | [ ] |
| Ingesta de datos de ventas | (a) CSV/XML masivo (b) API de integración (c) Ambos | (a) CSV/XML para el MVP; (b) como mejora futura | [ ] |
| Motor de conversión multi-moneda | (a) Tipo de cambio fijo por contrato (b) Índice publicado (c) Ambos | Pendiente de definir con D-10 | [ ] |

### 4.3 Riesgos y supuestos a validar

| ID | Supuesto | Riesgo si falla | Mitigación |
| :--- | :--- | :--- | :--- |
| R-01 | Los contratos tienen un VMA fijo mensual | Si hay VMA escalonado por trimestre, cambia el modelo de contrato | Modelar VMA como lista de vigencias |
| R-02 | La inflación se publica antes del cierre mensual | Si se publica a destiempo, se necesita liquidación provisoria + ajuste retroactivo | Implementar true-up (ver D-09, D-10) |
| R-03 | Todas las tiendas ancla tienen tope de expensas | Si algunas no lo tienen, el algoritmo debe manejar el caso base | Modelar cap como opcional |
| R-04 | Los cierres Z llegan en formato estándar | Si cada locatario usa un formato distinto, se necesita parser configurable | Definir esquema de importación único |
| R-05 | Los locales menores no tienen cap de expensas | Si lo tienen, la redistribución puede no converger | Ver D-06 |

---


## 5. Lógica del Negocio

> **Instrucciones para el equipo:** esta sección se llena **después** de cerrar las decisiones de la sección 4. Cada regla debe ser una frase verificable, con ID, y con fuente citada (sección 7). Estas reglas son las que después se traducen a entidades, endpoints y tests.

### 5.1 Reglas de cálculo del alquiler

- **RN-01:** _(pendiente — depende de D-01)_
- **RN-02:** _(pendiente — depende de D-02)_
- **RN-03:** _(pendiente — indexación y escalonamiento)_

### 5.2 Reglas de auditoría de ventas

- **RN-04:** _(pendiente — depende de D-03)_
- **RN-05:** _(pendiente — definición contractual de "ventas")_
- **RN-06:** _(pendiente — umbral de anomalía y multa)_

### 5.3 Reglas de prorrateo de expensas

- **RN-07:** _(pendiente — depende de D-04, D-05, D-06)_
- **RN-08:** _(pendiente — coeficientes de reparto)_
- **RN-09:** _(pendiente — true-up, D-09)_

### 5.4 Reglas de cobranza y garantías

- **RN-10:** _(pendiente — intereses punitorios)_
- **RN-11:** _(pendiente — garantías de caución)_
- **RN-12:** _(pendiente — fondo de promoción, D-07, D-08)_

---


## 6. Alcance del MVP y Recortes

> **Instrucciones para el equipo:** esta sección se esboza ahora y se cierra al final de la fase de análisis. Evita que el equipo se enamore de funcionalidades que no va a poder construir en el tiempo de la materia.

| Subsistema | Entra en el MVP | Mejora futura | Se simula con datos de prueba |
| :--- | :--- | :--- | :--- |
| 1 — Locales y Contratos | CRUD de locales y contratos; VMA y % variable; escalonamiento básico | Plano interactivo con drag-and-drop; adendas retroactivas complejas | Contratos de ejemplo precargados |
| 2 — Auditoría de Ventas | Carga de CSV de cierres Z; reporte de anomalías con Z-Score robusto | Integración con POS reales; compras misteriosas | CSVs generados con datos sintéticos |
| 3 — Liquidación y Expensas | Motor de liquidación dual; prorrateo con redistribución iterativa de caps | Fórmula matricial cerrada; true-up anual completo | Gastos comunes de ejemplo |
| 4 — Obras, Marketing y Cobranza | CRUD de permisos; cálculo de intereses simple; registro de garantías | Workflow de aprobación de obras; cálculo de intereses compuestos | Permisos y garantías de ejemplo |

---


## 7. Referencias y Fuentes de Investigación

> **Instrucciones para el equipo:** cada término del glosario (sección 3) y cada regla de negocio (sección 5) debe tener una fuente citable. Sin fuente, el término no está investigado.

| ID | Fuente | Tipo | Términos o reglas que respalda |
| :--- | :--- | :--- | :--- |
| F-01 | | Artículo / Libro / Contrato modelo / Guía | |
| F-02 | | | |
| F-03 | | | |

---


## 8. Próximos Pasos

1. Completar el glosario (sección 3) con definición, fuente y relevancia para cada término.
2. Cerrar las decisiones de la sección 4.1 en reunión de equipo.
3. Redactar las reglas de negocio (sección 5) a partir de las decisiones cerradas.
4. Validar riesgos y supuestos (sección 4.3) con la profesora o con material de la industria.
5. Recién entonces: diseñar modelo de datos, endpoints y arquitectura.