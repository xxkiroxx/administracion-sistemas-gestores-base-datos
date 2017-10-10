# MySQL Server en Ubuntu

## Instalación MySQL Server desde el gestor de paquetes.

Primero tenemos que actualizar los repositorios.

![image](img/001.png)

Para instalar el servicio de MySQL-Server, solo tenemos que escribir el siguiente comando.

![image](img/002.png)

En el proceso de instalación te pedirá que le pongas una contraseña al usuario root.

![image](img/003.png)

### Versión estable que se instala desde el repositorio.

Solo tenemos que escribir el siguiente comando.

![image](img/004.png)



## Reiniciar el servicio de mysqld que arranca el núcleo.

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

### EL directorio del servicio o proceso de demonio.

La ruta es la siguiente `/etc/init.d/mysql`

![image](img/013.png)

## Instalación MySQL Cliente en el Servidor

Primero tenemos que actualizar los repositorio.


![image](img/010.png)

Tenemos que instalar el mysql-cliente-5.7

![image](img/011.png)


## Instalación MySQL Cliente en el Cliente

Solo tenemos que escribir el siguiente comando.


![image](img/014.png)


## Instalación de Workbench en el Servidor

Solo tenemos que escribir el siguiente comando.

![image](img/012.png)

### Conexión usuario con el Workbench

Con le usuario root accedemos a la base de datos.

![image](img/016.png)

Comprobación que entra.

![image](img/017.png)



## Instalación de Workbench en el cliente

Tenemos que escribir el siguiente comando para instalar el Workbench.

![image](img/015.png)


## Configuración de fichero my.cnf para conectarse cliente desde la red.

Solo tenemos que abrir el Workbench, ir a opcion file, ir a la pestaña networking y activamos la casilla de bind address.

![image](img/025.png)

Le damos aplicar.

![image](img/026.png)

### Directorio del fichero my.conf



### Creación de Usuario en el Workbench

Tenemos que abir el Workbench, vamos a la pestaña usuario y privilegios.

Le damos add Acount y establecemos lo siguientes parametros de permisos.

![image](img/027.png)


## Probar la conexión al servidor, utilizando el programa cliente mysql.

Accedemos desde el servidor al cliente de mysql con el siguiente comando.

    `mysql -p`

![image](img/028.png)


## Configuración de la seguridad post-instalación (ejecutar mysql_secure_installation)

Solo tenemos que ejecutar el comando y seguir el asistente que nos indica.


![image](img/020.png)


## Instalación de phpmyadmin y apache en el Servidor.

Solo tenemos que escribir el siguiente comando en la terminal para instalar el servicio phpmyadmin.

![image](img/021.png)

En el proceso de la instalación nos pide elegir el servicio de apache.

![image](img/022.png)

En este proceso tenemos que crear una base de datos para phpmyadmin en mysql.

![image](img/023.png)

Tenemos que configurar una contraseña.

![image](img/024.png)

### Directorio de instalación base

### Directorio de datos

### Fichero de configuración del servidor y su ubicación




### ¿Quién es el usuario propietario de la instalación ?

El usuario propietario es el mysql.

### Aplicar el lenguaje de los mensajes de error  a español, modificando la configuración (indicar el directorio donde se aloja el fichero en español)
