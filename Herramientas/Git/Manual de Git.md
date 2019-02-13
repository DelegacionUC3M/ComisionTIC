# Manual de Git

## Aspectos Básicos

### Instalando Git

Git viene instalado en la mayoría de distribuciones por defecto. En caso de no estar instalada, siempre puedes hacerlo mediante el gestor de paquetes:

```bash
$ sudo pacman -S git
$ sudo apt install git-all
$ sudo dnf install git-all
$ sudo yum install git
```

### Configurando Git

Lo primero que necesitamos hacer es configurar nuestro usuario y contraseña para poder comenzar a trabajar con Git:

```bash
$ git config --global user.name "Usuario"
$ git config --global user.email correo@ejemplo.com
```

De esta manera, cualquier usuario sabe quien ha hecho cada cosa en cada proyecto y nos permite mantener cierto orden a la hora de trabajar en equipo.

### Crear Un Repositorio

Git guarda toda la información relativa al proyecto en una carpeta *.git* directamente en el proyecto.

Para iniciar un repositorio deberemos ir a la carpeta de nuestro proyecto e introducir las siguientes instrucciones:

```bash
$ cd /ruta/al/proyecto/
$ git init
```

Lo que nos devolverá el siguiente texto:

```bash
Initialized empty Git repository in /ruta/al/proyecto/.git/
```

La carpeta *.git* ha sido creada satisfactoriamente dentro del proyecto, lo que permitirá a Git de ahora en adelante almacenar el histórico de commits y la configuración del proyecto.

### Comprobando El Estado

`git status` es quizás el comando mas importante de git, dado que nos devuelve información relevante al estado del repositorio.

Si creamos un archivo `hola.txt` en el proyecto, al ejecutar dicho comando veremos esto:

```bash
$ git status

On branch master

Initial commit

Untracked files:
  (use "git add ..." to include in what will be committed)

    hola.txt
```

Este mensaje nos indica que el archivo hola.txt no esta siendo siendo seguido, también conocido como “untracked”. Esto significa que Git aun no esta siguiendo los posibles cambios de dicho archivo.

> Podemos ignorar los archivos o directorios que queremos mediante el archivo **.gitignore**.
>

Para poder guardar en el histórico los cambios de los archivos necesitamos pasar a la siguiente etapa, el `staging` 

### Staging

La siguiente etapa en el proceso de control de versiones es lo que se conoce como *“staging”*.

Los archivos que están en esta etapa, solo mantienen los cambios de los cuales nos gustaría hacer un *commit*.  Los archivos en el *“staging area”* aun están sujetos a cambios, por lo que es recomendable añadir juntos todos aquellos archivos de los cuales queremos crear un único commit.

Para añadir un solo archivo:

```bash
$ git add archivo
```

Si queremos añadir todo el contenido de un directorio:

```bash
$ git add -A
```

Comprobando el estado de nuestro proyecto ahora debería de devolver esto:

```bash
$ git status

On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached ..." to unstage)

    new file:   hola.txt
```

Dependiendo de los cambios que hayamos realizado, Git nos avisara si hemos añadido algún archivo o si hemos eliminado archivos que formaban parte del proyecto.

Vemos que Git nos avisa que nuestro archivo esta listo para la siguiente etapa, el `commit`.

### Creando Un Commit

La idea de un commit es representar los cambios de nuestro repositorio en cualquier punto. Mediante el histórico de commits, se puede regresar a una versión anterior del proyecto en cualquier momento.

Una vez tengamos los archivos que queremos en el “staging area”, ejecutaremos el siguiente comando, el cual creara un commit con los cambios que muestra el “staging area”:

```bash
$ git commit -m "Commit inicial."
```

> La idea de un commit es ser un mensaje conciso que represente a grandes rasgos el estado del proyecto en un instante. Es por eso que se escriben los commits con el parámetro `-m`.

Ademas de esto, es recomendable juntar en un solo commit pequemos cambios relacionados entre si. A medida que nuestro proyecto crezca, nos sera mucho mas fácil gestionar un histórico grande, pero ordenado en cuanto a cambios se refiere, que un histórico pequeño donde los cambios no tienen ningún tipo de cohesión.

## Repositorios

Hasta ahora, somos capaces de gestionar los cambios en nuestro proyecto, pero estos cambios son solo locales. 

Ahora daremos el salto a la nube para poder compartir nuestro proyecto con el resto del mundo.

