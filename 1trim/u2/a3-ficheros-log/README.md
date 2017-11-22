# 4.- Ficheros Log
## Ficheros LOG: Error LOG
El fichero "Error Log" registra problemas encontrados iniciando, ejecutando o parando mysqld.
Lee el pdf de la UD1.- Instalación y Configuración de un SGBD, la parte 5 de  Los Ficheros LOG
Haz la lectura de la siguiente página y contesta a las preguntas razonadamente:

- MySQL Server Logs: http://dev.mysql.com/doc/refman/5.7/en/server-logs.html

- The Error Log: http://dev.mysql.com/doc/refman/5.7/en/error-log.html


### 1. Explica qué es y para qué sirve el "ERROR LOG"

El registro de errores contiene un registro de los tiempos de inicio y apagado de mysqld . También contiene mensajes de diagnóstico como errores, advertencias y notas que se producen durante el inicio y el apagado del servidor, y mientras el servidor se está ejecutando. Por ejemplo, si mysqld nota que una tabla necesita ser revisada o reparada automáticamente, escribe un mensaje en el registro de errores.

El fichero de `error.log` está en la siguiente ruta. `/var/log/mysql/error.log`

```console
alu5906@server:/etc/mysql$ ls -l /var/log/mysql/
total 124
-rw-r----- 1 mysql adm   59890 nov 22 08:56 error.log
-rw-r----- 1 mysql adm    5878 nov 22 08:16 error.log.1.gz
-rw-r----- 1 mysql adm    2761 nov 21 08:44 error.log.2.gz
-rw-r----- 1 mysql adm    2457 nov 15 08:18 error.log.3.gz
-rw-r----- 1 mysql adm    4354 nov  8 08:41 error.log.4.gz
-rw-r----- 1 mysql adm    5287 nov  7 08:12 error.log.5.gz
-rw-r----- 1 mysql adm   10093 oct 31 08:53 error.log.6.gz
-rw-r----- 1 mysql adm    1669 nov 22 08:55 mysql-slow.log
-rw-r----- 1 mysql adm     172 nov 22 08:16 mysql-slow.log.1.gz
-rw-r----- 1 mysql adm    2017 nov 21 08:45 mysql-slow.log.2.gz
-rw-r----- 1 mysql mysql   494 nov 15 08:17 mysql-slow.log.3.gz
alu5906@server:/etc/mysql$
```
- Comprobamos el fichero error.log

```console
alu5906@server:/etc/mysql$ tail -f /var/log/mysql/error.log
2017-11-22T08:55:33.965891Z 0 [Note] InnoDB: Buffer pool(s) load completed at 171122  8:55:33
2017-11-22T08:55:33.965954Z 0 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.7.20-0ubuntu0.16.04.1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
2017-11-22T08:55:33.965961Z 0 [Note] Executing 'SELECT * FROM INFORMATION_SCHEMA.TABLES;' to get a list of tables using the deprecated partition engine. You may use the startup option '--disable-partition-engine-check' to skip this check.
2017-11-22T08:55:33.965963Z 0 [Note] Beginning of list of non-natively partitioned tables
2017-11-22T08:55:33.972834Z 0 [Note] End of list of non-natively partitioned tables
2017-11-22T08:55:34.738502Z 3 [Note] Acceso negado para usuario: 'root'@'localhost' (Usando clave: NO)
2017-11-22T08:56:16.986121Z 4 [Note] Acceso negado para usuario: 'root'@'localhost' (Usando clave: SI)
2017-11-22T08:56:41.305825Z 5 [Note] Acceso negado para usuario: 'root'@'localhost' (Usando clave: SI)
2017-11-22T08:56:53.397630Z 6 [Note] Acceso negado para usuario: 'root'@'localhost' (Usando clave: NO)
```

### 2. Indica al servidor en "my.cnf" que registre los errores en un fichero llamado "server_error". Reinicia el servidor y comprueba los mensajes visualizando dicho fichero.

Para modificar el fichero por defecto de `/var/log/mysql/error.log`

Tenemos que entrar en el fichero de configuración `/etc/mysql/my.cnf`

