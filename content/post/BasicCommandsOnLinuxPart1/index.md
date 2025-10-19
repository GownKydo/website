+++
title = 'Comandos Basicos en Linux(Guia Completa)'
description = "Introduccion para comenzar a usar sistemas GNU/Linux como todo un chad"
date = 2024-01-10
categories = [
    "Linux",
    "Bash",
    "Tutorial",
    "Comandos",
    "Sistemas Operativos",
]
tags = [
    "Linux",
    "Bash",
    "Comandos",
    "Terminal",
    "Sistemas Operativos",
    "Guía",
    "Automatización",
    "Productividad",
    "Desarrollo",
]

image = "wallpaper.jpg"
+++


En este post nos adentraremos en el mundo de Linux, ideal para quienes son nuevos en este sistema operativo. Aprenderemos a usar la terminal de manera segura y sin miedo a cometer errores con los comandos.

Vamos a practicar directamente en la terminal, paso a paso, explicando cada comando y su función. Utilizaremos una página especializada para practicar y aprender comandos básicos en Linux de manera efectiva.

La página ofrece desafíos de seguridad informática donde usaremos comandos en Linux para encontrar contraseñas en archivos .txt. A medida que progreses, los desafíos se vuelven más difíciles, requiriendo encontrar una "flag" para avanzar de nivel.

Espero que este artículo te sea útil y te anime a explorar más el fascinante mundo de Linux. ¡Empecemos!

## File Commands(Guia Rapida)

Los comandos de archivos, los cuales nos sirven para poder navegar atravez de la terminal y de igual forma crear, mover, renombrar, listar, eliminar etc.

Esta primera parte son los comandos fundamentales para empezar con el uso de una terminal.

* Comandos para archivos y directorios:

    * `ls` - Lista los directorios y archivos en la ubicacion que te encuentras
    * `ls -l` - Lista los directorios y archivos con un formato mas amplio, informacion de los mismos
    * `ls -a` - Lista todos los archivos y directorios incluyendo los que esten ocultos

    * `cd /path/to/directory` - Te permite entrar o salir de una carpeta
    * `cd ..` - Te permite salir del directorio actual en el que te encuentas.

    * `pwd` - Muestra la ubicacion actual en la que te encuentras dentro de un directorio

    * `touch file_name` - Crea un archivo
    * `mkdir dir_name` - Crear un directorio en la ruta actual en la que te encuentras
    * `rm` - Eliminar un archivo 
    * `rm -r` - Elimina una carpeta
    * `mv old_name new_name` - Renombra un archivo o directorio
    * `mv file_or_dir /path/to/move`  - Mueve un archivo o directorio a una carpeta

    * `cat file_name` - Muestra el contenido de un archivo
    * `cp file_name /path/to/copy` - Copia un archivo a una ruta
    * `cp -r dir_name /path/to/copy` - Copia un directorio a una ruta 


## File permisions

Los permisos de archivo se refieren a los derechos y restricciones que se asignan a archivos y directorios, estos permisos determinan quién puede leer, escribir y ejecutar un archivo o directorio. Hay tres tipos básicos de permisos **_lectura(r)(4), escritura(w)(2) y ejecucion(x)(1)_**

* Comandos:
    * `chmod +x file_name` - Asigna el permiso de ejecucion usando el identificador por letras.
    * `chmod 111 file_name` - Asigna el permiso de ejecucion de acuerdo al sistema binario.
    * `chown user:group file_name` - Cambia el propietario y grupo de un archivo o directorio


## ssh commands

Los comandos de SSH son herramientas fundamentales para gestionar conexiones seguras entre computadoras a través de una red. Permiten iniciar sesiones remotas, transferir archivos de manera segura y configurar túneles para el acceso seguro a servicios de red.

Estos comandos son esenciales para administrar sistemas de forma remota de manera segura y eficiente, facilitando tareas como la gestión de archivos, la ejecución de comandos en máquinas remotas, y la configuración y mantenimiento de servicios a través de conexiones encriptadas.

* Comandos basicos para hacer una conexion por ssh:
    * `ssh user@host` - conectarnos a un host como usuario
    * `ssh-keygen` - Se usa para generar una clave privada y una clave publica 
    * `ssh -p port user@host` - Conectarnos a un host como un usuario mediante un puerto en especifico
    * `ssh-copy-id user@host` - Copia tu llave publica al servidor remoto para registrar tu login


## Searching files or directories

Los comandos para buscar archivos o directorios como su nombre lo indica nos ayudar a encontrar mucho mas rapido el directorio o archivo desde nuestra terminal de una manera mas rapida sin tener que navegar hasta la ruta en la que se encuentra

* comandos de busqueda:
    * `grep "word" file_name` - Nos permite buscar palabras dentro de archivo
    * `find /path/to/find -name file_or_dir_name`- Buscar archivos por nombres haciendo uso de la base de datos en nuestro sistema

> Más adelante exploraremos otros usos del comando find para realizar búsquedas de manera aún más eficiente.


## Process Managment and System information

La gestión de procesos se refiere al conjunto de técnicas y herramientas utilizadas para controlar y supervisar los procesos que se ejecutan en un sistema operativo. Esto incluye actividades como la creación, terminación, pausa, reanudación y monitoreo de procesos.

* Comandos:
    * `ps` - Muestra los procesos activos en tiempo real
    * `ps aux | grep process_name` -  Busca procesos por el nombre
    * `top` - Muestra todos los procesos activos
    * `kill pid` - Cierra los procesos usando un pid(numero del proceso)
    * `killall process_name` - Cierra todos los procesos que se llamen por el nombre especificado

    * `date` - Muestra la fecha y hora actual configurada en tu sistema
    * `uname -a` - Muestra informacion del sistema y del kernel
    * `df -h` - Muestra el espacio en el disco duro del sistema
    * `du -sh dir_name` - Muestra espacio que consume un directorio


No te preocupes si no has entendido algunos de los comandos antes mencionados o incluso si no logras memorizarlos. Recuerda igual darte un descanso y luego seguir repasando. Más adelante estaré explicando cómo usar cada uno de los comandos mencionados y notarán que existen muchas formas de aplicar estos comandos. No te rindas, que viene lo interesante con los niveles de _OverTheWire_.

