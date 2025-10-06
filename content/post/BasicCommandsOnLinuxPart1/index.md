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

## Over The Wire (Practica)

### Level 11 -> level 12

Para este nivel nos dice que la contraseña esta siendo rotada en 13 posiciones, para poder entender esto les dare una explicaion acerca del cifrado cesar, ya que asi podriamos entender mejor el comando que vamos a usar.

#### Cifrado Cesar:

Vamos a utilizar la palabra "hola" de prueba y la vamos a rotar en 5 posiciones, y la forma en la que lo vamos a hacer es la siguiente:

teniendo en cuenta que tenemos la palabra hola, vamos a posicionar la letra inicial en el abecedario, quedando como la posicion de la 'M' en 0 y pasamos a contar 5 letras en adelante, llegando hasta la letra 'M', esto significa que vamos a intercambiar la letra 'H' con la 'M' y repetimos el proceso en cada letra vamos a empezar desde cero, quedando asi "_hola_" en forma cifrada "_mtpf_"

![Caesar-Chiper](img/level11/CaesarCode.png)

Si queremos decodificar el texto simplemente aplicamos todo al inversa, empezamos desde la letra "_M_" y contamos en reversa hasta llegar a 5, y podemos ver que es hasta la letra "_H_" y repetimos el proceso para las siguientes letras

![Decode](/img/level11/CaesarDecode.png)


Bueno una vez entenido esto pasamos de nuevo a resolver el nivel de bandit; Vamos a leer el contenido del archivo y ahora sabiendo que este texto hay que decodificarlo usando 13 posiciones vamos a usar el comando `tr`. 

`tr`: es utilizado para eliminar caracteres o traducirlos de una entrada.

El comando a utilizar es el siguiente:

`cat data.txt | tr '[G-ZA-Fg-za-f]' '[T-ZA-St-za-s]'`

Ahora quiero explicar que es exactamente los parametros del comando `tr`.

* `[G-ZA-Fg-za-f]`: Esto es el conjunto de caracteres que quiero traducir:
    * `G-Z`: Todos los caracteres desde la 'G' hasta la 'Z'
    * `A-F`: Todos los caracteres desde la 'A' hasta la 'F'

Aplicando los mismo para el letras minisculas y lo mismo para el siguiente parametro del comando tr. Le damos enter y podemos observar la contraseña

![password](/img/level11/pass.png)

### Level 12 -> Level 13


En este nivel nos especifica que vamos a trabajar con un archivo hexdump, un hexdump es un archivo que se ha comprimido varias veces, entonces para este nivel nos pide crear un directorio en la ruta `/tmp` para poder mover el archivo a la carpeta creada, tambien indica que hay que cambiarle el nombre al archivo.

Entonces vamos a empezar un **hexdump** _(Volcado hexadecimal)_ es una visualizacion de los datos de un archivo. Si leemos el contenido del archivo tendremos lo siguiente:

