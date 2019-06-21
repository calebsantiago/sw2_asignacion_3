# Asignación 3 - Ingeniería de Software 2

## Integrantes

- Guillermo Baca **20151635**
- Miguel Colina **20150346**
- Pelmef Méndez **20150865**
- Javier Ramírez **20152241**
- Caleb Santiago **20152339**

---

## Abstract

The advances in software evolve every day more and more, this due to the great amount of resources that appear day by day; nevertheless, it is no longer enough to develop software that only fulfills requested requirements, but to implement software with peculiarities that allow to make an easy maintenance, to add new modules of fast form, that is scalable, efficient, etc. For it is essential to know the metrics that this development has, so that it provides us with a vision of the quality, performance, extensibility, etc. Therefore, this research article is oriented to offer several useful metrics to know how good was our software development and what action we can cover to improve our coding.

---

## Introducción

El desarrollo de software engloba una gran cantidad de tareas que son necesarias, sin embargo para conocer si nuestro software fue el mas óptimo podemos comprobarlo mediante la aplicación de una serie de métricas que pueda darnos un diagnóstico de qué tan adecuado fue nuestro desarrollo o no, es por ello que realizar una correcta parametrización y análisis es imprescindible para comprender las métricas que deseamos calcular, es respecto a estas métricas que deseamos calcular, las que nos permitirán compararnos que tan bien hemos implementado nuestro software y si es necesario aplicar métodos de refactorización para mejorar nuestro programa. Para ello mediante el presente artículo buscamos dar a conocer métricas, así mismo como una ejemplificación de ellas y la relevancia que estas tienen para el desarrollo del software.

---

## Explicación del concepto de las métricas de software así como su relación con la ingeniería de software

La ingeniería de software es una disciplina para el desarrollo de software que combina métodos para todas las etapas de la elaboración del mismo, herramientas para automatizar dichos métodos, bloques de construcción potentes, técnicas que garantizan la calidad del software y una filosofía predominante para la coordinación, control y administración. Por otro lado, la calidad de software se define como la concordancia entre los requisitos funcionales y de rendimiento explícitamente establecidos, con los estándares de desarrollo explícitamente documentados y con las características implícitas que se esperan de todo software desarrollado profesionalmente (Pressman, 2002).

Por lo tanto, la medición es fundamental para la disciplina de la ingeniería de software, es por ello que existen varias razones (Sommerville, 2005): 
- Indica la calidad del producto.
- Evalúa la productividad de los desarrolladores que elaboran el producto.
- Evalúa los beneficios del uso de nuevos métodos y herramientas de la ingeniería de software.
- Establece una línea base para la estimación.
- Ayuda a justificar el uso de nuevas herramientas o de formación adicional.

Asimismo, los factores que afectan la calidad de software se clasifican en dos categorías: métricas cualitativas, como aquellas que miden el software de manera indirecta o subjetiva, y métricas cuantitativas, como aquellas que miden el software de manera directa u objetiva. Por esta razón, existen muchos factores que afectan el desarrollo de un producto de software, entre estos se incluyen el tipo de programa a desarrollar, el tamaño del mismo, el lenguaje de implementación, la experiencia de los desarrolladores, las técnicas de programación y el ambiente computacional (Pressman, 2002).

---

## Métricas de Software

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
El manejo de la métrica en el proyecto de software es apropiado, debido a que ayudará a estimar la dificultad de implementación y entendimiento en ciertas porciones de código, con el propósito de desarrollar un programa mantenible en el tiempo, en otras palabras, de alta calidad y de menor complejidad.
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
### **Métrica 3: Mantenibilidad**
#### **Descripción**
Hace referencia a la facilidad con la que se puede mantener un sistema. Es un atributo interno del sistema que no puede medirse directamente. En lugar de ello, se pueden medir atributos del proceso de mantenimiento, tales como el tiempo necesario para realizar un cambio, el cual está influenciado por la capacidad de mantenimiento del software (Frappier, Matwin, & Mili, 1994).
Fórmula = 171-5.2In(HV)-0.23CC-16.2In(LOC)+50.0sin√2.46*COM 
HV:Halstead
LOC : Líneas de código
COM : porcentaje de comentarios

