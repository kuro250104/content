Avant de commencer à utiliser Redis dans vos programmes Java, vous devez vous assurer que le pilote Java de Redis et Java sont installés sur votre machine. Vous pouvez consulter notre tutoriel Java pour l'installation de Java sur votre machine.

## Installation

Maintenant, voyons comment configurer le pilote Java de Redis.

- Vous devez télécharger le jar à partir du chemin Télécharger **jedis.jar**. Assurez-vous de télécharger la dernière version de ce fichier.
- Vous devez inclure le fichier **jedis.jar** dans votre classpath.

## Connection au serveur Redis

```java
import redis.clients.jedis.Jedis; 

public class RedisJava { 
    public static void main(String[] args) { 
        //Connecting to Redis server on localhost 
        Jedis jedis = new Jedis("localhost"); 
        System.out.println("Connection to server sucessfully"); 
        //check whether server is running or not 
        System.out.println("Server is running: "+jedis.ping()); 
    } 
}
```

Maintenant, compilons et exécutons le programme ci-dessus pour tester la connexion au serveur Redis. Vous pouvez changer votre chemin selon vos besoins. Nous supposons que la version actuelle de **jedis.jar** est disponible dans le chemin actuel.

```bash
$javac RedisJava.java 
$java RedisJava 
Connection to server sucessfully 
Server is running: PONG
```

## Exemple d'utilisation de Redis String en Java

```java
import redis.clients.jedis.Jedis; 

public class RedisStringJava { 
    public static void main(String[] args) { 
        //Connecting to Redis server on localhost 
        Jedis jedis = new Jedis("localhost"); 
        System.out.println("Connection to server sucessfully"); 
        //set the data in redis string 
        jedis.set("tutorial-name", "Redis tutorial"); 
        // Get the stored data and print it 
        System.out.println("Stored string in redis:: "+ jedis.get("tutorial-name")); 
    } 
}
```

Maintenant, compilons et exécutons le programme ci-dessus.

```bash
$javac RedisStringJava.java 
$java RedisStringJava 
Connection to server sucessfully 
Stored string in redis:: Redis tutorial 
```

## Exemple d'utilisation de Redis Lists en Java

```java
import redis.clients.jedis.Jedis; 

public class RedisListJava { 
    public static void main(String[] args) { 

        //Connecting to Redis server on localhost 
        Jedis jedis = new Jedis("localhost"); 
        System.out.println("Connection to server sucessfully"); 

        //store data in redis list 
        jedis.lpush("tutorial-list", "Redis"); 
        jedis.lpush("tutorial-list", "Mongodb"); 
        jedis.lpush("tutorial-list", "Mysql"); 
        // Get the stored data and print it 
        List<String> list = jedis.lrange("tutorial-list", 0 ,5); 

        for(int i = 0; i<list.size(); i++) { 
            System.out.println("Stored string in redis:: "+list.get(i)); 
        } 
    } 
}
```

Maintenant, compilons et exécutons le programme ci-dessus.

```java
$javac RedisListJava.java 
$java RedisListJava 
Connection to server sucessfully 
Stored string in redis:: Redis 
Stored string in redis:: Mongodb 
Stored string in redis:: Mysql
```

## Exemple d'utilisation de Redis Keys en Java

```java
import redis.clients.jedis.Jedis; 

public class RedisKeyJava { 
    public static void main(String[] args) { 

        //Connecting to Redis server on localhost 
        Jedis jedis = new Jedis("localhost"); 
        System.out.println("Connection to server sucessfully"); 
        //store data in redis list 
        // Get the stored data and print it 
        List<String> list = jedis.keys("*"); 
        
        for(int i = 0; i<list.size(); i++) { 
            System.out.println("List of stored keys:: "+list.get(i)); 
        } 
    } 
}
```

Maintenant, compilons et exécutons le programme ci-dessus.

```bash
$javac RedisKeyJava.java 
$java RedisKeyJava 
Connection to server sucessfully 
List of stored keys:: tutorial-name 
List of stored keys:: tutorial-list
```