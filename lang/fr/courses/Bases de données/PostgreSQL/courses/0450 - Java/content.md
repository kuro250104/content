## Installation

Avant de commencer à utiliser PostgreSQL dans nos programmes Java, nous devons nous assurer que PostgreSQL JDBC et Java sont installés sur la machine. Vous pouvez consulter le tutoriel Java pour l'installation de Java sur votre machine. Voyons maintenant comment configurer le pilote JDBC de PostgreSQL.

- Téléchargez la dernière version de postgresql-(VERSION).jdbc.jar à partir du référentiel postgresql-jdbc.
- Ajoutez le fichier jar téléchargé postgresql-(VERSION).jdbc.jar dans votre chemin de classe, ou vous pouvez l'utiliser avec l'option -classpath comme expliqué ci-dessous dans les exemples.

La section suivante suppose que vous avez une petite connaissance des concepts de Java JDBC. Si ce n'est pas le cas, nous vous suggérons de passer une demi-heure avec le tutoriel JDBC pour vous familiariser avec les concepts expliqués ci-dessous.

## Connection à la base de données

Le code Java suivant montre comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et enfin un objet de base de données sera retourné :

```c
import java.sql.Connection;
import java.sql.DriverManager;

public class PostgreSQLJDBC {
    public static void main(String args[]) {
        Connection c = null;
        try {
            Class.forName("org.postgresql.Driver");
            c = DriverManager
                .getConnection("jdbc:postgresql://localhost:5432/testdb",
                "postgres", "123");
        } catch (Exception e) {
            e.printStackTrace();
            System.err.println(e.getClass().getName()+": "+e.getMessage());
            System.exit(0);
        }
        System.out.println("Opened database successfully");
    }
}
```

Avant de compiler et d'exécuter le programme ci-dessus, trouvez le fichier pg_hba.conf dans votre répertoire d'installation PostgreSQL et ajoutez la ligne suivante :

```bash
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
```

Vous pouvez démarrer/redémarrer le serveur postgres s'il n'est pas en cours d'exécution à l'aide de la commande suivante :

```bash
[root@host]# service postgresql restart
Stopping postgresql service:                               [  OK  ]
Starting postgresql service:                               [  OK  ]
```

Maintenant, compilons et exécutons le programme ci-dessus pour nous connecter à testdb. Ici, nous utilisons postgres comme ID utilisateur et 123 comme mot de passe pour accéder à la base de données. Vous pouvez les modifier en fonction de la configuration de votre base de données. Nous supposons également que la version actuelle du pilote JDBC postgresql-9.2-1002.jdbc3.jar est disponible dans le chemin actuel.

```bash
C:\JavaPostgresIntegration>javac PostgreSQLJDBC.java
C:\JavaPostgresIntegration>java -cp c:\tools\postgresql-9.2-1002.jdbc3.jar;C:\JavaPostgresIntegration PostgreSQLJDBC
Open database successfully
```

## Création d'une table

Le programme Java suivant sera utilisé pour créer une table dans une base de données précédemment ouverte. Assurez-vous que cette table n'existe pas déjà dans votre base de données cible :

```java
import java.sql.*;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;


public class PostgreSQLJDBC {
    public static void main( String args[] ) {
        Connection c = null;
        Statement stmt = null;
        try {
            Class.forName("org.postgresql.Driver");
            c = DriverManager
                .getConnection("jdbc:postgresql://localhost:5432/testdb",
                "manisha", "123");
            System.out.println("Opened database successfully");

            stmt = c.createStatement();
            String sql = "CREATE TABLE COMPANY " +
                "(ID INT PRIMARY KEY     NOT NULL," +
                " NAME           TEXT    NOT NULL, " +
                " AGE            INT     NOT NULL, " +
                " ADDRESS        CHAR(50), " +
                " SALARY         REAL)";
            stmt.executeUpdate(sql);
            stmt.close();
            c.close();
        } catch (Exception e) {
            System.err.println(e.getClass().getName()+": "+ e.getMessage());
            System.exit(0);
        }
        System.out.println("Table created successfully");
    }
}
```

Lorsqu'un programme est compilé et exécuté, il créera la table COMPANY dans la base de données testdb et affichera les deux lignes suivantes :

```bash
Opened database successfully
Table created successfully
```

## INSERT Operation

Le programme Java suivant montre comment créer des enregistrements dans la table SOCIÉTÉ créée dans l'exemple ci-dessus :

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class PostgreSQLJDBC {
    public static void main(String args[]) {
        Connection c = null;
        Statement stmt = null;
        try {
            Class.forName("org.postgresql.Driver");
            c = DriverManager
                .getConnection("jdbc:postgresql://localhost:5432/testdb",
                "manisha", "123");
            c.setAutoCommit(false);
            System.out.println("Opened database successfully");

            stmt = c.createStatement();
            String sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) "
                + "VALUES (1, 'Paul', 32, 'California', 20000.00 );";
            stmt.executeUpdate(sql);

            sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) "
                + "VALUES (2, 'Allen', 25, 'Texas', 15000.00 );";
            stmt.executeUpdate(sql);

            sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) "
                + "VALUES (3, 'Teddy', 23, 'Norway', 20000.00 );";
            stmt.executeUpdate(sql);

            sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) "
                + "VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 );";
            stmt.executeUpdate(sql);

            stmt.close();
            c.commit();
            c.close();
        } catch (Exception e) {
            System.err.println(e.getClass().getName()+": "+ e.getMessage());
            System.exit(0);
        }
        System.out.println("Records created successfully");
    }
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il créera des enregistrements donnés dans la table SOCIÉTÉ et affichera les deux lignes suivantes :

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme Java suivant montre comment nous pouvons récupérer et afficher les enregistrements de notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;


