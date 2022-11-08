Dans ce chapitre, vous apprendrez à utiliser SQLite dans les programmes PHP.

## Installation

L'extension SQLite3 est activée par défaut depuis PHP 5.3.0. Il est possible de la désactiver en utilisant **--without-sqlite3** au moment de la compilation.

Les utilisateurs de Windows doivent activer php_sqlite3.dll afin d'utiliser cette extension. Cette DLL est incluse dans les distributions Windows de PHP à partir de PHP 5.3.0.

Pour des instructions d'installation détaillées, veuillez consulter notre tutoriel PHP et son site officiel.

## PHP Interface APIs

Voici les principales routines PHP qui peuvent répondre à vos besoins pour travailler avec la base de données SQLite depuis votre programme PHP. Si vous recherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle de PHP.

**API & Description**

- ```public void SQLite3::open ( filename, flags, encryption_key )``` - Ouvre la base de données SQLite 3. Si le build inclut le cryptage, alors il tentera d'utiliser la clé. Si le nom de fichier est donné comme ':memory:', SQLite3::open() créera une base de données en mémoire dans la RAM qui ne durera que le temps de la session. Si le nom de fichier est un nom de fichier réel du périphérique, SQLite3::open() tente d'ouvrir le fichier de base de données en utilisant sa valeur. Si aucun fichier de ce nom n'existe, alors un nouveau fichier de base de données de ce nom est créé. Drapeaux optionnels utilisés pour déterminer comment ouvrir la base de données SQLite. Par défaut, open utilise SQLITE3_OPEN_READWRITE | SQLITE3_OPEN_CREATE.
- ```public bool SQLite3::exec ( string $query )``` - Cette routine fournit un moyen rapide et facile d'exécuter les commandes SQL fournies par l'argument sql, qui peut être composé de plus d'une commande SQL. Cette routine est utilisée pour exécuter une requête sans résultat contre une base de données donnée.
- ```public SQLite3Result SQLite3::query ( string $query )``` - Cette routine exécute une requête SQL, renvoyant un objet SQLite3Result si la requête renvoie des résultats.
- ```public int SQLite3::lastErrorCode ( void )``` - Cette routine renvoie le code de résultat numérique de la plus récente requête SQLite qui a échoué.
- ```public string SQLite3::lastErrorMsg ( void )``` - Cette routine retourne un texte en anglais décrivant la plus récente requête SQLite échouée.
- ```public int SQLite3::changes ( void )``` - Cette routine renvoie le nombre de lignes de la base de données qui ont été mises à jour, insérées ou supprimées par l'instruction SQL la plus récente.
- ```public bool SQLite3::close ( void )``` - Cette routine ferme une connexion à une base de données précédemment ouverte par un appel à SQLite3::open().
- ```public string SQLite3::escapeString ( string $value )``` - Cette routine renvoie une chaîne qui a été correctement échappée pour être incluse en toute sécurité dans une instruction SQL.

## Connexion à la base de données

Le code PHP suivant montre comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et un objet base de données sera retourné.

```php
<?php
    class MyDB extends SQLite3 {
        function __construct() {
            $this->open('test.db');
        }
    }
    $db = new MyDB();
    if(!$db) {
        echo $db->lastErrorMsg();
    } else {
        echo "Opened database successfully\n";
    }
?>
```

Maintenant, exécutons le programme ci-dessus pour créer notre base de données **test.db** dans le répertoire courant. Vous pouvez modifier le chemin d'accès en fonction de vos besoins. Si la base de données est créée avec succès, alors le message suivant s'affichera -

```bash
Open database successfully
```

## Créer un tableau

Le programme PHP suivant sera utilisé pour créer une table dans la base de données précédemment créée.

```php
<?php
    class MyDB extends SQLite3 {
        function __construct() {
            $this->open('test.db');
        }
    }
    $db = new MyDB();
    if(!$db) {
            echo $db->lastErrorMsg();
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

    $ret = $db->exec($sql);
    if(!$ret){
        echo $db->lastErrorMsg();
    } else {
        echo "Table created successfully\n";
    }
    $db->close();
?>
```

Lorsque le programme ci-dessus est exécuté, il créera la table COMPANY dans votre test.db et il affichera les messages suivants -

