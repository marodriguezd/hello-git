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
- `git checkout HEAD`: Nos mueve a la rama que establecimos como la cabeza del proyecto por ejemplo.

### Si sufro de detached

1. Run `git branch tmp` - this will save your changes in a new branch called tmp.
2. Run `git checkout master`.
3. If you would like to incorporate the changes you made into master, run `git merge tmp` from the master branch. You should be on the master branch after running git checkout master.

- `git branch -m main`: Este comando cambiará el nombre de la rama actual a "main".
- `git commit -m "mensaje"`: El "mensaje" es lo que queremos que describa al commit que vamos a mandar.
- `git add ./<archivo>.<tipo>`: Agrega el archivo "./<arhivo>.<tipo>" ó "./<carpeta>/" al área de preparación.
- `git checkout .\<archivo>.<tipo>`: Este comando deshace los cambios realizados en el archivo "./<arhivo>.<tipo>" y lo restaura a su estado anterior en el repositorio. También se puede usar el hash, o nombre como HEAD o main, o acorte final del hash.
- `git reset`: Este comando se utiliza para deshacer cambios en el historial de commits en Git.
- `git log --graph --decorate --all --oneline`: Este comando muestra el historial de commits en una representación gráfica.
- `git config --global alias.tree "log --graph --decorate --all --oneline"`: Este comando crea un alias global llamado "tree" que muestra el historial de commits en formato gráfico.
- `git diff`: Este comando muestra las diferencias entre los cambios sin confirmar en el área de preparación y la versión actual de los archivos en el directorio de trabajo.
- `git status`: Este comando muestra el estado actual del repositorio de Git.
- `git tree`: No es un comando nativo de Git. `git config --global alias.tree "log --graph --decorate --all --oneline"`

- `git clone [url]`: Clona un repositorio existente en tu máquina local.
- `git add [archivo]`: Agrega un archivo específico al área de preparación.
- `git commit -m "mensaje"`: Realiza un commit con un mensaje descriptivo.

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
