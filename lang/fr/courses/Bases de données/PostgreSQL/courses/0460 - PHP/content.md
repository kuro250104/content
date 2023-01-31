## Installation

L'extension PostgreSQL est activée par défaut dans les dernières versions de PHP 5.3.x. Il est possible de la désactiver en utilisant ```--without-pgsql``` à la compilation. Vous pouvez néanmoins utiliser la commande ```yum``` pour installer l'interface PHP -PostgreSQL.

```bash
yum install php-pgsql
```

Avant de commencer à utiliser l'interface PHP PostgreSQL, trouvez le fichier ```pg_hba.conf``` dans votre répertoire d'installation de PostgreSQL et ajoutez la ligne suivante :

```bash
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
```

Vous pouvez démarrer/redémarrer le serveur postgres, au cas où il ne serait pas en cours d'exécution, à l'aide de la commande suivante :

```bash
[root@host]# service postgresql restart
Stopping postgresql service:                               [  OK  ]
Starting postgresql service:                               [  OK  ]
```

Les utilisateurs de Windows doivent activer php_pgsql.dll afin d'utiliser cette extension. Cette DLL est incluse dans les distributions Windows dans les dernières versions de PHP 5.3.x.

Pour des instructions d'installation détaillées, veuillez consulter notre tutoriel PHP et son site officiel.

## PHP Interface APIs

Voici des routines PHP importantes, qui peuvent répondre à votre besoin de travailler avec la base de données PostgreSQL depuis votre programme PHP. Si vous recherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle de PHP.

**API & Description**

- ```resource pg_connect ( string $connection_string [, int $connect_type ] )``` - Ceci ouvre une connexion à une base de données PostgreSQL spécifiée par la chaîne de connexion (connection_string). Si ```PGSQL_CONNECT_FORCE_NEW``` est passé comme ```connect_type```, alors une nouvelle connexion est créée en cas de second appel à ```pg_connect()```, même si la connection_string est identique à une connexion existante.
- ```bool pg_connection_reset ( resource $connection )``` - Cette routine réinitialise la connexion. Elle est utile pour la récupération des erreurs. Elle renvoie TRUE en cas de succès ou FALSE en cas d'échec.
- ```int pg_connection_status ( resource $connection )``` - Cette routine retourne l'état de la connexion spécifiée. Elle renvoie PGSQL_CONNECTION_OK ou PGSQL_CONNECTION_BAD.
- ```string pg_dbname ([ resource $connection ] )``` - Cette routine retourne le nom de la base de données que la ressource de connexion PostgreSQL donnée.
- ```resource pg_prepare ([ resource $connection ], string $stmtname, string $query )``` - Il soumet une demande de création d'une déclaration préparée avec les paramètres donnés et attend l'achèvement.
- ```resource pg_execute ([ resource $connection ], string $stmtname, array $params )``` - Cette routine envoie une demande d'exécution d'une instruction préparée avec des paramètres donnés et attend le résultat.
- ```resource pg_query ([ resource $connection ], string $query )``` - Cette routine exécute la requête sur la connexion à la base de données spécifiée.
- ```array pg_fetch_row ( resource $result [, int $row ] )``` - Cette routine extrait une ligne de données du résultat associé à la ressource de résultat spécifiée.
- ```array pg_fetch_all ( resource $result )``` - Cette routine renvoie un tableau qui contient toutes les lignes (enregistrements) dans la ressource de résultat.
- ```int pg_affected_rows ( resource $result )``` - Cette routine renvoie le nombre de lignes affectées par les requêtes INSERT, UPDATE et DELETE.
- ```int pg_num_rows ( resource $result )``` - Cette routine retourne le nombre de lignes dans une ressource de résultat PostgreSQL, par exemple le nombre de lignes retournées par l'instruction SELECT.
- ```bool pg_close ([ resource $connection ] )``` - Cette routine ferme la connexion non persistante à une base de données PostgreSQL associée à la ressource de connexion donnée.
- ```string pg_last_error ([ resource $connection ] )``` - Cette routine renvoie le dernier message d'erreur pour une connexion donnée.
- ```string pg_escape_literal ([ resource $connection ], string $data )``` - Cette routine échappe un littéral pour l'insérer dans un champ de texte.
- ```string pg_escape_string ([ resource $connection ], string $data )``` - Cette routine échappe une chaîne de caractères pour l'interrogation de la base de données.

