# Proyecto 2: Lógica secuencial

En este proyecto se busca la creacion impementacion y entendimiento de los siguientes componentes

### Bit

### Register

### RAM8

### RAM64

### RAM512

### RAM4K

### RAM16K

### PC

---

Hasta ahora hemos trabajado con circuitos logicos combinados en base a compuertas logicas los cuales son muy utiles para el
calculo y toma de deciciones logica pero para este proyecto necesitamos circuitos logicos que puedan mantener el estado.
Para ello este proyecto se vasa en el uso de compuetas flip flops las cuales permiten mantener el estado.
hay diferentes tipos de flip flops pero para este proyecto se usara el flips flops de datos o tambien llamado DFF.

## Diagrama del DFF

<image src="/Imagenes/dff.png" alt="dff">

### Bit

es el diseño mas simple que solo consta de un dff y un multiplexor.

## Diagrama de un Bit

<image src="/Imagenes/bit.png" alt="bit">

### Register

Un registro es un dispositivo de almacenamiento que puede "almacenar" o "recordar" un valor.
con el tiempo, este se puede modelar mediante la combiancion de varios bits.

## Diagrama Register

<image src="/Imagenes/registro.png" alt="registro">

### RAM

Una Ram deve permitir acceder a palabras elegidas al azar, sin restricciones en el orden en que
se accede a ellas. Es decir, requerimos que se acceda directamente a cualquier palabra de la
memoria, independientemente de su ubicación física, a la misma velocidad.

para ello tenemos que utilizar un demultiplexor que se conecta n cantidad de registros que a su ves se conecta a un mutiplexor.

## Diagrama de Ram

<image src="/Imagenes/registro.png" alt="ram">

### PC (counter).

Counter CHIP es algo que recuerda en qué línea de palabra/comando está trabajando la ROM.

Digamos que si comenzamos desde la línea 0 de la ROM (ubicación de memoria que guarda las instrucciones), en la mayoría de las situaciones nos gustaría ir a la línea 1 en el siguiente círculo, así podremos incrementar el contador cuando sea necesario. . También tenemos que crear algo que pueda obligar al contador a ir a una determinada línea, digamos 101, cuando el usuario así lo desee. entonces tenemos que obtener un bit de carga para indicarle al contador cuándo guardar datos y cambiar la salida de la siguiente ronda. Bueno, también tenemos que conseguir un bit de reinicio, que ponga el contador en 0 y permita que el sistema se reinicie.

## Diagrama del PC (counter).

<image src="/Imagenes/pc.png" alt="pc_counter">
