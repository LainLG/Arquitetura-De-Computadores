# Proyecto 01: Realizacion de compuertas Logicas

Para el entendimento del proyecto lo primero es entender la logica en que se basa las compuertas logicas la cual es
el algebra boooleana.
Para ello primero presentaremos la leyes basicas de la algebra booleana.

<image src="/Imagenes/algebra-booleana.png" alt="Propiedades de la algebra booleana">

luego de entender como funciona la algebra boolena podemos ver las compuertas logicas y entender porque esta se pueden 
definir por funciones logicas que esta regidas por la algebra booleana.

## Compuerta Not

En la compuerta NOT, el estado de la salida es inversa a la entrada. Evidentemente, una negación.

### Operación:

$$ Q = \bar{x} $$

Tabla de verdad y símbolo



<image src="/Imagenes/not.png" alt="Compuerta Not">

## Compuerta And

Para la compuerta AND, La salida estará en estado alto de tal manera que solo si las dos entradas se encuentran en estado alto. Por esta razón podemos considerar que es una multiplicación binaria.

### Operación:
 
$$ Q = A * B $$

Tabla de verdad y símbolo.

<image src="/Imagenes/and.png" alt="Compuerta And">


## Compuerta Or

la compuerta OR, la salida estará en estado alto cuando cualquier entrada o ambas estén en estado alto. De tal manera que sea una suma lógica.

### Operación
$$ Q = A + B $$

Tabla de verdad y símbolo.


<image src="/Imagenes/or.png" alt="Compuerta Or">

## Compuerta Nand

Para la compuerta NAND, cuando las dos entradas estén en estado alto la salida estará en estado bajo. Como resultado de la negación de una AND.

### Operación

$$ Q= \bar{(A*B)} $$

Tabla de verdad y símbolo.

<image src="/Imagenes/nand.png" alt="Compuerta Nand">

## Compuerta Nor

En la compuerta NOR, cuando las dos entradas estén estado bajo la salida estará en estado alto. Esencialmente una OR negada.

### Operación

$$ Q= \bar{(A+B)} $$

Tabla de verdad y símbolo.

<image src="/Imagenes/nor.png" alt="Compuerta Nor">

## Compuerta Xor

La compuerta XOR Su salida estará en estado bajo cuando las dos entradas se encuentren en estado bajo o alto. Al mismo tiempo podemos observar que entradas iguales es cero y diferentes es uno.

### Operación

 $$ Q = A*B+A*B $$

Tabla de verdad y símbolo.

<image src="/Imagenes/xor.png" alt="Compuerta Xor">

Una vez entendido estos conceptos podemos comenzar a realizar el Proyecto como dijimos toda compuerta logica se puede escribir solo usando compuertas Nand razon por
la cual el proyecto nos viene con dicha compuerta hecha.

Mostraremos el diagrama y la logica de las primeras compuertas logicas a realizar.

<image src="/Imagenes/compuertas.jpg" alt="Compuertas">


como podemos ver en la imagen podemos usar Morgan para convertir compuertas logicas a comuerta logicas Nand.

# Codigo

## Compuerta Not

// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/01/Not.hdl

/**
 * Not gate:
 * out = not in
 */

CHIP Not {
    IN in;
    OUT out;

    PARTS:
    Nand( a= in , b = in , out = out);
}

## Compuerta And

// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/01/And.hdl

/**
 * And gate: 
 * out = 1 if (a == 1 and b == 1)
 *       0 otherwise
 */

CHIP And {
    IN a, b;
    OUT out;

    PARTS:

    Nand(a = a, b = b ,out = out1 );
    Not(in = out1 , out = out);
}


## Compuerta Or 

// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/01/Or.hdl

 /**
 * Or gate:
 * out = 1 if (a == 1 or b == 1)
 *       0 otherwise
 */

CHIP Or {
    IN a, b;
    OUT out;

    PARTS:
    Not( in = a , out = out1);
    Not( in = b , out = out2);
    Nand(a = out1 , b = out2 , out = out);

}


Al finalizar el proyecto veremos y entenderemos porque toda compuerta logica se puede diseñar a partir de compuertas nand y que podemos utilizar
compuertas ya definidas para realizar circuitos mas complejos.


