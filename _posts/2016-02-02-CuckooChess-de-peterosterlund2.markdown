---
layout: post
comments: false
title: 'GitHub: CuckooChess de peterosterlund2'
date: '2016-02-01 19:08:44 -0300'
categories: Chess GitHub Stockfish Android
comments: true
---

Vamos a comentar nuestra experiencia con el proyecto [cuckoochess de peterosterlund2][github-chess-001-cuckoochess]{:target="chess001"}

# Comencemos

Directorio de trabajo:

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/chess/peterosterlund2/CuckooChess
```

Author: **peterosterlund2**

- Droidfish : Android App principar del repositior de GitHub
- CuckooChess : Es una aplicación Java, para lo cual, la abriremos con el eclipse.

# Prueba 01: Importamos CuckoocChess al Eclipse

Importamos los proyectos de GitHub de peterosterlund2 al eclipse:

/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/chess/peterosterlund2

![CuckooChess paso1 screenshot](/assets/post_002_img1.png)

Después de ejecutar el build, tomamos a CuckooChess que compilo y lo ejecutamos como una aplicación Java:

![CuckooChess paso2 screenshot](/assets/post_002_img2.png)

Run As > Java Application

![CuckooChess paso3 screenshot](/assets/post_002_img3.png)

Y pudimos abrir el AppletGUI y jugar contra CuckooChess aunque nos colgamos un peón en la apertura

![CuckooChess paso4 screenshot](/assets/post_002_img4.png)

El primer test anduvo ok

{% include google-adsense.html %}

# Prueba 02: Compiladon el DroidFish.apk con Eclipse Android Developer Tool (ADT)

Veamos que desde el eclipse, el DroidFish tiene problemas de compilación:

![CuckooChess paso4 screenshot](/assets/post_002_img4b.png)

Estos errores seguramente estarán asociados al JNI, NDK etc, o sea, a la plataforma nativa.

Tenemos dos posibilidades para avanzar, agregar el Android al eclipse (Plugin ADT), a la vieja usanza... O intentar reconvertir el proyecto DroidFish al Android Studio.

Vamos a probar con el plugin ADT, porque pareciera que el DroidFish no se hizo con el Android Studio:

Instalamos el ADT al eclipse:

![CuckooChess paso4 screenshot](/assets/post_002_img5.png)

Instalamos el ADT al eclipse (contnuación):

![CuckooChess paso4 screenshot](/assets/post_002_img6.png)

Finalmente agregué los directorios "gen" manualemnte, y ahora tengo los siguientes errores, relacionados con el Android y el Eclipse:

![CuckooChess paso4 screenshot](/assets/post_002_img7.png)

El error que me da es: Unable to resolve target 'android-7' until the SDK is loaded. Para lo cual, voy a agregar las API de Android 7 y Androd-16 al proyecto.

En el **Eclipse** voy a **window --> Android SDK manager** y selecciono la sdk api para level 16 y level 7:

![CuckooChess paso4 screenshot](/assets/post_002_img8.png)

Luego del update de las API de android, se solucionó el problema. Ahora el siguiente problema, esta con la constante de android "R":

![CuckooChess paso4 screenshot](/assets/post_002_img9.png)

Description Resource Path Location Type R cannot be resolved to a variable ColorTheme.java /DroidFish/src/org/petero/droidfish line 72 Java Problem

Igualmente fué un falso postivo, porque después de hacer restart en el eclipse, los errores desaparecieron.

No solamente desaparecieron los errores, sino que por fin pude lograr el objetivo de levantar la aplicación Android en el Emulador:

Tal como se ve a continuación, en donde estoy jugando con blancas una apertura de Peón Dama, a los cual las negras (el CuckooChess) responden con la **defensa Tarrash**

![CuckooChess paso4 screenshot](/assets/post_002_img10.png)

# Prueba 03: ¿Que sigue? Vamos por el DroidFish

Ok, logramos compilar el proyecto CuckooChess en Android. Pero ¿Que pasa si intentamos ejecutar la aplicaicón Androd DroidFish en el Emulador?

Nos da el siguiente error porque falta resolver o compilar algo del código nativo:

![CuckooChess paso4 screenshot](/assets/post_002_img11.png)

La excepcion es la siguiente: **couldn't find "libnativeutil.so"**

{% highlight bash %}

06-28 20:42:26.396: I/art(3290): Background partial concurrent mark sweep GC freed 3798(115KB) AllocSpace objects, 0(0B) LOS objects, 50% free, 1021KB/2045KB, paused 3.388ms total 121.688ms 06-28 20:42:26.545: D/AndroidRuntime(3290): Shutting down VM 06-28 20:42:26.566: E/AndroidRuntime(3290): FATAL EXCEPTION: main 06-28 20:42:26.566: E/AndroidRuntime(3290): Process: org.petero.droidfish, PID: 3290 06-28 20:42:26.566: E/AndroidRuntime(3290):

java.lang.UnsatisfiedLinkError: dalvik.system.PathClassLoader [DexPathList[[zip file "/data/app/org.petero.droidfish-1/base.apk"], nativeLibraryDirectories=[/vendor/lib, /system/lib]]] couldn't find "libnativeutil.so"

06-28 20:42:26.566: E/AndroidRuntime(3290): at java.lang.Runtime.loadLibrary(Runtime.java:366) 06-28 20:42:26.566: E/AndroidRuntime(3290): at java.lang.System.loadLibrary(System.java:988) 06-28 20:42:26.566: E/AndroidRuntime(3290): at org.petero.droidfish.engine.EngineUtil.

<clinit>(EngineUtil.java:33)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at org.petero.droidfish.DroidFish.setEngineTitle(DroidFish.java:1348)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at org.petero.droidfish.DroidFish.setEngineStrength(DroidFish.java:1343)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at org.petero.droidfish.DroidFish.readPrefs(DroidFish.java:1146)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at org.petero.droidfish.DroidFish.onCreate(DroidFish.java:449)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.app.Activity.performCreate(Activity.java:5990)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.app.Instrumentation.callActivityOnCreate(Instrumentation.java:1106)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2278)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:2387)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.app.ActivityThread.access$800(ActivityThread.java:151)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1303)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.os.Handler.dispatchMessage(Handler.java:102)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.os.Looper.loop(Looper.java:135)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at android.app.ActivityThread.main(ActivityThread.java:5254)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at java.lang.reflect.Method.invoke(Native Method)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at java.lang.reflect.Method.invoke(Method.java:372)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at com.android.internal.os.ZygoteInit$MethodAndArgsCaller.run(ZygoteInit.java:903)
06-28 20:42:26.566: E/AndroidRuntime(3290):     at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:698)</clinit>

{% endhighlight %}

Veamos los componentes que faltan compilar, utilizando al ndk:

![CuckooChess paso4 screenshot](/assets/post_002_img12.png)

Tenemos que verificar si en el **eclipse Mars** que estamos utilizando, con el plugin de **Android Developer Tool (ADT)** tenemos también el NDK instalado

- <http://tools.android.com/recent/usingthendkplugin>

Observamos que

Window -> Preferences -> Android -> NDK

Estaba vacío:

![CuckooChess paso4 screenshot](/assets/post_002_img13.png)

Y en mi PC, al NDK, gracias al uso del Android Studio, ya lo tenía instalado. Con lo cual agrego esa ruta al eclips:

/Users/pabloin/Library/Android/sdk/ndk-bundle

... pero no se como ejectuarlo al NDK (para compilar al codigo nativo JNI) desde el eclipse y me parece mas facil desde la linea de comando. Con lo cual, pasamos al próximo paso:

{% include google-adsense.html %}

# Compilando codigo nativo con NDK y jni

Para los que necesiten (como yo) repasar NDK y JNI, copio los siguientes links basicos sobre el tema:

- <https://developer.android.com/ndk/samples/sample_hellojni.html>

- <https://developer.android.com/ndk/guides/android_mk.html>

- <https://developer.android.com/ndk/guides/application_mk.html>

- <https://github.com/googlesamples/android-ndk/tree/android-mk>

Leyendo esos tutoriales, dice que el NDK se ejecuta en el directorio del proyecto: O sea:

{% highlight bash %}

cd

<project>
$ <ndk>/ndk-build</ndk></project>

Que en mi caso es:

$ cd /Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/chess/peterosterlund2/DroidFish $ ndk-build

{% endhighlight %}

Cuando lo ejecuto, obtengo el resultado:

make: /Users/pabloin/Library/Android/sdk/ndk-bundle/toolchains/aarch64-linux-android-4.8/prebuilt/darwin-x86_64/bin/aarch64-lin ux-android-gcc: No such file or directory

En mi caso, es porque tengo toolchains **aarch64-linux-android-4.9** (en vez de 4.8)

O sea, para que pueda compilar, tengo que cambiar el 4.8 por 4.9 en el Android.mk:

Tuve que cambiar la version en: Android.mk NDK_TOOLCHAIN_VERSION := 4.9 a NDK_TOOLCHAIN_VERSION := 4.9

Y luego de ejecutar el

{% highlight bash %} $ ndk-buid

... [mips] Compile++ : stockfish-nopie <= tt.cpp [mips] Compile++ : stockfish-nopie <= tbprobe.cpp [mips] Executable : stockfish-nopie [mips] Install : stockfish-nopie => libs/mips/stockfish-nopie

{% endhighlight %}

Vamos a ejecutar al proyecto DroidFish como Android application:

![CuckooChess paso4 screenshot](/assets/post_002_img14a.png)

Se ejecuto exitosamente, vemos los proyectos del eclipse de fondo, y el emulador con el DroidFish de Frente

![CuckooChess paso4 screenshot](/assets/post_002_img14.png)

Y hacemos algunas jugadas con el droidfish corriendo en el emulador

![CuckooChess paso4 screenshot](/assets/post_002_img15.png)

En este punto podemos dar por cerrado el post, con el objetivo cumplido de compilar los proyectos de GitHub de DroidFish y CuckooChess, resolviendo la compilación de código nativo JNI con NDK en el medio.

[github-chess-001-cuckoochess]: https://github.com/peterosterlund2/droidfish/tree/master/CuckooChess
[github-chess-001-droidfish]: https://github.com/peterosterlund2/droidfish
[github-chess-002-droidfishchess_android]: https://github.com/elitecoder/droidfishchess_android
[github-chess-003-stockfishchess-ios]: https://github.com/elitecoder/stockfishchess-ios
[github-chess-004-stockfishchess-android]: https://github.com/mqprichard/stockfishchess-android
