L’élément ```break``` permet de sortir d’une boucle ; tandis que ```continue``` permet de sauter une itération supplémentaire au sein d’une boucle. 

## Break

Cet élément a déjà été évoqué dans le cours sur la boucle ```switch``` - car c’est son utilisation la plus commune. 

```Break``` permet de sortir d’une boucle lorsqu’un bloc de code a été exécuté.

Exemple :

```js
var x = 3;
switch(x) {
	case 1:
        // Code
        break;

	case 2:
        // Code
        break;

	default:
	    // Code
}
```

## Continue

L’élément ```continue``` permet de sauter une itération là où une condition particulière est remplie. 

Exemple :

```js
while (i < 100) {
	if(i === 2) { continue; }
	text = i + "<br />"
}
```

Dans cet exemple, tous les chiffres de 0 à 99 sont affichés, excepté le chiffre 2, car dans le code, il y a un continue. Cela va donc sauter le 2 et afficher directement le 3.

## Label en Javascript

### Syntaxe 

Pour déclarer un label en JavaScript, il suffit d’écrire le nom du label suivi de deux points (:) :

```js
nom_du_label :
declaration
```

Les éléments ```break``` et ```continue``` sont les seuls éléments en JavaScript permettant de sortir ou sauter d’un bloc de code. 

La syntaxe est la suivante :

```js
break nom_du_label
continue nom_du_label
```

```continue```, avec ou sans label, ne peut sauter **qu’une seule itération de boucle**.
```break```, sans label, ne peut sortir **que d’une boucle ou d’un switch**.

Exemple :

```js
const numbers = [56, 25, 70, 3];
list: {
    text += cars[0] + "<br>";
    text += cars[1] + "<br>";
    text += cars[2] + "<br>";
    break list;
    text += cars[3] + "<br>";
}
```

Dans cet exemple, le programme sort du bloc de code juste après 70. 3 n’est donc pas retourné par le programme.

__Remarque__ : Est appelé “bloc de code” toute instruction ou code placé entre accolade ouvrante et fermante (**{ }**).