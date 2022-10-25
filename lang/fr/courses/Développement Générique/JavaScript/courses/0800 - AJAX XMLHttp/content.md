L’objet ```XMLHttpRequest``` est la clé de voûte de l’AJAX. Tous les navigateurs modernes le supportent et cet objet permet d’échanger des données en arrière-plan avec un serveur web. Il est donc possible de mettre à jour certaines parties d’une page web sans avoir besoin de la recharger. Cela améliore grandement l’expérience utilisateur. 

## Créer un objet XMLHttpRequest

Tous les navigateurs modernes ont un objet ```XMLHttpRequest``` intégré. 

La syntaxe pour créer cet objet est la suivante :

```js
variable = new XMLHttpRequest();
```

## Définir une fonction de rappel

Une fonction de rappel (*callback function* en anglais), est une fonction passée en paramètre d’une autre fonction.

En AJAX, cette fonction doit contenir le code à exécuter lorsque la réponse à été reçue :

```js
xhttp.onload = function() {
  // Code à exécuter lorsque la réponse a été reçue
}
```

## Envoyer une requête

Pour envoyer une requête à un serveur web, les méthodes ```open()``` et ```send()```, appartenant à l’objet ```XMLHttpRequest```, sont utilisées.

Voici les syntaxes pour utiliser ces deux méthodes :

```js
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

Exemple :

```js
// Création de l'objet XMLHttpRequest
const xhttp = new XMLHttpRequest();

// Définition de la fonction callback
xhttp.onload = function() {
  // Ici, les données récupérées sont utilisables
}

// Envoie d'une requête
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

## Accès à plusieurs domaines

Pour des raisons de sécurité, les navigateurs modernes n’autorisent pas, par défaut, l’accès à plusieurs domaines.

Cela signifie que la page web qui envoie la requête et le fichier à charger pour récupérer les données doivent se situer sur le même serveur.

## Méthodes de l’objet XMLHttpRequest

Voici une liste des méthodes utilisables avec l’objet ```XMLHttpRequest``` :

- ```new XMLHttpRequest()``` : permet de créer un nouvel objet de type ```XMLHttpRequest```.
- ```abort()``` : annule la requête actuelle
- ```getAllResponseHeaders()``` : retourne les informations d’en-tête
- ```getReponseHeader()``` : retourne une information d’en-tête spécifique
- ```open(method, url, async, user, psw)``` : définit le type de requête
    - ```method``` : précise le type de la requête : ```GET``` ou ```POST```
    - ```url``` : l’URL de l’endroit où se trouve le fichier
    - ```async``` : vaut **true** si la requête est asynchrone, et **false** si elle ne l’est pas
    - ```user``` : paramètre optionnel précisant un nom d’utilisateur si besoin
    - ```pwd``` : paramètre optionnel précisant un mot de passe si besoin
- ```send()``` : envoie la requête au serveur. Utilisé pour les requêtes de type GET
- ```send(string)``` : Envoie la requête au serveur. Utilisé pour les requêtes POST
- ```setRequestheader()``` : Ajoute une paire étiquette/valeur au header à envoyer

## Les propriétés de l’objet XMLHttpRequest

Ci-dessous la liste des propriétés de l’objet ```XMLHttpRequest``` :

- ```onload``` : Défini une fonction à appeler lorsque la réponse est reçue
- ```onreadystatechange``` : Défini une fonction à appeler lorsque la propriété ```readyState``` change
- ```readyState``` : “Retient” le statut de la requête ```XMLHttpRequest``` :
    - ```0``` : Requête non initialisée
    - ```1``` : Connexion établie avec le serveur
    - ```2``` : Requête reçue
    - ```3``` : Traitement de la requête
    - ```4``` : Requête terminée et réponse prête
- ```responseText``` : Retourne la réponse sous forme de chaîne de caractères
- ```responseXML``` : Retourne la réponse au format XML
- ```status``` : Retourne le status de la requête sous forme de nombre :
    - ```200``` : “OK”
    - ```403``` : “Interdit”
    - ```404``` : “Fichier ou page introuvable”
- ```statusText``` : Retourne le statut de la requête sous forme de texte (“OK” ou “Introuvable”, par exemple)

## La propriété onload

L’objet ```XMLHttpRequest``` permet de définir une fonction callback lorsque la requête a reçu une réponse.

La fonction est définie avec la propriété ```onload```.

Exemple :

```js
xhttp.onload = function() {
    document.getElementById("demo").innerHTML = this.responseText;
}
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

## Fonctions callback multiples

S’il y a plus d’une requête AJAX sur une page web, il est recommandé de créer une fonction exécutant l’objet ```XMLHttpRequest```, et une fonction callback pour chaque requête AJAX.

L’appel de la fonction doit contenir l’URL et quelle fonction appelée lorsque la réponse est prête.

Exemple :

```js
loadDoc("url-1", myFunction1);

loadDoc("url-2", myFunction2);

function loadDoc(url, cFunction) {
    const xhttp = new XMLHttpRequest();
    xhttp.onload = function() {cFunction(this);}
    xhttp.open("GET", url);
    xhttp.send();
}

function myFunction1(xhttp) {
    // Code à exécuter
}
function myFunction2(xhttp) {
    // Code à exécuter
}
```

## La propriété onreadystatechange

La propriété ```readyState``` contient le statut de la requête ```XMLHttpRequest```.

La propriété ```onreadystatechange```, quant à elle, définit une fonction callback à exécuter lorsque la propriété ```readyState``` change. Cette fonction est appelée chaque fois que ```readyState``` change.

Les propriétés ```status``` et ```statusText``` “retiennent” le statut de la requête ```XMLHttpRequest```.

Exemple :

```js
function loadDoc() {
    const xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
            document.getElementById("demo").innerHTML =
            this.responseText;
        }
    };
    xhttp.open("GET", "ajax_info.txt");
    xhttp.send();
}
```

Dans cet exemple, lorsque ```readyState``` vaut 4 et ```status``` vaut 200, alors la réponse est prête.