Dans ce chapitre, vous apprendrez à utiliser SQLite dans les programmes C/C++.

## Installation

Avant de commencer à utiliser SQLite dans nos programmes C/C++, vous devez vous assurer que la bibliothèque SQLite est installée sur la machine. Vous pouvez consulter le chapitre Installation de SQLite pour comprendre le processus d'installation.

## C/C++ Interface APIs

Voici les principales routines d'interface SQLite C/C++, qui peuvent répondre à vos besoins pour travailler avec la base de données SQLite depuis votre programme C/C++. Si vous cherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle de SQLite.

**API & Description**

- ```sqlite3_open(const char *filename, sqlite3 **ppDb)``` - Cette routine ouvre une connexion à un fichier de base de données SQLite et retourne un objet de connexion de base de données à utiliser par d'autres routines SQLite. Si l'argument filename est NULL ou ':memory:', sqlite3_open() créera une base de données en mémoire dans la RAM qui ne durera que le temps de la session. Si le nom du fichier n'est pas NULL, sqlite3_open() tente d'ouvrir le fichier de la base de données en utilisant sa valeur. Si aucun fichier de ce nom n'existe, sqlite3_open() ouvrira un nouveau fichier de base de données de ce nom.
- ```sqlite3_exec(sqlite3*, const char *sql, sqlite_callback, void *data, char **errmsg)``` - Cette routine fournit un moyen rapide et facile d'exécuter les commandes SQL fournies par l'argument sql qui peut être composé de plus d'une commande SQL. Ici, le premier argument sqlite3 est un objet de base de données ouvert, sqlite_callback est un call back pour lequel data est le 1er argument et errmsg sera retourné pour capturer toute erreur soulevée par la routine. La routine ```SQLite3_exec()``` analyse et exécute chaque commande donnée dans l'argument sql jusqu'à ce qu'elle atteigne la fin de la chaîne ou rencontre une erreur.
- ```sqlite3_close(sqlite3*)``` - Cette routine ferme une connexion à une base de données précédemment ouverte par un appel à ```sqlite3_open()```. Toutes les requêtes préparées associées à la connexion doivent être finalisées avant de fermer la connexion. S'il reste des requêtes qui n'ont pas été finalisées, ```sqlite3_close()``` retournera SQLITE_BUSY avec le message d'erreur Unable to close due to unfinalized statements.

## Connexion à la base de données

Le segment de code C suivant montre comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et finalement un objet de base de données sera retourné.

```c
#include <stdio.h>
#include <sqlite3.h> 

int main(int argc, char* argv[]) {
    sqlite3 *db;
    char *zErrMsg = 0;
    int rc;

    rc = sqlite3_open("test.db", &db);

    if( rc ) {
        fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
        return(0);
    } else {
        fprintf(stderr, "Opened database successfully\n");
    }
    sqlite3_close(db);
}
```

Maintenant, compilons et exécutons le programme ci-dessus pour créer notre base de données **test.db** dans le répertoire courant. Vous pouvez changer votre chemin selon vos besoins.

```bash
$gcc test.c -l sqlite3
$./a.out
Opened database successfully
```

Si vous allez utiliser le code source C++, vous pouvez compiler votre code comme suit -

```bash
$g++ test.c -l sqlite3
```

Ici, nous lions notre programme avec la bibliothèque sqlite3 pour fournir les fonctions requises au programme C. Cela va créer un fichier de base de données test.db dans votre répertoire et vous aurez le résultat suivant.

```bash
-rwxr-xr-x. 1 root root 7383 May 8 02:06 a.out
-rw-r--r--. 1 root root  323 May 8 02:05 test.c
-rw-r--r--. 1 root root    0 May 8 02:06 test.db
```

## Créer un tableau

Le segment de code C suivant sera utilisé pour créer une table dans la base de données précédemment créée -

