
`TRABAJO EN PROCESO`

# Implementación de una Red Neuronal Evolutiva mediante Data-Oriented Design

`Los ítems con este formato hacen referéncia a aspectos en desarrollo o a referencias usadas.`
`Únicamente hay añadido el contenido en trabajo o finalizado. Es por este motivo que puede faltar algún punto.`

#### ***Autor: Raúl García Alcázar*** 
#### ***Tutor: Rafael González Fernández***
#### ***Grado: Grado en Diseño y Producción de Videojuegos.***
#### ***Universidad: TecnoCampus Mataró***

## Índice
```
1. Introducción
2. Objetivos
3. Análisis de referentes
    3.1. Xenobots
4. Marco teórico --- OK 
    4.1. Inteligencia Artificial --- OK 
        4.1.1. Computación Evolutiva
            4.1.1.1. Contexto
            4.1.1.2. Terminología
                4.1.1.2.1. Generación
                4.1.1.2.2. Genotipo y Fenotipo
                4.1.1.2.3. Población
                4.1.1.2.4. Evaluación y aptitud
                4.1.1.2.5. Operadores
            4.1.1.3. Entrenamiento y Aprendizaje
            4.1.1.4. Aplicación
                4.1.1.4.1. Algoritmo genético
        4.1.2. Red Neuronal
            4.1.2.1. Contexto
            4.1.2.2. Terminología
                4.1.2.2.1. Neurona y Perceptron
                4.1.2.2.1. Función de activación
                4.1.2.2.2. Capa
            4.1.2.3. Entrenamiento y Aprendizaje
            4.1.2.4. Aplicación
        4.1.3. Red Neuronal Evolutiva
            4.1.3.1. Contexto
            4.1.3.2. Terminología
            4.1.3.3. Entrenamiento y Aprendizaje
            4.1.3.4. Aplicación
    4.2. ¿Implementación?
        4.2.1. Data-Oriented Design 
            4.2.1.1. Contexto
                4.2.1.1. Arquitectura de un ordenador
                4.2.1.2. Paradigma
            4.2.1.2. Aplicación
                4.2.1.2.1. Array of Structs y Struct of Arrays
                4.2.1.2.2. Entity System o Entity Component System
        4.2.2. Unity3D
            4.2.2.1. Contexto
            4.2.2.2. Lenguaje C#
            4.2.2.3. Unity's Package Manager.
        4.2.3. Unity Data-Oriented Tech Stack (DOTS)
            4.2.3.1. Contexto
            4.2.3.2. ECS
                4.2.3.2.1. Archetypes
                4.2.3.2.2. ArchetypeChunk
                4.2.3.2.3. Entity Queries
            4.2.3.3. C# Job System   
            4.2.3.4. Burst Compiler 
            4.2.3.4. Otros paquetes
5. Diseño metodológico y cronograma
6. Resultados del trabajo
7. Conclusiones y reflexión
8. Bibliografía  
```

## 4. Marco teórico.
Este proyecto se centra en la implementación de conceptos de inteligencia artificial aplicando un paradigma de programación específico. Para entender el funcionamiento de dichos conceptos hay que disponer de nociones de inteligencia artificial y conceptos de desarrollo de software. 

Por ello, el capítulo se ha dividido en dos grandes secciones de interés. La primera sección, la inteligencia artificial, concreta y expone los campos en los que se centra el proyecto. La segunda y última sección, entra en detalle sobre las tecnologías usadas, arquitectura de un ordenador y el tipo de programación usada en la implementación del proyecto.


### 4.1. Inteligencia Artificial.
Para entender que es la inteligencia artificial (en adelante AI) hay que entender cada una de las palabras que componen el término.

Actualmente, no existe un consenso en la definición de inteligencia. Aún así, la gran mayoría de los autores actuales estan de acuerdo o se basan en la teória de las inteligencias múltiples (Gardner, 1983).

`Gardner, H. (1983) Multiple intelligences.`

Esta falta de consenso se puede observar en la definición aportada por la Real Academia Española (2020): "inteligencia: 1. Capacidad de entender o comprender. 2. Capacidad de resolver problemas. 3. Conocimiento, comprensión, acto de entender. 5. Habilidad, destreza y experiencia."

