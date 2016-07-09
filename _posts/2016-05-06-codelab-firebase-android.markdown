---
layout: post
comments: false
title:  "CodeLab: Firebase Android de googlesamples"
date:   2016-05-07 19:08:44 -0300
categories: Codelab Firebase Android googlesamples
---
Continuado con la intención de seguir los CodeLab de Firebase, vamos dedicar este post a compentar las experiencias con el [CodeLab de Firebase para Android](https://codelabs.developers.google.com/codelabs/firebase-android/index.html?index=..%2F..%2Findex#0){: target="clgg"}.

## Comntexto



Antes de empezar el seguimiento de este CodeLab, ya había completado dos anteriores, sobre [Firebase y la web]({% post_url 2016-05-01-codelab-firebase-web %}){:target="cl1"} y [Firebase y con iOS y swift]({% post_url 2016-05-05-codelab-firebase-ios-swift %}){:target="cl1"}, por lo cual, el trabajo de confgurar la ***consola de Firebase*** para la aplicación  ***FriendlyChat***, ya esta practicamente realizado.

## Comencemos

Directorios de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat/android
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat/android-start
</pre>

Clonamos el proyecto:

{% highlight git %}
$ git clone https://github.com/firebase/friendlychat
{% endhighlight %}

## Paso 01: Compilar con el Android Studio

Vamos a abrir el proyecto (no la versión starter, sino la finalizada) con el Android Studio.

El primer error que nos da es:

{% highlight bash %}
Error:Cause: peer not authenticated
{% endhighlight %}

Para solucionar esto, vamos a seguir con los pasos 4 y 5 del CodeLab, que hacen la generación de las credenciales