#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
La mantenibilidad es importante en todo software hoy en dia, el grado de mantenibilidad está asociado al grado de calidad del software, ya que un software demasiado complejo a nivel de mantenimiento no sería el adecuado ya que no sería fácilmente modificable o reusable. Así mismo, según Herbold: La mantenibilidad se asocia a otros conceptos claves en el desarrollo del software los cuales son el grado de testeabilidad, comprensibilidad , extensibilidad de manera que si cumplen estas características satisfactoriamente se podría decir que el software será mantenible y en consecuencia la detección como la corrección de errores será rápida y eficiente, además de proporcionar otras ventajas (Informática & Ciencias, 2013).
#### **Ejemplo**

```typescript
public static String Sha1(String plainText)
{
  using (SHA1Managed sha1=new SHA1Managed())
  {
    Byte[] text=Encoding.Unicode.GetBytes(plainText);
    Byte[] hashBytes=sha1.ComputeHash(text);
    return Convert.ToBase64String(hashBytes);
   }
}

public static String Sha1(String plainText)
{
  Byte[] text, hashBytes;
  using (SHA1Managed sha1=new SHA1Managed())
  {
    text=Encoding.Unicode.GetBytes(plainText);
    hashBytes=sha1.ComputeHash(text);
  }
  return Convert.ToBase64String(hashBytes);
}
El índice de mantenibilidad (MI) para el primer ejemplo es de 71 mientras que con la aplicación de técnicas de refactorización, se observa que el valor de mantenibilidad aumenta en 2 puntos en general dicho código posee una buena mantenibilidad al encontrarse en el rango de 20-100.
*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
La aplicación de la métrica descrita es viable de implementar en nuestro proyecto de software debido a que nos permitirá conocer cuan mantenible es nuestro proyecto, de forma que podremos tener una retroalimentación de qué aspectos mejorar para futuros trabajos en base a este.


#### **Aplicación al proyecto de software**
```typescript
/*const tscomplex = require('ts-complex'); //adquiere la libreria ts-complex para posteriomente realizar el calculo
const path = './app.ts'; // accede a la ruta del archivo a evaluar 
const maintainability = tscomplex.calculateMaintainability(path); //calcula la mantenibilidad del software
console.log(maintainability);  // imprime valores de mantenibilidad del proyecto 
*/
```


---
### **Métrica 3: Core Size**
#### **Descripción**
Hace referencia al porcentaje de módulos que dependen en gran medida de otros módulos y que a su vez dependen de ellos mismos. Este valor es asociado a que a menor porcentaje mejor métrica.

#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**

Conocer el porcentaje de módulos que poseen dependencias es importante para tener conocimiento del grado de acoplamiento que posee el software, de manera que la meta en todo buen software es que posea una alta cohesión y un bajo acoplamiento de esta manera conocer dicha métrica será relevante al poder implementar las medidas correctivas y nuestro software sea mucho mas tolerante a fallos. Los beneficios de de su utilización será relevantes para disminuir tasa de errores, mejorar la mantenibilidad, etc. 
#### **Ejemplo**

```typescript
calculateCoreSize(projectReport, visibilityMatrix)  {
     if (projectReport.firstOrderDensity === 0)     {
        projectReport.coreSize = 0;
        return;
     }
      const length = visibilityMatrix.length;
      const fanIn = new Array(length);
     const fanOut = new Array(length);
     let coreSize = 0;
 
     for (let rowIndex = 0; rowIndex < length; rowIndex++)     {
        fanIn[rowIndex] = visibilityMatrix[rowIndex].reduce((sum,value,valueIndex) =>
        {
fanOut[valueIndex] = rowIndex === 0 ? value :fanOut[valueIndex]+ value;
           return sum + value;
       }, 0);
     }
Considerar que mientras mas bajo sea el valor mejor, viceversa.

*/
```
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Efectivamente la aplicación de esta métrica en nuestro de proyecto de software será de gran ayuda para conocer qué tan acoplados se encuentran nuestras clases y en proyectos futuros aplicar técnicas para reducir este acoplamiento de manera que en caso de algún error en alguno de los módulos del software no presente grandes inconvenientes en módulos que ahora se puedan encontrar acoplados a ellos.



#### **Aplicación al proyecto de software**
```typescript
/*const escomplex = require('escomplex');
const result = escomplex.analyse('./app.ts', options);
const CoreSize = true;
escomplex.processResults(result.coreSize, CoreSize);
*/
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

### **Métrica 5: Lack of Cohesion of Methods**
#### **Descripción**
La falta de cohesión en los métodos (LCOM), esta métrica se encarga de medir la correlación entre los métodos y las variables de instancia local de una clase. Si existe muy baja cohesión se aumenta la complejidad del software, por el contrario una alta cohesión garantiza una buena subdivisión de la clase. Las clases que presentan baja cohesión pueden ser divididas en dos o más subclases que tengan una cohesión mayor.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Aplicado donde no existen atributos de instancia para cada clase, esto quiere decir que todas las variables son heredadas de una clase superior (superclase). También existe el caso de haber definido instancias de clase, pero estas no tienen ninguna referencia. 
#### **Ejemplo**
```C#
public class NumberManipulator
{
    private int _number;
 
    public int NumberValue => _number;
 
    public void AddOne() => _number++;
 
    public void SubtractOne() => _number--;
}
```
En el ejemplo anterior se observa que la clase contiene una variable local, dos métodos y una propiedad. En este caso ambos métodos y la propiedad refieren a la variable local. Esta clase es cohesiva, ya que trabaja completamente entorno al campo numérico.
```C#
public class NonCohesiveNumberManipulator
{
    private int _firstNumber;
    private int _secondNumber;
    private int _thirdNumber;

    public void IncrementFirst() => _firstNumber++;
    public void IncrementSecond() => _secondNumber++;
    public void IncrementThird() => _thirdNumber++;
}
```
En el último ejemplo existen tres variables locales, las cuales se comunican con un método exclusivo para cada una. Por lo que se puede dar la pregunta si en realidad hay comunicación dentro de esta clase.
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
La métrica es totalmente viable para su aplicación en proyectos de software, dado que es importante conocer la cohesión entre las clases de dicho software.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

### **Métrica 6: Cognitive Complexity**
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

### **Métrica 7: Densidad de comentarios**
#### **Descripción**
Según Oliver Arafat y Dirk Riehle en _The Comment Density of Open Source Software Code_, se tienen los siguientes preconceptos:
*	Línea de código base (SLOC): Es una línea física en un archivo fuente que contiene código fuente.
*	Línea de comentario (CL): Es una línea física en un archivo fuente que representa un comentario.
*	Línea de código (LOC): Es un SLOC o un CL. 

La densidad de líneas de código es definida como el porcentaje resultante de dividir el total de líneas de comentario entre el total de líneas de código de un archivo o de un grupo de archivos.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Esta métrica puede ser usada para cualquier base de código, sin embargo, se considera que su uso es más beneficioso en código que no es autogenerado. Esto se debe a que el objetivo de la métrica es determinar que tanto un código fue o es comentado por sus desarrolladores. En el caso de código autogenerado es inusual que el desarrollador lo comente ya que normalmente se autogenera código simple.

Según Oliver Arafat y Dirk Riehle, _se asume que la densidad de comentarios es un buen predictor de la mantenibilidad y por lo tanto supervivencia de un proyecto_. Debido a esto, los beneficios de esta métrica son bastante parecidos a los del Índice de mantenibilidad los cuales ya han sido mencionados anteriormente. El único beneficio de esta métrica que no comparte con el índice de mantenibilidad es el conocimiento específico sobre los comentarios del código.

#### **Ejemplo**
```typescript
//Generated by typescript 1.8.10
var disp = function () {
   console.log("Function invoked");
};
disp();
```
En el presente ejemplo hay un total de 5 líneas de código y 1 línea de comentario por lo que la densidad de comentario seria 1/5 = 20% .

#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Tanto en proyectos de software en general como en nuestro proyecto la implementación de esta métrica es viable. Comentar la base de código es parte de las buenas prácticas de desarrollo de software por lo que hay una correlación entre la mantenibilidad de la base del código y su densidad de comentarios. Además, actualmente la mayoría de lenguajes de programación usados permiten los comentarios de forma nativa o tienen un plugin que permite añadirlos. El único escenario en el que podría no recomendarse esta métrica es en el caso en que una gran parte de la base de código ha sido autogenerado. 
#### **Aplicación al proyecto de software**
```
https://api.codetabs.com/v1/loc?github=calebsantiago/sw2_app
```
![Lineas de código](https://i.imgur.com/WDfO40Y.png)

En nuestro proyecto las líneas de código están distribuidas como muestran la imagen superior. Ya que buena parte del código JSON y JavaScript es autogenerado se ha optado por obtener la métrica de densidad de comentarios tomando solo en cuenta las líneas de código en TypeScript. Nuestro proyecto tiene un total de 1255 lineas de código de TypreScript de las cuales 23 son líneas de comentarios por lo tanto nuestra densidad de comentarios es de (23/1255)*100 = 1.83%


---

### **Métrica 8: Promedio de métodos por clase**
#### **Descripción**
Según Michele Lanza y Radu Marinescu en _Object-oriented metrics in practice: Using software metrics to characterize, evaluate, and improve the design of object-oriented systems_, métricas simples como NOC (Número de clases), NOM (Numero de métodos u operaciones, incluyendo funciones globales) o LOC (Líneas de código)  no son usadas por sí mismas sino más bien se usan para hallar proporciones entre sí mismas o con otras métricas. Una de estas proporciones tocada en el libro es la razón entre el número de métodos y la cantidad de clases: Promedio de métodos por clase o NOM promedio.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Esta métrica, como muchas otras, sirve para darse una idea de la mantenibilidad del código. El NOM de una clase puede servir para saber si tenemos “código muerto” en el caso de una clase sin métodos (NOM=0) o una clase sobrecargada si es que tiene muchos métodos (NOM>20). Un NOM promedio muy bajo o muy alto es un indicador de que existen clases con NOM bajo u alto, las cuales pueden ser un indicador de código con mala mantenibilidad. Es por esto que esta métrica puede ser usada en cualquier contexto de una base de código orientada a objetos.

Los beneficios de esta métrica son bastante parecidos al del índice de mantenibilidad ya que ambos se usan como un indicador de mantenibilidad. La diferencia radica en que NOM promedio solo toma en cuenta el código conformado por las clases del programa por lo que en caso de tener un resultado adverso es más fácil de determinar la fuente del problema. Sin embargo, solo tomar en cuenta las clases del programa significa que este indicador no toma en cuenta la mantenibilidad del código que no se encuentre definido como clases. 
#### **Ejemplo**
```typescript
class Animal {
    private name: string;
    constructor(theName: string) { this.name = theName; }
}

class Rhino extends Animal {
    constructor() { super("Rhino"); }
}

class Employee {
    private name: string;
    constructor(theName: string) { this.name = theName; }
}

let animal = new Animal("Goat");
let rhino = new Rhino();
let employee = new Employee("Bob");
```
En el presente ejemplo hay un total de 3 clases y 3 métodos por lo que el NOM promedio es 3/3 = 1. 
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
En proyectos de software en general, consideramos que es viable para software con una base de código orientada a objetos, sin embargo, consideramos que no debe ser la única métrica de mantenibilidad ya que se fija únicamente en las clases y sus métodos. El NOM por clase es especialmente útil para analizar clases en específico ya que se puede segmentar las clases con un valor mínimo y máximo. En el caso de nuestro proyecto de software, es viable su utilización ya que utilizamos hacemos uso de varias clases. 
#### **Aplicación al proyecto de software**
![Diagrama de clases contacta](https://i.imgur.com/ihm6sv9.jpg)
En nuestro proyecto de software tenemos 4 clases y 17 métodos por lo que nuestro NOM promedio es de 17/4 = 4.25

---

### **Métrica 9: Reliability**
#### **Descripción**
Reliability es una metrica importante en el desarrollo de software debido a que analiza la calidad del programa mediante factores individuales y colectivos. Esta métrica se enfoca en los defectos y errores del software. Mayor la probabilidad de ocurrencia de un defector en un sistema de software, menor es la confiabilidad del sistema de software (Aman Jatain, 2014). 
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Esta metrica se usaria debido a la incetidumbre sobre los errores que pueden ocurrir en tu software. Entre los diferentes parametros se encuentra la frecuencia al fallo, tipo de fallo, efecto de la ocurrencia del fallo, frecuencia de ejecución de módulos defectuosos, etc. Usar esta métrica disminuiria los costos, tiempo y recurso que se usan en un software desconfiable; además, al momento de insertar nuevo código se evitarian nuevos fallos y no se requerirá pruebas prolongadas en el sistema para tratarlos lo que ahorra tiempo en el desarrollo. Finalimente, podemos cuantificar la calidad del software y brindar a los desarrolladores una mejor comprensión del proceso de desarrollo.
#### **Ejemplo**
```C
int errores (int input)
{
    int x,y,k,1;
    k = input/100;
    x=2;
    y= k + 5;
    if ((3*k+100)> 43)
    {
        y++;
        x = x / (x- y);
    }

    return x;
}
```


Un bugg que podriamos encontrar en el código anterior seria que "x" y "y" serían igual, esto ocacionaria que sea una división a 0 lo cual generaria un error en el programa.
#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Si es viable en nuestro proyecto porque buscamos que sea confiable y no perder tanto tiempo en pruebas de errores.
#### **Aplicación al proyecto de software**



---

### **Métrica 10: Duplicated Code**
#### **Descripción**
Duplicated Code se da cuando se produce una copia y adaptación de un codigo ya existente, normalmente es implementado cuando se quiere reusar software. Duplicated Code es utilizado debido a que disminuye el tiempo de desarrollo, mejora la confiabilidad, evita malograr el código, etc. Aún asi, Duplicated Code trae problemas como generar un código más extenso, genera mayor esfuerzo a los trabajadores debido que tienen que ser más cautelosos al momento de cambiar las intancias clonadas y representa un desafio al momento de mantener el software.
#### **¿En qué contextos se utilizaría? ¿Cuáles serían los beneficios de su utilización?**
Esta métrica sirve para tener noción de la mantenibilidad del código, además que al usar codigo duplicado disminuye la escalabilidad de un software. Al saber que cantidad de código clonado tenemos, podemos disminuirlo y evitar las consecuencias que trae este.
#### **Ejemplo**
![Ejemplo10](https://image.slidesharecdn.com/codecraftsmanship-13426395586098-phpapp01-120719032401-phpapp01/95/code-craftsmanship-39-728.jpg?cb=1342668682)


**Figura Ejemplo10:** Duplicate Code Example (Prokarma, 2012)


En el ejemplo podemos ver que la estructura es identica y el cambio se da en el nombre de la función.

#### **¿Considera que la utilización de la técnica es viable para su aplicación en proyectos de software?**
Si, debido a que un proyecto de software debe ser escalable y fácil de mantener. Saber que cantidad de código es clonado en nuestro proyecto no ayudaria a dismuirlo e implementar un mejor diseño de sofware.
#### **Aplicación al proyecto de software**
```typescript
/*Aquí va la aplicación.*/
```

---

## Conclusiones

Aquí van las conclusiones.

---

## Referencias
- De Silva, D. I., Kodagoda, N., & Perera, H. (2012). *Applicability of Three Complexity Metrics.* The International Conference on Advances in ICT for Emerging Regions, 82–88. https://doi.org/10.1109/icter.2012.6421409
- Henderson-Sellers, B. & Tegarden, D. (1994). *The theoretical extension of two versions of cyclomatic complexity to multiple entrylexit modules.* Software Quality Control. 3. 253-269. https://doi.org/10.1007/BF00403560
- Herbold, S., Grabowski, J., & Waack, S. (2011). *Calculation and optimization of thresholds for sets of software metrics.* 812–841. https://doi.org/10.1007/s10664-011-9162-z
- Love, T., Sheppard, S. B., Milliman, P., & Borst, M. A. (1979). *Measuring the Psychological Complexity of Software Maintenance Tasks with the Halstead and McCabe Metrics.* IEEE Transactions on Software Engineering, SE-5(2), 96–104. https://doi.org/10.1109/TSE.1979.234165
- Madi, A., Zein, O.K., & Kadry, S. (2013). *On the improvement of cyclomatic complexity metric.* International Journal of Software Engineering and its Applications. 7. 67-82. 
- Mohamed, N., Fitriyah, R., Sulaiman, R., Rohana, W., & Endut, W. (2013). *The Use of Cyclomatic Complexity Metrics in Programming Performance ’ s Assessment.* Procedia - Social and Behavioral Sciences, 90(InCULT 2012), 497–503. https://doi.org/10.1016/j.sbspro.2013.07.119
- Pressman, R.S., (2002). *Ingeniería del Software: Un Enfoque Practico.* (5ta. Edición). Madrid: McGraw-Hill Interamericana.
- Shen, V. Y., Conte, S. D., & Dunsmore, H. E. (1983). *Software Science Revisited: A Critical Analysis of the Theory and Its Empirical Support.* IEEE Transactions on Software Engineering, SE-9(2), 155–165. https://doi.org/10.1109/TSE.1983.236460
- Sommerville, I., (2005). *Ingeniería del Software.* (7ma. Edición). Madrid: Addison-Wesley.
- Tiwari, U., & Kumar, S. (2014). *Cyclomatic complexity metric for component based software.* ACM SIGSOFT Software Engineering Notes, 39(1), 1–6. https://doi.org/10.1145/2557833.2557853
- Yu, S., & Zhou, S. (2010). *A Survey on Metric of Software.* 2nd IEEE Proceedings of International Conference on Information Management and Engineering (ICIME), 253–356. https://doi.org/10.1109/icime.2010.5477581
- Frappier, M., Matwin, S., & Mili, A. (1994). Software Metrics for Predicting Maintainability. Journal Of Software Maintenance Research   And Practice, 3(3), 129–143. Retrieved from http://www3.interscience.wiley.com/journal/113445994/abstract
- Informática, D. De, & Ciencias, F. De. (2013). open source utilizando métricas de orientación a objetos. 15–29.
- Lakshminarayana, A., & Newman, T. S. (1999). Principal component analysis of Lack of Cohesion in Methods (LCOM) metrics. Technical Report TRUAH-CS-1999-01. https://pdfs.semanticscholar.org/81f6/1e7225f2f89f6fe61df6d69ef65c1ecb87fd.pdf
- Arafati, O., & Riehle, D. (2009, May). The comment density of open source software code. In 2009 31st International Conference on Software Engineering-Companion Volume (pp. 195-198). IEEE.
- Lanza, M., & Marinescu, R. (2007). Object-oriented metrics in practice: using software metrics to characterize, evaluate, and improve the design of object-oriented systems. Springer Science & Business Media.
- Farooq, Sheikh Umar & Quadri, SMK & Ahmad, Nurain. (2012). Metrics, models and measurements in software reliability. IEEE 10th Jubilee International Symposium on Applied Machine Intelligence and Informatics, SAMI 2012 - Proceedings. 441-449. 10.1109/SAMI.2012.6209008.
- Jatain, Aman & mehta, Yukti. (2014). Metrics and Models for Software Reliability: A Systematic Review. 10.1109/ICICICT.2014.6781281.
- Jiang, Z. M. (2006). Visualizing and understanding code duplication in large software systems (Master's thesis, University of Waterloo).
- Hordijk, W., Ponisio, M. L., & Wieringa, R. (2009, April). Harmfulness of Code Duplication-A Structured Review of the Evidence. In EASE.
