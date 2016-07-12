---
layout: post
comments: false
title: ¿Cómo funciona la Realidad Virtual (VR) en Android?
date: '2016-04-20 19:08:44 -0300'
categories: CodeLab GoogleSamples Android VR VirtualReality
comments: true
---

Vamos seguir el ejercicio [CodeLab de GoogleSamples de Realidad Virtual (VR)][google-android-vr-codelab]{:target="new"} para entender como funciona la VR en Android y responder preguntas como:

- ¿Cómo funciona la Realidad Virtual (VR) en Android?
- ¿Que tan complicado es?
- ¿Cual es la versión mínima de dispositivos Android que se necesita?
- ¿Como se graban las imágenes para que se muestren dentro de la app de Realidad Virtual?

**Aclaración 1:** El CodeLab muestra como integrar las vistas de 360 grados en una aplicación Android, pero no como convertirla al modo binocular, o sea, con la pantalla dividida, al cual estamos acostumbrados cuando vemos las aplicaciones con el **Google Cardboard**.

Dicho de otra manera, para este tutorial no se utiliza en **Google Cardboard**.

**Aclaración 2:** El objetivo del post es ejecutar y compilar el ejercicio finalizado del CodeLab, y detenerse en donde resulte interesante. El paso a paso, y como se progama está en el [CodeLab de GoogleSamples de Realidad Virtual (VR)][google-android-vr-codelab]{:target="new"}

# Comencemos

Directorio de trabajo, en nuestra PC utilizaremos la carpeta:

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-vr-codelab
```

Ejecutamos el código:

{% highlight bash %} $ git clone https://github.com/googlecodelabs/vr_view_app_101.git {% endhighlight %}

Resultado:

{% highlight bash %}
$ pwd /Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-vr-codelab
$ git clone https://github.com/googlecodelabs/vr_view_app_101.git
Cloning into 'vr_view_app_101'...

remote: Counting objects: 94, done.
remote: Total 94 (delta 0), reused 0 (delta 0), pack-reused 94
Unpacking objects: 100% (94/94), done.
Checking connectivity... done.

{% endhighlight %}

{% include google-adsense.html %}<br>

# Paso 01: Abrimos y Compilamos el proyecto android-vr-codelab

Luego, abrimos el proyecto con el Adnroid Studio, y lo ejecutamos:

![VR en Android - screenshot](/assets/post_008_img1.png){: .center-image }

La primera página de la app:

![VR en Android - screenshot](/assets/post_008_img2.png){: .center-image }

La segunda página de la app:

![VR en Android - screenshot](/assets/post_008_img3.png){: .center-image }

A simple vista, la app tiene dos imágens, dos fragments (Gorilla + Wellcome), y un main activity.

{% include google-adsense.html %}<br>

# Paso 02: Generamos una imagen de VR

La aplicación ya viene con una imagén de VR, pero vamos a intentar generar nuestra propia imagen:

Para Android deberíamos utilizar [Cardboard Camera app](https://play.google.com/store/apps/details?id=com.google.vr.cyclops&hl=es_419){:target="vr1"}. ¿Y para iOS? En principio, no esta la aplicación de Google en iOS

Veamos como es la imagen de ejemplo que viene con la APP:

![VR en Android - screenshot](/assets/post_008_img_3d_01.jpg){: .center-image }

¿Como podríamos generala?

Quizá, si tenemos fotos 360 generadas con iOS, podríamos editarlas con el GIMP y duplicarlas... Mas adelante en el post, vamos a probar esta idea.

Por ahora vamos a saltear este paso, y utilizar para seguir al codelab a la imagen de ejemplo que viene con el proyecto.

O sea, nuestro:

app/src/main/assets/converted.jpg

seria:

app/src/main/assets/sample_converted.jpg

{% include google-adsense.html %}<br>

# Paso 03: Agregamos Andrid sdk

Tenemos que agregar el Android Google VR SDK a nuestro proyecto ¿Como lo hacemos?

Primero, desde el **Android Studio**, con una terminal ejecutamos el comando de Git:

{% highlight bash %} $ git clone https://github.com/googlevr/gvr-android-sdk.git {% endhighlight %}

Veamos que sucede:

![VR en Android - screenshot](/assets/post_008_img5.png){: .center-image }

Y aparce **avr-android-sdk** dentor del codelab listo para que lo agreguemos en el gradle:

![VR en Android - screenshot](/assets/post_008_img6.png){: .center-image }

En el **settings.gradle** agregamos:

{% highlight bash %} include ':app' include ':gvr-android-sdk/libraries:audio' include ':gvr-android-sdk/libraries:base' include ':gvr-android-sdk/libraries:common' include ':gvr-android-sdk/libraries:commonwidget' include ':gvr-android-sdk/libraries:panowidget' include ':gvr-android-sdk/libraries:videowidget' {% endhighlight %}

En el **build.gradle** de app agregamos:

{% highlight bash %} dependencies { compile 'com.android.support:appcompat-v7:23.4.0' compile 'com.android.support:design:23.4.0' compile project(':gvr-android-sdk/libraries:common') compile project(':gvr-android-sdk/libraries:commonwidget') compile project(':gvr-android-sdk/libraries:panowidget') } {% endhighlight %}

{% include google-adsense.html %}<br>

# Paso 04: Editando código Andrid sdk

Tenemos que agregar la imagen, y se va a cargar de forma eficientes. Para esto se siguen las recomendaciones de [Loading Large Bitmaps Efficiently](https://developer.android.com/training/displaying-bitmaps/load-bitmap.html){:target new}

Seguimos el CodeLab y finalizamos la primera parte, que es la pureba de VR con una imagens, con los siguientes resultados:

# Error #01: Poco espacio de Heap para Graddle

Me dice:

```
To run dex in process, the Gradle daemon needs a larger heap.
It currently has approximately 910 MB.

