Les conditions font partie des logiques “standard” de l’ensemble des langages de programmation. Elles permettent de définir s’il faut exécuter ou non une ou plusieurs lignes de code.

Ainsi la déclaration d’une condition créera un “bloc” de ligne(s) de code, qui ne sera exécuté que si la condition est “vraie”. Si celle-ci se révèle fausse, alors le bloc ne sera tout simplement pas exécuté.

L’ensemble des conditions est exprimé à l’aide d’opérateurs. C’est donc grâce à ces derniers que PHP pourra déterminer si la condition est vraie ou fausse, et donc par extension exécuter le code concerné ou non.

## Utilisation

### La condition “si” - IF

Le “si” est la base immuable de toute condition. Elle se représente en PHP à l’aide du mot clé “ **if** ”. La condition doit alors être exprimée entre parenthèses “ **( )** ” tout de suite après le premier mot-clé. Enfin, le bloc de code à exécuter si la condition est vraie doit être écrit entre accolades “ **{ }** “, elles-mêmes placées à la suite des parenthèses.

Prenons deux exemples afin de mieux comprendre la logique :

``` php
# Déclaration d'une variable "$a", et attribution de la valeur "0"
$a = 0;

# Déclaration de la condition. Ici on teste que la valeur de "$a" soit
# strictement égale à "0".
if ($a == 0) {
	# Début du bloc à exécuter si la condition est vraie.
	echo ("vrai");
}
```

Dans l’exemple ci-dessus, la condition vérifiée est vraie. Ainsi les instructions présentent dans le bloc qui suit, entre accolades, sera exécuté. De la sorte, PHP affichera “**vrai**”.

``` php
# Déclaration d'une variable "$a", et attribution de la valeur "0"
$a = 0;

# Déclaration de la condition. Ici on teste que la valeur de "$a" soit
# strictement égale à "1".
if ($a == 1) {
	# Début du bloc à exécuter si la condition est vraie.
	echo ("vrai");
}
```

Dans l’exemple ci-dessus, PHP va tester que la valeur de ```$a``` soit bien strictement égale à “1”. Or ```$a``` est égal à zéro et la condition nous renverra donc un résultat “faux”. Ainsi l’ensemble du code présent dans le bloc corrélé à la condition ne sera pas exécuté. La condition n’étant pas remplie, alors PHP ne rentrera pas dans le bloc et passera tout de suite à l’exécution de la suite du code, à savoir la fin du script dans le cas présenté.

### La condition “sinon” - ELSE

Les conditions “si” peuvent également comporter une partie “sinon”. Celle-ci se verra exécutée si la condition initiale décrite dans le bloc "if'' n'est pas remplie. Elle s’exprime grâce au mot-clé “else”, traduction littérale de “sinon” en anglais. 

Contrairement au “if”, il n’y a pas de condition à passer dans le “else” entre parenthèses, cependant il faut tout de même spécifier des accolades tout de suite après le mot clé afin d’y spécifier le code à exécuter si la condition initiale n’est pas remplie. Le “else” est optionnel, et il n’est nullement obligatoire de s’en servir.

``` php
# Déclaration d'une variable "$a", et attribution de la valeur "0"
$a = 0;

# Déclaration de la condition. Ici on teste que la valeur de "$a" soit
# strictement égale à "1".
if ($a == 1) {
	# Début du bloc à exécuter si la condition est vraie.
	echo ("vrai");
} else {
      # Bloc à exécuter si la condition n'est pas vraie.
      echo ("false");
}
```

Dans l’exemple ci-dessus, nous déclarons une variable ```$a``` qui prend pour valeur zéro. Le bloc “if” vérifie ici que la valeur de ```$a``` est égale à 1, or ce n’est pas le cas. Ainsi, c'est le bloc “else” qui sera exécuté et le code affichera “false” en conséquence.

Prenons un deuxième exemple : 

``` php
# Déclaration d'une variable "$a", et attribution de la valeur "0"
$a = 1;

# Déclaration de la condition. Ici on teste que la valeur de "$a" soit
# strictement égale à "1".
if ($a == 1) {
	# Début du bloc à exécuter si la condition est vraie.
	echo ("vrai");
} else {
    # Bloc à exécuter si la condition n'est pas vraie.
    echo ("false");
}
```

L’exemple ci-dessus est similaire au précédent, à ceci près que la valeur de “$a” est cette fois déclarée à “1”. Aussi lorsque PHP va exécuter le code, il va commencer par créer la variable “$a” et lui affecter la valeur “1”. 

