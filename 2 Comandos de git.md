# **2 Comandos de Git**

Los comandos de Git son aquellos que nos permiten realizar todas las acciones con nuestro código.

# Instalación de Git

## MAC OS

```
brew install git
```

## LINUX (Debian)

```
sudo apt-get install git
```

## WINDOWS

```
winget install --id Git.Git -e --source winget
```

Para más información acerca de las descargas visita el [sitio oficial de Git de descargas.][1]

[1]: https://git-scm.com/downloads

Para verificar que Git se instaló correctamente asegurate de ejecutar el comando git --vesion (indiferente para cada sistema operativo) en caso de tener un error verifica que lo hayas instalado bien o revisa en el Para más información acerca de las descargas visita el [sitio oficial de Git de descargas.][1]

[1]: https://git-scm.com/downloads

## Verificar la versión de git

```
git --version
```

# Configuración incial

Antes de empezar a utilizar git es necesario hacer unas configuraciones inciales. Las configuraciones globales son ajustes que se establecerán en todos los repositorios que creemos en la computadora. 

## Establecer el nombre del usuario
Establece el nombre del usuario, es decir el desarrollador del equipo.
```
git config --global user.name "<Nombre Appellido>"
```
## Establecer email del usuario
Establece el nombre del email asociado al nombre del usuario para que a la hora de ver el historial de cambios sepamos que miembro hizo cada modificación.
```
git config --global user.email "<email@gmail.com>"
```

## Establecer la coloración de la terminal
Esto permitirá que a la hora de ejecutar comandos lo veamos con colores y de esta manera más legible.
```
git config --global color.ui auto
```

## Configurar el CRLF
Entre Windows y Linux/MacOS existen formas diferentes de tratar a los saltos de líneas y a los espacios. Por eso es importante configurar un estandar para que no se vean cambios en el código que sean simplemente espacios en blanco y código importante modificado.

WINDOWS
```
git config core.autocrlf true
```
LINUX o MAC
```
git config core.autocrlf input
```

## Configurar editor
En caso de tener algún problema o simplemente querer modificar alguna configuración de git es útil tener configurado un editor por defecto que se abra en caso de haber un problema con git o querer hacer modificaciones. Los editores pueden ser Visual Studio Code, VIM o Emacs. Solo debes colocar el nombre del editor seguido del comando, como vemos en el evento.
```
git config --global core.editor <nombre del editor>
```

## Ver la configuración de Git

Retorna la configuración actual de Git
```
git config --list
```
# Inicialización del repositorio de Git

Ya tenemos todo configurado, es hora de crear nuestro repositorio. Para crear el repositorio debes situarte en la carpeta donde tengas tus archivos, o vallas a crearlos y ejecutar el siguiente comando. Al iniciar un repositorio se creará una carpeta oculta llamada `.git`. En esta carpeta se encuentra las configuraciones del proyecto y la cronología del proyecto como tal, los commits, etcétera.

**Importante**: no es necesario ponerle nombre al repositorio

```
git init "<Nombre del repositorio>"
```

## Ver el estado del repositorio local
Muestra el estado del repositorio local, archivos agregados (color verde), no agregados (color rojo), etc. Saber el estado del proyecto nos permite conocer los archivos que se encuentran agregados, los que no, si hemos realizado un commit, entre otras cosas.
```
git status
```

# Working area

## Agregar archivos
Los archivos que esten en el repositorio los deberemos agregar al repositorio. Tambien cuando hacemos una modificación en alguno de ellos tambien se lo debe de agregar. Para agregar utilizamos el comando `git add` pero puede recivir varios posibles parámetros tales como:
* `git add .` Agregarpa todos los archivos del directorio actual

* `git add *` Agregará todos los archivos nuevos y/o modificados

* `git add <archivo>.<ext> .... <archivo>.<ext>` Agregará los archivos los cuales hayamos especificado el nombre y la extención del mismo. En caso de querer agregar mas de uno escriba el nombre y extención de ese archivo separado del otro por un espacio.

* `git add *.txt` Agregará todos los archivos con la extención .txt, tu puedes especificar la extención que quieras. 

## Ignorar archivos

Si se quiere agregar varios archivos pero con algunas restricciones se puede crear un archivo llamado `.gitignore`. En este archivo podremos escribir ciertas reglas para que a la hora de agregar los archivos a la etapa de stage solo se agregen los que cumplan con ciertas características y no todos los archivos. Estas restricciones podrían ser que se ignoren los archivos con la extención .txt.

Reglas de ignoración de archivos:
```
# Comentarios

Ignora archivos del sistema Mac 
.DS_store

# Ignora la carpeta node_modules
node_modules

# Ignora todos los archivos de texto
*.txt

# Ignora los archivos relacionados a API keys
.env

# Ignora archivos de configuración SASS
.sass-cacheomentarios 
```

## Remover archivos
Al remover un archivo no lo estas eliminado solamente estas sacando al archivo de la etapa de preparación. Esto es últil si agregaste un archivo que no querias o necesitas hacer una última modificación.
```
git resert <archivo>
```

## Deshacer cambios en archivos

Deshace los cambios realizados al archivo especificado.
```
git checkout <archivo>.<ext> 
```

