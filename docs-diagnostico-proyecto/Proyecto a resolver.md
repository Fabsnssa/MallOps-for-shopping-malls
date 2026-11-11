Se intentan explicar la lógica y ciertos términos en [[Desglose del problema]].
El apoyo metodológico están en 3 libros de ing. software y análisis de sistemas, más 1 estándar de calidad [[Sustento Metodológico del proyecto]]
# Problema #42: Plataforma de Administración de Centros Comerciales (Shopping Malls), Renta Variable por Ventas y Gastos Comunes Ponderados

## 1. Descripción y Alcance

***"Sistema inmobiliario comercial y de auditoría de ingresos"*** para operadoras de grandes centros comerciales donde los cientos de locales arrendados (tiendas ancla, gastronomía, moda, cines, islas de pasillo) no pagan un alquiler fijo simple, sino un esquema híbrido compuesto por un *Valor Mínimo Mensual Asegurado (VMA)* más un *porcentaje variable* sobre sus ventas brutas declaradas y auditadas, además de fondos de promoción y expensas prorrateadas por coeficientes compuestos.

### 1.1 Descripción del 1er Subsistema
En el primer subsistema, el área comercial gestiona el plano interactivo de locales (Tenant Mix y Leasing) y la estructuración de contratos de locación: modela llaves de ingreso pagaderas en cuotas, períodos de gracia por remodelación del local, escalonamientos anuales del VMA indexados a inflación o moneda dura, y porcentajes de renta variable diferenciados por rubro o escalas de facturación mensual (por ejemplo, una tienda de electrónica paga el 4% de sus ventas si superan el VMA, mientras que una joyería paga el 9%).

### 1.2 Descripción del 2do Subsistema
En el segundo subsistema, opera el control y auditoría de Ventas de Locatarios: los comercios reportan sus cierres diarios de caja (cierres Z fiscales y liquidaciones de tarjetas de crédito/débito); simultáneamente, los auditores de campo del centro comercial realizan "puntos fijos y compras misteriosas" en locales seleccionados por algoritmo de sospecha (cuando las ventas por metro cuadrado de un local caen anormalmente respecto al promedio de su mismo rubro o respecto al conteo de flujo peatonal del pasillo), aplicando multas contractuales severas si detectan ventas omitidas sin facturar.

### 1.3 Descripción del 3er Subsistema
En el tercer subsistema, el motor de liquidación mensual calcula para cada local si en ese mes debe pagar solo el VMA o el VMA más el excedente porcentual sobre sus ventas netas de impuestos, y ejecuta el complejo prorrateo de Gastos Comunes Ordinarios y Extraordinarios (seguridad, climatización central, limpieza, seguros): pondera los metros cuadrados de cada local por coeficientes correctores según su ubicación (planta baja vs. tercer nivel), consumo energético y si es "tienda ancla" con tope contractual de expensas (cuyo diferencial no cubierto debe redistribuirse proporcionalmente entre el resto de los locales menores).

### 1.4 Descripción del 4to Subsistema
En el cuarto subsistema, administra los permisos de obra nocturna para remodelación de vidrieras, el fondo colectivo de marketing para campañas navideñas y la gestión de cobranza, intereses punitorios y garantías de caución.


## 2. Desafío y Valor en Ingeniería del Software

Motor de facturación inmobiliaria dual (alquiler mínimo vs. renta porcentual escalonada con liquidaciones provisorias y ajustes anuales), algoritmo de prorrateo de expensas con coeficientes ponderados y redistribución iterativa de topes contractuales de tiendas ancla (caps), y detección estadística de anomalías en declaraciones de ventas de locatarios.

---
