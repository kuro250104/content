Dans ce chapitre, nous allons apprendre à configurer MongoDB CLIENT.

## Installation

Avant de commencer à utiliser MongoDB dans vos programmes Java, vous devez vous assurer que MongoDB CLIENT et Java sont installés sur votre machine. Vous pouvez consulter le tutoriel Java pour l'installation de Java sur votre machine. Maintenant, voyons comment configurer MongoDB CLIENT.

- Vous devez télécharger le jar ```mongodb-driver-3.11.2.jar``` et sa dépendance ```mongodb-driver-core-3.11.2.jar```. Assurez-vous de télécharger la dernière version de ces fichiers jar.
- Vous devez inclure les fichiers jar téléchargés dans votre classpath.

## Connexion à la base de données

Pour connecter la base de données, vous devez spécifier le nom de la base de données, si la base de données n'existe pas, MongoDB la crée automatiquement.

Voici l'extrait de code permettant de se connecter à la base de données.

```java
import com.mongodb.client.MongoDatabase; 
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  
public class ConnectToDB { 

    public static void main( String args[] ) {  
        
        // Creating a Mongo client 
        MongoClient mongo = new MongoClient( "localhost" , 27017 ); 

        // Creating Credentials 
        MongoCredential credential; 
        credential = MongoCredential.createCredential("sampleUser", "myDb", 
            "password".toCharArray()); 
        System.out.println("Connected to the database successfully");  

        // Accessing the database 
        MongoDatabase database = mongo.getDatabase("myDb"); 
        System.out.println("Credentials ::"+ credential);     
   } 
}
```

Maintenant, compilons et exécutons le programme ci-dessus pour créer notre base de données myDb comme indiqué ci-dessous.

```
$javac ConnectToDB.java 
$java ConnectToDB
```

Lors de l'exécution, le programme ci-dessus vous donne la sortie suivante.

```
Connected to the database successfully 
Credentials ::MongoCredential{
    mechanism = null, 
    userName = 'sampleUser', 
    source = 'myDb', 
    password = <hidden>, 
    mechanismProperties = {}
}
```

## Créer une collection

Pour créer une collection, la méthode ```createCollection()``` de la classe ```com.mongodb.client.MongoDatabase``` est utilisée.

Le code suivant permet de créer une collection -

```java
import com.mongodb.client.MongoDatabase; 
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  
public class CreatingCollection { 
    public static void main( String args[] ) {  

        // Creating a Mongo client 
        MongoClient mongo = new MongoClient( "localhost" , 27017 ); 

        // Creating Credentials 
        MongoCredential credential; 
        credential = MongoCredential.createCredential("sampleUser", "myDb", 
            "password".toCharArray()); 
        System.out.println("Connected to the database successfully");  

        //Accessing the database 
        MongoDatabase database = mongo.getDatabase("myDb");  

        //Creating a collection 
        database.createCollection("sampleCollection"); 
        System.out.println("Collection created successfully"); 
   } 
}
```

À la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully 
Collection created successfully
```

## Obtenir/sélectionner une collection

Pour obtenir/sélectionner une collection dans la base de données, on utilise la méthode ```getCollection()``` de la classe ```com.mongodb.client.MongoDatabase```.

Le programme suivant permet d'obtenir/sélectionner une collection.

```java
import com.mongodb.client.MongoCollection; 
import com.mongodb.client.MongoDatabase; 
import org.bson.Document; 
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  
public class selectingCollection { 

    public static void main( String args[] ) {  

        // Creating a Mongo client 
        MongoClient mongo = new MongoClient( "localhost" , 27017 ); 

        // Creating Credentials 
        MongoCredential credential; 
        credential = MongoCredential.createCredential("sampleUser", "myDb", 
            "password".toCharArray()); 
        System.out.println("Connected to the database successfully");  

        // Accessing the database 
        MongoDatabase database = mongo.getDatabase("myDb");  

        // Creating a collection 
        System.out.println("Collection created successfully"); 
        // Retrieving a collection
        MongoCollection<Document> collection = database.getCollection("myCollection"); 
        System.out.println("Collection myCollection selected successfully"); 
    }
}
```

À la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully 
Collection created successfully 
Collection myCollection selected successfully
```

## Insert a Document

Pour insérer un document dans MongoDB, on utilise la méthode ```insert()``` de la classe ```com.mongodb.client.MongoCollection```.

Voici l'extrait de code permettant d'insérer un document.

