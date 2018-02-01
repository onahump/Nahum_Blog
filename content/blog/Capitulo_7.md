---
author: "Nahúm Ponce"
title: Capítulo 7&8 - Types & Boolean Logic
linktitle: Memory Organization and Access
date: 2018-02-01T00:35:06-06:00
draft: true
highlight: true
---

## Pointer types

Un apuntador es una variable de memoria que hace referencia a la direccion de un algun objeto.

*Ejemplo:*

>i = 0;

>M [ i ] = 100;

Un puntero es la abstraccion de una direccion de memoria, por lo que un lenguaje podria ocupar el puntero como un mecanismo que asigne el valor del puntero a la direccion de algun elemento de la memoria.

Ademas los punteros hacen referenca a variables anonimas que estan alojadas en el heap (cabecero), la cual es la region reervada para el amacenamiento dinamico de la memoria.

Se tiene entendido que los objetos que son almacenados en la cabecera son las variables anonimas, debido a que se refieren a ellas por su direccion y no a su nombre. Es cierto que muna variable apuntador puede tener un nombre,pero sin embargo este nombre hace referencia al dato del operador y no al nombre del objeto.

## Arrays

Un array es uno de los mas comunes tipos de datos compuesto. Un Array es un tipo de dato cuyos elementos son del mismo tipo.
Un miembro es seleccionado en base al indice del array por lo que el primer elemento del array es la direccion base. Ademas de que este contiene un indice.

Se tiene enendido que abstractamente un array es la coleccion de variables, por lo que para acceder a una variable en especifico debe ser a traves de un indice que nos ayude a consultar tablas. El numero de bytes de almacenamiento que consume un array es el producto de el numero de elementos  que contiene multiplcado por el numero de registros por bytes.

## Record / Structure

Se tiene entendido que un array es homogeneo, pero a que nos referimos con esto, significa que cada uno de sus elementos son del  mismo tipo de datos.

Por el lado contrario un Record/Structure es heterogeneo lo que quiere decir que cada uno de sus elementos puede ser de diferentes tipos de datos.

En los records se puede tomar un elemento desde un campo en donde este cuenta con un nombre y cada nombre es único. Los nombres son son variables locales de la estructura por lo que puedes ocupar el mismo nombre en otras estructuras o otro bloque de código.

## Uniones

Las uniones son similares a los records pero en las uniones para poder acceder a sus campos debes usar la notación ".". Otra de las diferencias que tienen las uniones es el uso de la palabra clave "union" en lugar de record, aunque parezca una pequeña diferencia la verdad es que es todo lo contrario.

Otro de los aspectos importantes a comentar de las uniones es que mientras en un record cada campo tiene su propio desplazamiento desde la direccion, y los campos se superoponen. En una union es todo lo contrario ya que si se cambia un campo todos los demas elementos/campos se recorren por lo que ests se superponen. Como resultado  el tamaño de un registro es la suma de los tamaños de todos sus campos (más algunos bytes de relleno). En la union su tamaño es el tamaño e su campo mas grande.

Otros usos de las uniones:

    Para crear aliases.
    Para desarmar objetos que son demasiado grandes.
    Componer y descomponer tipos de datos.


# Logica Booleana

El algebra booleana dentro de la programacion es parte del pan de cada dio por que es fundamental para un programador entender como funciona para poder desarrollar un software de calidad.

Dentro de el algebra Booleana se manejan 2 valores dentro de cada operador binario

True - 1
False - 0

Existen distintos tipos de operadores dentro del algebra booleana, dentro de los cuales los principales son

| Símbolo |   Operación   |   Operador   |   Resultado  |
|:---:|:---:|:---:|:---:|
| * | A * B | AND | producto| 
| + | A + B | OR | suma |
| ' | A' | NOT | inversa |

*Nota: "°" simboliza un operador binario*

## Consideraciones:

**Closure:**

* Un sistema booleano es cerrado con respecto a un operador binario por cada par de valores boolenos por lo que solo se poduce un resultado (0 ó 1)

**Conmutable**

* Un operador binario es conmutable si: 
> A°B = B°A

**Asociativo** 

* Un operador binario es asociaivo si:

> (A°B)°C = A(B°C)

**Distribuidos**

* Dos operadores binarios "°" y "%" son distribuidos si:

> A°B(B % C) = (A°B) % (A°C)

**Identidad**

* Una valor booleano **|** se dice ser el elemento de identidad con respecto a algun operador binario "°" si:

> A°| = A 

**Inverso**

* Un valor booleano se dce ser el elemento inverso con respecto a algun operador binario "°" si: 

> A°| = B y A != B 

## Consideraciones booleanas

1. La algebra booleana es terminada con las operaciones **AND**,**OR**,**NOT** 
2. El elemento de identidad de AND es 1 y el elemnto de identidad OR es 0. No existe valor de identidad para el operador NOT
3. AND y OR son Conmutables
4. AND y OR son distribuidos con respecto a cualquiera 

	>	A*(B+C) =  (A*B)+(A*C) Y A+(B*C) = (A*B)*(A+B).

5. AND y OR son asociativos 

	>	(A*B)*C = A*(B*C) y (A+B)+C = A+(B+C)

6. Para cada valor A existe un valor A' 

	>	A*A'= 0 y A+A'= 1*

## Teoremas 

Los teoremas nos permiten facilitar ciertas operaciones al trabajar con operadores booleanos:

1.	A+A = A
2.	A*A = A
3.	A+0 = A 
4.	A*1 = A
5.	A*0 = 0
6.	A+1 = 1
