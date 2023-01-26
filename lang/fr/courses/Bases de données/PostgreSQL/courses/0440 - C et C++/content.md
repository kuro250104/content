Ce tutoriel va utiliser la bibliothèque libpqxx, qui est l'API client C++ officielle de PostgreSQL. Le code source de libpqxx est disponible sous la licence BSD, vous êtes donc libre de le télécharger, de le transmettre à d'autres, de le modifier, de le vendre, de l'inclure dans votre propre code et de partager vos modifications avec qui vous voulez.

## Installation

La dernière version de libpqxx est disponible pour être téléchargée à partir du lien Télécharger Libpqxx. Alors, téléchargez la dernière version et suivez les étapes suivantes :

```bash
wget http://pqxx.org/download/software/libpqxx/libpqxx-4.0.tar.gz
tar xvfz libpqxx-4.0.tar.gz
cd libpqxx-4.0
./configure
make
make install
```

Avant de commencer à utiliser l'interface PostgreSQL C/C++, trouvez le fichier pg_hba.conf dans votre répertoire d'installation de PostgreSQL et ajoutez la ligne suivante :

```bash
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
```

Vous pouvez démarrer/redémarrer le serveur postgres s'il n'est pas en cours d'exécution à l'aide de la commande suivante -

```bash
[root@host]# service postgresql restart
Stopping postgresql service:                               [  OK  ]
Starting postgresql service:                               [  OK  ]
```

## C/C++ Interface APIs

Les éléments suivants sont des routines d'interface importantes qui peuvent répondre à votre besoin de travailler avec la base de données PostgreSQL depuis votre programme C/C++. Si vous cherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle de libpqxx ou utiliser les API disponibles dans le commerce.

**API & Description**

- ```pqxx::connection C( const std::string & dbstring )``` - Il s'agit d'un typedef qui sera utilisé pour se connecter à la base de données. Ici, ```dbstring``` fournit les paramètres nécessaires pour se connecter à la base de données, par exemple ```dbname=testdb user=postgres password=pass123 hostaddr=127.0.0.1 port=5432```. Si la connexion est établie avec succès, le programme crée un objet de connexion C qui fournit diverses fonctions publiques utiles.
- ```C.is_open()``` - La méthode ```is_open()``` est une méthode publique de l'objet connexion et renvoie une valeur booléenne. Si la connexion est active, alors cette méthode renvoie true, sinon elle renvoie false.
- ```C.disconnect()``` - Cette méthode est utilisée pour déconnecter une connexion ouverte à une base de données.
- ```pqxx::work W( C )``` - Il s'agit d'un typedef qui sera utilisé pour créer un objet transactionnel en utilisant la connexion C, qui sera finalement utilisé pour exécuter des instructions SQL en mode transactionnel. Si l'objet transactionnel est créé avec succès, alors il est assigné à la variable W qui sera utilisée pour accéder aux méthodes publiques liées à l'objet transactionnel.
- ```W.exec(const std::string & sql)``` - Cette méthode publique de l'objet transactionnel sera utilisée pour exécuter la déclaration SQL.
- ```W.commit()``` - Cette méthode publique de l'objet transactionnel sera utilisée pour valider la transaction.
- ```W.abort()``` - Cette méthode publique de l'objet transactionnel sera utilisée pour annuler la transaction.
- ```pqxx::nontransaction N( C )``` - Il s'agit d'un typedef qui sera utilisé pour créer un objet non transactionnel en utilisant la connexion C, qui sera finalement utilisé pour exécuter des instructions SQL en mode non transactionnel. Si l'objet transactionnel est créé avec succès, alors il est assigné à la variable N qui sera utilisée pour accéder aux méthodes publiques liées à l'objet non-transactionnel.
- ```N.exec(const std::string & sql)``` - Cette méthode publique d'un objet non transactionnel sera utilisée pour exécuter une instruction SQL et retourner un objet résultat qui est en fait un interator contenant tous les enregistrements retournés.

## Connexion à la base de données

Le segment de code C suivant montre comment se connecter à une base de données existante fonctionnant sur la machine locale au port 5432. Ici, j'ai utilisé la barre oblique inversée \ pour la continuation de la ligne :

```c
#include <iostream>
#include <pqxx/pqxx> 

using namespace std;
using namespace pqxx;

int main(int argc, char* argv[]) {
    try {
        connection C("dbname = testdb user = postgres password = cohondob \
        hostaddr = 127.0.0.1 port = 5432");
        if (C.is_open()) {
            cout << "Opened database successfully: " << C.dbname() << endl;
        } else {
            cout << "Can't open database" << endl;
            return 1;
        }
        C.disconnect ();
    } catch (const std::exception &e) {
        cerr << e.what() << std::endl;
        return 1;
    }
}
```

Maintenant, compilons et exécutons le programme ci-dessus pour nous connecter à notre base de données ```testdb```, qui est déjà disponible dans votre schéma et à laquelle on peut accéder en utilisant l'utilisateur postgres et le mot de passe pass123.

