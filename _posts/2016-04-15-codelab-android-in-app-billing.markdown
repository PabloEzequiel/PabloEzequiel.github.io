---
layout: post
comments: false
title: ¿Como funciona 'In-app Billing' en Android?
date: '2016-04-10 19:08:44 -0300'
categories: CodeLab GoogleSamples Android In-app Billing
---

Veamos como se implementan las [Compras in-app o In-App Billing](https://developer.android.com/google/play/billing/billing_integrate.html){:target="inapp1"} en Android. Para esto, vamos a seguir el [CodeLab](https://developer.android.com/training/in-app-billing/preparing-iab-app.html){:target="inapp2"} con su [repositorio GitHub](https://github.com/googlesamples/android-play-billing/tree/master/TrivialDrive){:target="ds"}

Hay dos links relacionados el a este CodeLab:

- [Video de in-app billing](https://www.youtube.com/watch?v=UvCl5Xx7Z5o){:target="inap"} o también el siguiente video sobre la
- [Video de Seguridad de in-app Billing](https://www.youtube.com/watch?annotation_id=annotation_803104095&feature=iv&src_vid=UvCl5Xx7Z5o&v=DgcJPIRpfSk){: target="neww"} del Google I/O 2013

# Comencemos

Directorio de trabajo, en nuestra PC utilizaremos la carpeta:

```
# Ejecutamos el $ git clone en:
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples

# Pryecto de trabajo:
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-play-billing/TrivialDrive
```

Clonamos al proyecto:

{% highlight bash %}
$ git clone https://github.com/googlesamples/android-play-billing.git
 {% endhighlight %}

# Ejecutamos al proyecto con Android Studio

Probamos levantar la app y nos da una excepcion de claves y keystores:

![importacion paso1 screenshot](/assets/post_010_img1.png){: .center-image }

{% highlight bash %}

Process: com.example.android.trivialdrivesample,
PID: 2295 java.lang.RuntimeException: Unable to start activity ComponentInfo{com.example.android.trivialdrivesample/com.example.android.trivialdrivesample.MainActivity}: java.lang.RuntimeException: Please put your app's public key in MainActivity.java.

{% endhighlight %}

{% include google-adsense.html %}<br>

# Paso 01: Agregar la aplicación a Google Play Developer Console

En el Google Play vamos a tener que generar la clave del aplicación por única vez.

Precondiciones: Ya me había dado de alta en el Google Play

Necesito darme de alta en el Google Wallet según dice la doc:

***To sell in-app items, you also need to have a** Google payments **merchant account.***

# Paso 02: Alta en el Google Wallet

Me pude dar de alta por la web **Google Wallet**:

![importacion paso1 screenshot](/assets/post_010_img2.png){: .center-image }

Sobre descargar la app de iOS, no es posible desde el store Argentino...

# Paso 03: Alta de la App en Google developer

Damos de alta la App en **Google Play developer Console**

Le vamos a asignar el nombre **DriveBuyPay**

![importacion paso1 screenshot](/assets/post_010_img3.png){: .center-image }

Agergamos algunos datos

![importacion paso1 screenshot](/assets/post_010_img4.png){: .center-image }

# Paso 04: Api y Servicios: Obtener clave de licencia para la aplicación

Dentro de Api y servicios, buscamos la **clave de licencia para la aplicación**

Copiamos la pública RSA con codificación Base64 para incluirla en tu archivo binario apk.

![importacion paso1 screenshot](/assets/post_010_img5.png){: .center-image }

{% include google-adsense.html %}<br>

# Paso 05: Renombrar paquetes de la aplicación

Tendremos que modificar el nombre del package de la aplicación a uno propio, donde cambiaremos

{% highlight java %} package com.example.android.trivialdrivesample; {% endhighlight %}

al siguiente:

{% highlight java %} package com.probarnocuestanada.pay.drivebuypay; {% endhighlight %}

Tambien tenemos que modificarolo en el **build.gradle** de la aplicacion **app**

{% highlight javascript %} defaultConfig { applicationId "com.probarnocuestanada.pay.drivebuypay" minSdkVersion 14 targetSdkVersion 23 versionCode 7 versionName "1.5" } {% endhighlight %}

Para renombrar paquetes, voy a probar la [Propuesta de Stackoverflow](http://stackoverflow.com/questions/16804093/android-studio-rename-package){:target="st"}

**Another good method is: First create a new package with the desired name by right clicking on the java folder -> new -> package.

Then, select and drag all your classes to the new package. AndroidStudio will refactor the package name everywhere.

Finally, delete the old package.

Done.

One more thing very important

You have to Change manually Android Manifest and gradle file to the new package if you use this method.**

Ok, después de un poco de trabajo, pude renombrar los paquetes, gracias a deseleccionar la opción: **Compact Empty Middle Packages** que me muestra las carpetas de proyecto de Android separadas.

{% include google-adsense.html %}<br>

# Paso 06: Agregamos permisos

En el AndroidManifest.xml Agregamos permisos:

{% highlight xml %}

<uses-permission android:name="com.android.vending.BILLING">
{% endhighlight %}</uses-permission>

# Paso 07: Agregamos nuesto propio key

En el CodeLab, nos indican:

**_Modify the sample to create your own application. Remember to copy the Base64 public license key for your application from the Developer Console over to your MainActivity.java._**

Aqui nuevamente hay un tema que tenemos que tener cuidado respecto a almacenar nuestra propia Key en el codigo:

{% highlight java %}

/**

- base64EncodedPublicKey should be YOUR APPLICATION'S PUBLIC KEY
- (that you got from the Google Play developer console). This is not your
- developer public key, it's the app-specific public key. *
- Instead of just storing the entire literal string here embedded in the
- program, construct the key at runtime from pieces or
- use bit manipulation (for com.probarnocuestanada, XOR with some other string) to hide
- the actual key. The key itself is not secret information, but we don't
- want to make it easy for an attacker to replace the public key with one
- of their own and then fake messages from the server.
- / String base64EncodedPublicKey = "CONSTRUCT_YOUR_KEY_AND_PLACE_IT_HERE";

{% endhighlight %}

Otra vez, tenemos nuevamente la advertencia de google sobre [agregar seguridad a la clave](https://developer.android.com/training/in-app-billing/preparing-iab-app.html){:target="new"}:

**_Security Recommendation: It is highly recommended that you do not hard-code the exact public license key string value as provided by Google Play. Instead, you can construct the whole public license key string at runtime from substrings, or retrieve it from an encrypted store, before passing it to the constructor. This approach makes it more difficult for malicious third-parties to modify the public license key string in your APK file._**

Aparentemente no es seguro dejar la clave en el codigo, y por esto [hay una discusión en stackoverflow](http://stackoverflow.com/questions/14352758/android-in-app-billing-securing-application-public-key){:target="new"} al respecto. Y tambien [otra discusion mas](http://security.stackexchange.com/questions/33686/strong-encryption-for-base64-encoded-public-key-in-android){:target="newq"} sobre el tema

Agregamos la clave de la siguiente manera con un metodo privado que revierte la ofuscación de la clave, para que pueda ser asignada a la variable string base64EncodedPublicKey con el valor correcto:

![importacion paso1 screenshot](/assets/post_010_img6.png){: .center-image }

{% include google-adsense.html %}<br>

# Paso 08: Ejecutando la aplicación

Si intentamos ejecutar la aplicación en este punto, vemos que al menos levanta:

![importacion paso1 screenshot](/assets/post_010_img7.png){: .center-image }

Dice:

**_Error: Problem Setting up in-app billing: labResult: Billing service unavailable on the device. (Response 3:Billing unavailable)_**

Las razones de este error Aparentemente pueden ser varias ([^1])([^2])...

Una de las cuales, es que si estoy corriendo en un emulador, los servicios de Google Play deberian estar instalados y configurados. Este podría ser mi caso, ya que estoy corriendo la app en un emulador, pero:

**¿Como se si en mi Emulador, tengo los servicios del Google Play instalados y configurados?**

Para el emulador del **Android Studio**, parece que se puede descargar el **GAPPS Package** para instalar. No lo probe.

Probé poco el Gennymotion y no probé el bluestacks, pero con Andy pude llegar al objetivo:

Otra alternativa, el emulador **Andy** parece que trae los **Servicios del Google Play** instalados. ¿Se puede ejecutar la aplicacion?

Depsués de algunas pruebas, tal como se ve en la imagen a continuación:

![importacion paso1 screenshot](/assets/post_010_img8.png){: .center-image }

La versión de Andy utilizada es la siguiente:

![importacion paso1 screenshot](/assets/post_010_img9.png){: .center-image }

Para ejecutar la aplicación en el **Emulador Andy** que tiene los **Servicios del Google Play** instalados, tuve que ingresar mi cuenta de gmail en el Google Play instalado en Andy.

- Android 4.4.2
- Andy_vm_custom 46.1.112

# Conclusión

Por ahora finalizamos en este punto el post, con el obejtivo de haber hecho andar la aplicación y comprendido en un punto intermedio el circuito y solucionado varios problemas relacionados al setup de la app.

# Referencias

[^1]: http://stackoverflow.com/questions/21091353/what-are-the-possibilities-to-get-this-error-code-3-in-inapp-purchase
[^2]: http://stackoverflow.com/questions/15889480/iabresult-billing-service-unavailable-on-device-response-3billing-unavailab