```console
alu5906@server:~$ cat /etc/mysql/my.cnf
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

slow-query-log = 1
slow-query-log-file = /var/log/mysql/mysql-slow.log
long_query_time = 1
log_queries-not-using-indexes
max_connections = 100
# Ficheros error
log-error = /var/log/mysql/server_error.log
# Ficheros Log-Query
#general_log_file = /var/lib/mysql/server_error.log
#general_log = 1
alu5906@server:~$
```
- Comprobamos en la línea comentada `ficheros error` y agregamos la nueva ruta con el nombre diferente de fichero log.



### 3. Detén el servidor abruptamente (haz lo que sea necesario) y comprueba cómo se ha modificado dicho fichero.

- Paramos el servicio y comprobamos el resultado. Comprobamos que el fichero `server_error.log` se registran nuevos datos de errores.


```console
alu5906@server:/etc/mysql$ sudo systemctl stop mysql.service
alu5906@server:/etc/mysql$ sudo systemctl start mysql.service
alu5906@server:/etc/mysql$ tail -f /var/log/mysql/server_error.log
tail: no se puede abrir '/var/log/mysql/server_error.log' para lectura: Permiso denegado
tail: no queda ningún fichero
alu5906@server:/etc/mysql$ sudo tail -f /var/log/mysql/server_error.log
2017-11-22T09:12:29.801194Z 0 [Note] Server socket created on IP: '0.0.0.0'.
2017-11-22T09:12:29.805956Z 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
2017-11-22T09:12:29.806471Z 0 [Note] InnoDB: Buffer pool(s) load completed at 171122  9:12:29
2017-11-22T09:12:29.806561Z 0 [Note] Event Scheduler: Loaded 0 events
2017-11-22T09:12:29.806656Z 0 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.7.20-0ubuntu0.16.04.1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
2017-11-22T09:12:29.806663Z 0 [Note] Executing 'SELECT * FROM INFORMATION_SCHEMA.TABLES;' to get a list of tables using the deprecated partition engine. You may use the startup option '--disable-partition-engine-check' to skip this check.
2017-11-22T09:12:29.806671Z 0 [Note] Beginning of list of non-natively partitioned tables
2017-11-22T09:12:29.814250Z 0 [Note] End of list of non-natively partitioned tables
2017-11-22T09:12:30.561568Z 3 [Note] Acceso negado para usuario: 'root'@'localhost' (Usando clave: NO)
```

- Comprobamos que el fichero `server_error.log` se crea solo.

```console
alu5906@server:/etc/mysql$ sudo ls -l /var/log/mysql/
total 144
-rw-r----- 1 mysql adm   64156 nov 22 09:03 error.log
-rw-r----- 1 mysql adm    5878 nov 22 08:16 error.log.1.gz
-rw-r----- 1 mysql adm    2761 nov 21 08:44 error.log.2.gz
-rw-r----- 1 mysql adm    2457 nov 15 08:18 error.log.3.gz
-rw-r----- 1 mysql adm    4354 nov  8 08:41 error.log.4.gz
-rw-r----- 1 mysql adm    5287 nov  7 08:12 error.log.5.gz
-rw-r----- 1 mysql adm   10093 oct 31 08:53 error.log.6.gz
-rw-r----- 1 mysql adm    2033 nov 22 09:12 mysql-slow.log
-rw-r----- 1 mysql adm     172 nov 22 08:16 mysql-slow.log.1.gz
-rw-r----- 1 mysql adm    2017 nov 21 08:45 mysql-slow.log.2.gz
-rw-r----- 1 mysql mysql   494 nov 15 08:17 mysql-slow.log.3.gz
-rw-r----- 1 mysql mysql 12649 nov 22 09:12 server_error.log
alu5906@server:/etc/mysql$
```

### 4. Prueba la función "perror" incluida en el directorio bin. ¿Cuál es su objeto? Puedes consultar http://dev.mysql.com/doc/refman/5.7/en/perror.html

Entramos en la base de datos de `mysql` y escribimos un error en este caso es el siguiente.

```console
alu5906@server:~$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.7.20-0ubuntu0.16.04.1-log (Ubuntu)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> select hola;
ERROR 1054 (42S22): La columna 'hola' en field list es desconocida
mysql>
```

- En otra terminal escribimos el siguiente comando `perror "codigo_error_mysql"`

