En AJAX, les réponses renvoyées par le serveur sont récupérables grâce aux propriétés ```responseText``` et ```responseXML```.

## La propriété responseText

Cette propriété retourne la réponse du serveur sous forme d’une chaîne de caractères JavaScript. Cette chaîne de caractères est ensuite utilisable comme telle. 

Exemple :

```js
document.getElementById("demo").innerHTML = xhttp.responseText;
```

## La propriété responseXML

L’objet ```XMLHttpRequest``` a un parser XML intégré. La propriété ```responseXML``` retourne la réponse du serveur sous forme d’objet du DOM XML. Ensuite, la réponse obtenue est parsable en tant qu’objet DOM XML.

Exemple :

```js
const xmlDoc = xhttp.responseXML;
const x = xmlDoc.getElementsByTagName("ARTIST");

let txt = "";
for (let i = 0; i < x.length; i++) {
    txt += x[i].childNodes[0].nodeValue + "<br>";
}
document.getElementById("demo").innerHTML = txt;

xhttp.open("GET", "cd_catalog.xml");
xhttp.send();
```

## Les méthodes utilisables pour les réponses serveur

Il existe deux méthodes permettant d’obtenir la réponse d’un serveur :

- ```getResponseHeader()```
- ```getAllResponseHeaders()```

### La méthode getAllResponseHeaders()

Cette méthode retourne toutes les informations du header retournées par la réponse du serveur.

Exemple :

```js
const xhttp = new XMLHttpRequest();
xhttp.onload = function() {
	document.getElementById("demo").innerHTML =
    this.getAllResponseHeaders();
}
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

### La méthode getResponseHeader()

Cette méthode retourne des informations spécifiques d’un header retournées dans la réponse du serveur. 

Exemple :

```js
const xhttp = new XMLHttpRequest();
xhttp.onload = function() {
	document.getElementById("demo").innerHTML =
    this.getResponseHeader("Last-Modified");
}
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

Cet exemple retourne la date et l’heure de la dernière modification de l’URL appelée : ```Last modified: Fri, 09 Jul 2021 11:45:14 GMT```