`Real Academia Española. (2020). Diccionario de la lengua española (23.4 ed.). Consultado en https://www.rae.es`

En este documento, se recoge la definición de inteligencia propuesta por Piaget (1963). La inteligencia es la capacidad de adaptarse. Entendiendo la adaptación como una palabra que agrupa varias de las definiciones aportadas anteriormente.

`Piaget, J. (1963) The Origins of Intelligence in Children`

Una vez definido el concepto de inteligencia, queda concretar a que se refiere el adjetivo artificial. Si se observa el diccionario de la lengua española, el concepto articial puede definirse como: no natural, falso o hecho por el hombre (RAE, 2020). 

`Real Academia Española. (2020). Diccionario de la lengua española (23.4 ed.). Consultado en https://www.rae.es`

Haciendo un ejercicio de comprensión, se pueden extraer tres posibles definiciones mediante la combinación de los conceptos:
1. La inteligencia artificial es la capacidad de adaptarse no natural.
1. La inteligencia artificial es la capacidad de adaptarse falsa.
1. La inteligencia artificial es la capacidad de adaptarse hecha por el hombre.

Estas definiciones en ningún caso son definiciones correctas pero permiten observar que el término artificial puede generar confusión, ya que por ejemplo, no se trata de una inteligencia falsa. De hecho, según John Haugeland (1989), el término más correcto para entender el concepto de inteligencia artificial es referirse a ella como inteligencia sintética.

`Haugeland, J. (1989) Artificial intelligence: The very idea.`

Para entender mejor a que se refiere por sintética se puede observar el siguiente ejemplo:
Una perla artificial es una perla falsa. Por lo tanto, no es una perla real. En cambio, una perla sintética no es natural pero si es una perla real (Poole, Mackworth & Goebel, 1998).

`Poole, D. Mackworth, A. Goebel,R. (1998) Computational Intelligence: A Logical Approach.`

Llegados a este punto, en el que se ha identificado que una AI es una inteligencia real, en este documento se recoge la definición proporcionada por Andreas Kaplan y Michael Haenlein (2019) que define la AI como la capacidad de un sistema para interpretar y aprender sobre datos externos y emplear el conocimiento aprendido para lograr tareas y metas a través de la adaptación.

`Kaplan, A. Haenlein, M. (2019) Siri, Siri, in my hand: Who’s the fairest in the land? On the interpretations, illustrations, and implications of artificial intelligence`

Se trata de una definición que engloba la definición de Piaget (1963) y lo situa en un entorno "computacional" al introducir el concepto de datos y sistema. 

`Piaget, J. (1963) The Origins of Intelligence in Children`