```console
alu5906@server:/etc/mysql$ perror 1054
MySQL error code 1054 (ER_BAD_FIELD_ERROR): Unknown column '%-.192s' in '%-.192s'
alu5906@server:/etc/mysql$
```


## Ficheros LOG: General Query LOG

El fichero "Global Query  Log" registra las conexiones establecidas por los clientes y las sentencias ejecutadas por ellos.

Haz la lectura de la siguiente página y contesta a las preguntas razonadamente:

- MySQL Server Logs: http://dev.mysql.com/doc/refman/5.7/en/server-logs.html

- The General Query Log: http://dev.mysql.com/doc/refman/5.7/en/query-log.html

### 1. Explica qué es y para qué sirve el "GENERAL QUERY LOG"

El registro general de consultas es un registro general de lo que está haciendo mysqld . El servidor escribe información en este registro cuando los clientes se conectan o desconectan, y registra cada instrucción SQL recibida de los clientes. El registro general de consultas puede ser muy útil cuando sospecha un error en un cliente y desea saber exactamente qué envió el cliente a mysqld .

Cada línea que se muestra cuando un cliente se conecta también incluye el using connection_type para indicar el protocolo utilizado para establecer la conexión. connection_type es uno de TCP/IP (conexión TCP / IP establecida sin SSL), SSL/TLS (conexión TCP / IP establecida con SSL), Socket (conexión de archivos de socket Unix), Named Pipe (Windows named pipe connection) o Shared Memory (Conexión de memoria compartida de Windows).

Para habilitarlo solo tenemos que escribir lo siguiente de modo dinámico.

```console
mysql> set global general_log=1;
Query OK, 0 rows affected (5,45 sec)

mysql>     
```

### 2. Configura MySQL para registrar consultas generales en el fichero denominado "miserver.log". Comprueba su funcionamiento haciendo que un compañero se conecte a tu servidor y ejecute varias consultas.

Primero tenemos que acceder a la base de datos de `mysql` y comprobamos si tenemos activado el fichero `general_log` disponible o activado.

```console
mysql> show variables like "general_log%";
+------------------+---------------------------+
| Variable_name    | Value                     |
+------------------+---------------------------+
| general_log      | OFF                       |
| general_log_file | /var/lib/mysql/server.log |
+------------------+---------------------------+
2 rows in set (0,00 sec)
```
Por lo que comprobamos el fichero `general_log` está desactivado, para activarlo tenemos que escribir el siguiente comando. `set global general_log=1`

```console
mysql> set global general_log=1;
Query OK, 0 rows affected (5,45 sec)

mysql>                     

^C
mysql> show variables like "general_log%";
+------------------+---------------------------------+
| Variable_name    | Value                           |
+------------------+---------------------------------+
| general_log      | ON                              |
| general_log_file | /var/lib/mysql/server.log |
+------------------+---------------------------------+
2 rows in set (0,01 sec)

mysql>
```
El problema es cuando reiniciamos el Servicio pues se desactiva el fichero log. Esté método es dinámicamente y si lo queremos tener para siempre tenemos que ir al fichero de configuración `my.cnf`

```console
alu5906@server:/etc/mysql$ sudo systemctl restart mysql.service
alu5906@server:/etc/mysql$
```
- Comprobamos como se desactiva el fichero `general_log`

```console
mysql> mysql> show variables like "general_log%";
ERROR 2006 (HY000): MySQL server has gone away
No connection. Trying to reconnect...
Connection id:    4
Current database: *** NONE ***

+------------------+---------------------------------+
| Variable_name    | Value                           |
+------------------+---------------------------------+
| general_log      | OFF                             |
| general_log_file | /var/lib/mysql/server.log |
+------------------+---------------------------------+
2 rows in set (0,00 sec)

mysql>
```

Si queremos dejarlo para siempre solo tenemos que realizar la configuración en el fichero `my.cnf`

Tenemos que ir a la ruta `/etc/mysql/my.cnf`

