# **3 Ejemplo práctico en WINDOWS**

### Creamos carpeta

```
mkdir my-app
```

### Realizamos las configuraciones iniciales e inicializamos el repositorio local

```
git init my-app
```

```
git config --global user.name "Antú Boccalandro"
```

```
git config --global user.email "email@gmail.com"
```

```
git config --global core.autocrlf true
```

```
git config --global core.editor code
```
### Creo el repositorio en GitHub

<video width="320" height="240" controls>
  <source src="https://imgur.com/gallery/ZYumnEs" type="video/mp4">
</video>

### Añadimos el origen remoto (repositorio de GitHub)

```
git remote add origin https://github.com/AntuBoccalandro/my-app
```

### Creamos app.py

```
print('Hello World') > app.py
```

### Modificamos app.py

```
print('Usando Git')
```

### Agregamos los archivos a la etapa de preparación

```
git add *
```

### Agregamos los archivos a la etapa de stage (commit)

```
git commit -m "Creamos app.py"
```

### Subimos los archivos al repositorio

```
git push -u origin master
```