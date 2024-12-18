+++
title = 'Aprendiendo a usar Docker'
description = "introducción completa para comenzar a trabajar con contenedores de manera eficiente"
date = 2024-12-17
categories = [
    "Linux",
    "Docker",
    "Bash",
    "Tutorial",
    "Contenedores",
    "DevOps",
    "Virtualización",
]
tags = [
    "Docker",
    "Bash",
    "Linux",
    "Contenedores",
    "Virtualización",
    "Automatización",
    "Desarrollo",
    "Microservicios",
    "DevOps",
]
image = "Docker.png"
+++


# ¿Que es docker?

Docker es una plataforma que permite crear, desplegar y ejecutar aplicaciones en **contenedores**. Los contenedores son entornos ligeros y aislados que incluyen todo lo necesario para ejecutar una aplicación (código, dependencias, configuraciones). Esto garantiza que las aplicaciones se ejecuten de manera consistente en cualquier entorno, sin importar el sistema operativo o la infraestructura.

## Ventajas clave:

- **Portabilidad**: Docker garantiza que una aplicación se ejecute de la misma manera en cualquier entorno, ya que los contenedores incluyen todo lo necesario para la ejecución (código, dependencias, etc.). Esto facilita mover aplicaciones entre diferentes sistemas operativos y plataformas (como Windows, macOS, Linux, servidores, o la nube) sin problemas. 
<br>

- **Aislamiento**: Cada contenedor es independiente, lo que significa que las aplicaciones no interfieren entre sí, incluso si usan diferentes versiones de dependencias o bibliotecas
<br>

- **Eficiencia**: Docker es más eficiente que las máquinas virtuales (VM) porque comparte el núcleo del sistema operativo en lugar de ejecutar un sistema operativo completo para cada instancia. Esto hace que los contenedores sean más ligeros, rápidos de iniciar y con menos consumo de recursos, lo que permite ejecutar más aplicaciones en el mismo hardware.

## Comparativas entre docker y una maquina vitual

|**Caracteristicas**|**Docker**|**Virutal Machine**|
| --- | --- |---|
|**_Uso de recursos_**|_Comparten el nucleo del SO_|_Requiere un SO completo_|
|**_Arranque_**|_En segundos_|_En minutos_|
|**_Aislamiento_**|_Tiene su propio entorno_|_Aislado, pero con un sistema completo_|
|**_Escalabilidad_**|_Escalable rapidamente_|_Requiere mas recursos y tiempo_|
|**_Portabilidad_**|_Se mueve entre plataformas rapidamente_|_Requiere que la VM sea compatible con el hipervisor_|


Docker facilita el desarrollo, pruebas y despliegue de aplicaciones, asegurando que funcionen de la misma manera en cualquier lugar.


# Instalar docker en nuestro sistema

## Instalacion en debian y derivados

Si estás utilizando un sistema basado en Debian, como **Ubuntu** o **Linux Mint**, te proporcionaré una guía paso a paso para instalar Docker y verificar que todo esté funcionando correctamente.

1. **Accede como usuario root**
```bash
sudo su
```

3. **Actualizar el sistema e instalar dependencias necesarias** 
```bash
apt update && apt install -y \ apt-transport-https \ ca-certificates \ curl \ software-properties-common
```

2. **Agrega la clave GPG oficial de Docker**
```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

3. **Añade el repositorio de Docker a tus fuentes de paquetes**
```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
```

4. Actualizar de nuevo el sistema e instalar docker
```bash
apt upgrade && apt install docker 
```

5. **Verificar que se haya instalado correctamente y verificacion del estado de docker**

## Instalacion en Arch y derivados

Para empezar a aprender Docker en un sistema basado en Arch Linux, te proporcionaré una guía paso a paso para que puedas instalar y comenzar a usar Docker.

1. **Accede como usuario root**
```bash
sudo su
```

3. **Instala Docker y actualiza el sistema**
```bash
pacman -Sy docker && pacman -Syu
```

5. **Verifica que Docker se haya instalado correctamente y verificar su estado**
```bash
docker --version && systemctl status docker 
```


## Instalacion en sistemas basados en windows

Si estás utilizando **Windows** y deseas instalar Docker, te proporcionaré una guía sencilla y clara para hacerlo. Docker es una herramienta popular para la creación y gestión de contenedores, y ahora puedes usarlo en tu máquina con Windows fácilmente.


1. **Nos dirigimos a la pagina oficial de docker para hacer la instalacion: [Download Docker](https://docs.docker.com/desktop/setup/install/windows-install/)**
<br>

3. **Instalacion de WSL_(Windows Subsystem for Linux)_**
	* Abrimos la terminal de **powershell** en modo administrador y escribimos el siguiente comando: 
		<center>
		```powershell 
		wsl --list --online 
		```
		</center>
		Este comando es unicamente para listar la distribucion que mas nos guste, por defecto se instala **Ubuntu**
		Pero yo recomiendo instalar debian, entonces escribimos el siguiente comando:
		<center>
		```powershell 
		wsl --install -d debian
		```
		</center>
		Una vez terminada la instalacion verificamos que version de WSL estamos utilizando, con el siguiente comando:
		<center>
		```powershell 
		wsl -l -v
		```
		</center>
		Una vez que sabemos que ya esta instalado correctamente seguimos con la instalacion de docker.
<br>
1. **Instalacion de docker desde el command promt**

Para este paso ya tenemos la opcion de descargar docker de dos formas distintas, una es seguir una instalacion de forma interactiva y la otra es a pura terminal, nosotros lo haremos desde terminal todo

Vamos a abrir una terminal de **poweshell** y vamos a ejecutar el siguiente comando: 

```poweshell
Start-Process 'Docker Desktop Installer.exe' -Wait -ArgumentList 'install', '--backend=wsl-2', '--accept-license'

