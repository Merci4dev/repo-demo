# Curso de Git
    Git es un sistema de control de versiones distribuido, lo que significa que un clon local del proyecto es un repositorio de control de versiones completo. Estos repositorios locales plenamente funcionales permiten trabajar sin conexión o de forma remota con facilidad. Los desarrolladores confirman su trabajo localmente y, a continuación, sincronizan su copia del repositorio con la copia en el servidor.


# Configuracion Inicial
* git --version
    ver la version de git intalada
* git config --global 
    configuracion global para todo tu sistema
* git config --global user.email merci4dev@...
* git config --global user.name "Merci4dev"
    configura ell correo elctronico y el user

* git config --list
    mustra la configuracion de git
    
* git config --global core.editor "code --wait"
    asignando visual studio code como editor de configuración de git
* git config --global -e
    habre la configuracion en visul etudio code
* git config --global core.autocrlf input
    para estandarizar los saltos de línea en linux/mac
* git config --global core.autocrlf true
    para estandarizar los saltos de línea en windows
* git config -h
    ver todas las opciones de la configuración en la terminal
* git help config
    ver todas las opciones de la configuración en el navegador
* 

# Inicializar un projecto de git
    En  git existen 4 estado, 3 de ello suceden en la maquina del user(el el working directory) y el 4 en github
    modified:
        cada vez que modificamos un file 
    staged:
        cuan do hacemo un (git add). Registra los cambio. Se puede descartar algunos cambios 
    commmited:
        git commit (pasa del staged a la cabeza del repo local). los cambio se registrar de manera oficial
    remote:
        git push. Empuja los cambio de loca al repo remote

* git init
    inicializa el projecto
* git add archivo/directorio
    agregar los cambios de un archivo al staged
* git add .
    agregar todos los cambios de todos los archivos al staged
* git status -s 
    para ver el status de los cambio
* git commit
    habre la interfaz de visul s code para en nombre del commit
* git commit -m "commit name"
    ejecuta el commit directamente con un nombre
* git push
    enpuja los cmbio de local a remoto (aqui va la url)
* git pull
    para descargar cambion de un repo hacia tu pc

    git init
    git commit -m "first commit"
    git branch -M main
    git remote add origin https://github.com/Merci4dev/repo-demo.git
    git push -u origin main


# Pasar de master a main
paso 1
* git branch -m master main
    Crea la rama local main y pásale el historial de la rama master

paso 2
* git push -u origin main
Haz un push de la nueva rama local main en el repositorio remoto de GitHub


paso 3
* git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
    Cambia el HEAD actual a la rama main

paso 4
    Cambia la rama default de master a main en tu repositorio de GitHub (en settings)

paso 5
* git push origin --delete master
    Elimina la rama master del repositorio remoto


# Ignorar archivos
    En el archivo .gitignore incluimos todo lo que NO queramos incluir en nuestro repositorio. Lo podemos crear manualmente o con gitignore.io.

    # esto es un comentario
    archivo.ext
    carpeta
    /archivo_desde_raiz.ext

* ignorar todos los archivos que terminen en .log
    *.log

* excepto production.log
    !production.log

