# Clase 2

## ¿Qué es la computación?

- Processing
- Modo estático
- Comentarios
- Coordenadas cartesianas: pixel coordinates

Ejecución de Processing, PDE, sketches. 

Variables, coloreado del código y componentes de un sketch de Processing.

## Funciones (en processing)

Las funciones son los los bloques basicos para construir programas en Processing. 

Algunas de ellas son *size()* *line()* *fill()* 

La modularidad es una de las características más importantes de las funciones en Processing. Son unidades de software independientes que pueden ser usadas para construir programas más complejos. 

Más adelante aprenderemos a escribir funciones para extender las capacidades de Processing más allá de sus características incorporadas. 

Imprimir en la consola. 

### Sistema de coordenadas

Recordemos que la pantalla de una computadora es una cuadrícula de elementos que emiten luz llamados pixeles.

Escribimos las coordenadas de un pixel de la siguiente manera: (x, y)

Si invocamos una pantalla de 200x200 pixeles, la esquina superior izquierda es el origen, o sea (0, 0) y la esquina inferior derecha es (199, 199)

¿En este ejemplo, qué coordenadas tendría el centro? 

### Formas

Mientras tanto, recordemos las formas básicas 

`line(x1, y1, x2, y2)`

Ejemplo: 

```java
size(480, 120);
line(20, 50, 420, 110);
```

Rectángulos...

`rect(x, y, anchura, altura)`

```java
// Dibujar un rectángulo con punto inicial en (180, 60), ancho de 220 y alto de 40
size(480, 120);
rect(180, 60, 220, 40);
```
Círculos...

`ellipse(x, y, width height)` 

```java
size(480, 120);
ellipse(278, -100, 400, 400);
```

Otras formas son: `triangle, quad` y `arc.` 

El sistema de coordenadas inicia arriba y a la izquierda ¿Por qué?

El orden de las instrucciones importa, en este ejemplo el rectángulo se dibuja encima del círculo debido a que aparece después en el código.

```java
size(480, 120);
ellipse(140, 0, 190, 190);
rect(160, 30, 260, 20);
```

En este otro, la elipse se encuentra encima debido a que aparece después 

```java
size(480, 120);
rect(160, 30, 260, 20);
ellipse(140, 0, 190, 190);
```

## Color

Hasta el momento hemos dibujado formas en blanco y negro y el fondo de la ventana se ha mantenido en gris claro. 

Para cambiar esto vamos a utilizar las funciones `background()` `fill` y `stroke`. 

Los valores de los parámetros tienen el rango de 0 a 255, donde 255 es blanco, 128 es un gris medio y 0 es negro. 

El siguiente ejemplo muestra tres diferentes valores en circulos que están sobre un fondo negro. 

```java
size(480, 120);
background(0); // negro
fill(204); // gris claro
ellipse(132, 82, 200, 200); // círculo gris claro
fill(153); // gris medio 
ellipse(228, -16, 200, 200); // círculo gris medio
fill(102); // gris oscuro
ellipse(268, 118, 200, 200); círculo gris oscuro
```

Es posible deshabilitar el contorno y el relleno con `noStroke()` y `noFill()`. 

```java
size(480, 120);
fill(153);
ellipse(132, 82, 200, 200);
noFill();
ellipse(228, -16, 200, 200);
noStroke();
ellipse(268, 118, 200, 200);
```

Si queremos usar valores más allá de la escala de grises, podemos usar tres parámetros para especificar los componentes de un color (rojo, verde y azu). 

```java
size(480, 120);
noStroke();
background(0, 26, 51);
fill(255, 0, 0);
ellipse(132, 82, 200, 200);
fill(0, 255, 0);
ellipse(228, -16, 200, 200);
fill(0, 0, 255);
ellipse(268, 118, 200, 200);
```

La definición de un color con la convención RGB proviene de la manera en que la computadora define colores en la pantalla. 

Los valores RGB se pueden definir en un rango que va de 0 a 255. 

Hay un cuarto valor que se puede utilizar para definir un valor de color. El valor alpha define transparencia. 

Este valor, como los que hemos visto hasta el momento, puede ir de 0 a 255 donde 0 define un color completalmente transparente y 255 un color completamente opaco. 

```java
size(480, 120);
noStroke();
background(204, 226, 225);
fill(255, 0, 0, 160);
ellipse(132, 82, 200, 200);
fill(0, 255, 0, 160);
ellipse(228, -16, 200, 200); 
27fill(0, 0, 255, 160);
ellipse(268, 118, 200, 200);
```
Otras formas de definir el color. 

## Aleatoriedad

Las computadoras pueden generar valores y comportamientos líneales muy facilmente. Sin embargo, el mundo físico se comporta de maneras diversas, muchas veces alejadas de ese comportamiento lineal. 

Es posible simular comportamientos y cualidad inpredecibles al generar números aleatorios. 

En Processing, una función que puede realizar esto es la función `random()` 

Antes de dibujar...

```java
float r = random(0, mouseX);
println(r);
```

El ejemplo anterior imprime valores aleatorios en la Consola, en un rango que está limitado por la posición del mouse en el eje X. 

La función `random()` siempre devuelve un valor de punto flotante. Hay que asegurarse que la variable declarada sea un número de punto flotante. Esto se puede determinar con `float`

### Operadores aritméticos

En términos de código, símbolos como +, - y * son operadores. Cuando aparecen entre dos valores, crean una expresión. 

Por ejemplo 5 + 9 y 1024 - 512 son ambas experesiones. 

Los operadores para realizar operaciones matemáticas básicas son: 

| Símbolo | Operación        |
|:-------:|:----------------:|
| +       | Suma             | 
| -       | Resta            |
| *       | Multiplicación   |
| /       | División         |
| =       | Igual a          |

Processing tiene una serie de reglas para definir que operadores tienen preferencia. Esto quiere decir que algunos cálculos se hacen primero, luego otros y luego otros. 

Estas reglas definen el orden de declaración del código cuando se ejecuta. 

Ejemplo:

```java
int x = 4 + 4 * 5; 
```

En este caso la operación 4 * 5 se evalúa primero debido a que la multiplicación tiene la prioridad más alta. Posteriormente, al producto de 4 * 5 se le agrega 4. 

Para forzar el orden de las operaciones se utilizan los paréntesis. Todo lo que está entre paréntesis se calcula primero. 

|
```java
int x = (4 + 4) * 5; 
```

Otros tipos de operaciones que son convenciones para ahorrar escritura: 

```java
x += 10; // es igual a x = x +10 
```

```java
x ++; // es igual a x = x + 1 
```