```
import com.mongodb.client.MongoCollection;
import com.mongodb.client.MongoDatabase;
import org.bson.Document;
import com.mongodb.MongoClient;
public class InsertingDocument {
	public static void main( String args[] ) {
	
	// Creating a Mongo client
	MongoClient mongo = new MongoClient( "localhost" , 27017 );
	
	// Accessing the database
	MongoDatabase database = mongo.getDatabase("myDb");
	
	// Creating a collection
	database.createCollection("sampleCollection");
	System.out.println("Collection created successfully");
	
	// Retrieving a collection
	MongoCollection<Document> collection = database.getCollection("sampleCollection");
	System.out.println("Collection sampleCollection selected successfully");
	Document document = new Document("title", "MongoDB")
	.append("description", "database")
	.append("likes", 100)
	.append("url", "http://www.Microlead.fr/mongodb/")
	.append("by", "Microlead");
	
	//Inserting document into the collection
	collection.insertOne(document);
	System.out.println("Document inserted successfully");
}
```

A la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully 
Collection sampleCollection selected successfully 
Document inserted successfully
```

## Récupérer tous les documents

Pour sélectionner tous les documents de la collection, on utilise la méthode ```find()``` de la classe ```com.mongodb.client.MongoCollection```. Cette méthode renvoie un curseur, vous devez donc itérer ce curseur.

Le programme suivant permet de sélectionner tous les documents -

```java
import com.mongodb.client.FindIterable;
import com.mongodb.client.MongoCollection;
import com.mongodb.client.MongoDatabase;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import org.bson.Document;
import com.mongodb.MongoClient;
import com.mongodb.MongoCredential;
public class RetrievingAllDocuments {
	public static void main( String args[] ) {

		// Creating a Mongo client
		MongoClient mongo = new MongoClient( "localhost" , 27017 );

		// Creating Credentials
		MongoCredential credential;
		credential = MongoCredential.createCredential("sampleUser", "myDb", "password".toCharArray());
		System.out.println("Connected to the database successfully");

		// Accessing the database
		MongoDatabase database = mongo.getDatabase("myDb");

		// Retrieving a collection
		MongoCollection<Document> collection = database.getCollection("sampleCollection");
		System.out.println("Collection sampleCollection selected successfully");
		Document document1 = new Document("title", "MongoDB")
		.append("description", "database")
		.append("likes", 100)
		.append("url", "http://www.Microlead.fr/mongodb/")
		.append("by", "Microlead");
		Document document2 = new Document("title", "RethinkDB")
		.append("description", "database")
		.append("likes", 200)
		.append("url", "http://www.Microlead.fr/rethinkdb/")
		.append("by", "Microlead");
		List<Document> list = new ArrayList<Document>();
		list.add(document1);
		list.add(document2);
		collection.insertMany(list);
		// Getting the iterable object
		FindIterable<Document> iterDoc = collection.find();
		int i = 1;
		// Getting the iterator
		Iterator it = iterDoc.iterator();
		while (it.hasNext()) {
			System.out.println(it.next());
			i++;
		}
	}
}
```

A la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully
Collection sampleCollection selected successfully
Document{{_id=5dce4e9ff68a9c2449e197b2, title=MongoDB, description=database, likes=100, url=http://www.Microlead.fr/mongodb/, by=Microlead}}
Document{{_id=5dce4e9ff68a9c2449e197b3, title=RethinkDB, description=database, likes=200, url=http://www.Microlead.fr/rethinkdb/, by=Microlead}}
```

## Document de mise à jour

Pour mettre à jour un document de la collection, la méthode ```updateOne()``` de la classe ```com.mongodb.client.MongoCollection``` est utilisée.

Le programme suivant permet de sélectionner le premier document.

```java
import com.mongodb.client.FindIterable; 
import com.mongodb.client.MongoCollection; 
import com.mongodb.client.MongoDatabase; 
import com.mongodb.client.model.Filters; 
import com.mongodb.client.model.Updates; 
import java.util.Iterator; 
import org.bson.Document;  
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  
public class UpdatingDocuments { 

    public static void main( String args[] ) {  

        // Creating a Mongo client 
        MongoClient mongo = new MongoClient( "localhost" , 27017 ); 

        // Creating Credentials 
        MongoCredential credential; 
        credential = MongoCredential.createCredential("sampleUser", "myDb", 
            "password".toCharArray()); 
        System.out.println("Connected to the database successfully");  

        // Accessing the database 
        MongoDatabase database = mongo.getDatabase("myDb"); 
        // Retrieving a collection 
        MongoCollection<Document> collection = database.getCollection("sampleCollection");
        System.out.println("Collection myCollection selected successfully"); 
        collection.updateOne(Filters.eq("title", 1), Updates.set("likes", 150));       
        System.out.println("Document update successfully...");  

        // Retrieving the documents after updation 
        // Getting the iterable object
        FindIterable<Document> iterDoc = collection.find(); 
        int i = 1; 
        // Getting the iterator 
        Iterator it = iterDoc.iterator(); 
        while (it.hasNext()) {  
            System.out.println(it.next());  
            i++; 
        }     
    }  
}
```

