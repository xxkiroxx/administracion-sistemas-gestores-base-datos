# Instalación de SQL Server 2014 Express en Windows Server 2012

- [Instalación de SQL Server Express 2014](#1)

- [Instalación Management Studio](#2)

- [Configuración Servidor SQL server 2014 conexiones remotas](#6)

- [Comprobación de acceso local desde Management Studio a la instancia de SQL Server](#3)

- [Instalación de Management Studio en un cliente Windows 7](#4)

- [Acceso remoto desde Management Studio de Windows 7 a la instancia de SQL Server del servidor Windows Server 2012, tanto por nombre de máquina como por IP. Investigar con los recursos del curso y realizar las configuraciones necesarias para estas conexiones](#5)

En la siguiente actividad tenemos que instalar el SQL Server Express 2014 y Management Studio en un Servidor Windows Server 2012.

![imagen](img/000.png)

## Instalación de SQL Server Express 2014<a name="1"></a>

La instalación de SQL Server Express 2014 solo tenemos que ir a la siguiente página de Microsoft y descargar el programa de [SQL Server Express 2014](https://www.microsoft.com/es-es/download/details.aspx?id=42299).

![imagen](img/001.png)


## Instalación Management Studio<a name="2"></a>

Solo debemos ejecutar la aplicación que descargamos de la página de Microsoft y seguir el asistente de modo por defecto, no es necesario cambiar nada de los valores.

![imagen](img/002.png)

![imagen](img/003.png)

![imagen](img/004.png)

![imagen](img/005.png)

![imagen](img/006.png)

![imagen](img/007.png)

![imagen](img/023.png)

![imagen](img/009.png)

![imagen](img/010.png)

![imagen](img/011.png)

![imagen](img/012.png)

![imagen](img/013.png)

Comprobamos que se realizó la instalación de SQL Server 2014

![imagen](img/014.png)

## Configuración Servidor SQL server 2014 conexiones remotas<a name="6"></a>

Accedemos con un usuario administrador al SQL server 2014, en el servidor de base de datos le damos con el botón secundario y seleccionamos propiedades.

![imagen](img/025.png)

Vamos a la pestaña de conexiones y tenemos que marcar `permitir conexiones remotas con este servidor`

![imagen](img/026.png)

Vamos a la pestaña de seguridad, seleccionamos `modo de autenticación de Windows y SQL Server`

![imagen](img/027.png)

Tenemos que buscar la aplicación que instala sql server 2014, llamada `SQL server Configuration Manager`, seleccionamos configuraciñon de red de SQL server y activamos la conexión TCP/IP.

![imagen](img/028.png)

Abrimos el fichero de configuración de TCP/IP

![imagen](img/029.png)

Ya tenemos todo configurado, solo nos falta reiniciar el servicio de SQL.

![imagen](img/042.png)

![imagen](img/043.png)


## Comprobación de acceso local desde Management Studio a la instancia de SQL Server<a name="3"></a>

Ejecutamos la aplicación y accedemos con el usuario de Windows.

![imagen](img/040.png)

Se comprueba que entramos a la Base de datos de SQL server 2014.

![imagen](img/041.png)


## Instalación de Management Studio en  Windows Server 2012 y Windows 10<a name="4"></a>

Tenemos que ir la página de Microsoft y descargamos el siguiente [Management-Studio](https://docs.microsoft.com/es-es/sql/ssms/download-sql-server-management-studio-ssms)

![imagen](img/015.png)

Ejecutamos la aplicación para iniciar la instalación en Windows Server 2012.

![imagen](img/016.png)

![imagen](img/017.png)

![imagen](img/018.png)

![imagen](img/019.png)

Abrimos el Management-Studio y vamos a crear una base de datos llamada neptuno

![imagen](img/021.png)


Solo tenemos que crear un new query

![imagen](img/020.png)

Realizamos el mismo procedimiento de instalación del Windows Server 2012 en el cliente Windows 10


## Acceso remoto desde Management Studio de Windows 10 a la instancia de SQL Server del servidor Windows Server 2012, tanto por nombre de máquina como por IP. Investigar con los recursos del curso y realizar las configuraciones necesarias para estas conexiones. <a name="5"></a>

Para configurar el nombre del Equipo con la dirección IP, es importante ir al fichero de configuración de `hosts`. Realizamos este procedimiento si escribimos en la conexión de SQL el nombre del Servidor y no se conecta.

- `windows\system32\drivers\etc\hosts`

Solo debemos modificar el fichero y escribir lo siguiente.

`172.18.22.2   server`

![imagen](img/039.png)



Conectamos mediante al nombre del Servidor Windows Server 2012, nombre `server`.

Escribimos el usuario creado llamado `roberto` y accedemos mediante la red.

![imagen](img/035.png)

La siguiente captura se comprueba como se conecta desde un Equipo Windows 10 al servidor SQL 2014 con Windows Server 2012.

![imagen](img/036.png)


Conectamos mediante la IP del servidor Windows Server 2012, IP `172.18.22.1`.

![imagen](img/037.png)

La siguiente captura se comprueba como se conecta desde un Equipo Windows 10 al servidor SQL 2014 con Windows Server 2012.

![imagen](img/038.png)
