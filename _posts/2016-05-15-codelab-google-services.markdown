---
layout: post
comments: false
title:  "CodeLab: Explorando Google Identity Platform para Android"
date:   2016-05-15 19:08:44 -0300
categories: Codelab Google-Services googlesamples
---
Vamos a seguir un CodeLab vinculado a **Google Identity Platform** que se enseña a utilizar algunos **google-services** para autenticarse a través del perfil, o la cuenta de Google.

Específicamente, vamos a ver como se hace esto en **aplicaciones Android**, aunque el mismo Codelab explica como obtener los mismos resultados para iOS y WEB.

Los links son los siguientes:

- [Google Identity Platform](https://developers.google.com/identity/){: target="codelab1"}
- [Google Sign-In for Android](https://developers.google.com/identity/sign-in/android/start){: target="codelab2"}
- [Repo en GitHub](https://github.com/googlesamples/google-services.git){: target="codelab3"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/google-services
</pre>

Clonamos el proyecto de:

{% highlight git %}
$ git clone https://github.com/googlesamples/google-services
{% endhighlight %}

## Paso 01: Abrir con Adndroid Studio

Abrimos la aplicación

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/google-services/android/signin
</pre>

Observamos que con la primera compilación, nos aparece el siguiente error, producto la aplicación no está integrada aún a los servicios de Google:

{% highlight bash %}
File google-services.json is missing. The Google Services Plugin cannot function without it.
   Searched Location:
  /.../GitHub-tmp/googlesamples/google-services/android/signin/app/src/debug/google-services.json
  /.../GitHub-tmp/googlesamples/google-services/android/signin/app/google-services.json
{% endhighlight %}

Para solucionar esto, debemos generar un archivo de configruación llamado ***google-services.json***

![Google Identity Platform para Android - screenshot](/assets/post_013_img1.png)

En la siguiente consola [https://developers.google.com/mobile/add](https://developers.google.com/mobile/add){:target="new"}, elegimos la plataforma Android:

![Google Identity Platform para Android - screenshot](/assets/post_013_img2.png)

Le damos el **nombre** y el **package** a nuestra aplicación:

![Google Identity Platform para Android - screenshot](/assets/post_013_img3.png)

Le damos siguiente para obtener el **google-services.json** que estamos buscando:

![Google Identity Platform para Android - screenshot](/assets/post_013_img4_sign_1.png)

{% include google-adsense.html %} <br/>

## Paso 02: Obtener nuestra clave SHA-1 de "Huella Digital"

Tal como dice, tenemos que obtener nuestra **clave SHA-1**, para utilizarla en el sign-in.

Tenemos dos links que nos ayudan a entender la parte teorica de este paso:

- [Authenticating Your Client](https://developers.google.com/android/guides/client-auth){:target="sh1"}
- [Sign Your App](https://developer.android.com/studio/publish/app-signing.html){:target="sh2"}

Vamos a resumir de forma muy brebe y poco exacta los conceptos de estos artículos.
a) La clave "sha-1" nos sirve como una ***"fingerprint"*** o ***"huella digital"*** de nuestra aplicación mobil. Con lo cual, para futuras update de la aplicación, Google se da cuenta que se trata de la misma app porque tiene la misma ***"huella digital"***

b) El **Keystore** para almacenar la huella digital puede ser para utilizarse en desarrollo o para producción. Si es para **producción**, después va a ser importante que ese keystore que almacena la huella, no lo perdamos... ni olvidemos donde esta, porque lo vamos a necesitar el día que quisieramos hacer un update de la app.

c) Si el **keystore** es para **debug**, podemos utiizar el que nos viene con Android, usualmente en nuestra home **~/.android/debug.keystore**. Recordemos también que en ese repositorio de debug, tal como es de publico conocimiento, la clave que nos pide para abrir el **~/.android/debug.keystore** es **android**.

El keystore de debug **~/.android/debug.keystore** es el que vamos a ejecutar en este ejercicio:

d) Repasando el comando **keytool** con algunos ejemplos básicos, en las distintas variantes vemos que aparece la clave del **SHA-1** que actúa como nuestra **"huella digital"** o **"fingerprint"**, y que necesitamos para obtener a **google-services.json**

**Listando el certificado con keytool -list**: (Se puede agregar -v de verbose):

{% highlight bash %}
$ keytool -list -keystore ~/.android/debug.keystore
Introduzca la contraseña del almacén de claves:

Tipo de Almacén de Claves: JKS
Proveedor de Almacén de Claves: SUN

Su almacén de claves contiene 1 entrada

androiddebugkey, 14/08/2015, PrivateKeyEntry,
Huella Digital de Certificado (SHA1): 2D:ED:D2:B0:75:55:79:AD:4D:C3..........
{% endhighlight %}

Acabamos de ver el contenido del keystore. Vamos a ejectar la variante que nos sugieren en el **CodeLab**:
Donde también nos muestra la clave **SHA-1**:

{% highlight bash %}
keytool -exportcert -list -v -alias androiddebugkey -keystore ~/.android/debug.keystore
IIntroduzca la contraseña del almacén de claves:

Nombre de Alias: androiddebugkey
Fecha de Creación: 14/08/2015
Tipo de Entrada: PrivateKeyEntry
Longitud de la Cadena de Certificado: 1
Certificado[1]:
Propietario: CN=Android Debug, O=Android, C=US
Emisor: CN=Android Debug, O=Android, C=US
Número de serie: 55......
Válido desde: Fri Aug 14 11:35:56 ART 2015 hasta: Sun Aug 06 11:35:56 ART 2045
Huellas digitales del Certificado:
         MD5: BF:54:E4:97:24:4F:F2............
         SHA1: 2D:ED:D2:B0:75:55:79:AD:4D:C3..........
         SHA256: 0F:B1:56:59:FA:B4:D3........................
         Nombre del Algoritmo de Firma: SHA1withRSA
         Versión: 3
{% endhighlight %}

{% include google-adsense.html %} <br/>

## Paso 03: Ingresar nuestra clave SHA-1 de "Huella Digital" y obtener ***google-services.json***

Ahora que ya sabemos cual el nuestra **"Huella Digital" SHA-1** vamos a cargarla para habiliar el paso del registro de **Google sign-in** para nuestra app:


![Google Identity Platform para Android - screenshot](/assets/post_013_img4_sign_2.png)

Paso siguiente **Enable Google sign-in**:

![Google Identity Platform para Android - screenshot](/assets/post_013_img4_sign_3.png)

Y finalemnte podemos descargar el archivo ***google-services.json*** que teníamos que agregar al proyecto del Android Sudio de inicio del post:

![Google Identity Platform para Android - screenshot](/assets/post_013_img4_sign_4.png)

{% include google-adsense.html %} <br/>

## Paso 04: Copiar ***google-services.json*** al proyecto

Copiamos el archivo ***google-services.json*** dentro de **../googlesamples/google-services/android/signin/app**

![Google Identity Platform para Android - screenshot](/assets/post_013_img4_sign_5.png)

Y por fin! podemos **compilar**... pero aún **no podemos ejecutar** la aplicación de ejemplo de **google sign-in** para android:
![Google Identity Platform para Android - screenshot](/assets/post_013_img4_sign_6.png)

El error que nos da es **Sign-In quickstart won´t run unless you update Google Play Services**

Cabe recordar que estoy ejecutando el ejercicio en un **emulador**, no en **dispositivo fisico**

Además el Emulador es el de Android Studio

<pre>
Solucion:
Para el ejercicio, baje al versión en el build.gradle (app) y anduvo ok:
// Dependency for Google Sign-In
// compile 'com.google.android.gms:play-services-auth:9.2.0'
compile 'com.google.android.gms:play-services-auth:9.0.0'

Aunque me anduvo recién después de agregar la KEY en string.xml
que es el paso que se hace mas adelante.
</pre>


Links interesantes sobre el tema de **Google Play**:
- [Google Play Versiones y Dependencias](https://developers.google.com/android/guides/setup){:target="new"}

{% include google-adsense.html %} <br/>

## Paso 05: "Create a web client ID for your server"

En nuestro ***paso 05*** vamos a seguir el ***paso 4*** del [turorial que estamos siguiendo](https://developers.google.com/identity/sign-in/android/start){:target="new"}:

![Google Identity Platform para Android - screenshot](/assets/post_013_img4_sign_7.png)

Tiene de título "Create a web client ID for your server", que no termino de entender que tiene que ver un web client, con un cliente Android... pero bueno, contnuamos con un paso (...mas...) de fe hacia la siguiente indicación:

Para esto, tenemos que ir a la [consola de developers](https://console.developers.google.com/apis/credentials?project=_){:target="new"} y elegir a nuestra aplicación:

![Google Identity Platform para Android - screenshot](/assets/post_013_img5_sign_1.png)

Seleccionamos nuestra aplicación, y tenemos habilitadas nuestras credenciales:

![Google Identity Platform para Android - screenshot](/assets/post_013_img5_sign_2.png)

Nota: La parte **IDs de cliente de OAuth 2.0** es la que necesitamos. La parte **Claves de API** la tenemos porque elegí de mas también habilitar la mensajería... pero para este post, ignoramos esa parte.


Bueno, según el ***"paso 4 del tutorial"*** debería hacer:
**2. Click Add credentials > OAuth 2.0 client ID.**

En el menú castellano que yo veo en mi consola, son los pasos:

![Google Identity Platform para Android - screenshot](/assets/post_013_img5_sign_3.png)

Y elijo la parte **web** por recomendiación del tutorial:
**3. Select Web application.**

![Google Identity Platform para Android - screenshot](/assets/post_013_img5_sign_4.png)

Después de presionar **CREAR** nos genera la clave de **ID de cliente**

![Google Identity Platform para Android - screenshot](/assets/post_013_img6_sign_1.png)

Que copiamos dentro de **string.xml** del Android Studio:

![Google Identity Platform para Android - screenshot](/assets/post_013_img6_sign_2.png)

Aunque si volvemos a ejecutar la App me da el mismo error de que tengo que actualzar el Google Play ...

El error que nos da es **Sign-In quickstart won´t run unless you update Google Play Services**

<pre>
Solución:

Bajar la versión dentro del **build.gradle** de la dependecia para Google Sign-In
// compile 'com.google.android.gms:play-services-auth:9.2.0'
compile 'com.google.android.gms:play-services-auth:9.0.0'
</pre>

Y de esta forma, finalmente!! vemos a la aplicación funcionando:

![Google Sign-in demo - screenshot](/assets/post_013_img7_sign_1.png)

Veamos algunas pantallas:

![Google Sign-in demo - screenshot](/assets/post_013_img7_sign_2.png){: .center-image-2 }

Iniciamos sesión con la cuenta de Google:

![Google Sign-in demo - screenshot](/assets/post_013_img7_sign_3.png){: .center-image-2 }

Nos pide la password. (Son pantallas de Google, no de nuestra app):

![Google Sign-in demo - screenshot](/assets/post_013_img7_sign_4.png){: .center-image-2 }

Aceptar TYC:

![Google Sign-in demo - screenshot](/assets/post_013_img7_sign_5.png){: .center-image-2 }

Y nos desconectamos

![Google Sign-in demo - screenshot](/assets/post_013_img7_sign_6.png){: .center-image-2 }

Con esto damos por cerrado el post de Google Sign In y el ejemplo del CodeLab