public class PostgreSQLJDBC {
    public static void main( String args[] ) {
        Connection c = null;
        Statement stmt = null;
        try {
            Class.forName("org.postgresql.Driver");
            c = DriverManager
                .getConnection("jdbc:postgresql://localhost:5432/testdb",
                "manisha", "123");
            c.setAutoCommit(false);
            System.out.println("Opened database successfully");

            stmt = c.createStatement();
            ResultSet rs = stmt.executeQuery("SELECT * FROM COMPANY;");
            while (rs.next()) {
                int id = rs.getInt("id");
                String  name = rs.getString("name");
                int age  = rs.getInt("age");
                String  address = rs.getString("address");
                float salary = rs.getFloat("salary");
                System.out.println("ID = " + id);
                System.out.println("NAME = " + name);
                System.out.println("AGE = " + age);
                System.out.println("ADDRESS = " + address);
                System.out.println("SALARY = " + salary);
                System.out.println();
            }
            rs.close();
            stmt.close();
            c.close();
        } catch (Exception e) {
            System.err.println(e.getClass().getName()+": "+ e.getMessage());
            System.exit(0);
        }
        System.out.println("Operation done successfully");
    }
}
```

Lorsque le programme est compilé et exécuté, il produira le résultat suivant :

```bash
Opened database successfully
ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 20000.0

ID = 2
NAME = Allen
AGE = 25
ADDRESS = Texas
SALARY = 15000.0

ID = 3
NAME = Teddy
AGE = 23
ADDRESS = Norway
SALARY = 20000.0

ID = 4
NAME = Mark
AGE = 25
ADDRESS = Rich-Mond
SALARY = 65000.0

Operation done successfully
```

## Opération UPDATE

Le code Java suivant montre comment utiliser l'instruction UPDATE pour mettre à jour n'importe quel enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table COMPANY :

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;


public class PostgreSQLJDBC {
    public static void main( String args[] ) {
        Connection c = null;
        Statement stmt = null;
        try {
            Class.forName("org.postgresql.Driver");
            c = DriverManager
                .getConnection("jdbc:postgresql://localhost:5432/testdb",
                "manisha", "123");
            c.setAutoCommit(false);
            System.out.println("Opened database successfully");

            stmt = c.createStatement();
            String sql = "UPDATE COMPANY set SALARY = 25000.00 where ID=1;";
            stmt.executeUpdate(sql);
            c.commit();

            ResultSet rs = stmt.executeQuery("SELECT * FROM COMPANY;");
            while (rs.next()) {
                int id = rs.getInt("id");
                String  name = rs.getString("name");
                int age  = rs.getInt("age");
                String  address = rs.getString("address");
                float salary = rs.getFloat("salary");
                System.out.println("ID = " + id ;
                System.out.println("NAME = " + name);
                System.out.println("AGE = " + age);
                System.out.println("ADDRESS = " + address);
                System.out.println("SALARY = " + salary);
                System.out.println();
            }
            rs.close();
            stmt.close();
            c.close();
        } catch ( Exception e ) {
            System.err.println(e.getClass().getName()+": "+ e.getMessage());
            System.exit(0);
        }
        System.out.println("Operation done successfully");
    }
}
```

Lorsque le programme est compilé et exécuté, il produira le résultat suivant :

```bash
Opened database successfully
ID = 2
NAME = Allen
AGE = 25
ADDRESS = Texas
SALARY = 15000.0

ID = 3
NAME = Teddy
AGE = 23
ADDRESS = Norway
SALARY = 20000.0

ID = 4
NAME = Mark
AGE = 25
ADDRESS = Rich-Mond
SALARY = 65000.0

ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 25000.0

Operation done successfully
```

## Opération DELETE

Le code Java suivant montre comment nous pouvons utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY :

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;


public class PostgreSQLJDBC6 {
    public static void main( String args[] ) {
        Connection c = null;
        Statement stmt = null;
        try {
            Class.forName("org.postgresql.Driver");
            c = DriverManager
                .getConnection("jdbc:postgresql://localhost:5432/testdb",
                "manisha", "123");
            c.setAutoCommit(false);
            System.out.println("Opened database successfully");

            stmt = c.createStatement();
            String sql = "DELETE from COMPANY where ID = 2;";
            stmt.executeUpdate(sql);
            c.commit();

            ResultSet rs = stmt.executeQuery("SELECT * FROM COMPANY;");
            while (rs.next()) {
                int id = rs.getInt("id");
                String  name = rs.getString("name");
                int age  = rs.getInt("age");
                String  address = rs.getString("address");
                float salary = rs.getFloat("salary");
                System.out.println("ID = " + id);
                System.out.println("NAME = " + name);
                System.out.println("AGE = " + age);
                System.out.println("ADDRESS = " + address);
                System.out.println("SALARY = " + salary);
                System.out.println();
            }
            rs.close();
            stmt.close();
            c.close();
        } catch ( Exception e ) {
            System.err.println(e.getClass().getName()+": "+ e.getMessage());
            System.exit(0);
        }
        System.out.println("Operation done successfully");
    }
}
```

Lorsque le programme est compilé et exécuté, il produira le résultat suivant :

```bash
Opened database successfully
ID = 3
NAME = Teddy
AGE = 23
ADDRESS = Norway
SALARY = 20000.0

ID = 4
NAME = Mark
AGE = 25
ADDRESS = Rich-Mond
SALARY = 65000.0

ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 25000.0
Operation done successfully
```
