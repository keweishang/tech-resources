# MySQL

Useful instructions of MySQL in Mac OS.

## Installation

Download and install MySQL via Homebrew, also install the MySQL service which
allows to run MySQL in the backend. Then reset root password (like `NewPass`).

```
$ brew install mysql
$ brew tap homebrew/services
$ brew services start mysql
$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 26
Server version: 5.7.22 Homebrew

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

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

## Java Connection

Use the following code to check the database connection in Java. You also need
the MySQL Java connector
([Connector/J](https://dev.mysql.com/downloads/connector/j/)):

```java
import java.sql.*;

public class DbCheck {
  public static void main(String[] args) throws Exception {
    String user = "<username>";
    String pass = "<password>";
    String db = "<database>";

    String url = "jdbc:mysql://localhost:3306/" + db;
    url += "?serverTimezone=CET";
    url += "&verifyServerCertificate=false";
    System.out.println("Connecting...");
    try (Connection conn = DriverManager.getConnection(url, user, pass)) {
      System.out.println("Connected to dababase " + db);
      System.out.println("URL=\"" + url + "\"");
    } catch (Exception e) {
      e.printStackTrace();
    }
    System.out.println("Finished");
  }
}
```

Copy the program to your desktop. Then, compile and run. You'll see the
following result if everything works correctly:

```
Desktop $ javac DbCheck.java
Desktop $ java -classpath '.:../Downloads/mysql-connector-java-8.0.11.jar' DbCheck
Connecting...
Connected to dababase telegram
URL="jdbc:mysql://localhost:3306/telegram?serverTimezone=CET&useSSL=false"
Finished
```

## Uninstallation

- <https://community.jaspersoft.com/wiki/uninstall-mysql-mac-os-x>
- <https://gist.github.com/vitorbritto/0555879fe4414d18569d>

## Reference

- <sup>[1]</sup> [Stack Overflow: Can't access mysql from command line mac][so1]
- [Install MySQL on macOS Sierra][2]

[so1]: https://stackoverflow.com/questions/8195418
[2]: https://gist.github.com/nrollr/3f57fc15ded7dddddcc4e82fe137b58e
