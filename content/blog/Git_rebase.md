---
author: "Nahúm Ponce"
title: "Git rebase"
date: 2017-12-27T01:23:36-06:00
draft: true
highlight: true
---

Hace 1 semana tuve la fortuna de tomar un curso en el cual nos enseñaron un poco de Git, una herramienta que ha tomado mucha fuerza en el desarrollo de software y la cual es verdaderamente poderosa.    

La verdad es que anteriormente ya había manejado este controlador de versiones y uno de los puntos que más se me dificultaba, era entender la parte del rebase. Por lo que el verlo durante el curso fue un gran suspiro de alivio para futuros proyectos.   

Básicamente el rebase tiene que ver con el branching por lo que si tenemos que ramificar un proyecto y tomar cambios de otras ramas será nuestro perfecto aleado. Sigamos el siguiente ejemplo para exponer un caso de mejor forma:    

Creamos un directorio e iniciamos nuestro repo de git para poner manos a la obra. 


``` 
➜  Documents mkdir practices-git    
➜  Documents cd practices-git  
➜  practices-git git init 
Initialized empty Git repository in /home/user/Documents/practices-git/.git/ 
➜  practices-git git:(master)    

``` 

Ahora creemos un archivo html vacío dentro de este repositorio. 
  

``` 
<!DOCTYPE html> 

<html lang="en"> 

    <head> 

        <h1>Hola mundo</h1> 

    </head> 
    <body> 
    </body> 

</html> 

``` 

Dejando nuestra carpeta de la siguiente manera    

     ▾ practices-git/ 
         index.html 


No queda más que verificar nuestros cambios, agregar nuestro archivo y comprometerlo para ir a nuestro siguiente paso 
  

``` 
➜  practices-git git:(master) gst   

On branch master 
No commits yet 

Untracked files: 

  (use "git add <file>..." to include in what will be committed)   

    index.html 

nothing added to commit but untracked files present (use "git add" to track) 

➜  practices-git git:(master) ✗ git add index.html  
➜  practices-git git:(master) ✗ gcmsg "Agregando index.html"   
[master (root-commit) 21c3fb0] Agregando index.html 
1 file changed, 9 insertions(+) 
create mode 100644 index.html 

``` 

Crearemos un nuevo branch, el cual nombraremos css y en el cual agregaremos nuestro archivo `style.css` y realizamos unos pequeños cambios a nuestro h1. 

``` 
h1{  

    font-size:50px;  
	background-color: yellow;  

} 

```   

También modificaremos nuestro `index.html` agregándole la referencia de nuestro css de la siguiente manera. 

``` 
<!DOCTYPE html> 

<link href="css/style.css" rel="stylesheet" type="text/css">  //Agregando referencia de nuestro css 
  
<html lang="en"> 
    <head> 
        <h1>Hola mundo</h1> 
    </head> 
    <body> 
    </body> 

</html> 
``` 
  

Ahora solamente guardamos, agregamos y hacemos commit de nuestros cambios.  


``` 
➜  css git:(css) gst 

On branch css 
Changes not staged for commit: 

  (use "git add <file>..." to update what will be committed) 
  (use "git checkout -- <file>..." to discard changes in working directory) 

    modified:   ../index.html   

Untracked files: 

  (use "git add <file>..." to include in what will be committed) 

 
    ./ 

no changes added to commit (use "git add" and/or "git commit -a") 

➜  css git:(css) ✗ git add ../index.html 
➜  css git:(css) ✗ gcmsg "Agregando referencia de nuestro css" 
[css bb4b654] Agregando referencia de nuestro css 
1 file changed, 2 insertions(+) 
➜  css git:(css) ✗ git add ./ 
➜  css git:(css) ✗ gcmsg "Agregando nuestro style.css" 
[css 4971b29] Agregando nuestro style.css 
1 file changed, 4 insertions(+) 
create mode 100644 css/style.css 

``` 
  