```c
#include <stdio.h>
#include <stdlib.h>
#include <sqlite3.h> 

static int callback(void *NotUsed, int argc, char **argv, char **azColName) {
    int i;
    for(i = 0; i<argc; i++) {
        printf("%s = %s\n", azColName[i], argv[i] ? argv[i] : "NULL");
    }
    printf("\n");
    return 0;
}

int main(int argc, char* argv[]) {
    sqlite3 *db;
    char *zErrMsg = 0;
    int rc;
    char *sql;

    /* Open database */
    rc = sqlite3_open("test.db", &db);
    
    if( rc ) {
        fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
        return(0);
    } else {
        fprintf(stdout, "Opened database successfully\n");
    }

    /* Create SQL statement */
    sql = "CREATE TABLE COMPANY("  \
        "ID INT PRIMARY KEY     NOT NULL," \
        "NAME           TEXT    NOT NULL," \
        "AGE            INT     NOT NULL," \
        "ADDRESS        CHAR(50)," \
        "SALARY         REAL );";

    /* Execute SQL statement */
    rc = sqlite3_exec(db, sql, callback, 0, &zErrMsg);
    
    if( rc != SQLITE_OK ){
        fprintf(stderr, "SQL error: %s\n", zErrMsg);
        sqlite3_free(zErrMsg);
    } else {
        fprintf(stdout, "Table created successfully\n");
    }
    sqlite3_close(db);
    return 0;
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il créera la table COMPANY dans votre test.db et le listing final du fichier sera le suivant -

```bash
-rwxr-xr-x. 1 root root 9567 May 8 02:31 a.out
-rw-r--r--. 1 root root 1207 May 8 02:31 test.c
-rw-r--r--. 1 root root 3072 May 8 02:31 test.db
```

## Opération INSERT

Le segment de code C suivant montre comment créer des enregistrements dans la table SOCIÉTÉ créée dans l'exemple ci-dessus -.

```c
#include <stdio.h>
#include <stdlib.h>
#include <sqlite3.h> 

static int callback(void *NotUsed, int argc, char **argv, char **azColName) {
    int i;
    for(i = 0; i<argc; i++) {
        printf("%s = %s\n", azColName[i], argv[i] ? argv[i] : "NULL");
    }
    printf("\n");
    return 0;
}

