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

Genotipo: 0000000000 0000000000     
fenotipo: punto (-5.12, -5.12)   
valor de f(x) o aptitud: f(-5.12, -5.12)=52.4288

y

Genotipo: 1111111111 1111111111     
fenotipo: punto (5.12, 5.12)   
valor de f(x) o aptitud: f(5.12, 5.12)=52.4288


Para las pruebas se fijó la probabilidad de mutación a 0.001 y la probabilidad de cruce a 0.3, variando la población, y obteniendo los siguientes resultados:


POBLACIÓN	 GENERACIONES	FITNESS/FENOTIPO	TIEMPO
11	       590	        0,001	            0,0156 Segs. 
121		     6	          0,005	            0,0156 Segs. 
1331		   2	          0,0073	          0,0000 Segs.,
2049		   5	          0,0025	          0,0156 Segs.
4097		   3	          0,0041	          0,0156 Segs.
8193		   1	          0,0036	          0,0156 Segs.
16385		   1	          0,0034	          0,0624 Segs.
32769		   1	          0,0004	          0,1093 Segs.
65537		   1	          0,0002	          0,1874 Segs.
131073		 1	          0,0002	          0,3758 Segs.


Es evidente que con los valores fijados, manteniendo la probabilidad de mutación y cruce, lo primero que observamos es que 
para obtener una dierencia en el tiempo de ejecución nos debemos ir a valores de población muy altos, con poblaciones oscilando 
entre los 11 individuos y los 8193, el tiempo de ejecución era muy similar, variando a partir del 5 o 5 decimal (el caso de la
población de 1331 es anecdótico, si repitiéramos esa ejecución múltiples veces acabaría acercándose el tiempo a la de las demás).

Lo segundo que vemos es que conforme aumenta el tamaño de la pobación es más fácil que el mejor individuo se encuentre en la primera población, ya  a apartr de una población de 8193 individuos, no encontré nunca el mejor individuo fuera de la población inicial, siendo significativo el salto entre una población con 11 individuos y una con 121, pasando de unas 590 generaciones a 6 generaciones, el fitness/fenotipo vemos el valor que tendría en un punto dado (que también facilita por pantalla el programa) y que nos sírve para situarlo en la gráfica que se obtiene en el archivo. Lo intereante es que mientras al principio vemos como va tomando valores más elevados hasta que llega a un cierto tamaño de población, luego al ir incrementando este, comienza a descender, hasta que llega a un punto en que se mantiene practicamente constante.

Variando la probabilidad de cruce y mutación, se obtienen resultados diferentes, evidentemente.
