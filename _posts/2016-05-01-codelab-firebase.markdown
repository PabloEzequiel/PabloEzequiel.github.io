---
layout: post
comments: false
title:  "CodeLab: Firebase de googlesamples"
date:   2016-05-01 19:08:44 -0300
categories: Codelab Firebase googlesamplesr
---
Desde que vi los videos del Google I/0 2016, me llamó la atención las posibilidades de Firebase: Fué uno de los productos destacados del Google I/O. Nosotros como desarrolladores: ¿Como podemos sacarle provecho?¿De que forma se configura?¿Que se puede hacer con el uso gratuito de la plataforma?

Vamos a tratar de encontrar respuestas a estras preguntas, mientras recorremos el [CodeLab de Google de Firebase][google-codelab-firebase-1]{: target="new"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat
</pre>

Clonamos el proyecto:

{% highlight git %}
$ git clone https://github.com/firebase/friendlychat
{% endhighlight %}

Y de aquí vamos a [Firebase](https://www.firebase.com/){:target="fb"}. En mi caso, ya estaba dado de alta en Firebase [cuando realicés mis primeras pruebas en la plataforma][pncn-post-firebase-1]{: target="pncn"}... por cierto, sin demasiado éxito, o con un alto grado de fracaso...


## Paso 01: Creamos nuestro proyecto en Firebase

Sigueindo al CodeLab, denominamos al proyecto **FriendlyChat** dentro de la consola de **Firebase**

![Firebase screenshot](/assets/post_009_img1.png)

Una vez creado el pryecto, vemos la siguiente pantalla de Firebase:

![Firebase screenshot](/assets/post_009_img2.png)

Y después de presionar el boton de Firebase </> tenemos el código para Añadir ***Firebase a nuestra aplicación web***

![Firebase screenshot](/assets/post_009_img3.png)

Agregamos del snippet de **Firebase Console > Overview > Add Firebase to your web app**

![Firebase screenshot](/assets/post_009_img4.png)

{% include google-adsense.html %} <br/>

## Paso 02: Enable Google Auth

Ahora debemos habilitar el **Google Sign In** en lai izquierda dentro de AUTH

![Firebase screenshot](/assets/post_009_img5.png)


{% include google-adsense.html %} <br/>

## Paso 03: Instalamos Firebase CLI (Command Line Interface)

Veamos como instalamos Firebase Command Line Interface.

¿Que es Firebase Hosting? El [video oficial de Firebase](https://www.youtube.com/watch?v=jsRVHeQd5kU){:target="new"} lo explica de una forma concisa

Basicamwente nos permite centrarnos mas en las construicción de nuestra aplicación, que en la configuración de la plataforma.

Seguimos los pasos:

![Firebase screenshot](/assets/post_009_img6.png)

y

![Firebase screenshot](/assets/post_009_img7.png)

Y para hacer la instalación ejecutamos

{% highlight bash %}
$ npm install -g firebase-tools
{% endhighlight %}

A lo cual me da un problemas de permisos. Según el codelab, nos lleva a una pagina donde [hay tres formas de solucionar este problema](https://docs.npmjs.com/getting-started/fixing-npm-permissions){:target="new"}: elegimos la tercera que es la instalacion de **Homebrew package manager**, por ser la recomendada para una Mac OS.

***Instalamos Homebrew*** todo ok:
{% highlight bash %}
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

***Ejecutamos brew install node*** para solucionar el problema de permisos, todo ok:
{% highlight bash %}
$ brew install node
{% endhighlight %}

Con lo cual, podemos reintentar la instalaciónd de Firebase CLI:

{% highlight bash %}
$ npm install -g firebase-tools
{% endhighlight %}

Aunque el error persiste....

Continuemos:

Hay un [post muy bueno](https://johnpapa.net/how-to-use-npm-global-without-sudo-on-osx/){:target="oks"} sobre como solucionar los prolemas de permisos de Homebrew en Mac OS, sin recurrir al SUDO. Y recomienda ampliamente el uso de Homebrew.

Vamos a seguir los pasos de ese post, que recomienda desintalar y volver a instalar el nod con brew:

Veamos el resultado:

{% highlight bash %}

MacBook-Pro-de-Pablo:PabloEzequiel.github.io pabloin$ sudo rm -rf /usr/local/lib/node_modules
Password:
MacBook-Pro-de-Pablo:PabloEzequiel.github.io pabloin$ sudo rm -rf ~/.npm
MacBook-Pro-de-Pablo:PabloEzequiel.github.io pabloin$ brew uninstall node
Uninstalling /usr/local/Cellar/node/6.2.2... (3,771 files, 38.7M)

MacBook-Pro-de-Pablo:PabloEzequiel.github.io pabloin$ brew install node --without-npm
==> Installing dependencies for node: xz, pkg-config
==> Installing node dependency: xz
==> Downloading https://homebrew.bintray.com/bottles/xz-5.2.2.el_capitan.bottle.tar.gz
######################################################################## 100.0%
==> Pouring xz-5.2.2.el_capitan.bottle.tar.gz
🍺  /usr/local/Cellar/xz/5.2.2: 91 files, 1.4M
==> Installing node dependency: pkg-config
==> Downloading https://homebrew.bintray.com/bottles/pkg-config-0.29.1.el_capitan.bottle.tar.gz
######################################################################## 100.0%
==> Pouring pkg-config-0.29.1.el_capitan.bottle.tar.gz

🍺  /usr/local/Cellar/pkg-config/0.29.1: 10 files, 627.2K
==> Installing node
==> Downloading https://nodejs.org/dist/v6.2.2/node-v6.2.2.tar.xz
######################################################################## 100.0%
==> ./configure --prefix=/usr/local/Cellar/node/6.2.2 --without-npm

==> make install
....

/usr/local/lib/dtrace/node.d
==> Caveats
Homebrew has NOT installed npm. If you later install it, you should supplement
your NODE_PATH with the npm module folder:
  /usr/local/lib/node_modules
Please note by default only English locale support is provided. If you need
full locale support you should either rebuild with full icu:
  `brew reinstall node --with-full-icu`
or add full icu data at runtime following:
  https://github.com/nodejs/node/wiki/Intl#using-and-customizing-the-small-icu-build
==> Summary
🍺  /usr/local/Cellar/node/6.2.2: 143 files, 27.3M, built in 8 minutes 58 seconds

MacBook-Pro-de-Pablo:PabloEzequiel.github.io pabloin$
{% endhighlight %}

Después de casi 9 minutos que duró la instalación del último paso, podemos continuar con el siguiente:

{% highlight bash %}
mkdir "${HOME}/.npm-packages"
echo NPM_PACKAGES="${HOME}/.npm-packages" >> ${HOME}/.bashrc
echo prefix=${HOME}/.npm-packages >> ${HOME}/.npmrc
{% endhighlight %}

continuamos con la instalación de la ultima verion:

{% highlight bash %}
curl -L https://www.npmjs.org/install.sh | sh
{% endhighlight %}

Y luego:

{% highlight bash %}
$ echo NODE_PATH=\"\$NPM_PACKAGES/lib/node_modules\:\$NODE_PATH\" >> ${HOME}/.bashrc
$ echo PATH=\"\$NPM_PACKAGES/bin\:\$PATH\" >> ${HOME}/.bashrc
$ cat  ${HOME}/.bashrc
NPM_PACKAGES=/Users/pabloin/.npm-packages
NODE_PATH="$NPM_PACKAGES/lib/node_modules:$NODE_PATH"
PATH="$NPM_PACKAGES/bin:$PATH"

$ echo source "~/.bashrc" >> ${HOME}/.bash_profile
{% endhighlight %}


Repasando un poco de bash, según el post de [^1]:

{% highlight bash %}
/etc/profile --> Se ejecuta al iniciar la sesión.
/etc/bashrc  --> Se ejecuta al ejecutar el programa bash

Para nuestro usuario:

~/.bash_profile --> Se ejecuta el .bash_profile cuando el usuario inicia su sesión.
~/.bashrc --> Se ejecuta el .bashrc el usuairo ejecuta el programa bash.
{% endhighlight %}

Verificando la instalacion de node :

{% highlight bash %}
$ source ~/.bashrc
$ cat ~/.npmrc
prefix=/Users/pabloin/.npm-packages
$ cat ~/.bashrc
NPM_PACKAGES=/Users/pabloin/.npm-packages
NODE_PATH="$NPM_PACKAGES/lib/node_modules:$NODE_PATH"
PATH="$NPM_PACKAGES/bin:$PATH"
$ node -v
v4.4.2
$ npm -v
3.10.3
$ npm list -g --depth=0
/Users/pabloin/.npm-packages/lib
└── npm@3.10.3

$ npm list -g --depth=1
/Users/pabloin/.npm-packages/lib
└─┬ npm@3.10.3
  ├── abbrev@1.0.9
  ├── ansi-regex@2.0.0
	...

{% endhighlight %}


Ok.... Y ahora, después de todo lo que trabajamos, deberíamos (por fin!), poder instalar el Firbase CLI:

{% highlight bash %}
$ npm install -g firebase-tools
/Users/pabloin/.npm-packages/bin/firebase -> /Users/pabloin/.npm-packages/lib/node_modules/firebase-tools/bin/firebase
/Users/pabloin/.npm-packages/lib
└─┬ firebase-tools@3.0.4
  ├─┬ archiver@0.16.0

  │ ├── async@1.4.2
  │ ├── buffer-crc32@0.2.5
  │ ├─┬ glob@5.0.15
  │ │ ├─┬ inflight@1.0.5
  │ │ │ └── wrappy@1.0.2
....
....
  │ └── semver-diff@2.1.0
  ├─┬ user-home@2.0.0
  │ └── os-homedir@1.0.1
  ├── uuid@2.0.2

  └─┬ winston@1.1.2
    ├── async@1.0.0
    ├── cycle@1.0.3
    ├── eyes@0.1.8
    ├── pkginfo@0.3.1
    └── stack-trace@0.0.9

{% endhighlight %}

Mostramos la imagen con el resultado de la instalación de **firebase-tools**

![Firebase screenshot](/assets/post_009_img5.png)

Verificamos la instalación

{% highlight bash %}
$ firebase version
3.0.4
{% endhighlight %}

Excelente, con el Firebase CLI instalado ok, vamos al siguente paso:

{% include google-adsense.html %} <br/>

## Paso 04: Otorgando permisos a Firebase Command Line Interface (CLI)

Logramos finalizar el paso de **$ npm install -g firebase-tools** y el paso siguiente se muestra en la siguiente imagen:

![Firebase screenshot](/assets/post_009_img9.png)

Pero quisiera agregar un comentario de algo que me llamó mucho la atención:

Cuando ejecutamos **firebase login** nos abre el browser (safari) y nos dice que va a vincular nuestra cuenta de google con Firebase, para lo cual debemos otorgar algunos permisos.

Primero es importante estar dentro de **web_start**:

{% highlight bash %}
cd /Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/firebase/friendlychat/web-start
{% endhighlight %}

Luego, veamos los resultados de ejecutar los comandos de Firebase:

{% highlight bash %}
$ firebase login
$ firebase init
$ firebase deploy
{% endhighlight %}


Ejecutamos el **Firebase login**

![Firebase screenshot](/assets/post_009_img10.png)

Que abre el Safari para solicitar permisos

![Firebase screenshot](/assets/post_009_img11.png)

Luego me dice que el login es exitoso

![Firebase screenshot](/assets/post_009_img12.png)

Ejecutamos el **Firebase init** para la configuración

![Firebase screenshot](/assets/post_009_img13.png)

Tenemos que elegir opciones para realizar el Setup del proyecto

![Firebase screenshot](/assets/post_009_img14.png)

Opciones sobre Hosting Setup:

![Firebase screenshot](/assets/post_009_img15.png)

Finalmente Eejecutamos el **Firebase deploy**:

![Firebase screenshot](/assets/post_009_img16.png)

Veamos la consola del Firebase:

![Firebase screenshot](/assets/post_009_img17.png)

Y la evidencia de la instalación correcta

![Firebase screenshot](/assets/post_009_img18.png)

{% include google-adsense.html %} <br/>

## Paso 05: ¿Y ahora que esta todo ok...? ¿Como seguimos?

Segun el **CodeLab** (fin del paso 5) tenemos que ejectuar (siempre dentrp del directorio del proyecto **web_start**):

{% highlight bash %}
$ firebase use --add
{% endhighlight %}

El resultado es:

![Firebase screenshot](/assets/post_009_img19.png)

Levantamos la aplicacion con

{% highlight bash %}
$ firebase serve
{% endhighlight %}

Y luego el server levantado:

![Firebase screenshot](/assets/post_009_img20.png)

El problema, es que cuando invocamos a:

http://localhost:5000

no encotramos nada, simplemente algo que nos dice que la aplicacion está ejecutando ok...
Pero ***¿Donde está el chat del CodeLab?***

![Firebase screenshot](/assets/post_009_img21.png)


.... Ok... por ahora suspendemos el post en este punto, esperando tener mejor suerte con los pasos siguientes cuando retomemos....

 





## Referencias

[^1]: http://elpuig.xeill.net/Members/rborrell/articles/los-archivos-bashrc-bash_profile-etc-bashrc-etc-profile-los-archivos-bashrc-bash_profile-etc-bashrc-etc-profile-cual-utilizar




[google-codelab-firebase-1]:  https://codelabs.developers.google.com/codelabs/firebase-web/index.html
[pncn-post-firebase-1]:       http://www.probarnocuestanada.com/2016/04/what-about-firebase.html
