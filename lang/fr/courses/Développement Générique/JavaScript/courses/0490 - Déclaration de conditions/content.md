Les conditions sont utilisées pour tester des égalités entre des données et effectuer des actions en fonction des résultats retournés.

## Déclarations conditionnelles

La plupart du temps, il y a besoin de tester différentes des égalités entre des données et de retourner des résultats en fonction. Pour ce faire, il faut utiliser les déclarations conditionnelles, également appelées conditions.

### La condition if

Cette condition est utilisée afin d’exécuter un code si la condition est vraie. 

Exemple :

```js
var userAge, text = "";

if(userAge >= 18) {
	return text = "A l'âge de voter";
}
```

Dans cet exemple, le if vérifie si la valeur contenue dans la variable ```userAge``` est supérieure ou égale à 18. Si tel est le cas, le texte “A l’âge de voter” est retourné.

__Remarque__ : Le mot ```if``` doit être écrit en minuscule. S’il est en majuscule, cela retournera une erreur.

### Else

```else``` Est utilisé en complément de la condition ```if``` afin de permettre au programme de pouvoir retourner quelque chose si l’expression testée dans le ```if``` n’est pas vraie. 

Exemple :

```js
var userAge, text = "";

if(userAge >= 18) {
	return text = "A l'âge de voter";
} else {
	return text = "N'a pas l'age de voter";
}
```

Dans cet exemple, si la valeur contenue dans ```userAge``` est supérieure ou égale à 18, alors le texte “A l’âge de voter” est retourné, sinon c’est “N’a pas l’âge de voter” qui est retourné. 

### Else if

Cette condition permet de rajouter un test avant un ```else```.

Exemple :

```js
var userAge, text = "";

if(userAge >= 18) {
	return text = "A l'âge de voter";
} else if (userAge >= 16 && userAge < 18) {
	return text = "Vous pourrez voter dans 2 ans";
} else {
	return text = "Vous n'avez pas l'age de voter";
}
```

Dans cet exemple, le premier ```if``` teste si la variable ```userAge``` est supérieure ou égale à 18. Si ce n’est pas le cas, le programme passe au ```else if``` et regarde si la variable est supérieure ou égale à 18 ans ; si tel est le cas, le texte “Vous pourrez voter dans 2 ans” est retourné. Sinon, le texte du ```else``` est retourné. 
