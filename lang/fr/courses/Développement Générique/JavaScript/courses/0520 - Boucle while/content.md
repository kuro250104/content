La boucle ```while``` (*tant que*, en français), est utilisée afin d’exécuter un bloc de code tant qu’une condition spécifiée est vraie. 

## Boucle while

### Syntaxe

Ci-dessous, la syntaxe de la boucle ```while``` :

```js
while (condition) {
	// Code
}
```

### Utilisation

Tel que mentionné dans l’introduction, le but d’une boucle ```while``` est d’exécuter un bloc de code *tant qu*’une condition particulière est vraie. Une fois que cette condition devient fausse, le programme sort de la boucle et le reste du code est alors exécuté.

Exemple :

```js
var texte = "";
while( i < 10) {
	texte += "Bonjour";
	i++
};
```

Ici, le texte “Bonjour” est passé en valeur de la variable ```texte``` tant que ```i``` est inférieure à 10. De plus, à chaque passage dans la boucle, la variable ```i``` est incrémenté.

__Remarque__ : Il ne faut surtout pas oublier d’incrémenter ```i``` à chaque passage dans la boucle, sinon cela créera une boucle infinie - et le programme pourrait alors planter.

## La boucle do while

Cette boucle - signifiant *faire tant que*, en français - est similaire à ```while``` à ceci près que le programme entre une première fois dans la boucle **avant** de vérifier si la condition est vraie. Ensuite, il continue de rentrer dans la boucle tant que la condition est vraie, et s’arrête une fois que la condition est fausse. 

Exemple :

```js
var texte = "";
do {
	texte += "Bonjour";
	i++
} while( i < 10);
```

Dans cet exemple, le programme rentre une première fois dans la boucle - et exécute le code qui s’y trouve - avant de vérifier la condition.