---
layout: post
comments: false
title:  "GitHub: Android NDK de googlesamples"
date:   2016-04-01 19:08:44 -0300
categories: GitHub NDK Android googlesamples
---
Vamos a realizar algunas pruebas sobre [Android NDK][github-android-ndk]:{:target="ndk"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-ndk-master
</pre>

Android NDK son ejemplos de utilización de codigo nativo.

Observemos que googlesamples nos ofrece varios ejemplos desde GitHub.
Estamos tomando la rama **master** porque nos interesa utilizar al graddle experimental.  

![importacion paso1 screenshot](/assets/post_005_googlesamples_android_ndk.png)

## Proyecto 01: hello-jni

Vamos a comenzar compilando el primer proyecto hello-jni

Seguimos las indicaciones de https://github.com/googlesamples/android-ndk/tree/master/hello-jni

![importacion paso2 screenshot](/assets/post_005_img2.png)

Launch Android Studio.
Open the sample directory.
Open File/Project Structure...
Click Download or Select NDK location:

![importacion paso2 screenshot](/assets/post_005_img3.png)

Click Tools/Android/Sync Project with Gradle Files.
Click Run/Run 'app'.

![importacion paso2 screenshot](/assets/post_005_img4.png)

Con lo cual finalizamos el ejercicio, desde el punto de vista de compilación/ejecución de Andorid NDK y JNI.
Con graddle experimental

¿Que podemos obserar y aprender?

Observemos la clase Java

![importacion paso2 screenshot](/assets/post_005_img5.png)

El objeto c

![importacion paso2 screenshot](/assets/post_005_img6.png)

Y ademas el script de graddle experimental:

![importacion paso2 screenshot](/assets/post_005_img7.png)





[github-android-ndk]:                https://github.com/googlesamples/android-ndk