* ignorar los archivos terminados en .txt dentro de la carpeta doc,
    pero no en sus subcarpetas
    doc/*.txt

* ignorar todos los archivos terminados en .txt dentro de la    carpeta doc y también en sus subcarpetas

# Clonado de ropositorios
    git clone https://github.com/mercedes4developers/react-p-portfolio.git


# Ramas
    Una rama nos permite aislar una nueva funcionalidad en nuestro código que después podremos añadir a la versión principal.

* git branch nombre-rama
    crear rama

* git checkout nombre-rama
    cambiar de rama
    Ojo: hay que hacer commit antes de dejar una rama

* git checkout -b rama
    crear una rama y cambiarte a ella

* git branch -d nombre-rama
    eliminar rama. si estas en una rama tendras que cambiarte para poder eliminar esta

* git push origin --delete nombre-rama
    eliminar ramas remotas

* git branch -D nombre-rama
    eliminar rama (forzado)

* git branch
    listar todas las ramas del repositorio

* git push --set-upstream origin branchName
    añade de forma remota esa rama al repo
    OJO pero los files no se añaden al repo principal. Si nos cambiamos a una de las rams que pusheamos veremos los files

    par que una rama solo tenga su file y los del repo original hay que ir a la rama principal y despues crear la rama.


* git branch --no-merged
    lista ramas no fusionadas a la rama actual

* git branch --merged
    lista ramas fusionadas a la rama actual

* git checkout rama-secundaria
  git rebase rama-principal
    rebasar ramas

# Fusiones
    Une dos ramas. Para hacer una fusión necesitamos:

    Situarnos en la rama que se quedará con el contenido fusionado.

    Fusionar.
    Cuando se fusionan ramas se pueden dar 2 resultados diferentes:

    Fast-Forward: La fusión se hace automática, no hay conflictos por resolver.
    Manual Merge: La fusión hay que hacerla manual, para resolver conflictos de duplicación de contenido.

* git checkout rama-principal
    nos cambiamos a la rama principal que quedará de la fusión

* git merge rama-secundaria
    ejecutamos el comando merge con la rama secundaria a fusionar


# Cambios(commits)
    Puedes agregar modificaciones al último cambio

* git commit --amend --no-edit
    midifica un commit pero sin modificar el mensaje del último commit. Pero el if del commit se modifica

* git commit --amend -m "nuevo mensaje para el último commit"
    editando el mensaje del último commit

* git reset --hard HEAD~1
    eliminar el último commit
    Podemos desplazarnos en el historial del repositorio hacia atrás o adelante en cambios o ramas , sin afectar el repositorio como tal.

* git checkout nombre-rama
    cambiar a una rama

* git checkout id-commit
    git checkout 3986293 
    cambiar a un commit en particular

# Registro del historial
* git log 
    nos permite conocer todo el historial de un proyecto, con la información de la fecha, el autor y id de cada cambio.

* git log --oneline
    muestra en una sola línea por cambio

* git log > commits.txt
    guarda el log en la ruta y archivo que especifiquemos

* git log --pretty=format:"%h - %an, %ar : %s"
    muestra el historial con el formato que indicamos

* git log -n
    git log -2
    cambiamos la n por cualquier número entero y mostrará los n cambios recientes

* git log --after="2019-07-07 00:00:00"
    muestra los cambios realizados después de la fecha especificada

* git log --before="2019-07-08 00:00:00"
    muestra los cambios realizados antes de la fecha especificada

* muestra los cambios realizados en el rango de fecha especificado
    git log --after="2019-07-07 00:00:00" --before="2019-07-08 00:00:00"

* git log --oneline --graph --all
    muestra una gráfica del historial de cambios, rama y fusiones

* git reflog    
    muestra todo el registro de acciones del log
    incluyendo inserciones, cambios, eliminaciones, fusiones, etc.

* git diff
    diferencias entre el Working Directory y el Staging Area

*  git log --oneline --graph --all
    para ver los commit, ramas, fusines en un grafico 

*  git log --oneline --graph --all > graph.tx
    lo guarda en file

# Reseteo del historial
    Podemos eliminar el historial de cambios del proyecto hacia adelante con respecto de un punto de referencia.

* git status
    nos muestra el listado de archivos nuevos (untracked), borrados o editados

* git reset --soft
    borra HEAD del repo. reseteo suave

* git reset --mixed
* git restore --staged 
    borra HEAD y Staging

* git reset --hard
    borra todo: HEAD, Staging y Working Directory

* git reset id-commit
    deshace todos los cambios después del commit indicado, preservando los cambios localmente

* git reset --hard id-commit
    desecha todo el historial y regresa al commit especificado

# Resetear un repositorio
    Si en algún momento tienes la necesidad de resetear el historial de cambios de un repositorio para que quede como si lo acabarás de crear ejecuta esta serie de comandos:

cd carpeta-repositorio

* mv .git/config ~/saved_git_config
    respaldo del git config
* rm -rf .git
    ellimina el dir .git
git init
    inicializar git
git branch -M main
git add .
git commit -m "Commit inicial"
* mv ~/saved_git_config .git/config
    vueve la configuracion al dir .git
* git push --force origin main
    hacemos un push

# Remotos
* git remote
    muestra los orígenes remotos del repositorio

+ git remote -v
    muestra los orígenes remotos con detalle

* git remote add nombre-orígen https://github.com/usuario/repositorio.git
agregar un orígen remoto

* git remote rename nombre-viejo nombre-nuevo
    renombrar un orígen remoto

* git remote remove nombre-orígen
    eliminar un orígen remoto

* git checkout --track -b rama-remota origin/rama-remota
    descargar una rama remota a local diferente a la principal


# Etiquetas
    Con esta opción git nos permite versionar nuestro código, librería o proyecto.

* git tag
    listar etiquetas

* git tag numero-versión
    crea una etiqueta

* git tag -d numero-versión
    eliminar una etiqueta

* git show numero-versión
    mostrar información de una etiqueta

*sincronizando la etiqueta del repositorio local al remoto
    git add .
    git  tag v1.0.0
    git commit -m "v1.0.0"
    git push origin numero-versión

* generando una etiqueta anotada (con mensaje de commit)
    git add .
    git tag -a "v1.0.0" -m "Mensaje de la etiqueta"
    git push --tags

#