## Connection à la base de données

Le code PHP suivant montre comment se connecter à une base de données existante sur une machine locale et finalement un objet de connexion de base de données sera retourné :

```php
<?php
    $host = "host = 127.0.0.1";
    $port = "port = 5432";
    $dbnam = "dbname = testdb";
    $credentials = "user = postgres password=pass123";

    $db = pg_connect("$host $port $dbname $credentials");
    if(!$db) {
        echo "Error : Unable to open database\n";
    } else {
        echo "Opened database successfully\n";
    }
?>
```

Maintenant, exécutons le programme ci-dessus pour ouvrir notre base de données testdb : si la base de données est ouverte avec succès, le message suivant apparaîtra :

```bash
Opened database successfully
```

## Créer une table

Le programme PHP suivant sera utilisé pour créer une table dans une base de données créée précédemment :

```php
<?php
    $host = "host = 127.0.0.1";
    $port = "port = 5432";
    $dbname = "dbname = testdb";
    $credentials = "user = postgres password=pass123";

    $db = pg_connect("$host $port $dbname $credentials");
    if(!$db) {
        echo "Error : Unable to open database\n";
    } else {
        echo "Opened database successfully\n";
    }
    
    $sql =<<<EOF
        CREATE TABLE COMPANY
        (ID INT PRIMARY KEY     NOT NULL,
        NAME           TEXT    NOT NULL,
        AGE            INT     NOT NULL,
        ADDRESS        CHAR(50),
        SALARY         REAL);
    EOF;

    $ret = pg_query($db, $sql);
    if(!$ret) {
        echo pg_last_error($db);
    } else {
        echo "Table created successfully\n";
    }
    pg_close($db);
?>²-²
```

Lorsque le programme ci-dessus est exécuté, il créera une table COMPANY dans votre testdb et affichera les messages suivants :

```bash
Opened database successfully
Table created successfully
```

## Opération INSERT

Le programme PHP suivant montre comment nous pouvons créer des enregistrements dans notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```php
<?php
    $host = "host=127.0.0.1";
    $port = "port=5432";
    $dbname = "dbname = testdb";
    $credentials = "user = postgres password=pass123";

    $db = pg_connect("$host $port $dbname $credentials");
    if(!$db) {
        echo "Error : Unable to open database\n";
    } else {
        echo "Opened database successfully\n";
    }

    $sql =<<<EOF
        INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
        VALUES (1, 'Paul', 32, 'California', 20000.00 );

        INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
        VALUES (2, 'Allen', 25, 'Texas', 15000.00 );

        INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
        VALUES (3, 'Teddy', 23, 'Norway', 20000.00 );

        INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
        VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 );
    EOF;

    $ret = pg_query($db, $sql);
    if(!$ret) {
        echo pg_last_error($db);
    } else {
        echo "Records created successfully\n";
    }
    pg_close($db);
?>
```

Lorsque le programme ci-dessus est exécuté, il créera les enregistrements donnés dans la table COMPANY et affichera les deux lignes suivantes :

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme PHP suivant montre comment nous pouvons récupérer et afficher les enregistrements de notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```php
<?php
    $host = "host = 127.0.0.1";
    $port = "port = 5432";
    $dbname = "dbname = testdb";
    $credentials = "user = postgres password=pass123";

    $db = pg_connect("$host $port $dbname $credentials");
    if(!$db) {
        echo "Error : Unable to open database\n";
    } else {
        echo "Opened database successfully\n";
    }

    $sql =<<<EOF
        SELECT * from COMPANY;
    EOF;

    $ret = pg_query($db, $sql);
    if(!$ret) {
        echo pg_last_error($db);
        exit;
    } 
    while($row = pg_fetch_row($ret)) {
        echo "ID = ". $row[0] . "\n";
        echo "NAME = ". $row[1] ."\n";
        echo "ADDRESS = ". $row[2] ."\n";
        echo "SALARY = ".$row[4] ."\n\n";
    }
    echo "Operation done successfully\n";
    pg_close($db);
?>
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant. Notez que les champs sont retournés dans l'ordre où ils ont été utilisés lors de la création de la table :

```bash
Opened database successfully
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 20000