```

### Explicación:

- **`Start-Process`**: Lanza el proceso de instalación.
- **`-Wait`**: Hace que PowerShell espere a que el proceso de instalación termine antes de continuar.
- **`-ArgumentList`**: Aquí es donde agregamos las flags para la instalación:
    - `'install'`: Comando básico de instalación.
    - `'--backend=wsl-2'`: Establece WSL 2 como el backend para ejecutar los contenedores (esto garantiza que Docker use WSL 2 en lugar de Hyper-V o Windows Containers).
    - `'--accept-license'`: Acepta la licencia de Docker de manera automática durante la instalación.

Este comando debería permitirte instalar Docker Desktop con **WSL 2** como backend y aceptar la licencia automáticamente, todo sin intervención manual.

Cuando ejecutes este comando en PowerShell como administrador, Docker Desktop debería instalarse correctamente con la integración de **WSL 2**.
<br>

> Si tu cuenta de administrador es diferente a la de tu usuario, deberas agregar tu usuario a el grupo de docker, para porder usarlo en otra cuenta ademas de root, este es el comando que se va a utlizar: `net localgroup docker-users <tu_user> /add`


# Comandos basicos para usar docker

## Probando Docker


Primero verificamos el estatus del demonio de docker, eso lo verificamos con el siguiente comando:

Este comando muestra el estado del servicio, y te indicará si Docker está activo (corriendo) o inactivo (detenido).

```bash
systemctl status docker
```

De igual forma podemos verificar la version de docker con la que estamos trabajando, para eso podemos escribir el siguiente comando y este nos dara la version de docker con la cual estamos trabajando, comando:

```bash
docker --version
```

### Modos de activacion de Docker

Si notamos que el demonio de docker esta inactivo simplemente lo activamos con el siguiente comando:

```bash
sudo systemctl start docker
```

Si por alguna razón necesitamos detener el servicio de Docker, podemos hacerlo con el siguiente comando:

```bash
sudo systemctl stop docker
```

Este comando detendrá el servicio de Docker, lo que significa que no podrás ejecutar ni interactuar con contenedores hasta que lo vuelvas a activar.

Si, en cambio, prefieres asegurarte de que Docker se inicie automáticamente cuando inicies el sistema o reinicies el mismo, puedes habilitarlo con:

```bash
sudo systemctl enable docker
```

Y si por alguna razon deseas desactivar Docker de Forma Permanente o que no se inicie automaticamente cuando se inicie o reinicie el sistema, puede hacerlo con el siguiente comando:

```bash
sudo systemctl disable docker
```

Esto deshabilitará Docker en el inicio del sistema, lo que significa que deberás iniciarlo manualmente en cada reinicio, si lo deseas.


## Funcionalidades de Docker

Ejecuta el siguiente comando para verificar que Docker está funcionando correctamente; Este comando descargará una imagen de prueba y ejecutará un contenedor que imprimirá un mensaje de éxito si Docker está bien configurado.

```bash
docker run hello-world
```

**¿Qué sucede cuando ejecutas este comando?**

- **Docker descarga la imagen**: Si no tienes la imagen `hello-world` en tu máquina, Docker automáticamente la descargará desde Docker Hub, que es el registro oficial de imágenes de Docker.
<br>
- **Ejecuta el contenedor**: Una vez descargada, Docker crea y ejecuta un contenedor basado en esta imagen.
<br>
- **Muestra un mensaje**: El contenedor ejecuta su aplicación (en este caso, una simple aplicación que imprime un mensaje) y luego termina su ejecución. Verás un mensaje similar al siguiente en la terminal:

### Ver el uso de recursos

Para ver el uso de recursos del sistema por parte de Docker (incluyendo contenedores, imágenes y volúmenes), puedes usar:

```bash
docker system df
```

Este comando te mostrará el espacio utilizado por cada categoría (contenedores, imágenes, volúmenes).

## Crear un contenedor 

**Crear y ejecutar un contenedor Basico**
Una vez que tienes la imagen de Ubuntu descargada, puedes crear y ejecutar un contenedor a partir de ella con el siguiente comando:

```bash
docker run -it ubuntu
```

- `run` le dice a Docker que ejecute un contenedor.
- `-it` es una combinación de dos opciones:
- `-i` (interactive): Mantiene el contenedor en ejecución en modo interactivo.
- `-t` (tty): Asigna un terminal para que puedas interactuar con el contenedor.
- `Debian` es el nombre de la imagen que acabamos de descargar.

### Construir una imagen de docker

Si deseas crear un contenedor para tu proyecto, necesitarás construir una imagen personalizada a partir de tu aplicación y sus dependencias. A continuación, te muestro cómo hacerlo.

#### Crear un archivo `Dockerfile`

Primero, necesitas un archivo `Dockerfile` en tu directorio raíz del proyecto. Este archivo describe los pasos para construir la imagen de docker, un `Dockerfile` típico podría verse así:

```dockerfile
# Usar una imagen base de Python
FROM python:3.12-slim

