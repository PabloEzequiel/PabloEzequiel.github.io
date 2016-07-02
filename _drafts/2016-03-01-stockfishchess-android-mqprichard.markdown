---
layout: post
comments: false
title:  "GitHub: Stockfishchess android de mqprichard"
date:   2016-03-01 19:08:44 -0300
categories: Chess GitHub Stockfish Android
---
Vamos a comentar los exitos y fracasos de trabajar con el proyecto [Stockfishchess android de mqprichard][github-chess-004-stockfishchess-android]{:target="chess004"}

Este proyecto fue adaptado para Integración Continua con CloudBees/Jenkins.
Veamos si podemos compilarlo

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/mqprichard
</pre>

Author: **mqprichard**

## Paso 01: Siguiendo instrucciones

Seguimos las instrucciones del [README.md][https://github.com/mqprichard/stockfishchess-android/blob/master/README.md]

O sea,

{% highlight bash %}

The final APK can be downloaded from the workspace: /DroidFish/bin/DroidFish-debug.apk

To run the application using the Android emulator:

/Users/pabloin/Library/Android/sdk

create avd -n android.16 -t "android-16" -b armeabi-v7a -c 128M

emulator -avd android.16

Wait for the emulator to start...

adb connect localhost:5554

adb install DroidFish-debug.apk

adb shell am start -n org.petero.droidfish/.DroidFish

{% endhighlight %}



## Paso 02: Errores

No pude hacer andar con el Android Studio el Ejercicio.
El proyecto de GitHub es del 2012

https://www.cloudbees.com/blog/mobile-builds-jenkins-cloud-recap-and-launching-emulators

En concreto: Interrumplo el post aqui, y doy por cerrado este tema... 


[github-chess-001-droidfish]:                https://github.com/peterosterlund2/droidfish
[github-chess-002-droidfishchess_android]:   https://github.com/elitecoder/droidfishchess_android
[github-chess-003-stockfishchess-ios]:       https://github.com/elitecoder/stockfishchess-ios
[github-chess-004-stockfishchess-android]:   https://github.com/mqprichard/stockfishchess-android
