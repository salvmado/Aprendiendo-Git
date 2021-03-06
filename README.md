# Git básico.

<br/>

## Instalación de git en debian.
```sh
:~# apt install git
```

**Ver la versión que tengo instalada.**
```sh
git --version
```

**Ver todos los comandos de git.**
```sh
git
```

---

<br/>

## Comandos básicos de git. 

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

Es para que otras personas vean quien hizo el cambio en el repositorio.
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
git add <archivo>
```
o para agregar varios archivos al mismo tiempo.
```sh
git add .
```

<br/>

---

<br/>

**Saco archivos del staging, no borra nada.**

Y cuando lo necesite para hacer `commit` lo puedo agregar nuevamente con `add`
```sh 
git reset HEAD
```

**Elimina el archivo que está en staging y del repositorio local.**

--cached significa que está en la memoria ram. Si me equivoco al hacer `add` me puedo regresar, el archivo quedará untracked.
```sh
git rm --cached <archivo>
```  

<br/>

---

<br/>

**Envía los cambios del archivo a la base de datos del control de versiones (repositorio local).**

El mensaje entre comillas es para hacer un comentario corto del cambio que se hizo.

Cada `commit` es una versión diferente de mi archivo.
```sh
git commit -m "Versión 1"
```
Una vez que hice `add` una vez, la próxima lo puedo omitir y hacer directamente el `commit` con el flag `-a`.
```sh
git commit -am "Versión 1"
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

La cadena alfanumérica que aparece es el nombre de una modificación (de un `commit`). 
También aparece autor y fecha exacta.
```sh
git log <archivo>
```
```sh
git log
```
Se ven los cambios de una forma más completa.
```sh
git log --stat <archivo>
```

<br/>

---

<br/>

**Comparar dos modificaciones que se hicieron.**

```sh
git diff  cadena-alfanumérica-es-el-nombre-del-commit cadena-alfanumérica-es-el-nombre-del-commit
```

<br/>

---

<br/>

**Guardar una actualización en el repositorio remoto, por ejemplo, en github.**
```sh
git push
```

<br/>

---

<br/>

**Traer archivo de un repositorio remoto.**

por ejemplo: si alguien más hizo una actualización, entonces yo la puedo traer a mi computadora 
o si yo hago una actualización directa en github, también actualizo mi archivo local con este comando:
```sh
git pull
```

<br/>

---

<br/>

**Puedo regresar en la historia y revisar un `commit`.**
```sh 
git checkout cadena-alfanumérica-es-el-nombre-del-commit <archivo>
```
Y ya que lo revisé, regreso a mi versión actual con:
```sh 
git checkout master <archivo>
```

**Regresar a cambios anteriores, sin borrar nada de historia en git.**
```sh 
git checkout cadena-alfanumérica-es-el-nombre-del-commit <archivo>
```
El `checkout` deja en staging el archivo, solo tengo que hacer `commit` para traerlo de nuevo.  
```sh 
git commit -m "Regreso a la versión anterior"
```

<br/>

---

<br/>

`**¡Precaución!**`

**Volver a una versión anterior, pero puedo borrar todo lo que hice antes.**

Vuelve a la versión anterior que yo quiera y deja en staging el contenido actual, solo tengo que hacer `commit` para actualizarlo. Lo malo es que borra la historia en git.
```sh 
git reset cadena-alfanumérica-es-el-nombre-del-commit --soft
```

De esta forma todo vuelve a la versión anterior que yo quiera, pero borra todo y no hay vuelta atrás.
```sh 
git reset cadena-alfanumérica-es-el-nombre-del-commit --hard
```

**Elimina los archivos de git y de mi disco duro.**

```sh
git rm --force <archivo>
``` 
Intenté recuperar el archivo borrado. reviso con `git status` y parece que el archivo está en staging, lo que hice es crear un archivo con el mismo nombre que borré y después usé este comando:
```sh 
git restore --staged <archivo>
```
Reviso el `git log` y regreso en la última versión con este comando. 
```sh 
git reset cadena-alfanumérica-es-el-nombre-del-commit --hard
```
Checo el `log` y sigo teniendo toda mi historia de git, aparte el archivo está con todos mis datos.

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

- Tener asociada mi key SSH publica, para después poder hacer cambios.

**En mi máquina local**

- `git clone git@github.com:nombre-usuario/nombre-de-proyecto.git`

- Hacer cambios `git add .` --> `git commit -m "mensaje"`

- Y `git push` para subir cambios hechos.

<br/>

---

<br/>

**Lo básico lo entiendo así:**

Para guardar en mi repositorio local y remoto.
| Mi directorio | Preparación o staging | Repositorio local | Repositorio remoto |
| ------------- | ----------------------| ----------------- | ------------------ |
| `Desarrollo` --> | `git add` --> | `git commit` --> | `git push` |

Y si quiero traer actualizaciones de un repositorio remoto.
| Mi directorio | Preparación o staging | Repositorio local | Repositorio remoto |
| ------------- | ----------------------| ----------------- | ------------------ |
| `Desarrollo` --> |                    | `git pull`        |                    |

<br/>

---

<br/>


## Trabajando con ramas.

**Cómo creo una nueva rama**

```sh 
git  branch <nombre-rama>
``` 
Cuando escribo el comando `git status` me doy cuenta de que el `HEAD` es el último `commit` de la rama master.

Ahora tengo que moverme a la nueva rama y para regresar es con el mismo comando, solo cambiaré a master.
```sh 
git  checkout <nombre-rama>
``` 
`git status` y ahora el `HEAD` ya está en `<nombre-rama>`. 

Ya puedo hacer cambios, pero tengo que hacer `commit` antes de cambiar de rama, si no lo hago se perdería todo el avance.

**Cómo saber cuántas ramas tengo, su nombre y en cuál estoy situado.**
```sh 
git  branch
``` 
**Unir la rama creada a la principal**

Tengo que estar en la rama que quiero que sea la principal, por ejemplo, la master.
```sh 
git  merge <nombre-rama>
``` 
Y con esto los cambios hechos en `<nombre-rama>` ya estarán unidos a la master. Si quiero podré deshacerme de la rama y hacer otra para más cambios futuros.