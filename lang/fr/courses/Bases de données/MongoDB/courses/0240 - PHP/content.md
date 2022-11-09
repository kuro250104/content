Pour utiliser MongoDB avec PHP, vous devez utiliser le pilote PHP de MongoDB. Téléchargez le pilote à partir de l'url Download PHP Driver. Assurez-vous de télécharger la dernière version du pilote. Maintenant, dézippez l'archive et placez php_mongo.dll dans votre répertoire d'extension PHP ("ext" par défaut) et ajoutez la ligne suivante à votre fichier php.ini -

```
extension = php_mongo.dll
```

## Établir une connexion et sélectionner une base de données

Pour établir une connexion, vous devez spécifier le nom de la base de données. Si la base de données n'existe pas, MongoDB la crée automatiquement.

Voici l'extrait de code permettant de se connecter à la base de données.

```php
<?php
    // connect to mongodb
    $m = new MongoClient();

    echo "Connection to database successfully";
    // select a database
    $db = $m->mydb;

    echo "Database mydb selected";
?>
```

Lorsque le programme sera exécuté, il produira le résultat suivant -

```
Connection to database successfully
Database mydb selected
```

## Créer une collection

Le code suivant permet de créer une collection -

```php
<?php
    // connect to mongodb
    $m = new MongoClient();
    echo "Connection to database successfully";
        
    // select a database
    $db = $m->mydb;
    echo "Database mydb selected";
    $collection = $db->createCollection("mycol");
    echo "Collection created succsessfully";
?>
```

Lorsque le programme sera exécuté, il produira le résultat suivant -

```
Connection to database successfully
Database mydb selected
Collection created succsessfully
```

## Insert a Document

Pour insérer un document dans MongoDB, on utilise la méthode ```insert()```.

Voici l'extrait de code permettant d'insérer un document.

```php
<?php
    // connect to mongodb
    $m = new MongoClient();
    echo "Connection to database successfully";

    // select a database
    $db = $m->mydb;
    echo "Database mydb selected";
    $collection = $db->mycol;
    echo "Collection selected succsessfully";

    $document = array( 
        "title" => "MongoDB", 
        "description" => "database", 
        "likes" => 100,
        "url" => "http://www.Microlead.fr/mongodb/",
        "by" => "Microlead"
    );

    $collection->insert($document);
    echo "Document inserted successfully";
?>
```

Lorsque le programme sera exécuté, il produira le résultat suivant -

```
Connection to database successfully
Database mydb selected
Collection selected succsessfully
Document inserted successfully
```

## Rechercher tous les documents

Pour sélectionner tous les documents de la collection, la méthode ```find()``` est utilisée.

Voici l'extrait de code permettant de sélectionner tous les documents.

```php
<?php
    // connect to mongodb
    $m = new MongoClient();
    echo "Connection to database successfully";
        
    // select a database
    $db = $m->mydb;
    echo "Database mydb selected";
    $collection = $db->mycol;
    echo "Collection selected succsessfully";
    $cursor = $collection->find();
    // iterate cursor to display title of documents
        
    foreach ($cursor as $document) {
        echo $document["title"] . "\n";
    }
?>
```

Lorsque le programme sera exécuté, il produira le résultat suivant -

```
Connection to database successfully
Database mydb selected
Collection selected succsessfully {
    "title": "MongoDB"
}
```

## Mettre à jour un document

Pour mettre à jour un document, vous devez utiliser la méthode ```update()```.

Dans l'exemple suivant, nous allons mettre à jour le titre du document inséré en Tutorial MongoDB. Voici l'extrait de code permettant de mettre à jour un document.

```php
<?php
    // connect to mongodb
    $m = new MongoClient();
    echo "Connection to database successfully";

    // select a database
    $db = $m->mydb;
    echo "Database mydb selected";
    $collection = $db->mycol;
    echo "Collection selected succsessfully";
    // now update the document
    $collection->update(array("title"=>"MongoDB"), 
        array('$set'=>array("title"=>"MongoDB Tutorial")));
    echo "Document updated successfully";

    // now display the updated document
    $cursor = $collection->find();

    // iterate cursor to display title of documents
    echo "Updated document";

    foreach ($cursor as $document) {
        echo $document["title"] . "\n";
    }
?>
```

Lorsque le programme sera exécuté, il produira le résultat suivant -

```
Connection to database successfully
Database mydb selected
Collection selected succsessfully
Document updated successfully
Updated document {
    "title": "MongoDB Tutorial"
}
```

## Supprimer un document

Pour supprimer un document, vous devez utiliser la méthode ```remove()```.

Dans l'exemple suivant, nous allons supprimer les documents dont le titre est MongoDB Tutorial. Voici l'extrait de code permettant de supprimer un document.

```php
<?php
    // connect to mongodb
    $m = new MongoClient();
    echo "Connection to database successfully";

    // select a database
    $db = $m->mydb;
    echo "Database mydb selected";
    $collection = $db->mycol;
    echo "Collection selected succsessfully";

    // now remove the document
    $collection->remove(array("title"=>"MongoDB Tutorial"),false);
    echo "Documents deleted successfully";

    // now display the available documents
    $cursor = $collection->find();

    // iterate cursor to display title of documents
    echo "Updated document";

    foreach ($cursor as $document) {
        echo $document["title"] . "\n";
    }
?>
```

Lorsque le programme sera exécuté, il produira le résultat suivant -

```
Connection to database successfully
Database mydb selected
Collection selected successfully
Documents deleted successfully
```

Dans l'exemple ci-dessus, le deuxième paramètre est de type booléen et est utilisé pour le champ justOne de la méthode ```remove()```.

Les autres méthodes MongoDB ```findOne()```, ```save()```, ```limit()```, ```skip()```, ```sort()``` etc. fonctionnent comme expliqué ci-dessus.