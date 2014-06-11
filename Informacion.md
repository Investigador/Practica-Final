Información de la práctica

En esta práctica, distribuída bajo licencia GPLv3, se ha realizado una librería para la gestión de  poblaciones necesaria para la
creación de un algoritmo genético base. 
En la raíz de la práctica encontrareis una estructura similar a esta:

• .travis.yml                (librerías específicas para la práctica, referentes a árboles).

• Informacion.md             (Memoria de la práctica).

• LICENSE                    (Licencia libre GNU de este programa).

• README.md                  (Descripción del repositorio).

• prueba.xml                 (archivo con los datos a psar al AG).

• algoritmo_genetico.cpp     (código en C++ del AG).

• Pruebas AG.ods             (Resultado de las pruebas).


En este programa se ha intentado realizar un programa para minimizar la función definida como:

f(x) = Sumnatoria desde i=0 hasta N. de (X sub i) elevado al cuadrado.

En donde X = {X sub 1,X sub 2,.....,X sub N} y x tomo valores en el intervalo [-5.12, 5.12]. El valor de N será 2, para que la función sea bidimensional.
Para codificar cada varibale x sub i, usamos 10 bits, por lo que solo podemos representar 1024 puntos. 

Para implementar el AG se ha utilizado una selección por torneos de 2, cruce en un punto. PArando el AG cuando f(x) < 1*10 elevado a -2. Usamos elitismo de un individuo.
Con idea de facilitar los cálculs del programa, se recomienda usar poblaciones impares.
Ejemplo:
Con una población de 11 individuos, selecciona 10 para cruzar, estos 10 generan 10 hijos, que serán mutados (o no) facilitándonos una población de 10 individuos, a la que añadimos el mejor individuo de la población anterior.

Los parámetros que podemos variar son:

• Población.

• Probabilidad de cruce.

• Probabilidad de mutación.

El resto de parámetros están fijos.

El código es comentado por funciones para que se pueda ver que hace cada una, se añadieron funciones para imprimir en archivo 
ficheros de puntos, usados en GNUPLOT para dibujar gráficas, así como para imprimir por pantalla el genotipo asociado a un indiviuo que se le pasa como parámetro. Estas funciones no están activadas en el programa, añadiendo la llamada correspondiente
en el código del programa se mostrarán. Se dejan desactivadas debido al tiempo que se toma en escribir el archivo con poblaciones grandes.

Dado que es una función bidimensional, y que la fun´ción está definida en unos límites fijados, tendremos un rango de soluciones que oscilará entre los siguientes valores:

Genotipo: 0000000000 0000000000     fenotipo: punto (-5.12, -5.12)   valor de f(x) o aptitud: f(-5.12, -5.12)=52.4288
y
Genotipo: 1111111111 1111111111     fenotipo: punto (5.12, 5.12)   valor de f(x) o aptitud: f(5.12, 5.12)=52.4288

