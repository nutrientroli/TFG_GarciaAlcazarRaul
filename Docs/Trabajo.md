
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
        4.1.1. Computación Evolutiva --- OK
            4.1.1.1. Contexto --- OK
            4.1.1.2. Terminología --- OK
                4.1.1.2.1. Generación --- OK
                4.1.1.2.2. Genotipo y Fenotipo --- OK
                4.1.1.2.3. Población --- OK
                4.1.1.2.4. Evaluación y aptitud --- OK
                4.1.1.2.5. Operadores --- OK
            4.1.1.3. Entrenamiento y Aprendizaje --- OK
            4.1.1.4. Aplicación --- OK
                4.1.1.4.1. Algoritmo genético --- OK
        4.1.2. Red Neuronal Artificial --- OK
            4.1.2.1. Contexto --- OK
            4.1.2.2. Terminología --- OK
                4.1.2.2.1. Neurona y Perceptron --- OK
                4.1.2.2.1. Función de activación --- OK
                4.1.2.2.2. Capa --- OK
            4.1.2.3. Entrenamiento y Aprendizaje --- OK
        4.1.3. Red Neuronal Artificial Evolutiva
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
Como se ha mencionado, los fenotipos son las potenciales soluciones de un problema concreto y las generaciones, son cada una de las iteraciones que evalúa unos nuevos fenotipos.

Con estos dos conceptos, se puede observar que el sistema en cada generación selecciona (mediante el operador de selección) las soluciones más óptimas respecto los demás fenotipos de su generación. Los fenotipos seleccionados sirven como base genética para crear la población de la siguiente generación (mediante operadoes de cruce y mutación).

Por lo tanto, en cada generación se encontrará generalmente una solución igual o más óptima que la generación anterior. Solo es cuestión de repetir el proceso hasta encontrar una solucción deseada.

##### 4.1.1.4. Aplicación.
Como se ha comentado anteriormente, existen diversas variaciones de aplicación del algoritmo evolutivo y este hecho da lugar a una distinción de estrategias a seguir según el propósito.

A continuación se listan las diferentes variaciones de aplicación que existen:
1. Algoritmo genético (Holland, 1975).
`Holland, J. (1975). Adaptation In Natural and Artificial Systems. University of Michigan Press, Ann Arbor.`
1. Programación evolutiva (Fogel, 1962).
`Fogel, L.J. (1962) Autonomous automata, Industrial Research, 4, 14–19.`
1. Estrategias de evolución (Rechenberg, 1965).
`Rechenberg, I. (1965) Cybernetic Solution Path ofan Experimental Problem, Royal Aircraft Establishment, Library Translation No. 1122, Farnborough, UK.`
1. Programación genética (Friedberg, 1958).
`Friedberg, R.M. (1958) A learning machine: Part I, IBM Journal ofResearch and Development, 2(1), 2–13.`
1. Evolución diferencial (Storn, 1995).
`Storn, R. (1995) Constrained optimization, Dr. Dobb’s Journal, May, pp. 119–123.`
1. Algoritmo cultural (Reynolds, 1994).
`Reynolds, R.G. (1994) Introduction to cultural algorithms. In Proceedings of the Third Annual Conference on Evolutionary Programming, A.V. Sebald and L.J. Fogel (eds), World Scientific, Singapore, pp. 131–139.`

De las diferentes aplicaciones, este documento solo desarrolla y expone el concepto de algoritmo genético. Variación del algoritmo evolutivo que se utiliza en el desarrollo de la parte práctica del proyecto.

###### 4.1.1.4.1. Algoritmo genético.
El algoritmo génetico (en adelante GA) se trata de la aplicación del algoritmo evolutivo (EA) más popular. Es introducido y desarrollado por John H. Holland (1975) y sus estudiantes (DeJong, 1975). 

`Holland, J. (1975). Adaptation In Natural and Artificial Systems. University of Michigan Press, Ann Arbor.`

`DeJong, K. (1975). An Analysis of the Behavior of a Class of Genetic Adaptive Systems. PhD Dissertation, Department of Computer and Communication Sciences, University of Michigan, Ann Arbor.`

Este algoritmo tiene dos aspectos que lo diferencian de la aplicacion de EA por defecto.
1. El concepto de la genética y estructuración de datos.
1. Se basa en una función de coste que evalua únicamente la aptitud de los fenotipos.