```bash
00000000: 1f8b 0808 dcaa 7366 0203 6461 7461 322e  ......sf..data2.
00000010: 6269 6e00 0141 02be fd42 5a68 3931 4159  bin..A...BZh91AY
00000020: 2653 5946 b21b 1500 001c 7fff dcff d2ff  &SYF............
00000030: f96f b6bf 0fd6 d7ff b7bf bffd a5fe 3fef  .o............?.
00000040: b6de 9fff bebe ffbc cfef f7ff b001 3b16  ..............;.
00000050: 51d0 0191 a1a0 68c9 a000 000d 321a 0680  Q.....h.....2...
00000060: 0d00 000d 000c 4c4c 101a 0006 8006 8000  ......LL........
00000070: 6834 1ea1 a699 3d4f 46a7 a880 0000 0034  h4....=OF......4
00000080: 0000 681a 1a32 34da 80d0 1a68 c803 4003  ..h..24....h..@.
00000090: 4193 2794 d1a3 4f41 1ea0 1a6d 41ea 0000  A.'...OA...mA...
000000a0: d1a0 6800 6800 74d1 a1a3 236a 0343 4d06  ..h.h.t...#j.CM.
000000b0: 41a0 0193 40d0 0006 81a6 8068 34d0 1a00  A...@......h4...
000000c0: 0034 f483 2000 341a 1a07 a8d1 ea00 01ea  .4.. .4.........
000000d0: 7a40 d341 11a3 2206 8c3e 78ef 6b88 f36a  z@.A.."..>x.k..j
000000e0: d1e9 00a8 22a8 54de d2cb 05f7 589c afb2  ....".T.....X...
000000f0: 57d7 5466 402c e6e8 c692 14f8 77e6 c3a4  W.Tf@,......w...
00000100: 8f56 b2e9 14a3 4b69 6c34 6632 0c50 6d95  .V....Kil4f2.Pm.
00000110: 8dbd cd71 b0a1 4dae 0e49 a568 74aa 7111  ...q..M..I.ht.q.
00000120: 8fa6 5c3c 1dcf 8384 9db0 c5f7 a31d f97d  ..\<...........}
00000130: 5b02 0708 b1eb cb42 4024 131a 0be7 e8df  [......B@$......
00000140: 26fb d4c1 0fda ea8f 13a0 fdf5 ff60 811d  &............`..
00000150: b030 b5f5 b627 7a27 32c7 084f bde4 40e6  .0...'z'2..O..@.
00000160: 5528 d67c 9000 fa43 8547 d5b9 0aa2 0c84  U(.|...C.G......
00000170: 0849 ad45 ea52 a830 863e beb3 4cbb a8e3  .I.E.R.0.>..L...
00000180: 7a94 470d 0865 0935 3546 5167 f791 7f81  z.G..e.55FQg....
00000190: 9d54 275a 5125 d043 720a 8328 a05c 6507  .T'ZQ%.Cr..(.\e.
000001a0: 29d7 445d 3287 9444 396a 09c0 2c66 04f2  ).D]2..D9j..,f..
000001b0: d12a 8c12 5122 48b2 b594 b43c bcc5 e44d  .*..Q"H....<...M
000001c0: 045d 32df b558 6088 2c19 4e83 7102 9018  .]2..X`.,.N.q...
000001d0: f052 147e bc75 a772 ff8b 156d 4f2b 8c73  .R.~.u.r...mO+.s
000001e0: f7b1 344b aba4 0b3c 89a0 2434 4501 d86f  ..4K...<..$4E..o
000001f0: 0ad9 6dd2 8543 d008 d3fa 2e8f d86a 743c  ..m..C.......jt<
00000200: 4996 19b5 ac0a 110c aa40 4edf 4e6f 0ed4  I........@N.No..
00000210: dc9f 1a07 d343 1328 a9c1 34ba e4d2 d1e8  .....C.(..4.....
00000220: 626c 4701 aa5d 75d5 e0b3 ee16 6218 5d04  blG..]u.....b.].
00000230: 991d f752 c613 bfa0 8664 9bb1 0dbf e775  ...R.....d.....u
00000240: ba89 1487 72b9 28c1 df81 8665 4082 27ff  ....r.(....e@.'.
00000250: 1772 4538 5090 46b2 1b15 8195 ba71 4102  .rE8P.F......qA.
00000260: 0000                                     ..


```

Para saber exactamente de que archivo se trata tenemos que verificar los magic numbers. Estos numeros magicos son bytes agrupados que indican el tipo al que pertenece un archivo, para encontrar los numeros magicos nos dirigimos a la primera linea del contenido del archivo, la cual es la siguiente:

`00000000: 1f8b 0808 dcaa 7366 0203 6461 7461 322e  ......sf..data2.`

