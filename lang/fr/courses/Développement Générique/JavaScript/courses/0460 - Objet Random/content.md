Il est des moments où un développeur a besoin qu’un nombre au hasard soit généré automatiquement.

Pour ce faire, le langage JavaScript met à disposition l’objet Random.

## Math.random()

Cette méthode retourne un nombre généré au hasard entre 0 inclus et 1 exclu.

Exemple :

```js
Math.random(); // Retourne, ici, 0.1322070779637874
```

## Générer un nombre entier au hasard

Le problème de ```Math.random()``` est qu’elle génère un nombre décimal. Alors comment faire pour générer au hasard un nombre entier ? La réponse est simple : utiliser ```Math.floor()```.

Exemple :

```js
Math.floor(Math.random() * 10); // Ici, un nombre entre 0 et 9 est généré au hasard
```

## Fonction “random” propre

Le mieux, pour générer un nombre entier au hasard, est de créer une fonction. 

Voilà à quoi peut ressembler une fonction “random” :

```js
function randomNumber(min, max) {
	return Math.floor(Math.random * (max - min)) + min ;
}
```

Ici, la fonction ```randomNumber``` retourne un nombre situé entre ```min``` et ```max```, tous deux inclus. 