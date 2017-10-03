# MYSQL Windows

- [Descarga de MySQL para Windows](#id1)

- [Instalación de MySQL](#id2)

    - [Problema y solución en la instalación](#id3)

    - [Entramos en una Línea de comando](#id4)

    - [Ruta de Instalación MySQL Windows](#id5)

    - [Comprobación del Servicio de MySQL en Windows](#id6)


- [Instalación Workbench en Windows clientes](#id7)

- [Crear Usuarios desde línea comando](#id9)

- [Crear Usuarios desde Workbench](#id12)


    - [Permisos de Usuarios](#id10)
    - [Permisos de Usuarios desde Workbench](#id11)

- [Instalación del XAMP](#id13)



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

Tenemos que activar los archivos ocultos. En la unidad C:\, tiene que tener una carpeta oculta llamada *programadata*

![imagen](img/039.jpg)

Accedemos a la carpeta.

![imagen](img/040.jpg)

El fichero my.ini es elfichero de configuración de MySQL.

Si accedemos a la carpeta Data es la información de las base de datos.

![imagen](img/041.jpg)

Comprobar la ruta de my.ini desde el Workbench con una conexión local.

![imagen](img/042.jpg)


### Comprobación del Servicio de MySQL en Windows.<a name="id6"></a>

Escribimos services y comprobamos los servicios activados.

![imagen](img/027.png)

Para comprobar que el servicio esta iniciado por comando sería. net start

![imagen](img/030.png)

### Configuración modo remoto en el servidor de MYSQL desde Workbench.

Tenemos que ejecutar el Workbench, vamos a options file. Luego en la pestaña networking y vamos a general y marcamos **bind-address**

![imagen](img/043.png)

Resultado a la hora de aplicar.

![imagen](img/044.png)



## Instalación Workbench en Windows clientes<a name="id7"></a>

Tenemos que instalar el Workbench en Windows 7 cliente para poder acceder al servidor de MySQL. Tenemos que descargar desde [MySQL](https://dev.mysql.com/downloads/windows/installer/5.7.html).

![imagen](img/028.png)

Solo tenemos que ejecutar el msi, seguir el asistente.

![imagen](img/029.png)

Solo tenemos que seguir el asistente todo siguiente y dejar todo por defecto en la instalación.

### Conectarse con el Workbench Cliente al servidor<a name="id8"></a>

Tenemos que abrir el Workbench y configurar la siguiente ruta de direccion ip. El usuario debe ser técnico.

![imagen](img/048.jpg)

Ejecutamos la conexion remota y se comprueba que podemos ver la base de datos.

![imagen](img/051.jpg)
![imagen](img/050.jpg)

## Crear Usuarios desde línea comando<a name="id9"></a>

Creamos el usuario desde línea de comando.

![imagen](img/032.png)

si queremos crear un usuario desde Workbench podemos copiar el mismo comando de la línea de comando.

## Crear Usuarios desde Workbench<a name="id12"></a>

Tenemos que ejecutar el Workbench y ir a users and privileges.

![imagen](img/045.jpg)

Creamos un usuarios nuevo llamado roberto que permite todos los hosts.

![imagen](img/046.jpg)

Creamos otro usuarios llamado técnico para las conexiones remotas.

![imagen](img/047.jpg)

### Permisos de Usuarios desde comando <a name="id10"></a>

Tenemos que escribir el siguiente comando.

![imagen](img/033.png)

Esto significa que le da permiso total, pero no llega al mismo nivel que el usuario root de privilegios.

Para que todo se aplique debemos utilizar el siguiente comando.

![imagen](img/034.png)

### Permisos de Usuarios desde Workbench<a name="id11"></a>


Ejecutamos el Workbench, vamos a users y privileges, seleccionamos el usuario técnico y vamos a la pestaña administrative Roles. En principio vamos a dar permiso total para el usuario técnico.

![imagen](img/049.jpg)

Solo debemos aplicar.

El usuario root solo debe tener acceso desde el modo local.

![imagen](img/052.jpg)

## Instalación del XAMP<a name="id13"></a>
Descargamos el XAMP que tenemos en el servidor Leela.

![imagen](img/053.jpg)

Iniciamos la instalación de XAMP.

![imagen](img/054.jpg)

Solo instalamos los clic que tenemos marcado en la imagen.

![imagen](img/055.jpg)

Proceso de la instalación

![imagen](img/056.jpg)
