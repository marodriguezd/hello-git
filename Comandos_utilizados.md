# Placeholder para comandos y configuraciones de Git

---

## Instalación en Windows desde powershell con winget:

- `winget install --id Git.Git -e --source winget`: El comando necesario para instalar de una Git en Windows.

## Comandos básicos

Aquí puedes agregar los comandos básicos de Git que vayas aprendiendo:

- `git --version`: Muestra la versión instalada de Git.
- `git config --global user.name "marodriguezd"`: Para configurar el name del usuario del proyecto en el PC.
- `git config --global user.email "migueadali@gmail.com"`: Para configurar el email del usuario del proyecto en el PC.
- `git init`: Inicializa un nuevo repositorio Git.
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
