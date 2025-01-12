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
    id int,
    name varchar(299),
    age int
);
```
# Inserting data in the table 
```bash
show tables;
describe table_name;
insert into table_name values (1, "name", 25);
```
## Pull Data from the Table
```sql
select * from table_name;
select name from table_name;
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

## Alter Table
```sql
alter table table_name add new_column boolean;
```
