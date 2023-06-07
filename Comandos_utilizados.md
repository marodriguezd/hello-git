# Placeholder para comandos y configuraciones de Git

---

## Instalación en Windows desde powershell con winget:

- `winget install --id Git.Git -e --source winget`: El comando necesario para instalar de una Git en Windows.

## Configuración de Git

Comandos de configuración de Git por orden de aparición en el curso, previamente estar en la ruta del proyecto:

- `git config`: Es para establecer la configuración de git.
- `git config --global`: De esta forma establecemos la configuración a nivel global dentro del equipo.
- `git config --global user.name "NombreUsuario"`: De esta forma configuramos el nombre de usuario.
- `git config --global user.email "emailUsuario@host.com"`: De esta forma configuramos el email del usuario.

## "git init"

Comando de inicialización de Git en la ruta deseada:

- `git init`: Inicializa un nuevo repositorio Git en el directorio actual. Nos crea una ruta .git donde declara que todo está bien.

## Ramas en Git

Por defecto la rama principal se llama master, pero es recomendable cambiarla para quitar la connotación negativa:

- `git branch -m main`: Esto renombra la rama actual a "main".

## "git add" y "git commit"

Comandos para ir usando ya de forma básica Git:

- `git status`: Con esto podemos ver el estado actual de nuestro proyecto.
- `git add fichero.extensión`: Añade el archivo deseado al Git versionándolo.
- `git commit`: Es para lanzar la "fotografía" del estado, es decir actualizar todo lo que haya hasta ahora.
- `git commit -m "mensaje"`: Para pasarle directamente el mensaje deseado al commit.

## "git log" y "git status"

Comandos para ver los estados y registros del repositorio:

- `git log`: Muestra todos los commits hechos con mucha cantidad de datos.
- `git status`: Con esto podemos ver el estado actual de nuestro proyecto.

# "git checkout" y "git reset"

Comandos para gestionar y moverse por versiones:

- `git checkout`: Es para devolver la rama a una versión anterior o moverse entre diferentes ramas.
- `git checkout fichero.extension`: Es para devolver el archivo a su última versión comiteada.
- `git reset`: Para volver hacia atrás a la "última fotografía".
- `git log --graph --decorate --all --oneline`: Este comando muestra el historial de commits en una representación gráfica.

## "git alias"

Para facilitar el uso de comandos largos con un alias:

- `git config --global alias.nombre "comando"`: Ponerle el nombre deseado al alias y el comando entero.
- `git config --global alias.tree "log --graph --decorate --all --oneline"`: Este comando crea un alias global llamado "tree" que muestra el historial de commits en formato gráfico.

## Fichero .gitignore

- `touch .gitignore`: No es un comando nativo de Git. Sino que para crear el fichero y así rellenamos los ficheros que no queremos que sean vistos por el Git. La forma de rellenarlo es: **./nombreArchivoODirectorio.

## "git diff"

- `git diff`: Para comparar el último commit con los cambios efectuados hasta ahora.

## Desplazamiento en una rama

- `git checkout`: Para moverte entre ramas pero no guarda lo actual.
- `git checkout fichero.extensión`: Resetea el fichero a como estuviera en la rama anterior.
- `git checkout hash`: Permite moverte entre distintas ramas haciendo uso del hash.
- `git checkout main`: Nos mueve a la rama que establecimos como la cabeza del proyecto por ejemplo. Jugando un poco se entiende

### Si sufro de detached

1. Run `git branch tmp` - this will save your changes in a new branch called tmp.
2. Run `git checkout master`.
3. If you would like to incorporate the changes you made into master, run `git merge tmp` from the master branch. You should be on the master branch after running git checkout master.

## "git reset --hard" y "git reflog"

- `git reset --hard id`: Para cagadas gordas y hacer un rollback del copón poniendo el ID de a dónde queremos dirigirnos. Pudiendo volver a hacerse añadiendo el id deseado incluso si se ha borrado tras una cagada ese, haciendo uso del comando de abajo.
- `git reflog`: Nos muestra un log que es un historial completo de todo lo que se haya hecho.

## "git tag"

- `git tag etiqueta_asi_puesta`: Por ejemplo para etiquetar todos los commits hechos el mismo día.
- `git add .`: Añade al área de stage todo lo que haya pendiente.
- `git tag`: Nos muestra todos los tags creados en el repositorio.
- `git checkout tags/nombre_tag`: Nos mueve al commit con esa tag al igual que si usáramos cualquier otro id.

## "git branch" y "git switch"

- `git branch nombreRama`: Para crear una rama paralela
- `git switch nombreRama`: Para cambiarme entre la rama actual y la destino.

Lo que se hace en una rama se queda en esa rama, solo se comparte el punto de partida.

## "git merge"

- `git merge nombreRama`: Es para combinar las ramas/cambios para implementarlos juntos. Es mergear con la rama que queremos absorver.

## Resolución de conflictos en Git

- `git merge nombreRama`: En caso de cagarla duro desde el editor te deja elegir con cuál versión de los ficheros entre ramas te quieres quedar y puedes jugar con checkouts en caso de necesitar recuperar cosas o lo que sea mergeando luego en la rama principal, aunque tengas que copiar, pegar fuera y reinsertar en el peor de los casos.

## "git stash"

- `git stash`: Para almacenar temporalmente de cara a cambiarnos entre ramas sin hacer un commit, ya que este solo debe hacerse de código que funciona.
- `git stash list`: Me muestra la lista de los stash existentes en todo el proyecto, independientemente del branch en el que estés. 
- `git stash pop`: Recupera todo lo que esté guardado en el stash. 
- `git stash drop`: En caso de querer eliminar el stash guardado porque realmente no nos interese.

## Configuraciones

Puedes añadir aquí las configuraciones de Git que quieras recordar:

[filter "lfs"]
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process
	required = true
[user]
	name = marodriguezd
	email = migueadali@gmail.com
[alias]
	tree = log --graph --decorate --all --oneline
