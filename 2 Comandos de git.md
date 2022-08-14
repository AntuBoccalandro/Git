# **2 Comandos de Git**

Antes de comenzar a ejecutar comandos en importante conocer de que manera ejecutamos estos comados, ¿porque en este orden?

## **Flujo de trabajo con Git**

Ahora aprenderemos sobre lo denominado Flujo de Trabajo con Git o Gitflow. Es la manera de aprender bien como trabajar con esta herramienta en equipo o simplemente solo en algun proyecto personal.

Primero hay que entender ciertos conceptos:
Local: cuando hablamos de git hablamos de términos como repositorio local o remoto. Nos referimos a *local* cuando el código de nuestra aplicación se encuentra de manera local, es decir en la unidad de almacenamiento de nuesta computadora. Hablamos de *remoto* cuando nuestro código se encuentra en el repositrio, alojado en un servidor remoto. 

## **Instalación de Git**

### MAC OS

```
brew install git
```

### LINUX (Debian)

```
sudo apt-get install git
```

### WINDOWS

```
winget install --id Git.Git -e --source winget
```

Para más información acerca de las descargas visita el [sitio oficial de Git de descargas.][1]

[1]: https://git-scm.com/downloads

Para verificar que Git se instaló correctamente asegurate de ejecutar el comando git --vesion (indiferente para cada sistema operativo) en caso de tener un error verifica que lo hayas instalado bien o revisa en el Para más información acerca de las descargas visita el [sitio oficial de Git de descargas.][1]

[1]: https://git-scm.com/downloads

## **Configuración incial**

Antes de empezar a utilizar git es necesario hacer unas configuraciones inciales.

### Establecer el nombre del usuario
Establece el nombre del usuario, es decir el desarrollador del equipo.
```
git config --global user.name "Nombre Appellido"
```
### Establecer email del usuario
Establece el nombre del email asociado al nombre del usuario para que a la hora de ver el historial de cambios sepamos que miembro hizo cada modificación.
```
git config --global user.email "email@gmail.com"
```

### Establecer la coloración de la terminal
Esto permitirá que a la hora de ejecutar comandos lo veamos con colores y de esta manera más legible.
```
git config --global color.ui auto
```

### Configurar el CRLF
Entre Windows y Linux/MacOS existen formas diferentes de tratar a los saltos de líneas y a los espacios. Por eso es importante configurar un estandar para que no se vean cambios en el código que sean simplemente espacios en blanco y código importante modificado.

WINDOWS
```
git config core.autocrlf true
```
LINUX o MAC
```
git config core.autocrlf input
```

### Configurar editor
En caso de tener algún problema o simplemente querer modificar alguna configuración de git es útil tener configurado un editor por defecto que se abra en caso de haber un problema con git o querer hacer modificaciones. Los editores pueden ser Visual Studio Code, VIM o Emacs. Solo debes colocar el nombre del editor seguido del comando, como vemos en el evento.
```
git config --global core.editor <nombre del editor>
```

## **Inicialización del repositorio de Git**

Ya tenemos todo configurado, es hora de crear nuestro repositorio. Para crear el repositorio debes situarte en la carpeta donde tengas tus archivos, o vallas a crearlos y ejecutar el siguiente comando.

**Importante**: no es necesario ponerle nombre al repositorio
```
git init "Nombre del repositorio"
```

## **Trabajo con Git**

### Ver el estado del repositorio local
Muestra el estado del repositorio local, archivos agregados (color verde), no agregados (color rojo), etc.
```
git status
```

### Agregar archivos
Los archivos que esten en el repositorio los deberemos agregar al repositorio. Tambien cuando hacemos una modificación en alguno de ellos tambien se lo debe de agregar. Para agregar utilizamos el comando `git add` pero puede recivir varios posibles parámetros tales como:
* `git add *` Agregará todos los archivos nuevos y/o modificados

* `git add arhivo1.txt archivo2.html` Agregará los archivos los cuales hayamos especificado el nombre y la extención del mismo. En caso de querer agregar mas de uno escriba el nombre y extención de ese archivo separado del otro por un espacio.

* `git add *.txt` Agregará todos los archivos con la extención .txt, tu puedes especificar la extención que quieras. 
```
git add 
```

### Remover archivos
Al remover un archivo no lo estas eliminado solamente estas sacando al archivo de la etapa de preparación. Esto es últil si agregaste un archivo que no querias o necesitas hacer una última modificación.
```
git resert <Nombre del archivo>
```

### Comprometer los archivos
Comprometer los archivos o commitearlos es la etapa en la cual pasamos los archivos locales a la etapa de *stage* para luego subirlos al repositorio. El mensaje del commit es importante ya que con el podremos saber que cambios ha realizado cada desarrollador. Si no agregamos un mensaje se nos abrirá el editor de código establecido por defecto y nos colocará el cursor al principio del archivo abrierto para escribir el mensage del commit, luego de escribirlo guardamos y cerramos el editor.
```
git commit -m "Mensaje del commit"
```

### Ver rama actual
Si se quiere ver la rama actual en la cual nos encontramos debemos ejecutar el comando. Este devolverá una lista de todas las ramas creadas y la rama en la que nos encontramos.
```
git branch
```

### Crear rama
Creará una rama con el nombre especificado.
```
git branch <nombre de la rama>
```

### Cambiar entre ramas
Cambiaremos entre ramas para trabajar en los diferentes ambientes aislados. Como parámetro el comando recibe el nombre de la rama a la cual nos quermos cambiar.
```
git checkout <nombre de la rama>
```
### Unir dos ramas
Si se terminó de desarrollar el trabajo en una de las ramas y se quiere unificar el proyecto se debe unir la rama adyasente a la rama principal (main/master). Como parámetro el comando `git merge` recibe el nombre de la rama a la que esta se unirá.
```
git merge <nombre de la rama>
```

### Agregar repositorio
Al repositorio en Git se lo llama origen remoto ya que es justamente eso. Para agregar un origen (se puede agregar más de uno) se debe ejecutar el siguiente comando. Donde la url a especificar será la url del repositorio que hayas creado. Es decir que antes de agregar el origen remoto debes crearlo. Para crearlo revisa este archivo.
```
git remote add origin <url>
```
### Subir cambios al repositorio
Una vez pasado los archivos la etapa de stage es necesario subirlos al repositorio (origen remoto) para poder ver los cambios y ya no estar de manera local solamente. En el comando mostrado subimos los archivos al repositorio (push) especificado (origin) y mediante el parámetro -u creamos la rama "master" si esta no esta creada.
``` 
git push -u origin master
```
En caso de haber errores puedes solucionarlo mediante el comando
```
git push origin master --force
```