La AI se divide en varias ramas. En este documento, se describen diferentes técnicas de AI que pertenecen a la rama de inteligencia computacional. Rama que se dedica a crear sistemas inteligentes que pueden percibir y razonar sin mucha idea (a priori) de su entorno y producen mecanismos de control y adaptabilidad de una manera robusta (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

A continuación se describen dos campos de la inteligencia computacional: la computación evolutiva y la red neuronal. Finalmente, se detalla una técnica de AI que combina dichos campos para la creación del sistema computacional.

#### 4.1.1. Computación Evolutiva.
En este punto se describe en que consiste la computación evolutiva así como el algoritmo evolutivo. Primero se situa un contexto y punto de partida, seguido por una explicación de la terminología y el método de aprendizaje. Finalmente, se menciona el tipo de aplicación de algoritmo evolutivo usada en el desarrollo del proyecto.

##### 4.1.1.1. Contexto.
Para entender el campo de la computación evolutiva (en adelante EC), hay que entender a que se refiere con el término evolutiva.

Este término es usado con el mismo proposito que se utiliza en biología. Se trata de la evolución de las especies. Concretamente y de manera general, se basa en la evolución por selección natural definida por Charles Darwin (1859). 

Según Darwin, la selección natural tiene las siguientes premisas:
1. Los organismos se reproducen y los descendientes heredan las características de sus progenitores.
1. Los organismos han de presentar unas características diferenciadas o variables entre ellos.
1. Las diferencias en las características dan lugar a diferencias en la supervivencia y reproducción de los organismos.

De esta manera, si las premisas se repiten durante el transcurso de varias generaciones, se puede observar como ciertas características perduran en el tiempo y otras son eliminadas. Esta acumulación de cambios de características a lo largo de generaciones es a lo que se denomina evolución.

`Darwin, C. (1859) On the Origin of Species.`

En las ideas anteriores es en lo que se basa la computación evolutiva (EC). Por lo tanto, se puede definir la EC como la emulación del proceso de selección natural en un proceso de búsqueda (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

El término de búsqueda utilizado en la anterior definición es entendido como el proceso que se realiza para encontrar una solución a un problema concreto según un criterio de validación. Según lo que se observa con la evolución, los individuos más aptos (considerados los más próximos al criterio de validación) son los que perduran en el tiempo. Por lo tanto, se espera que en cada generación, los individuos más aptos sean más óptimos o igual de óptimos que la generación anterior. Por este motivo, la computación evolutiva es catalogada como un tipo de función de optimización (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Toda aplicación de la EC presenta lo que se conoce como algoritmo evolutivo (en adelante EA) pero con ciertas variaciones. A continuación se representa un ciclo del EA general.

![EA](./assets/AlgoritmoEvolutivo.PNG)
Algoritmo evolutivo.
`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`


##### 4.1.1.2. Terminología.
A continuación, se presenta la terminología general que presentan las aplicaciones del algoritmo evolutivo. Con los siguientes conceptos se puede entender mejor el AE representado en la figura anterior.

###### 4.1.1.2.1. Generación.
Una generación equivale a un ciclo entero del algoritmo evolutivo. Dispone del término generación debido a la connotación evolutiva que proporciona la herencia. Ya que, en cada ciclo, la población corresponde a la herencia del ciclo anterior.

###### 4.1.1.2.2. Genotipo y Fenotipo.
En la computación evolutiva (EC) se utilizan los términos biológicos de genotipo y fenotipo.

El genotipo describe la composición genética de un individuo y el fenotipo es la expresion de los rasgos en un entorno específico (Mendel, 1866). 

`Gregor, M. (1866). Versuche über Plflanzen-hybriden. Verhandlungen des naturforschenden Ver-eines in Brünn, Bd. IV für das Jahr 1865, Abhand-lungen, 3–47.`

A continuación, se puede observar una tabla en la que se puede apreciar de manera visual estos dos términos.

![Genotipo+Fenotipo](./assets/Flors_de_Mendel.svg.png)
Tabla de flores de Mendel.

`Genotip. (s.f.). En Wikipedia. Recuperado el 17 de abril de 2021 de https://ca.wikipedia.org/wiki/Genotip`

El genotipo es el conjunto de genes (B o b) y el fenotipo es la representación de rasgos que se observan, flores de diferentes colores. Observando el fenotipo de la flor blanca, podemos deducir su genotipo. En cambio, si se observa la flor de color, observamos que es más probable que disponga de un genotipo que otro, pero no es posible saber que genotipo dispone.

Si se analizan los términos a nivel de EC, se entiende el genotipo como la codificación de información de un individuo y el fenotipo como los individuos que forman las posibles soluciones en un contexto original del problema (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Según la aplicación del algoritmo evolutivo que se realize y según el problema a resolver, estos términos de los individuos, tienen mayor o menor peso en la implementación y se representan o codifican de manera diferente.

###### 4.1.1.2.3. Población.
La población es el conjunto de individuos utilizados en el transcurso del algoritmo evolutivo y de los que se acaba extrayendo un único individuo (fenotipo) como solución (Della et al, 2004).

`Della, A. De Stefano, C. Marcelli, A. (2004) On the role of population size and niche radius in fitness sharing.`

En cada generación, los individuos de la población son sustituidos por su herencia pero el número máximo de individuos es una constante establecida al inicio del proceso.

De hecho, al inicio de proceso hay que establacer dos aspectos de la población:
- Informar el número de individuos (tamaño de la población).
- Inicializar la población inicial.

El tamaño de la población es un aspecto importante en el rendimiento del algoritmo evolutivo. A nivel de variabilidad, cuanto mayor población mejor. La variabilidad ayuda a poder encontrar un fenotipo de éxito en menor tiempo (tiempo medido en generaciones). A nivel de tiempo de cálculo, cuanto mayor es la población, más calculos se han de realizar y por lo tanto puede convertirse en una tarea lenta y ineficiente. Por otro lado, si la población es demasiado pequeña, puede ser más rápida a nivel de cálculos, pero tardará más en encontrar un fenotipo de éxito (Federico, 2005). En 1975, Teniendo en cuenta el estado del hardware, DeJong comprobo que las poblaciones más eficaces eran entre 20 y 100 individuos (1975). 

`Federico, L. (2005) Entrenamiento de redes neuronales basado en algoritmos evolutivos.`

`DeJong, K. (1975). An Analysis of the Behavior of a Class of Genetic Adaptive Systems. PhD Dissertation, Department of Computer and Communication Sciences, University of Michigan, Ann Arbor.`

Sobre la inicialización, existen diferentes técnicas que se pueden utilizar como una inicialización manual, una uniforme para abarcar el espectro máximo de posibles fenotipos o de manera aleatoria (la más común) entre otras (Hidalgo & Turrado, 2011).

`Hidalgo, J. Turrado, J. (2011) Algoritmos genéticos: Aplicación al problema de la mochila.`

###### 4.1.1.2.4. Evaluación y aptitud.
Según se ha observado, el algoritmo se reproduce por generaciones. En cada generación, la población es modificada realizando una simulación de evolución genética y mediante la selección natural, los individuos más aptos son los que mayor herencia disponen.

Para seleccionar los individuos que se reproducen en la siguiente generación, hay que disponer de un criterio de rendimiento de los individuos (Siddique & Adeli, 2013). Según el objetivo del algoritmo evolutivo, se puede usar una función de evaluación o una función de aptitud.

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.`

Es común usar los conceptos de función de evaluación y función de aptitud como sinonimos, pero son distintos (Federico, 2005). 

`Federico, L. (2005) Entrenamiento de redes neuronales basado en algoritmos evolutivos.`

La función de evalución, provee una medida de optimización sobre un conjunto de parámetros. Indica que tan buena es una posible solución independientmente del resto de posibles soluciones (Whitley, 1994).

`Whitley, D. (1994). A genetic algorithm tutorial. Statistics and computing.`

Por el contrario, la función de aptitud indica que tan buena (o mala) es una posible solución en comparación con el resto de posibles soluciones (Federico, 2005).

`Federico, L. (2005) Entrenamiento de redes neuronales basado en algoritmos evolutivos.`

###### 4.1.1.2.5. Operadores.
En cada generación del algoritmo evolutivo (EA) se han de crear los nuevos individuos a través de la aplicación de operadores. Los operadores son aplicados mediante el orden definido en la siguiente lista de puntos.

**Selección**.
La selección consiste en la elección de unos individuos de la actual generación que serviran como base para la reproducción de la siguiente generación. La selección se puede realizar utilizando diferentes estrategias. Generalmente se utiliza una selección en base a la aptitud de los individuos. Existen otras estrategias como pueden ser la aleatoria, la ruleta y el elitismo entre otras (Siddique & Adeli, 2013). Ninguna estrategia es correcta o incorrecta, depende del dominio del problema a resolver, puede ser más adecuadop usar una u otra.

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

**Cruce**.
Una vez se ha realizado la selección de los individuos a reproducir, entra en acción la operación de cruce. Es esta operación la responsable de generar nuevos genotipos y por lo tanto, la responsable de que aparezcan nuevos fenotipos (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Existen tres clases de operaciones de cruce.
- Asexual. Cuando un solo individuo es utilizado para generar un nuevo individuo.
- Sexual. Cuando dos individuos son utilizados para generar un nuevo individuo.
- Multi-parent. Cuando más de dos individuos son utilizados para generar un nuevo individuo.

Para la realización de la nueva generación a través del cruce, se tienen presente dos parámetros necesarios:

- La probabilidad de cruce. Indica que tanto por ciento de la población se ha creado mediante el cruce de varios individuos. Por ejemplo, si el valor es un 60%, el 40% de la nueva población ha sido generada por un cruce asexual. En cambio, el otro 60%, ha sido creado mediante un cruce sexual o multi-parent.
- El punto de cruce. Punto en el que se define que genes del genotipo son cruzados. Pueden existir más de un punto de cruze en una misma operación de cruce.

En la siguiente figura se puede observar un ejemplo de cruze sexual con dos puntos de cruce.

![Cruce](./assets/AE_Cruce.PNG)

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

A nivel de genotipo y usando el ejemplo proporcionado por la figura anterior, se podria realizar la representación siguiente. Se trata de un genotipo binario con dos puntos de cruce.

![Cruce](./assets/AE_Cruce2.PNG)

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

El resultado del cruce es la definición de la nueva población. Una vez finalizado este operador, ya se dispone de todos los individuos de la nueva generación.

Existen otras formas de realizar el cruce que no consisten en unicamente seleccionar los genes del genotipo a cruzar. Algunas de ellas consisten en aplicar funciones aritméticas a genes concretos o al total de los genes (Siddique & Adeli, 2013) y otras por cruze binomial según la aptitud de los padres (Federico, 2005).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

`Federico, L. (2005) Entrenamiento de redes neuronales basado en algoritmos evolutivos`

**Mutación**.
La mutación consiste en realizar un cambio concreto en un gen de un individuo. Este cambio solo se produce a través de un procentaje de mutación. Este porcentaje, ha de poseer un valor muy pequeño (0.001%) para no convertir la nueva generación en una muestra aleatoria (DeJong, 1975).

`DeJong, K. (1975). An Analysis of the Behavior of a Class of Genetic Adaptive Systems. PhD Dissertation, Department of Computer and Communication Sciences, University of Michigan, Ann Arbor.`

Por ejemplo, si se dispone de un genotipo binario, la mutación suele consistir en cambiar el valor de un gen al valor opuesto.

![Cruce](./assets/AE_Mutacion.PNG)

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Existen diferentes formas de realizar cambios en los genes. Aplicar cambios de orden, aplicar operaciones matemáticas, invertir el signo del valor, ...

Una vez aplicado el operador de mutación, ya se dispone de una nueva generación de individuos diferentes a la anterior generación y es en este momento en el que se inicia de nuevo el ciclo de evaluación y aplicación de operadores sobre la población.

##### 4.1.1.3. Entrenamiento y Aprendizaje.
##### 4.1.1.4. Aplicación.
###### 4.1.1.4.1. Algoritmo genético.

## 8. Bibliografía.
Darwin, C. (1859) On the Origin of Species.

DeJong, K. (1975). An Analysis of the Behavior of a Class of Genetic Adaptive Systems. PhD Dissertation, Department of Computer and Communication Sciences, University of Michigan, Ann Arbor.

Della, A. De Stefano, C. Marcelli, A. (2004) On the role of population size and niche radius in fitness sharing.

Federico, L. (2005) Entrenamiento de redes neuronales basado en algoritmos evolutivos.

Gardner, H. (1983) Multiple intelligences.

Genotip. (s.f.). En Wikipedia. Recuperado el 17 de abril de 2021 de https://ca.wikipedia.org/wiki/Genotip

Gregor, M. (1866). Versuche über Plflanzen-hybriden. Verhandlungen des naturforschenden Ver-eines in Brünn, Bd. IV für das Jahr 1865, Abhand-lungen, 3–47.

Haugeland, J. (1989) Artificial intelligence: The very idea.

Hidalgo, J. Turrado, J. (2011) Algoritmos genéticos: Aplicación al problema de la mochila.

Kaplan, A. Haenlein, M. (2019) Siri, Siri, in my hand: Who’s the fairest in the land? On the interpretations, illustrations, and implications of artificial intelligence.

Piaget, J. (1963) The Origins of Intelligence in Children.

Poole, D. Mackworth, A. Goebel, R. (1998) Computational Intelligence: A Logical Approach.

Real Academia Española. (2020). Diccionario de la lengua española (23.4 ed.). Consultado en https://www.rae.es

Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing

Whitley, D. (1994). A genetic algorithm tutorial. Statistics and computing.