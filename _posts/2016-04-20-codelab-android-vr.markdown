---
layout: post
comments: false
title:  "CodeLab: Android VR de googlesamples"
date:   2016-04-20 19:08:44 -0300
categories: Android CodeLab googlesamplesr
---
Veamos que sucede si intentamos seguir algún ejercicio sobre realidad virtual (VR) sobre Android.
¿Que tan complicado es? ¿Cual es la versión mínima de dispositivos Android que se necesita? ¿Como se graban las imágenes para que se muestren dentro de la app de realidad virtual?

Sigamos los ejercicio del [Google Codelab de VR][google-android-vr-codelab] para encontrar estas respuestas.

## Comencemos

Directorio de trabajo, en nuestra PC utilizaremos la carpeta:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-vr-codelab
</pre>

Ejecutamos el código:

{% highlight bash %}
$ git clone https://github.com/googlecodelabs/vr_view_app_101.git
{% endhighlight %}


Resultado:

{% highlight bash %}
$ pwd
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-vr-codelab
$ git clone https://github.com/googlecodelabs/vr_view_app_101.git
Cloning into 'vr_view_app_101'...

remote: Counting objects: 94, done.
remote: Total 94 (delta 0), reused 0 (delta 0), pack-reused 94
Unpacking objects: 100% (94/94), done.
Checking connectivity... done.

{% endhighlight %}

# Paso 01: Abrimos y Compilamos el proyecto android-vr-codelab

Luego, abrimos el proyecto con el Adnroid Studio, y lo ejecutamos:

![importacion paso1 screenshot](/assets/post_008_img1.png){: .center-image }

La primera página de la app:

![importacion paso1 screenshot](/assets/post_008_img2.png){: .center-image }

La segunda página de la app:

![importacion paso1 screenshot](/assets/post_008_img3.png){: .center-image }

A simple vista, la app tiene dos imágens, dos fragments (Gorilla + Wellcome), y un main activity.

{% include google-adsense.html %} <br/>

# Paso 02: Generamos una imagen de VR

La aplicación ya viene con una imagén de VR, pero vamos a intentar generar nuestra propia imagen:

Para Android deberíamos utilizar [Cardboard Camera app](https://play.google.com/store/apps/details?id=com.google.vr.cyclops&hl=es_419){:target="vr1"}. ¿Y para iOS?
En principio, no esta la aplicación de Google en iOS

Veamos como es la imagen de ejemplo que viene con la APP:

![importacion paso1 screenshot](/assets/post_008_img_3d_01.jpg){: .center-image }

¿Como podríamos generala?

Quizá, si tenemos fotos 360 generadas con iOS, podríamos editarlas con el GIMP y duplicarlas...
Mas adelante en el post, vamos a probar esta idea.

Por ahora vamos a saltear este paso, y utilizar para seguir al codelab a la imagen de ejemplo que viene con el proyecto.

O sea, nuestro:

app/src/main/assets/converted.jpg

seria:

app/src/main/assets/sample_converted.jpg

{% include google-adsense.html %} <br/>

# Paso 03: Agregamos Andrid sdk

Tenemos que agregar el Android Google VR SDK a nuestro proyecto ¿Como lo hacemos?

Primero, desde el **Android Studio**, con una terminal ejecutamos el comando de Git:

{% highlight bash %}
$ git clone https://github.com/googlevr/gvr-android-sdk.git
{% endhighlight %}

Veamos que sucede:

![importacion paso1 screenshot](/assets/post_008_img5.png){: .center-image }

Y aparce **avr-android-sdk** dentor del codelab listo para que lo agreguemos en el gradle:

![importacion paso1 screenshot](/assets/post_008_img6.png){: .center-image }

En el  **settings.gradle** agregamos:

{% highlight bash %}
include ':app'
include ':gvr-android-sdk/libraries:audio'
include ':gvr-android-sdk/libraries:base'
include ':gvr-android-sdk/libraries:common'
include ':gvr-android-sdk/libraries:commonwidget'
include ':gvr-android-sdk/libraries:panowidget'
include ':gvr-android-sdk/libraries:videowidget'
{% endhighlight %}

En el  **build.gradle** de app agregamos:

{% highlight bash %}
dependencies {
    compile 'com.android.support:appcompat-v7:23.4.0'
    compile 'com.android.support:design:23.4.0'
    compile project(':gvr-android-sdk/libraries:common')
    compile project(':gvr-android-sdk/libraries:commonwidget')
    compile project(':gvr-android-sdk/libraries:panowidget')
}
{% endhighlight %}


## ERROR: Lamentablemente perdi el proyecto... deberia retomar desde el paso 5 del CodeLab
https://codelabs.developers.google.com/codelabs/vr_view_app_101/index.html#5


# Paso 04: Editando código Andrid sdk

Tenemos que agregar la imagen, y se va a cargar de forma eficientes. Para esto se siguen las recomendaciones de [Loading Large Bitmaps Efficiently](https://developer.android.com/training/displaying-bitmaps/load-bitmap.html){:target new}

Seguimos el CodeLab y finalizamos la primera parte, que es la pureba de VR con una imagens, con los siguientes resultados:

# Error #01: Poco espacio de Heap para Graddle

Me dice:
<pre>
To run dex in process, the Gradle daemon needs a larger heap.
It currently has approximately 910 MB.

For faster builds, increase the maximum heap size for the Gradle daemon to more than 2048 MB.
To do this set org.gradle.jvmargs=-Xmx2048M in the project gradle.properties.
For more information see https://docs.gradle.org/current/userguide/build_environment.html
</pre>

**Solución:** en mi caso, como no tenia el archivo ***gradle.properties*** lo tuve que crear, y luego agregué
org.gradle.jvmargs = -Xmx2048m

De esta manera se corrigió ese error.

# Error #02: Poco espacio de Heap para Graddle

El error que me da es el siguiente:

<pre>
$ adb shell pm install -r "/data/local/tmp/com.google.devrel.vrviewapp"
	pkg: /data/local/tmp/com.google.devrel.vrviewapp
Failure [INSTALL_FAILED_NO_MATCHING_ABIS]

$ adb shell pm uninstall com.google.devrel.vrviewapp
DELETE_FAILED_INTERNAL_ERROR
Error while Installing APK
</pre>

Desconozco si esta asociado a que estoy ejecutando sobre el emulador.

Intente como soluciones, limpiar el proyecto con un **gradle clean** y también desintalar la versioón anterior del .apk del emulador, pero el error persiste.


Recordemos que solicitaba
An Android Device running Android 5.0 (Lollipop) or greater.
Y también un dispositivo fisico...

Como yo estoy utilizando el emulador, voy a suspender por ahora el este punto el post, en vista de que no es posible avanzar mucho mas.

https://codelabs.developers.google.com/codelabs/vr_view_app_101/index.html#4


## Next Steps

Ver el siguiente converor de Google Api para realidad virtual [google-api-vr-link][https://storage.googleapis.com/cardboard-camera-converter/index.html]{: target="new"}



[google-android-vr-codelab]:  https://codelabs.developers.google.com/codelabs/vr_view_app_101/index.html
[google-api-vr-link]:          https://storage.googleapis.com/cardboard-camera-converter/index.html