```console
alu5906@server:/etc/mysql$ cat my.cnf
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

slow-query-log = 1
slow-query-log-file = /var/log/mysql/mysql-slow.log
long_query_time = 1
log_queries-not-using-indexes
max_connections = 100

# Ficheros Log
general_log_file = /var/lib/mysql/miserver.log
general_log = 1
alu5906@server:/etc/mysql$
```
- Nos fijamos en la línea comentada de `# Ficheros Log` y aquí decimos la ruta donde se guardará el fichero miserver.log y habilitamos para siempre esté fichero. Si reiniciamos el servicio de mysql se mantiene la configuración.

```console
alu5906@server:/etc/mysql$ sudo systemctl restart mysql.service
alu5906@server:/etc/mysql$
```

- Entramos a la base de datos y escribimos el siguiente comando. `show variables like "general_log%"`

```console
mysql> show variables like "general_log%";
ERROR 2006 (HY000): MySQL server has gone away
No connection. Trying to reconnect...
Connection id:    4
Current database: *** NONE ***

+------------------+---------------------------------+
| Variable_name    | Value                           |
+------------------+---------------------------------+
| general_log      | ON                              |
| general_log_file | /var/lib/mysql/miserver.log |
+------------------+---------------------------------+
2 rows in set (0,00 sec)

```

- Realizo una prueba para ver si se registra conexiones o consultas en el fichero `miserver.log`

```console
alu5906@server:/etc/mysql$ sudo tail -f /var/lib/mysql/miserver.log
/usr/sbin/mysqld, Version: 5.7.20-0ubuntu0.16.04.1-log ((Ubuntu)). started with:
Tcp port: 3306  Unix socket: /var/run/mysqld/mysqld.sock
Time                 Id Command    Argument
2017-11-22T09:23:50.053934Z	    2 Query	SELECT TABLE_SCHEMA, TABLE_NAME FROM INFORMATION_SCHEMA.TABLES WHERE CREATE_OPTIONS LIKE '%partitioned%';
2017-11-22T09:23:50.812710Z	    3 Connect	root@localhost on  using Socket
2017-11-22T09:23:50.812736Z	    3 Connect	Acceso negado para usuario: 'root'@'localhost' (Usando clave: NO)
2017-11-22T09:24:07.624086Z	    4 Connect	root@localhost on  using Socket
2017-11-22T09:24:07.624205Z	    4 Query	show variables like "general_log%"
2017-11-22T09:24:47.967871Z	    4 Query	select hola
^C
alu5906@server:/etc/mysql$
```
- Comprobamos que el fichero está creado.

```console
alu5906@server:/etc/mysql$ sudo ls -l /var/lib/mysql/
total 188468
-rw-r----- 1 mysql mysql       56 oct 10 09:14 auto.cnf
-rw-r--r-- 1 mysql mysql        0 oct 31 08:55 debian-5.7.flag
-rw-r----- 1 mysql mysql      532 nov 22 09:23 ib_buffer_pool
-rw-r----- 1 mysql mysql 79691776 nov 22 09:23 ibdata1
-rw-r----- 1 mysql mysql 50331648 nov 22 09:23 ib_logfile0
-rw-r----- 1 mysql mysql 50331648 oct 10 09:14 ib_logfile1
-rw-r----- 1 mysql mysql 12582912 nov 22 09:23 ibtmp1
-rw-r----- 1 mysql mysql      711 nov 22 09:24 miserver.log
drwxr-x--- 2 mysql mysql     4096 oct 31 08:55 mysql
-rw-r--r-- 1 root  root         6 oct 31 08:55 mysql_upgrade_info
drwxr-x--- 2 mysql mysql     4096 oct 31 08:55 performance_schema
drwxr-x--- 2 mysql mysql     4096 oct 10 10:13 phpmyadmin
drwxr-x--- 2 mysql mysql     4096 oct 10 14:31 prueba
drwxr-x--- 2 mysql mysql     4096 nov 15 08:54 sakila
-rw-r----- 1 mysql mysql     2508 nov 22 08:53 server_error.log
drwxr-x--- 2 mysql mysql    12288 oct 10 09:14 sys
alu5906@server:/etc/mysql$
```

### 3. Averigua viendo el fichero "miserver.log" la hora en que se conectó tu compañero y ejecutó las consultas del apartado anterior.



### 4. Accede al servidor a través de Workbench. ¿Qué se registra en "general_log"?¿Hay alguna diferencia respecto al cliente mysql ?
