# Git básico.

---

## Instalación de git en Debian.
```sh
:~# apt-get install git
```

**Para saber que versión que tengo instalada.**
```sh
git --version
```

**Para ver todos los comandos de git.**
```sh
git
```

---

## Comandos de Git.

**Comenzar un repositorio.**
```sh
git init
```

**Poner mis datos de usuario.**
```sh
git config --global user.name "Mi Nombre"
```
```sh
git config --global user.email "micorreo@mail.com.mx"
```

**Mostrar el nombre de usuario y correo.**
```sh
git config --list
```

**Mostrar archivos donde están las configuraciones guardadas.**
```sh
git config --list --show-origin
```

**Comandos de configuraciones.**
```sh
git config
```

**Poner archivos en Stage.** 
Es como agregar archivos y prepararlos para hacer el `commit`
```sh
git add archivo.txt
```
```sh
git add .
```

**Cambia el estatus de agregado a cacheado, vuelve al estado inicial.**
--cached significa que está en la memoria ram.
```sh
git rm --cached archivo.txt
```

**Envía los cambios del archivo a la base de datos del control de versiones.**
```sh
git commit -m "Versión 1"
```

**Ver el estatus de la base de datos del control de versiones.**
```sh
git status
```

**Muestra los cambios históricos.**
```sh
git show
```

**Muestra toda la historia de un archivo.**
```sh
git log archivo.txt
```
El número largo que aparece es el nombre de esa modificación.

**Llevar el archivo a un servidor remoto, por ejemplo a github.**
```sh
git push
```

**Traer archivo de un servidor remoto.**
```sh
git pull
```

--- 

## Pasos para subir un proyecto local a github.

**En Github**

- Tener asociada mi key SSH publica.

- Crear un repositorio.

**En mi máquina local.**

- Ya debe de estar hecho el `commit`

- `git remote add origin git@github.com:nombre-usuario/nombre-de-proyecto.git`

- `git push -u origin master` o como se llame la rama.

- Para subir los próximos cambios solo será hacer `git push`

---

## Pasos para clonar un repositorio de Github a local.

**En Github**

- Tener asociada mi key SSH publica.

- Crear un repositorio.

**En mi máquina local**

- `git clone git@github.com:nombre-usuario/nombre-de-proyecto.git`

- Hacer cambios `git add .` --> `git commit -m "mensaje"`

- Y `git push` para subir los cambios hechos.