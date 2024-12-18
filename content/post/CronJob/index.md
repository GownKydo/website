+++
title = 'Administracion de tareas cron'
date = 2024-06-06
categories = [
    "Linux",
    "Bash",
    "Automatización",
    "CyberSecurity",
    "Sistemas Operativos",
]
tags = [
    "Cron",
    "Automatización",
    "Linux",
    "Scripting",
    "Tareas Programadas",
    "Administración de Sistemas",
    "Seguridad Informática",
    "DevOps",
]
image = "CronJob.jpg"
+++

<br>

## ¡Hola a todos!

En esta ocasión, vamos a abordar el fascinante tema de las tareas cron, como se indica en el título. Para comenzar, vamos a adentrarnos en el concepto de qué es una tarea cron y su importancia en la administración de sistemas

## ¿Qué es una tarea cron?

Cron es un demonio que ejecuta comandos en horarios definidos por el administrador. Está diseñado para simplificar tareas repetitivas que, de otro modo, tendrían que ejecutarse manualmente.

Cada tarea gestionada por cron es conocida como un **"cron job"**, la cual se especifica en una tabla llamada **"cron tab"**. Cada línea en la crontab representa una tarea y consta de una combinación de hora y fecha seguida del comando a ejecutar. Estas tareas pueden ejecutarse en segundo plano, permitiendo que los comandos se ejecuten automáticamente en el momento deseado por el administrador.

### Limitaciones de una tarea cron

A pesar de sus beneficios cron tiene sus limitaciones.

1. **Ejecucion en redes distribuidas:** Cron no está diseñado para ejecutarse en una red distribuida, lo que significa que no puede coordinar tareas entre varios servidores o terminales de red. Esta limitación puede ser un inconveniente en entornos de alta disponibilidad y sistemas distribuidos.
2. **Capacidades avanzadas de gestion:** Aunque cron es una herramienta poderosa y sencilla, no cuenta con capacidades avanzadas para la gestión de tareas, como el manejo de dependencias entre tareas o la detección y recuperación automática de fallos. Esto puede limitar su uso en sistemas más complejos donde estas características son esenciales.

### Estructura de una tarea cron

Las tareas cron tienen la siguiente estrucutra, estan divididas en 5 grupos y dos mas que identifican que usuario esta ejecutando la tarea y el comando o script que se esta corriendo.

| <center> minutes </center> | <center> hours </center> | <center> day month </center> | <center> month </center> | <center> day week </center> | <center> user </center> | <center> script/command </center>        |
| -------------------------- | ------------------------ | ---------------------------- | ------------------------ | --------------------------- | ----------------------- | -------------------------------- |
| <center> 0-59 </center>    | <center> 0-23 </center>  | <center> 1-31 </center>      | <center> 1-12 </center>  | <center> 0-6 </center>      | <center> user </center> | <center> /path/test.sh </center> |
| <center>  * </center>      | <center> * </center>     | <center> * </center>         | <center> * </center>     | <center> * </center>        | <center>  </center>     |                                  |


**Caracteres especiales:**

Tambien tenemos los caracteres especiales, los cuales nos ayudar a facilitar la redaccion de las tareas o crear procesos mucho mas complejos y como tal mucho mas precisos.

| <center> Caracter </center> | <center> Definicion </center> |
| -------------------- | -------------------------------------------- |
| <center> * </center> | Rellena un campo sin ningun valor especifico |
| <center> / </center> | Especificar un intervalo de tiempo           |
| <center> , </center> | Seleccionar multiples valores|
| <center> - </center> | Especificar un rango especifico|

Una vez sabemos todo esto, ya podremos empezar a crear nuestras propias reglas. Pero es probable que, si queremos hacer alguna muy compleja, sea necesario tener algunos conocimientos de programación. Sobre todo, para comprender la estructura de cómo se va a ejecutar alguna tarea concreta. Y en caso de que falle, sabes donde se puede estar produciendo el problema en cuestión.

## Practicando con tareas cron

_Es importante mencionar que las pruebas de esta práctica se realizan en sistemas operativos basados en Arch. Por lo tanto, algunos comandos pueden diferir de aquellos utilizados en otros sistemas operativos basados en Debian o sistemas basados en RHE(red hat enterprise)._

