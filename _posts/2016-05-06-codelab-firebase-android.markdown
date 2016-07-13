---
layout: post
comments: false
title: ¿Como utilizar Firebase con Android? FriendlyChat App
date: '2016-05-06 19:08:44 -0300'
categories: CodeLab GoogleSamples Android Firebase Android
comments: true
---

Continuado con la intención de seguir los CodeLab de Firebase, vamos dedicar este post a compentar las experiencias con el [CodeLab de Firebase para Android](https://codelabs.developers.google.com/codelabs/firebase-android/index.html?index=..%2F..%2Findex#0){: target="clgg"}.

# Contexto

Antes de empezar el seguimiento de este CodeLab, ya había completado dos anteriores, sobre [Firebase y la web]({% post_url 2016-05-01-codelab-firebase-web %}){:target="cl1"} y [Firebase y con iOS y swift]({% post_url 2016-05-05-codelab-firebase-ios-swift %}){:target="cl1"}, por lo cual, el trabajo de confgurar la **_consola de Firebase_** para la aplicación **_FriendlyChat_**, ya esta practicamente realizado.

# Comencemos

Directorios de trabajo:

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat/android
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat/android-start
```

Clonamos el proyecto:

{% highlight bash %} $ git clone https://github.com/firebase/friendlychat {% endhighlight %}

{% include google-adsense.html %}<br>

# Paso 01: Compilar con el Android Studio

Vamos a abrir el proyecto (no la versión starter, sino la finalizada) con el Android Studio.

El primer error que nos da es:

{% highlight bash %} Error:Cause: peer not authenticated {% endhighlight %}

Para solucionar esto, vamos a seguir con los pasos 4 y 5 del CodeLab, que hacen la generación de las credenciales.

**Solución:** Este es un error conocido para nosotros y vamos a intentar solucionarlo con los pasos mencionados en el [Post de Google Sign-In Services]({% post_url 2016-05-15-codelab-google-services %}){:target="p"}

- Vamos a registrar la parte **Android** de la App en la consola
- Vamos a volver a subir la clave SHA-1 para Android en la consola
- Vamos a obtener el archivo **google-services.json**

{% include google-adsense.html %}<br>

# Paso 02: Configuración en la consola de developer de google

Como el proyecto **FriendlyChat** ya exisitan.... Vamos a acceder a [nuestra consola de Google](https://console.developers.google.com/apis/credentials?project=) {:target="c2"} con la [sigueinte url](https://console.developers.google.com/apis/credentials?project=){:target="c2"}.

Y elegimos **Crear credenciales** y **ID Cliente de OAuth**:

![Android FriendlyChat with Firebase - screenshot](/assets/post_011_img1.png)

Completamos los datos para Android: nombre, la clave SHA-1 que identifica nuestra app (nuestra huella digital) y el nombre de paquete:

![Android FriendlyChat with Firebase - screenshot](/assets/post_011_img2.png)

Después de lo cual obtenemos la clave que estámos necesitando:

![Android FriendlyChat with Firebase - screenshot](/assets/post_011_img4.png)

En realidad el paso anterior estuvo de mas .... ya que debería haber realizado el alta desde la [consola de Firebase](https://console.firebase.google.com/){:target="new"}:

{% include google-adsense.html %}<br>

# Paso 03: Configuración en la consola de Firebase de Google

En la [consola de Firebase](https://console.firebase.google.com/){:target="new"} elegimos nuestra proyecto FriendlyChat que ya estaba creado, y añadimos la configuración para **aplicaciones Android**

![Android FriendlyChat with Firebase - screenshot](/assets/post_011_img5.png)

Luego, agregamos el **package name** y la clave **SHA-1**:

![Android FriendlyChat with Firebase - screenshot](/assets/post_011_img6.png)

Y finalmente descargamos el **google-services.json** que copiamos dentro del directorio **app** de la aplicación:

![Android FriendlyChat with Firebase - screenshot](/assets/post_011_img7.png)

{% include google-adsense.html %}<br>

# Paso 04: Ejecutamos la aplicación

Observamos que es posible ejecutar la aplicación y que, una vez pasado el sign-in se recuperan los mensajes creados desde los tutoriales de [Firebase con swift]({% post_url 2016-05-05-codelab-firebase-ios-swift %}){:target="new2"} y [Firebase con Objective-c]({% post_url 2016-05-04-codelab-firebase-ios-objc %}){:target="new3"}

![Android FriendlyChat with Firebase - screenshot](/assets/post_011_img8.png)

Hemos logrado el obejtivo de que la aplicación de Android también funciones.

Con esto damos por cerrado el seguimiento del CodeLab de Android.

En este mismo CodeLab, en la página de Google developers, se muestra como trabajar con AdMob y otras cosas mas.
