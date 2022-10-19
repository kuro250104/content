Le PHP Data Objects (PDO) définit une interface légère pour accéder aux bases de données en PHP. Il fournit une couche d'abstraction d'accès aux données pour travailler avec les bases de données en PHP. Il définit une API cohérente pour travailler avec différents systèmes de bases de données.

## Classes PHP PDO

Le PDO représente une connexion entre PHP et un serveur de base de données. La classe PDOStatement représente une instruction préparée et, après l'exécution de l'instruction, un ensemble de résultats associés. La classe ```PDOException``` représente une erreur soulevée par PDO.

## Base de données MySQL

Dans ce cours, nous travaillons avec une base de données MySQL. Voici le code permettant de créer la table dont nous nous servirons pendant ce cours. Si vous ne savez pas comment l'exploiter, référez vous aux cours de MySQL.

``` sql
DROP TABLE IF EXISTS countries;
CREATE TABLE countries(id BIGINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	name VARCHAR(255), population INT);

INSERT INTO countries(name, population) VALUES('China', 1382050000);
INSERT INTO countries(name, population) VALUES('India', 1313210000);
INSERT INTO countries(name, population) VALUES('USA', 324666000);
INSERT INTO countries(name, population) VALUES('Indonesia', 260581000);
INSERT INTO countries(name, population) VALUES('Brazil', 207221000);
INSERT INTO countries(name, population) VALUES('Pakistan', 196626000);
INSERT INTO countries(name, population) VALUES('Nigeria', 186988000);
INSERT INTO countries(name, population) VALUES('Bangladesh', 162099000);
INSERT INTO countries(name, population) VALUES('Nigeria', 186988000);
INSERT INTO countries(name, population) VALUES('Russia', 146838000);
INSERT INTO countries(name, population) VALUES('Japan', 126830000);
```

## PHP PDO query

La fonction PDO ```query()``` exécute une instruction SQL en un seul appel de fonction, et renvoie le jeu de résultats (s'il y en a) renvoyé par l'instruction.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);

$stm = $pdo->query("SELECT VERSION()");

$version = $stm->fetch();

echo $version[0] . PHP_EOL;
```

L'exemple renvoie la version de MySQL.

``` php
$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";
```

Ces variables sont utilisées pour créer une chaîne de connexion à la base de données. Le ```$dsn``` est le nom de la source de données, qui contient les informations nécessaires pour se connecter à la base de données.

``` php
$pdo = new PDO($dsn, $user, $passwd);
```

Un nouvel objet PDO est créé. Il passe au constructeur le nom de la source de données ainsi que le nom d'utilisateur et le mot de passe. La classe PDO représente une connexion entre PHP et un serveur de base de données.

``` php
$stm = $pdo->query("SELECT VERSION()");
```

La méthode ```query()``` exécute une instruction SQL en un seul appel de fonction. Elle renvoie le jeu de résultats.

``` php
$version = $stm->fetch();
```

La méthode ```fetch()``` de l'instruction PDO permet d'extraire la ligne suivante d'un ensemble de résultats. Dans notre cas, il s'agit d'une version de MySQL.

``` php
echo $version[0] . PHP_EOL;
```

La variable ```$version``` est un tableau, il affiche sa première valeur.

## PHP PDO exec

La fonction PDO ```exec()``` exécute une instruction SQL et renvoie le nombre de lignes concernées.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);
$id = 12;
$nrows = $pdo->exec("DELETE FROM countries WHERE id IN (1, 2, 3)");
echo "La déclaration a supprimé $nrows lignes\n";
```

L'exemple de code supprime trois lignes. Il affiche le nombre de lignes concernées.

``` php
$nrows = $pdo->exec("DELETE FROM countries WHERE id IN (1, 2, 3)");
```

Dans cette instruction SQL, les lignes avec les identifiants 1, 2 et 3 sont supprimées. Le nombre de lignes supprimées est stocké dans la variable ```$nrows```.

``` php
echo "La déclaration a supprimé $nrows lignes\n";
```

Cela affiche le nombre de lignes supprimées.

