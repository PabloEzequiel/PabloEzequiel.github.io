---
layout: post
comments: false
title:  "GitHub: CuckooChess de peterosterlund2"
date:   2016-02-01 19:08:44 -0300
categories: Chess GitHub Stockfish Android
---
Vamos a comentar nuestra experiencia con el proyecto [cuckoochess de peterosterlund2][github-chess-001-cuckoochess]{:target="chess001"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/peterosterlund2/CuckooChess
</pre>

Author: **peterosterlund2**

-  Droidfish   : Android App principar del repositior de GitHub
-  CuckooChess : Es una aplicación Java, para lo cual, la abriremos con el eclipse.



## Prueba 01: Importamos CuckoocChess al Eclipse

Importamos los proyectos de GitHub de peterosterlund2 al eclipse:

/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/peterosterlund2

![CuckooChess paso1 screenshot](/assets/post_002_img1.png)

Después de ejecutar el build, tomamos a CuckooChess que compilo y lo ejecutamos como una aplicación Java:

![CuckooChess paso2 screenshot](/assets/post_002_img2.png)

Run As > Java Application

![CuckooChess paso3 screenshot](/assets/post_002_img3.png)

Y pudimos abrir el AppletGUI y jugar contra CuckooChess aunque nos colgamos un peón en la apertura

![CuckooChess paso4 screenshot](/assets/post_002_img4.png)

El primer test anduvo ok

## Prueba 02: Compiladon el DroidFish.apk con Eclipse Android Developer Tool (ADT)

Veamos que desde el eclipse, el DroidFish tiene problemas de compilación:

![CuckooChess paso4 screenshot](/assets/post_002_img4b.png)

Estos errores seguramente estarán asociados al JNI, NDK etc, o sea, a la plataforma nativa.

Tenemos dos posibilidades para avanzar, agregar el Android al eclipse (Plugin ADT), a la vieja usanza...
O intentar reconvertir el proyecto DroidFish al Android Studio.

Vamos a probar con el plugin ADT, porque pareciera que el DroidFish no se hizo con el Android Studio:

Instalamos el ADT al eclipse:

![CuckooChess paso4 screenshot](/assets/post_002_img5.png)

Instalamos el ADT al eclipse (contnuación):

![CuckooChess paso4 screenshot](/assets/post_002_img6.png)

Finalmente agregué los directorios "gen" manualemnte, y ahora tengo los siguientes errores, relacionados con el Android y el Eclipse:

![CuckooChess paso4 screenshot](/assets/post_002_img7.png)

El error que me da es:
Unable to resolve target 'android-7' until the SDK is loaded.
Para lo cual, voy a agregar las API de Android 7 y Androd-16 al proyecto.

En el **Eclipse** voy a **window --> Android SDK manager** y selecciono la sdk api  para level 16 y level 7:

![CuckooChess paso4 screenshot](/assets/post_002_img8.png)

Luego del update de las API de android, se solucionó el problema.
Ahora el siguiente problema, esta con la constante de android "R":

![CuckooChess paso4 screenshot](/assets/post_002_img9.png)

Description	Resource	Path	Location	Type
R cannot be resolved to a variable
	ColorTheme.java
	/DroidFish/src/org/petero/droidfish	line 72	Java Problem






[github-chess-001-droidfish]:                https://github.com/peterosterlund2/droidfish
[github-chess-001-cuckoochess]:             https://github.com/peterosterlund2/droidfish/tree/master/CuckooChess
[github-chess-002-droidfishchess_android]:   https://github.com/elitecoder/droidfishchess_android
[github-chess-003-stockfishchess-ios]:       https://github.com/elitecoder/stockfishchess-ios
[github-chess-004-stockfishchess-android]:   https://github.com/mqprichard/stockfishchess-android