Sobre el concepto genética, el término "genético" de los GA proviene de la emulación de poblaciones mendelianas. Poblaciones basadas en los modelos de herencia y evolución genética definidos por Gregor Mendel (1866). Los individuos de la población se representan mediante cadenas de información similares a una estructura genética como los cromosomas (Whitley, 1994). 

`Gregor, M. (1866). Versuche über Plflanzen-hybriden. Verhandlungen des naturforschenden Ver-eines in Brünn, Bd. IV für das Jahr 1865, Abhand-lungen, 3–47.`

`Whitley, D. (1994). A genetic algorithm tutorial. Statistics and computing.`

Sobre la función de coste, GA se basa en una función de coste que evalua a cada individuo según sus características respecto a los demás. Este planteamiento difiere a otras aplicaciónes del EA en las que se precisa una descripción matemática del problema a optimizar (Goldberg, 1989).

`Goldberg, D. (1989). Genetic Algorithms in Search, Optimization& Machine Learning.`

El algoritmo genético se puede considerar una aplicación del algoritmo evolutivo espejo. Aplica estrictamente dicho algoritmo pero con unas pequeñas diferencias que lo distinguen. A continuación, se nombran las diferencias que identifican un algoritmo genético en base a la terminología usada en el algoritmo evolutivo.

**Genotipo y Fenotipo:** en el algoritmo genético el genotipo se expresa como una cadena de valores representando el concepto genetico de cromosoma. 

**Evaluación y Aptitud:** únicamente se realiza una función de aptitud respecto el resto de cromosomas.


