# SQL Basic commands
- Use `;` after completed commands.
- Use `,` when continuing or adding more.
- Use `()` for parentheses, e.g., adding rows, columns, and numbers.
- `int` - integer. Use AUTO_INCREMENT with it for unique numbers
- `varchar` - variable character or strings.
- `describe` to show details about tables.
- Defining the table with columns and rows is defining the schema or how our database is arranged.
- Write strings in `""`.
- `insert into` inserts data into the specified table.
- `select` pulls data from tables.
- Use `*` wildcard to pull everything from the table.
- `asc` = ascending, `desc` = descending.
- `alter` to change a table that is already created.
- `boolean` = true/false (1 = true, 0 = false).
- `ctrl+l` = clear screen
- `now())` = for current date and time 

## Additional Commands
- `update` to modify existing records in a table.
```bash
update table_name set column1 = value1, column2 = value2 where condition;
```
- `delete` to remove records from a table.
```bash
delete from table_name where condition;
```
- `drop table` to delete a table.
```bash
drop table table_name;
```
- `drop database` to delete a database.
```bash
drop database db_name;
```