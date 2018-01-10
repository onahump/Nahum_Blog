---
author: "Nahúm Ponce"
title: Capítulo 6 - Memory Organization and Access
linktitle: Memory Organization and Access
date: 2018-01-10T00:35:06-06:00
draft: true
highlight: true
---

## Los componentes Básicos del sistema

A lo largo de la historia de la computación han existido distintas `arquitectura`s de sistemas, pero en la actualidad la principal ha sido la `arquitectura` de `John Van Newman (VNA)`. Demasiados sistemas ocupan dicha `arquitectura`, como por ejemplo la familia 80X86. Esta `arquitectura` esta dividida en 3 componente principales:

1. **Unidad Central de Procesamiento (CPU)** - Calcula todas las operaciones que ocurren en un sistema.
2. **`Memoria`** - Todos los datos residen  dentro de la `memoria`, asi como las instrucciones principales.
3. **Entradas y Salidas (E/S)** - Son todos aquellos elementos o hardware que nos permite interactuar con el sistema como teclado,mouse etc...

<center>
	<img class="special-img-class" src="/img/capitulo6/c_1.png" width="400" /> 
</center>

--- 

### El bus del Sistema

Un bus es una colección de cables que transportan datos y por el cual pasan señales electricas, ademas el bus del sistema conecta los componentes que existen en el `VNA` y se divide en 3 buses principales:

* Bus de dirección 
* Bus de datos
* Bus de control

--- 

#### Bus de Datos

El CPU usa el bus de datos para mezclar o intercambiar datos entre los componentes. Actualmente la mayoria de los `CPU's` usan un bus de datos de 32 bits o de 64 bits de ancho, pero pueden existir de 8 - 16 bits o hasta 128 bits.

El bus de datos permite transferir información a una localización particular de la `memoria` o a un dispositivo de E/S. 

#### Bus de Dirección 

Este bus asigna una dirección a la localización de la `memoria` o ya sea la dirección de un dispositivo de E/S para poder identificarlo, por lo tanto, cuando se requiera hacer una búsqueda de un dispositivo o  una asignación de `memoria`, se hará en base a la dirección asignada.

Un CPU en una sola linea de bus de dirección podría acceder a 2 direcciones ( 0 y 1). Entonces con n lineas de dirección se podría decir que el procesador puede acceder a *2^n* direcciones. Por lo que la cantidad de bits en el bus de direcciones determina la cantidad máxima de `memoria` direccionable y la cantidad de ubicaciones de E/S. 

#### Bus de Control

Es la colección intermedia de señales que controlan como el CPU se comunica con el resto del sistema. El CPU usa dos lineas en el bus de control, de escritura y lectura. Ambas sirven para determinar el flujo de datos del CPU a la `memoria` o de la `memoria` a la CPU.

Cuando el CPU requiere escribir datos da una señal a la linea de escritura, y en el caso de que solo quiera leer datos de la `memoria` manda una señal a la linea de lectura. Existen mas lineas dentro del bus de control como la linea del reloj, las linea de interrupción, las lineas de habilitación de bytes y la linea de estado, pero estas pueden variar de acuerdo a la `arquitectura`. 


## Organización Física de la `memoria` 

Un CPU ocupa un máximo de *2^n* ubicaciones de `memoria` en donde n es el numero de bits en el bus de direcciones. 

> Pero.... ¿Que es una ubicación de `memoria`?

Para entenderlo debes de saber primero que la familia 80X86 admite direcciones de `memoria`, y se tiene entendido que la unidad basca de `memoria` son los bytes, por lo que cada ubicación de `memoria` ocupa un byte.  Actualmente casi todas las familias de CPU son direccionables pero como en casi todo existen algunas excepciones y es el caso de las direcciones  que son partidas en pedazos como son las palabras doble o cuátruples.

La `memoria` se podría decir que es como una matriz de bytes en donde su primera dirección es 0 y la ultima es *2^n* - 1.

Ejemplo:

> Se le asigna una ubicación de `memoria`, en este caso será la [125] en donde su valor será igual a 0, por lo que se hará una escritura: 

<center>
	<img class="special-img-class" src="/img/capitulo6/c_2.png" width="400" /> 
</center>

> Basándonos en el mismo caso, pero ahora en forma contraria, para hacer una lectura se buscara la dirección 125 dentro de la `memoria` a través del bus de control.

<center>
	<img class="special-img-class" src="/img/capitulo6/c_4.png" width="400" /> 
