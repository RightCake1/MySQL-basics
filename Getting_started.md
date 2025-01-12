# Getting Started with MySQL

## Start MySQL
```bash
sudo mysql # start MySQL
```
## Create user 
```bash
CREATE USER 'someuser'@'localhost' IDENTIFIED BY 'somepassword';
```
## Show all users
```bash
SHOW GRANTS FOR 'someuser'@'localhost';
``` 
## Grant permissions
GRANT ALL PRIVILEGES ON * . * TO 'someuser'@'localhost';
FLUSH PRIVILEGES;

# Delete user
```bash
DROP USER 'someuser'@'localhost';
``` 


