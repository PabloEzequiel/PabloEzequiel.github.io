---
layout: post
comments: false
title:  "GitHub: Chess Java de jhrcek"
date:   2016-02-13 19:08:44 -0300
categories: Chess GitHub JAva
---
Vamos a ver un proyecto de Java relacionado al ajedrez [Chess java](https://github.com/jhrcek/Chess){:target="chess003"}


## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/chess/jhrcek/
</pre>



Author: **jhrcek**

Clonamos el repositorio

{% highlight bash %}
$ git clone git://github.com/jhrcek/Chess.git
{% endhighlight %}

Lo ejecutamos el eclipse, vemos que el build y los test funcionan:

![importacion paso1 screenshot](/assets/post_003_img2_b.png){: .center-image }

Lo ejecutamos

![importacion paso1 screenshot](/assets/post_003_img3_b.png){: .center-image }

Pero da una excepcion:

{% highlight bash %}
03:01:26.303 INFO  c.j.chess.FEN.Fen - Parsing: "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1"
03:01:26.311 INFO  c.j.c.m.i.GameImpl - Creating new instance of Game using initial position "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1"
Exception in thread "AWT-EventQueue-0" java.util.ConcurrentModificationException
	at java.util.LinkedHashMap$LinkedHashIterator.nextNode(LinkedHashMap.java:711)
	at java.util.LinkedHashMap$LinkedKeyIterator.next(LinkedHashMap.java:734)
	at java.util.Collections$3.nextElement(Collections.java:5216)
	at cz.janhrcek.chess.gui.GameTreeDisplayer.setupStylesheet(GameTreeDisplayer.java:62)
	at cz.janhrcek.chess.gui.GameTreeDisplayer.<init>(GameTreeDisplayer.java:33)
	at cz.janhrcek.chess.gui.MainWindow.createAndShowGui(MainWindow.java:47)
	at cz.janhrcek.chess.gui.MainWindow.<init>(MainWindow.java:36)
	at cz.janhrcek.chess.gui.Main$1.run(Main.java:16)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:311)
	at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:756)
	at java.awt.EventQueue.access$500(EventQueue.java:97)
	at java.awt.EventQueue$3.run(EventQueue.java:709)
	at java.awt.EventQueue$3.run(EventQueue.java:703)
{% endhighlight  %}

{% include google-adsense.html %} <br/>

## Otro Proeycto

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/chess/jhrcek/
</pre>

Clonamos el repositorio

{% highlight bash %}
$ git clone git://github.com/jhrcek/chess-fx.git
{% endhighlight %}

Vemos la ejecucio del cliente de texto:

![importacion paso1 screenshot](/assets/post_003_img4_b.png){: .center-image }

Y de java-fx:

![importacion paso1 screenshot](/assets/post_003_img5_b.png){: .center-image }





[github-chess-001-java]:                      https://github.com/jhrcek/Chess