For faster builds, increase the maximum heap size for the Gradle daemon to more than 2048 MB.
To do this set org.gradle.jvmargs=-Xmx2048M in the project gradle.properties.
For more information see https://docs.gradle.org/current/userguide/build_environment.html
```

**Solución:** en mi caso, como no tenia el archivo **_gradle.properties_** lo tuve que crear, y luego agregué org.gradle.jvmargs = -Xmx2048m

De esta manera se corrigió ese error.

# Error #02: [INSTALL_FAILED_NO_MATCHING_ABIS]

El error que me da es el siguiente:

```
$ adb shell pm install -r "/data/local/tmp/com.google.devrel.vrviewapp"
    pkg: /data/local/tmp/com.google.devrel.vrviewapp
Failure [INSTALL_FAILED_NO_MATCHING_ABIS]

$ adb shell pm uninstall com.google.devrel.vrviewapp
DELETE_FAILED_INTERNAL_ERROR
Error while Installing APK
```

Desconozco si esta asociado a que estoy ejecutando sobre el emulador.

Intente como soluciones, limpiar el proyecto con un **gradle clean** y también desintalar la versioón anterior del .apk del emulador, pero el error persiste.

{% include google-adsense.html %}<br>

## Prueba 01: ¿Que pasa si reempplazo el emulador de Android por Gennymotion?

Da el mismo error:

{% highlight bash %} 07/03 18:07:05: Launching app $ adb push /Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-vr-codelab/vr_view_app_101/app/build/outputs/apk/app-debug.apk /data/local/tmp/com.google.devrel.vrviewapp $ adb shell pm install -r "/data/local/tmp/com.google.devrel.vrviewapp" pkg: /data/local/tmp/com.google.devrel.vrviewapp Failure [INSTALL_FAILED_NO_MATCHING_ABIS]

$ adb shell pm uninstall com.google.devrel.vrviewapp DELETE_FAILED_INTERNAL_ERROR Error while Installing APK {% endhighlight %}

Que significa este error?

De un [post de stackoverflow](http://stackoverflow.com/questions/24572052/install-failed-no-matching-abis-when-install-apk){:target="new"} leemos:

_INSTALL_FAILED_NO_MATCHING_ABIS is when you are trying to install an app that has native libraries and it doesn't have a native library for your cpu architecture. For example if you compiled an app for armv7 and are trying to install it on an emulator that uses the Intel architecture instead it will not work._

O sea, que la arquitectura del emulador que estamos utilizando, no es la esperada por el apk.

El emulador que utilizamos tiene una arquitectura **x86**, vamos a dar de alta otro con arquitectura **arm** Aclaramos que también da el mismo error de ABI con otro emulador **x96_64**

![VR en Android - screenshot](/assets/post_008_img7.png){: .center-image }

Veamos al emulador dado de alta, con arquitectura **arm**:

![VR en Android - screenshot](/assets/post_008_img8.png){: .center-image }

Y ahora solo queda ejecutar la aplicación sobre ese emulador:

![VR en Android - screenshot](/assets/post_008_img9.png){: .center-image }

Nos aparece un mensaje que nos dice:

_Running an x86 Based Android Virtual Device (AVD) is 10X faster. We strongly recommend creating a new AVD_

![VR en Android - screenshot](/assets/post_008_img10.png){: .center-image }

Ese el problema de utilizar un **arm** en vez de un **x86**

{% include google-adsense.html %}<br>

# Error #02: [INSTALL_FAILED_NO_MATCHING_ABIS] en ARM:

{% highlight bash %} 07/03 19:08:21: Launching app Error while waiting for device: Timed out after 300seconds waiting for emulator to come online. {% endhighlight %}

Me parece que la posibilidad de avanzar con estos proyectos de VR es directamente utilizar celulares Android fisicos.

Como comentario, los emuladores corren sobre emuladores en, por ejemplo, una Mac, con un procesador [Intel Code i5 de arquitectura x86](https://es.wikipedia.org/wiki/Intel_Core_i5_(Nehalem)){:target="wiki"}

Mientras que los celulares suelen correr sobre dispositivos ARM:

Por Ejemplo, el **Samsung Samsung I9300 Galaxy S III** tiene un procesador **Quad-core 1.4 GHz Cortex-A9** y la wikipedia dice que el [Cortex-A9 tiene arquitectura ARM](https://en.wikipedia.org/wiki/ARM_Cortex-A9){:target="wiki"}

Por esta razón, correr un emuladores ARM en una MAC con procesador X86 es muchísimo mas lento.... Dejo un link muy bueno sobre las [Diferencias entre ARM y x86](https://www.pabloyglesias.com/guia-de-supervivencia-geek-diferencias-entre-procesadores-x86-y-arm/){:target="neww"}

{% include google-adsense.html %}<br>

# Error #03: En Andy API 19 vs API 17

Me da el Error que Android de Andy es versio 17 y la minima de esta App es versión 19...

# Error #03: Pruebo en un Motorla G

Voy a hacer la prueba en un **Moto G (Tercera Generacion)** que tiene la versión de **Android 5.1.1**. Lamentablemente este **Moto Gno No viene con Giroscopio** con lo cual hay aplicaciones de Realidad Virtual que no funcionan en el **Moto G (Tercera Generacion)**. Yo, desde mi costador de desarrollador, no hubiera comprado este MotoG si hubiera sabido esto de antemano:

![VR en Android - screenshot](/assets/post_008_img11.png){: .center-image }

... pero ahora es tarde...

Continuemos:

Tenemos como soporte el post sobre [Como conectar un Moto G al Android Studio](http://javaen.blogspot.com.ar/2015/10/como-conectar-un-moto-g-al-android.html){:target="javaen"}.

Observemos que pudimos ejecutar exitosamente la aplicación en el motorola:

, aunque no divide la imagen tal como lo necesita **Google Cardboard**:

![VR en Android - screenshot](/assets/post_008_img12.png){: .center-image }

Tal como aclaramos al inicio del post, esta aplicación muestra como integrar las vistas de 360 grados en una aplicación Android, pero no como convertirla al modo binocular, o sea, con la pantalla dividida, al cual estamos acostumbrados cuando vemos las aplicaciones con el **Google Cardboard**.

Dicho de otra manera, para este tutorial no se utiliza en **Google Cardboard**.

## Parte II: video

Avancemos con la segunda parte del CodeLab que tiene que ver con la incorporación de un video de VR

{% highlight bash %} dependencies { compile fileTree(dir: 'libs', include: ['*.jar']) compile 'com.android.support:appcompat-v7:23.4.0' compile 'com.android.support:design:23.4.0' compile project(':gvr-android-sdk/libraries:common') compile project(':gvr-android-sdk/libraries:commonwidget') compile project(':gvr-android-sdk/libraries:panowidget') compile project(':gvr-android-sdk/libraries:videowidget') } {% endhighlight %}

El **componente Java** asociado a la incorporación del video es **GorillaFragment.java**:

El resultado es la posibilidad de ver el Video 360 dentro de la App.

La siguiente imagen no le hace justicia al resultado, pero es un video 360 donde el Gorilla y su cria se mueven por la pantalla. Además de que desde nuestra perspectiva podemos ver todo el entorno en los 360 de ese bosque:

![VR en Android - screenshot](/assets/post_008_img13.png){: .center-image }

En este punto vamos a dar por cerrado el post, con la sensación de que aún queda mucho mas por aprender de los videos 360 y la realidad virtual. Aunque también, a través de los pasos recorridos en este post, y las dificultades técnicas que se presentaron, pudimos aprender al menos algunas cosas interesantes sobre estos temas.

## Next Steps

- Ver el siguiente conversor de Google Api para realidad virtual [google-api-vr-link]{: target="new"}

- Ver los ejemplos de [Google VR for Android](https://developers.google.com/vr/android/samples/vrview){: target="new2"}

[google-android-vr-codelab]: https://codelabs.developers.google.com/codelabs/vr_view_app_101/index.html
[google-api-vr-link]: https://storage.googleapis.com/cardboard-camera-converter/index.html
