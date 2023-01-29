Utilizará a base _sakila_, disponibilizada pelo time do MySql
[Baixar aqui](https://dev.mysql.com/doc/index-other.html)

**MySql Client**

```bash
source c:\seudir\sakila-db\sakila-schema.sql
source c:\seudir\sakila-db\sakila-data.sql
```

**CMD**
```bash
mysql -u admin -p
MYSQL > show databases;
MYSQL > use sakila;
Database changed
```

#### MySQL Data Types

Character can be stored as either:
- char(20) -- fixed-length
- varchar(20) -- variable-length

Exemplo:

```sql
mysql> CREATE TABLE vc (v VARCHAR(4), c CHAR(4));
mysql> INSERT INTO vc VALUES('AB     ','AB    ');
mysql> SELECT CONCAT('(',v,')'), CONCAT('(',c,')') FROM VC;
+-------------------+-------------------+
| CONCAT('(',v,')') | CONCAT('(',c,')') |
+-------------------+-------------------+
| (AB  )            | (AB)              |
+-------------------+-------------------+
```

VARCHAR permite espaços em branco

Caso precise armazenar strings maiores(emails, docs XML, etc.), é recomendado o tipo texto
como _mediumtext_ e _longtext_

Quando utilizar char:
- Todas as strings que serão armazenadas são do mesmo tamanho

Quando utilizar _varchar_:
- Todas as strings que serão armazenadas são de tamanho variado

[Doc Ref](https://dev.mysql.com/doc/refman/8.0/en/char.html)

#### Numeric Data

_MySQL integer types_

|Type|Signed range|unsigned range|
|---|---|---|
|tinyint|-128 to 127|0 to 255|
|smallint|-21,768 to 32,767|0 to 65,535|
|mediumint|-8,388,608 to 8,388,607|0 to 16,777,215|
|int|-2,147,483,648 to 2,147,483,647|0 to 4,294,967,295|
|bigint|-2^63 to 2^63 - 1|0 to 2^64 - 1|

_MySQL floating-point types_
|Type|Numeric range|
|---|---|
|float( p, s )|-3.402823466E+38 to -1.175494351E-38|
|double( p,s )|-1.797693134862315E+308 to -2.250738585072014E-308 and 2.225073858072
014E-308 to 1.79769931348623157E+308|

#### Temporal Data

_MySQL temporal types_

|Type|Default format|Allowable values|
|---|---|---|
|date|YYYY-MM-DD|1000-01-01 to 9999-12-31|
|datetime|YYY-MM-DD HH:MI:SS|1000-01-01 00:00:00.000000|
|timestamp|YYYY-MM-DD HH:MI:SS|1970-01-01 00:00:00000 to 2038-01-18 22:14:07.999999|
|year|YYYY|1901 to 2155|
|time|HHH:MI:SS|-838:59:59.000000 to 838:59:59.000000|


