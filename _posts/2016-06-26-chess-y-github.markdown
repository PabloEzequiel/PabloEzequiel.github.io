---
layout: post
comments: true
title:  "Chess y GitHub"
date:   2016-06-26 10:08:44 -0300
categories: Chess GitHub Stockfish Android
---
Vamos a comentar los exitos y fracasos de trabajar con el proyecto [DroidFish de GitHub][DroidFish-GitHub].

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

Y ahora tenemos el siguiente problema de compilación/dependencia:
Error:(40, 23) Lzma86Enc.h: No such file or directory

![importacion paso2 screenshot](/assets/post_001_droidfish00003.png)

## Links

Relacionado a:
http://web.comhem.se/petero2home/javachess/index.html
http://web.comhem.se/petero2home/droidfish/index.html

Otra distribución
https://github.com/mqprichard/stockfishchess-android

[DroidFish-GitHub]: https://github.com/peterosterlund2/droidfish


{% if page.comments %}

<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */
    /*
    var disqus_config = function () {
        this.page.url = https://pabloezequiel.github.io;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = "{{ page.url }}"; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() {  // REQUIRED CONFIGURATION VARIABLE: EDIT THE SHORTNAME BELOW
        var d = document, s = d.createElement('script');

        s.src = '//PabloEze.disqus.com/embed.js';  // IMPORTANT: Replace EXAMPLE with your forum shortname!

        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>


{% endif %}
