---
layout: post
comments: false
title:  "CodeLab: Android compras inApp de googlesamples"
date:   2016-04-10 19:08:44 -0300
categories: Android Pay CodeLab googlesamples
---
Veamos como se implementan las [Compras in-app en Andorid](https://developer.android.com/google/play/billing/billing_integrate.html){:target="inapp"}. Para esto, vamos a seguir el [CodeLab](https://developer.android.com/training/in-app-billing/preparing-iab-app.html){:target="inapp2"} con su [repositorio GitHub](https://github.com/googlesamples/android-play-billing/tree/master/TrivialDrive){:target="ds"}


## Comencemos

Directorio de trabajo, en nuestra PC utilizaremos la carpeta:

<pre>
# Ejecutamos el $ git clone en:
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples

# Pryecto de trabajo:
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-play-billing/TrivialDrive
</pre>

Ejecutamos:

{% highlight bash %}
$ git clone https://github.com/googlesamples/android-play-billing.git
{% endhighlight %}



PERDI TODO EL Directorio
MacBook-Pro-de-Pablo:android-play-billing pabloin$ cd ..
MacBook-Pro-de-Pablo:googlesamples pabloin$ l
total 77784
-rw-r--r--@  1 pabloin  staff  23549422 Jun 27 20:25 android-ndk.zip
-rw-r--r--@  1 pabloin  staff  16258652 Jun 28 22:53 android-ndk-android-mk.zip
drwxr-xr-x@ 30 pabloin  staff      1020 Jun 29 14:34 android-ndk-master
drwxr-xr-x@ 22 pabloin  staff       748 Jun 29 14:34 android-ndk-android-mk
drwxr-xr-x   4 pabloin  staff       136 Jun 29 14:38 android-pay-codelab
-rw-r--r--@  1 pabloin  staff      8196 Jul  1 13:13 .DS_Store
drwxr-xr-x   4 pabloin  staff       136 Jul  1 13:25 android-vr-codelab
drwxr-xr-x   3 pabloin  staff       102 Jul  2 11:14 firebase

drwxr-xr-x   8 pabloin  staff       272 Jul  3 01:41 ..
drwxr-xr-x  11 pabloin  staff       374 Jul  3 04:36 .
drwxr-xr-x   9 pabloin  staff       306 Jul  3 04:41 android-play-billing
MacBook-Pro-de-Pablo:googlesamples pabloin$ rm -rf /Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples
MacBook-Pro-de-Pablo:googlesamples pabloin$
