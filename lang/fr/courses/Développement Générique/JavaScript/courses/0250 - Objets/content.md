Comme beaucoup de langages de programmation, le JavaScript permet d’utiliser la notion d’objet dans la notation du code. 

## Définition d’un objet

Dans la vie de tous les jours, il y a des objets partout (voitures, stylos, tables, maisons, etc.). Chacun de ces objets a des **propriétés** qui lui sont propres comme la taille et le poids et des **méthodes** telles que le start and stop pour une voiture, par exemple. 

Pour chaque objet, les propriétés sont communes, mais les valeurs qu’elles contiennent sont différentes (le poids et la taille diffère d’un stylo à l’autre, mais chaque stylo a, pour sûr, une taille et un poids).

De même, chaque objet a les mêmes méthodes, mais chacune est appelée à un moment différent. 

## Les objets en JavaScript

En JavaScript, les objets sont des variables qui contiennent plusieurs valeurs. 

### Syntaxe

Voici la syntaxe des objets en JavaScript :

```js
var nomDeLObjet = { propriété1: valeur1, propriété2: valeur2 };
```

__Remarque__ : La combinaison ```propriété:valeur``` s’appelle combinaison ```clé:valeur```. Attention aux deux points qui permettent de séparer la valeur de la clé.

## Écrire sur plusieurs lignes

La déclaration peut se faire sur une seule ligne, mais pour des raisons de lisibilité du code, il est recommandé de l’écrire sur plusieurs lignes.

Exemple :

```js
var stylo = { 
	couleur: "bleu",
	marque: "MicroLead",
	type: "bille"
};
```

## Les propriétés d’objet

Les combinaisons ```clé:valeur``` représentent les **propriétés** d’un objet.

### Accéder à une propriété

En JavaScript, il existe deux moyens d’accéder à un objet :

En utilisant la syntaxe ```nomDeLObjet.propriété```
En utilisant la syntaxe des tableaux : ```nomDeLObjet[“nomDeLaPropriété”]```

Exemple en utilisant la première syntaxe :

```js
console.log(stylo.couleur); // La console affiche "bleu"
```

Exemple en utilisant la deuxième syntaxe :

```js
console.log(stylo["couleur"]); // La console affiche également "bleu"
```

## Les méthodes d’objet

En JavaScript Objet, les méthodes sont des actions effectuées sur un objet. En d’autres termes, ce sont des fonctions définies au sein d’un objet, qui permettent d’effectuer une action sur cet objet. 

Exemple :

```js
var stylo = { 
	couleur: "bleu",
	marque: "MicroLead",
	type: "bille"
	afficherStylo: function() { console.log(this.couleur + this.marque + this.type); }
};
```

Dans cet exemple, lorsque la propriété ```afficherStylo``` est appelée, la couleur, la marque et le type du stylo sont affichés dans la console.

### Le mot-clé this

Le mot clé ```this```, en JavaScript objet, désigne l’objet au sein duquel est déclarée la fonction. En d’autres termes, dans l’exemple précédent, le mot-clé ```this``` désigne l’objet en lui-même, donc ```stylo```.

### Accéder aux méthodes d’objet

La syntaxe permettant d’accéder à une méthode d’objet est quasiment similaire à celle donnant accès aux propriétés d’objet.

```js
nomDeLObjet.nomDeLaMethode();
```

Accéder à la méthode sans utiliser les parenthèses permet d’accéder à la définition de la méthode. 

Exemple :

```js
console.log(stylo.afficherStylo); // Affiche dans la console "function() { console.log(this.couleur + this.marque + this.type); }"
```