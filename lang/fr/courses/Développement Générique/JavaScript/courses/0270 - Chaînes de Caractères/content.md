En JavaScript, les chaînes de caractères - communément appelées par leur nom anglais *string* - sont utilisées pour stocker et manipuler du texte.

## Les chaînes de caractères

En langage JavaScript, un string contient zéro caractère ou plus placé entre guillemets. Les chaînes de caractères peuvent être placées entre guillemets simples (‘ ’) ou doubles (“ ”).

Exemple avec des guillemets simples :

```js
var x = 'Ceci est une chaîne de caractères';
```

Exemple avec des guillemets doubles :

```js
var y = "Ceci est une autre chaîne de caractères";
```

__Remarque__ : Des guillemets peuvent être utilisés au sein d’une chaîne de caractères, du moment que ces guillemets sont différents de ceux qui entourent le string. 

Exemple :

```js
var z = 'Voici des guillemets simples qui "entourent" une chaîne de caractères';
```

Dans cet exemple, le mot *entoure* est encadré par des guillemets doubles, différents des guillemets simples qui entourent la totalité de la chaîne de caractères.

## Longueur d’un string

Le langage JavaScript met à disposition une propriété afin de terminer la taille d’une chaîne de caractères : **length**.

Exemple :

```js
var chaine = "Bonjour !";
console.log(chaine.length);  /* Ici, la console affiche le chiffre 8, car la variable chaine contient 8 caractères */
```

## Échapper un caractère

Il existe certains caractères que le langage JavaScript pourrait confondre avec des caractères réservés aux *strings* ; c’est pourquoi il est possible “d’échapper” un caractère afin que celui-ci soit interprété comme appartenant à la chaîne de caractères.

Exemple :

```js
var x = "Cette string ne sera pas correctement "lue" par le navigateur"; 
```

Dans l’exemple ci-dessus, le mot *lue* ne sera pas correctement interprété par le navigateur, car des guillemets doubles entourent ce mot, alors que ces mêmes guillemets sont utilisés pour entourer la chaîne de caractères. 

Pour résoudre ce problème, il faut utiliser le caractère d'échappement : le backslash (\).

Exemple : 

```js
var x = "Cette string sera correctement \"lue\" par le navigateur"; 
```

Dans cet exemple, le mot *lu* est correctement interprété par le navigateur, car les guillemets doubles sont échappés, donc non considérés comme ceux entourant la chaîne de caractères. 

Il existe d’autres caractères à échapper en JavaScript :

- ```\’``` : permet d’insérer un guillemet simple
- ```\\``` : permet d’insérer un autre backslash

## Couper les longues lignes de code

Pour des raisons de lisibilité du code, il est recommandé de couper les longues lignes de code. De manière générale, les lignes de codes ne dépassent pas plus de 80 caractères. 

Afin que cette recommandation puisse être appliquée, il existe deux possibilités pour couper les lignes de code :

- Après un opérateur (**=**, par exemple)
- Un backslash peut être utilisé pour couper une ligne de code au sein d’une chaîne de caractères. Cependant, cette méthode n’est pas recommandée, car certains navigateurs ne permettent pas d’insérer un espace après un backslash.
- Utiliser la concaténation de string à l’aide de l’opérateur **+**

## Les chaînes de caractères peuvent être des objets

De manière générale, les chaînes de caractères sont des valeurs primitives créées et stockées dans des variables.

Exemple :

```js
var x = "Ceci est une chaîne de caractères";
```

Cependant, une chaîne de caractères peut également être créée comme un objet, avec le mot-clé ```new```.

Exemple :

```js
var y = new String("Ceci est une chaîne de caractères déclarée comme un objet");
```

__Remarque__ : Il n’est pas recommandé de créer une chaîne de caractères comme un objet. Cela complique le code et peut retourner des résultats inattendus.