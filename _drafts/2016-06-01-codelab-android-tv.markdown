---
layout: post
comments: false
title: ¿Como funciona una aplicación con Android TV?
date: '2016-06-01 19:08:44 -0300'
categories: Chess GitHub Stockfish Android
comments: true
permalink: 2016/06/2016-06-01-codelab-android-tv.html
---

Vamos a seguir el [CodeLab de Google sobre Android TV][codelab-android-tv]{:target="atv"}

# Comencemos

Directorio de trabajo

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-tv-codelab
```

Clonamos el repositorio:

{% highlight bash %}
$ git clone https://github.com/googlecodelabs/android-tv-leanback.git
{% endhighlight %}

El proyecto descargado:

![Android TV - screenshot](/assets/images/mes06/post_015_android_tv_001.png){: .center-image }

Lo importamos al Android Studio

![Android TV - screenshot](/assets/images/mes06/post_015_android_tv_002.png){: .center-image }

Ejecutamos en Android el checkpoint_0, sobre un celular con la API 23:

![Android TV - screenshot](/assets/images/mes06/post_015_android_tv_003.png){: .center-image }


Despúes de conectar el cable USB al televisor, vemos que el dispositivos no aparece disponible

![Android TV - screenshot](/assets/images/mes06/post_015_android_tv_004.png){: .center-image }

Vamos a buscar la solución siguiendo los pasos del tutorial, para buscar la dirección IP del dispositivo físico.

# Find the IP of the device.

- Back out to the main Settings page and click Device.
- Select the method that you've used to connect the device to your intranet.
- If you're using Wi-Fi, select Wi-Fi and then select the network you're currently connected to.
- Click on Status info and record your IP.
- If you're using ethernet select the Internet connection and record your IP.


Ejecutamos el comando en la terminal:

adb connect 192.168.0.102:4321

Empeze a probar puertos aleatoriamente, y encontre que el Android TV mio, escucha en el puerto 8080


com.android.ddmlib.AdbCommandRejectedException: device '192.168.0.102:8080' not found
Error while Installing APK



Vamos a instalar SammyWidgets para MAc
=>> No exite ahora es otro sotware ...

# Device

55" UHD 4K Flat Smart TV JU6500 Series 6

Nota Samsung tiene Tizen


# NoCuestaNada



# Links relacionados

- Post sobre **SammyWidgets** y sobre **Smart TV de Samsung**

[codelab-android-tv]:   https://codelabs.developers.google.com/codelabs/androidtv-adding-leanback/index.html?index=..%2F..%2Findex#0

[android-tv-link1]:  http://www.mundonas.com/2014/01/instalar-apps-no-oficiales-en-smart-tv.html
