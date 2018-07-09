---
author: "Nahúm Ponce"
title: "Alta de dominios en Sentora"
linktitle: Dominios en Sentora
date: 2018-07-08T20:31:09-05:00
draft: true
highlight: true
---

En este Post aprenderemos como dar de alta dominios con Sentora desde nuestra cuenta de administrador y por consiguiente usar dichos dominios para la generacion de nuestros sitios con WordPress. 

---

Para poder empezar a trabajar, debemos de cumplir con los siguientes puntos:

* Tener instalado Sentora
* Tener una cuenta de administrador para crear nuestros dominios

Una vez cumplidos estos dos requisitos comenzemos a trabajar.

---

### Paso 1: Generar nuestro archivo base

Antes de comenzar a trabajar con Sentora debemos de generar nuestro archivo base.El cual nos servira como guía y documentador y asi llevar un mejor control al momento de generar nuestros dominios.

Para poder ejemplificar de mejor forma, generaremos el siguiente dominio:

#### `nahump.com.mx`

Crearemos un *archivo de texto(.txt)* el cual iremos llenando conforme vayamos avanzando:

``` 
nombre-de-nuestro-dominio 

user: nombre-principal-del-dominio
pass: contraseña-que-asigna-sentora

db(bases de datos):
	(nombre-base-de-datos-para-wordpress)_wp   
    	(nombre-base-de-datos-para-la-aplicacion)_db   

mb(mailbox):	
	contacto@nuestro-dominio

ftp:  nombre-de-nuestro-dominio_ftp

``` 

---

### Paso 2: Acceder con nuestra cuenta de administrador

Ingresaremos a la direccion IP (o dominio) de nuestro Sentora e ingresaremos los datos de nuestra cuenta de administrador.

<center>
	<img class="special-img-class" src="/img/sentora/inicio_sentora.png" width="400" /> 
</center> 

---

### Paso 3: Crear nuestro cliente

Para crear nuestro cliente, nos dirigimos al apartado de `Reseller` y escogemos la opción de `Manage Clients`

<center>
	<img class="special-img-class" src="/img/sentora/reseller.png" width="400" /> 
</center> 

Una vez que ingresamos, nos dirigimos a la parte inferior del sitio en el apartado`Create new client account` y llenamos los siguientes campos con datos relacionados a nuestro dominio(*nahump.com.mx*):


<center>
	<img class="special-img-class" src="/img/sentora/client.png" width="700" /> 
</center> 

Una vez llenados los campos que se muestran en la imagen,damos click en `Guardar` y sustituimos los datos de nuestra Guía ***(user, pass y mailbox)*** por los generados en el formulario.


```
nombre-de-nuestro-dominio 

user: nahump
pass: a2ysumaja

db(bases de datos):
	(nombre-base-de-datos-para-wordpress)_wp   
    	(nombre-base-de-datos-para-la-aplicacion)_db   

mb(mailbox):	
	contacto@nahump.com.mx

ftp:  nombre-de-nuestro-dominio_ftp

``` 

Salimos de nuestra cuenta de administrador en el apartado de `Account`y `Logout`.

<center>
	<img class="special-img-class" src="/img/sentora/logout.png" width="400" /> 
</center> 

---

### Paso 4: Crear dominio en nuestra archivo /etc/hosts

En nuestro archivo `hosts` ubicado dentro de `etc`, agregamos como ultima línea nuestra `direccion ip` de nuestro sentora y la direccion de nuestro `nuevo dominio` cliente (Ejemplo):

```
(Direccion-IP-de-Sentora)  		(Dominio) //Ignorar esta línea
xx.xxx.xxx 				nahump.com.mx

```
Despues seguimos modificando nuestra guia `sustituyendo el nombre de dominio` por el que hemos creado(*nahump.com.mx*) en nuestro archivo /etc/hosts

```
nahump.com.mx

user: nahump
pass: a2ysumaja

db(bases de datos):
	(nombre-base-de-datos-para-wordpress)_wp   
    	(nombre-base-de-datos-para-la-aplicacion)_db   

mb(mailbox):	
	contacto@nahump.com.mx

ftp:  nombre-de-nuestro-dominio_ftp

``` 



---

### Paso 5: Ingresar a Sentora con el User & Pass Generados


<center>
	<img class="special-img-class" src="/img/sentora/login_client.png" width="400" /> 
</center> 

--- 

### Paso 6: Ir al apartado de Domains

Una vez que ingresamos nos dirigimos al apartado de `Domain` y `Domains`para poder crear nuestro dominio.

<center>
	<img class="special-img-class" src="/img/sentora/domains.png" width="400" /> 
</center> 

Cuando entremos, llenaremos el apartado de `Domain name` con el nombre de dominio de nuestra guía y seleccionaremos la opción `Create a new home directory`.

<center>
	<img class="special-img-class" src="/img/sentora/domain.png" width="600" /> 
</center> 

Damos click en `Create`y nos generara el siguiente apartado.

