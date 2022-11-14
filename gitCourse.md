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
