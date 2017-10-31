# Fichero de Opciones y variables de servidor en MySQL

## 1 Ficheros de opciones
El servidor dispone de un conjunto de variables que determinan su funcionamiento. Una de las tareas más importantes del administrador implica el conocimiento y ajuste óptimo de los valores de las mismas según los requerimientos de las aplicaciones.
Debemos diferenciar entre variables del servidor y las opciones que permiten modificar el valor de las variables.
Podemos ajustar los valores de las diferentes variables usando ficheros de opciones, incluyendo dichas opciones cuando arrancamos el servidor; o modificándolas con el comando SET (sólo en el caso de ser dinámicas).
La mejor forma de conocer las variables es buscarlas cuando se necesiten. En tal caso debemos consultar el manual donde disponemos de una referencia detallada, donde para cada variable se detallan normalmente su nombre largo y corto para usar en la línea de comandos, su nombre para ficheros de opciones (no siempe coincide), si son modificables con SET, el nombre de la variable, su alcance (global o de sesión) y si es dinámica (modificable en tiempo de ejecución), su dominio o valores permitidos, su tipo y su valor por defecto.

Ajustar variables con Ficheros de Opciones.
Cuando queremos que las opciones sean permanentes lo normal es hacer que los programas de MySQL (mysqld entre ellos) puedan leer opciones de inicio desde ficheros de opciones (también llamados ficheros de configuración). Estos proporcionan una forma conveniente de especificar opciones comúnmente usadas. Este fichero determina el funcionamiento de nuestro servidor.

## 1.2 Haz la lectura de la siguiente página "[Using Option Files](http://dev.mysql.com/doc/refman/5.7/en/option-files.html)"

![](img/001.png)

Encuentra el fichero `my.ini o my.cnf` de tu instalación de MySQL (podría no estar en una ubicación no estándar).

```console

alu5906@server:~$ ls -l /etc/mysql/
total 48
drwxr-xr-x 2 root root  4096 oct 31 08:53 conf.d
-rw------- 1 root root   317 oct 31 08:55 debian.cnf
-rwxr-xr-x 1 root root   120 jul 19 20:28 debian-start
-rw-r--r-- 1 root root  1055 may 23  2015 fabric.cfg
lrwxrwxrwx 1 root root    24 oct 10 09:13 my.cnf -> /etc/alternatives/my.cnf
-rw-r--r-- 1 root root   839 ene 21  2017 my.cnf.fallback
-rw-r--r-- 1 root root   778 oct 10 14:02 my.cnf.wba.bak
-rw-r--r-- 1 root root   791 oct 10 14:02 mysql.cnf
drwxr-xr-x 2 root root  4096 oct 31 08:55 mysql.conf.d
-rw-r--r-- 1 root root 13132 feb 26  2015 mysql-fabric-doctrine-1.4.0.zip
alu5906@server:~$ cat /etc/mysql/mysql.cnf
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#

!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

[mysqld]
bind-address = 0.0.0.0
skip-external-locking
lc-messages = es_ES
language = "spanish"

port = 3306
alu5906@server:~$


```

- ¿Cómo se escribe un comentario en este fichero?

Solo tenemos que escribir delante `# Escribe aquí` por lo tanto esa línea esta comentada.
Para comentar múltiple líneas `/* escribe aquí */`

Ejemplo

```console
alu5906@server:~$ cat /etc/mysql/mysql.cnf
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#

!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mysql.conf.d/

[mysqld]
bind-address = 0.0.0.0
skip-external-locking
lc-messages = es_ES
language = "spanish"

port = 3306

```

- ¿Y un grupo de opciones?


Solo tenemos que abrir unos corchetes `[Escribe_Nombre_Grupo]`.

``` bash
[mysqld]
bind-address = 0.0.0.0
skip-external-locking
lc-messages = es_ES
language = "spanish"

```
- ¿Todas las opciones tienen un valor?

Según algunas opciones necesitan un valor y otras no.

![](img/002.png)

- Ejecuta "mysqld --verbose --help" desde una consola para ver una lista de las variables del servidor. Para ver mejor el texto mejor redirecciona la salida a fichero.

```console
alu5906@server:~$ sudo mysqld --verbose --help >> mysqld-verbose-help.txt

```
Ejemplo del fichero mysqld-verbose-help.texto

![](img/003.png)

- Explica qué significan y que se consigue con cada una de las variables del siguiente fichero de configuración

