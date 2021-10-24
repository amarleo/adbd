# INFORME: "Introducción a PostgreSQL"

## INDICE

1. [Introducción](#introducción)
2. [Uso de comandos útiles](#uso-de-comandos-útiles)  
    2.1. [Creación de un usuario](#creación-de-un-usuario)  
    2.2. [Creación de Bases de datos y tablas](#creación-de-bases-de-datos-y-tablas)  
    2.3. [Otros comandos útiles](#otros-comandos-útiles)
1. [Ejemplo de pruebas](#ejemplo-de-pruebas)
4. [Referencias](#referencias)
***
## Introducción
***

**PostgreSQL** es un sistema de gestión de bases de datos relacional orientado a objetos. Se trata de un programa *open source*, contando con una comunidad de desarrolladores que trabajan en mejorar el programa de forma desinteresada. Tiene su origen en el año 1982, siendo este proyecto liderado por [Michael Stonebraker](https://es.wikipedia.org/wiki/Michael_Stonebraker). 

***
## Instalación y acceso
***

A continuación, se procederá a detallar todos los pasos llevados a cabo para realizar la instalación de PostgreSQL. En este caso, se hará uso de una Máquina Virtual, proporcionada por el [IaaS](https://iaas.ull.es) de la ULL.

Una vez iniciada la misma, y después de haber actualizado a través del comando ```sudo apt update```, se procede a usar la siguiente sentencia: 

```sudo apt-get install postgresql```

Una vez terminada la instalación, se procederá a acceder al entorno de postgreSQL. Para ello: 

```sudo su postgres```

A través de la terminal se podrá visualizar algo parecido a lo siguiente: 

![Imágen1](/img/img1.png)

De esta forma se cambian las credenciales del usuario al superusuario de postgreSQL, identificado como "postgres". Desde ahí, se procederá a acceder al programa **psql**

```psql -U <usuario>```

Sustituyendo en el comando anterior el parámetro *usuario* por *postgres* se accederá al programa desde el superusuario de PostgreSQL. Se mostrará por la terminal el siguiente resultado: 

![Imagen2](/img/img2.png)

***
## Uso de comandos útiles
***

Una vez realizada apropiadamente la instalación y accedido al programa **psql** se procederá a detallar con claridad algunos de los comandos que permite utilizar PostgreSQL.

***
### Creación de un usuario
***

Desde un primer momento, en la instalación de PostgreSQL, se crea en el sistema el superusuario **postgre**. Con él, se pueden crear además diferentes usuarios. Para crear un usuario se hace uso del siguiente comando: 

```
CREATE USER <usuario> WITH PASSWORD '<contraseña>';
```

Para crearlo sin contraseña: 

```
CREATE USER <usuario>;
```

Se sustituirá el parámetro **usuario** por el nombre que identificará al usuario y el parámetro **contraseña**, por la clave de acceso del mismo, contenida entre comillas simples. Un ejemplo del mismo se muestra a continuación: 

![imagen4](/img/img4.png)

Además, por cada usuario se han de poder establecer y modificar roles para los mismos. Aprovechando la creación del usuario anterior, establecido por defecto sin contraseña, se mostrará a continuación el procedimiento para establecerle un credencial al mismo:

![imagen7](/img/img7.png)

Los usuarios que han sido creados se pueden listar, para conseguir esto se ha de hacer uso del comando ``` \du ```, el cuál mostrará por la terminal el listado siguiente: 

![imagen5](/img/img5.png)

En este listado ofrece información adicional sobre cada usuario, como es su lista de roles, así como de las tablas de las que son miembros.
Los usuarios además se pueden eliminar, para ello se puede hacer uso de la siguiente sentencia: 

```
DROP USER <nombre>;
```

![imagen6](/img/img6.png)

***
### Creación de Bases de datos y tablas
***

Después de conocer los pasos para la creación de usuarios, es de importancia conocer cuáles son los procedimientos llevados a cabo para la creación de las bases de datos, con sus respectivas tablas. En primer lugar, se procede a crear una base de datos, utilizando el siguiente comando: 

```CREATE DATABASE <nombre_bd>```

Donde se sustituirá **nombre_db** por el nombre que identificará a la base de datos deseada. Esta base de datos por defecto se encontrará vacía, es por ello que para crear las tablas correspondientes a la misma será necesario seleccionar previamente la base de datos deseada. Para ello, se hace uso del comando: 

```\c <nombre_db>```

El cuál seleccionará la base de datos indicada, pudiendo así hacer cambios sobre la misma. Ahora, es momento de crear la primera tabla de la base de datos, para ello: 

```
CREATE TABLE <nombre_tabla> (
    <nombre_atributo> <tipo_atributo>
    . . .
    . . .

);
```

Por último, será necesario insertar las tuplas que complementarán la tabla. PAra realizar esta tarea se hace uso de las sentencias: 

```
INSERT INTO <nombre_tabla>(<columna1>, <columna2>, ...) VALUES (<valor1>, <valor2>, ...);
```

Un ejemplo más detallado de esto se podrá ver en el apartado [Ejemplo de pruebas](#ejemplo-de-pruebas).


***
### Otros comandos útiles
***

A continuación se detallarán una serie de comandos que pueden resultar de utilidad en el uso de PosgreSQL.

 - Listar las bases de datos: Esto se puede lograr con el comando \l: 

![imagen8](/img/img8.png)

 - Conectar a una base de datos: Se puede conectar a una base de datos a través del siguiente comando:  

 ```\c <nombre_basededatos>```

![imagen20](/img/img20.png)
 
 Esto permitirá poder acceder a las tablas de la misma, así como realizar los cambios pertinentes en la composición de la Base de Datos. Además, se puede especificar un usuario para acceder a la misma con él. 

 - Listar las tablas en la base de datos actual: 

 Dentro de una base de datos, se puede listar todas las tablas que la componen, de la siguiente manera: 

 ```\dt```

 ![img20](/img/img21.png)

 - Comando para la ayuda: 

El comando ```\?``` proporcionará un listado de los comandos de psql, con una breve descripción del mismo. Se podrá ver a continuación una pequeña parte de lo que muestra por la terminal: 

![img22](/img/img22.png)

Además, existe el comando ```\h <comando>``` que proporcionará una ayuda detallada del comando que se le proporcione, como por ejemplo: 

![img23](/img/img23.png)

 - Grabar el histórico de comandos:

 Para grabar el histórico de comandos se usará la sentencia: ```\s```

 - Ejecutar comandos desde un fichero:

 Con el comando ```\i <ruta_fichero>``` se podrán ejecutar scripts.

 - Salir: ```\q```

***
## Ejemplo de pruebas
***

Después de esta introducción a PosgreSQL, se va a proponer un pequeño ejemplo de creación de bases de datos y tablas, así como inserciones de valores en las mismas. 

En primer lugar, se procede a crear la base de datos de ejemplo. Para ello, se hará uso del comando: 

```
CREATE DATABASE <basededatos>;
```

Donde se sustituirá el parámetro **basesdedatos** por el nombre de la base de datos deseada. De esta forma: 

![imagen9](/img/img9.png)

Para comprobar que la base de datos ha sido creada se procederá a hacer uso del comando ```\l```.

![imagen10](/img/img10.png)

En el ejemplo anterior se muestran dos usos del comando ```\l```, donde en el primero se muestran todas las bases de datos creadas. En el segundo ejemplo, el comando se encuentra seguido del nombre de la base de datos a listar.

A continuación, se procederá a crear una tabla dentro de la base de datos creada con anterioridad. Para ello, se ha de seleccionar en primer lugar la base de datos a editar. Para ello, se hace uso del comando anteriormente detallado ```\c <nombre_basededatos>```.

Una vez seleccionada, se procede a crear la tabla. Para ello, se hará uso de la sintaxis siguiente: 

```
CREATE TABLE <nombre_tabla> (
    <nombre_atributo> <tipo_atributo>
    . . .
    . . .

);
```
Una vez vista la sintaxis, se procede a mostrar el ejemplo:

![imagen11](/img/img11.png)

En la imágen anterior se aprecia el uso del comando ```\d <nombre_tabla>```, el cuál mostrará toda la información referente a la misma.

Una vez creada la tabla con todos los atributos deseados, se procederá a la introdución de datos en la misma. Para llevar a cabo esta tarea, se hará uso del comando: 

```
INSERT INTO <nombre_tabla>(<columna1>, <columna2>, ...) VALUES (<valor1>, <valor2>, ...);
```
Se mostrará a continuación ejemplo llevado a cabo sobre la tabla **usuarios**

![imagen12](/img/img13.png)

Y para mostrar el contenido de la tabla, haciendo uso de SQL: 

![imagen13](/img/img12.png)

***
## Referencias
***

1. [Cheat Sheet Markdown](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

2. [¿Qué es PostgreSQL?](https://ayudaleyprotecciondatos.es/bases-de-datos/que-es-postgresql-ventajas/)

3. [Enlace Wikipedia Michael Stonebraker](https://es.wikipedia.org/wiki/Michael_Stonebraker)

4. [Insert PSQL](https://www.postgresqltutorial.com/postgresql-insert/)

5. [Commonly used commands PSQL](http://postgresguide.com/utilities/psql.html)

[VOLVER AL INICIO](#indice)