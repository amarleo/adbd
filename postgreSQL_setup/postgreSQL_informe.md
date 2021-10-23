# INFORME: "Introducción a PostgreSQL"

## Introducción

**PostgreSQL** es un sistema de gestión de bases de datos relacional orientado a objetos. Se trata de un programa *open source*, contando con una comunidad de desarrolladores que trabajan en mejorar el programa de forma desinteresada. Tiene su origen en el año 1982, siendo este proyecto liderado por [Michael Stonebraker](https://es.wikipedia.org/wiki/Michael_Stonebraker). 

## Instalación y acceso

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


## Uso de comandos útiles

Una vez realizada apropiadamente la instalación y accedido al programa **psql** se procederá a detallar con claridad algunos de los comandos que permite utilizar PostgreSQL.



## Ejemplo de pruebas

## Referencias

1. [Cheat Sheet Markdown](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

2. [¿Qué es PostgreSQL?](https://ayudaleyprotecciondatos.es/bases-de-datos/que-es-postgresql-ventajas/)

3. [Enlace Wikipedia Michael Stonebraker](https://es.wikipedia.org/wiki/Michael_Stonebraker)