Por el momento la estructura de nuestro archivo quedara de la siguiente forma: 

     ▾ practices-git/ 
         ▾ css/ 
             /* style.css 
         <> index.html 

Ahora nos cambiaremos a nuestra rama master con el siguiente comando 

    git checkout master 

 
Y repetiremos el mismo paso que hicimos con el css pero ahora agregando nuestro archivos js, quedando de la siguiente manera   

``` 
➜  practices-git git:(master) gco -b js 
Switched to a new branch 'js' 
➜  practices-git git:(js) mkdir js 
➜  practices-git git:(js) gst      

On branch js 

Changes not staged for commit: 
  (use "git add <file>..." to update what will be committed) 
  (use "git checkout -- <file>..." to discard changes in working directory) 

    modified:   index.html 

Untracked files: 

  (use "git add <file>..." to include in what will be committed) 

    js/ 

no changes added to commit (use "git add" and/or "git commit -a") 

➜  practices-git git:(js) ✗ git add index.html  
➜  practices-git git:(js) ✗ gcmsg "referenciando script y agregando button" 
[js c186615] referenciando script y agregando button 
1 file changed, 4 insertions(+) 
➜  practices-git git:(js) ✗ gst 

On branch js 

Untracked files: 

  (use "git add <file>..." to include in what will be committed) 
    
    js/ 

nothing added to commit but untracked files present (use "git add" to track) 

➜  practices-git git:(js) ✗ git add js/ 
➜  practices-git git:(js) ✗ gcmsg "Agregando MyScript.js" 
[js ee5e1f7] Agregando MyScript.js 
1 file changed, 3 insertions(+) 
create mode 100644 js/myScript.js 
➜  practices-git git:(js) 

``` 

Agrego el archivo `myScript.js`:  

``` 

function myFunction() { 
   document.getElementById("demo").innerHTML = "Paragraph changed."; 
} 

``` 

La modificación que se le hizo al `index.html` 

``` 

<!DOCTYPE html> 

  <html lang="en"> 

    <head> 
        <h1>Hola mundo</h1> 
    </head> 
    <body> 

        <p id="demo">A Paragraph.</p> 

        <button type="button" onclick="myFunction()">Puchame</button> 

        <script src="myScript.js"></script> 
    </body> 
</html>  

``` 

Y la estructura de nuestro  `branch js`   

     ▾ practices-git/ 
         ▾ js/ 
             /* myScript.js 
         <> index.html   

Ahora toca realizar la parte interesante, en la cual aplicaremos por primera vez nuestro rebase, por lo que nos mantendremos en nuestro `branch js` y escribiremos lo siguiente en nuestra línea de comandos: 

    git rebase css   

Como podrás ver ahora ya tienes los cambios de nuestro `branch css` dentro de nuestro `branch js`  


``` 

➜  practices-git git:(js) git rebase css 

First, rewinding head to replay your work on top of it... 

Applying: referenciando script y agregando button 

Applying: Agregando MyScript.js 

➜  practices-git git:(js) ls 

css  index.html  js 

➜  practices-git git:(js)   

```   

> Y.…¿Como fue que esto sucedió? 

Te lo mostrare con la siguiente imagen.  
  

<center> 
    <img class="special-img-class" src="/img/rebase/rebase.gif" width="850" />  
</center> 


Como podrás ver en la imagen primero creamos nuestro `branch css` e hicimos algunos commits, después nuestro `branch js` e igual realizamos algunos commits. Después realizamos nuestro rebase cuando estábamos posicionados en el `branch js` para llevar todos los cambios que teníamos en esta rama sobre el `branch css`.  

Lo cierto es que existen muchos tipos de rebase, pero primordialmente esta es la forma más sencilla de realizar un rebase para poder tomar los cambios que hemos realizado en otras ramas y adecuarlo a la que nosotros requeramos en un futuro o al mismo `branch master`.   

Espero que te haya servido esta explicación, si llegaras a tener alguna duda u observación con respecto a mi post puedes contactarme como @onahump en twitter y github. 

  

 
 
 