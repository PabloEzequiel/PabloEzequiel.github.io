---
layout: post
comments: false
title:  "CodeLab: Firebase de googlesamples"
date:   2016-05-01 19:08:44 -0300
categories: Codelab Firebase googlesamplesr
---
Desde que vi los videos del Google I/0 2016, me llamó la atención las posibilidades de Firebase: Fué uno de los productos destacados del Google I/O. Nosotros como desarrolladores: ¿Como podemos sacarle provecho?¿De que forma se configura?¿Que se puede hacer con el uso gratuito de la plataforma?

Vamos a tratar de encontrar respuestas a estras preguntas, mientras recorremos el [CodeLab de Google de Firebase][google-codelab-firebase-1]{: target="new"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat
</pre>

Clonamos el proyecto:

{% highlight git %}
$ git clone https://github.com/firebase/friendlychat
{% endhighlight %}

Y de aquí vamos a [Firebase](https://www.firebase.com/){:target="fb"}. En mi caso, ya estaba dado de alta en Firebase [cuando realicés mis primeras pruebas en la plataforma][pncn-post-firebase-1]{: target="pncn"}... por cierto, sin demasiado éxito, o con un alto grado de fracaso...


## Paso 01: Creamos nuestro proyecto en Firebase

Sigueindo al CodeLab, denominamos al proyecto **FriendlyChat** dentro de la consola de **Firebase**

![Firebase screenshot](/assets/post_009_img1.png)

Una vez creado el pryecto, vemos la siguiente pantalla de Firebase:

![Firebase screenshot](/assets/post_009_img2.png)

Y después de presionar el boton de Firebase </> tenemos el código para Añadir ***Firebase a nuestra aplicación web***

![Firebase screenshot](/assets/post_009_img3.png)

Agregamos del snippet de **Firebase Console > Overview > Add Firebase to your web app**

![Firebase screenshot](/assets/post_009_img4.png)

## Paso 02: Enable Google Auth

Ahora debemos habilitar el **Google Sign In** en lai izquierda dentro de AUTH

![Firebase screenshot](/assets/post_009_img5.png)


## Paso 03: Instalamos Firebase CLI (Command Line Interface)

Veamos como instalamos Firebase Command Line Interface.

¿Que es Firebase Hosting? El siguiente video oficial lo explica de una forma concisa:


<iframe width="420" height="315" src="https://www.youtube.com/watch?v=jsRVHeQd5kU" frameborder="0" allowfullscreen="allowfullscreen"></iframe>


Basicamwente nos permite centrarnos mas en las construicción de nuestra aplicación, que en la configuración de la plataforma.


[google-codelab-firebase-1]:  https://codelabs.developers.google.com/codelabs/firebase-web/index.html
[pncn-post-firebase-1]:       http://www.probarnocuestanada.com/2016/04/what-about-firebase.html
