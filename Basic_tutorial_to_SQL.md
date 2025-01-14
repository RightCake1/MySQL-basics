## Make a Database
```sql
show databases;
create database db_name;
use db_name;
```

## Make a Table in the Database
```sql
show tables;
create table table_name (
    id int AUTO_INCREMENT,
    name varchar(299),
    age int
);
```

## Inserting Data in the Table
```sql
show tables;
describe table_name;
insert into table_name values (1, "name", 25);
```

## Pull Data from the Table
```sql
select * from table_name;
select name from table_name;
SELECT DISTINCT location FROM users; 
SELECT * FROM users WHERE dept LIKE 'd%'; 
SELECT * FROM users WHERE dept IN ('design', 'sales');
SELECT * FROM users WHERE age BETWEEN 20 AND 25;
select * from table_name where column_name = value;
select * from table_name where column_name = value or column_name = another_value;
select id from table_name where age < 30;
select * from table_name where not column_name = value;
```

## Remove Data from the Table
```sql
delete from table_name where column_name = value;
```

## Update Data
```sql
update table_name set column_name = new_value where column_name = value;
```

## Sorting
```sql
select * from table_name order by column_name asc;
select * from table_name order by column_name desc;
```

## Generate Truly Random Ages for All Rows in One Command
```sql
UPDATE your_table_name
SET age = FLOOR(RAND() * (50 - 20 + 1)) + 20
WHERE id IN (1, 2, 3, 4, 5, 6, 7);
```

## Alter Table
```sql
alter table table_name add new_column boolean;
```

## Alter Type
```sql
ALTER TABLE users MODIFY COLUMN age INT(3);
```

```sql
ALTER TABLE "table name"
CHANGE COLUMN "oldColumn" "newcolumnName" VARCHAR(255);
```

## Deleting Data
```sql
delete from table_name where condition;
```
```sql
drop table table_name;
```
```sql
drop database db_name;
```

## Concatenate Data
```sql
SELECT CONCAT(first_name, ' ', last_name) AS 'Name', dept FROM users;
```

# Indexing
```bash
CREATE INDEX LIndex On users(location);
DROP INDEX LIndex ON users;
```

# Linking tables
```bash
 PRIMARY KEY(id),
   FOREIGN KEY (user_id) REFERENCES users(id)
```