Al solo aplicar una evaluación de aptitud en base a la población, se puede considerar al algoritmo genético como un proceso que desconoce el espacio del problema a resolver. Aún así, es capaz de encontrar una posible solución partiendo de la aleatoriedad. Esto lo convierte en un proceso útil en problemas en los que se desconoce como se han de resolver (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.`

#### 4.1.2. Red Neuronal Artificial.
En este punto se detalla el concepto de red neuronal artificial. Primero se situa un contexto y una visión de su historia. A continuación se describe la terminología y sus métodos de aprendizaje. Por último, se realiza una mención a las diferentes aplicaciones existentes.

##### 4.1.2.1. Contexto.
Una red neuronal artificial (en adelante ANN) es un análogo eléctrico de una red neuronal biológica (Siddique & Adeli, 2013). 

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.`

La red neuronal biológica esta compuesta por un conjunto de neuronas. Cada neurona posee un soma (input) y un axón (output). Además, las uniones entre neuronas siempre siguen un patrón de unión entre el axón de una primera neurona y el soma de una segunda. De esta manera, las neuronas estan conectadas entre si y cuando existe un impulso eléctrico, este impulso recorre las neuronas según las conexiones existentes (McCulloch & Pitts, 1943).

`McCulloch, W.S. and Pitts, W.H. (1943) A logical calculus of the ideas imminent in nervous activity, Bulletin of Mathematical Biophysics, 5, 115–133.`

![Cruce](./assets/Neurona.PNG)

Representación de neurona biológica

`Salman, A. (2009) An Open Domain-Extensible Environment for Simulation-Based Scientific Investigation (ODESSI).`

En la figura anterior, se observa la representación de una neurona biológica. Permite observar que disponen de ramificaciones en los puntos de conexión y es que las conexiones entre neuronas no tienen una relación de una a una, sinó que un soma puede estar conectado con múltipes axones de otras neuronas y un axón puede estar conectado con múltiples somas de otras neuronas.

La primera implementación de red neuronal artificial fue creada por Warren McCulloch y Walter Pitts. Modelaron una ANN simple mediante circuitos eléctricos y diseñaron la neurona artificial presente en la siguiente figura (McCulloch & Pitts, 1943).

`McCulloch, W.S. and Pitts, W.H. (1943) A logical calculus of the ideas imminent in nervous activity, Bulletin of Mathematical Biophysics, 5, 115–133.`

![Cruce](./assets/Neurona2.PNG)

Neurona del modelo McCulloch y Pitts

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.`

El funcionamiento del modelo representado en el diagrama anterior es el siguiente:
- "X" es el valor de entrada. Existen múltiples valores de entrada binarios (0 o 1) y los valores van variando durante la ejecución.
- "W" es el valor de peso de la entrada. Define que importancia tiene la entrada según la neurona y es definido en el diseño de la neurona. El valor es fijo durante la ejecución.
- "T" es el valor de umbral que ayuda a definir el valor de salida y es definido en el diseño de la neurona. El valor es fijo durante la ejecución.
- "O" es el valor de salida. Una única salida de valor binario y el valor va variando durante la ejecución.

Teniendo en cuenta las aclaraciones anteriores, se puede realizar una representación matemática. Esta representación se visualiza em la siguiente figura. 

![Cruce](./assets/Neurona2_mat.PNG)

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.`

Como se puede observar, este modelo planteado únicamente reproduce la comunicación entre neuronas, pero es un modelo que no es capaz de aprender. Quien diseña el modelo define como funciona y este no varia. 

Es aquí donde entró Donald Hebb y introdujo un esquema de aprendizaje que utilizaba las neuronas como herramienta en donde guardar la información aprendida (Hebb, 1949). Este aprendizaje consiste en modificar los valores de los pesos en las conexiones para alterar el resultado final.

`Hebb, D.O. (1949) The Organization ofBehavior: A Neuropsychological Theory, John Wiley, New York.`

Unos años más tarde se introdujo un nuevo modelo de neurona que añadió un nuevo elemento de corrección a posibles errores. Se introdujo el concepto de "bias" a la equación (Rosenblatt, 1950). Además, durante la época en la que se propuso este nuevo modelo, hubo un cambio de terminología y se empezo a usar el término de perceptron.

`Rosenblatt, F. (1958) The perceptron: a probabilistic model for information storage and organisation in the brain, Psychology Review, 65, 386–408.`

Con la introducción del nuevo elemento, se puede observar una modificación de las equaciones y esquema anteriores.

![Cruce](./assets/Neurona3.PNG)

Percerptron Rosenblatt

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.`

Hasta los años 80, el interés general sobre la investigación y uso de redes neuronales era muy bajo debido a que el perceptron era un modelo muy limitado, no era capaz de resolver funciones no-lineales (Minsky and Papert, 1969). Todo cambió cuando John Hopfield presento un paper en donde demostraba el uso potencial de las redes neuronales para dispositivos reales (Hopfield, 1982). 

`Minsky, M. and Papert, S. (1969) Perceptrons, MIT Press, Cambridge, MA.`

`Hopfield, J.J. (1982) Neural networks and physical systems with emergent collective computational abilities, Pro- ceedings ofNational Academy ofSciences, 79, 2554–2558.`

Después del interés despertado por Hopfield, se realizaron o se descrubrieron trabajos de investigación que reconfigurarían las ANN a nivel de estructura, a nivel de aprendizaje y a nivel de optimización. Aquí se puede destacar una investigación que sucedió antes de los años 80 pero paso desapercibida. Se trata del aprendizaje de propagación hacia atrás (Werbos, 1974). Actualmente, uno de los métodos de aprendizaje de redes neuronales más usados.

`Werbos, P.J. (1974) Beyond regression: new tools for prediction and analysis in the behavioural sciences, Doctoral Dissertation, Applied Mathematics, Harvard University.`

Actualmente el modelo general de una ANN esta representado por la siguiente figura. Se trata de modelo perceptron multicapa.

![Cruce](./assets/Neurona5.PNG)

Perceptron multicapa

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.`


##### 4.1.2.2. Terminología.
A continuación se detalla la terminología usada en las ANN y se oberva como es el modelo actual de red neuronal artificial general, entrando en detalle en cada concepto del perceptron multicapa.

###### 4.1.2.2.1. Neurona y Perceptron.
La neurona o Perceptron es un elemento de procesamiento (Yao, 1999). La modelo actual de la neurona presenta la siguiente representación.

`Yao, X. (1990) Evolving artificial neural networks` 

![Cruce](./assets/Neurona4.PNG)

Perceptron

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

El modelo actual es prácticamente el mismo que el presentado por Rosenblatt (1958), pero con la evolución de las redes neuronales, se ha definido de forma diferente algun concepto para una mayor abstracción y mejor flexibilidad. De hecho, el elemento más diferenciador entre los dos modelos es la identificación de la función de activación ( ***f(.)*** ).

`Rosenblatt, F. (1958) The perceptron: a probabilistic model for information storage and organisation in the brain, Psychology Review, 65, 386–408.`

Con este nuevo concepto identificado, las equaciones matemáticas también han variado en cierta medida. A continuación se observa el proceso matemático que sigue una neurona para obtener su valor de salida. 

![Cruce](./assets/funcionActivacion2.PNG)

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Primero se calcula el valor de salida sin aplicar la función de activación aplicando una suma ponderada y aplicando una desviación de umbral. Posteriormente, se aplica la función de activación.

![Cruce](./assets/funcionActivacion3.PNG)

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

El valor resultante de la función de activación, es el valor que recibirà la siguiente neurona situada en la siguiente capa.

###### 4.1.2.2.1. Función de activación.
La función de activación permite definir el tipo de salida de una neurona (lineal o no-lineal). Este concepto existía desde el primer modelo de neurona (McCulloch & Pitts, 1943) y también estaba presente en el modelo de perceptron de Rosenblatt (1958). Estos modelos usaban una función de activación del tipo escalón.

`McCulloch, W.S. and Pitts, W.H. (1943) A logical calculus of the ideas imminent in nervous activity, Bulletin of Mathematical Biophysics, 5, 115–133.`

`Rosenblatt, F. (1958) The perceptron: a probabilistic model for information storage and organisation in the brain, Psychology Review, 65, 386–408.`

A continuación se muestran las funciones de activación más típicas.

![Cruce](./assets/funcionActivacion.PNG)

`Nacelle, A. (2009) Redes neuronales artificiales.`

Como se menciona anteriormente, los modelos iniciales ya presentaban el concepto de función de activación y concretamente la función de escalón (0 o 1 como valor). El uso de esta función fue debido al medio en el que se diseñaron los modelos. Se trata de una representación de circuito eléctrico en donde el valor "0" corresponde a que no hay impulso y el valor "1" a que hay impulso eléctrico. 

Esta función de activación de escalón, fue una de las limitaciones que se detectaron en los años 60. Matemáticamente, un conjunto de equaciones lineales dan como resultado una única ecuación lineal. Por lo que aunque se añadieran neuronas, el modelo siempre se podía simplificar en una única neurona (Minsky and Papert, 1969). Con la introducción de funciones no-lineales, esta limitación se remedió y a día de hoy permiten obtener resultados complejos medianto la combinación de neuronas y sus correspondientes funciones de activación.

`Minsky, M. and Papert, S. (1969) Perceptrons, MIT Press, Cambridge, MA.`

###### 4.1.2.2.2. Capa.
Una capa es una medio de agrupación de neuronas. Cada capa puede disponer de como mínimo una neurona y no existe un número determinado como máximo. Además, el resultado de las neuronas de cada capa es conectado con cada una de las neuronas de la siguiente capa (Nacelle, 2009). Existen variaciones en donde puede existir la no conexión entre algunas neuronas de capas contiguas, pero en términos generales, todas se conectan.

`Nacelle, A. (2009) Redes neuronales artificiales.`

En toda ANN existen mínimo dos capas. La capa de entrada y la capa de salida. Como su nombre indica, son las capas que se relacionan con aspectos externos. La primera recibe una série de datos y la segunda es la que comunica el resultado de esos datos procesados (Siddique & Adeli, 2013). Internamente, la red puede disponer de las denominadas capas ocultas. El número de capas ocultas depende del diseño que uno quiera realizar.

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

![Cruce](./assets/ANN_Capas.PNG)

`Alvarado, M. Meneses-Bautista, F.D. (2017). Pronóstico del tipo de cambio USD/MXN con redes neuronales de retropropagación.`

El número de neuronas por capas es un número definido por el que diseña el modelo. Entiendiendo las neuronas como unidades de procesamiento (Yao, 1999), según el problema a resolver puede interesar disponer de más o menos neuronas, ya que que cada neurona puede llegar a especializarse en un ámbito del problema concreto.

`Yao, X. (1990) Evolving artificial neural networks`

Esta especialización en ningún caso es planteada en el diseño de la ANN. Se realiza una vez se ha entrenado la red.

##### 4.1.2.3. Entrenamiento y Aprendizaje.
El aprendizaje de una ANN es un procedimiento que modifica los pesos de las conexiones y la desviación del umbral de las neuronas. Este procedimiento es denominado entrenamiento y consiste en forzar a una red para dar un respuesta concreta a una entrada de datos específica (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Existen muchos procesos de aprendizaje, pero se pueden agrupar en dos tipos de aprendizaje:
- Aprendizaje supervisado
- Aprendizaje no supervisado

El aprendizaje supervisado consiste en proporcionar al modelo los datos de entrada y salida que se espera obtener con el procesamiento de la red. Una vez obtenido el valor proporcionado con la red, se compara con el objetivo y si existen diferencias de valores, se ajustan los pesos para aproximarse al resultado objetivo(Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Respecto al aprendizaje no supervisado, se refiere al aprendizaje que no conoce el valor objetivo. Al no conocerse la información sobre si es correcto o incorrecto, el modelo busca regularidades, patrones o tendencias para ajustar sus pesos (Siddique & Adeli, 2013).

`Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing`

Existen diferentes técnicas para realizar cada uno de los aprendizajes mencionados. De entre ellas, se puede destacar al aprendizaje mediante la propagación hacia atrás (Backpropagation) que introdujo Werbos (1974). Se trata de un algoritmo de aprendizaje supervisado que optimiza el proceso de reconfiguración de la red neuronal respecto a otros procesos. En vez de recorrer cada una de las opciones posibles a través de las neuras para configurar sus pesos, realiza el mínimo recorrido necesario según el peso que a tenido una neurona en el error encontrado.

`Werbos, P.J. (1974) Beyond regression: new tools for prediction and analysis in the behavioural sciences, Doctoral Dissertation, Applied Mathematics, Harvard University.`

## 8. Bibliografía.
Darwin, C. (1859) On the Origin of Species.

DeJong, K. (1975). An Analysis of the Behavior of a Class of Genetic Adaptive Systems. PhD Dissertation, Department of Computer and Communication Sciences, University of Michigan, Ann Arbor.

Della, A. De Stefano, C. Marcelli, A. (2004) On the role of population size and niche radius in fitness sharing.

Federico, L. (2005) Entrenamiento de redes neuronales basado en algoritmos evolutivos.

Fogel, L.J. (1962) Autonomous automata, Industrial Research, 4, 14–19.

Friedberg, R.M. (1958) A learning machine: Part I, IBM Journal ofResearch and Development, 2(1), 2–13.

Gardner, H. (1983) Multiple intelligences.

Genotip. (s.f.). En Wikipedia. Recuperado el 17 de abril de 2021 de https://ca.wikipedia.org/wiki/Genotip

Gregor, M. (1866). Versuche über Plflanzen-hybriden. Verhandlungen des naturforschenden Ver-eines in Brünn, Bd. IV für das Jahr 1865, Abhand-lungen, 3–47.

Goldberg, D. (1989). Genetic Algorithms in Search, Optimization& Machine Learning.

Haugeland, J. (1989) Artificial intelligence: The very idea.

Hebb, D.O. (1949) The Organization ofBehavior: A Neuropsychological Theory, John Wiley, New York.

Hidalgo, J. Turrado, J. (2011) Algoritmos genéticos: Aplicación al problema de la mochila.

Holland, J. (1975). Adaptation In Natural and Artificial Systems. University of Michigan Press, Ann Arbor.

Hopfield, J.J. (1982) Neural networks and physical systems with emergent collective computational abilities, Pro- ceedings ofNational Academy ofSciences, 79, 2554–2558.

Kaplan, A. Haenlein, M. (2019) Siri, Siri, in my hand: Who’s the fairest in the land? On the interpretations, illustrations, and implications of artificial intelligence.

Minsky, M. and Papert, S. (1969) Perceptrons, MIT Press, Cambridge, MA.

McCulloch, W.S. and Pitts, W.H. (1943) A logical calculus of the ideas imminent in nervous activity, Bulletin of Mathematical Biophysics, 5, 115–133.

Nacelle, A. (2009) Redes neuronales artificiales.

Piaget, J. (1963) The Origins of Intelligence in Children.

Poole, D. Mackworth, A. Goebel, R. (1998) Computational Intelligence: A Logical Approach.

Real Academia Española. (2020). Diccionario de la lengua española (23.4 ed.). Consultado en https://www.rae.es

Rechenberg, I. (1965) Cybernetic Solution Path ofan Experimental Problem, Royal Aircraft Establishment, Library Translation No. 1122, Farnborough, UK.

Reynolds, R.G. (1994) Introduction to cultural algorithms. In Proceedings of the Third Annual Conference on Evolutionary Programming, A.V. Sebald and L.J. Fogel (eds), World Scientific, Singapore, pp. 131–139.

Rosenblatt, F. (1958) The perceptron: a probabilistic model for information storage and organisation in the brain, Psychology Review, 65, 386–408.

Salman, A. (2009) An Open Domain-Extensible Environment for Simulation-Based Scientific Investigation (ODESSI).

Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing.

Storn, R. (1995) Constrained optimization, Dr. Dobb’s Journal, May, pp. 119–123.

Werbos, P.J. (1974) Beyond regression: new tools for prediction and analysis in the behavioural sciences, Doctoral Dissertation, Applied Mathematics, Harvard University.

Whitley, D. (1994). A genetic algorithm tutorial. Statistics and computing.

Yao, X. (1990) Evolving artificial neural networks.