<center>
	<img class="special-img-class" src="/img/sentora/domain-block.png" width="600" /> 
</center> 

---

### Paso 6: Crear las bases de datos

En este apartado, nos dirigiremos a `DataBase` y `MySQL Database`

<center>
	<img class="special-img-class" src="/img/sentora/database.png" width="400" /> 
</center> 

Crearemos nuestra base de datos `nahump_db` 

<center>
	<img class="special-img-class" src="/img/sentora/nahumdb.png" width="700" /> 
</center> 

Despues generamos la base de datos `nahum_wp`

<center>
	<img class="special-img-class" src="/img/sentora/databases.png" width="700" /> 
</center> 

---

### Paso 7: Crear usuario para gestionar las bases de datos

Nos dirigimos al apartado `DataBase` y `MySQL Users`

<center>
	<img class="special-img-class" src="/img/sentora/mysql_users.png" width="400" /> 
</center> 

Asignamos el mismo `user` de nuestra guía al `user name` de MySQL, asignamos la base de datos `nahum_db` y creamos. 

<center>
	<img class="special-img-class" src="/img/sentora/match.png" width="550" /> 
</center>

Generado el `user name` vamos al apartado de Editar.

<center>
	<img class="special-img-class" src="/img/sentora/edit_db.png" width="700" /> 
</center>

Agregamos la base de datos `nahum_wp` y cambiamos el `Password`por el mismos password de nuestra `Guia`

<center>
	<img class="special-img-class" src="/img/sentora/add_db.png" width="700" /> 
</center>

Ahora, `actualicemos los datos` de las base de datos de nuestra `guía`.


```
nahump.com.mx

user: nahump
pass: a2ysumaja

db(bases de datos):
	nahump_wp   
    	nahump_db   

mb(mailbox):	
	contacto@nahump.com.mx

ftp:  nombre-de-nuestro-dominio_ftp

``` 

---

### Paso 8: Crear mailbox para nuestro dominio

Nos dirigimos al apartado de `Mail` y `Mailboxes`

<center>
	<img class="special-img-class" src="/img/sentora/mailbox.png" width="400" /> 
</center>

Generamos el mismo mailbox que habíamos generado en nuestra guia, de igual forma con la contraseña y damos click en `Create`.

<center>
	<img class="special-img-class" src="/img/sentora/mail.png" width="600" /> 
</center>

---

### Paso 9: Crear una cuenta FTP

Elegimos la opcion de `File` y `FTP Accounts`

<center>
	<img class="special-img-class" src="/img/sentora/ftp.png" width="400" /> 
</center>

Como username asignamos `ftp`, como password la misma que tenemos en la guía, damos full acces y usamos el directorio del dominio (/root). 

<center>
	<img class="special-img-class" src="/img/sentora/ftp2.png" width="600" /> 
</center>

Actualizamos nuestra guía nuevamente:

```
nahump.com.mx

user: nahump
pass: a2ysumaja

db(bases de datos):
	nahump_wp   
    	nahump_db   

mb(mailbox):	
	contacto@nahump.com.mx

ftp:  nahump_ftp

``` 


---

### Paso 10: Ejecutamos Sentástico

En el apartado de `Advanced`, escogemos la opcion de `Sentastico` y damos click.

<center>
	<img class="special-img-class" src="/img/sentora/sentastico.png" width="400" /> 
</center>

Ahora nos permitira la instalacion por medio de Sentastico, daremos click en `Install`

<center>
	<img class="special-img-class" src="/img/sentora/sen2.png" width="600" /> 
</center>

Se dirigira a la siguiente pantalla y seleccionaremos el comboBox para instalar el dominio root

<center>
	<img class="special-img-class" src="/img/sentora/sen3.png" width="600" /> 
</center>

Mandará a una nueva pantalla para confirmar la instalacion, daremos click y nos enviara al siguiente paso.


---

### Paso 11: Instalacion de WordPress


Una vez hecho lo anterior nos abrira una nueva ventana con la instalacion de WordPress, seleccionaremos nuestro idioma y daremos click en siguiente.

<center>
	<img class="special-img-class" src="/img/sentora/idioma.png" width="600" /> 
</center>

Despues daremos click en **¡Vamos a ello!** y nos enviara a una pantalla en la cual tendremos que llenar con la información que hemos guardado en nuestra guia.

<center>
	<img class="special-img-class" src="/img/sentora/info.png" width="600" /> 
</center>

Damos click en **Enviar** y despues en **Ejecutar instalación**.

Nos aparecera la siguiente pantalla que al igual que la anterior, la debemos de llenar con los mismos campos que tenemos en nuestra guía para poder tener un mejor control del sitio.


<center>
	<img class="special-img-class" src="/img/sentora/info.png" width="600" /> 
</center>

Enviamos los datos del sitio y `¡Pum!` tenemos listo nuestro sitio en WordPress.

<center>
	<img class="special-img-class" src="/img/sentora/site.png" width="700" /> 
</center>

¡Espero que este post les haya sido de gran ayuda!

@onahump