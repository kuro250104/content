Avant de commencer à utiliser Redis dans vos programmes PHP, vous devez vous assurer que vous avez le pilote Redis PHP et que PHP est installé sur votre machine. Vous pouvez consulter le tutoriel PHP pour l'installation de PHP sur votre machine.

## Installation

Maintenant, voyons comment configurer le pilote PHP de Redis.

Vous devez télécharger le phpredis à partir du dépôt github <a href="https://github.com/nicolasff/phpredis" title="Dépôt Github de téléchargement de PHP Redis" target="_blank">https://github.com/nicolasff/phpredis</a>. Une fois que vous l'avez téléchargé, extrayez les fichiers dans le répertoire phpredis. Sur Ubuntu, installez l'extension suivante.

```bash
cd phpredis 
sudo phpize 
sudo ./configure 
sudo make 
sudo make install 
```

Maintenant, copiez et collez le contenu du dossier "modules" dans le répertoire d'extension PHP et ajoutez les lignes suivantes dans le ```php.ini```.

```bash
extension = redis.so
```

Maintenant, votre installation PHP de Redis est terminée

## Connection au serveur Redis

```php
<?php 
    //Connecting to Redis server on localhost 
    $redis = new Redis(); 
    $redis->connect('127.0.0.1', 6379); 
    echo "Connection to server sucessfully"; 
    //check whether server is running or not 
    echo "Server is running: ".$redis->ping(); 
?>
```

Lorsque le programme est exécuté, il produit le résultat suivant.

```bash
Connection to server sucessfully 
Server is running: PONG 
```

## Exemple d'utilisation de Redis String en PHP

```php
<?php 
    //Connecting to Redis server on localhost 
    $redis = new Redis(); 
    $redis->connect('127.0.0.1', 6379); 
    echo "Connection to server sucessfully"; 
    //set the data in redis string 
    $redis->set("tutorial-name", "Redis tutorial"); 
    // Get the stored data and print it 
    echo "Stored string in redis:: " .$redis→get("tutorial-name"); 
?>
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

```bash
Connection to server sucessfully 
Stored string in redis:: Redis tutorial 
```

## Exemple d'utilisation de Redis Lists en PHP

```php
<?php 
    //Connecting to Redis server on localhost 
    $redis = new Redis(); 
    $redis->connect('127.0.0.1', 6379); 
    echo "Connection to server sucessfully"; 
    //store data in redis list 
    $redis->lpush("tutorial-list", "Redis"); 
    $redis->lpush("tutorial-list", "Mongodb"); 
    $redis->lpush("tutorial-list", "Mysql");  
    
    // Get the stored data and print it 
    $arList = $redis->lrange("tutorial-list", 0 ,5); 
    echo "Stored string in redis:: "; 
    print_r($arList); 
?>
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

```bash
Connection to server sucessfully 
Stored string in redis:: 
Redis 
Mongodb 
Mysql 
```

## Exemple d'utilisation de Redis Keys en PHP

```php
<?php 
    //Connecting to Redis server on localhost 
    $redis = new Redis(); 
    $redis->connect('127.0.0.1', 6379); 
    echo "Connection to server sucessfully"; 
    // Get the stored keys and print it 
    $arList = $redis->keys("*"); 
    echo "Stored keys in redis:: " 
    print_r($arList); 
?>
```

Lorsque le programme est exécuté, il produit le résultat suivant.

```bash
Connection to server sucessfully 
Stored string in redis:: 
tutorial-name 
tutorial-list
```