Vous pouvez utiliser l'ID utilisateur et le mot de passe en fonction des paramètres de votre base de données. Rappelez-vous de garder les ```-lpqxx``` et ```-lpq``` dans l'ordre donné ! Sinon, l'éditeur de liens se plaindra amèrement des fonctions manquantes dont le nom commence par "PQ".

```bash
$g++ test.cpp -lpqxx -lpq
$./a.out
Opened database successfully: testdb
```

## Créer une table

Le segment de code C suivant sera utilisé pour créer une table dans la base de données créée précédemment :

```c
#include <iostream>
#include <pqxx/pqxx> 

using namespace std;
using namespace pqxx;

int main(int argc, char* argv[]) {
    char * sql;
    
    try {
        connection C("dbname = testdb user = postgres password = cohondob \
        hostaddr = 127.0.0.1 port = 5432");
        if (C.is_open()) {
            cout << "Opened database successfully: " << C.dbname() << endl;
        } else {
            cout << "Can't open database" << endl;
            return 1;
        }

        /* Create SQL statement */
        sql = "CREATE TABLE COMPANY("  \
        "ID INT PRIMARY KEY     NOT NULL," \
        "NAME           TEXT    NOT NULL," \
        "AGE            INT     NOT NULL," \
        "ADDRESS        CHAR(50)," \
        "SALARY         REAL );";

        /* Create a transactional object. */
        work W(C);
        
        /* Execute SQL query */
        W.exec( sql );
        W.commit();
        cout << "Table created successfully" << endl;
        C.disconnect ();
    } catch (const std::exception &e) {
        cerr << e.what() << std::endl;
        return 1;
    }

    return 0;
}
```

Lorsque le programme donné ci-dessus est compilé et exécuté, il créera la table COMPANY dans votre base de données ```testdb``` et affichera les déclarations suivantes :

```bash
Opened database successfully: testdb
Table created successfully
```

## Opération INSERT

Le segment de code C suivant montre comment créer des enregistrements dans la table SOCIÉTÉ créée dans l'exemple ci-dessus :

```c
#include <iostream>
#include <pqxx/pqxx> 

using namespace std;
using namespace pqxx;

int main(int argc, char* argv[]) {
    char * sql;
    
    try {
        connection C("dbname = testdb user = postgres password = cohondob \
        hostaddr = 127.0.0.1 port = 5432");
        if (C.is_open()) {
            cout << "Opened database successfully: " << C.dbname() << endl;
        } else {
            cout << "Can't open database" << endl;
            return 1;
        }

        /* Create SQL statement */
        sql = "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) "  \
            "VALUES (1, 'Paul', 32, 'California', 20000.00 ); " \
            "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) "  \
            "VALUES (2, 'Allen', 25, 'Texas', 15000.00 ); "     \
            "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)" \
            "VALUES (3, 'Teddy', 23, 'Norway', 20000.00 );" \
            "INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)" \
            "VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 );";

        /* Create a transactional object. */
        work W(C);
        
        /* Execute SQL query */
        W.exec( sql );
        W.commit();
        cout << "Records created successfully" << endl;
        C.disconnect ();
    } catch (const std::exception &e) {
        cerr << e.what() << std::endl;
        return 1;
    }

    return 0;
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il créera des enregistrements donnés dans la table COMPANY et affichera les deux lignes suivantes :

```bash
Opened database successfully: testdb
Records created successfully
```

## Opération SELECT

Le segment de code C suivant montre comment nous pouvons récupérer et afficher les enregistrements de notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```c
#include <iostream>
#include <pqxx/pqxx> 

using namespace std;
using namespace pqxx;

int main(int argc, char* argv[]) {
    char * sql;

    try {
        connection C("dbname = testdb user = postgres password = cohondob \
        hostaddr = 127.0.0.1 port = 5432");
        if (C.is_open()) {
            cout << "Opened database successfully: " << C.dbname() << endl;
        } else {
            cout << "Can't open database" << endl;
            return 1;
        }

        /* Create SQL statement */
        sql = "SELECT * from COMPANY";

        /* Create a non-transactional object. */
        nontransaction N(C);
        
        /* Execute SQL query */
        result R( N.exec( sql ));
        
        /* List down all the records */
        for (result::const_iterator c = R.begin(); c != R.end(); ++c) {
            cout << "ID = " << c[0].as<int>() << endl;
            cout << "Name = " << c[1].as<string>() << endl;
            cout << "Age = " << c[2].as<int>() << endl;
            cout << "Address = " << c[3].as<string>() << endl;
            cout << "Salary = " << c[4].as<float>() << endl;
        }
        cout << "Operation done successfully" << endl;
        C.disconnect ();
    } catch (const std::exception &e) {
        cerr << e.what() << std::endl;
        return 1;
    }

    return 0;
}
```

Lorsque le programme donné ci-dessus est compilé et exécuté, il produira le résultat suivant :

```bash
Opened database successfully: testdb
ID = 1
Name = Paul
Age = 32
Address = California
Salary = 20000
ID = 2
Name = Allen
Age = 25
Address = Texas
Salary = 15000
ID = 3
Name = Teddy
Age = 23
Address = Norway
Salary = 20000
ID = 4
Name = Mark
Age = 25
Address = Rich-Mond
Salary = 65000
Operation done successfully
```

## Opération UPDATE

Le segment de code C suivant montre comment utiliser l'instruction UPDATE pour mettre à jour n'importe quel enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table SOCIÉTÉ :

```c
#include <iostream>
#include <pqxx/pqxx> 

