# MySQL Server en Ubuntu


- [Instalación MySQL Server desde el gestor de paquetes](#1)

    - [Versión estable que se instala desde el repositorio.](#2)


- [El servicio o demonio de mysql que arranca/reinicia/para el núcleo](#3)

    - [EL directorio del servicio o proceso de demonio.](#4)


- [Instalación MySQL Cliente en el Servidor](#5)

- [Instalación MySQL Cliente en el Cliente](#6)

- [Instalación de Workbench en el Servidor](#7)

    - [Conexión usuario con el Workbench](#8)


- [Instalación de Workbench en el cliente](#9)

- [Configuración de fichero `my.cnf` para conectarse cliente desde la red](#10)

    - [Directorio del fichero `my.conf`](#11)

    - [Directorio donde se guarda los ficheros de datos de la instalación mysql](#12)

- [Creación de Usuario en el Workbench](#13)

- [Probar la conexión al servidor, utilizando el programa cliente mysql.](#14)

- [Configuración de la seguridad post-instalación (ejecutar mysql_secure_installation)](#15)

- [Instalación de phpmyadmin y apache en el Servidor](#16)

    - [Directorio de instalación base de phpmyadmin](#17)

    - [Fichero de configuración de phpmyadmin](#18)

    - [Comprobación que podemos acceder a la base de datos mediante phpmyadmin en local](#19)

- [¿Quién es el usuario propietario de la instalación ?](#20)

- [Aplicar el lenguaje de los mensajes de error  a español, modificando la configuración (indicar el directorio donde se aloja el fichero en español)](#21)

- [Comprobación que podemos acceder desde un equipo de red a la base de datos del servidor.](#22)



![image](img/000.png)

## Instalación MySQL Server desde el gestor de paquetes.<a name="1"></a>

Primero tenemos que actualizar los repositorios.

![image](img/001.png)

Para instalar el servicio de MySQL-Server, solo tenemos que escribir el siguiente comando.

![image](img/002.png)

En el proceso de instalación te pedirá que le pongas una contraseña al usuario root.

![image](img/003.png)

### Versión estable que se instala desde el repositorio.<a name="2"></a>

Solo tenemos que escribir el siguiente comando.

![image](img/004.png)


## El servicio o demonio de mysql que arranca/reinicia/para el núcleo<a name="3"></a>

Para saber el status solo debemos escribir el siguiente comando. `systemctl status mysql`

![image](img/005.png)

Para saber el habilitar solo debemos escribir el siguiente comando. `systemctl enable mysql`

![image](img/007.png)

Para saber el stop solo debemos escribir el siguiente comando.`systemctl stop mysql`

![image](img/008.png)

Para saber el reiniciar solo debemos escribir el siguiente comando. `systemctl restart mysql`

![image](img/006.png)

Para saber el reiniciar solo debemos escribir el siguiente comando. `systemctl start mysql`

![image](img/009.png)

### EL directorio del servicio o proceso de demonio.<a name="4"></a>

La ruta es la siguiente `/etc/init.d/mysql`

![image](img/013.png)

Para saber si el servicio se está ejecutando podemos utilizar el siguiente comando.

![image](img/044.png)

## Instalación MySQL Cliente en el Servidor<a name="5"></a>

Primero tenemos que actualizar los repositorio.


![image](img/010.png)

Tenemos que instalar el `mysql-cliente-5.7`

![image](img/011.png)


## Instalación MySQL Cliente en el Cliente<a name="6"></a>

Solo tenemos que escribir el siguiente comando.


![image](img/014.png)


## Instalación de Workbench en el Servidor<a name="7"></a>

Solo tenemos que escribir el siguiente comando.

![image](img/012.png)

### Conexión usuario con el Workbench<a name="8"></a>

Con el usuario `root` accedemos a la base de datos.

![image](img/016.png)

Comprobación que entra.

![image](img/017.png)



## Instalación de Workbench en el cliente<a name="9"></a>

Tenemos que escribir el siguiente comando para instalar el Workbench.

![image](img/015.png)


## Configuración de fichero my.cnf para conectarse cliente desde la red.<a name="10"></a>

Solo tenemos que abrir el Workbench, ir a opcion file, ir a la pestaña networking y activamos la casilla de `bind address`

![image](img/025.png)

Le damos aplicar.

![image](img/026.png)

En la misma pestaña de networking debemos activar el puerto.

![image](img/040.png)

En la pestaña de general activamos la siguiente opción.

![image](img/041.png)

### Directorio del fichero my.conf<a name="11"></a>

La ruta del fichero de my.conf se encuentra:

![image](img/019.png)

Realizamos un cat de este fichero para ver su contenido.

![image](img/029.png)

### Directorio donde se guarda los ficheros de datos de la instalación mysql<a name="12"></a>

En la siguiente ruta es donde esta almacenado los datos de instalación y comprobamos en los permios de usuario y grupos, como se ve esta como mysql, cuando se instala el mysql, se coloca como permisos con el nombre de mysql.


![image](img/035.png)

## Creación de Usuario en el Workbench<a name="13"></a>

Tenemos que abrir el Workbench, vamos a la pestaña usuario y privilegios.

Le damos add Acount y establecemos lo siguientes parametros de permisos.

![image](img/027.png)


## Probar la conexión al servidor, utilizando el programa cliente mysql.<a name="14"></a>

Accedemos desde el servidor al cliente de mysql con el siguiente comando.

    `mysql -p`

![image](img/028.png)

Realizamos la misma comprobación desde un Equipo mediante red, remoto y conectamos a la base de datos del servidor.

![image](img/042.png)

## Configuración de la seguridad post-instalación (ejecutar mysql_secure_installation)<a name="15"></a>

Solo tenemos que ejecutar el comando y seguir el asistente que nos indica.


![image](img/020.png)


## Instalación de phpmyadmin y apache en el Servidor.<a name="16"></a>

Solo tenemos que escribir el siguiente comando en la terminal para instalar el servicio phpmyadmin.

![image](img/021.png)

En el proceso de la instalación nos pide elegir el servicio de apache.

![image](img/022.png)

En este proceso tenemos que crear una base de datos para phpmyadmin en mysql.

![image](img/023.png)

Tenemos que configurar una contraseña.

![image](img/024.png)

### Directorio de instalación base de phpmyadmin<a name="17"></a>

La ruta donde se instala el phpmyadmin es:

![image](img/030.png)

### Fichero de configuración de phpmyadmin<a name="18"></a>

La ruta del Fichero de configuración es la siguiente.

![image](img/033.png)

El fichero se llama `config.inc.php`

![image](img/034.png)


### Comprobación que podemos acceder a la base de datos mediante phpmyadmin en local<a name="19"></a>

Abrimos un navegador escribimos lo siguiente `localhost\phpmyadmin` se debe abrir la siguiente página pidiendo el usuario y contraseña.

![image](img/031.png)

Escribimos los datos y deberiamos ver la base de datos.

![image](img/032.png)


## ¿Quién es el usuario propietario de la instalación?<a name="20"></a>

El usuario propietario es el mysql.

![image](img/035.png)

## Aplicar el lenguaje de los mensajes de error  a español, modificando la configuración (indicar el directorio donde se aloja el fichero en español)<a name="21"></a>

Para cambiar los mensajes de error a español tenemos dos opciones.

- Podemos acceder al Workbench y en option file, buscamos `lc_messages`, lo marcamos en la casilla y escribimos `es_ES`.

![image](img/036.png)

- Vamos a la ruta `/etc/mysql/my.cnf` y escribimos `lc_messages=es_ES`

![image](img/037.png)

Si nos fijamos a la hora de escribir un error a la hora de realizar una búsqueda o consulta.

![image](img/043.png)


## Comprobación que podemos acceder desde un equipo de red a la base de datos del servidor.<a name="22"></a>

Solo tenemos que abrir un navegador escribir la siguiente dirección IP.

![image](img/038.png)

Nos pide un usuario y una contraseña.

Como se comprueba en la imagen, hemos establecido conexión con el servidor mysql por red.

![image](img/039.png)
