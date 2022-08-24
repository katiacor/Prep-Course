# :chopsticks: Uso de Git

## :cactus: Version Control System
Un sistema de control de versiones registra los cambios realizados en uno o más archivos, permitiendo retroceder a versiones anteriores. También te permite comparar cambios y ver quién realizó una modificación que puede estar causando un conflicto. Te permite recuperar facilmente archivos que has perdido.

### Locales
Copiar los archivos a otro directorio (con fecha y hora de creación) es una forma común de controlar versiones, pero es propensa a errores. Es ideal para trabajar solos, pero no para trabajar en equipo.

### Centralizados
Los CVCSs (Centralized Version Control Systems) tienen un único servidor que contiene todos los archivos versionados. Ha sido el estándar.  

Ventajas:
- Todos saben en qué están trabajando los demás usuarios.
- Los administradores tienen control sobre las acciones que pueden realizar cada usuario.

Desventajas:
- Si el servidor se cae, nadie puede continuar su trabajo ni rastrear cambios.
- Si el servidor se cae, se pierde todo el trabajo.

### Distribuido
En un DVCs (Distributed Version Control System), los clientes se sincronizan descargando la última versión de los archivos y replican completamente el repositorio. Si una persona hizo cambios en un archivo que nadie más ha modificado, entonces no existe conflicto y es posible fusionar los cambios.

Ventaja:
- Si un servidor muere, y había colaboradores, otro repositorio puede copiarse en el servidor y restaurar.

## :church: Git
Surge después de que BitKeeper deja de ser gratuito. La comunidad de Linux y Linux Torvalds deciden desarrollar su propia herramienta. Git nace en 2005.  

Características:
- Velocidad
- Diseño sencillo
- Completamente distribuido
- Capacidad para grandes proyectos
- Sistema de ramificación (branching/sistema no lineal)

Git != GitHub. Git es una herramienta que se instala en la maquina local.

### Usage:
- `git init` - Inicializa un repositorio en el directorio actual. Con `ls -a` confirmas la creación de la carpeta oculta `.git`.  
- `git status` - Muestra el estado actual de tu repositorio con respecto a la base de datos local.  
- `git add <filename>` - Los archivos son staged y están listos para ser confirmados. Las opciones `.` y `--all` agrega todos los archivos modificados, y deben ser usadas con precaución.  
- `git reset HEAD` - Devuelve los archivos 'staged' a su estado anterior (unstaged o untracked, según el caso).
- `git commit -m "mensaje"` - Confirmas y almacenas en la base de datos local. El mensaje describe brevemente los cambios que se realizaron.  
- `git rm <option>` - `<--cached>` para mover archivos a untracked; `<--force>` para eliminar archivos git del disco duro.
- `git push origin <branch>`  
- `git restore`  
- `git log` - Muestra id de los commits.
- `git show` - Muestra cambios realizados en un archivo a través del tiempo. Permite identificar la modificación que causó un error.
- `git diff <commitA> <commitB>` - Muestra la diferencia entre dos versiones del mismo archivo.
- `git pull`  
- `git clone <url>`  
- `git fetch`  
- `git checkout <commit_id>` - Permite volver a una versión anterior de un archivo o del proyecto.
- `git log --stat` - Muestra el commit descriptivo con número de líneas agregadas y removidas en un archivo.
- `git reset --soft <commit_id>` - Mantiene archivos en staging para poder aplicar cambios desde el commit anterior.
- `git reset --hard` - Borra información que hay en el staging permanentemente.
- `git checkout master <filename>` - Vuelve a la versión madre del archivo.
- `git commit --amend` - Remendar un commit incorrecto o incompleto y lo agrega al commit anterior.

### Config y errores:
- `git config --global user.name <username>`
- `git config --global user.email <user@email.com>`

Para sincronizar el repositorio de GitHub con el repositorio local (.git):
- `git remote add origin <URL>` - Guarda la liga como el repositorio remoto.

Verifica que la URL se guardó:
- `git remote`
- `git remote -v`

Sincroniza el repositorio local con los contenidos del remoto. Puedes usar uno de los primeros dos comandos de abajo:
- `git fetch`  
- `git pull origin master--allow-unrelated-histories` - Mergea ambas partes.
- `git push origin master` - Verificar que los push se pueden realizar sin conflictos.

## :scroll: Conceptos
Cada vez que se confirma un cambio, Git realiza algo parecido a una instantanea del aspecto de los archivos en ese momento. Si los archivos no se han modificado, git no almacena esos archivos de nuevo, sino un enlace a la última versión de ellos.  

Todo en Git es verificado mediante una __checksum__, y es identificado a partir de esa suma. Eso hace imposible cambiar los contenidos de cualquier archivo sin que Git lo sepa. Chechsum usa SHA-1, una cadena de caracteres hexadecimales con base en los contenidos del archivo:

```
c51cce4660f7057541da4325d45d5f01ffc23faf
```

### :godmode: Estados
Los archivos en tu repositorio se pueden encontrar principalmente en los siguientes estados:
- commited: cambios fueron confirmados y almacenados en tu base de datos local (ya fueron git committed.
- modified: modificados pero aún no están confirmados para ir a la base de datos local (la nueva versión no ha sido git added aún).
- staged: modificado y marcado para subir en el próximo commit (git added).
- untracked: elementos que no están siendo trackeados en el repositorio (ninguna versión del archivo ha sido git added aún. Cuando se hace un commit, arroja un mensaje de que se ha creado).

## Branches
Las branches en git se utilizan para mantener una versión (main regularmente) 'deployable'. Permite a un equipo trabajar en diferentes 'features' a la vez, sin comprometer la rama principal del proyecto.

Ramas estándares en equipos:
- Master o Main: producción
- Development: se alojan nuevas features, características y experimentos
- Hotfix: aquí se trabaja en issues y errores

### Usage:
- `git branch <branch_name>` - Crea una rama.
- `git checkout <branch_name>` - Sale de la rama actual y activa la rama indicada.
- `git checkout -b <branch_name>` - Sale de la rama actual, crea la rama indicada y la activa.
- `git push origin <branch_name>` - Para publicar la rama creada en el repositorio remoto.
Nota: Se debe hacer commit con los cambios realizados antes de salir de la rama actual.
- `git merge <branch_name>` - Crea un commit con la combinación de dos ramas (la activa y la indicada en el comando).
- `git branch -d <branch_name>` - Eliminar branch.

## :octocat: GitHub
Es la red que estaremos utilizando para almacenar nuestros repositorios. Git != GitHub. Te permite compartir tu código y explorar otros proyectos.

# Consola/Terminal
- CLI: codificada y estricta
- GUI: metafórica y exploratoria
- NUI: directa e intuitiva

La interfaz de usuario permite al usuario comunicarse con la computadora y comprende los puntos de contacto entre estos dos.

## CLI (Command Line Interface)
Lanza un prompt (`$ `) que espera un comando. La estructura de los comandos:

```
command [-option(s) [argument(s)]
```
Por ejemplo:
```
$ head -n 3 README.md
$ 
```
donde `head` me muestra las n primeras líneas de un archivo.

Ventajas:
- Pocos recursos
- Fácil de automatizar
- Más opciones de comandos

Desventajas:
- No intuitivo
- Curva de aprendizaje lenta
- No agradable a la vista
