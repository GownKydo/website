+++
title = 'Comandos Basicos en Linux - Parte 1'
description = "Introduccion para comenzar a usar sistemas GNU/Linux como todo un chad"
date = 2024-01-10
categories = [
    "Linux",
    "bash",
]

image = "wallpaper.jpg"
+++


En esta ocasión, como se menciona en el título, vamos a adentrarnos en el mundo de Linux. Este post está dirigido a aquellos que son nuevos en este sistema operativo, con el fin de ayudarles y guiarlos en el uso de la terminal sin temor a romper algo con algún comando.  

Este post será muy práctico ya que nos vamos a abrir una terminar y vamos a ir probando los comandos, yo se los explicare paso a paso y la descripcion de cada uno y es importante que se para complementar los comandos basicos que aprenderemos en esta primera parte haremos esto todavia mas practico y practicaremos en una pagina considero increíble para aprender sobre los comandos en Linux un poco mas a fondo, lo cual es fundamental para saber acerca de linux.

Para dar un breve resumen, esta página consiste en un juego de desafios en seguridad informatica. Tendrás que usar comandos en Linux para encontrar un archivo .txt donde se encuentra una contraseña para un usuario. A medida que subes de nivel, la dificultad aumenta. Para avanzar, deberás encontrar una "flag" para cada usuario, lo que representa los diferentes niveles y la flag la contraseña de acceso a los mismos.

Espero que este post te sea de gran ayuda y te anime a explorar más sobre el fascinante mundo de Linux. ¡Empecemos!


## File Commands

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


No te preocupes si no has entendido algunos de los comandos antes mencionados o incluso si no logras memorizarlos. Recuerda igual darte un descanso y luego seguir repasando. Más adelante estaré explicando cómo usar cada uno de los comandos mencionados y notarán que existen muchas formas de aplicar estos comandos. No te rindas, que aquí viene lo interesante con los niveles de _OverTheWire_.

## Over The Wire 