ID = 2
NAME = Allen
ADDRESS = Texas
SALARY = 15000

ID = 3
NAME = Teddy
ADDRESS = Norway
SALARY = 20000

ID = 4
NAME = Mark
ADDRESS = Rich-Mond
SALARY = 65000

Operation done successfully
```

## Opération UPDATE

Le code PHP suivant montre comment utiliser l'instruction UPDATE pour mettre à jour n'importe quel enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table SOCIÉTÉ :

```php
<?php
    $host = "host=127.0.0.1";
    $port = "port=5432";
    $dbname = "dbname = testdb";
    $credentials = "user = postgres password=pass123";

    $db = pg_connect( "$host $port $dbname $credentials"  );
    if(!$db) {
        echo "Error : Unable to open database\n";
    } else {
        echo "Opened database successfully\n";
    }
    $sql =<<<EOF
        UPDATE COMPANY set SALARY = 25000.00 where ID=1;
    EOF;
    $ret = pg_query($db, $sql);
    if(!$ret) {
        echo pg_last_error($db);
        exit;
    } else {
        echo "Record updated successfully\n";
    }
    
    $sql =<<<EOF
        SELECT * from COMPANY;
    EOF;

    $ret = pg_query($db, $sql);
    if(!$ret) {
        echo pg_last_error($db);
        exit;
    } 
    while($row = pg_fetch_row($ret)) {
        echo "ID = ". $row[0] . "\n";
        echo "NAME = ". $row[1] ."\n";
        echo "ADDRESS = ". $row[2] ."\n";
        echo "SALARY = ".$row[4] ."\n\n";
    }
    echo "Operation done successfully\n";
    pg_close($db);
?>
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant -

```bash
Opened database successfully
Record updated successfully
ID = 2
NAME = Allen
ADDRESS = 25
SALARY = 15000

ID = 3
NAME = Teddy
ADDRESS = 23
SALARY = 20000

ID = 4
NAME = Mark
ADDRESS = 25
SALARY = 65000

ID = 1
NAME = Paul
ADDRESS = 32
SALARY = 25000

Operation done successfully
```

## Opération DELETE

Le code PHP suivant montre comment utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY :

```php
<?php
    $host = "host = 127.0.0.1";
    $port = "port = 5432";
    $dbname = "dbname = testdb";
    $credentials = "user = postgres password=pass123";

    $db = pg_connect("$host $port $dbname $credentials");
    if(!$db) {
        echo "Error : Unable to open database\n";
    } else {
        echo "Opened database successfully\n";
    }
    $sql =<<<EOF
        DELETE from COMPANY where ID=2;
    EOF;
    $ret = pg_query($db, $sql);
    if(!$ret) {
        echo pg_last_error($db);
        exit;
    } else {
        echo "Record deleted successfully\n";
    }
    
    $sql =<<<EOF
        SELECT * from COMPANY;
    EOF;

    $ret = pg_query($db, $sql);
    if(!$ret) {
        echo pg_last_error($db);
        exit;
    } 
    while($row = pg_fetch_row($ret)) {
        echo "ID = ". $row[0] . "\n";
        echo "NAME = ". $row[1] ."\n";
        echo "ADDRESS = ". $row[2] ."\n";
        echo "SALARY = ".$row[4] ."\n\n";
    }
    echo "Operation done successfully\n";
    pg_close($db);
?>
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant :

```bash
Opened database successfully
Record deleted successfully
ID = 3
NAME = Teddy
ADDRESS = 23
SALARY = 20000

ID = 4
NAME = Mark
ADDRESS = 25
SALARY = 65000

ID = 1
NAME = Paul
ADDRESS = 32
SALARY = 25000

Operation done successfully
```