### Conectarse a un repositorio

Para poder subir los cambios de nuestro repositorio local a un repositorio en la nube es necesario establecer una conexión entre ambos. 

Utilizaremos como ejemplo de repositorio online: *https://github.com/usuario/proyecto.git*

Para establecer el link entre el repositorio local y el online utilizaremos el comando `git remote`.

```bash
$ git remote add origin https://github.com/usuario/proyecto.git
```

> Un proyecto puede tener varios repositorios al mismo tiempo. Para poder diferenciarlos es necesario darles distintos nombres. 
>
> El repositorio principal se llama **origin.**

### Subir al servidor

Ya estamos preparados para subir nuestros commits al repositorio, lo que se conoce como **hacer push**. Es necesario hacer push cada vez que queremos subir los cambios al repositorio.

El comando para subir los cambios es `git push`. Este comando necesita dos parámetros:

1. **Repositorio** al que queremos subir los cambios. Suele ser **origin**.
2. **Rama** a la que queremos subir los cambios.  La rama principal para cualquier repositorio es **master**.

```bash
$ git push origin master

Counting objects: 3, done.
Writing objects: 100% (3/3), 212 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/usuario/proyecto.git
 * [new branch]      master -> master
```

> Una vez introducido el comando, necesitaremos identificarnos con nuestro usuario y contraseña.

### Clonar un repositorio

Ahora cualquiera puede ver tu repositorio en la nube. Para que puedan descargarse tu proyecto es necesario **clonarlo**, lo cual se realiza mediante el comando `git clone`.

```bash
$ git clone https://github.com/usuario/proyecto.git
```

> El repositorio local se ha creado automáticamente con el repositorio online configurado.

### Obtener nuevos cambios

Para obtener la ultima versión del proyecto solo tenemos que ejecutar un comando, **pull**:

```bash
$ git pull origin master

From https://github.com/usuario/proyecto
 * branch            master     -> FETCH_HEAD
Already up-to-date.
```

> Si no se han realizado cambios desde el ultimo commit, no se hace nada durante el pull

## Ramas

A medida que nuestro proyecto crece, es conveniente separar las distintas funcionalidades del mismo en lo que se conocen como *ramas*.

Cada rama mantiene su propio histórico, lo cual nos permite mantener cambios que no afecten a otras ramas hasta que las unamos.

### Creación de ramas

La rama por defecto en cualquier repositorio se conoce como **master**.

Para crear una rama nueva solo tenemos que introducir `git branch <rama>`:

```bash
$ git branch nueva_rama
```

La rama que se ha creado es exactamente igual a *master*

### Cambio de ramas

Si introducimos `git branch` cuando tenemos mas de una rama obtenemos esto:

```bash
$ git branch
  nueva_rama
* master
```

La rama marcada con el asterisco es la rama en la que nos encontramos actualmente.

Para cambiar a la otra rama, deberemos de introducir `git checkout`.

```bash
$ git checkout nueva_rama
```

> Podemos crear una rama y cambiar a esta automáticamente con el comando:
>
> `git checkout -b <rama>`

### Uniendo ramas

Una vez queramos guardar nuestro progreso en nuestra nueva rama, bastara con hacer lo mismo que se he hemos hecho en master.

```bash
$ git add nuevo_archivo.txt
$ git commit -m "Archivo nuevo finalizado"
```

Para volver ahora a la rama master:

```bash
$ git checkout master
```

Si observamos el proyecto, podremos ver que el archivo *nuevo_archivo.txt* ha desaparecido sin dejar rastro.

Como se ha mencionado antes, cada rama mantiene su propio histórico de cambios, por lo que necesitamos traer los cambios de nuestra rama a master. Esto es lo que se conoce como **merging.**

Para traer los cambios de una rama a otra, en nuestro caso de *nueva_rama* a *master*, deberemos de hacerlo mediante `git merge`.

```bash
$ git merge nueva_rama  # Estando en la rama master
```

Si no necesitamos más nuestra rama podemos eliminarla de la siguiente manera:

```bash
$ git branch -d nueva_rama
```

## Referencias

[Página Oficial](https://git-scm.com/)

[Manual Completo](https://tutorialzine.com/2016/06/learn-git-in-30-minutes)

[Lista De Manuales y Guias](https://try.github.io/)

[Workflow De Control de Software](https://www.git-tower.com/learn/cheat-sheets/vcs-workflow)