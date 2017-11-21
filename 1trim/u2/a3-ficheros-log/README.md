# 4.- Ficheros Log
## Ficheros LOG: Error LOG
El fichero "Error Log" registra problemas encontrados iniciando, ejecutando o parando mysqld.
Lee el pdf de la UD1.- Instalación y Configuración de un SGBD, la parte 5 de  Los Ficheros LOG
Haz la lectura de la siguiente página y contesta a las preguntas razonadamente:

- MySQL Server Logs: http://dev.mysql.com/doc/refman/5.7/en/server-logs.html

- The Error Log: http://dev.mysql.com/doc/refman/5.7/en/error-log.html


### 1. Explica qué es y para qué sirve el "ERROR LOG"

El registro de errores contiene un registro de los tiempos de inicio y apagado de mysqld . También contiene mensajes de diagnóstico como errores, advertencias y notas que se producen durante el inicio y el apagado del servidor, y mientras el servidor se está ejecutando. Por ejemplo, si mysqld nota que una tabla necesita ser revisada o reparada automáticamente, escribe un mensaje en el registro de errores.

En la siguiente ruta tenemos los ficheros de error por defecto de mysql.

```console
alu5906@server:/etc/mysql$ cd /var/log/mysql/
alu5906@server:/var/log/mysql$ ls -l
total 60
-rw-r----- 1 mysql adm    8619 nov 21 09:49 error.log
-rw-r----- 1 mysql adm    2761 nov 21 08:44 error.log.1.gz
-rw-r----- 1 mysql adm    2457 nov 15 08:18 error.log.2.gz
-rw-r----- 1 mysql adm    4354 nov  8 08:41 error.log.3.gz
-rw-r----- 1 mysql adm    5287 nov  7 08:12 error.log.4.gz
-rw-r----- 1 mysql adm   10093 oct 31 08:53 error.log.5.gz
-rw-r----- 1 mysql adm     364 nov 21 09:49 mysql-slow.log
-rw-r----- 1 mysql adm    2017 nov 21 08:45 mysql-slow.log.1.gz
-rw-r----- 1 mysql mysql   494 nov 15 08:17 mysql-slow.log.2.gz
alu5906@server:/var/log/mysql$

```
Comprobamos el fichero de error.log

