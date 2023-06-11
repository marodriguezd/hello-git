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

- `git remote add origin https://github.com/marodriguezd/hello-git.git`: Lanzamos esto en la ruta del proyecto.