## PHP PDO fetch

Le paramètre fetch contrôle la façon dont la ligne suivante sera retournée à l'appelant. Par exemple, ```PDO::FETCH_ASSOC``` renvoie un tableau indexé par le nom de la colonne, ```PDO::FETCH_NUM``` renvoie un tableau indexé par le numéro de la colonne, et ```PDO::FETCH_BOTH``` renvoie un tableau indexé à la fois par le nom et le numéro de la colonne indexée. Le style de récupération par défaut est ```PDO::FETCH_BOTH```.

``` php
<?php
$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);
$stm = $pdo->query("SELECT * FROM countries");
$rows = $stm->fetchAll(PDO::FETCH_NUM);
foreach($rows as $row) {
    printf("$row[0] $row[1] $row[2]\n");
}
```

Dans cet exemple, le code affichera les données dans un tableau indexé.

``` php
$stm = $pdo->query("SELECT * FROM countries");
```

Il sélectionne toutes les données du tableau des pays.

``` php
$rows = $stm->fetchAll(PDO::FETCH_NUM);
```

Il passe le style ```PDO:FETCH_NUM``` à la méthode ```fetchAll()```.

``` php
foreach($rows as $row) {
    printf("$row[0] $row[1] $row[2]\n");
}
```

Il parcourt le tableau ```$rows``` et affiche les champs. Les champs sont accessibles via les index du tableau.

## Liaison des paramètres PHP PDO

Les instructions SQL sont souvent construites de manière dynamique. Un utilisateur fournit une entrée et cette entrée est intégrée dans la déclaration. Nous devons être prudents chaque fois que nous traitons une entrée provenant d'un utilisateur. Cela a de sérieuses implications en matière de sécurité. La manière recommandée de construire dynamiquement des instructions SQL est d'utiliser la liaison des paramètres.

PDO contient les méthodes ```bindParam()``` et ```bindValue()``` pour créer des requêtes paramétrées.

PDO permet de lier des données à des points d'interrogation ou à des espaces nommés.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "root";
$passwd = "andrea";

$pdo = new PDO($dsn, $user, $passwd);

$id = 12;

$stm = $pdo->prepare("SELECT * FROM countries WHERE id = ?");
$stm->bindValue(1, $id);
$stm->execute();

$row = $stm->fetch(PDO::FETCH_ASSOC);

echo "Id: " . $row['id'] . PHP_EOL;
echo "Name: " . $row['name'] . PHP_EOL;
echo "Population: " . $row['population'] . PHP_EOL;
```

Dans l'exemple, nous utilisons bindValue() pour créer une requête paramétrée. Nous utilisons le point d'interrogation comme placeholder.

``` php
$id = 12;
```

Disons que cette entrée provient d'un utilisateur.

``` php
$stm = $pdo->prepare("SELECT * FROM countries WHERE id = ?");
$stm->bindValue(1, $id);
$stm->execute();
```

L'instruction select récupère une ligne spécifique du tableau. Nous lions la valeur avec ```bindValue()``` à un point d'interrogation.

Dans le second cas, nous utilisons ```bindParam()```.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);

$id = 12;

$stm = $pdo->prepare("SELECT * FROM countries WHERE id = :id");
$stm->bindParam(":id", $id, PDO::PARAM_INT);
$stm->execute();

$row = $stm->fetch(PDO::FETCH_ASSOC);

echo "Id : " . $row['id'] . PHP_EOL;
echo "Nom : " . $row['name'] . PHP_EOL;
echo "Population : " . $row['population'] . PHP_EOL;
```

L'exemple sélectionne et affiche une ligne spécifique.

``` php
$stm = $pdo->prepare("SELECT * FROM countries WHERE id = :id");
$stm->bindParam(":id", $id, PDO::PARAM_INT);
$stm->execute();
```

Cette fois-ci, nous utilisons un placeholder nommé (:id) et bindParam().

## PHP PDO lastInsertId

La méthode PDO ```lastInsertId()``` renvoie l'identifiant de la dernière ligne insérée.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);

