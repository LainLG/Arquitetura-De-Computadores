# Proyecto 01: Realizacion de compuertas Logicas

Para el entendimento del proyecto lo primero es entender la logica en que se basa las compuertas logicas la cual es
el algebra boooleana.
Para ello primero presentaremos la leyes basicas de la algebra booleana.

<image src="./Imagenes/algebra-booleana.jpg" alt="Propiedades de la algebra booleana">

luego de entender como funciona la algebra boolena podemos ver las compuertas logicas y entender porque esta se pueden 
definir por funciones logicas que esta regidas por la algebra booleana.

## Compuerta Not

En la compuerta NOT, el estado de la salida es inversa a la entrada. Evidentemente, una negación.

### Operación:

 Q = \bar{x}

Tabla de verdad y símbolo



<image src="/Imagenes/not.jpg" alt="Compuerta Not">

## Compuerta And

Para la compuerta AND, La salida estará en estado alto de tal manera que solo si las dos entradas se encuentran en estado alto. Por esta razón podemos considerar que es una multiplicación binaria.

### Operación:
 
 Q = A * B

Tabla de verdad y símbolo.

<image src="./Imagenes/and.jpg" alt="Compuerta And">


## Compuerta Or

la compuerta OR, la salida estará en estado alto cuando cualquier entrada o ambas estén en estado alto. De tal manera que sea una suma lógica.

### Operación
 Q = A + B

Tabla de verdad y símbolo.


<image src="./Imagenes/or.jpg" alt="Compuerta Or">

## Compuerta Nand

Para la compuerta NAND, cuando las dos entradas estén en estado alto la salida estará en estado bajo. Como resultado de la negación de una AND.

### Operación

 Q= \bar{(A*B)}

Tabla de verdad y símbolo.

<image src="./Imagenes/nand.jpg" alt="Compuerta Nand">

## Compuerta Nor

En la compuerta NOR, cuando las dos entradas estén estado bajo la salida estará en estado alto. Esencialmente una OR negada.

### Operación
 Q= \bar{(A+B)}

Tabla de verdad y símbolo.

<image src="./Imagenes/nor.jpg" alt="Compuerta Nor">

## Compuerta Xor

La compuerta XOR Su salida estará en estado bajo cuando las dos entradas se encuentren en estado bajo o alto. Al mismo tiempo podemos observar que entradas iguales es cero y diferentes es uno.

### Operación

Q = A*B+A*B

Tabla de verdad y símbolo.

<image src="./Imagenes/xor.jpg" alt="Compuerta Xor">
