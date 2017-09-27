# MYSQL Windows

- [Descarga de MySQL para Windows](#id1)

- [Instalación de MySQL](#id2)

    - [Problema y solución en la instalación](#id3)

    - [Entramos en una Línea de comando](#id4)

    - [Ruta de Instalación MySQL Windows](#id5)

    - [Comprobación del Servicio de MySQL en Windows](#id6)


- [Instalación Workbench en Windows clientes](#id7)

- [Crear Usuarios desde línea comando](#id9)

    - [Permisos de Usuarios](#id10)
    

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

### Entramos en una Línea de comando.<a name="id4"></a>

Comprobamos que podamos acceder a la base de datos por defecto de MySQL.

![imagen](img/023.png)

### Ruta de Instalación MySQL Windows <a name="id5"></a>

Tenemos que ir a archivos de programas de windows y la carpeta mysql.

![imagen](img/024.png)

Entramos en MySQL Server 5.7 y comprobamos sus ficheros.

![imagen](img/025.png)

Entramos en la carpeta bin

![imagen](img/026.png)

### Comprobación del Servicio de MySQL en Windows.<a name="id6"></a>

Escribimos services y comprobamos los servicios activados.

![imagen](img/027.png)

Para comprobar que el servicio esta iniciado por comando sería. net start

![imagen](img/030.png)

## Instalación Workbench en Windows clientes<a name="id7"></a>

Tenemos que instalar el Workbench en Windows 7 cliente para poder acceder al servidor de MySQL. Tenemos que descargar desde [MySQL](https://dev.mysql.com/downloads/windows/installer/5.7.html).

![imagen](img/028.png)

Solo tenemos que ejecutar el msi, seguir el asistente.

![imagen](img/029.png)

Solo tenemos que seguir el asistente todo siguiente y dejar todo por defecto en la instalación.

### Conectarse con el Workbench Cliente al servidor<a name="id8"></a>

Tenemos que abrir el Workbench y configurar la siguiente ruta.

![imagen](img/031.png)


## Crear Usuarios desde línea comando<a name="id9"></a>

Creamos el usuario desde línea de comando.

![imagen](img/032.png)

si queremos crear un usuario desde Workbench podemos copiar el mismo comando de la línea de comando.

### Permisos de Usuarios <a name="id10"></a>

Tenemos que escribir el siguiente comando.

![imagen](img/033.png)

Esto significa que le da permiso total, pero no llega al mismo nivel que el usuario root de privilegios.

Para que todo se aplique debemos utilizar el siguiente comando.

![imagen](img/034.png)
