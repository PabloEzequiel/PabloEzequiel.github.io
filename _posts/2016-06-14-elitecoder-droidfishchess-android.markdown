---
layout: post
comments: false
title:  "GitHub: Droidfish chess android de elitecoder"
date:   2016-06-15 19:08:44 -0300
categories: Chess GitHub Stockfish Android
---
Vamos a comentar los exitos y fracasos de trabajar con el proyecto [Droidfishchess android de elitecoder][github-chess-002-droidfishchess_android]{:target="chess002"}.


## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/elitecoder/droidfishchess_android

Después de importarlo desde Eclipse ADT to Android Studio:
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/elitecoder/droidfishchess_android_1
</pre>

Author: **elitecoder**

## Paso 01

Tuve que importar el proyecto a Android Studio porque estaba con una versión vieja de Android.

<pre>
Error #001:

Gradle sync failed: Cause: failed to find target with hash string 'android-10' in: /Users/pabloin/Library/Android/sdk

Solución:
build.graddle=23

Igual creo que no es una buena solución si se quieren soportar versiones viejas
</pre>

Después de la última corrección, pude levantar el emulador y compilar el proyecto


<pre>
Error #002: cannot resolve method setLatestEventinfo

Es codigo deprecado. Opte por comentarlo....
</pre>

Seguimos, y ya me da el mismo error que los otros proyectos que no se como solucionar.

<pre>
Error #003:

#include "Lzma86Enc.h"
Error:(40, 23) Lzma86Enc.h: No such file or directory

Solucion:
Pareciera que debiera ejecutar el compilador de JNI, Android.nk

Observemos:
.../droidfishchess_android/app/src/main/jni/Android.nk

Segun:
https://developer.android.com/ndk/guides/android_mk.html

y Segun:
https://developer.android.com/ndk/guides/concepts.html

Necesito instalado al Android-ndk

ndk-build

Pero no se si lo tengo instalado

# Android NDK
export ANDROID_SDK=/Users/pabloin/Library/Android/sdk
export ANDROID_NDK=/Users/pabloin/Library/Android/sdk/ndk-bundle
export PATH="$PATH:$ANDROID_SDK/tools:$ANDROID_SDK/platform-tools:$ANDROID_NDK"

</pre>

Volvemos a repetir el proceso de importación, con el NDK instalado y configurado:



<pre>
Error #003:

Error:(12, 0) NDK integration is deprecated in the current plugin.
<a href="http://tools.android.com/tech-docs/new-build-system/gradle-experimental">Consider trying the new experimental plugin</a><br><a href="useDeprecatedNdk">Set "android.useDeprecatedNdk=true" in gradle.properties to continue using the current NDK integration</a>


Solución:
Agregue un nuevo archivo gradle.properties a la raiz del proyecto.
Agergué la entrada 'android.useDeprecatedNdk=true' al archivo: gradle.properties
</pre>

Volvemos a repetir el Error


<pre>
Error #004:
Error:(40, 23) Lzma86Enc.h: No such file or directory

/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/elitecoder/droidfishchess_android_1/app/src/main/jni

Cuando Intente compilar al Android.mk con ndk-build me dice
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/elitecoder/droidfishchess_android_1/app/src/main/jni/Android.mk:17: jni/gtb/Android.mk: No such file or directory

Entonces edite Android.mk y suprimi la carpeta "lib"

decia:

include lib/stockfish/Android.mk
include lib/gtb/Android.mk

deje:

include stockfish/Android.mk
include gtb/Android.mk

Y funciono la compilacion:

...

[mips] Compile        : gtb <= infback.c
[mips] Compile        : gtb <= inffast.c
[mips] Compile        : gtb <= inftrees.c
[mips] Compile        : gtb <= trees.c
[mips] Compile        : gtb <= zutil.c
[mips] Compile        : gtb <= lzf_c.c
[mips] Compile        : gtb <= lzf_d.c
[mips] Compile++      : gtb <= GtbProbe.cpp
[mips] SharedLibrary  : libgtb.so
[mips] Install        : libgtb.so => libs/mips/libgtb.so
[mips] Compile++      : nativeutil <= nativeutil.cpp
[mips] SharedLibrary  : libnativeutil.so
[mips] Install        : libnativeutil.so => libs/mips/libnativeutil.so
[mips] Compile++      : stockfish <= evaluate.cpp
[mips] Compile++      : stockfish <= move.cpp
[mips] Compile++      : stockfish <= search.cpp
[mips] Compile++      : stockfish <= benchmark.cpp
[mips] Compile++      : stockfish <= movegen.cpp
[mips] Compile++      : stockfish <= tt.cpp
[mips] Compile++      : stockfish <= bitbase.cpp
[mips] Compile++      : stockfish <= main.cpp
[mips] Compile++      : stockfish <= movepick.cpp
[mips] Compile++      : stockfish <= uci.cpp
[mips] Compile++      : stockfish <= bitboard.cpp
[mips] Compile++      : stockfish <= pawns.cpp
[mips] Compile++      : stockfish <= ucioption.cpp
[mips] Compile++      : stockfish <= book.cpp
[mips] Compile++      : stockfish <= material.cpp
[mips] Compile++      : stockfish <= position.cpp
[mips] Compile++      : stockfish <= endgame.cpp
[mips] Compile++      : stockfish <= misc.cpp
[mips] Compile++      : stockfish <= timeman.cpp
[mips] Compile++      : stockfish <= thread.cpp
[mips] Executable     : stockfish
[mips] Install        : stockfish => libs/mips/stockfish


pwd
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/elitecoder/droidfishchess_android_1/app/src/main/libs/mips
MacBook-Pro-de-Pablo:mips pabloin$ ls -la
total 2016
drwxr-xr-x  5 pabloin  staff     170 Jun 26 14:21 .
drwxr-xr-x  6 pabloin  staff     204 Jun 26 14:20 ..
-rwxr-xr-x  1 pabloin  staff  217580 Jun 26 14:20 libgtb.so
-rwxr-xr-x  1 pabloin  staff    5556 Jun 26 14:20 libnativeutil.so
-rwxr-xr-x  1 pabloin  staff  800852 Jun 26 14:21 stockfish

</pre>

<pre>

Error:
TODO:
http://ph0b.com/android-studio-gradle-and-ndk-integration/

Muy complicado

En realidad creo que conviene seguir:
http://tools.android.com/tech-docs/new-build-system
http://tools.android.com/tech-docs/new-build-system/gradle-experimental

compile 'com.android.tools.build:gradle-experimental:0.8.0-alpha4'

Creo que voy a tener que volver a arrancar de cero....


TODO:

Puedo probar los siguientes ejemplos para familiarizarme con el JNI
https://github.com/googlesamples/android-ndk
</pre>

Por ahora suspendo aqui el post....

[github-chess-001-droidfish]:                https://github.com/peterosterlund2/droidfish
[github-chess-002-droidfishchess_android]:   https://github.com/elitecoder/droidfishchess_android
[github-chess-003-stockfishchess-ios]:       https://github.com/elitecoder/stockfishchess-ios
[github-chess-004-stockfishchess-android]:   https://github.com/mqprichard/stockfishchess-android
