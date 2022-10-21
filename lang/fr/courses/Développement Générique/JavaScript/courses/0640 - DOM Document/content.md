L’objet ```document``` représente la page web. Pour accéder à n’importe quel élément HTML, il faut d’abord accéder à l’objet ```document```.

## Trouver des éléments HTML

Ci-dessous, quelques méthodes de l’objet ```document``` permettant de trouver un élément HTML :

- ```document.getElementById(‘id’)``` : permet de trouver un élément avec son ```id```
- ```document.getElementsByTagName``` : permet de trouver un élément HTML grâce au nom du tag (par exemple : ```<p>```)
- ```document.getElementsByClassName``` : permet de trouver un élément grâce au nom de sa classe.

## Modifier des éléments HTML

Voici la liste des propriétés permettant de modifier des éléments HTML :

- ```element.innerHTML = “Nouveau contenu HTML”``` : Change le contenu HTML d’un élément.
- ```element.attribute = “Nouvelle valeur”``` : Change la valeur de l’attribut d’un élément HTML.
- ```element.style.property = “Nouveau style”``` : Change le style d’un élément HTML.

Il existe également une méthode permettant de modifier des éléments HTML :

- ```element.setAttribute(attribut, valeur)``` : permet de modifier la valeur d’un attribut HTML.

## Ajouter et effacer des éléments

Ci-dessous, la liste des méthodes permettant d’ajouter et modifier des élément HTML : 

- ```document.createElement(element)``` : Permet de créer un nouvel élément HTML
- ```document.removeChild(element)``` : Permet de supprimer un élément HTML
- ```document.appendChild(element)``` : Une fois l’élément HTML créé, cette méthode permet de l’ajouter au document HTML
- ```document.replaceChild(new, old)``` : Permet de remplacer un élément par un autre
- ```document.write(text)``` : Permet d’écrire dans le flux HTML

## Ajouter des évènements

Le grand avantage du Javascript - et ce qui l’a rendu aussi populaire - c’est qu’il permet de gérer les évènements. 

En informatique, un événement est toute action effectuée par l’utilisateur sur le site. Par exemple : un clic sur un lien, le survol d’un élément avec la souris, etc.

Il existe une méthode qui permet d’écouter un évènement sur un élément HTML :

- ```document.getElementById(id).onclick = function(){code}``` : permet d'exécuter une fonction anonyme lors du clic sur un élément

## Trouver des objets HTML

Il existe plusieurs méthodes permettant de trouver un objet HTML. En voici une liste non-exhaustive :

- ```document.anchors``` : retourne tous les éléments HTML ```<a>``` ayant un attribut name
- ```document.body``` : retourne l’élément ```<body>``` du document
- ```document.cookie``` : retourne le cookie d’un document
- ```document.doctype``` : retourne le doctype d’un document
- ```document.documentElement``` : retourne l’élément ```<html>``` d’un document
- ```document.documentURI``` : retourne l’URI du document
- ```document.domain``` : retourne le nom de domaine du serveur du document
- ```document.embed``` : retourne tous les ```<embed>``` d’un document
- ```document.form``` : retourne tous les éléments ```<form>``` d’un document
- ```document.head``` : retourne l’élément ```<head>``` d’un document
- ```document.images``` : retourne tous les éléments ```<img>``` d’un document
- ```document.implementation``` : retourne l’implémentation DOM
- ```document.inputEncoding``` : retourne l’encodage du document (attribut HTML charset)
- ```document.lastModified``` : retourne la date et l’heure de la dernière modification du document
- ```document.links``` : retourne tous les éléments ```<area>``` et ```<a>``` ayant un attribut ```href```
- ```document.readyState``` : retourne le statut de chargement du document
- ```document.scripts``` : retourne la totalité de l’élément ```<script>```
- ```document.strictErrorChecking``` : retourne si la vérification de l’erreur est renforcé
- ```document.title``` : retourne l’élément ```<title>```
- ```document.URL``` : retourne l’URL complète du document