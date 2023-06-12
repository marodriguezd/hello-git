# Comandos y configuraciones de GitHub

---

## Primeros pasos en GitHub

Lo primero que deberíamos hacer en GitHub es configurarlo como "red social para desarrolladores" creando nuestro propio repositorio personal main con nuestro mismo nombre y un readme.md bien pana mi fino.

## Local y remoto

Es básicamente como el Git en local pero sincronizado en la nube dando mayor seguridad y consistencia

## Autenticación SSH en GitHub

Para hacer la conexión `https://docs.github.com/es/authentication/connecting-to-github-with-ssh/using-ssh-agent-forwarding`
En sí SSH es un protocolo de autenticación basado en una clave privada.

La buena práctica para tener las claves es en un directorio llamado SSH.
Para irla creando desde cero `https://docs.github.com/es/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent`

- `ssh-keygen -t ed25519-sk -C "YOUR_EMAIL"`: Para crear la clave.

Lo suyo es:
- `C:\Users\TU_USUARIO\.ssh`: Ir o crear esta ruta
- `ssh-keygen -t ed25519 -C "TU_CORREO@SERVICIO_HOST.TERMINACIÓN"`: Con esto creamos las credenciales públicas y privadas.
  
- `eval "$(ssh-agent -s)"`: Para iniciar el agente ssh en segundo plano.
Si falla:
- `Get-Service ssh-agent | Select StartType`: Si esto sale Disabled.
- `Get-Service -Name ssh-agent | Set-Service -StartupType Manual`: Poner esto como administrador.
- `ssh-agent -s`: Si esto no muestra nada:
- 

Si no existe un fichero de configuración habría que crearlo:
- `touch config`: Para crearlo en el directorio y rellenarlo con: Host *.github.com
	AddKeysToAgent yes
	IdentityFile ~/.ssh/id_rsa
- `ssh-add 'C:\Users\Miguel Angel\.ssh\id_rsa'`: Para añadir la clave al ssh agent.

Conexión con GitHub:
Vamos a settings dentro de nuestro perfil, nos vamos a SSH y GPG keys, creamos una clave nueva ssh, abrimos nuestra clave .pub con editor de texto, copiamos su contenido y lo añadimos al creador de GitHub, 

Ahora probamos la conexión con GitHub:
- `ssh -T git@github.com`: Lo ponemos en la terminal y yes a lo que salga.

## Repositorio proyecto

Vamos a crear en nuestro GitHub un repositorio con el mismo que tengamos en local

## Git remote

- `git remote add origin https://github.com/marodriguezd/hello-git.git`: Lanzamos esto en la ruta del proyecto. Emparejando nuestro local al público.
- `git push`: Para hacer la subida del local a la nube pero.
- `git push origin`: Ya que donde nos encontramos es el origen ahora mismo, el punto final del repositorio. Pero como hemos hecho bien y llamada a la rama principal main. El comando completo recomendado es:
- `git push -u origin main`: Para subir todo al repositorio de GitHub. Aceptamos si nos pide autorizar la primera vez desde el navegador por ejemplo con la cuenta de GitHub.

## Subida de un proyecto a GitHub

Podemos crearle un readme básico por si alguien más trabaja con ello. Tomando de ejemplo que este lo haya subido el otro desarrollador.
Y nosotros seguimos modificando en nuestro local.
Guardamos las cosas como siempre en local con sus commits y cosas para luego hacer el push. Además todos los commits que hayamos hecho en local se sincronizarán en GitHub.
- `git push`: Esto dará un pete ya que ha sido modificada la pública y no lo tenemos en la local. Si no hay modificaciones irá de una porque ya está conectada.

## "git fetch" y "git pull"

- `git fetch`: Se descarga el historial de cambios pero sin descargarse los cambios. Pudiendo ver así los problemas.
- `git pull`: Se descarga el historial y los cambios. Si no tienes ramas adicionales no daría ningún problema aparentemente.
Por si acaso podemos poner que por defecto lo que deseamos si hay algún problema más allá es hacer un merge.
- `git config pull.rebase false`: Para cambiar la acción por defecto

### Hasta aquí podemos trabajar con el local y hasta cierto punto con el público

## "git clone"

Útil por ejemplo para añadir un nuevo miembro al equipo y que se baje todo lo que haya en el repositorio o ir a otro ordenador. Siendo recomendable bajarlo por SSH. Por ejemplo siendo

- `cd Desktop`: Para ir al Escritorio desde la terminal.
- `git clone url`: Para clonar el repositorio ahí directamente, usando de ejemplo.
- `git clone git@github.com:marodriguezd/hello-git.git`: Haciéndolo de esta forma nos crearía una carpeta con el mismo nombre del repositorio.

## "git push"

- `git push`: Tras haber sincronizado todo en local con el git pull, etc. Para subirlo al repo