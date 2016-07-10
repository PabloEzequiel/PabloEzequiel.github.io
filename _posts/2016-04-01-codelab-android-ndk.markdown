---
layout: post
comments: false
title:  "¿Que es y como funciona Android NDK?"
date:   2016-04-01 19:08:44 -0300
categories: CodeLab Googlesampes GitHub NDK Android
---
¿Que es **Android NDK**?¿Como funciona?

Para resumir la teoría en dos palabras, podemos decir que **Android NDK (Native Development Kit)** nos permite reutilizar código escrito en C/C++. Y para esto se utiliza de JNI (Java Native Interface).

Muchas aplicaciones, como juegos, hacen uso del NDK. La idea de este post es aprender lo mínimo y necesario para entender de que se trata NDK y JNI.

Para esto, vamos a recorrer el **"CodeLab: Android NDK de googlesamples"** que podemos encontrar en [GitHub: Android NDK][github-android-ndk]{:target="ndk"}

## Comencemos

Directorio de trabajo:

<pre>
/Users/pabloin/Desktop/NoCuestaNada/Mob/GitHub-tmp/googlesamples/android-ndk
</pre>

Android NDK son ejemplos de utilización de codigo nativo.

Observemos que googlesamples nos ofrece varios ejemplos desde GitHub.
Estamos tomando la rama **master** porque nos interesa utilizar al graddle experimental.  

![importacion paso1 screenshot](/assets/post_005_googlesamples_android_ndk.png)

{% include google-adsense.html %} <br/>

## Paso 01: Proyecto hello-jni

Vamos a comenzar compilando el primer proyecto hello-jni

Seguimos las indicaciones de https://github.com/googlesamples/android-ndk/tree/master/hello-jni

Además, podemos consultar al siguiente **Codelab** de Google que explica un proyecto practicamente indentico:
[Codelab de Google Andoir JNI y NDK][google-codelab-link1]{:target="g1"}.

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img2.png)

En el Android Studio, abrimos **Open File/Project Structure...** y **Select NDK location:**

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img3.png)

Hacemos Click en **Sync Project with Gradle Files** y luego en **Run 'app'**

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img4.png)

Veamos los componentes clave del proyecto:

La clase Java

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img5.png)

El objeto hello-jni.c

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img6.png)

Y ademas el script de graddle experimental:

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img7.png)

Vemos que el texto "Hello JNI" es tomado desde la funcion nativa:

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img8.png)

{% include google-adsense.html %} <br/>

## Paso 02: Agregamos un nuevo método JNI

Como mensionábamos previamente, podemos consultar al siguiente **Codelab** de Google que explica un proyecto practicamente indentico: [Codelab de Google Andoir JNI y NDK][google-codelab-link1]{:target="g1"}.

Sobre el **codelab** me parecieron excelentes los puntos 4 y 5 que indican como agregar una función nativa y ademas hacer el debug. Vamos a tratar de hacer essos pasos:


Una función que simplemente diga "Hello Pablo Ezequiel" en el activity:

Primero modificamos el onCreate del Activity para poder ingresar dos textos.

Utilizamos un LinearLayout por código (no XML), para editar menos componentes:

{% highlight java linenos %}

@Override
public void onCreate(Bundle savedInstanceState)
{
    super.onCreate(savedInstanceState);

    /* Create a TextView and set its content.
     * the text is retrieved by calling a native function.
     */
    TextView  tv = new TextView(this);
    tv.setText( stringFromJNI() );

    TextView  tv2 = new TextView(this);
    tv2.setText( sayHelloFromJNI("Pablo Ezequiel") );    // NEW!


    // Diseño principal de la actividad
    LinearLayout principal = new LinearLayout(this);
    principal.setLayoutParams(new ViewGroup.LayoutParams(
            LinearLayout.LayoutParams.MATCH_PARENT,
            LinearLayout.LayoutParams.MATCH_PARENT));
    principal.setOrientation(LinearLayout.VERTICAL);
    principal.addView(tv);
    principal.addView(tv2);

    setContentView(principal);

}

{% endhighlight %}

Luego agregamos en la misma Activity, la nueva función nativa **sayHelloFromJNI**:

{% highlight java %}

    public native String  sayHelloFromJNI(String name);

{% endhighlight %}

Para la cual el compilador nos data la posibilidad de corregirlo:

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img9.png)

Con el asistente del Android Studio podemos implementar el método:

Codigo C native, mayormente generado por el Android Studio:

{% highlight java %}

JNIEXPORT jstring JNICALL
Java_com_example_hellojni_HelloJni_sayHelloFromJNI(JNIEnv *env, jobject instance, jstring name_) {
    const char *name = (*env)->GetStringUTFChars(env, name_, 0);

    // TODO

    char buf_rta[256];
    snprintf(buf_rta, sizeof buf_rta, "Hello %s", name);


    (*env)->ReleaseStringUTFChars(env, name_, name);

    return (*env)->NewStringUTF(env, buf_rta);
}

{% endhighlight %}

Veamos el **IDE**:

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img10.png)

Y el resultado de la ejecución:

![Ejemplo App Android NDK y JNI screenshot](/assets/post_005_img11.png)

De esta forma, podemos cerrar el post, donde utilizando el proyecto de GitHub **hello-jni**, pudimos agregar un nuevo método JNI que utiliza la plataforma NDK.






[github-android-ndk]:    https://github.com/googlesamples/android-ndk
[google-codelab-link1]:  https://codelabs.developers.google.com/codelabs/android-studio-jni/index.html