$sql = "CREATE TABLE words(id INT PRIMARY KEY AUTO_INCREMENT,
    word VARCHAR(255))";

$ret = $pdo->exec($sql);
$pdo->exec("INSERT INTO words(word) VALUES ('pen')");
$pdo->exec("INSERT INTO words(word) VALUES ('bum')");
$pdo->exec("INSERT INTO words(word) VALUES ('hum')");
$pdo->exec("INSERT INTO words(word) VALUES ('den')");

$rowid = $pdo->lastInsertId();

echo "L'ID de la dernière ligne insérée est : $rowid\n";
```

Dans l'exemple, nous créons une nouvelle table. Après la création de la table, nous trouvons le dernier Id inséré avec ```lastInsertId()```.

```
L'ID de la dernière ligne insérée est : 4
```

Voici la réponse.

``` sql
mysql> select * from words;
+----+------+
| id | word |
+----+------+
|  1 | pen  |
|  2 | bum  |
|  3 | hum  |
|  4 | den  |
+----+------+
4 rows in set (0.01 sec)
```

Nous vérifions les données.

## Transactions PHP PDO

Une transaction est une unité atomique d'opérations de base de données sur les données d'une ou plusieurs bases de données. Les effets de toutes les instructions SQL dans une transaction peuvent être soit tous validés dans la base de données, soit tous annulés.

La fonction PDO ```beginTransaction()``` initie une nouvelle transaction. PDO ```commit()``` commet la transaction. Et PDO ```rollback()``` annule la transaction.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);

try {
    $pdo->beginTransaction();
    $stm = $pdo->exec("INSERT INTO countries(name, population) VALUES ('Iraq', 38274000)");
    $stm = $pdo->exec("INSERT INTO countries(name, population) VALUES ('Uganda', 37673800)");
    $pdo->commit();

} catch(Exception $e) {
    $pdo->rollback();
    throw $e;
}
```

Dans l'exemple, nous ajoutons deux nouveaux pays à la table de la base de données. Les instructions d'insertion sont placées dans une transaction : soit les deux insertions sont exécutées, soit aucune.

``` php
} catch(Exception $e) {
    $pdo->rollback();
    throw $e;
}
```

En cas d'exception, nous annulons la transaction : aucune donnée n'est écrite dans la base de données. Nous lançons l'exception pour que le traitement des exceptions continue de la manière habituelle.

## PHP PDO obtention de métadonnées

Les métadonnées sont des informations sur les données d'une base de données. Les métadonnées contiennent des informations sur les tables et les colonnes dans lesquelles nous stockons les données. Le nombre de lignes qu'une instruction SQL affecte est une métadonnée. Le nombre de lignes et de colonnes renvoyées dans un jeu de résultats sont également des métadonnées.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);

$stm = $pdo->query("SELECT name, population FROM countries WHERE id=1");

$ncols = $stm->columnCount();

echo "Le jeu de résultats contient $ncols colonnes\n";
```

Dans l'exemple, il affiche le nombre de colonnes dans le jeu de résultats avec la méthode ```columnCount()```.

La méthode ```getAttribute()``` permet de récupérer un attribut de connexion à une base de données.

``` php
<?php

$dsn = "mysql:host=localhost;dbname=mydb";
$user = "user12";
$passwd = "12user";

$pdo = new PDO($dsn, $user, $passwd);

$driver = $pdo->getAttribute(PDO::ATTR_DRIVER_NAME);
$server_version = $pdo->getAttribute(PDO::ATTR_SERVER_VERSION);
$autocommit_mode = $pdo->getAttribute(PDO::ATTR_AUTOCOMMIT);

echo "Driver: $driver\n";
echo "Server version: $server_version\n";
echo "Autocommit mode: $autocommit_mode\n";
```

Dans l'exemple, nous obtenons le nom du pilote, la version du serveur et le mode autocommit avec la méthode ```getAttribute()```.

Voici un exemple de réponse :

``` sql
Driver: mysql
Server version: 5.7.22-0ubuntu0.16.04.1
Autocommit mode: 1
```