```console

alu5906@server:/var/log/mysql$ cat error.log
2017-11-21T09:49:30.424123Z 0 [Note] Giving 2 client threads a chance to die gracefully
2017-11-21T09:49:30.424173Z 0 [Note] Shutting down slave threads
2017-11-21T09:49:32.424357Z 0 [Note] Forcefully disconnecting 2 remaining clients
2017-11-21T09:49:32.424407Z 0 [Warning] /usr/sbin/mysqld: Forzando a cerrar el thread 6  usuario: 'root'

2017-11-21T09:49:32.424468Z 0 [Warning] /usr/sbin/mysqld: Forzando a cerrar el thread 5  usuario: 'root'

2017-11-21T09:49:32.424505Z 0 [Note] Event Scheduler: Purging the queue. 0 events
2017-11-21T09:49:32.443919Z 0 [Note] Binlog end
2017-11-21T09:49:32.446072Z 0 [Note] Shutting down plugin 'ngram'
2017-11-21T09:49:32.446089Z 0 [Note] Shutting down plugin 'BLACKHOLE'
2017-11-21T09:49:32.446096Z 0 [Note] Shutting down plugin 'partition'
2017-11-21T09:49:32.446098Z 0 [Note] Shutting down plugin 'ARCHIVE'
2017-11-21T09:49:32.446100Z 0 [Note] Shutting down plugin 'MRG_MYISAM'
2017-11-21T09:49:32.446102Z 0 [Note] Shutting down plugin 'INNODB_SYS_VIRTUAL'
2017-11-21T09:49:32.446317Z 0 [Note] Shutting down plugin 'INNODB_SYS_DATAFILES'
2017-11-21T09:49:32.446325Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESPACES'
2017-11-21T09:49:32.446327Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN_COLS'
2017-11-21T09:49:32.446329Z 0 [Note] Shutting down plugin 'INNODB_SYS_FOREIGN'
2017-11-21T09:49:32.446331Z 0 [Note] Shutting down plugin 'INNODB_SYS_FIELDS'
2017-11-21T09:49:32.446333Z 0 [Note] Shutting down plugin 'INNODB_SYS_COLUMNS'
2017-11-21T09:49:32.446335Z 0 [Note] Shutting down plugin 'INNODB_SYS_INDEXES'
2017-11-21T09:49:32.446337Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLESTATS'
2017-11-21T09:49:32.446339Z 0 [Note] Shutting down plugin 'INNODB_SYS_TABLES'
2017-11-21T09:49:32.446341Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_TABLE'
2017-11-21T09:49:32.446343Z 0 [Note] Shutting down plugin 'INNODB_FT_INDEX_CACHE'
2017-11-21T09:49:32.446344Z 0 [Note] Shutting down plugin 'INNODB_FT_CONFIG'
2017-11-21T09:49:32.446346Z 0 [Note] Shutting down plugin 'INNODB_FT_BEING_DELETED'
2017-11-21T09:49:32.446348Z 0 [Note] Shutting down plugin 'INNODB_FT_DELETED'
2017-11-21T09:49:32.446350Z 0 [Note] Shutting down plugin 'INNODB_FT_DEFAULT_STOPWORD'
2017-11-21T09:49:32.446352Z 0 [Note] Shutting down plugin 'INNODB_METRICS'
2017-11-21T09:49:32.446354Z 0 [Note] Shutting down plugin 'INNODB_TEMP_TABLE_INFO'
2017-11-21T09:49:32.446356Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_POOL_STATS'
2017-11-21T09:49:32.446358Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE_LRU'
2017-11-21T09:49:32.446360Z 0 [Note] Shutting down plugin 'INNODB_BUFFER_PAGE'
2017-11-21T09:49:32.446362Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX_RESET'
2017-11-21T09:49:32.446363Z 0 [Note] Shutting down plugin 'INNODB_CMP_PER_INDEX'
2017-11-21T09:49:32.446365Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM_RESET'
2017-11-21T09:49:32.446367Z 0 [Note] Shutting down plugin 'INNODB_CMPMEM'
2017-11-21T09:49:32.446369Z 0 [Note] Shutting down plugin 'INNODB_CMP_RESET'
2017-11-21T09:49:32.446371Z 0 [Note] Shutting down plugin 'INNODB_CMP'
2017-11-21T09:49:32.446373Z 0 [Note] Shutting down plugin 'INNODB_LOCK_WAITS'
2017-11-21T09:49:32.446375Z 0 [Note] Shutting down plugin 'INNODB_LOCKS'
2017-11-21T09:49:32.446377Z 0 [Note] Shutting down plugin 'INNODB_TRX'
2017-11-21T09:49:32.446379Z 0 [Note] Shutting down plugin 'InnoDB'
2017-11-21T09:49:32.447550Z 0 [Note] InnoDB: FTS optimize thread exiting.
2017-11-21T09:49:32.487545Z 0 [Note] InnoDB: Starting shutdown...
2017-11-21T09:49:32.598148Z 0 [Note] InnoDB: Dumping buffer pool(s) to /var/lib/mysql/ib_buffer_pool
2017-11-21T09:49:32.598293Z 0 [Note] InnoDB: Buffer pool(s) dump completed at 171121  9:49:32
2017-11-21T09:49:34.216341Z 0 [Note] InnoDB: Shutdown completed; log sequence number 10183455
2017-11-21T09:49:34.217525Z 0 [Note] InnoDB: Removed temporary tablespace data file: "ibtmp1"
2017-11-21T09:49:34.217539Z 0 [Note] Shutting down plugin 'PERFORMANCE_SCHEMA'
2017-11-21T09:49:34.217561Z 0 [Note] Shutting down plugin 'MEMORY'
2017-11-21T09:49:34.217564Z 0 [Note] Shutting down plugin 'CSV'
2017-11-21T09:49:34.217767Z 0 [Note] Shutting down plugin 'MyISAM'
2017-11-21T09:49:34.217912Z 0 [Note] Shutting down plugin 'sha256_password'
2017-11-21T09:49:34.217919Z 0 [Note] Shutting down plugin 'mysql_native_password'
2017-11-21T09:49:34.245278Z 0 [Note] Shutting down plugin 'binlog'
2017-11-21T09:49:34.250720Z 0 [Note] /usr/sbin/mysqld: Apagado completado

2017-11-21T09:49:40.680062Z 0 [Warning] Changed limits: max_open_files: 1024 (requested 5000)
2017-11-21T09:49:40.680106Z 0 [Warning] Changed limits: table_open_cache: 457 (requested 2000)
2017-11-21T09:49:40.814366Z 0 [Warning] The syntax '--language/-l' is deprecated and will be removed in a future release. Please use '--lc-messages-dir' instead.
2017-11-21T09:49:40.814391Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2017-11-21T09:49:40.815109Z 0 [Note] /usr/sbin/mysqld (mysqld 5.7.20-0ubuntu0.16.04.1-log) starting as process 21740 ...
2017-11-21T09:49:40.815410Z 0 [Warning] Using pre 5.5 semantics to load error messages from /usr/share/mysql/spanish/.
2017-11-21T09:49:40.815415Z 0 [Warning] If this is not intended, refer to the documentation for valid usage of --lc-messages-dir and --language parameters.
2017-11-21T09:49:40.821287Z 0 [Note] InnoDB: PUNCH HOLE support available
2017-11-21T09:49:40.821304Z 0 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2017-11-21T09:49:40.821307Z 0 [Note] InnoDB: Uses event mutexes
2017-11-21T09:49:40.821310Z 0 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
2017-11-21T09:49:40.821314Z 0 [Note] InnoDB: Compressed tables use zlib 1.2.8
2017-11-21T09:49:40.821316Z 0 [Note] InnoDB: Using Linux native AIO
2017-11-21T09:49:40.821450Z 0 [Note] InnoDB: Number of pools: 1
2017-11-21T09:49:40.821514Z 0 [Note] InnoDB: Using CPU crc32 instructions
2017-11-21T09:49:40.822426Z 0 [Note] InnoDB: Initializing buffer pool, total size = 128M, instances = 1, chunk size = 128M
2017-11-21T09:49:40.826907Z 0 [Note] InnoDB: Completed initialization of buffer pool
2017-11-21T09:49:40.827890Z 0 [Note] InnoDB: If the mysqld execution user is authorized, page cleaner thread priority can be changed. See the man page of setpriority().
2017-11-21T09:49:40.842723Z 0 [Note] InnoDB: Highest supported file format is Barracuda.
2017-11-21T09:49:40.892738Z 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2017-11-21T09:49:40.892796Z 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2017-11-21T09:49:40.914698Z 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
2017-11-21T09:49:40.915321Z 0 [Note] InnoDB: 96 redo rollback segment(s) found. 96 redo rollback segment(s) are active.
2017-11-21T09:49:40.915331Z 0 [Note] InnoDB: 32 non-redo rollback segment(s) are active.
2017-11-21T09:49:40.915662Z 0 [Note] InnoDB: Waiting for purge to start
2017-11-21T09:49:40.965925Z 0 [Note] InnoDB: 5.7.20 started; log sequence number 10183455
2017-11-21T09:49:40.966296Z 0 [Note] Plugin 'FEDERATED' is disabled.
2017-11-21T09:49:40.967059Z 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
2017-11-21T09:49:40.973955Z 0 [Note] InnoDB: Buffer pool(s) load completed at 171121  9:49:40
2017-11-21T09:49:40.985481Z 0 [Warning] Failed to set up SSL because of the following SSL library error: SSL context is not usable without certificate and private key
2017-11-21T09:49:40.985500Z 0 [Note] Server hostname (bind-address): '0.0.0.0'; port: 3306
2017-11-21T09:49:40.985512Z 0 [Note]   - '0.0.0.0' resolves to '0.0.0.0';
2017-11-21T09:49:40.985537Z 0 [Note] Server socket created on IP: '0.0.0.0'.
2017-11-21T09:49:41.006320Z 0 [Note] Event Scheduler: Loaded 0 events
2017-11-21T09:49:41.006439Z 0 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.7.20-0ubuntu0.16.04.1-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
2017-11-21T09:49:41.006445Z 0 [Note] Executing 'SELECT * FROM INFORMATION_SCHEMA.TABLES;' to get a list of tables using the deprecated partition engine. You may use the startup option '--disable-partition-engine-check' to skip this check.
2017-11-21T09:49:41.006452Z 0 [Note] Beginning of list of non-natively partitioned tables
2017-11-21T09:49:41.040732Z 0 [Note] End of list of non-natively partitioned tables
2017-11-21T09:49:41.663262Z 3 [Note] Acceso negado para usuario: 'root'@'localhost' (Usando clave: NO)
alu5906@server:/var/log/mysql$

```

