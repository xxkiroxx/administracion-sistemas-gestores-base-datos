# Triggers en MySQL

![](img/000.png)

## 1. Crear una base de datos llamada Banco. Dentro de Banco, crear una tabla llamada cuentas que va a tener dos campos, número de cuenta (entero y clave primaria) y saldo (10 partes enteras y 2 partes decimales)


Primero tenemos que crear una base de datos que se llame `banco`.

```console

create database banco;

```

Luego creamos la tabla de `cuenta` y dos campos:

- `numero_cuenta`: Entero y Clave primaria.
- `saldo`: 10 partes enteras y 2 decimales.

```console

use banco;

create table cuentas(
	numero_cuenta int,
	primary key(numero_cuenta),
    saldo decimal(10,2))
```
- Comprobamos que tenemos creado la base de datos de `banco`

```console
alu5906@server:~$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 6
Server version: 5.7.21-0ubuntu0.16.04.1-log (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| COMERCIO           |
| banco              |
| bd_disparadores    |
| jardineria         |
| mysql              |
| performance_schema |
| phpmyadmin         |
| prueba             |
| sakila             |
| sys                |
+--------------------+
11 rows in set (0,00 sec)

mysql>
```

- Ahora vamos a comprobar si tenemos la tabla creada `cuentas`

```console

mysql> use banco;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+-----------------+
| Tables_in_banco |
+-----------------+
| cuentas         |
+-----------------+
1 row in set (0,00 sec)

mysql>
```
