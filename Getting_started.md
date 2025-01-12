# Getting Started with MySQL

## Start MySQL
```bash
sudo mysql # start MySQL
```

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
show tables;
describe table_name;
insert into table_name values (1, "name", 25);
```