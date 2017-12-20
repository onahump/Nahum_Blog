+++
title = "Writing Great Code: Capítulos 1 & 2 "
author = "Nahúm Ponce"
description = "Bienvenido a mi blog personal, da un vistazo a mi nuevo post / @onahump"
tags = [
    "reseña",
    "writing",
    "great",
    "code",
]
date = "2017-12-20"
categories = [
    "WGC",
    "Reseña",
]
highlight = "true"
+++


Durante estas 3 semanas he estado leyendo el libro de Writing Great Code, el cual en verdad ha sido un libro muy interesante. El introducirte más a fondo acerca del funcionamiento de lo que es el software y darte cuenta que las cosas van más allá de solo líneas de código, cambia completamente la perspectiva de lo que puedes llegar a pensar a lo que en realidad es hacer software. 

Lo cierto es que el título también tiene mucho que ver con el contenido del libro, debido a que también se podría considerar como una guía para programadores que te hará pensar dos veces lo que estas escribiendo al momento de realizar código. 

Creo que sería interesante realizar una pequeña reseña de cada uno de los capítulos, por lo que me gustaría compartirles un poco sobre la lectura que he hecho y tratar de intercambiar puntos de vista de lo que es el libro.  
Por lo que me gustaría comenzar a hablar primeramente sobre los capítulos 2 y 3 del libro, ya que el capítulo 1 es un poco más introductorio.   

Capítulo 2 - Representación numérica 

En este capítulo básicamente se habla sobre como los lenguajes de bajo nivel y nuestros sistemas se comunican, además de hablar sobre el funcionamiento de los distintos sistemas numéricos, haciendo referencia desde el sistema decimal hasta el hexadecimal. 

Durante nuestra vida cotidiana usamos el sistema numérico decimal, el cual fue creado por los árabes y con el cual nos apoyamos para realizar distintas operaciones matemáticas. Algo interesante sobre este sistema es que puede ser representado en notación decimal o también conocida como base 10, la cual nos explica un poco sobre cómo es que se representan los números en este sistema. como, por ejemplo:  

<center>
	<img class="special-img-class" src="/img/WGC/wgc_1.png" width="250" /> 
</center>

Por otra parte, el libro entra a detalle en los distintos sistemas numéricos, principalmente en el sistema binario, el cual es representado por 1's y 0's. 
Uno de los aspectos más llamativos de dicho sistema es el poder comprender como es que funciona y es representado en los diferentes lenguajes de programación, así como el saber cuál es la forma correcta de poderlo escribir para que sea más comprensible para nosotros. Otro punto muy interesante es el de poder convertir este sistema en otro sistema numérico, ya sea el sistema decimal, hexadecimal u octal a través de un conjunto de reglas las cuales nos permitirán realizar correctamente dicha transformación además del conocer cuál es la interacción que tiene con nuestros sistemas. 

Además de esto el libro entra a detalle en cómo podemos realizar la conversión entre representaciones numéricas a String y viceversa, ambas a través de un conjunto de reglas que nos facilitaran la forma de realizarlo. 

Les he hablado sobre sistemas numéricos, pero se preguntaran: 
¿Entonces como es que todo esto se representa en una computadora? 

La respuesta es atreves de bits los cuales son representados por 1's y 0's, ósea de forma binaria. 
Después de esto tenemos el nible el cual es la representación de 4 bits el cual es muy útil para la representación de un digito hexadecimal.  
También tenemos el byte el cual contiene 8 bits y este es el más pequeño tipo de dato que manejan muchos CPU's y muchos lenguajes de programación. 

Existen distintos tipos de datos los cuales ocupan cierta cantidad de bits como lo son: 
word - la cual puede ocupar de 16 bits a 64 bits 
double word - occupant 32 bits 
floating point - que son 64 bits  
long word - 120 bits. 

