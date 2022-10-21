```Location``` est une interface qui nous permet d’obtenir des informations relatives à l’URL d’une page.

On peut y accéder à partir des interfaces ```Window``` et ```Document``` grâce à leur propriété respective ```location```.

## Rappels sur la construction d’une URL

Pour bien saisir les différentes utilisations de l’objet “location”, il est important de bien comprendre comment une URL est construite. Voici un exemple d’URL complet :

```http
http://www.sd.ndd.fr:80/chemin/fichier.html?cle=abc&cle2=def#coucou
```

Et voici le découpage que l’on peut faire de cette url : 

- ```http://``` : correspond au “protocole” utilisé pour que le navigateur accède au document souhaité.
- ```www.sd.ndd.fr``` : correspond à “l’url de base” du site, qui peut lui-même être découpé en différentes parties :
    - ```www``` : constitue le “préfixe” (maintenant optionnel)
    - ```sd``` : constitue un “sous domaine”
    - ```ndd.fr``` : constitue le nom de domaine
    - ```fr``` : correspond à l’extension
- ```:80``` : Correspond au “port” utilisé pour atteindre le document sur le serveur. Ce paramètre est optionnel, et “80” est sa valeur par défaut.
- ```/chemin/fichier.html``` : correspond au “chemin” permettant d’atteindre le document souhaité.
- ```?cle=abc&cle2=def``` : correspond à des “paramètres” que peuvent nécessiter les sites internet pour fonctionner correctement.
- ```#coucou``` : correspond à une “ancre”, c'est-à-dire un lien à l’intérieur de la page.

## Propriétés et Méthodes

L’objet Location va nous donner une dizaine de propriétés intéressantes :

- L’attribut ```hash``` retourne l'ancre d'une URL si elle en possède une, incluant le symbole “#”.
- L’attribut ```search``` retourne les paramètres de l’URL si elle en possède une, incluant le symbole “ ?”.
- L’attribut ```pathname``` retourne le chemin de l’URL précédé par un “/”.
- L’attribut ```href``` retourne l’URL entière.
- L’attribut ```hostname``` retourne l’url de base.
- L’attribut ```port``` retourne le port de l’URL si celui par défaut n’est pas spécifié.
- L’attribut ```protocol``` retourne le protocole de l’URL
- L’attribut ```host``` retourne l’url de base ainsi que le port relatif à l’URL
- L’attribut ```origin``` retourne le protocole, l’url de base et le port de l’URL

L’objet ```Location``` nous propose également 3 méthodes principalement utilisées :

- La méthode ```reload()``` permet de recharger la page actuelle.
- La méthode ```assign()``` permet de charger une ressource à partir d’une URL passée en argument.
- La méthode ```replace()``` permet de remplacer le document actuel par un autre disponible à l’URL fournie en argument.

Attention, la différence entre les méthodes ```assign()``` et ```replace()``` est que la première permet d’inclure l’url AVANT le rechargement dans l’historique de navigation, alors que la seconde ne l’intègre pas. Ainsi lorsque vous utilisez ```replace()```, l’url existante avant l’appel de la méthode ne sera pas enregistrée dans l’historique.

## Exemples

Pour cet exemple, nous partirons du principe que l’url sur laquelle nous nous trouvons est la suivante :

```http
http://www.sd.ndd.fr:80/chemin/fichier.html?cle=abc&cle2=def#coucou
```

```js
// Affiche : #coucou
console.log( location.hash )

// Affiche : ?cle=abc&cle2=def
console.log( location.search )

// Affiche : /chemin/fichier.html
console.log( location.pathname )

// Affiche : http://www.sd.ndd.fr:80/chemin/
// fichier.html?cle=abc&cle2=def#coucou
console.log( location.href )

// Affiche : www.sd.ndd.fr
console.log( location.hostname )

// Affiche : 80
console.log( location.port )

// Affiche : http://
console.log( location.protocol )

// Affiche : www.sd.ndd.fr:80
console.log( location.host )

// Affiche : http://www.sd.ndd.fr:80
console.log( location.origin )

// renvoie l’utilisateur sur google
location.assign(“http://google.com”)

// recharge la page courante
location.reload()

// renvoie l’utilisateur sur google
location.replace(“http://google.com”)
```