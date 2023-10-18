# Proyecto 2: Lenguaje maquina

En este proyecto se busca el entendimiento de los lenjuages de bajo nivel principalmente el lenguaje hack utilizada en el proyecto

### mult

### fill

---

## Hackear lenguaje de máquina

La computadora pirateada es una máquina de 16 bits, que consta de una CPU , dos módulos de memoria separados que sirven como memoria de instrucciones y memoria de datos , y dos dispositivos de E/S mapeados en memoria: una pantalla y un teclado.

Espacios de direcciones de memoria:
memoria de instrucciones: 16 bits de ancho

memoria de datos: 16 bits de ancho

espacio de direcciones: 15 bits

## Registros:

#### Registro D :

solo se puede utilizar para almacenar valores de datos.

#### Un registro

puede interpretarse como un valor de datos, como una dirección en la memoria de datos o como una dirección en la memoria de instrucciones.

#### Registro M:

se refiere a la palabra de memoria cuya dirección es el valor actual del registro A. (M significa Memoria [A])

### Ejemplo:

`@value:` almacena el valor especificado en el registro A.

Por ejemplo, si configuro @21, eso significa que el efecto es que al configurar el registro A en 21, también RAM[21]se convierte en el registro RAM seleccionado.

En realidad, el lenguaje Hack consta de dos instrucciones genéricas: una instrucción de dirección , también llamada instrucción A, y una instrucción de cálculo , también llamada instrucción C. Cada instrucción tiene una representación binaria.

### Operación típica:

```

// D = 10
@10
D = A
// D++
D = D + 1
// D = RAM[17]
@17
D = M
//RAM[17] = D
@17
M = D
//RAM[17] = 10
@10
D = A
@17
M = D
//RAM[5] = RAM[3]
@3
D = M
@5
M = D

```

### la instrucción A

```
@value  //where value is either a non-negative decimal number or a symbol referring to sum number.
```

<image src="/Imagenes/instrucciona.png" alt="instruccion a">

### la instrucción C

```
dest = comp;jump   //Either the dest or jump fields may be empty.If dest is empty,the "=" is ommitted.If jump is empty,the ";"is omitted.
```

<image src="/Imagenes/instruccionc.png" alt="instruccion c">

el bit más a la izquierda es el código de instrucción C, que es 1. Los dos bits siguientes no se utilizan. Los bits restantes forman tres campos que corresponden a las tres partes de la representación simbólica de la instrucción.

### comp :

qué calcular

<image src="/Imagenes/tablaa.png" alt="tabla 1">

### destino :

dónde almacenar el valor calculado (salida ALU)

<image src="/Imagenes/tablab.png" alt="tabla 2">

### salto :

especifica una condición de salto, es decir, qué comando buscar y ejecutar a continuación

<image src="/Imagenes/tablac.png" alt="tabla 3">

Ahora podemos usar Hack Language para multiplicar dos números y luego almacenarlos en un registro específico.

## Manejo de entrada/salida

#### Pantalla :

el contenido de la pantalla comienza en la dirección RAM 16384(0x4000). El bit correspondiente en el mapa de memoria residente en RAM: 1 = negro, 0 = blanco.

Para activar/desactivar píxeles (fila, columna) :

1.palabra = Pantalla[32 fila + columna/16], palabra = RAM[16384 + 32 fila + columna/16].

2.Establezca el (col%16)ésimo bit de la palabra en 0 o 1.

3.Confirmar palabra a la RAM.

#### Teclado :

Las interfaces entre la computadora y el teclado se encuentran en la dirección RAM 24576 (0x6000). Cada vez que se presiona una tecla en el teclado físico, su código ASCII de 16 bits aparece en la RAM [24576]. Cuando no se presiona ninguna tecla, el código 0 aparece en esta ubicación. Además de los códigos ASCII habituales, el teclado Hack reconoce las teclas que se muestran en la siguiente imagen.

<image src="/Imagenes/tablad.png" alt="tabla 4">

### Producción

Mapa de memoria de pantalla Un área de memoria designada, dedicada a administrar una unidad de visualización. La pantalla física se actualiza continuamente desde el mapa de memoria, muchas veces por segundo. La salida se efectúa escribiendo código que manipula el mapa de memoria de la pantalla.
