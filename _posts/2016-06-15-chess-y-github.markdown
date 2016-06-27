---
layout: post
comments: false
title:  "GitHub: DroidFish de peterosterlund2"
description: "ñkv.ka"
date:   2016-06-15 19:08:44 -0300
categories: Chess GitHub Stockfish Android
---
Vamos a comentar los exitos y fracasos de trabajar con el proyecto [DroidFish de GitHub][DroidFish-GitHub]{:target="DroidFish"}.

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/peterosterlund2
</pre>

Author: **peterosterlund2**

-  Droidfish   : Android App
-  CuckooChess : Es la GUI



## Prueba 01

Intentaremos compilar **DroidFish** con el **Android Studio**.
Tiene dependencia con CuckooChess.

![importacion paso1 screenshot](/assets/post_001_droidfish00000.png)


![importacion paso2 screenshot](/assets/post_001_droidfish00001.png)

Después de la adaptación de Eclipse ADT a Android Studio, es necesario bajar el Android NDK

![importacion paso2 screenshot](/assets/post_001_droidfish00002.png)


<br />
<div style="text-align: center;">
<script async="" src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- probarnocuestanada_468x60_creado_20150520 -->
<br />
<ins class="adsbygoogle" data-ad-client="ca-pub-4671718819110940" data-ad-slot="5798260795" style="display: inline-block; height: 60px; width: 468px;"></ins><script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>
</div>
<br />


Y ahora tenemos el siguiente problema de compilación/dependencia:
Error:(40, 23) Lzma86Enc.h: No such file or directory

![importacion paso2 screenshot](/assets/post_001_droidfish00003.png)

## Links

Relacionado a:
http://web.comhem.se/petero2home/javachess/index.html
http://web.comhem.se/petero2home/droidfish/index.html

Otra distribución
https://github.com/mqprichard/stockfishchess-android

[DroidFish-GitHub]:               https://github.com/peterosterlund2/droidfish
[stockfishchess-android-GitHub]:  https://github.com/mqprichard/stockfishchess-android


## Pausa

Todavía me faltan conocimientos para solucionar este problema
que seguramente está asociado a la conversión de proyectos
de Eclipse a Android Studio ...

Por ahora suspendo aqui el post....


{% if page.comments %}

<div id="disqus_thread"></div>
<script>

    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */

    var disqus_config = function () {
        this.page.url = pabloezequiel.github.io;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = "PabloEze";          // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };


    (function() {  // REQUIRED CONFIGURATION VARIABLE: EDIT THE SHORTNAME BELOW
        var d = document, s = d.createElement('script');

        s.src = '//PabloEze.disqus.com/embed.js';  // IMPORTANT: Replace EXAMPLE with your forum shortname!

        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>


{% endif %}