A la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully
Collection myCollection selected successfully
Document update successfully...
Document{{_id=5dce4e9ff68a9c2449e197b2, title=MongoDB, description=database, likes=100, url=http://www.Microlead.fr/mongodb/, by=Microlead}}
Document{{_id=5dce4e9ff68a9c2449e197b3, title=RethinkDB, description=database, likes=200, url=http://www.Microlead.fr/rethinkdb/, by=Microlead}}
```

## Supprimer un document

Pour supprimer un document de la collection, vous devez utiliser la méthode ```deleteOne()``` de la classe ```com.mongodb.client.MongoCollection```.

Voici le programme pour supprimer un document -

```java
import com.mongodb.client.FindIterable; 
import com.mongodb.client.MongoCollection; 
import com.mongodb.client.MongoDatabase; 
import com.mongodb.client.model.Filters;  
import java.util.Iterator; 
import org.bson.Document; 
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  
public class DeletingDocuments { 

    public static void main( String args[] ) {  

        // Creating a Mongo client 
        MongoClient mongo = new MongoClient( "localhost" , 27017 );

        // Creating Credentials 
        MongoCredential credential; 
        credential = MongoCredential.createCredential("sampleUser", "myDb", 
            "password".toCharArray()); 
        System.out.println("Connected to the database successfully");  

        // Accessing the database 
        MongoDatabase database = mongo.getDatabase("myDb"); 
        // Retrieving a collection
        MongoCollection<Document> collection = database.getCollection("sampleCollection");
        System.out.println("Collection sampleCollection selected successfully"); 
        // Deleting the documents 
        collection.deleteOne(Filters.eq("title", "MongoDB")); 
        System.out.println("Document deleted successfully...");  

        // Retrieving the documents after updation 
        // Getting the iterable object 
        FindIterable<Document> iterDoc = collection.find(); 
        int i = 1; 
        // Getting the iterator 
        Iterator it = iterDoc.iterator(); 
        while (it.hasNext()) {  
            System.out.println(it.next());  
            i++; 
        }       
    } 
}
```

A la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully 
Collection sampleCollection selected successfully 
Document deleted successfully...
Document{{_id=5dce4e9ff68a9c2449e197b3, title=RethinkDB, description=database, likes=200, url=http://www.Microlead.fr/rethinkdb/, by=Microlead}}
```

## Déposer une collection

Pour supprimer une collection d'une base de données, vous devez utiliser la méthode ```drop()``` de la classe ```com.mongodb.client.MongoCollection```.

Voici le programme pour supprimer une collection -

```java
import com.mongodb.client.MongoCollection; 
import com.mongodb.client.MongoDatabase;  
import org.bson.Document;  
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  
public class DropingCollection { 

    public static void main( String args[] ) {  
        // Creating a Mongo client 
        MongoClient mongo = new MongoClient( "localhost" , 27017 ); 
        // Creating Credentials 
        MongoCredential credential; 
        credential = MongoCredential.createCredential("sampleUser", "myDb", 
            "password".toCharArray()); 
        System.out.println("Connected to the database successfully");  

        // Accessing the database 
        MongoDatabase database = mongo.getDatabase("myDb");  

        // Creating a collection 
        System.out.println("Collections created successfully"); 
        // Retrieving a collection
        MongoCollection<Document> collection = database.getCollection("sampleCollection");
        // Dropping a Collection 
        collection.drop(); 
        System.out.println("Collection dropped successfully");
    } 
}
```

À la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully 
Collection sampleCollection selected successfully 
Collection dropped successfully
```

## Liste de toutes les collections

Pour lister toutes les collections d'une base de données, vous devez utiliser la méthode ```listCollectionNames()``` de la classe ```com.mongodb.client.MongoDatabase```.

Le programme suivant permet de lister toutes les collections d'une base de données.

```java
import com.mongodb.client.MongoDatabase; 
import com.mongodb.MongoClient; 
import com.mongodb.MongoCredential;  
public class ListOfCollection { 

    public static void main( String args[] ) {  

        // Creating a Mongo client 
        MongoClient mongo = new MongoClient( "localhost" , 27017 ); 
        // Creating Credentials 
        MongoCredential credential; 
        credential = MongoCredential.createCredential("sampleUser", "myDb", 
            "password".toCharArray()); 
        System.out.println("Connected to the database successfully");  

        // Accessing the database 
        MongoDatabase database = mongo.getDatabase("myDb"); 
        System.out.println("Collection created successfully"); 
        for (String name : database.listCollectionNames()) { 
            System.out.println(name); 
        } 
    }
}
```

À la compilation, le programme ci-dessus donne le résultat suivant -

```
Connected to the database successfully 
Collection created successfully 
myCollection 
myCollection1 
myCollection5
```

Les autres méthodes MongoDB ```save()```, ```limit()```, ```skip()```, ```sort()``` etc. fonctionnent de la même manière que celle expliquée dans le tutoriel suivant.