Nos diriguimos a la siguiente pagina [over the wire](https://overthewire.org/wargames/bandit/), nos llevara a esta pagina:

![Menu](/img/level0/bandit0Menu.png)

### Level 0 -> Level 1

Aquí puedes leer más sobre lo que trata Bandit y en qué consiste. Nos dirigiremos al nivel 0, donde podemos ver las instrucciones para acceder como bandit0 y conectarnos al servidor mediante el comando SSH. Una vez que hemos leído las instrucciones, pasamos al siguiente nivel. En el siguiente nivel, podemos observar que nos dan las siguientes instrucciones.

![bandit0](/img/level0/bandit0.png)

Aquí ya podemos observar que las instrucciones nos indican que la contraseña para el siguiente nivel se encuentra en un archivo llamado "_readme_", localizado en el directorio home de nuestro usuario "_bandit0_". Vamos a confirmarlo. Como aún no me he conectado al juego, vamos a hacerlo.

En el nivel 0 se especifica que se debe usar `ssh` para acceder al servidor. Nos proporcionan un nombre de host, un puerto y la contraseña. La estructura del comando para acceder al nivel cero es la siguiente: `ssh bandit0@bandit.labs.overthewire.org -p 2220`. Si es nuestra primera vez usando el comando ssh, nos preguntará si estamos seguros de acceder al servidor. Entonces, escribimos 'Y/y' o simplemente "yes". A continuación, nos pedirá la contraseña del usuario bandit0, la cual es **bandit0**.

Una vez dentro del servidor, comprobamos que somos el usuario bandit0 con el comando `whoami`. Este comando nos sirve para saber qué usuario está usando el sistema actualmente y, si todo está bien, podemos observar claramente que se trata del usuario "bandit0". Posteriormente, escribimos el comando `ls` para listar el contenido de nuestro directorio home y ahí es donde se encuentra el archivo "_readme_" que contiene la contraseña para acceder a "bandit1". Escribimos el comando `cat readme` para leer el contenido de este archivo y, como se puede observar, esa es la contraseña para el siguiente nivel, la copiamos en nuestro portapapeles y del servidor con el comando `exit`

![level-0](/img/level0/level0.png)

### Level 1 -> Level 2

Para el siguiente nivel, vamos a acceder como bandit1. Vamos a usar el mismo comando que usamos anteriormente con bandit0, pero cambiando el usuario. El comando es el siguiente: `ssh bandit1@bandit.labs.overthewire.org -p 2220`. La única diferencia será el número del usuario, todo lo demás se mantiene igual. Accedemos y una vez que nos pida la contraseña pegamos la que habíamos guardado anteriormente en nuestro portapapeles.

Las instrucciones para el siguiente nivel son las siguientes.

![instructions-level-1](/img/level1/instructions_level1.png)

Nos especifica que la contraseña está guardada en un archivo localizado en el directorio home con el nombre: -.

El desafío parece simple, pero el problema surge cuando escribimos el comando `cat -`. Este se queda en espera, ya que lo toma como si fuera un parámetro de `cat`. Entonces, ¿cómo solucionamos esto? Para poder resolver este desafío, podemos hacerlo de varias formas:

1. **Desde la ruta absoluta:** `cat /home/bandit1/-`. De esta forma, indicamos la ruta completa del archivo, evitando que `cat` lo confunda con un parámetro.

1. **Forma alternativa de usar la ruta absoluta:** `cat $(pwd)/-`. Usando este método, nos ahorramos escribir toda la ruta. El comando `pwd` nos da la ruta actual, y si lo combinamos con los caracteres especiales `$()`, tomtamos el output del comando `pwd`, para que asi el comando `cat` interprete la ubicación donde estamos y ya solo hace falta poner el nombre del archivo que queremos leer.

2. **Indicando la ruta actual:** `cat ./-`. De esta forma le indicamos que queremos leer un archivo desde la ruta actual en la que nos encontramos (representada por un punto), y posteriormente escribmos el nombre del archivo que queremos leer.

Y podemos observamos que de cualquiera de estas maneras obtenemos la contraseña.

![level-1](/img/level1/level1.png)

Aqui conluimos con este nivel, nos salimos y accedemos al siguiente.

### Level 2 -> level 3

![instructions](/img/level2/instructions.png)

Para este nivel, observamos que hay un archivo llamado "_spaces in this filename_". Para poder leer este tipo de archivos con espacios, necesitamos escapar cada espacio con el carácter especial barra inversa `\`, quedando así el comando: `cat spaces\ in\ this\ filename`. De igual forma, podemos ahorrarnos esto usando la tecla tab, la cual nos autocompleta lo mencionado anteriormente.

Otra forma de hacer este proceso es usando comillas dobles, quedando de esta manera: `cat "spaces in this filename"`. De esta forma le indicamos el nombre del archivo.

Pero además de hacer eso, también podemos ahorrarnos escribir el nombre. Para hacer esto más rápido, hacemos uso del carácter especial asterisco `*`, quedando así el comando: `cat *filename`. De esta forma, le indicamos que queremos leer todos los archivos que terminen en "filename". Igualmente, se puede modificar el orden del asterisco, por ejemplo: `cat spaces*`, aquí se indica que queremos leer todos los archivos que comiencen con el nombre "spaces". 

Cabe aclarar que este comando es mejor usarlo cuando sabemos que solo existe un archivo con ese nombre; en caso contrario, listará el contenido de todos los archivos que encuentre con el nombre _spaces_.

![level-2](/img/level2/level2.png)

Ahora que tenemos la contraseña nos dirigimos al siguiente nivel.

### Level 3 -> Level 4

Para este nivel la contraseña esta guardada en un archivo oculto dentro del directorio "inhere"

Este nivel es muy simple, si listamos el contenido de la carpeta con el comando `ls`, sabremos que a simple vista nos e ve nada, para ello vamos a hacer uso de los parametros de dicho comando, usaremos el parametro `-a` para listar todo lo que se encuentre dentro del directorio quedando asi el comando: `ls -a inhere`. Y ahora podemos observar que hay un archivo con el nombre "...Hiding-From-You", con el comando cat revisamos el contenido y tendremos la contraseña.

![Level-3](/img/level3/download.png)

### Level 4 -> level 5

Para este nivel, se nos indica que la contraseña está guardada en un archivo humanamente legible, dentro del directorio "inhere".

Si listamos el contenido del directorio, podemos notar que hay múltiples archivos con distintos nombres. Dado que no todos tienen contenido legible y para evitar abrir e inspeccionar uno por uno, vamos a identificar el archivo correcto con el comando `file`, `xargs` y el comando `find`.

El comando `file` nos permite saber la clasificación de cada archivo: si es una imagen, un archivo de texto, un binario, un video etc. 

El comando `find` es una alternativa al comando `ls`, con la diferencia de que `find` busca desde la raíz de la ruta que se le pase. Por ejemplo, si escribimos el comando `find inhere`, este nos listará el contenido en forma de lista usando un formato de árbol binario.

El comando `xargs` lee los argumentos desde la entrada estándar. Por ejemplo, si nosotros escribimos el siguiente comando:

`echo "file1.txt file2.txt file3.txt" | xargs touch`

Esto creará los archivos `file1.txt`, `file2.txt`, y `file3.txt`

![ejemplo-xargs](/img/level4/ejemplo.png)

Lo que estamos haciendo es lo siguiente: dada la salida del comando `echo`, queremos crear archivos con el nombre de dicha salida. Entonces, se ejecuta `xargs touch` y el resultado es que se crean tres archivos con los nombres `file1.txt`, `file2.txt` y `file3.txt`.

Usando el carácter "or/pipe" `|`, que es un carácter especial, se puede hacer que la salida de un comando sea la entrada de otro comando. En el ejemplo anterior la salida del comando `echo` se vuelve la entrada del comando siguiente, en este caso del comando `touch`.

Bien, una vez explicado esto, utilizamos lo que sabemos con el comando `find`. Vamos a ejecutar la siguiente instrucción: `find . | xargs file`. Usamos el punto `.` en el comando `find` para especificar que queremos que busque archivos desde la ruta en la que estamos.

Si seguimos los pasos hasta aquí, ya tendremos listados todos los archivos y notamos que hay uno que es de tipo ASCII. Es el único dentro del directorio `inhere`. Por lo tanto, abrimos ese archivo con el comando `cat` y observamos que contiene la contraseña para el siguiente nivel.

![level-4](img/level4/level4.png)

### Level 5 -> level 6

Para este nivel, las instrucciones mencionan que el archivo que guarda la contraseña está en algún lugar dentro del directorio "inhere" y tiene las siguientes propiedades:

- Es humanamente legible.

- Tiene un tamaño de 1033 bytes.

- No es un archivo ejecutable.

Vamos a usar el comando `find`, ya que este comando tiene parámetros que nos pueden ayudar a encontrar el archivo siguiendo estas propiedades.

El comando que vamos a utilizar es el siguiente:

`find inhere/ -readable -size 1033c ! -executable`.

El parámetro `-readable` busca un archivo que sea legible. Con el parámetro `-size` especificamos que sea de un determinado tamaño; puede ser en megas, gigas, etc., pero en esta ocasión es en bytes, por lo tanto, se usa la letra 'c'_(Cada tamaño tiene una letra en especifico, puedes encontrarla en el manual page del comando find)_. El carácter de exclamacion `!` es para negar una condición, así que especificamos que no queremos que sea ejecutable. Si quitamos el signo de exclamación, le estamos indicando que queremos que sea ejecutable.

Al ejecutar el comando, podemos ver que nos da un output de un archivo en la carpeta "_maybehere07_", dentro del archivo "_.file2_". Entonces, tenemos varias formas de leer este archivo.

* Usando `cat` tomando el output del comando `find` como lo haría un chad promedio, el comando es el siguiente:

`cat $(find inhere/ -readable -size 1033c ! -executable)`

* Usando `cat` de manera normal, el siguiente comando seria este:

`cat inhere/maybehere07/.file2`

![ejemplo-1](/img/level5/metodos.png)

Ambas maneras nos daran la contraseña, pero de igual forma puedes seguir buscando mas alternativas y jugar con lo que hemos aprendido para tener un formato mas limpio de la contraseña, como se ve a continuacion.

![ejemplo-1.1](/img/level5/ejemplo.png)

Una vez obtuvimos la contraseña nos vamos para el siguiente nivel.  

### Level 6 -> level 7

Las instrucciones de este nivel son bastante similares a las del nivel anterior. Nos indican que la contraseña está guardada en algún lugar dentro del servidor. Por lo tanto, el archivo donde se encuentra la flag para el siguiente nivel tiene las siguientes propiedades:

* El propietario es bandit7.
* Pertenece al grupo bandit6.
* Tiene un tamaño de 33 bytes.

Una vez entendemos esto, vamos a usar el comando find con los siguientes parámetros:

* `-group`: para especificar el grupo al que pertenece el archivo.
* `-user`: seguido del nombre del propietario del archivo.
* `-size`: para especificar el tamaño del archivo, añadiendo una 'c' al final para indicar que estamos buscando en bytes.

El comando nos quedaría de la siguiente forma:

`find / -user bandit7 -group bandit6 -size 33c`

Una vez que presionamos Enter, observaremos que la pantalla se llenará de archivos que no podemos abrir, mostrando el mensaje "_Access denied_". Para filtrar estos accesos denegados, vamos a modificar nuestro comando agregando una instrucción al final: `2>/dev/null`.

Esta instrucción redirige los mensajes de error al `/dev/null`, veanlo como un agujero negro, se va al vacio, evitando que se muestren en la pantalla.

![ejemplo-1](/img/level6/level6.png)


El comando completo es el siguiente:

`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

dandonos como resultado el archivo que buscabamos, simplemente le hacemos un `cat` a la ruta o pueden hacerlo con `xargs cat`. Y nos vamos para el siguiente nivel.

![ejemplo-1.1](/img/level6/password.png)

### Level 7 -> level 8

Este nivel es muy simple, para esta parte ya pasamoa a la busqueda dentro de archivos, por lo que el nivel nos lo da entender, en las instrucciones se especifica que la contraseña esta almacenada dentro de un archivo llamado "_data.txt_" la contraseña es la siguiente a la palabra "_millionth_", entonces para completar este nivel vamos a usar el comando `grep`.

* `grep`: el comando grep es muy utili cuando queremos filtar informacion dentro de un archivo.

Para darle mas formato a nuestros ouputs tambien vamos a incluir el comando `xargs`, este comando igualemnte nos permite filtrar informacion, pero podemos jugar con sus parametros para que nos filtre informacion especifica de un output.

Entonces una vez dentro de bandit7, vamos a escribir el siguiente comando:

`grep "millionth" data.txt`

![ejemplo-1](/img/level7/ejemplo.png)

Y como podemos ver, tenemos la contraseña. Tambien podemos especificar la linea en la que se encuentra con el ṕarametro `-n`, pero para esta ocacion vamos a usar `awk` para unicamente filtrar por la contraseña, quedando asi el comando:

`grep "millionth" data.txt | awk '{print$2}'`

![ejemplo-1.1](/img/level7/argumento.png)

Y De igual forma nos da la contraseña. El numero 2, se usa para especificar un argumento, en este caso el output del comando grep tiene dos textos, por lo tanto le estamos filtrando por el segundo texto, el cual es tomando como un argumento o inlcuso podemos modificar el comando de `awk` para imprimir uncamente el ultimo argumento, el comando es el siguiente:

`grep "millionth" data.txt | awk 'NF{print$NF}'`

![ejemplo-1.2](/img/level7/awk.png)

Y nos da el mismo resultado que el anterior, la unica diferencia es la instruccion que le estamos pasando, en este ultimo comando queremos que nos imprima el ultimo argumento de la oracion y con el anterior comando unicamente el segundo argumento. Si existieran mas palabras despues de la contraseña seria mas optimo usar el anterior comando especificando donde se encutra el texto por el cual queremos filtar.

Nos pasamos al siguiente nivel.

### Level 8 -> level 9

Para este nivel nos indica que la contraseña esta guardada en el archivo "_data.txt_" y nos indica que es la unica linea que no se repite, si nosotros verificamos el contenido que hay dentro vamos a observar que nada tiene sentido no podemos saber cual es la contraseña, entonces lo que vamos a hacer es usar el comando `uniq` combinado con el comando `sort`.

![ejemplo-1](/img/level8/text.png)

El comando `sort`: nos va a permitir ordenar las lineas, lo toma en cuenta en cuestion de la primera letra, si es un numero con el numero 0, si es letra con la letra 'a'

![ejemplo-1.1](/img/level8/sort.png)

El comando `uniq`: nos ayudara a saber cual es la unica letra que no se repite en el texto.

Este es el comando que vamos a utilizar:

`sort data.txt | uniq -u`

dando la contraseña en cuestion y nos pasamos al siguiente nivel.

![ejemplo-2](/img/level8/pass.png)

### Level 9 -> level 10

Para este nivel nos indica que la contraseña se encuentra almacenada en un archivo "_data.txt_" y la contraseña se encuentra ubicada seguida de las unicas palabras que son humanamente legibles.

Lo que nos dice esto es que si leemos el contenido del archivo lo que vamos a encontrar es texto que no se entiende, entonces lo que vamos a hacer es usar el comando `strings`:

Contenido del archivo:

![file-data](/img/level9/data.png)

`strings`: Este comando nos listara todas las partes del archivo que son texto.

![strings_command](/img/level9/strings.png)

Podemos ver que nos ha filtrado las cadenas que son de texto, y aunque en su mayoría no se entiende, podemos ver una que dice “the”, y como el nivel nos decia, que la contraseña estaba en un valor con signos de igual, así que filtraremos con grep las lineas que tengan simbolos de igual:

`strings data.txt | grep "===="`

Vemos que nos a dado la contraseña, pero de igual manera podemos aplicar mas modificaciones a nuestro comando para obtener un texto mas claro y simplemnte sea la contraseña, por ejemplo:

Usando el comando `string data.txt | grep "====" | tail 1` hacemos que unicamente nos de la parte de de la ultima linea, ahora tambien haciendo esto podemos jugar de nuevo con el comando `awk` con el uso de parametros, entonces vamos a decirle a agregarle a nuestra salida que unicamente queremos el ultimo parametro que es donde se encuentra la contraseña, quedando asi el comando: 

`string data.txt | grep "====" | tail -1 | awk 'NF{print$NF}'`

Y esto nos dara la contraseña.

![pass](/img/level9/pass.png)


flag _(checkpoint)_: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey


### Level 10 -> level 11

Ahora este nivel es bastante facil ya que unicamente nos indica que hay que decodificar un archivo que contiene texto en base64, por lo tanto unicamente vamos a utilizar el comando `base64 -d`, el parametro -d quiere decir "decode"

por lo tanto el el comando seria el siguiente:

`cat data.txt | base64 -d`

Y como podemos ver tenemos la contraseña, nos dirigimos al siguiente nivel.


![password](/img/level10/pass.png)


> Recomiendo descansar aca e iniciar de nuevo desde el nivel 0 para intentar nuevas maneras de acceder a los niveles


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

# Level 14 > Level 15