</center>


## Bit - Data Buses

Una matriz de `memoria` direccionable es aquella en la que la CPU puede direccionar la `memoria` en fragmentos tan pequeños como un byte. Por lo que si se desea acceder un valor de 4 bits en un espacio de `memoria` se ocuparan los 4 bits y se dejaran en blanco los otros 4 bits, debido a que un byte es la menor unidad.

Por otra parte, cada dirección son enteros, esto quiere decir que no se puede acceder a una dirección 12.3 o 14.2, si no que solo se puede acceder a direcciones como 12, 7 , 0. 

### 8-Bit Data Buses

Ahora, hablando un poco de los CPU. Un procesador con 8-bit de bus (como el 8088) puede transferir 8 bits de datos a la vez, debido a que cada dirección de `memoria` corresponde a un byte de 8 bits, este tipo de bus resulta ser dentro de las `arquitectura`s el mas común.

<center>
	<img class="special-img-class" src="/img/capitulo6/c_5.png" width="400" /> 
</center>

### 16-Bit Data Buses ( `CPU's` - 8086, 80286 y ARM)
   
Este tipo de CPU permite acceder al doble de `memoria` en la misma cantidad de tiempo que el de 8-Bit, ademas de que permite organiza la `memoria` en "par" e "impar". 
<center>
	<img class="special-img-class" src="/img/capitulo6/c_6.png" width="400" /> 
</center>

> ¿Como funciona?

El procesador obtiene el byte LO del valor de la dirección especifica y el byte HO da la siguiente dirección.

<center>
	<img class="special-img-class" src="/img/capitulo6/c_7.png" width="400" /> 
</center>

*Problemas:*
* Puede provocar conflictos a la hora de realizar escritura y lectura.
* Al acceder palabras, debido a que accede a 2 bytes separados, cada uno contiene una dirección de bytes aparte.



### 32-Bit Data Buses ( `CPU's` - 80386 y 80486 )

En su funcionamiento se requiere de al menos 2 operaciones de `memoria` de procesadores de 16-bit. Se accede a una cantidad de 32 Bits en una dirección impar, un procesador de 16-Bit puede realizar 3 operaciones de `memoria` para acceder a los datos.   Un CPU de 32 bits utilizan 4 bancos de `memoria` conectados y pude acceder a una palabra de `memoria` usando solo una operación de `memoria`.

<center>
	<img class="special-img-class" src="/img/capitulo6/c_8.png" width="400" /> 
</center>


La interfaz de `memoria` de 32 bits puede acceder a cualquier byte con una operación de `memoria`. En esta interfaz la dirección ubicada en el bus de direcciones es siempre un múltiplo de 4, en el cual el CPU seleccionara cual de los 4 bytes desea acceder. 

### 64-Bit Data Buses
Proporcionan un bus de datos de 64 bits y una `memoria` cache que redice el impacto del acceso de datos no alineados. 

## Big Endian Versus Little Endian Organization

Como los diferentes procesadores almacenan objetos de múltiples bytes en la `memoria` direccionabe por bytes, ademas cuando existen objetos de 8 bits, todo se vuelve mas complicado ya que existen diferentes `CPU's` que organizan los bytes de distinta forma.

El byte LO que aporta el componente mas pequeño de un numero binario se ubica en las posiciones de bit 0 a 7 y aparecen en la dirección mas baja. 

<center>
	<img class="special-img-class" src="/img/capitulo6/c_9.png" width="400" /> 
</center>

Pero existen algunos `CPU's` como los de la apple Macintosh y la mayoría de los UNIX que invierten las direcciones de los bytes de una palabra doble. 

Intel por su parte organiza los bytes de distinta forma, la cual es mejor conocida como Little Edian. Mientras que su forma alternativa es el Big Edian. 
De acuerdo a estas dos formas se habla de que existen sexos o géneros, debido a que la información obtenida de una es deferente a la otra. También se habla de una comparación para saber cual es mejor pero la verdad es que eso es lo de menos ya que existen problemas entre ambas formas a la hora de transmitir información.

Por lo que al hacer una transferencia de información de datos entre ambas, lo mejor es realizar conversiones a una forma canónica, y en el caso de que esto no sea suficiente lo mejor es hacer una conversión a la forma local ( Ya sea Little Edian o Big Edian).

Ejemplo: 

La representacion binaria de la palabra doble 256:
<center>
	<img class="special-img-class" src="/img/capitulo6/c_11.png" width="400" /> 