```bash
Opened database successfully
Table created successfully
```

## Opération INSERT

Le programme PHP suivant montre comment créer des enregistrements dans la table COMPANY créée dans l'exemple ci-dessus.

```php
<?php
   class MyDB extends SQLite3 {
        function __construct() {
            $this->open('test.db');
        }
    }

    $db = new MyDB();
    if(!$db){
        echo $db->lastErrorMsg();
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

    $ret = $db->exec($sql);
    if(!$ret) {
        echo $db->lastErrorMsg();
    } else {
        echo "Records created successfully\n";
    }
    $db->close();
?>
```

Lorsque le programme ci-dessus est exécuté, il crée les enregistrements donnés dans la table SOCIÉTÉ et affiche les deux lignes suivantes.

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme PHP suivant montre comment extraire et afficher les enregistrements de la table SOCIÉTÉ créée dans l'exemple ci-dessus.

```php
<?php
    class MyDB extends SQLite3 {
        function __construct() {
            $this->open('test.db');
        }
    }
    
    $db = new MyDB();
    if(!$db) {
        echo $db->lastErrorMsg();
    } else {
        echo "Opened database successfully\n";
    }

    $sql =<<<EOF
        SELECT * from COMPANY;
    EOF;

    $ret = $db->query($sql);
    while($row = $ret->fetchArray(SQLITE3_ASSOC) ) {
        echo "ID = ". $row['ID'] . "\n";
        echo "NAME = ". $row['NAME'] ."\n";
        echo "ADDRESS = ". $row['ADDRESS'] ."\n";
        echo "SALARY = ".$row['SALARY'] ."\n\n";
    }
    echo "Operation done successfully\n";
    $db->close();
?>
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

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

Le code PHP suivant montre comment utiliser l'instruction UPDATE pour mettre à jour un enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table COMPANY.

```php
<?php
    class MyDB extends SQLite3 {
        function __construct() {
            $this->open('test.db');
        }
    }
    
    $db = new MyDB();
    if(!$db) {
        echo $db->lastErrorMsg();
    } else {
        echo "Opened database successfully\n";
    }
    $sql =<<<EOF
        UPDATE COMPANY set SALARY = 25000.00 where ID=1;
    EOF;
    $ret = $db->exec($sql);
    if(!$ret) {
        echo $db->lastErrorMsg();
    } else {
        echo $db->changes(), " Record updated successfully\n";
    }

    $sql =<<<EOF
        SELECT * from COMPANY;
    EOF;
    
    $ret = $db->query($sql);
    while($row = $ret->fetchArray(SQLITE3_ASSOC) ) {
        echo "ID = ". $row['ID'] . "\n";
        echo "NAME = ". $row['NAME'] ."\n";
        echo "ADDRESS = ". $row['ADDRESS'] ."\n";
        echo "SALARY = ".$row['SALARY'] ."\n\n";
    }
    echo "Operation done successfully\n";
    $db->close();
?>
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

```bash
Opened database successfully
1 Record updated successfully
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 25000

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

## Opération DELETE

Le code PHP suivant montre comment utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY.

```php
<?php
    class MyDB extends SQLite3 {
        function __construct() {
            $this->open('test.db');
        }
    }
    
    $db = new MyDB();
    if(!$db) {
        echo $db->lastErrorMsg();
    } else {
        echo "Opened database successfully\n";
    }
    $sql =<<<EOF
        DELETE from COMPANY where ID = 2;
    EOF;
    
    $ret = $db->exec($sql);
    if(!$ret){
        echo $db->lastErrorMsg();
    } else {
        echo $db->changes(), " Record deleted successfully\n";
    }

    $sql =<<<EOF
        SELECT * from COMPANY;
    EOF;
    $ret = $db->query($sql);
    while($row = $ret->fetchArray(SQLITE3_ASSOC) ) {
        echo "ID = ". $row['ID'] . "\n";
        echo "NAME = ". $row['NAME'] ."\n";
        echo "ADDRESS = ". $row['ADDRESS'] ."\n";
        echo "SALARY = ".$row['SALARY'] ."\n\n";
    }
    echo "Operation done successfully\n";
    $db->close();
?>
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

```bash
Opened database successfully
1 Record deleted successfully
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 25000

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