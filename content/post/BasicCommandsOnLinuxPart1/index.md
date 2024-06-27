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

Este post será muy práctico, y para ello me guiaré de una página que considero increíble para aprender sobre los comandos en Linux. Para dar un breve resumen, esta página consiste en un juego de desafios en seguridad informatica. Tendrás que usar comandos en Linux para encontrar un archivo .txt donde se encuentra una contraseña para un usuario. A medida que subes de nivel, la dificultad aumenta. Para avanzar, deberás encontrar una "flag" para cada usuario, lo que representa los diferentes niveles y la flag la contraseña de acceso a los mismos.

Espero que este post te sea de gran ayuda y te anime a explorar más sobre el fascinante mundo de Linux. ¡Empecemos!

Nos diriguimos a la siguiente pagina [over the wire](https://overthewire.org/wargames/bandit/), nos llevara a esta pagina:

![Menu](/img/level0/bandit0Menu.png)

# Level 0 -> Level 1

Aquí puedes leer más sobre lo que trata Bandit y en qué consiste. Nos dirigiremos al nivel 0, donde podemos ver las instrucciones para acceder como bandit0 y conectarnos al servidor mediante el comando SSH. Una vez que hemos leído las instrucciones, pasamos al siguiente nivel. En el siguiente nivel, podemos observar que nos dan las siguientes instrucciones.

![bandit0](/img/level0/bandit0.png)

Aquí ya podemos observar que las instrucciones nos indican que la contraseña para el siguiente nivel se encuentra en un archivo llamado "_readme_", localizado en el directorio home de nuestro usuario "_bandit0_". Vamos a confirmarlo. Como aún no me he conectado al juego, vamos a hacerlo.

En el nivel 0 se especifica que se debe usar `ssh` para acceder al servidor. Nos proporcionan un nombre de host, un puerto y la contraseña. La estructura del comando para acceder al nivel cero es la siguiente: `ssh bandit0@bandit.labs.overthewire.org -p 2220`. Si es nuestra primera vez usando el comando ssh, nos preguntará si estamos seguros de acceder al servidor. Entonces, escribimos 'Y/y' o simplemente "yes". A continuación, nos pedirá la contraseña del usuario bandit0, la cual es **bandit0**.

Una vez dentro del servidor, comprobamos que somos el usuario bandit0 con el comando `whoami`. Este comando nos sirve para saber qué usuario está usando el sistema actualmente y, si todo está bien, podemos observar claramente que se trata del usuario "bandit0". Posteriormente, escribimos el comando `ls` para listar el contenido de nuestro directorio home y ahí es donde se encuentra el archivo "_readme_" que contiene la contraseña para acceder a "bandit1". Escribimos el comando `cat readme` para leer el contenido de este archivo y, como se puede observar, esa es la contraseña para el siguiente nivel, la copiamos en nuestro portapapeles y del servidor con el comando `exit`

![level-0](/img/level0/level0.png)

# Level 1 -> Level 2

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

# Level 2 -> level 3

![instructions](/img/level2/instructions.png)

Para este nivel, observamos que hay un archivo llamado "_spaces in this filename_". Para poder leer este tipo de archivos con espacios, necesitamos escapar cada espacio con el carácter especial barra inversa `\`, quedando así el comando: `cat spaces\ in\ this\ filename`. De igual forma, podemos ahorrarnos esto usando la tecla tab, la cual nos autocompleta lo mencionado anteriormente.

Otra forma de hacer este proceso es usando comillas dobles, quedando de esta manera: `cat "spaces in this filename"`. De esta forma le indicamos el nombre del archivo.

Pero además de hacer eso, también podemos ahorrarnos escribir el nombre. Para hacer esto más rápido, hacemos uso del carácter especial asterisco `*`, quedando así el comando: `cat *filename`. De esta forma, le indicamos que queremos leer todos los archivos que terminen en "filename". Igualmente, se puede modificar el orden del asterisco, por ejemplo: `cat spaces*`, aquí se indica que queremos leer todos los archivos que comiencen con el nombre "spaces". 

Cabe aclarar que este comando es mejor usarlo cuando sabemos que solo existe un archivo con ese nombre; en caso contrario, listará el contenido de todos los archivos que encuentre con el nombre _spaces_.

![level-2](/img/level2/level2.png)

Ahora que tenemos la contraseña nos dirigimos al siguiente nivel.

# Level 3 -> Level 4

Para este nivel la contraseña esta guardada en un archivo oculto dentro del directorio "inhere"

Este nivel es muy simple, si listamos el contenido de la carpeta con el comando `ls`, sabremos que a simple vista nos e ve nada, para ello vamos a hacer uso de los parametros de dicho comando, usaremos el parametro `-a` para listar todo lo que se encuentre dentro del directorio quedando asi el comando: `ls -a inhere`. Y ahora podemos observar que hay un archivo con el nombre "...Hiding-From-You", con el comando cat revisamos el contenido y tendremos la contraseña.

![Level-3](/img/level3/download.png)

# Level 4 -> level 5

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

# Level 5 -> 6

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

# Level 6 -> 7

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

# Level 7 -> 8

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

dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

# Level 8 -> 9

Para este nivel nos indica que la contraseña esta guardada en el archivo "_data.txt_" y nos indica que es la unica linea que no se repite, si nosotros verificamos el contenido que hay dentro vamos a observar que nada tiene sentido no podemos saber cual es la contraseña, entonces lo que vamos a hacer es usar el comando `uniq` combinado con el comando `sort`.

![ejemplo-1](/img/level8/text.png)

El comando `sort`: nos va a permitir ordenar las lineas, lo toma en cuenta en cuestion de la primera letra, si es un numero con el numero 0, si es letra con la letra 'a'

![ejemplo-1.1](/img/level8/sort.png)

El comando `uniq`: nos ayudara a saber cual es la unica letra que no se repite en el texto.

Este es el comando que vamos a utilizar:

`sort data.txt | uniq -u`

dando la contraseña en cuestion y nos pasamos al siguiente nivel.

![ejemplo-2](/img/level8/pass.png)

# Level 9 -> 10

Para este nivel nos indica que la contraseña se encuentra almacenada en un archivo "_data.txt_" y la contraseña se encuentra ubicada seguida de las unicas palabras que son humanamente legibles.

Lo que nos dice esto es que si leemos el contenido del archivo lo que vamos a encontrar es texto que no se entiende, entonces lo que vamos a hacer es usar el comando `strings`:

Contenido del archivo:

![file-data](/img/level8/data.png)

`strings`: Este comando nos listara todas las partes del archivo que son texto.

![strings_command](/img/level8/strings.png)

Podemos ver que nos ha filtrado las cadenas que son de texto, y aunque en su mayoría no se entiende, podemos ver una que dice “the”, y como el nivel nos decia, que la contraseña estaba en un valor con signos de igual, así que filtraremos con grep las lineas que tengan simbolos de igual:

`strings data.txt | grep "===="`

Vemos que nos a dado la contraseña, pero de igual manera podemos aplicar mas modificaciones a nuestro comando para obtener un texto mas claro y simplemnte sea la contraseña, por ejemplo:

Usando el comando `string data.txt | grep "====" | tail 1` hacemos que unicamente nos de la parte de de la ultima linea, ahora tambien haciendo esto podemos jugar de nuevo con el comando `awk` con el uso de parametros, entonces vamos a decirle a agregarle a nuestra salida que unicamente queremos el ultimo parametro que es donde se encuentra la contraseña, quedando asi el comando: 

`string data.txt | grep "====" | tail -1 | awk 'NF{print$NF}'`

Y esto nos dara la contraseña.

![pass](/img/level9/pass.png)


flag _(checkpoint)_: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey


# Level 10 -> level 11

Ahora este nivel es bastante facil ya que unicamente nos indica que hay que decodificar un archivo que contiene texto en base64, por lo tanto unicamente vamos a utilizar el comando `base64 -d`, el parametro -d quiere decir "decode"

por lo tanto el el comando seria el siguiente:

`cat data.txt | base64 -d`

Y como podemos ver tenemos la contraseña, nos dirigimos al siguiente nivel.


![password](/img/level10/pass.png)

# Level 11 -> level 12

Para este nivel nos dice que la contraseña esta siendo rotada en 13 posiciones, para poder entender esto les dare una explicaion acerca del cifrado cesar, ya que asi podriamos entender mejor el comando que vamos a usar.

## Cifrado Cesar:

Vamos a utilizar la palabra "hola" de prueba y la vamos a rotar en 5 posiciones, y la forma en la que lo vamos a hacer es la siguiente:

teniendo en cuenta que tenemos la palabra hola, vamos a posicionar la letra inicial en el abecedario, quedando como la posicion de la 'M' en 0 y pasamos a contar 5 letras en adelante, llegando hasta la letra 'M', esto significa que vamos a intercambiar la letra 'H' con la 'M' y repetimos el proceso en cada letra vamos a empezar desde cero, quedando asi "_hola_" en forma cifrada "_mtpf_"

![Caesar Chiper]((img/level11/CaesarCode.png))

Si queremos decodificar el texto simplemente aplicamos todo al inversa, empezamos desde la letra "_M_" y contamos en reversa hasta llegar a 5, y podemos ver que es hasta la letra "_H_" y repetimos el proceso para las siguientes letras

![Decode](/img/CaesarDecode.png)


Bueno una vez entenido esto pasamos de nuevo a resolver el nivel de bandit; Vamos a leer el contenido del archivo y ahora sabiendo que este texto hay que decodificarlo usando 13 posiciones vamos a usar el comando `tr`. 

`tr`: es utilizado para eliminar caracteres o traducirlos de una entrada.

El comando a utilizar es el siguiente:

`cat data.txt | tr '[G-ZA-Fg-za-f]' '[T-ZA-St-za-s]'`

Ahora quiero explicar que es exactamente los parametros del comando `tr`.

* `[G-ZA-Fg-za-f]`: Esto es el conjunto de caracteres que quiero traducir:
    * `G-Z`: Todos los caracteres desde la 'G' hasta la 'Z'
    * `A-F`: Todos los caracteres desde la 'A' hasta la 'F'

Aplicando los mismo para el letras minisculas y lo mismo para el siguiente parametro del comando tr. Le damos enter y podemos observar la contraseña

![password]((/img/level11/pass.png))


# Level 12 -> Level 13


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


. . .

