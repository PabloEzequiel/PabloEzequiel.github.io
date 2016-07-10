---
layout: post
comments: false
title:  "¿Como utilizar Firebase con iOS (swift)? FriendlyChat App"
date:   2016-05-05 19:08:44 -0300
categories: CodeLab GoogleSamples Android Firebase iOS swift FriendlyChat
---
Continuado con la intención de seguir los CodeLab de Firebase, vamos dedicar este post a comentar las experiencias con el CodeLab de Firebase para iOS. Este post es la versión Swift.

El CodeLab que seguimoes es el sigueinte [Firebase iOS Codelab Swift (starter)
](https://codelabs.developers.google.com/codelabs/firebase-ios-swift/index.html?index=..%2F..%2Findex){:target="cdlios"}

Hay algunos prerrequisitos que hay que complir, como tener el Xcode, el CocoaPod, pero lo que es nuevo para el desarrollador de iOS es que hay que [configuar iOS para Firebase] (https://firebase.google.com/docs/ios/setup){:target="cdls"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat

#Utilizamos:
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat/ios-starter/swift-starter
</pre>

Clonamos el proyecto:

{% highlight git %}
$ git clone https://github.com/firebase/friendlychat
{% endhighlight %}

Obervemos que cuando clonamos el proyecto, nos baja todas las versiones de clientes de **Firebase**: O sea, versiones **WEB**, **iOS objective c**, **iOS swift**, **Android**:

![Firebase screenshot](/assets/post_012_img1.png)

En este post, utilizamos los de swift: **swift** y **swift-starter**

La diferencia, es que el "start" tiene el código de inicio, y que nos permite a nosotros agregarle más código a medida que avanzamos con el CodeLab.

{% include google-adsense.html %} <br/>

## Paso 01: Instalamos Cocoa y CocoaPod

Este es uno de los primeros requisitos:

¿Que son los **pod**? En dos palabras, los **pod** son un **gestor de dependecias para proyectos del framework Cocoa en iOS y Swift**. Mas info en [https://cocoapods.org/](https://cocoapods.org/){:target="cocoa1"} y [wiki Cocoa](https://es.wikipedia.org/wiki/Cocoa_(inform%C3%A1tica)){:target="cocoa"}

Para instalar Cocoa. tengo que ejecutar:

{% highlight bash %}
$ sudo gem install cocoapods
{% endhighlight %}

## Paso 02: Ejecutamos pod update sobre el proyecto Firebase

Vamos al directorio **ios-starter/swift-starter** y ejecutamos **pod update**

{% highlight bash %}
$ pwd
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat
$ cd ios-starter/swift-starter
$ pwd
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat/ios-starter/swift-starter
{% endhighlight %}

Luego ejecutamos según el Codelab

{% highlight bash %}
$ pod update
{% endhighlight %}

Me dio el siguiente error:

{% highlight bash %}
$ pod update

[!] Unable to add a source with url `https://github.com/CocoaPods/Specs.git` named `master`.
You can try adding it manually in `~/.cocoapods/repos` or via `pod repo add`.
{% endhighlight %}

Lo cual solucioné, ejecutando manualmente el Git con lo siguiente:

{% highlight bash %}
$ cd ~/.cocoapods/repos
$ git clone https://github.com/CocoaPods/Specs.git master
{% endhighlight %}

Con lo que finalemnte anduvo ok, ejecutado dentro del directorio **... friendlychat/ios-starter/swift-starter**

{% highlight bash %}
$ pod update
{% endhighlight %}


Los paquetes que instalo, son los enumerados en **Podfile**

{% highlight bash %}
$ cat Podfile
# FriendlyChat Codelab

use_frameworks!
platform :ios, '7.0'

pod 'Firebase/Storage'
pod 'Firebase/AdMob'
pod 'Firebase/Auth'
pod 'Firebase/Crash'
pod 'Firebase/Database'

pod 'Firebase/RemoteConfig'

target 'FriendlyChatSwift' do
end
{% endhighlight %}

Con este paso, sabemos que cumplimos con el primer **requerimiento** de tener instaldo **Cocoa** y **CocoaPod**

## Paso 03: Compilamos la aplicacion

Con el Xcode abrimos el proyecto **FriendlyChatSwift.xcworkspace**:

![Codelab FriendlyChat Swift](/assets/post_012_img5_sw.png)

Que nos permite abrir y compilar la aplicación:

![FCodelab FriendlyChat Swift](/assets/post_012_img6_sw.png)

{% include google-adsense.html %} <br/>

## Paso 04: Create Firebase console Project

El proyecto **FriendlyChat** de Firebase ya lo había creado cuando segui el [CodeLab de la parte web]({% post_url 2016-05-01-codelab-firebase-web %}){:target="new"}.

El proyecto **FriendlyChat**  estaba creado:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_01.png)

Seleccionamos iOS integración.

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_02.png)

Agrgamos el bundle y el ID:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_03.png)