Deshace forzadamente los cambios realizados desde el último commit.
```
git checkout -f
```

Quita del commit al archivo y lo devuleve al área de trabajo.
```
git restore --staged <archivo>
```

# Staging area

## Commitear los archivos
Comprometer los archivos o commitearlos es la etapa en la cual pasamos los archivos locales a la etapa de *stage* para luego subirlos al repositorio. El mensaje del commit es importante ya que con el podremos saber que cambios ha realizado cada desarrollador. Si no agregamos un mensaje se nos abrirá el editor de código establecido por defecto y nos colocará el cursor al principio del archivo abrierto para escribir el mensage del commit, luego de escribirlo guardamos y cerramos el editor.

Compromete los cambios, para agregar el mensaje del commit se abrirá el editor de código configurado por defecto para poder agregar el mensaje del commit:
```
git commit
```

Si se quiere comprometer los archivos y al mismo tiempo colocar su mensaje deberemos utilizar el siguiente comando:
```
git commit -m "<Mensaje del commit>"
```

Agrega los archivos a la vez que realiza el commit
```
git commit -am "<Mensaje del commit>"
```

## Deshacer commits

**Deshacer el último commit conservando los cambios**:
```
git reset --soft HEAD~1
```
**Deshacer el último commit sin conservar los cambios**:
```
git reset --hard HEAD~1
```
**Deshacer el último commit ya subido al repositorio**:
```
git revert <commit hash>
```

## Modificación de mensajes de commits

Volver a escribir el comentario del último commit.
```
git commit --amend -m "Este es el mensaje correcto"
```

# Repository

## Agregar repositorio
Al repositorio en Git se lo llama origen remoto ya que es justamente eso. Para agregar un origen (se puede agregar más de uno) se debe ejecutar el siguiente comando. Donde la url a especificar será la url del repositorio que hayas creado. Es decir que antes de agregar el origen remoto debes crearlo. Para crearlo revisa este archivo.
```
git remote add origin <url>
```
## Subir cambios al repositorio
Una vez pasado los archivos la etapa de stage es necesario subirlos al repositorio (origen remoto) para poder ver los cambios y ya no estar de manera local solamente. En el comando mostrado subimos los archivos al repositorio (push) especificado (origin).
``` 
git push origin <nombre de la rama>
```
En caso de haber errores puedes solucionarlo mediante el comando
```
git push origin <nombre de la rama> --force
```

## Descargar cambios del repositorio a local

Este comando permite traer los cambios del repositorio a local.
```
git fetch origin
```

Descarga los cambios del repositorio a local.
```
git pull origin master
```

# Ramas

## Ramas

## Ver rama actual
Si se quiere ver la rama actual en la cual nos encontramos debemos ejecutar el comando. Este devolverá una lista de todas las ramas creadas y la rama en la que nos encontramos.
```
git branch
```

## Crear rama
Creará una rama con el nombre especificado.
```
git branch <nombre de la rama>
```

## Cambiar entre ramas
Cambiaremos entre ramas para trabajar en los diferentes ambientes aislados. Como parámetro el comando recibe el nombre de la rama a la cual nos quermos cambiar.
```
git checkout <nombre de la rama>

# Comando equivalente
git switch <nombre de la rama>
```
## Unir dos ramas
Si se terminó de desarrollar el trabajo en una de las ramas y se quiere unificar el proyecto se debe unir la rama adyasente a la rama principal (main/master). Como parámetro el comando `git merge` recibe el nombre de la rama a la que esta se unirá.
```
git merge <nombre de la rama>
```

## Eliminar rama 

Poscisionandose desde otra rama con el comando se puede eliminar la rama especificada enm el parámetro.
```
git branch -D <nombre de la rama>
```

## Resolver conflictos entre ramas

Cuando se modifican los mismos archivos en dos ramas diferentes esto puede generar conflictos. Ya que al modificar los mismos archivos git no sabe que hacer con los cambios. Cuando intentemos unir dos ramas git nos avisará del conflicto. Para solucionarlo deberemos abrir el editor de código y seleccionar manualmente el código con el que nos queremos quedar, es decir, git nos dirá cual es el trozo de código modificado de cada rama y tendremos que eliminar el código que queremos descartar para quedarnos con la modificación definitiva. Una vez realizado esto se habrá solucionado el conflicto y podremos unir las dos ramas.

# Historial

## Ver cambios del proyecto

Permite ver la diferencia entre los archivos almacenados y los subidos al repositorio. Al ejecutar el comando nos detalla las líneas que se han eliminado, modificado, etcétera.
```
git diff <archivo>
```

Permite ver un resumen de los cambios del archivo, a modo de resumen nos indica la cantidad de líneas agregadas, modificadas, etcétera.
```
git diff --stat <archivo>
```

## Historial de cambios

Permite visualizar un historial de los commits. Por cada commit realizado se mostrará información sobre el hash del commit, usuario que lo haya realizado, etcétera.
```
git log
```

Cambia al commit especificado con su hash. Es decir, volvemos una versión atrás dentro del proyecto. 
```
git chekout <commit hash>
```

Para ir al último commit se utiliza el comando.
git commit --amend -m "Este es el mensaje correcto"
```
git checkout master
```
