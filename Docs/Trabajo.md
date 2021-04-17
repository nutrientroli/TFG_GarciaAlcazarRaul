
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
                4.1.1.2.1. Genotipo y Fenotipo
                4.1.1.2.2. Población
                4.1.1.2.3. Evaluación y aptitud
                4.1.1.2.4. Operadores
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

# 8. Bibliografía.
Gardner, H. (1983) Multiple intelligences.
Haugeland, J. (1989) Artificial intelligence: The very idea.
Kaplan, A. Haenlein, M. (2019) Siri, Siri, in my hand: Who’s the fairest in the land? On the interpretations, illustrations, and implications of artificial intelligence
Piaget, J. (1963) The Origins of Intelligence in Children
Poole, D. Mackworth, A. Goebel, R. (1998) Computational Intelligence: A Logical Approach.
Real Academia Española. (2020). Diccionario de la lengua española (23.4 ed.). Consultado en https://www.rae.es
Siddique, N. & Adeli, H. (2013) Computational Intelligence: Synergies of Fuzzy Logic, Neural Networks and Evolutionary Computing