Para empezar, debemos convertirnos en usuarios root para poder administrar las tareas cron. Una vez con permisos de root, navegamos a la ruta `/etc/cron.d`, donde se encuentran las tareas. Dentro del directorio, verificaremos el estado de nuestro demonio cron con el siguiente comando: `systemctl status cronie`. En sistemas basados en Debian, se debe cambiar la palabra _cronie_ por _cron_, o de igual forma pueden usar el siguiente comando `service cron status`. Una vez escrito el comando, obtendremos el siguiente resultado:

```bash
● cronie.service - Command Scheduler
     Loaded: loaded (/usr/lib/systemd/system/cronie.service; enabled; preset: disabled)
     Active: active (running) since Fri 2024-06-07 16:04:45 EST; 8s ago
   Main PID: 6880 (crond)
      Tasks: 1 (limit: 6988)
     Memory: 888.0K (peak: 1000.0K)
        CPU: 3ms
     CGroup: /system.slice/cronie.service
             └─6880 /usr/sbin/crond -n

Jun 07 16:04:45 kinghost systemd[1]: Started Command Scheduler.
Jun 07 16:04:45 kinghost crond[6880]: (CRON) STARTUP (1.7.2)
Jun 07 16:04:45 kinghost crond[6880]: (CRON) INFO (Syslog will be used instead of sendmail.)
Jun 07 16:04:45 kinghost crond[6880]: (CRON) INFO (RANDOM_DELAY will be scaled with factor 92% if used.)
Jun 07 16:04:45 kinghost crond[6880]: (CRON) INFO (running with inotify support)
Jun 07 16:04:45 kinghost crond[6880]: (CRON) bad command (/etc/cron.d/0hourly)
Jun 07 16:04:45 kinghost crond[6880]: (CRON) INFO (@reboot jobs will be run at computer's startup.)
```

Aquí podemos notar que el servicio ya está activado. Si en tu sistema está desactivado, escribe el siguiente comando para activarlo: `systemctl start cronie`. En sistemas de debian tambien podemos usar esta alternativa `service cron start`. Posteriormente, vuelve a escribir el comando para verificar el estado de nuestro demonio cron y ya debería estar activo.

### Creando una tarea cron

Ahora vamos a crear una tarea cron. Para este caso, dentro de la ruta en la que estamos que es `/etc/cron.d`, crearemos un archivo que puede llevar el nombre que desees. En mi caso, lo llamaré "_tarea_". Escribiremos el siguiente comando para crear el archivo: `touch tarea`

Luego, procedemos a abrirlo con el editor de texto de preferencia y una vez dentro, escribimos la estructura de una tarea cron, que está dividida en cinco campos como lo explique anteriormente, colocare los 5 campos con asteriscos, esto le indica a el servicio cron que quiero que se ejecute cada minuto. Esta seria la estructura de nuestro archivo:

```bash
* * * * * root /home/gerardokydo/Desktop/file.sh
```

Y como sabemos que este archivo "file.sh" no existe, vamos a crearlo. Nos dirigimos a la ruta "Desktop" de nuestro usuario normal y creamos el archivo usando el comando `touch file.sh`. Una vez que el archivo esté creado, le daremos permisos de ejecución con el siguiente comando: `chmod +x file.sh`. Luego procedemos a editarlo con nuestro editor preferido y escribimos la tarea que deseamos que realice. A modo de ejemplo, escribimos lo siguiente:

```bash
#!/bin/bash

sleep 10
rm -rf /tmp/*

```

En este script, `sleep 10` hace una pausa de 10 segundos y `rm -rf /tmp/*` borra todos los archivos en el directorio `/tmp/`. Guardamos el archivo y en este punto nuestro demonio cron debería estar ejecutándose correctamente.

## Abuso de tareas cron

Es importante destacar que, en términos de seguridad, es crucial administrar adecuadamente el acceso al sistema cron. Cualquier usuario con permisos puede modificar su propio archivo crontab, lo que podría permitir la ejecución de comandos con privilegios de usuario. Por lo tanto, se recomienda limitar el acceso a cron solo a usuarios autorizados y revisar regularmente los archivos de crontab para evitar abusos o errores.

