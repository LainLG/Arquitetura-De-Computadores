# Proyecto 5: Arquitectura de Computadores

## Arquitectura de Von Neumann y la CPU

<image src="/Imagenes/project5_1.png">

La Máquina de Turing es un concepto tal que una máquina puede realizar diferentes tipos de tareas, es una máquina de máquinas. Von Neumann diseñó esta arquitectura y hizo posible la máquina de Turing.

La imagen de arriba es un resumen del sistema informático moderno. Comencemos desde el corazón de la computadora: la CPU.

<image src="/Imagenes/project5_2.png">

## ENTRADAS:

La CPU aceptará 3 entradas.

Instrucción. La CPU puede recibir instrucciones de dirección e instrucciones de computación, entonces, ¿cómo las distinguimos? Recuerde que todas las instrucciones, datos o etiquetas están representados por un número binario de 16 bits. Noam y Shimon decidieron usar el primer bit de izquierda a derecha para representar el tipo de instrucción. Si el primer bit es cero, entonces es una instrucción de dirección; de lo contrario, es una instrucción informática. Por ejemplo:

´´´
0000 0000 0000 0001 se traducirá a @1, esta es una instrucción A.
1000 0000 0000 0001 se traducirá a D&A;JGT, y esta es una instrucción C.

´´´
Si queremos saber cómo traducir la instrucción C, tendremos que mirar la imagen a continuación.

<image src="/Imagenes/project5_3.png">

2. Memoria de datos: los datos almacenados en la ranura de la memoria de trabajo actual.

3. reset: 1 bit encargado de resetear todo el sistema (que consiste en poner la PC a 0).

## PRODUCCIÓN:

a) outM: el resultado del ciclo de cálculo anterior.
b) writeM: el bit de carga que decide si escribimos en la RAM o no.
c) addressM: la ubicación de la ranura de RAM en la que queremos escribir.
d) PC: contador de programa, puede tomar datos de 16 bits como entrada y tiene 3 bits de carga: inc, reset, load. este registro de PC decide qué línea de código procesar, y si reiniciamos la PC, todo el programa finalizará y volveremos a la línea 0.

<image src="/Imagenes/projec5_4.png">

Ahora podemos echar un vistazo más de cerca a todo el sistema de CPU.

El Mux16 más a la izquierda se ocupa de la entrada de instrucciones. Recuerde que la instrucción puede ser una Dirección o también puede ser una Instrucción. El bit de control del Mux. Imaginemos que estamos tratando con una instrucción @100, el 100 debe ir al registro A y debemos establecer el bit de carga del registro A en 1. Y este 100 también irá al Mux16 en el medio de la imagen. Todavía queremos que este Mux16 genere 100 porque no nos importa en este punto cuál sea la entrada de la Memoria, solo queremos que el sistema recuerde el valor almacenado en la RAM [100], después de todo este proceso, la ALU solo debería generar “y”, por lo que podemos poner a cero la entrada “x” y devolver “x + y”, luego la salida se guardará en D-Register, A-Register y también se copiará a la entrada de la PC. entonces la siguiente instrucción de @100 puede ser muchas cosas. Puede ser D=A, si ese es el caso podemos establecer el bit de control del D-Register en 1 y el valor de la salida anterior, que es 100, se almacenará en el D-Register; o la siguiente instrucción puede ser “0;JMP”, entonces el bit de control de la PC se configurará en carga =1, y ahora la salida de la PC será 100, e iremos a la ROM[100] para procesar la siguiente línea de instrucción; o puede ser M=A, en el ciclo anterior, la salida del registro A también fue emitida por el sistema en el nombre de “direcciónM”, y si configuramos el bit de escrituraM en 1, entonces se dará RAM[100] un valor que es la salida de la CPU: 100, M=A. Realmente puede hacer muchas cosas con esta CPU, sólo necesitamos saber cómo manipular esos bits de control para permitirles hacer las cosas correctas.

<image src="/Imagenes/project_5_5.png">

La instrucción es de ROM32K y el valor de retorno de la PC irá a la ROM para indicar qué línea de código estamos procesando a continuación.

inM proviene de la RAM, la ubicación de la RAM en la que trabajaremos en realidad la decide la salida del Registro A del último ciclo. RECUERDA que estamos en un sistema secuencial. Esta entradaM se decide por la salida de la direcciónM, que era un producto secundario del Registro A, por ejemplo, si tenemos un comando @128; M=5, el primer comando @128 ha establecido el valor del Registro A en 128 y, al mismo tiempo, la salida del Registro A irá a la dirección M, y en la siguiente ronda, la memoria usará la dirección M para encontrar la RAM. [128] y establezca el bit de escritura M en 1, porque estamos a punto de cambiar el valor almacenado allí para que sea 5. "Reiniciar" es solo una acción única, se presionará al principio, la PC irá a la línea 0 de ROM para comenzar a tomar comandos, y después de leer un comando de la ROM, colocamos el comando en el bus de instrucciones y lo enviamos a la CPU, la CPU decidirá qué tipo de cálculo tomaría.

<image src="/Imagenes/project5_6.png">
