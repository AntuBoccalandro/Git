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

## **snapshot**