La boucle ```switch``` est utilisée pour effectuer différentes actions en fonction de différents résultats retournés lors du test d’une égalité. En d’autres termes, si plusieurs ```else if``` doivent être écrits à la suite dans un programme, la boucle ```switch``` est utilisée.

__Remarque__ : En programmation, ```switch``` est appelé une boucle. Il existe d’autres boucles qui sont détaillées dans d’autres cours.

## Syntaxe

Voici la syntaxe de la boucle ```switch``` :

```js
switch(expression) {
	case 1:
        // Code à exécuter
        break;
	case 2:
        // Codes à exécuter
        break;

	default :
	    // Code à exécuter par défaut
}
```

Voici comment fonctionne la boucle ```switch``` :

- Le programme entre dans la boucle pour tester les différentes valeurs qui peuvent être passées à l’expression.
- Si la valeur vaut 1, le code du bloc est exécuté et le programme sort de la boucle. 
- Sinon, le programme regarde si la valeur vaut 2. Si tel est le cas, le code est exécuté et le programme quitte la boucle.
- Sinon, le programme exécute le bloc de code placé après le ```default```.

## Le mot-clé break

Quand le programme rencontre le mot-clé ```break;``` il sort de la boucle ```switch```. En d’autres termes, cela arrête l’exécution de la boucle. 

Il n’est pas nécessaire d’ajouter un ```break``` à la dernière instruction de la boucle, car l’exécution s’arrête-là, quoi qu’il en soit. 

__Remarque__ : Si un ```break``` est oublié après un bloc d’instruction, le programme passera au bloc suivant, peu importe que l’évaluation soit bonne ou mauvaise. 

## Le mot-clé default

Ce mot-clé définit le code à exécuter si aucune des cases de la boucle ne correspond. 

Exemple :

```js
var userAge = 12, text = "";
switch(userAge) {
	case 16 :
        text = "Vous pourrez voter dans 2 ans";
        break
	
	case 18 : 
	    text = "Vous êtes en âge de voter";

	default :
	    text = "Vous n'êtes pas en âge de voter";
}
```

Dans cet exemple, c’est le texte contenu dans le ```default``` qui est retourné, car la variable ```userAge``` est initialisée à 12, et aucune des cases de la boucle ne correspond.

__Remarque__ : De manière générale, le bloc ```default``` est écrit à la fin de la boucle, mais rien n’oblige à la faire. Ainsi le code ci-dessous fonctionne-t-il très bien :

Exemple :

```js
var userAge = 12, text = "";
switch(userAge) {
	default :
	    text = "Vous n'êtes pas en âge de voter";
        break;

	case 16 :
        text = "Vous pourrez voter dans 2 ans";
        break
	
	case 18 : 
	    text = "Vous êtes en âge de voter";
}
```

Si ```default``` n’est pas le dernier bloc de la boucle, il faut penser à y ajouter un ```break``` à la fin du bloc.