PHP va ensuite vérifier la condition “if”, et donc trouver que cette condition est vraie. Ainsi il va afficher “vrai”, mais il n'exécutera pas le code dans le “else”. En effet, partant du principe que la condition exprimée dans le “si” est vraie, alors il n’aura aucun besoin d’exécuter le code dans le bloc “sinon”. De la sorte, il n’affichera pas “false”.

### ELSE IF

Il existe une alternative au “si” et au “sinon” : le “sinon si”. Celle-ci va permettre de tester d’autres conditions avant de passer au “else”, et va ainsi permettre de déterminer différentes actions à réaliser en fonction de plusieurs valeurs.

Le “sinon si” se traduit littéralement en anglais par “else if”. Aussi ce sont les deux mot-clés qu’il faut employer si l’on souhaite s’en servir. Tout comme pour le “if”, il conviendra ici de passer une condition à tester entre parenthèses. Tout comme pour le “else”, le “else if” n’est pas obligatoire.

``` php
# Déclaration d'une variable "$a", et attribution de la valeur "0"
$a = 0;

# Déclaration de la condition. Ici on teste que la valeur de "$a" soit
# strictement égale à "1".
if ($a == 1) {
	# Début du bloc à exécuter si la condition est vraie.
	echo ("a vaut 1");
} else if ($a == 0) {
    # Bloc à exécuter si $a vaut zéro.
    echo ("a vaut zéro");
} else {
    # Bloc à exécuter si la condition n'est pas vraie.
    echo ("a ne vaut ni un, ni zéro");
}
```

En exécutant le code ci-dessus, PHP commencera par créer la variable ```$a```, et lui affecter la valeur zéro. Il va ensuite arriver sur la condition “if” et vérifiera que la valeur de ```$a``` est bien égale à “1”. Ceci n’étant pas vrai, il n’exécutera pas le code présent dans le bloc “if”. PHP va donc continuer son exécution du code et arrivera à la condition “sinon si” où il vérifiera que ```$a``` est bien égale à zéro. Cette condition étant vraie, alors il exécutera le code à l’intérieur de ce bloc “else if” et affichera “a vaut zéro”.

Étant donné qu’un bloc de la condition aura été exécuté, alors PHP ne poursuivra pas son exécution des autres blocs de cette condition. Ainsi il n’exécutera pas le code présent dans le bloc “else”.

## Conclusion

L’utilisation des conditions est relativement simple en PHP. Les principales difficultés que vous rencontrerez seront de savoir quoi vérifier, et grâce à quel opérateur.

Il faut ici bien retenir deux points : 

- Une condition est constituée de plusieurs blocs. Lors de l’exécution du code, PHP traitera les blocs dans l’ordre d’écriture. Dès lors qu’un des blocs est exécuté, PHP considérera que la condition est terminée, et ne poursuivra donc pas l’exécution des blocs suivants
- Il est possible de faire autant de blocs que l’on souhaite. Le premier est obligatoirement un “if”. Vous pouvez ensuite mettre zéro ou plusieurs blocs “else if” en fonction de vos besoins. Vous pouvez enfin ajouter à la fin un bloc “else” qui sera exécuté si aucun des blocs précédents (dans la même condition) ne sont exécutés.

Par ailleurs, il est important de noter que dans une condition “if-else” (sans “else if”), il est souvent possible de ne pas utiliser le “else”. Voici un exemple :

``` php
$a = 0;
$b = 0;
if ( $a == 0 ) {
    $b = 4
} else {
    $b = 3;
}
```

L’exemple ci-dessus montre un algorithme simple : 

- ```$a``` et ```$b``` sont deux variables initialisées chacune avec la valeur zéro
- si ```$a``` est égale à zéro, alors on passe la valeur de ```$b``` à “4”
- sinon on passe la valeur de ```$b``` à 3.

Il est possible d’écrire cette même condition sans le “else”, juste en changeant d’approche :

``` php
$a = 0;
$b = 3;
if ( $a == 0 ) {
    $b = 4
}
```

L’idée est ici de définir la valeur de ```$b``` à 3 dès le début (ce qui était présent dans le bloc “else” de la condition du premier exemple. De la sorte, lorsque PHP va exécuter la condition, il ne changera la valeur de ```$b``` que si ```$a``` est égale à zéro. Dans l’autre cas de figure, alors il ne changera pas la valeur de ```$b``` puisque celui-ci aura déjà été déclaré avec la valeur qu’il aurait dû obtenir dans le bloc “else” de la condition précédente.