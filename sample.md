# Asignación 3 - Ingeniería de Software 2

## Integrantes

- Guillermo Baca **20151635**
- Miguel Colina **20150346**
- Pelmef Méndez **20150865**
- Javier Ramírez **20152241**
- Caleb Santiago **20152339**

---

## Abstract

Aquí va el abstract.

---

## Introducción

Aquí va la introducción.

---

## Explicación del concepto de las métricas de software así como su relación con la ingeniería de software

Aquí va eso. 

---

## Métricas de Sofwtare

### **Métrica 1: Complejidad Ciclomática**
#### **Descripción**
Se enfoca en medir la complejidad de una estructura de código a través de un gráfico de flujo de control, el cual se desarrolla sobre la base del mismo programa, con la finalidad de cuantificar el número de rutas linealmente independientes (Tiwari & Kumar, 2014). Por lo tanto, la fórmula de la complejidad ciclomática de un gráfico G con "e" lados o aristas, "n" nodos o vértices y "p" componentes conectados es: **V(G) = e - n + 2p**, en donde 2 es el resultado de agregar un lado extra desde el nodo de salida al nodo de cada gráfico del módulo de componentes (Henderson-Sellers & Tegarden, 1994).
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Su utilidad se puede observar en escenarios tales como la estimación de los esfuerzos requeridos para el desarrollo de pruebas unitarias (longitud y amplitud) en unidades de código y en la detección de partes inestables del código fuente en donde es necesario el desarrollo de una refactorización o una mejor documentación del mismo (Mohamed, Fitriyah, Sulaiman, Rohana, & Endut, 2013). Por otro lado, la idea es obtener la métrica con el valor más bajo posible para que el riesgo de modificar dicho código fuente sea menor y, por ende, mucho más entendible y mantenible para los desarrolladores (Herbold, Grabowski, & Waack, 2011).
#### **Ejemplo**
![Image 1](https://www.researchgate.net/profile/Seifedine_Kadry/publication/288695710/figure/fig3/AS:323620028076034@1454168435561/Control-Flow-Graph-where-the-Cyclomatic-Complexity-of-McCabe-is-Calculated.png)  
**Figura 1:** Complejidad Ciclomática (Madi, Zein & Kadry, 2013)  
La complejidad ciclomática para el código anterior se obtiene a través del gráfico de flujo de control, en donde se observan 14 lados o aristas y 11 nodos o vértices, por lo que el valor de la métrica es: **14 - 11 + 2 = 5**.
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
La utilización de la métrica en el proyecto de software es adecuada debido a que ayudará a encontrar porciones inconsistentes del programa, en donde se requerirá refactorizar para que los mismos sean mucho más entendibles y mantenibles, asimismo, se reducirán sus riesgos asociados con respecto a su modificación en el tiempo.
#### **Aplicación al proyecto de software**
```typescript
/*ejecutar el comando 'npm install ts-complex --save' en cmd*/
const tscomplex = require('ts-complex') /*invoca a la librería ts-complex*/
const path = './app.ts' /*ruta del archivo con extensión typescript*/
const complexity = tscomplex.calculateCyclomaticComplexity(path) /*calcula la complejidad ciclomática*/
console.log(complexity) /*imprime el cálculo en pantalla*/
/*se obtuvo el resultado de 2.22 como valor promedio debido a la independencia de las funciones*/
```

---

### **Métrica 2: Complejidad de Halstead**
#### **Descripción**
Se basa en calcular la complejidad de un módulo de programa a través del conteo de operadores y operandos desde el mismo código fuente, asimismo, cabe resaltar que Halstead proporciona varios indicadores que se enfocan en distintos aspectos de la complejidad del software (Yu & Zhou, 2010). Sin embargo, se realizará un mayor énfasis en la medida del esfuerzo, el cual es conocido como aquello que se necesita para producir una porción de software, es decir, está métrica esta muy relacionada con la dificultad de entendimiento e implementación del código. Por lo tanto, la fórmula del esfuerzo de Halstead es: **E = (n1 * N2 * (N1 + N2) * log2(n1 + n2)) / 2 * n2**, en donde "n1" es el número de operadores únicos, "n2" es el número de operandos únicos, "N1" es la frecuencia total de operadores y "N2" es la frecuencia total de operandos (Love, Sheppard, Milliman, & Borst, 1979).
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
La medida se puede aplicar en contextos tales como la elaboración y comprensión de estructuras de código, en donde se requiere evaluar la calidad y claridad de los mismos, y en la comparación de programas de bajo nivel con programas equivalentes, pero de alto nivel (Shen, Conte, & Dunsmore, 1983). De igual forma, la finalidad es estimar de forma directa la dificultad de entendimiento e implementación que los desarrolladores requieren, debido a que la capacidad de mantenimiento debe ser una preocupación durante la etapa de desarrollo, a fin de que dichas porciones de código presenten una mejor calidad, un menor tiempo de desarrollo y una menor complejidad (De Silva, Kodagoda, & Perera, 2012).
#### **Ejemplo**
![Image 2](https://www.researchgate.net/profile/Seifedine_Kadry/publication/288695710/figure/fig1/AS:323620028076032@1454168435508/Example-of-C-alculation-of-Halsteads-Indices.png)  
**Figura 2:** Complejidad de Halstead (Madi, Zein & Kadry, 2013)  
El esfuerzo de Halstead para el código anterior se obtiene a través del conteo de operadores y operandos, en donde se observan 17 operadores, 7 operandos, 50 repeticiones del total de operadores y 30 repeticiones del total de operandos, por lo que el valor de la métrica es: **(17 * 30 * (50 + 30) * log2(17 + 7)) / 2 * 7 = 13361.89**.
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
La implementación de la métrica es adecuado para dar a conocer el rendimiento de los
componentes del nodo Heroku tales como memoria, cpu y espacio en disco frente a las solicitudes
HTTP e invocaciones de métodos tanto del lado back end como front end.
#### **Aplicación al proyecto de software**
```typescript
/*ejecutar el comando 'npm install ts-complex --save' en cmd*/
const tscomplex = require('ts-complex') /*invoca a la librería ts-complex*/
const path = './app.ts' /*ruta del archivo con extensión typescript*/
const complexity = tscomplex.calculateHalstead(path) /*calcula la complejidad de halstead*/
console.log(complexity) /*imprime el cálculo en pantalla*/
/*se obtuvo el resultado de 10071.70 como valor promedio debido a la independencia de las funciones*/
```

---

### **Métrica 3: Counter**
#### **Descripción**
Permite cuantificar las llamadas que se puede realizar de una función, variables, etc.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
El contexto de utilización de esta métrica se daría cuando se quiere conocer cuántas veces se hace llamada a un método, por ejemplo en el caso de una aerolínea se quisiera saber cuántas veces se hizo uso del método de pago.
#### **Ejemplo**
En los peajes de vehículos se podría querer conocer cuántos vehículos hicieron uso de peaje electrónico para lo cual hacen uso de un contador para conocer dicho valor.
```typescript
import { Counter, MetricRegistry } from "inspector-metrics";
const registry = new MetricRegistry();
const requestCount: Counter = registry.newCounter("requestCount");
// +1
requestCount.increment(1);
// -1
requestCount.decrement(1);
// =0
requestCount.getCount();
requestCount.reset();*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
La métrica identificada es viable a implementar en nuestro proyecto de software y en muchos más, en específico si deseamos la implementación de esta métrica en nuestro proyecto de software podemos querer conocer cuántos prestadores de servicios recurren a la funcionalidad de localización de su origen y destino para ejecutar el servicio, evidenciando si dicha funcionalidad es relevante para los usuarios,  por otro lado también podemos querer conocer el porcentaje de servicios que se ejecutan respecto al total de cotizaciones para lo cual podríamos implementamos un contador para las cotizaciones y otro para los servicios finalizados y podríamos conocer dicho valor.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 4: Meter**
#### **Descripción**
Meter mide la tasa de eventos realizados de diferentes maneras. La tasa media es la tasa promedio de eventos. Por lo general, se representa como la tasa total para toda la vida útil de su aplicación (por ejemplo, la cantidad total de solicitudes manejadas, dividida por la cantidad de segundos que el proceso ha estado ejecutándose), no ofrece una sensación de actualidad. Afortunadamente, los medidores también registran tres diferentes promedios móviles de ponderación exponencial: los promedios móviles de 1, 5 y 15 minutos.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Como meter permite medir la tasa de eventos realizados, podemos evaluar la cantidad de transacciones que se realizaron a un método de un software en un determinado rango de tiempo, se podría evaluar cuántas veces se realiza la transacción de compras en una página web en un día festivo. De esta manera podemos estar a la vanguardia de las afluencia que tendrá el sistema en cierto periodo de tiempo.
#### **Ejemplo**
```typescript
import { Meter, MetricRegistry } from "inspector-metrics";
const registry = new MetricRegistry();
const callCount: Meter = registry.newMeter("callCount");
callCount.mark(1);
const count: number = callCount.getCount();
const m15: number = callCount.get15MinuteRate();
const m5: number = callCount.get5MinuteRate();
const m1: number = callCount.get1MinuteRate();
const mean: number = callCount.getMeanRate();
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Es viable identificar la cantidad de solicitudes de cotización en un periodo de tiempo para poder saber cual es el impacto que tiene nuestra aplicación.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 5: Aquí va el título**
#### **Descripción**
Aquí va la descripción.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Aquí va eso.
#### **Ejemplo**
```typescript
/*Aquí va el ejemplo.*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Aquí va eso.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 6: Aquí va el título**
#### **Descripción**
Aquí va la descripción.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Aquí va eso.
#### **Ejemplo**
```typescript
/*Aquí va el ejemplo.*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Aquí va eso.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 7: Aquí va el título**
#### **Descripción**
Aquí va la descripción.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Aquí va eso.
#### **Ejemplo**
```typescript
/*Aquí va el ejemplo.*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Aquí va eso.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 8: Aquí va el título**
#### **Descripción**
Aquí va la descripción.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Aquí va eso.
#### **Ejemplo**
```typescript
/*Aquí va el ejemplo.*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Aquí va eso.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 9: Aquí va el título**
#### **Descripción**
Aquí va la descripción.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Aquí va eso.
#### **Ejemplo**
```typescript
/*Aquí va el ejemplo.*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Aquí va eso.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 10: Aquí va el título**
#### **Descripción**
Aquí va la descripción.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Aquí va eso.
#### **Ejemplo**
```typescript
/*Aquí va el ejemplo.*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Aquí va eso.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

## Conclusiones

Aquí van las conclusiones.

---

## Rúbrica

| Criterio | Sobresaliente | Aceptable | Deficiente |
|------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.Clasificación de fuentes | El alumno presenta una adecuada clasificación de los temas recopilados, considerando las áreas y sub áreas del tema escogido. (5 ptos.)   | Existen cierta información que no guarda una relación directa con el tema analizado. (4-3 ptos.)  | Las fuentes bibliográficas son dispersas y no guardan relación con el tema escogido. (1-2 ptos.)  |
| 2.Material relevante obtenido de fuentes confiables | La información obtenida es de alta calidad dada por: conferencias o journals de la especialidad y de alto impacto. Clasificación del material obtenido de journals q1-q2. (5 ptos.)  | Alguna de la información recopilada proviene de fuentes de dudosa procedencia. Se ha centrado en journals q3-q4 o en congresos de la especialidad de bajo impacto. (4-3 ptos.) | El material recopilado ha sido obtenido de fuentes de bajo nivel, en algunos casos se presume que proviene de journals o conferencias clasificadas como depredadoras. (1-2 ptos.) |
| 3.Utilización del formato APA u otro formato de referencia | Se ha utilizado de forma adecuada el formato APA, Vancouver o Harvard, con sus respectivas variantes aceptadas. Esto incluye la referencia a todo nivel: texto y figuras. (5 ptos.) | Se presentan ciertas fallas, menos al 30% de referencias utilizadas de forma errónea o material no referenciado, al interior del artículo. (4-3 ptos.)  | No se ha utilizado el formato de referencia adecuado o se ha usado combinación entre varios formatos. Existen diversas partes sin referenciar al interior del artículo. (1-2 ptos.)  |
| 4.Síntesis adecuada de la información recopilada  | Se han tomado aproximadamente más de 5 artículos para la elaboración de su artículo. Información relevante ha sido obtenida de cada uno de ellos, sintetizando de forma adecuada el aporte de cada uno de ellos. (5 ptos.)     | El número de referencias tomadas para el artículo ha sido entre 3 y <5 artículos. Algunos artículos no han sido adecuadament e resumidos o se presume que han sido colocados para llenar vacíos en su artículo. (4-3 ptos.)      | La cantidad de artículos considerados ha sido < 3. La mayor parte de la información obtenida no es relevante o no está adecuadamente resumida. (1-2 ptos)   |

---

## Referencias
- De Silva, D. I., Kodagoda, N., & Perera, H. (2012). *Applicability of Three Complexity Metrics.* The International Conference on Advances in ICT for Emerging Regions, 82–88. https://doi.org/10.1109/icter.2012.6421409
- Henderson-Sellers, B. & Tegarden, D. (1994). *The theoretical extension of two versions of cyclomatic complexity to multiple entrylexit modules.* Software Quality Control. 3. 253-269. https://doi.org/10.1007/BF00403560
- Herbold, S., Grabowski, J., & Waack, S. (2011). *Calculation and optimization of thresholds for sets of software metrics.* 812–841. https://doi.org/10.1007/s10664-011-9162-z
- Love, T., Sheppard, S. B., Milliman, P., & Borst, M. A. (1979). *Measuring the Psychological Complexity of Software Maintenance Tasks with the Halstead and McCabe Metrics.* IEEE Transactions on Software Engineering, SE-5(2), 96–104. https://doi.org/10.1109/TSE.1979.234165
- Madi, A., Zein, O.K., & Kadry, S. (2013). *On the improvement of cyclomatic complexity metric.* International Journal of Software Engineering and its Applications. 7. 67-82. 
- Mohamed, N., Fitriyah, R., Sulaiman, R., Rohana, W., & Endut, W. (2013). *The Use of Cyclomatic Complexity Metrics in Programming Performance ’ s Assessment.* Procedia - Social and Behavioral Sciences, 90(InCULT 2012), 497–503. https://doi.org/10.1016/j.sbspro.2013.07.119
- Shen, V. Y., Conte, S. D., & Dunsmore, H. E. (1983). *Software Science Revisited: A Critical Analysis of the Theory and Its Empirical Support.* IEEE Transactions on Software Engineering, SE-9(2), 155–165. https://doi.org/10.1109/TSE.1983.236460
- Tiwari, U., & Kumar, S. (2014). *Cyclomatic complexity metric for component based software.* ACM SIGSOFT Software Engineering Notes, 39(1), 1–6. https://doi.org/10.1145/2557833.2557853
- Yu, S., & Zhou, S. (2010). *A Survey on Metric of Software.* 2nd IEEE Proceedings of International Conference on Information Management and Engineering (ICIME), 253–356. https://doi.org/10.1109/icime.2010.5477581