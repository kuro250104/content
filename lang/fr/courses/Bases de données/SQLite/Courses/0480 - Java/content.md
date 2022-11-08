Dans ce chapitre, vous apprendrez à utiliser SQLite dans les programmes Java.

## Installation

Avant de commencer à utiliser SQLite dans nos programmes Java, vous devez vous assurer que le pilote SQLite JDBC et Java sont installés sur votre machine. Vous pouvez consulter le tutoriel Java pour l'installation de Java sur votre machine. Maintenant, voyons comment configurer le pilote SQLite JDBC.

- Téléchargez la dernière version de sqlite-jdbc-(VERSION).jar depuis le référentiel sqlite-jdbc.
- Ajoutez le fichier jar téléchargé sqlite-jdbc-(VERSION).jar dans votre chemin de classe, ou vous pouvez l'utiliser avec l'option -classpath comme expliqué dans les exemples suivants.

La section suivante suppose que vous avez une petite connaissance des concepts de Java JDBC. Si ce n'est pas le cas, nous vous suggérons de passer une demi-heure avec le tutoriel JDBC pour vous familiariser avec les concepts expliqués ci-dessous.

## Connexion à la base de données

Les programmes Java suivants montrent comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et finalement un objet de base de données sera retourné.

```java
import java.sql.*;

public class SQLiteJDBC {
    public static void main( String args[] ) {
        Connection c = null;

        try {
            Class.forName("org.sqlite.JDBC");
            c = DriverManager.getConnection("jdbc:sqlite:test.db");
        } catch ( Exception e ) {
            System.err.println( e.getClass().getName() + ": " + e.getMessage() );
            System.exit(0);
        }
        System.out.println("Opened database successfully");
    }
}
```

Maintenant, compilons et exécutons le programme ci-dessus pour créer notre base de données **test.db** dans le répertoire courant. Vous pouvez changer votre chemin selon vos besoins. Nous supposons que la version actuelle du pilote JDBC sqlite-jdbc-3.7.2.jar est disponible dans le chemin actuel.

```bash
$javac SQLiteJDBC.java
$java -classpath ".:sqlite-jdbc-3.7.2.jar" SQLiteJDBC
Open database successfully
```

Si vous allez utiliser une machine Windows, vous pouvez compiler et exécuter votre code comme suit -

```java
$javac SQLiteJDBC.java
$java -classpath ".;sqlite-jdbc-3.7.2.jar" SQLiteJDBC
Opened database successfully
```

## Créer un tableau

Le programme Java suivant sera utilisé pour créer une table dans la base de données précédemment créée.

```java
import java.sql.*;

public class SQLiteJDBC {

    public static void main( String args[] ) {
        Connection c = null;
        Statement stmt = null;

        try {
            Class.forName("org.sqlite.JDBC");
            c = DriverManager.getConnection("jdbc:sqlite:test.db");
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
        } catch ( Exception e ) {
            System.err.println( e.getClass().getName() + ": " + e.getMessage() );
            System.exit(0);
        }
        System.out.println("Table created successfully");
    }
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il créera la table COMPANY dans votre **test.db** et le listing final du fichier sera le suivant -

```bash
-rw-r--r--. 1 root root 3201128 Jan 22 19:04 sqlite-jdbc-3.7.2.jar
-rw-r--r--. 1 root root    1506 May  8 05:43 SQLiteJDBC.class
-rw-r--r--. 1 root root     832 May  8 05:42 SQLiteJDBC.java
-rw-r--r--. 1 root root    3072 May  8 05:43 test.db
```

## Opération INSERT

Le programme Java suivant montre comment créer des enregistrements dans la table SOCIÉTÉ créée dans l'exemple ci-dessus.

```java
import java.sql.*;

public class SQLiteJDBC {

   public static void main( String args[] ) {
        Connection c = null;
        Statement stmt = null;

        try {
            Class.forName("org.sqlite.JDBC");
            c = DriverManager.getConnection("jdbc:sqlite:test.db");
            c.setAutoCommit(false);
            System.out.println("Opened database successfully");

            stmt = c.createStatement();
            String sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) " +
                            "VALUES (1, 'Paul', 32, 'California', 20000.00 );"; 
            stmt.executeUpdate(sql);

            sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) " +
                    "VALUES (2, 'Allen', 25, 'Texas', 15000.00 );"; 
            stmt.executeUpdate(sql);

            sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) " +
                    "VALUES (3, 'Teddy', 23, 'Norway', 20000.00 );"; 
            stmt.executeUpdate(sql);

            sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) " +
                    "VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 );"; 
            stmt.executeUpdate(sql);

            stmt.close();
            c.commit();
            c.close();
        } catch ( Exception e ) {
            System.err.println( e.getClass().getName() + ": " + e.getMessage() );
            System.exit(0);
        }
        System.out.println("Records created successfully");
    }
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il créera des enregistrements donnés dans la table SOCIÉTÉ et affichera les deux lignes suivantes : -.

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme Java suivant montre comment récupérer et afficher les enregistrements de la table SOCIÉTÉ créée dans l'exemple ci-dessus.

```java
import java.sql.*;

public class SQLiteJDBC {

    public static void main( String args[] ) {

    Connection c = null;
    Statement stmt = null;
    try {
        Class.forName("org.sqlite.JDBC");
        c = DriverManager.getConnection("jdbc:sqlite:test.db");
        c.setAutoCommit(false);
        System.out.println("Opened database successfully");

        stmt = c.createStatement();
        ResultSet rs = stmt.executeQuery( "SELECT * FROM COMPANY;" );

        while ( rs.next() ) {
            int id = rs.getInt("id");
            String  name = rs.getString("name");
            int age  = rs.getInt("age");
            String  address = rs.getString("address");
            float salary = rs.getFloat("salary");

            System.out.println( "ID = " + id );
            System.out.println( "NAME = " + name );
            System.out.println( "AGE = " + age );
            System.out.println( "ADDRESS = " + address );
            System.out.println( "SALARY = " + salary );
            System.out.println();
        }
        rs.close();
        stmt.close();
        c.close();
    } catch ( Exception e ) {
        System.err.println( e.getClass().getName() + ": " + e.getMessage() );
        System.exit(0);
    }
    System.out.println("Operation done successfully");
    }
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il produit le résultat suivant.

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

Le code Java suivant montre comment utiliser l'instruction UPDATE pour mettre à jour un enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table COMPANY.

```java
import java.sql.*;

public class SQLiteJDBC {

    public static void main( String args[] ) {

    Connection c = null;
    Statement stmt = null;

    try {
        Class.forName("org.sqlite.JDBC");
        c = DriverManager.getConnection("jdbc:sqlite:test.db");
        c.setAutoCommit(false);
        System.out.println("Opened database successfully");

        stmt = c.createStatement();
        String sql = "UPDATE COMPANY set SALARY = 25000.00 where ID=1;";
        stmt.executeUpdate(sql);
        c.commit();

        ResultSet rs = stmt.executeQuery( "SELECT * FROM COMPANY;" );

        while ( rs.next() ) {
            int id = rs.getInt("id");
            String  name = rs.getString("name");
            int age  = rs.getInt("age");
            String  address = rs.getString("address");
            float salary = rs.getFloat("salary");

            System.out.println( "ID = " + id );
            System.out.println( "NAME = " + name );
            System.out.println( "AGE = " + age );
            System.out.println( "ADDRESS = " + address );
            System.out.println( "SALARY = " + salary );
            System.out.println();
        }
        rs.close();
        stmt.close();
        c.close();
    } catch ( Exception e ) {
        System.err.println( e.getClass().getName() + ": " + e.getMessage() );
        System.exit(0);
    }
        System.out.println("Operation done successfully");
    }
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il produit le résultat suivant.

```bash
Opened database successfully
ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 25000.0

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

## Opération DELETE

Le code Java suivant montre comment utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY.

```java
import java.sql.*;

public class SQLiteJDBC {

    public static void main( String args[] ) {
        Connection c = null;
        Statement stmt = null;

        try {
            Class.forName("org.sqlite.JDBC");
            c = DriverManager.getConnection("jdbc:sqlite:test.db");
            c.setAutoCommit(false);
            System.out.println("Opened database successfully");

            stmt = c.createStatement();
            String sql = "DELETE from COMPANY where ID=2;";
            stmt.executeUpdate(sql);
            c.commit();

            ResultSet rs = stmt.executeQuery( "SELECT * FROM COMPANY;" );

            while ( rs.next() ) {
            int id = rs.getInt("id");
            String  name = rs.getString("name");
            int age  = rs.getInt("age");
            String  address = rs.getString("address");
            float salary = rs.getFloat("salary");

            System.out.println( "ID = " + id );
            System.out.println( "NAME = " + name );
            System.out.println( "AGE = " + age );
            System.out.println( "ADDRESS = " + address );
            System.out.println( "SALARY = " + salary );
            System.out.println();
        }
        rs.close();
        stmt.close();
        c.close();
        } catch ( Exception e ) {
            System.err.println( e.getClass().getName() + ": " + e.getMessage() );
            System.exit(0);
        }
        System.out.println("Operation done successfully");
    }
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il produit le résultat suivant.

```bash
Opened database successfully
ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 25000.0

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