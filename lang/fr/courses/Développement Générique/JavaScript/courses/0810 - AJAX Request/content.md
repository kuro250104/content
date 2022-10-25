L’objet ```XMLHttpRequest``` est utilisé afin de récupérer des données stockées sur un serveur. 

## Envoyer une requête au serveur

Pour envoyer une requête à un serveur, les méthodes ```open()``` et ```send()``` sont utilisées.

Exemple :

```js
xhttp.open("GET", "ajax_info.txt", true);
xhttp.send();
```

## L’URL - Fichier sur le serveur

Le paramètre ```url``` de la méthode ```open()``` est l’adresse d’un fichier se trouvant sur le serveur. L’extension du fichier à ouvrir peut être de n’importe quel type, tel que .txt, .php, .asp, etc.

Exemple :

```js
xhttp.open("GET", "ajax_test.asp", true);
```

Cet exemple ouvre le fichier “ajax_test.asp” situé sur le serveur.

## Asynchrone - true ou false ?

Les requêtes faites sur un serveur doivent être envoyées de manière asynchrone. Par conséquent, le paramètre ```async``` de la méthode ```open()``` doit être définie à **true**.

Exemple :

```js
xhttp.open("GET", "ajax_test.asp", true);
```

En envoyant des requêtes de manière asynchrone, Javascript n’attend pas la réponse du serveur, mais peut en revanche :

- Exécuter d’autres scripts en attendant la réponse du serveur
- Gérer la réponse une fois que celle-ci est prête

__Remarque__ : La valeur par défaut de ```async``` est **true**. Le définir à **false** n’est pas recommandé, car le programme s’arrête jusqu’à ce que la réponse soit reçue.

## GET ou POST ?

GET est plus rapide et plus simple que POST. Il peut être utilisé dans la plupart des cas.

Cependant, il faut toujours utiliser POST dans les situations suivantes :

- Pour envoyer un nombre élevé de données au serveur (POST n’a pas de limitation de taille)
- Envoyer des données saisies par l’utilisateur. POST est beaucoup plus sécurisé que GET.

### Requêtes GET

Voici un requête GET simple :

```js
xhttp.open("GET", "demo_get.asp");
xhttp.send();
```

Pour envoyer des informations avec une requête GET, il suffit d’ajouter les informations dans l’URL.

Exemple :

```js
xhttp.open("GET", "demo_get2.asp?fname=Henry&lname=Ford");
xhttp.send();
```

### Requêtes POST

Ci-dessous, une requête POST simple :

```js
xhttp.open("POST", "demo_post.asp");
xhttp.send();
```

Pour envoyer des données avec POST, comme des données récupérées par un formulaire HTML, par exemple, il faut ajouter un header HTTP avec ```setRequestHeader```. Il faut ensuite spécifier les données à envoyer dans la méthode ```send()```.

Exemple :

```js
xhttp.open("POST", "ajax_test.asp");
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xhttp.send("fname=Henry&lname=Ford");
```

Dans cet exemple, une requête POST est envoyée. Ensuite, une header HTTP est créé avec la méthode ```setRequestHeader()```. Enfin, les données à envoyer sont spécifiées au sein de la méthode ```send()```.

## Requêtes synchrones

Pour effectuer une requête synchrone, il suffit de changer le troisième paramètre de la méthode ```send()``` à **false**.

Exemple :

```js
xhttp.open("GET", "ajax_info.txt", false);
```

La plupart du temps, les requêtes synchrones sont utilisées pour effectuer des tests rapides. Ces requêtes synchrones sont aussi trouvables dans de vieux codes JavaScript.

De plus, comme le programme attend que le serveur renvoie une réponse avant de continuer, il n’y a pas besoin d’une méthode ```onreadystatechange```.

Exemple :

```js
xhttp.open("GET", "ajax_info.txt", false);
xhttp.send();
document.getElementById("demo").innerHTML = xhttp.responseText;
```