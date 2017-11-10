# MySQL

Useful instructions of MySQL in Mac OS.

## Download

Download the community edition from <https://www.mysql.com/downloads/>.

## Installation

- Open the downloaded `.dmg` file and follow the instruction.
- Password will be prompted, save it somewhere.
- Export the installation path to Bash profile<sup>[1]</sup>:

    ```
    # MySQL
    export PATH="/usr/local/mysql/bin:$PATH"
    ```

- Reload bash profile `source ~/.bash_profile`
- Start the server: Go to _System Preferences_ > _MySQL_ > _Start MySQL Server_
- Open your terminal, check MySQL can be accessed:
  - `mysql -u root -p`, the password will be promted
  - Enter the password saved previously
  - Now you should be able to access the MySQL shell:

```
~ $ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 26
Server version: 5.7.20

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

- Reset the password:

    ```
    mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'NewPass';
    ```

## Creating and Using Database

See <https://dev.mysql.com/doc/refman/5.7/en/database-use.html>.

Create a new database `sonarqube`:

```
mysql> CREATE DATABASE sonarqube;
```

Use database `sonarqube`:

```
mysql> USE sonarqube
```

## User Account Management

See <https://dev.mysql.com/doc/refman/5.7/en/user-account-management.html>.

Create a user `sonarqube`. Grant it to database `sonarqube` with all privileges:

```
mysql> CREATE USER 'sonarqube'@'localhost' IDENTIFIED BY 'password';
mysql> GRANT ALL PRIVILEGES ON sonarqube.* TO 'sonarqube'@'localhost';
mysql> SHOW GRANTS FOR 'sonarqube'@'localhost';
+------------------------------------------------------------------+
| Grants for sonarqube@localhost                                   |
+------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'sonarqube'@'localhost'                    |
| GRANT ALL PRIVILEGES ON `sonarqube`.* TO 'sonarqube'@'localhost' |
+------------------------------------------------------------------+
2 rows in set (0.00 sec)
```

## Reference

- <sup>[1]</sup> [Stack Overflow: Can't access mysql from command line mac][so1]

[so1]: https://stackoverflow.com/questions/8195418
