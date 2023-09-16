# Proyecto 2: Aritmética booleana

En este proyecto se busca la creacion impementacion y entendimiento de los siguientes componentes

### HalfAdder

### FullAdder

### Imcrementer

### Adder

### ALU

---

para ello partiremos de la necesidad de definir el lenguaje que manejan estos dispositivos que es el binario como su nombre lo indica
esta compuestos de solo dos posibles resultados ( 0 , 1 ) y tiene `math 2^{n}  ` n es un numero real positivo

los numeros binarios se puede pasar al lenguaje humano el cual es el decimal o base 10 para ello se realiza la siguiente operacion sencilla

```math

(10101)_{2} = 1 \ast 2^{4} + 0 \ast 2^{3} + 1 \ast 2^{2} + 0 \ast 2^{1} + 1 \ast 2^{0} = 16 + 4 + 1 = (21)_{10}

```

## Suma binario

la suma en numeros bidarios esta definida bajo la siguiente criterio

0 + 0 = 0 --> carry = 0
0 + 1 = 1 --> carry = 0
1 + 1 = 0 --> carry = 1

si al final de una suma binaria el carry = 1 se dice que hay overflow (desbordamiento) es decir supera la cantidad de bits
con los que esta definido.

### Ejemplo:

<image src="/Imagenes/suma_binaria.png" alt="Suma binaria">

## Resta Binaria

Como explicaremos a continuacion la resta binaria se puede definir como una suma es decir x - y se puede definir como x + (-y) :
para ello se han definido diferentes metodos en este caso aplicaremos el metodo de complemento 2 el cual esta definido por:

<image src="/Imagenes/complemento_2.png" alt="Complemento 2">

### Ejemplo:

```math

\left ( 10101 \right )_{2} - \left ( 00101 \right )_{2} = \left ( 10101 \right )_{2} + \left ( 2^{5} \right )_{10} - \left ( 5 \right )_{10} = \left ( 10101 \right )_{2} + \left ( 27 \right )_{10} = \left( 10101 \right )_{2} + \left ( 11011 \right )_{2} = \left ( 10000 \right )_{2}

```

de manera mas facil la resta se puede hacer negando el numero y sumandole uno es decir

```math

 (10101)_{2} - (00101)_{2} = (10101)_{2} + (11010)_{2} --> (01111)_{2} + (00001)_{2} = (10000)_{2}

```

Esto permite la simplificacion de los circuitos logicos ya que la resta se puede realizaro como sumas
esto simplifica mucho permitiendo tener en un solo chip ALU toda las operaciones Aritmeticas y Logicas

## HalfAdder

El medio sumador es un componente básico para sumar dos números como dos entradas y producir dos salidas. El sumador se utiliza para realizar la operación OR de dos números binarios de un solo bit. Los bits augente y sumador son dos estados de entrada, y 'llevar ' y 'suma ' son dos estados de salida del medio sumador.

<image src="/Imagenes/halfadder.png" alt="HalfAdder">

### En la tabla anterior,

'A' y 'B' son los estados de entrada, y 'suma' y 'carry' son los estados de salida.
La salida de acarreo es 0 en caso de que ambas entradas no sean 1.
El bit menos significativo de la suma se define mediante el bit de 'suma'.

### La forma SOP de suma y acarreo es la siguiente:

Suma = x'y+xy'
Llevar = xy

### Circuito Logico:

<image src="/Imagenes/half-adder.png" alt="Circuito_HallAdder">

## FullAdder

El medio sumador se utiliza para sumar sólo dos números. Para superar este problema, se desarrolló el sumador completo. El sumador completo se utiliza para sumar tres números binarios de 1 bit A, B y acarreo C. El sumador completo tiene tres estados de entrada y dos estados de salida, es decir, suma y acarreo.

<image src="/Imagenes/fulladder.png" alt="FullAdder">

### En la tabla anterior,

'A' y 'B' son las variables de entrada. Estas variables representan los dos bits significativos que se van a sumar.
'C in ' es la tercera entrada que representa el acarreo. Desde la posición significativa inferior anterior, se recupera el bit de acarreo.
La 'Suma' y el 'Carry' son las variables de salida que definen los valores de salida.
Las ocho filas debajo de la variable de entrada designan todas las combinaciones posibles de 0 y 1 que pueden ocurrir en estas variables.
Nota: Podemos simplificar cada una de las 'funciones booleanas' de salida con la ayuda del método de mapa único.

### El formulario SOP se puede obtener con la ayuda de K-map como:

Suma = x' y' z+x' yz+xy' z'+xyz
Llevar = xy+xz+yz

<image src="/Imagenes/full-adder5.png" alt="Circuito_FullAdder">

## Adder16

UN Adder de 16 bits es la coneciion de un HalfAdder y 15 FullAdder en cascada siendo este primero un HalfAder porque la primera ejecucion
no lleva acarreo.

<image src="/Imagenes/adder.png" alt="Adder">

## Inc16

un Inc de 16 bits es un incrementador que tiene 16 entrada de datos donde la funcion de un incremtador es sumar uno al dato anterior es deciir
out = x+1 donde out es la salida y x es el dato de entrada un incrementador se puede modelar facilmente con un adder de 16 bits

## ALU

La unidad aritmética lógica o unidad aritmético-lógica, también conocida como ALU
(siglas en inglés de arithmetic logic unit), es un circuito digital que calcula operaciones
aritméticas (como suma, resta, multiplicación, etc.) y operaciones lógicas (si, y, o, no),
entre valores (generalmente uno o dos) de los argumentos.

### Diagrama de caja:

<image src="/Imagenes/alu.png" alt="ALU">

### SeudoCodigo del ALU

<image src="/Imagenes/seudocodigo.png" alt="seudocodigo_alu">

### Tabla De Verdad:

<image src="/Imagenes/tabla_alu.png" alt="tabla_de_verdad_alu">

La tabla de verdad de ALU. En conjunto, las operaciones binarias codificadas por los primeros seis
Las columnas efectúan la función enumerada en la columna de la derecha (usamos los símbolos !, & y | para representar los operadores Not, And y Or, respectivamente, realizados bit a bit). La ALU completa
La tabla de verdad consta de sesenta y cuatro filas, de las cuales sólo las dieciocho presentadas aquí son de interés.
