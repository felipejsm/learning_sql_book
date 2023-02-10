
#### Tables

Tipos de tabelas:

- Permanent Tables - criadas utilizando o comando **create table**
- Derived Tables - linhas retornadas de uma _sub-query_ e armazenadas em memória
- Temporary Tables - dados voláteis armazenadas em memória
- Virtual Tables - criadas utilizando o comando **create view**


#### Derived (subquery-generated) tables

Uma _subquery_ is a query dentro de outra query

```sql
mysql> SELECT concat(cust.last_name, ', ', cust.first_name) full_name from (SELECT first_name, last_name, email FROM cus
tomer WHERE first_name = 'JESSIE') cust;
+---------------+
| full_name     |
+---------------+
| BANKS, JESSIE |
| MILAM, JESSIE |
+---------------+
2 rows in set (0.05 sec)
```

#### Temporary tables
São semelhantes às tabelas permanentes mas qualquer dado inserido numa tabela temporária serão descartados em algum momento.
Fim da sessão ou transação


**Criação da tabela temporária**
```sql
mysql> CREATE TEMPORARY TABLE actors_j(actor_id smallint(5), first_name varchar(45), last_name varchar(45));
Query OK, 0 rows affected, 1 warning (0.03 sec)
```

**Inserindo dados**
```sql
mysql> INSERT INTO actors_j SELECT actor_id, first_name, last_name FROM actor WHERE last_name LIKE 'J%';
Query OK, 7 rows affected (0.01 sec)
```

#### Views
É uma query armazenada no dicionário de dados
Não há nenhum dado associado a ele

**Criação**
```sql
mysql> CREATE VIEW cust_vw AS SELECT customer_id, first_name, last_name, active FROM customer;
Query OK, 0 rows affected (0.04 sec)
```

**Busca**

```sql
mysql> SELECT first_name, last_name FROM cust_vw WHERE active = 0;
```

Usado para simplificar, esconder colunas dos usuários

**Table links**

Unindo múltiplas tabelas
Exemplo simples(**INNER JOIN**)

```sql
SELECT customer.first_name, customer.last_name, time(rental.rental_date) rental_time
FROM customer
	INNER JOIN rental
	ON customer.customer_id = rental.customer_id
WHERE date(rental.rental_date) = '2005-06-14';
```