Lo que nos indica con que archivo estamos lidiando es lo que sigue despues de los numeros '0', podemos observar que es `1f8b`, Si buscamos a que archivo pertenece este numero magico nos saldra que es de un archivo con formato gzip, lo que nos dice que se trata de un archivo con extencion `.gz``

![format](/img/level12/Table.png)

Una vez sabemos esto, nos dirigimos a la carpeta tmp donde nos copiaremos el archivo. Vamos a aplicarle el comando `xxd` con el parametro `-r`, quedando asi el comando: `cat data | xxd | xxd -r`

* El comando `xxd -r`: Convierte el contenido hexadecimal a su forma binaria original.

Por ejemplo: Nosotros tenemos esta cadena "Hola que tal" y le aplicamos el comando xxd nos permite ver la cadena en hexadecimal: 

`echo "Hola que tal" | xxd`

Pero ahora si hacemos 

`echo "Hola que tal" | xxd | xxd -r`

Nos tendira que revertir al texto original. Ahora si unicamente queremos quedarnos con la parte hexadecimal tendriamos que aplicarle otro parametro al comando xxd, el cual es el siguiente:

`echo "Hola que tal" | xxd -ps` 

![ejemplo](/img/level12/ejemplo.png)

Ahora nos pasamos a nuestro archivo y lo primero que nos interesa es que es todo ese texto, entonces nos dirigimos a la ruta /tmp que fue donde creamos nuestra carpeta de trabajo para este nivel y copiamos ahi el archivo, lo vamos a copiar con la extencion **.hex**, quedando asi el comando: `cp ~/data.txt data.hex`.
Una vez hecho eso ejecutamos el comando `xxd -r data.hex` vamos a observar que nos dara simbolos raros y esto claramente no nos dice muy bien de que archivo se trata, entonces lo que vamos a hacer es migrar todo este output a un archivo y esto lo haremos de la siguiente manera: 

`xdd -r data.hex > data` 

Bien y ahora con el comando `file` vamos a verificar que tipo de arhcivo es, y como se puede ver se trata de un gzip,

![ejemplo-1](/img/level12/hexdump.png)

#### Instalacion de herramientas 7z y xxd

Lo que vamos a hacer a continuacion es usar el comando `7z`, esta herramienta nos permite descomprimir archivos ya que es universal, nos ahorramos escribir comandos como `tar-xf, gunzip, bzip2` etc. Y otra cosa importante es que 7z nos permite listar el contenido de un archivo comprimido, con el parametro 'l'. Una cosa a aclarar es que 7z no viene instalado en el servidor de over the wire, por lo que tendremos que migrar todo a nuestro entorno.

Si no tiene instalado 7z o xxd en su sistema pueden escribir el siguiente comando para inslarlo: 
* instalar 7z
    * Para sistemas basados en debian `sudo apt install 7z`.
    * Para sistemas basados en arch: `sudo pacman -S p7zip` 
* Instalar xxd
    * Para sistemas basados en debian `sudo apt install xxd`.
    * Para sistemas basados en arch: `sudo pacman -S tinyxxd`

Como en las intrucciones de over the wire se nos indica que un comprimido se comprimio varias veces pues vamos a automatizar el poceso de descomprimir los archivos esto para evitarnos hacer el mismo proceso para cada archivo manualmente.

#### Script para descomprimir archivos.

Bien una vez en nuestro entorno y ya con las herramientas instaladas, vamos a copiar el contenido antes visto y lo pegamos en un archivo con extencion ".hex", despues copiamos todo el output a otro archivo llamado "data", Una vez llegamos al mismo punto que en el servidor de over the wire empezamos con el script, 

Creamos el archivo usando `touch` y le damos permisos de ejecution con `chmod +x` y escribimos lo siguiente

```bash
#!/bin/bash/

name_decompressed=$(7z l data.gzip | grep "Name" -A 2 | tail -1 | awk 'NF{print$NF}')
7z x data.gzip > /dev/null 2>&1

while true; do
    7z l $name_decompressed > /dev/null 2>&1

    if [ $? -eq 0 ]; then
        decompressed_next=$(7z l $name_decompressed | grep "Name" -A 2 | tail -1 | awk 'NF{print$NF}')
        7z x $name_decompressed > /dev/null 2>&1 && name_decompressed=$decompressed_next
    else
        cat $name_decompressed
        exit 1
    fi
done
```

Aqui la explicacion de que hace cada linea de codigo:

* `name_decompressed=$(7z l data.gzip | grep "name" -A 2 | tail -1 | awk 'NF{print$NF}')`
    * `7z l data.gzip`: Es utilizado para listar el contenido del archivo con el parametro 'l'.
    
    ![ejemplo-2](/img/level12/ejemplo2.png)

    * `grep "Name" -A 2`: Filtra las lineas que coniene la palabra "Name" y muestra ademas las dos lineas siguientes despues de encontrar la palabra "Name".

    ![ejemplo-2.1](/img/level12/ejemplo2-1.png)
    
    * `tail -1`: Muestra la ultima linea de la salida generada por `grep`.

    ![ejemplo-2.2](/img/level12/ejemplo2-2.png)

    * `àwk NF{print$NF}`: Se utiliza para imprimir el ultimo campo de las lineas, esto se usa para extraer el nombre del archivo siguiente a descomprimir.

    ![ejemplo-2.3](/img/level12/ejemplo2-3.png)

* `7z x data.gzip > /dev/null 2>&1`: Esta line adescomprime nuestro primer archivo
    * `> /dev/null 2>&1`: Redirige la salida estandar **STDOUT** al `/dev/null`, es STDOUT descarta cualquier output, añadiendo esta operacion `2>&1`, lo que hace que sea **STDERR**, antes habiamos usardo el estandar **STDOUT** que solo descarta los mensajes de errores porque colocabamos `2>/dev/null` que lo hace diferente.

* `while true; do`: inicia un bucle infinito el cual se cierra con `done`.

* `7z l "$name_descompressed" > /dev/null 2>&1`: Esta listando el contenido del primer archivo descomprimido

* `if [ $? -eq 0 ]; then`; Esta linea verifica el comando de salida ejecutado recientemente, para validar si es verdadero o falso.
    * `$?`: Es una variable en bash que contiene el ultimo codigo de estado, puede ser cero o uno.
    * `-eq 0`: Comprar que el codigo de salida sea igual a 0, en la mayoria de casos es un codigo de estado verdadero.

* `7z x "$name_decompressed" > /dev/null 2>&1 && name_decompressed=$decompressed_next`: Descomprime el archivo actual (`$name_decompressed`). Si la descompresión tiene éxito (comando retorna 0), actualiza name_decompressed con el nombre del próximo archivo descomprimido (`$decompressed_next`).

```bash
    else
        cat "$name_decompressed"
        exit 1
    fi