using namespace std;
using namespace pqxx;

int main(int argc, char* argv[]) {
    char * sql;
    
    try {
        connection C("dbname = testdb user = postgres password = cohondob \
        hostaddr = 127.0.0.1 port = 5432");
        if (C.is_open()) {
            cout << "Opened database successfully: " << C.dbname() << endl;
        } else {
            cout << "Can't open database" << endl;
            return 1;
        }
        
        /* Create a transactional object. */
        work W(C);
        /* Create  SQL UPDATE statement */
        sql = "UPDATE COMPANY set SALARY = 25000.00 where ID=1";
        /* Execute SQL query */
        W.exec( sql );
        W.commit();
        cout << "Records updated successfully" << endl;
        
        /* Create SQL SELECT statement */
        sql = "SELECT * from COMPANY";

        /* Create a non-transactional object. */
        nontransaction N(C);
        
        /* Execute SQL query */
        result R( N.exec( sql ));
        
        /* List down all the records */
        for (result::const_iterator c = R.begin(); c != R.end(); ++c) {
            cout << "ID = " << c[0].as<int>() << endl;
            cout << "Name = " << c[1].as<string>() << endl;
            cout << "Age = " << c[2].as<int>() << endl;
            cout << "Address = " << c[3].as<string>() << endl;
            cout << "Salary = " << c[4].as<float>() << endl;
        }
        cout << "Operation done successfully" << endl;
        C.disconnect ();
    } catch (const std::exception &e) {
        cerr << e.what() << std::endl;
        return 1;
    }

    return 0;
}
```

Lorsque le programme donné ci-dessus est compilé et exécuté, il produira le résultat suivant :

```bash
Opened database successfully: testdb
Records updated successfully
ID = 2
Name = Allen
Age = 25
Address = Texas
Salary = 15000
ID = 3
Name = Teddy
Age = 23
Address = Norway
Salary = 20000
ID = 4
Name = Mark
Age = 25
Address = Rich-Mond
Salary = 65000
ID = 1
Name = Paul
Age = 32
Address = California
Salary = 25000
Operation done successfully
```

## DELETE Operation

Le segment de code C suivant montre comment utiliser l'instruction DELETE pour supprimer n'importe quel enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY :

```c
#include <iostream>
#include <pqxx/pqxx> 

using namespace std;
using namespace pqxx;

int main(int argc, char* argv[]) {
    char * sql;

    try {
        connection C("dbname = testdb user = postgres password = cohondob \
        hostaddr = 127.0.0.1 port = 5432");
        if (C.is_open()) {
            cout << "Opened database successfully: " << C.dbname() << endl;
        } else {
            cout << "Can't open database" << endl;
            return 1;
        }

        /* Create a transactional object. */
        work W(C);
        /* Create  SQL DELETE statement */
        sql = "DELETE from COMPANY where ID = 2";
        /* Execute SQL query */
        W.exec( sql );
        W.commit();
        cout << "Records deleted successfully" << endl;

        /* Create SQL SELECT statement */
        sql = "SELECT * from COMPANY";

        /* Create a non-transactional object. */
        nontransaction N(C);
        
        /* Execute SQL query */
        result R( N.exec( sql ));
        
        /* List down all the records */
        for (result::const_iterator c = R.begin(); c != R.end(); ++c) {
            cout << "ID = " << c[0].as<int>() << endl;
            cout << "Name = " << c[1].as<string>() << endl;
            cout << "Age = " << c[2].as<int>() << endl;
            cout << "Address = " << c[3].as<string>() << endl;
            cout << "Salary = " << c[4].as<float>() << endl;
        }
        cout << "Operation done successfully" << endl;
        C.disconnect ();
    } catch (const std::exception &e) {
        cerr << e.what() << std::endl;
        return 1;
    }

    return 0;
}
```

Lorsque le programme donné ci-dessus est compilé et exécuté, il produira le résultat suivant :

```bash
Opened database successfully: testdb
Records deleted successfully
ID = 3
Name = Teddy
Age = 23
Address = Norway
Salary = 20000
ID = 4
Name = Mark
Age = 25
Address = Rich-Mond
Salary = 65000
ID = 1
Name = Paul
Age = 32
Address = California
Salary = 25000
Operation done successfully
```
