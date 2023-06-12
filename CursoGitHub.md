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

Si no existe un fichero de configuración habría que crearlo:
- `touch config`: Para crearlo en el directorio y rellenarlo con: Host *.github.com
	AddKeysToAgent yes
	IdentityFile ~/.ssh/id_rsa
- `ssh-add 'C:\Users\tu_usuario\.ssh\id_rsa'`: Para añadir la clave al ssh agent.

Conexión con GitHub:
Vamos a settings dentro de nuestro perfil, nos vamos a SSH y GPG keys, creamos una clave nueva ssh, abrimos nuestra clave .pub con editor de texto, copiamos su contenido y lo añadimos al creador de GitHub, 

Ahora probamos la conexión con GitHub:
- `ssh -T git@github.com`: Lo ponemos en la terminal y yes a lo que salga.

## Repositorio proyecto

Vamos a crear en nuestro GitHub un repositorio con el mismo que tengamos en local

## Git remote

- `git remote add origin https://github.com/tu_usuario/hello-git.git`: Lanzamos esto en la ruta del proyecto. Emparejando nuestro local al público.
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
- `git clone git@github.com:tu_usuario/hello-git.git`: Haciéndolo de esta forma nos crearía una carpeta con el mismo nombre del repositorio.

## "git push"

- `git push`: Tras haber sincronizado todo en local con el git pull, etc. Para subirlo al repo. Si todo está ya bien sincronizado subirá sin problemas

## "Fork" en GitHub

Por ejemplo es clonando un repositorio que ya existe usándolo de base, trabajar encima de este añadiéndolo a un repositorio idéntico en nuestro GitHub. En resumen es un clon del repositorio original pero en nuestro repositorio. Pudiendo copiar todos los branchs que deseemos. El forkeo se hace desde el propio GitHub. Y es de este fork del que debemos hacer el git clone.

- `git clone git@github.com:tu_usuario/hello-git-mouredev.git`: Aquí estamos haciendo de ejemplo que hemos forkeado el hello-git de mouredev a nuestro perfil/repo de GitHub, y es ese mismo el que hemos clonado en local.

## Flujo colaborativo en GitHub

Ahora vamos a hacer modificaciones en el fork de mouredev por ejemplo:

