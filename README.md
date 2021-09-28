# Git básico.

<br/>

## Instalación de git en debian.
```sh
:~# apt install git
```

**Para saber la versión que tengo instalada.**
```sh
git --version
```

**Para ver todos los comandos de git.**
```sh
git
```

<br/>

## Comandos de git. 

<br/>  


**Comenzar un repositorio.**  

En la terminal entro al directorio en el que quiero hacer el control de versiones y pongo este comando.
```sh
git init
```

<br/>  

---

<br/>

**Poner mis datos de usuario.**

Es para que otras personas sepan quien hizo el cambio.
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

<br/>

---

<br/>

**Mostrar archivos donde están las configuraciones guardadas.**
```sh
git config --list --show-origin
```

**Comandos para configuraciones.**
```sh
git config
```

<br/>

---

<br/>

**Poner archivos en Staging.** 

Es como agregar archivos y prepararlos para después hacer `commit`.
Antes de hacer `add` es untracked y con `add` ya es tracked
```sh
git add archivo.txt
```
o para agregar varios archivos al mismo tiempo.
```sh
git add .
```

**Cambia el estatus de agregado a cacheado, vuelve al estado inicial.**

--cached significa que está en la memoria ram. Si me equivoco al hacer `add` me puedo regresar.
```sh
git rm --cached archivo.txt
```

<br/>

---

<br/>

**Envía los cambios del archivo a la base de datos del control de versiones (repositorio).**

El mensaje entre comillas es para hacer un comentario corto del cambio que se hizo.

Cada `commit` es una versión diferente de mi archivo.
```sh
git commit -m "Versión 1"
```

<br/>

---

<br/>

**Ver el estatus de la base de datos del control de versiones.**
```sh
git status
```

<br/>

---

<br/>

**Muestra los cambios históricos.**
```sh
git show
```

<br/>

---

<br/>

**Muestra toda la historia de un archivo.**

La cadena alfanumerica que aparece es el nombre de una modificación (de un `commit`).
```sh
git log archivo.txt
```
```sh
git log
```
Se ven los cambios de una forma más completa.
```sh
git log --stat
```

<br/>

---

<br/>

**Comparar dos modificaciones que se hicieron.**

```sh
git diff  cadena-alfanumerica-nombre-del-commit cadena-alfanumerica-nombre-del-commit
```
O solo poner `git diff` y hará la comparación en el tiempo del archivo.
```sh
git diff 
```

<br/>

---

<br/>

**Guardar una actualización en el servidor remoto, por ejemplo en github.**
```sh
git push
```

<br/>

---

<br/>

**Traer archivo de un servidor remoto.**

Por ejemplo: si alguién más hizo una actualización, entonces yo la puedo traer a mi computadora 
o si yo hago una actualización directa en github, también actualizo mi archivo local con este comando:
```sh
git pull
```

<br/>

---

<br/>

**Regresar a cambios anteriores, sin borrar nada de historia.**

Elijo la versión y si hago `commit` de esta modificación **borraré todo lo que hice antes**.
```sh 
git checkout cadena-alfanumerica-nombre-del-commit archivo.txt
```
Si aún no he hecho `commit` puedo regresar a como estaba antes del `checkout`
```sh 
git checkout master archivo.txt
```
**Lo correcto sería hacer** `checkout`, después hacer los cambios en el archivo, hacer `add` --> `commit` y con esto envío esa actualización a la rama principal, pero sin perder nada de historia.

<br/>

---

<br/>

**Volver a una versión anterior, esto borra todo lo que hice antes, ¡Precaución!.**

De esta forma todo vuelve a la versión anterior.
```sh 
git reset cadena-alfanumerica-nombre-del-commit --hard
```
También vuelve a la versión anterior, pero si tenemos algo en staging ahí se sigue quedando, disponible para hacer el `commit`.
```sh 
git reset cadena-alfanumerica-nombre-del-commit --soft
```

<br/>

---

<br/>

##  Cómo subir un proyecto local a github.

**En Github**

- Tener asociada mi key SSH publica.

- Crear un repositorio.

**En mi máquina local.**

- Ya debe de estar hecho el `commit`

- `git remote add origin git@github.com:nombre-usuario/nombre-de-proyecto.git`

- `git push -u origin master` o como se llame la rama.

- Para subir los próximos cambios solo será hacer `git push`

<br/>

---

<br/>

## Cómo clonar un repositorio de github.

**En Github**

- Tener asociada mi key SSH publica.

- Crear un repositorio.

**En mi máquina local**

- `git clone git@github.com:nombre-usuario/nombre-de-proyecto.git`

- Hacer cambios `git add .` --> `git commit -m "mensaje"`

- Y `git push` para subir cambios hechos.

<br/>

---

<br/>