```
Si el comando `7z l "$name_decompressed"` no tuvo éxito (código de salida distinto de 0):
* `cat "$name_decompressed"`: Muestra el contenido del archivo descomprimido actual.
* `exit 1`: Termina el script con un código de salida 1, indicando un error.

Y asi es como podemos obtener la contraseña sin tener que descomprimir todos los archivos manualmente, procedemos a irnos al siguiente nivel.

![ejemplo-1](/img/level12/pass.png)

### Level 13 -> level 14

En este nivel se nos esta indicando que la contraseña esta guardada en la ruta `/etc/bandit_pass/bandit14`, pero esta contraseña solo puede leerla el usuario _"bandit14"_, entonces se nos dara una clave ssh para poder acceder como _bandit14_.

![ejemplo-1](/img/level13/problem.png)

Entonces haremos lo siguiente:

`ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`

Nosotros ya sabemos que tenemos una clave ssh privada y con el comando que le acabamos de pasar le especificamos nos queremos conectar a el usuario bandit14 si tener que usar una contraseña, porque la llave privada generada ya actua como una contraseña para entrar como el usuario bandit14.

y haciendo esto vemos que accedemos como bandit14, entonces nos dirigimos al archivo y podremos ver la contraseña.

![](/img/level13/password.png)

### Level 14 > Level 15

Este nivel se va a centar en conexiones por TCP, lo que nos dice en el este nivel es que la contraseña puede ser capturada proporcionando la contraseña del nivel actual por el puerto 30000 del localhost

Bueno entonces con eso nosotros ya identificamos que el puerto 30000 esta abierto y para comprobarlo vamos a lanzar una cadena por ese puerto:

`echo '' > /dev/tcp/127.0.0.1/30000`

Posterior a esto podemos ver que no nos devuelve nada y si imprimimos el codigo de estado podemos ver que nos da un codigo de estado exitoso, entonces confirmamos que el puerto esta abierto 

Ahora lo que vamos a hacer es mandarle la contraseña de nuestro usuario bandit14, ahora vamos a hacerlo, para esta ocacion usaremos el comando `nc`, quedando de la siguiente manera

`nc bandit.labs.overthewire.org 30000`

damos enter e ingresamos la contraseña y como podemos ver nos dara la contraseña.

![ejemplo](/img/level14/password.png)


> flag _(checkpoint)_: 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

### Level 15 

Este nivel es parecido al nivel anterior, lo que vamos, lo que podemos observar de principio si el comando que usamos anteriormente usando el comando nc por el puerto 30001 vemos que no nos da nada, si probamos conectarnos por telenet tampoco nos dara el acceso, esto se debe a que ahora la comunicacion esta viajando por un un protocolo de encriptacion.

![](/img/level15/information.png)

Entonces vamos a usar la biblioteca **openssl** para comunicaciones seguras a traves de redes, con una implementacion de protocolos criptograficos como por ejemplo usando **TLS**_(Transport Layer Security)_ y **SSL**_(Secure Sockets Layer)_

Usando openssl y revisando un poco la documentacion del mismo, vamos a usar el parametro s_client para conectarnos como clientes y no como si fueramos un servidor como lo haciamos por "telnet" o con "nc"

El comando es el siguiente: `openssl s_client -connect localhost:30001`

Explicacion del comando: 

1. **OpenSSL**: Nombre de la biblioteca y launcher de la misma para la biblioteca
2. **s_client**: Este es una implementacion SSL/TLS de una conexion tranparente como cliente para acceder a un servidor de manera remota hablando de igual forma SSL/TLS lo que hace que pueda entender lo que estamos mandando por este canal.
3. **-connect host:port**: Parametro de s_client para conectarnos usando un host y un puerto en especifico, si no establece el puerto tomara el de localhost por defecto.

Una vez que le demos enter veremos lo siguiente, en este espacio solo copiaremos y pegamos la contraseña del nivel 15 y nos tiene que devolver la contraseña del nivel 16. Y aqui es como terminamos el nivel 15!

![](/img/level15/password.png)

# Level 16

> building . . .
