## Practica Final ##

Documentación de la práctica final.

### Licencia ###

Distribuída bajo licencia GPLv3.

### Objetivo ###
Se ha realizado una librería para la gestión de poblaciones necesaria para la creación de un algoritmo genético base. 

En la raíz de la práctica encontrareis una estructura similar a esta:

- .travis.yml (librerías específicas para la práctica, referentes a árboles).
- Informacion.md (Memoria de la práctica).
- LICENSE (Licencia libre GNU de este programa).
- README.md (Descripción del repositorio).
- prueba.xml (archivo con los datos a psar al AG).
- algoritmo_genetico.cpp (código en C++ del AG).
-  Pruebas AG.ods (Resultado de las pruebas).


### Descripción del AG ###

En este programa se ha intentado realizar un programa para minimizar la función definida como:

- f(x) = Sumatoria desde i=0 hasta N. de (X sub i) elevado al cuadrado.

En donde X = {X sub 1,X sub 2,.....,X sub N} y x tomo valores en el intervalo [-5.12, 5.12]. El valor de N será 2, para que la función sea bidimensional. Para codificar cada varibale x sub i, usamos 10 bits, por lo que solo podemos representar 1024 puntos. 

Para implementar el AG se ha utilizado una selección por torneos de 2, cruce en un punto. PArando el AG cuando f(x) < 1*10 elevado a -2. Usamos elitismo de un individuo. Con idea de facilitar los cálculs del programa, se recomienda usar poblaciones impares. Ejemplo: Con una población de 11 individuos, selecciona 10 para cruzar, estos 10 generan 10 hijos, que serán mutados (o no) facilitándonos una población de 10 individuos, a la que añadimos el mejor individuo de la población anterior.

Los parámetros que podemos variar son:

- Población.
- Probabilidad de cruce.
- Probabilidad de mutción.

El código es comentado por funciones para que se pueda ver que hace cada una, se añadieron funciones para imprimir en archivo ficheros de puntos, usados en GNUPLOT para dibujar gráficas, así como para imprimir por pantalla el genotipo asociado a un indiviuo que se le pasa como parámetro. Estas funciones no están activadas en el programa, añadiendo la llamada correspondiente en el código del programa se mostrarán. Se dejan desactivadas debido al tiempo que se toma en escribir el archivo con poblaciones grandes.

Dado que es una función bidimensional, y que la fun´ción está definida en unos límites fijados, tendremos un rango de soluciones que oscilará entre los siguientes valores:

- Genotipo: 0000000000 0000000000
- fenotipo: punto (-5.12, -5.12)
- valor de f(x) o aptitud: f(-5.12, -5.12)=52.4288

y

- Genotipo: 1111111111 1111111111
- fenotipo: punto (5.12, 5.12)
- valor de f(x) o aptitud: f(5.12, 5.12)=52.4288

Para las pruebas se fijó la probabilidad de mutación a 0.001 y la probabilidad de cruce a 0.3, variando la población, y obteniendo los siguientes resultados:


<table>
<thead><tr>
<th>POBLACIÓN</th>
<th>GENERACIONES</th>
<th>FENOTIPO</th>
<th>TIEMPO</th>
</tr></thead>
<tbody>
<tr>
<td>11</td>
<td>590</td>
<td>0.001</td>
<td>0.0156 seg.</td>
</tr>
<tr>
<td>121</td>
<td>6</td>
<td>0.005</td>
<td>0.0156 seg.</td>
</tr>
<tr>
<td>1331</td>
<td>2</td>
<td>0.0073</td>
<td>0.0000 seg.</td>
</tr>
<tr>
<td>2049</td>
<td>5</td>
<td>0.0025</td>
<td>0.0156 seg.</td>
</tr>
<tr>
<td>4097</td>
<td>3</td>
<td>0.0041</td>
<td>0.0156 seg.</td>
</tr>
<tr>
<td>8193</td>
<td>1</td>
<td>0.0036</td>
<td>0.0156 seg.</td>
</tr>
<tr>
<td>16385</td>
<td>1</td>
<td>0.0034</td>
<td>0.0624 seg.</td>
</tr>
<tr>
<td>32769</td>
<td>1</td>
<td>0.0004</td>
<td>0.1093 seg.</td>
</tr>
<tr>
<td>65537</td>
<td>1</td>
<td>0.0002</td>
<td>0.1874 seg.</td>
</tr>
<tr>
<td>131073</td>
<td>1</td>
<td>0.0002</td>
<td>0.3758 seg.</td>
</tr>
</tbody>
</table>


Es evidente que con los valores fijados, manteniendo la probabilidad de mutación y cruce, lo primero que observamos es que para obtener una diferencia en el tiempo de ejecución nos debemos ir a valores de población muy altos, con poblaciones oscilando entre los 11 individuos y los 8193, el tiempo de ejecución era muy similar, variando a partir del 5 o 6 decimal (el caso de la población de 1331 es anecdótico, si repitiéramos esa ejecución múltiples veces acabaría acercándose el tiempo a la de las demás).

Lo segundo que vemos es que conforme aumenta el tamaño de la población es más fácil que el mejor individuo se encuentre en la población inicial, a partir de una población de 8193 individuos, no encontré nunca el mejor individuo fuera de la población inicial, siendo significativo el salto entre una población con 11 individuos y una con 121, pasando de unas 590 generaciones a 6 generaciones, el fitness/fenotipo vemos el valor que tendría en un punto dado y que nos sirve para situarlo en la gráfica que se obtiene en el archivo. Lo interesante es que mientras al principio vemos como va tomando valores más elevados hasta que llega a un cierto tamaño de población, luego al ir incrementando este, comienza a descender, hasta que llega a un punto en que se mantiene prácticamente constante.

El archivo Puntos.dat generado por el programa y visualizado con GNUplot es el siguiente:

<p>
  <a href="https://github.com/Investigador/Practica-Final/grafico.png" target="_blank">
    <img src="https://github.com/Investigador/Practica-Final/grafico.png" alt="Grafica generada en archivo Puntos.dat" style="max-width:100%;">
  </a>
</p>

![Gráfica](c:\Users\Sofia\SkyDrive\Documentos\grafico.png "Gráfica")

### Comentarios Finales ###

Es un algoritmo genético muy simple, que espero haber realizado correctamente, ya que es mi primer algoritmo genético y nunca había realizado nada de este tipo, al principio pensé en tomar los valores de un archivo de texto, hasta que vi el ejercicio del compañero Juanjo, del que tomé la manera de leer los archivos de un fichero .xml, que me pareció más elegante y correcto que lo que yo mismo había realizado (la parte del código de lectura del archivo xml está basada en su código).

En Junio de 2014 Alfonso Soto García