# Establecer el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar todos los archivos del proyecto al contenedor
COPY . /app

# Instalar las dependencias de Python desde el archivo requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Exponer el puerto en el que la aplicación estará corriendo (suponiendo que uses Flask en el puerto 5000)
EXPOSE 5000

# Comando para ejecutar la aplicación cuando el contenedor se inicie
CMD ["python", "run.py"]
```

#### Construir la imagen de Docker

Una vez que tengas tu `Dockerfile`, debes construir la imagen utilizando el siguiente comando:

```bash
docker build -t <name> .
```

- `docker build`: Le indica a Docker que construya una imagen.

- `-t <name>`: Asigna un nombre a la imagen (en este caso, `name`).

- `.`: Indica que Docker debe buscar el `Dockerfile` en el directorio actual.

Este comando creará una imagen Docker basada en la configuración definida en el `Dockerfile`.

#### Ejecutar el contenedor

Una vez que la imagen se ha construido correctamente, puedes ejecutar un contenedor a partir de ella con:

```bash
docker run -p 5000:5000 <name>
```

- `-p 5000:5000`: Mapea el puerto 5000 del contenedor al puerto 5000 de tu máquina local, lo que te permitirá acceder a la aplicación en `http://localhost:5000`.

- `name`: El nombre de la imagen que acabas de crear.

Al ejecutar este comando, Docker iniciará un contenedor basado en la imagen, ejecutará tu aplicación y podrás acceder a ella desde el navegador.

## Ver los contenedores activos

Para ver qué contenedores están en ejecución, usa el siguiente comando:

```bash
docker ps
```

Esto mostrará una lista de contenedores activos. Si el contenedor está detenido, no aparecerá en esta lista. Si quieres ver todos los contenedores, incluidos los detenidos, usa el siguiente comando:

```bash
docker ps -a
```

### Activar un contenedor

tienes un contenedor que está detenido y deseas iniciarlo (activarlo), puedes usar el comando `docker start`. Para esto, necesitas el **ID** o **nombre** del contenedor, como por ejemplo el sigiente ejemplo:

```bash
docker start <container_id_or_name>
```

### Desactivar un contenedor 

Cuando termines de trabajar con un contenedor y quieras detenerlo, usa el siguiente comando:

```bash
docker stop <container_id_or_name>
```

Este comando detiene un contenedor en ejecución de manera segura, pero si el contenedor no responde o se encuentra en un estado no controlado, puedes usar el siguiente comando para forzar su detención:

```bash
docker kill <container_id_or_name>
```

## Eliminar un contenedor

Si un contenedor ya no es necesario y deseas liberarlo de tu sistema, puedes eliminarlo con el siguiente comando:

```bash
docker rm <container_id_or_name>
```

Este comando elimina el contenedor especificado de manera permanente. Para eliminar varios contenedores a la vez, puedes usar el siguiente comando:

```bash
docker rm -f $(docker ps -a -q)
```

* `docker ps -a -q`: Lista todos los ID de los contenedores (detenidos o activos), y el comando `docker rm` los elimina todos.

<br>

> Si intentas eliminar un contenedor que está en ejecución, Docker no te permitirá hacerlo hasta que lo detengas primero. Para eliminar contenedores activos de manera inmediata, puedes usar `docker rm -f`.


# Conclusion

Con estos pasos, habrás instalado y configurado Docker en tu sistema. Ahora puedes comenzar a trabajar con contenedores y explorar todo lo que Docker tiene para ofrecer!.

<br><center> Nos vemos en el siguiente post!! </center>