int main(int argc, char* argv[]) {
    sqlite3 *db;
    char *zErrMsg = 0;
    int rc;
    char *sql;

    /* Open database */
    rc = sqlite3_open("test.db", &db);
    
    if( rc ) {
        fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
        return(0);
    } else {
        fprintf(stderr, "Opened database successfully\n");
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

    /* Execute SQL statement */
    rc = sqlite3_exec(db, sql, callback, 0, &zErrMsg);
    
    if( rc != SQLITE_OK ){
        fprintf(stderr, "SQL error: %s\n", zErrMsg);
        sqlite3_free(zErrMsg);
    } else {
        fprintf(stdout, "Records created successfully\n");
    }
    sqlite3_close(db);
    return 0;
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il créera les enregistrements donnés dans le tableau de la SOCIÉTÉ et affichera les deux lignes suivantes -

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Avant de passer à l'exemple concret de récupération d'enregistrements, examinons quelques détails sur la fonction de rappel, que nous utilisons dans nos exemples. Cette fonction de rappel permet d'obtenir les résultats des instructions SELECT. Elle a la déclaration suivante -

```c
typedef int (*sqlite3_callback)(
    void*,    /* Data provided in the 4th argument of sqlite3_exec() */
    int,      /* The number of columns in row */
    char**,   /* An array of strings representing fields in the row */
    char**    /* An array of strings representing column names */
);
```

Si la fonction de rappel ci-dessus est fournie dans la routine ```sqlite_exec()``` comme troisième argument, SQLite appellera cette fonction de rappel pour chaque enregistrement traité dans chaque instruction SELECT exécutée dans l'argument SQL.

Le segment de code C suivant montre comment vous pouvez récupérer et afficher les enregistrements de la table SOCIÉTÉ créée dans l'exemple ci-dessus.

```c
#include <stdio.h>
#include <stdlib.h>
#include <sqlite3.h> 

static int callback(void *data, int argc, char **argv, char **azColName){
    int i;
    fprintf(stderr, "%s: ", (const char*)data);
    
    for(i = 0; i<argc; i++){
        printf("%s = %s\n", azColName[i], argv[i] ? argv[i] : "NULL");
    }
    
    printf("\n");
    return 0;
}

int main(int argc, char* argv[]) {
    sqlite3 *db;
    char *zErrMsg = 0;
    int rc;
    char *sql;
    const char* data = "Callback function called";

    /* Open database */
    rc = sqlite3_open("test.db", &db);
    
    if( rc ) {
        fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
        return(0);
    } else {
        fprintf(stderr, "Opened database successfully\n");
    }

    /* Create SQL statement */
    sql = "SELECT * from COMPANY";

    /* Execute SQL statement */
    rc = sqlite3_exec(db, sql, callback, (void*)data, &zErrMsg);
    
    if( rc != SQLITE_OK ) {
        fprintf(stderr, "SQL error: %s\n", zErrMsg);
        sqlite3_free(zErrMsg);
    } else {
        fprintf(stdout, "Operation done successfully\n");
    }
    sqlite3_close(db);
    return 0;
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il produit le résultat suivant.

```bash
Opened database successfully
Callback function called: ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 20000.0

Callback function called: ID = 2
NAME = Allen
AGE = 25
ADDRESS = Texas
SALARY = 15000.0

Callback function called: ID = 3
NAME = Teddy
AGE = 23
ADDRESS = Norway
SALARY = 20000.0

Callback function called: ID = 4
NAME = Mark
AGE = 25
ADDRESS = Rich-Mond
SALARY = 65000.0

Operation done successfully
```

## Opération UPDATE

Le segment de code C suivant montre comment utiliser l'instruction UPDATE pour mettre à jour un enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table COMPANY.

```c
#include <stdio.h>
#include <stdlib.h>
#include <sqlite3.h> 

static int callback(void *data, int argc, char **argv, char **azColName){
    int i;
    fprintf(stderr, "%s: ", (const char*)data);
    
    for(i = 0; i<argc; i++) {
        printf("%s = %s\n", azColName[i], argv[i] ? argv[i] : "NULL");
    }
    printf("\n");
    return 0;
}

int main(int argc, char* argv[]) {
    sqlite3 *db;
    char *zErrMsg = 0;
    int rc;
    char *sql;
    const char* data = "Callback function called";

    /* Open database */
    rc = sqlite3_open("test.db", &db);
    
    if( rc ) {
        fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
        return(0);
    } else {
        fprintf(stderr, "Opened database successfully\n");
    }

    /* Create merged SQL statement */
    sql = "UPDATE COMPANY set SALARY = 25000.00 where ID=1; " \
            "SELECT * from COMPANY";

    /* Execute SQL statement */
    rc = sqlite3_exec(db, sql, callback, (void*)data, &zErrMsg);
    
    if( rc != SQLITE_OK ) {
        fprintf(stderr, "SQL error: %s\n", zErrMsg);
        sqlite3_free(zErrMsg);
    } else {
        fprintf(stdout, "Operation done successfully\n");
    }
    sqlite3_close(db);
    return 0;
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il produit le résultat suivant.

```bash
Opened database successfully
Callback function called: ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 25000.0

Callback function called: ID = 2
NAME = Allen
AGE = 25
ADDRESS = Texas
SALARY = 15000.0

Callback function called: ID = 3
NAME = Teddy
AGE = 23
ADDRESS = Norway
SALARY = 20000.0

Callback function called: ID = 4
NAME = Mark
AGE = 25
ADDRESS = Rich-Mond
SALARY = 65000.0

Operation done successfully
```

## Opération DELETE

Le segment de code C suivant montre comment vous pouvez utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY.

```c
#include <stdio.h>
#include <stdlib.h>
#include <sqlite3.h> 

static int callback(void *data, int argc, char **argv, char **azColName) {
    int i;
    fprintf(stderr, "%s: ", (const char*)data);
    
    for(i = 0; i<argc; i++) {
        printf("%s = %s\n", azColName[i], argv[i] ? argv[i] : "NULL");
    }
    printf("\n");
    return 0;
}

int main(int argc, char* argv[]) {
    sqlite3 *db;
    char *zErrMsg = 0;
    int rc;
    char *sql;
    const char* data = "Callback function called";

    /* Open database */
    rc = sqlite3_open("test.db", &db);
    
    if( rc ) {
        fprintf(stderr, "Can't open database: %s\n", sqlite3_errmsg(db));
        return(0);
    } else {
        fprintf(stderr, "Opened database successfully\n");
    }

    /* Create merged SQL statement */
    sql = "DELETE from COMPANY where ID=2; " \
            "SELECT * from COMPANY";

    /* Execute SQL statement */
    rc = sqlite3_exec(db, sql, callback, (void*)data, &zErrMsg);
    
    if( rc != SQLITE_OK ) {
        fprintf(stderr, "SQL error: %s\n", zErrMsg);
        sqlite3_free(zErrMsg);
    } else {
        fprintf(stdout, "Operation done successfully\n");
    }
    sqlite3_close(db);
    return 0;
}
```

Lorsque le programme ci-dessus est compilé et exécuté, il produit le résultat suivant.

```bash
Opened database successfully
Callback function called: ID = 1
NAME = Paul
AGE = 32
ADDRESS = California
SALARY = 20000.0

Callback function called: ID = 3
NAME = Teddy
AGE = 23
ADDRESS = Norway
SALARY = 20000.0

Callback function called: ID = 4
NAME = Mark
AGE = 25
ADDRESS = Rich-Mond
SALARY = 65000.0

Operation done successfully
```