- `cd .\Desktop\hello-git-mouredev\`: Con esto accederíamos a nuestra ruta en local donde se encuentra el fork.
Aquí vamos a crear y modificar un md:
- `touch hello.md`: Con esto lo creamos.
Lo hemos rellenado con un texto y nuestro usuario de GitHub para darle un añadido y diferenciarlo. Commiteando y pusheando todo.
Desde GitHub nos deja sincronizar el fork con el original por si el dueño legítimo añade modificaciones. Esta sincronización es como una especie de merge entre usuarios distintos.

## "Pull Request (PR)" en GitHub

Desde GitHub, en nuestro fork podemos hacer una Pull Request, dando en Contribute y open pull request. Hemos hecho el envío del PR poniendo título y texto.
El que recibe el PR puede hacer review de los cambios commentando, aprobando o pidiendo cambios. Siendo el base approve con un comentario.
Debiendo luego la persona que mantiene el repositorio hacer merge al pull request. Primero lo aprueba y acepta y luego hace el merge para añadir las modificaciones al repositorio original.

## Resolución de conlfictos en Pull Request

La recomendación es solucionar todas estas cosas usando siempre GitHub ya que es su forma nativa e intuitiva. Pero solo a nivel de Pull Request, etc. El resto perfectamente lo podemos hacer por terminal de comandos como hasta ahora.
Una vez resuelto el conflicto de la Pull Request en GitHub hay que commitear el merge. Y luego mergear el pull request una vez solucionado el conflicto.
Esto es bastante importante.

## Sincronización de un Fork en GitHub

Desde el propio GitHub puedes sincronizar el fork comparando para ver lo cambios y en qué te afectaría o actualizando el branch directamente.

## Markdown en GitHub

Vital tanto para la página de presentación de GitHub (la cual ya tengo bien pana) o como documentaciones.

## Herramientas gráficas (GUI) para Git y GitHub

Seguir [esta guía](https://youtu.be/3GymExBkKjE?t=14437).

[GitHub Desktop](https://desktop.github.com)
Simplemente te permite de manera sencilla y visual ver todos los commits, repos, etc. 

De cara a commitear o no los cambios se pueden checkear los ficheros que detecta automáticamente con las modificaciones.
Pero se queda bastante limitada en usabilidad, habiendo mejores alternativas.

[GitKraken](https://www.gitkraken.com)
Es una herramienta mucho más profesional y que utilizan más empresas. Siendo muchísisimo más potente y se ve claramente en todo lo que te sale de primeras en la interfaz. Pero para trabajar con datos públicos va bien, pero con privados hay que pagar.

[SourceTree](https://www.sourcetreeapp.com)
Este nos permite trabajar con repositorios públicos y privados totalmente gratis, siendo la mejor alternativa de cara a no invertir dinero pero tener una gran potencia de uso hasta ahora.

[GitFork](https://git-fork.com)
Siendo esta otra herramienta muy buena también. Pero por lo que he visto tiene opciones de pago, siendo el más recomendado por la comunidad respecto a SourceTree. Pero SourceTree es 100% gratuito.

## Git y GitHub "flow"

[GitFlow](https://www.atlassian.com/es/git/tutorials/comparing-workflows/gitflow-workflow)
Recomendable ver todas estas explicaciones de esta página directamente, ya que es de donde está saliendo la siguiente información junto al curso.

Los flujos de trabajo son para cuando por ejemplo hay desarrollos en varias ramas pero hay un fallo en producción, poder arreglar eso y entiendo que propagar el parche al resto. Pero sea como fuere lo recomendable es siempre seguir cierto orden.

Digamos que la rama develop es la que debería poder llegar a producción y la rama main la que versiona. Depositando en develop solamente aquello que sepamos que funciona al 100% y siendo main la que va gestionando las versiones. Teniendo main solamente los puntos en los que se considera una versión "estable" la de develop, siendo la foto que se sube a producción, la de develop en main.

- `main`: Solo para lo que pasa a producción y taggear.
- `develop`: Donde se va volcando todo lo que se va haciendo en el proyecto. Y lo que está aquí es lo que puede pasar a producción.
Pero el proyecto como tal se va evolucionando en ramas feature. Es decir que cada implementación N debe ser una rama que nazca de develop y que esté centrada en una función solo, para poder permitir que existan tantas ramas como hagan falta; cerrando su ciclo volviendo a mergearse con develop. Las únicas ramas que nunca se cierran son main y develop. Aunque podamos hacer esto con branches y el uso aprendido hasta ahora con Git, usar Git Flow ofrece ventajas de mayores complejidades. Permitiendo por ejemplo que él solo te pase la rama a develop e incluso la cierre llegado el caso.

- `release`: Este es otra rama que nace de develop pero de cara a main, donde hacemos lo necesario ya de cara a pasarla a producción. Estando diseñada de tal forma que en el momento que la cerremos va a volcarse sobre la rama main creando un tag sobre esta y se cierra sobre la rama develop.

- `hotfix`: Es una rama especial que se abre a partir de la rama main solo en caso de necesitar resolver un problema rápido y sin tener que depender de nada más. Porque así solucionamos el error justamente en la parte que está pegando el petardeo en producción. Y cuando lo cerramos Git Flow nos lo pasa directamente a main creando su tag y develop. Esto último para propagarlo al resto de ramas y versiones.

## Ejemplo Gitflow

[Instalación de GitFlow en Windows](https://gist.github.com/geedelur/3208244)
Dará un error a la hora de hacer el clone, antes de ello:
- `git config --global url.https://github.com/.insteadOf git://github.com/`: Con esto se arregla el error y conecta fino.
Luego simplemente siguiendo lo que dice el gist va todo fino, siendo sí o sí cmd en admin para lo último.

- `git flow init`: Ponemos esto en la ruta donde tenemos el Git, para simplemente arrancarlo dejando todo por defecto.
De ejemplo vamos a crear un flow sobre la feature de prueba que vamos a implementar.
- `git flow start feature 2auth`: El 2auth es un ejemplo de cómo vamos a llamar a la implementación.