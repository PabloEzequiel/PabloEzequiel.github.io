---
layout: post
comments: false
title: ¿Que nos ofrece el 'Google VR SDK' para Android?
date: '2016-04-22 19:08:44 -0300'
categories: CodeLab GoogleSamples Android VR VirtualReality
---

El [Google VR SDK](https://developers.google.com/vr/android/download){:target="new"} nos abre las puertas al desarrollo de aplicaciones para Realidad Virtual, Google Cardboard y seguramente muchas otras cosas mas...

Veamos a través de este post, algunas de las cosas de **Google VR SDK** nos ofrece:

# Comencemos

Directorio de trabajo:

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/gvr-android-sdk
```

Ejecutamos el código:

{% highlight bash %} $ git clone <https://github.com/googlevr/gvr-android-sdk.git> {% endhighlight %}

# Paso 01: Descargar Google VR SDK

Lo primero que me llamó la atención es que debemos aceptar los TyC para descargar el SDK de VR. No es que esté mal, por su puesto, solamente es que no lo esperaba:

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_01.png){: .center-image }

Clonamos el repositorio Git:

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_02.png){: .center-image }

Y vemos nuestro entorno de trabajo dentro del **excelente** Atom Editor:

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_03.png){: .center-image }

{% include google-adsense.html %}<br>

# Paso 02: Compilamos la aplicación VR de ejemplo

La aplicación de ejemplo se llama **Treasure Hunt sample app**, y se trata es una aplicación de búsqueda del tesoro.

Entre otras cosas, va a demostrar el uso de las **Google Cardboard**.

Cone el **Android Studio** abrimos los proyectos del directorio **gvr-android-sdk**

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/gvr-android-sdk
```

Tengamos cuidado de no confundir al directorio, son varios proyectos. Veamos la imagen:

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_04.png){: .center-image }

Veamos los proyectos importados, también ejecuté en **Sync gradle**:

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_05.png){: .center-image }

{% include google-adsense.html %}<br>

# Paso 03: Ejecutamos la aplicación VR de ejemplo

Elegimos el proyecto **sdk-treasurehunt**

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_06.png){: .center-image }

Y el destino de ejecución/deployment será sobre el dispositivo fisico (no sobre un emulador):

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_07.png){: .center-image }

Vemos como resultado de la ejecución, un Cubo de Colores que se desplaza por el espacio. Tal como se ve, es una aplicación para **Google Cardboard**:

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_08.jpg){: .center-image }

# Paso 04: Ejecutamos la aplicación SimplePanoWidget

![Google VR SDK - screenshot](/assets/post_008_SdkVr_img_09.png){: .center-image }

En este punto vamos a dejar cerrado por ahora el post, con el objetivo cumplido de ver el funcionamiento de la app para Google Cardboard.

Quedará pendiente analizar los componentes claves de código fuente, los cuales están [explicados en la documentación oficial](https://developers.google.com/vr/android/samples/treasure-hunt){:target="gog"}

# Next Steps

Ejecutar tambien video. Ejecutar la version para iOS.