En este fichero nos muestra los errores que puede tener mysql.


### 2. Indica al servidor en "my.cnf" que registre los errores en un fichero llamado "server_error". Reinicia el servidor y comprueba los mensajes visualizando dicho fichero.

### 3. Detén el servidor abruptamente (haz lo que sea necesario) y comprueba cómo se ha modificado dicho fichero.

### 4. Prueba la función "perror" incluida en el directorio bin. ¿Cuál es su objeto? Puedes consultar http://dev.mysql.com/doc/refman/5.7/en/perror.html


## Ficheros LOG: General Query LOG

El fichero "Global Query  Log" registra las conexiones establecidas por los clientes y las sentencias ejecutadas por ellos.

Haz la lectura de la siguiente página y contesta a las preguntas razonadamente:

- MySQL Server Logs: http://dev.mysql.com/doc/refman/5.7/en/server-logs.html

- The General Query Log: http://dev.mysql.com/doc/refman/5.7/en/query-log.html

### 1. Explica qué es y para qué sirve el "GENERAL QUERY LOG"

### 2. Configura MySQL para registrar consultas generales en el fichero denominado "miserver.log". Comprueba su funcionamiento haciendo que un compañero se conecte a tu servidor y ejecute varias consultas.

### 3. Averigua viendo el fichero "miserver.log" la hora en que se conectó tu compañero y ejecutó las consultas del apartado anterior.

### 4. Accede al servidor a través de Workbench. ¿Qué se registra en "general_log"?¿Hay alguna diferencia respecto al cliente mysql ?