</center>

*Little Edian:*

<center>
	<img class="special-img-class" src="/img/capitulo6/c_12.png" width="400" /> 
</center>

*Big Edian:*
<center>
	<img class="special-img-class" src="/img/capitulo6/c_13.png" width="400" /> 
</center>


## El reloj del Sistema

Los sistemas requieren de cierto tiempo para realizar las tareas. En las `arquitectura`s `VNA`, las operaciones se serializan, esto quiere decir que las tareas se ejecutan en base a un orden y todo esto en parte es gracias al reloj del sistema.

Ademas, el reloj del sistema es una señal eléctrica en el bus de control que se alterna entre 0 y 1 a una velocidad periódica, dicha señal marca un periodo que también es llamado ciclo del reloj.

<center>
	<img class="special-img-class" src="/img/capitulo6/c_14.png" width="400" /> 
</center>

Por otra parte la frecuencia con la que  se alterna entre 0 y 1 se le llama frecuencia del reloj del sistema.El periodo del reloj es reciproco a la frecuencia del reloj.

Por ejemplo:

> 1 MHz de frecuencia del reloj tendría un periodo de reloj de un microsegundo (una milésima de segundo) o 16 Hz tendrían un periodo de reloj de un nano segundo (mil millonésimas de segundo).

## Acceso a la `memoria`

El acceso a la `memoria` es una operación que sincroniza el reloj del sistema y que permite el acceso a la misma `memoria` en cada ciclo del reloj. 

El tiempo de acceso a la `memoria` es el numero de ciclos del reloj entre lo que es una solicitud de `memoria` y la finalización de la operación. 

Por otra parte, cuando se lee desde la `memoria`, el tiempo de acceso a la `memoria` es el tiempo entre cuando el CPU ubica la dirección en el bus y el tiempo cuando el CPU toma los datos en el bus de datos.

### Estados de Espera

Los estados de espera son un ciclo de reloj extra que da al dispositivo tiempo adicional para responder al CPU.

Casi todos los `CPU's` proporcionan un PIN que permite la inserción de estados de espera, lo que permite a la `memoria` darle el suficiente tiempo a cada acceso.
Pero cabe destacar que los estados de espera no son algo bueno observándolo desde el punto de vista de rendimiento debido a que mientras el CPU espera datos de la `memoria` no puede operar con dichos datos ya que al agregar estados de espera se duplica el tiempo requerido para obtener el acceso.

### CPU Acceso a la `Memoria`

Los `CPU's` tienen 2 o 3 formas de acceder a la `memoria` y los modos mas comunes en la actualidad son los directos, indirectos e indexados. El tener modos de `direccionamiento` de `memoria` hacen el acceso a la `memoria` mas flexible, ademas de que permiten el uso de menos instrucciones.

#### Modo de `Direccionamiento` Directo

El `direccionamiento` directo codifica la dirección de `memoria` de una variable como parte de la instrucción de maquina real que accede a dicha variable.

*Usos:*

* Puede ser implementado en un programa que ocupa variables estáticas globales
* Para acceder a variables cuya dirección de `memoria` se conoce antes de la ejecución.

#### Modo de `Direccionamiento` Indirecto

Usa un registro para mantener una dirección de `memoria`

*Ventajas:*

* Puede encontrar el valor de una dirección indirecta en tiempo de ejecución
* Codifica que registro especifica a la dirección indirecta, lo que requiere menos bits que un `direccionamiento` directo.

*Desventajas:*

* Pueden tomar una o mas instrucciones para cargar un registro con su dirección. 

#### Modo de `Direccionamiento` Indexado

El modo de `direccionamiento` indexado combina el `direccionamiento` directo e indirecto.Codifica de forma directa y hace la ejecución como la indirecta.

*Usos:*

* Para acceder a elementos arraylist
* Para acceder indirectamente a objetos como estructuras y registros.

*Ventajas:*

* Puede especificar una dirección directamente dentro e una instrucción sin tener que otra instrucción separada.

#### Modo de `Direccionamiento` indexado a escala

Provee de 2 facilidades mas que el `direccionamiento` indexado:

1. Usar 2 registros para calcular la dirección efectiva.
2. Capacidad de multiplicar uno de los dos registros por una constante común antes de calcular la dirección efectiva.

*Usos:*

* Para acceder a elementos de matrices cuyos tamaños coinciden con las contantes de escalamiento.

 
 