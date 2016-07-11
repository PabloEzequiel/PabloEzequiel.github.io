---
layout: post
comments: false
title: 'GitHub: DroidFish de peterosterlund2'
date: '2016-02-01 19:08:44 -0300'
categories: Chess GitHub Stockfish Android
---

Vamos a comentar los exitos y fracasos de trabajar con el proyecto [DroidFish de peterosterlund2][github-chess-001-droidfish]{:target="chess001"}

# Comencemos

Directorio de trabajo:

```
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/chess/peterosterlund2
```

Author: **peterosterlund2**

- Droidfish : Android App
- CuckooChess : Es la GUI

# Prueba 01

Intentaremos compilar **DroidFish** con el **Android Studio**. Tiene dependencia con CuckooChess.

![importacion paso1 screenshot](/assets/post_001_droidfish00000.png)

![importacion paso2 screenshot](/assets/post_001_droidfish00001.png)

Después de la adaptación de Eclipse ADT a Android Studio, es necesario bajar el Android NDK

![importacion paso2 screenshot](/assets/post_001_droidfish00002.png)

Y ahora tenemos el siguiente problema de compilación/dependencia: Error:(40, 23) Lzma86Enc.h: No such file or directory

![importacion paso2 screenshot](/assets/post_001_droidfish00003.png)

Estos errores no los logor solucionar, con lo cual cierro en este punto el post. Pero afortunamente, en el siguiente intento pude compilar y ejecutar tos los proyectos de DroidFish en GitHub, utilizando el eclipse en vez del Android Studio:

# Siguiente Intento:

Leer el [GitHub: CuckooChess de peterosterlund2]({% post_url 2016-02-02-CuckooChess-de-peterosterlund2 %}) En donde pude compilar y ejectuar todos los proyecto de GitHub de DroidFish y detallo también todos los pasos.

[github-chess-001-droidfish]: https://github.com/peterosterlund2/droidfish
[github-chess-002-droidfishchess_android]: https://github.com/elitecoder/droidfishchess_android
[github-chess-003-stockfishchess-ios]: https://github.com/elitecoder/stockfishchess-ios
[github-chess-004-stockfishchess-android]: https://github.com/mqprichard/stockfishchess-android
