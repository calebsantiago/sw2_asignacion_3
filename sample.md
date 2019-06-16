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

### **Métrica 1: Timer**
#### **Descripción**
Se enfoca en medir la duración de un tipo de evento, su tasa de ocurrencia y proporciona
estadísticas de duración.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Por ejemplo, la utilidad de la métrica se puede observar en escenarios tales como el seguimiento 
del tiempo en que se tarda en ejecutar una consulta SQL, una petición HTTP, un método o función en 
particular.
#### **Ejemplo**
```typescript
/*la métrica Timer se puede utilizar de 2 formas*/
/*pasando una acción en el método Time*/
let requestTimer = new TimerOptions {
  Name = 'Request Timer',
  MeasurementUnit = Unit.Requests,
  DurationUnit = TimeUnit.Milliseconds,
  RateUnit = TimeUnit.Milliseconds
}
_metrics.Measure.Timer.Time(requestTimer, () => PerformRequest())

/*utilizando una declaración using, en donde la métrica Timer finalizará la grabación
al desecharla*/
using(_metrics.Measure.Timer.Time(requestTimer)) {
  PerformRequest()
}
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
La métrica Timer es adecuada para su utilización en el proyecto de software, ya que gracias a ella 
se puede dar a conocer cuánto es la duración así como la tasa ocurrencia de las consultas que se 
realizan a la base de datos Atlas MongoDB a través de la librería Mongoose,  la cual se implementa en 
el archivo connection con extensión de typescript.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 2: Gauge**
#### **Descripción**
Acción que devuelve la medida instantanea de un valor, en donde dicho valor aumenta y disminuye 
arbitrariamente.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Es ideal para cuantificar el uso actual de la memoria, cpu, temperatura, espacio en disco, etc.
#### **Ejemplo**
```typescript
let processPhysicalMemoryGauge = new GaugeOptions {
  Name = "Process Physical Memory",
  MeasurementUnit = Unit.Bytes
}
let process = Process.GetCurrentProcess()
_metrics.Measure.Gauge.SetValue(MetricsRegistry.Gauges.TestGauge, process.WorkingSet64)
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
La implementación de la métrica Gauge es adecuado para dar a conocer el rendimiento de los
componentes del nodo Heroku tales como memoria, cpu y espacio en disco frente a las solicitudes
HTTP e invocaciones de métodos tanto del lado back end como front end.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
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

- Aquí va la referencia 1
- Aquí va la referencia 2
- Aquí va la referencia 3