```bash
[client] # Grupo Cliente
port=3306  # Puerto de escucha
password="telesforo"; # LA contraseña se enviará a todos los clientes MySQL estándar.

[mysqld] # Grupo del demonio de mysql
port=3306 # Puerto de escucha
key_buffer_size=16M # Es el tamaño del indice y depende de su tamaño ayuda para mejorar la lectura.
max_allowed_packet=8M # Tamaño máximo del paquete.

[mysqldump] # grupo de copia de seguridad
quick # Se realizará la copia de seguridad en modo rápido.
```

## 2 Variables del servidor
Haz la lecturas de los siguientes enlaces y responde documentando las preguntas:

- "Server System Variables" http://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html

- "Using System Variables" http://dev.mysql.com/doc/refman/5.7/en/using-system-variables.html

Si queremos guardar el resultado de una consulta SQL en un fichero de texto, debemos construir la consulta del siguiente modo, ejemplo con un SELECT utilizando INTO OUTFILE :

```console
SELECT * INTO OUTFIELD '/var/lib/mysql-files/volcadosql.txt'
FROM tabla
WHERE ... ;

```
Podéis observar que el modo es usar INTO OUTFILE y posteriormente indicarle la ruta y nombre del fichero a crear, sobre el que tras ejecutar la consulta quedarán volcados los datos.

MySQL soporta varios motores de almacenamiento (storage engine)que tratan con distintos tipos de tabla. Los motores de almacenamiento de MySQL incluyen algunos que tratan con tablas transaccionales y otros que no lo hacen. Normalmente se utiliza MyISAM para lecturas rápidas e InnoDB para transacciones e integridad referencial. Si deseamos cambiar el motor por defecto para la creación de nuevas tablas en MySQL, debemos añadir la siguiente línea al ficher my.cnf (Linux) o my.ini (Windows), en este caso sería para poner como motor por defecto MyISAM:

`default-storage-engine=MyIsam`

Si quisieramos poner por defecto InnoDB:

`default-storage-engine=InnoDB`

1. Define qué son las variables del servidor.
2. Usa el comando "SHOW VARIABLES" para conocer el valor de todas las variables y enviar el resultado a un fichero.
3. Repite lo anterior para mostrar solo las variables relacionadas con el motor "InnoDB".
4. Para gestionar variables tenemos, como hemos visto, el comando SHOW "comando":

    - cómo mostrar todos los motores de almacenamiento

    - cómo mostrar el estado actual del servidor

    - cómo averiguar todos los clientes que están conectados al servidor

    - cómo conocer todas las tablas que están abiertas

### 2.1 Variables de estado
Haz la lecturas de los siguientes enlaces y responde documentando las preguntas:

- "Server Status Variables" http://dev.mysql.com/doc/refman/5.7/en/server-status-variables.html

- "SHOW STATUS Syntax" http://dev.mysql.com/doc/refman/5.7/en/show-status.html

- "SHOW Syntax" http://dev.mysql.com/doc/refman/5.7/en/show.html


1. Define qué son las variables de estado.
2. Usa el comando "SHOW STATUS" para conocer el valor de todas las variables..
3. Haz que uno o más de tus compañeros se conecte a tu servidor (puede que por cuestión de permisos no os podáis conectar).
4. Comprueba quién está conectado usando el comando correspondiente (Pista: es un comando visto SHOW XYZ).
5. Intenta desconectarlo con el comando "kill"
6. ¿Cuántas consultas se están ejecutado hasta el momento en tu servidor MYSQL? ¿Y si se trata de consultas lentas?
7. Un estado informa  el sobre el máximo de conexiones concurrentes que se ha dado en la sesión de trabajo. ¿Cuál es?

### 2.2 Variables dinámicas
Son aquellas que son modificables en tiempo de ejecución.

Haz la lectura de los siguientes enlaces y contesta razonadamente a las preguntas:

- "Dynamic System Variables" http://dev.mysql.com/doc/refman/5.7/en/dynamic-system-variables.html

- "SET Syntax" http://dev.mysql.com/doc/refman/5.7/en/set-statement.html


1. Detalla los posibles atributos que tendría una variable de servidor como "port".

|Command-Line Format | | |
|---- |---- |---- |
|System Variable|	Name|	port|
|               |Variable Scope| |
|               |Dynamic Variable| |
|               |Dynamic Variable| |
|  Permitted Values	             |Type	| |
|               |Default| |
|               |Min Value| |
|               |Max Value| |



2.-¿Cómo podemos saber si una variable es dinámica o no?

## 3.-¿Qué hace la variable "uptime"?

- Indica su valor en tu servidor


- ¿Es posible modificar su valor con comando SET?


## 4.- Localiza la variable que establece el límite de conexiones concurrentes. ¿Cuál es?

Modifícala y establece un máximo de 100 conexiones concurrentes
