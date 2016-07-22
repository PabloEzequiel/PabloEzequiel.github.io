---
layout: post
comments: false
title: ¿Como funciona una aplicación en una TV Samsung con el SO Tizen?
date: '2016-06-10 19:08:44 -0300'
categories: GitHub Samsung Tizen Android
comments: true
permalink: 2016/06/2016-06-10-samsung-tizen-tv.html
---
¿Que es **Tizen**?¿Que diferencias tiene con **Android TV**?¿Samsung tiene su propio sistema operativo?¿Como es el **SDK de Tizen** para desarrollar aplicaciones sobre los **Smart TV de Samsung**?¿Cual es la página con la documentación oficail?

Haciendo pruebas sobre **Android TV** me enteré que en realidad mi **TV Samsung** tenía el sistema operativo **Tizen**.

Veamos como podemos ejecutar una app sencilla sobre **samsung y tizen**, siguiendo principalmente los links [samsung-tizen-tv][samsung-tizen-tv]{:target="atv"} y  [develop-tizen-tv][develop-tizen-tv]{:target="atv"}

# Comencemos

Directorio de trabajo

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/samsung-tizen
```

Clonamos del repositorio https://github.com/SamsungDForum/ el proyecto **HelloWorld** aunque no son los mas me gustan...

{% highlight bash %}
$ git clone https://github.com/SamsungDForum/SmartViewSDKHelloWorld.git
{% endhighlight %}

El proyecto descargado, tal como se ve, se descargan tres proyectos, en objetive-c, en Android y en Javascript

![Android TV - screenshot](/assets/images/mes06/post_015_android_tv_001.png){: .center-image }

# Version xCode

Lo abrimos con el xCode....


![Android TV - screenshot](/assets/images/mes06/post_015_android_tv_002.png){: .center-image }

Pero me da el error: Y no se como recompilar:

Module file was created by an older version of the compiler;
rebuild 'SmartView' and try again:
 samsung-tizen/SmartViewSDKHelloWorld/HelloWorld_iOS/HelloWorld/SmartView.framework/Modules/SmartView.swiftmodule/x86_64.swiftmodule



--------------
# Device

55" UHD 4K Flat Smart TV JU6500 Series 6


https://developer.tizen.org/tizen/tv


# Links relacionados


[samsung-tizen-tv]:   https://www.samsungdforum.com/TizenSampleGuide/
[develop-tizen-tv]:   https://developer.tizen.org/tizen/tv
