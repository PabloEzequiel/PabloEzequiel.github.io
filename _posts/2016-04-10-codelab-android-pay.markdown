---
layout: post
comments: false
title:  "CodeLab: Android Pay de googlesamples"
date:   2016-04-10 19:08:44 -0300
categories: Android Pay CodeLab googlesamples
---
Vamos a hacer algunas pruebas sobre el [Android Pay][google-android-pay-link1]{:target="apy1"} y para hacer las pruebas, vamos a recorrer al [CodeLab de Google de Androy Pay][google-android-pay-codelab]{:target="pay1"}

Como dijo Sócrates: "No puedo enseñar nada a nadie; solo puedo hacerles pensar"

Pues bien.... comencemos pensando, programando y aunque "sepamos que no sabemos nada" vamos a hacer el esfuerzo de intentar aprender algo nuevo.

## Comencemos

Directorio de trabajo, en nuestra PC utilizaremos la carpeta:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-pay-codelab
</pre>

El proyecto en Android, lo llamaremos de la siguiente manera:

<pre>
TestAndroidPay
pay.probarnocuestanada.com
</pre>

# Paso 01 - Creamos el Proyecto TestAndroidPay a partir del Codelab

Creamos el proyeto Android, y luego seguimos la mayoría de los pasos del [CodeLab de Google de Androy Pay][google-android-pay-codelab]{:target="pay1"}.

El resultado, después de 40 minutos, es el poryecto practimanete finalizado, como se ve en la imagen a continuación, donde se ejecutó el emulador, con el botón de Android Pay:

![importacion paso1 screenshot](/assets/post_007_img3.png){: .center-image }

Cuando presionamos el botón de **Android Pay** del Emulador, la prierma vez, en nuestro caso, nos solicita que asociemos la cuenta de Google al emulador:

![importacion paso1 screenshot](/assets/post_007_img4.png){: .center-image }

Después de Agregar la cuenta, nuevamente presionamos el botón de **Android Pay** del Emulador y obtenermos el siguiente mensaje de error:

***"To make purchase using Android Pay, please setup your card in android pay app"***

![importacion paso1 screenshot](/assets/post_007_img5.png){: .center-image }

¿Como debería continuar? Hay una [pregunta similar el stackoverflow](http://stackoverflow.com/questions/34306835/android-pay-error){:target="stk"}



# Paso 02 - Pensemos

Si bien, fué positivo poder avanzar con la aplicación **codelab** que nos da Google, tenemos que hacer las siguientes preguntas y observaciones

- En el ejemplo, estamos utilizando una apikey de Google ¿Como generamos nuestra propia apikey?
- En la documentación, dice que para compras in-app hay que utilizar [In-app Billing][google-in-app-billing]{:target="pay2"} ¿Que diferencia hay entre **Google Pay** y **In-app Billing**?
- La documentación dice que **Andorid Pay** esta disponible para EEUU y ENG [^1] ¿A que se refiere?
- ¿Como se prueba Android Pay en un ambiente de Testing?
- ¿Como se generan número de Tj de Crédito de Testing para los ambientes de desarrollo?
- La aplicación Andorid Pay ¿Se puede ejecutar y correr sobre el emulador? ¿Hay que habilitar algún permiso extra?

{% include google-adsense.html %} <br/>

Por ahora, interrumpimos el post en este punto, y vamos a avanzar leyendo un poco mas la docuentación oficial antes de retomar.


# Next Step

Seguiremos el ejemplo de [Android Pay Quickstart][google-android-pay-github-demo]{:target="pay2"}

Y luego, las indicaciones en: [Google Android Pay Alta][google-android-start]{:target="pay3"} para utilizar Android Pay en nuestra propia aplicación




# Referencias

[^1]:  https://developers.google.com/android-pay/get-started#step_1


[google-android-pay-link1]:        https://www.android.com/pay/
[google-android-pay-tutor]:        https://developers.google.com/android-pay/android/tutorial
[google-android-pay-codelab]:      https://codelabs.developers.google.com/codelabs/android-pay/index.html
[google-android-samples-tutor]:    https://developer.android.com/samples/index.html
[google-android-samples-github]:   https://github.com/googlesamples
[google-android-pay-github-demo]:  https://github.com/android-pay/androidpay-quickstart
[google-android-start]:            https://developers.google.com/android-pay/
[google-in-app-billing]:           https://developer.android.com/google/play/billing/index.html
