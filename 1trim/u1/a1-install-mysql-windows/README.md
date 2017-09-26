# MYSQL Windows

- [Descarga de MySQL para Windows](#id1)

- [Instalación de MySQL](#id2)

    - [Problema y solución en la instalación](#id3)

    - [Entramos en una Línea de comando](#id4)

    - [Ruta de Instalación MySQL Windows](#id5)


- [Creación de un Virtual Host en el Servidor Ngnix](#id7)

- [Crear carpeta y fichero index.html](#id8)

- [Crear un enlace simbólico en /etc/nginx/sites-enabled](#id9)

- [Esctuctura final de la carpeta series](#id10)

- [Comprobación que la Página Web se pueda visualizar](#id6)

![imagen](img/mysql.png)

## Descarga de MySQL para Windows<a name="id1"></a>
Tenemos que ir a la página de MySQL y nos descargamos del siguiente [MySQL](https://dev.mysql.com/downloads/windows/installer/5.7.html).

![imagen](img/001.png)

## Instalación de MySQL<a name="id2"></a>
Ejecutamos el msi que se descargo y solo debemos seguir el asistente de MySQL.

![imagen](img/002.png)

Le damos siguiente.

![imagen](img/003.png)

Seleccionamos developer default, es el por defecto de la instalación.

![imagen](img/004.png)
Tenemos que darle a ejecutar. El sistema comprobara si necesitas algún paquete especial para instalar.


### Problema y solución en la instalación MySQL<a name="id3"></a>

 > Si el proceso de instalación falla en este paso, tenemos que ir a la siguiente página para instalar el [Visual C++ 2015](https://www.microsoft.com/es-es/download/details.aspx?id=52685)

![imagen](img/008.png)

Seguimos con la instalación de MySQL.

![imagen](img/005.png)

Le damos Execute, para realizar la instalación.

![imagen](img/006.png)

Le damos siguiente.

![imagen](img/007.png)

Escribimos el usuario root con la contraseña.

![imagen](img/009.png)

Se comprueba que se instalo todos los paquetes necesarios.

![imagen](img/011.png)

En un momento de la instalación nos pedirá la contraseña de root.

![imagen](img/014.png)

Seguimos y dejamos todo por defecto hasta llegar a la última ventana de la instalación.

![imagen](img/018.png)

## Entramos en una Línea de comando.<a name="id4"></a>

Comprobamos que podamos acceder a la base de datos por defecto de MySQL.

![imagen](img/023.png)

## Ruta de Instalación MySQL Windows <a name="id5"></a>

Tenemos que ir a archivos de programas de windows y la carpeta mysql.

![imagen](img/024.png)

Entramos en MySQL Server 5.7 y comprobamos sus ficheros.

![imagen](img/025.png)

Entramos en la carpeta bin

![imagen](img/026.png)