Teneoms que copiar el **GoogleService-Info.plist** dentro del Xcode:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_04.png)

El siguiente paso, por ahora no lo ejecutamos:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_05.png)

Continuamos con el copiado del archivo **GoogleService-Info.plist** al Xcode:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_06.png)

El archivo esta agregado:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_07.png)

Chequear que esté el **import Firebase** en AppDelegate.swift, FCViewController.swift:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_08.png)

Esta el import en **FCViewController.swift**

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_09.png)

Y tenemos que agregar la siguiente linea de codigo en **AppDelegate.swift** que configura Firebase, siguendo lo que dice en:  **GoogleService-Info.plist** a

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_10.png)

¿Podemos finalizar el wizard que había quedado pendiente en Firebase? ... si, podemos:

![Codelab FriendlyChat Swift Vincular Proeycto](/assets/post_012_img7_swift_05b.png)

De esta forma vemos que en Firebase tenemos el registro de la aplicación de iOS

{% include google-adsense.html %} <br/>

## Paso 05: Reglas de Acceso a la aplicación:

En la consola de Firebse, agregamos las restricciones:

{% highlight javascript %}
{
  "rules": {
        "messages": {
            ".read": "auth != null",
            ".write": "auth != null"
        }
  }
}
{% endhighlight %}

Vamos a la sección de Database:

![Codelab FriendlyChat Swift Firebase Database](/assets/post_012_img8_swift_1.png)

Las reglas (y el simulador):

![Codelab FriendlyChat Swift Firebase Database](/assets/post_012_img8_swift_2.png)

## Paso 06: Firebase Authentication

De nuevo, vamos a la consola de Firebase para configurar la autenticación, pero habilitamos autenticación por mail (recordemos que en el [CodeLab de la parte web]({% post_url 2016-05-01-codelab-firebase-web %}){:target="new"} la autenticación fué por Google):

![Codelab FriendlyChat Swift Firebase Database](/assets/post_012_img9_swift.png)

agregamos el pod 'FirebaseAuth'

{% highlight javascript %}
pod 'FirebaseAuth'
{% endhighlight %}

***duda:*** ¿No sera pod 'Firebase/Auth'... creo que hay un error de tipeo?
***Respuesta***: Si miramos el proyecto **swift** en vez del **swift-starter** vemos que efectivamente es un error de tipeo.

## Paso 07: Pausa - Ejecutamos el proyecto finalizado

Vemos a ejectuar la versión finalizada del proyecto: O sea  **swift** en vez del **swift-starter**

Creo que este es un buen momento para hacer esto, porque ya está configurada la consola de Firebase.

Lo unico que tenemos que ajustar son dos cosas: **GoogleService-Info.plist** y la dirección dada por **Firebase**

Y vemos el resultado, que efectivamente la aplicación levanta:

![Codelab FriendlyChat Swift finalizado](/assets/post_012_img10_swift.png)

Se ve en la aplicación finalzada,
- La publicidad AdMob
- La Autenticación, etc.

Observemos como parte de los chats ingresados, quedan cargados dentro de la plataforma Firebase:

![Codelab FriendlyChat Swift finalizado](/assets/post_012_img11_swift.png)

También están las imágenes subidas como adjuntos:

![Codelab FriendlyChat Swift finalizado](/assets/post_012_img12_swift.png)





## Links




[firebase-links-rapidos]:         https://firebase.google.com/docs/samples/#ios
