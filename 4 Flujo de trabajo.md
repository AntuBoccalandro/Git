# **4 Flujo de trabajo en Git**

Existen bastantes flujo de trabajos, a continuación detallaremos los más utilizados.

* Centralizado
* Gitflow
* Bifurcación
* Ramas de funcionalidades

# **Flujo de trabajo centralizado**

El flujo de trabajo consiste en centralizar todos los cambios en una sola rama llamada `main`, en esta rama se subirán todos los cambios realizados por los diferentes desarrolladores. 

El funcionamiento consiste en que todos los desarrolladores clonan el repositorio central. Cada desarrollador localmente realizará los commit de manera local para que a la hora de la publicación todos los desarrolladores suban sus cambios al repositorio.

![](https://wac-cdn.atlassian.com/dam/jcr:8fe7b38d-e671-4d2f-bde7-52c5f60e1164/01%20Central%20Repository.svg?cdnVersion=638)

# **Flujo de trabajo de bifurcación**

Este flujo de trabajo suele utilizarse en proyectos de código abierto. No se centra en un servidor central si no que cada colaborador tiene dos repositorios de Git: uno local y privado, y otro público y en servidor. Cabe aclarar que el único que pueda subir los cambios al respositorio será el creador o el mantenedor del proyecto, esto permite que cualquier persona no pueda subir los cambios y tengan que ser revisados por el creador antes de subir los cambios.

* Podemos resumir el funcionamiento de este flujo de trabajo en los siguientes pasos:
* Un desarrollador "bifurca" un repositorio"oficial" en servidor. Esto crea su propia copia en servidor.
* La nueva copia en servidor se clona en su sistema local.
* Se añade una ruta remota de Git para el repositorio "oficial" al clon local.
* Se crea una nueva rama de función local.
* El desarrollador hace cambios en la nueva rama.
* Se crean nuevas confirmaciones para los cambios.
* La rama se envía a la copia en servidor del desarrollador.
* El desarrollador abre una solicitud de incorporación de cambios desde la nueva rama al repositorio "oficial".
* La solicitud de incorporación de cambios se aprueba para la fusión y se hace la fusión en el repositorio en servidor original.


# **Flujo de trabajo de ramas de funcionalidades**

Este flujo de trabajo se basa en la creación de ramas para el desarrollo de nuevas funcionalidades o modificaciones. De esta manera el código de la rama `main` del proyecto siempre tendrá una versión estable del proyecto. Las ramas servirán como entornos aislados que proporcionarán seguridad a la hora de realizar modificaciones del proyecto principal.

Se basa en la creación de un repositorio central con la rama `main`. Cada desarrollador que quiera realizar una nueva funcionalidad o modificación deberá crear una nueva rama, al subir esta rama al repositorio central los demás desarrolladores podrán revisar el código, dar sugerencias para que cuando la nueva funcionalidad no contenga errores se pueda fusionar a la rama `main`.

# **Flujo de trabajo de Gitflow**

Este flujo de trabajo fue de los primeros flujos de trabajo y aunque no es muy recomendado actualmente es una referencia. Se basa en la creación de ramas específicas con ciertas funciones, además se definen las interacciones que cada rama puede realizar con las otras, también especifica como funcionar las ramas.

Existe una extención de línea de comandos llamada `gitflow` que permite trabajar con este tipo de flujo de trabajo, los comandos serán los mismos que utilizamos habitualemente solo que mediante esta herramienta se haran menos largos los comandos y más convenientes si se desea utilizar este flujo de trabajo.

Las ramas principales son la rama `main` y la rama `develop`. En la rama main se subirán los cambios definitivos de cada versión del desarrollo, en cambio en la rama develop es de donde se crearán nuevas ramas para cada funcionalidad.

![](https://wac-cdn.atlassian.com/dam/jcr:a13c18d6-94f3-4fc4-84fb-2b8f1b2fd339/01%20How%20it%20works.svg?cdnVersion=638)

De la rama develop derivarán las ramas de `features` que servirán para el desarrollo de cada funcionalidad. Cuando se termine de desarrollar la funcionalidad esta se unirá a la rama develop, esta rama actuará como la principal de las funcionalidades. 

![](https://wac-cdn.atlassian.com/dam/jcr:34c86360-8dea-4be4-92f7-6597d4d5bfae/02%20Feature%20branches.svg?cdnVersion=638)

Las ramas de publicación se crean cada vez que se acumulan suficientes funcionalidades en la rama de desarrollo. Cuando se realiza una publicación se debe crear una rama llamada `release` a partir de develop. En esta rama no se podrán agregar nuevas funcionalides y solo se podrá relizar tareas relacionadas a la publicación, como solucionar últimos errores y generar la documentación de dicha versión. Esta rama luego se unirá con la rama main para ver el el proyecto principal el historial de versiones del proyecto. Cuadndo se realize la publicación la rama `release`se unirá de nuevo con la rama `develop`. Este sistema de ramas permite que se pueda estar trabajando en una publicación a la vez que en la rama de desarrollo se siguen agregando nuevas funcionalidades. 

![](https://wac-cdn.atlassian.com/dam/jcr:8f00f1a4-ef2d-498a-a2c6-8020bb97902f/03%20Release%20branches.svg?cdnVersion=638)

Las ramas de mantenimiento, de corrección o de `hotfix` sirven para reparar rápidamente las publicaciones de producción. Las ramas hotfix son muy similares a las ramas release y feature, salvo por el hecho de que se basan en la rama main y no en la develop. Esta es la única rama que debería bifurcarse directamente a partir de main. Cuando se haya terminado de aplicar la corrección, debería fusionarse en main y develop (o la rama release actual), y main debería etiquetarse con un número de versión actualizado.

![](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=638)

Resumiendo:

* Se crea una rama develop a partir de main.
* Se crea una rama release a partir de la develop.
* Se crean ramas feature a partir de la develop.
* Cuando se termina una rama feature, se fusiona en la rama develop.
* Cuando la rama release está lista, se fusiona en las ramas develop y main.
* Si se detecta un problema en main, se crea una rama hotfix a partir de main.
* Una vez terminada la rama hotfix, esta se fusiona tanto en develop como en main.

