---
layout: post
comments: false
title:  "CodeLab: Firebase iOS (Obj-C) de googlesamples"
date:   2016-05-05 19:08:44 -0300
categories: Codelab Firebase iOS googlesamples Objective-c
---
Continuado con la intención de seguir los CodeLab de Firebase, vamos dedicar este post a compentar las experiencias con el CodeLab de Firebase para iOS. Este post es la versión de Objecti-c

El CodeLab que seguimoes es el sigueinte [Firebase iOS Codelab objective c
](https://codelabs.developers.google.com/codelabs/firebase-ios-objc/index.html?index=..%2F..%2Findex){:target="cdlios"}

Hay algunos prerrequisitos que hay que complir, como tener el Xcode, el CocoaPod, pero lo que es nuevo para el desarrollador de iOS es que hay que [configuar iOS para Firebase] (https://firebase.google.com/docs/ios/setup){:target="cdls"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat
</pre>

Clonamos el proyecto:

{% highlight git %}
$ git clone https://github.com/firebase/friendlychat
{% endhighlight %}

Obervemos que cuando clonamos el proyecto, nos baja todas las versiones de clientes de **Firebase**: O sea, versiones **WEB**, **iOS objective c**, **iOS swift**, **Android**:

![Firebase screenshot](/assets/post_012_img1.png)

En este post, utilizamos los de objective-c: **objc** y **objc-starter**

La diferencia, es que el "start" tiene el código de inicio, y que nos permite a nosotros agregarle más código a medida que avanzamos con el CodeLab.

{% include google-adsense.html %} <br/>

## Paso 01: Instalamos Cocoa y CocoaPod

Ya lo teniamos instalado **Cocoa y CocoaPod**, por las otras pruebas de la [versión de swift y firebase que hicimos]({% post_url 2016-05-05-codelab-firebase-ios-swift %}){:target="p"}

Con lo cual solo queda ejecutar en nuestro di **./googlesamples/firebase/friendlychat/ios-starter/objc-starter**:

{% highlight bash %}
$ pod update
{% endhighlight %}

Veamos el resultado de la instalación:

![Firebase en iOS con Objecti-c](/assets/post_012_img2.png)

A continuación, vamos a abrir el proyecto Xcode objective-c **FriendlyChatObjC.xcworkspace** y compilarlo a ver que pasa.

Me da el siguiente error, que también me dio cuando intenté compilar las versiones swift de los protectos

<pre>
ld: library not found for -lPods-FriendlyChatObjC
clang: error: linker command failed with exit code 1 (use -v to see invocation)
</pre>

Vemos la pantalla de error:

![Firebase en iOS con Objective-c](/assets/post_012_img3.png)

**Solución:**

Simplemente, el error es por un poco de falta de experiencias de mi parte con los proyectos Cocoa.
Cuando hay un proyecto Cocoa, hay que abrir:

- FriendlyChatSwift.xcworkspace  (Si!)
- FriendlyChatObjC.xcodeproj   (No!)

Veamos que cuando efectivamente, el proyecto se abre OK:

![Firebase en iOS con Objective-c](/assets/post_012_img4.png)

 Y podemos ver la aplicación funcionando:

![Firebase en iOS con Objective-c](/assets/post_012_img5.png)


.... por ahora suspendemos el post aqui...
Y seguimos con el tema en la versión de iOS