Cada uno de ellos divididos en sets de bytes y segmentados a través de High Order(HO) los cuales son la mitad de sus bits del centro a la izquierda y el Lower Order que son del centro a la derecha de todos sus bits. 
  
Además de todo, se pueden hacer contracciones con estos números binarios, que consisten en convertir una palabra de 16-bits en un byte lo cual e muy interesante porque te permite conocer cómo puedes ahorrar el uso de cantidades de bytes dentro de un equipo. 


Capitulo 3 - Aritmética binaria & operaciones binarias 

En este capítulo nos demuestran básicamente las operaciones que se pueden realizar con nuestros bits desde una suma, una resta, una multiplicación y una división, cada una de ellas descritas a través de un conjunto de reglas las cuales nos permitirán realizar las operaciones de forma correcta. 

<center>
	<img class="special-img-class" src="/img/WGC/wgc_2.png" width="100" /> 
</center> 

Por otra parte también podemos conocer lo que son los principales operadores lógicos AND,OR y XOR los cuales son visualizados de la siguiente manera: 

<center>
	<img class="special-img-class" src="/img/WGC/xorand.png" width="300" /> 
</center> 

Pero, además de ver como son estos operadores lógicos, también comprobamos como trabajan en un sistema a través de pruebas como lo son:  

<center>
	<img class="special-img-class" src="/img/WGC/ejemplo.png" width="500" /> 
</center>  

Esto no tan solo siendo representado para el operador AND, si no también para los demás operadores lógicos, mostrando que se puede realizar desde un contador por medio del operador AND o compara un conjunto de bits con un conjunto de cualquier otro tipo. 

Otro de los aspectos interesantes que se pueden realizar es el corrimiento de datos de que puede ser de izquierda a derecha.  

<center>
	<img class="special-img-class" src="/img/WGC/wgc_4.png" width="300" /> 
</center> 
 
que equivale a como si se multiplicaran los valores por 2. 

Por otra parte está el corrimiento hacia la derecha:  

<center>
	<img class="special-img-class" src="/img/WGC/wgc_3.png" width="300" /> 
</center> 
 
que es demasiado similar al de la izquierda solo que con este se puede dar el caso de que puedas encontrar exactamente la mitad del valor al realizar el corrimiento, por ejemplo: 

Si buscas encontrar la mitad del valor 6, al realizar este corrimiento encontraras exactamente la mitad de este, obteniendo como resultado el número 3. Lógicamente todo este proceso a través de nuestros sistemas numéricos. 

Pero dentro de este existe un pequeño detalle debido a que no se puede realizar de la misma forma con los binarios, ya que si se realiza igual de la forma anterior este valor no se obtenga un valor esperado por lo que se tiene que realizar una tercera operación, la cual sería el agregar un 0 al último corrimiento, como se mostrara en la siguiente imagen. 

<center>
	<img class="special-img-class" src="/img/WGC/wgc_5.png" width="300" /> 
</center> 

Cambiando de tema, también en este capítulo podemos ver lo que es el empaquetado de datos, lo cual es demasiado interesante debido a que te muestra cómo es que con una sola fecha puedes ocupar lo que ocupa una sola palabra, sabiendo repartir obviamente la información de forma correcta como lo sería la siguiente imagen: 

<center>
	<img class="special-img-class" src="/img/WGC/fecha.png" width="350" /> 
</center> 

 
Esto a la hora de programar nos ayuda demasiado debido a que podemos administrar la cantidad de memoria que se está ocupando, aficionando completamente nuestros programas. 

Esto no solamente pasa en casos de 16 bits, si no que también se puede representar en 32 bits por lo que las representaciones, dentro del capítulo se muestra tal cual como se representa esto en código en distintos lenguajes.

Concluyendo el libro es demasiado interesante y te amplia demasiado el panorama sobre el funcionamiento interno de un CPU’s o software por lo que el objetivo principal de este libro durante estos 2 capítulos es comprender dicha interacción para poderla aplicar a la hora de escribir código.




