# mysql-cli-helper
Helps run SQL commands via CLI on several DB
# Installation and Setup
Add the tool as a dev dependency to your project
```sh
composer config repositories.saganov vcs https://github.com/saganov/mysql-cli-helper
composer require --dev -- saganov/mysql-cli-helper:dev-master
```
Install the tool. Run the following command from root of your project
```sh
vendor/bin/sql install
```
You will be prompted for the MySQL credentials and the installator create configuration file `ROOT/bin/db/.my.local.cnf`
for MySQL client and a shortcut in `ROOT/bin/db/local`.
With thefollowing command you could create as many DB configs with shortcuts as you need
```sh
vendor/vin/sql install <environment>
```
# Usage
There are several commands:
- `sql` - run any SQL statement that are followed by the command itself. Example:
```sh
bin/db/local sql "show tables"
```
Take into account that SQL statements have to be enclosed by quotes.
- `dump` - run `mysqldump` command for specified environment. Example:
```sh
bin/db/local dump > my-db-dump.sql
```
- `recreate` - Drop database and then create it again. Only applicable for local DBs
- `all` - retrieve all records form a table. Example (the following command print all records from table `users`):
```sh
bin/db/local all users
```
Default command is sql, so you can skil the `sql`. Example:
```sh
bin/db/local "select * from users\G"
```