A continuación, presentamos un ejemplo de abuso de tareas cron. Este ejemplo se realiza con fines educativos en un entorno controlado y sin afectar a nadie. La intención es demostrar cómo un uso indebido de cron puede comprometer la seguridad del sistema y cómo podemos prevenirlo mediante buenas prácticas.

### Deteccion de tareas cron

Vamos a realizar una detección de tareas cron con el objetivo de buscar archivos en la raíz que puedan ser modificados por un usuario sin permisos de root. Esto se puede hacer de dos formas: manualmente mediante un script en bash, o utilizando una herramienta en Linux llamada **pspy** que está escrita en Go. Sin embargo, para entender mejor cómo detectar tareas cron, lo haremos de forma manual, lo que también nos ayudará a comprender la lógica subyacente.

Para esta ocasión, vamos a utilizar el comando `ps`. Este comando, con ciertos parámetros, puede listar los comandos que se están ejecutando en tiempo real en el sistema, lo cual es muy útil para monitorear y detectar tareas cron. Además, utilizaremos el comando `diff`, que permite comparar dos archivos y mostrar sus diferencias. Esta combinación de herramientas nos ayudará a identificar cambios en los procesos y archivos del sistema. Si quieres saber mas acerca de los comandos y sus diferentes parametors les dejare al final del blog el manual page de cada uno de los comandos presentados en este post.

Continuemos. Vamos a crear un archivo en nuestro escritorio con el siguiente comando: `touch MonitorProcess.sh`, le asignamos los permisos de ejecucion con el siguiente comando: `chmod +x MonitorProcess.sh`

Luego, lo abrimos con el editor de texto de nuestra preferencia. Una vez dentro del archivo, escribimos el siguiente código:

``` bash
#!/bin/bash

old_process=$(ps -eo command)

while true; do
    new_process=$(ps -eo command)
    
    diff_result=$(diff <(echo "$old_process") <(echo "$new_process"))
    echo "$diff_result" | grep "[\>\<]" | grep -v "kworker"
    
    old_process=$new_process
    
done


```

Una vez tengamos el codigo, vamos a repasar lo que hemos escrito:

1. Empezamos definiendo las cabeceras principales de nuestro codigo las cuales se identifican al inicio del mismo `#!/bin/bash.` 
<br>

3. Creamos una variable llamada "_old_process_" la cual va a guardar el output de nuestro comando `ps -eo command`. Si escribimos dicho comando desde nuestra terminal tendremos los procesos listados que se estan ejecutando en tiempo real. 
<br>

5. Creamos un bucle while infinito para ir actualizando los cambios de los procesos:

	1. Dentro de este mismo bucle, creamos una variable llamada "_new_process_" la cual va a guardar los nuevos procesos que vayan apareciendo.
	<br>
	3. Haciendo uso del comando `diff`  creamos una nueva variable llamada "_diff_result_" que guardara el output del comando diff, a este comando le pasamos por parametros que evalue la diferencia de las variables "_old_process_" y "_new_process_"
	<br>
	4. Posteriormente con el comando `echo` imprimimos el contenido de nuestra variable "_diff_result_" y con la ayuda del comando `grep` y el parametro `-v` filtramos los procesos que se *cierran(<)* y los que se *abren(>)* tambien filtramos por los procesos no deseados para que no los tome en cuenta, en mi caso todos aquellos que contiene la palabra "_kworker_"
	<br>
	5. Y para concluir con el programa solo actualizamos nuestra variable "_old_process" igualadnola a nuestra variable "_new_process_".

Una vez que tengamos pasando este punto procedemos a correr el codigo y si esperan un tiempo podran notar que este estara listando los procesos que se estan ejecutando en tu sistema, esto va desde configuraciones que has hecho, aplicaciones abiertas, pero lo que nos va a importar es cuando aparezca algo relacionado a las tareas cron, por ejemplo lo siguiente:

```bash
< /usr/sbin/CROND -n
< /bin/bash /home/gerardokydo/Desktop/file.sh
< sleep 10
> (udev-worker)
> /bin/sh /usr/bin/tlp auto
> /usr/bin/perl /usr/share/tlp/tlp-readconfs --outfile /run/tlp/tlp-run.conf_tmp9CBkvC
< /usr/bin/perl /usr/share/tlp/tlp-readconfs --outfile /run/tlp/tlp-run.conf_tmp9CBkvC
> /bin/sh /usr/bin/tlp auto
> cat /sys/class/power_supply/AC/online
< /bin/sh /usr/bin/tlp auto
< cat /sys/class/power_supply/AC/online
< /bin/sh /usr/bin/tlp auto
```

En mi caso, estos fueron los procesos que se listaron. El más relevante es el que se encuentra en las primeras líneas, donde podemos observar que se está ejecutando el demonio `/usr/sbin/CROND -n` y, a su vez, este ejecuta nuestro archivo "_file.sh_" almacenado en nuestro escritorio. Recordarán que este archivo hace un `sleep 10` y posteriormente borra todo lo que está en la carpeta "_/tmp/_".

Ahora, suponiendo que soy un atacante y noto este registro de procesos, investigaría más acerca de este fichero. Por lo tanto, escribiría el siguiente comando: `ls -l /home/gerardokydo/Desktop/file.sh`, lo que me dara el siguiente resultado: 

`-rwxr-xrwx 1 gerardokydo gerardokydo 36 Jun 7 /home/gerardokydo/Desktop/file.sh`

Podemos observar que el propietario de este archivo ha habilitado la edición del archivo para el grupo "otros". Esto significa que cualquier usuario en el sistema, independientemente de sus permisos, puede modificar este archivo. Como un usuario no privilegiado, puedo explotar esta configuración incorrecta de permisos para obtener privilegios elevados.

Primero, nos dirigimos a la ruta donde se encuentra el archivo. Dado que el archivo está siendo ejecutado por el usuario root, podemos cambiar su contenido para ejecutar comandos con privilegios de root. Esto es una vulnerabilidad seria que permite a un usuario no autorizado ejecutar acciones que normalmente estarían restringidas.

Para modificar el contenido del archivo, utilizamos el siguiente comando:

```bash
#!/bin/bash

chmod 4775 /bin/bash

```

Este script le asigna privilegios **SUID** a nuestra shell. El bit **SUID** permite que un archivo ejecutable se ejecute con los permisos del propietario del archivo, en este caso, root. Guardamos los cambios y salimos del archivo

Si ahora escribimos `ls -l /bin/bash`, vamos a notar los privilegios, que se verían de la siguiente manera:

`rwxr-xr-x root root 1.1 MB Tue Jan 23 16:22:43 2024 /bin/bash`

Para monitorear los cambios en los permisos, utilizaremos el comando `watch -n 1 ls -l /bin/bash`, que actualizará la visualización cada segundo para mostrar el cambio en los permisos realizado por el script. Notaremos una letra 's' en los permisos:

`-rwsrwxr-x 1 root root 1112784 Jan 23 16:22 /bin/bash`

Esto sucede porque ahora **SUID** está activado. Esto nos permite ejecutar el binario con los permisos del propietario del archivo, en este caso, root.

Para lanzar una shell con los privilegios del propietario (root), escribimos `bash -p`. Al presionar Enter, veremos que ahora somos usuario root. Podemos confirmarlo con el comando `whoami`.

Con esto, hemos demostrado la importancia de una correcta configuración de las tareas cron. Si un atacante detecta archivos que se están ejecutando con permisos inadecuados, puede explotarlos para obtener privilegios elevados. Es crucial asegurar que los permisos estén correctamente configurados para prevenir intrusiones por parte de usuarios no autorizados.

<br>

## Referencias

* [systemctl(1) — Linux manual page](https://www.man7.org/linux/man-pages/man1/systemctl.1.html)

* [ps(1) — Linux manual page](https://www.man7.org/linux/man-pages/man1/ps.1.html).

* [diff(1) — Linux manual page](https://www.man7.org/linux/man-pages/man1/diff.1.html)

* [grep()1 — Linux manual page](https://www.man7.org/linux/man-pages/man1/grep.1.html)

* [watch(1) — Linux manual page](https://www.man7.org/linux/man-pages/man1/watch.1.html)
