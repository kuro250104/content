La notation arrow (*fléchée*, en anglais) pour les fonctions a été introduite en 2015.

## La notation flechée

Ce moyen d’écrire une fonction en JavaScript permet de raccourcir le code et de gagner du temps. 

### Syntaxe

Voici, normalement, comment s’écrit une fonction en JavaScript :

```js
variable = maFonction(paramètre 1, paramètre 2) {
    // Code à exécuter
}
```

Désormais, voici comment il est possible d’écrire une fonction JavaScript avec la noation fléchée :

```js
variable = () => {
    // Code à exécuter
}
```

Comme pour une fonction, si la fonction arrow doit recevoir des paramètres, ceux-ci sont placés entre les parenthèses.

Exemple :

```js
variable = (parametre) => {
    // Code à exécuter
}
```

Il est également possible, si la fonction ne prend qu’**un seul** paramètre, de ne pas mettre les parenthèses. 

Exemple :

```js
variable = parametre => {
	// Code à exécuter
}
```