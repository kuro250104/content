Une constante est un conteneur qui permet de stocker une ou plusieurs informations. Elle est similaire aux variables dans le sens où n’importe quel type de donnée peut être stocké, et que ce stockage est temporaire puisque la constante disparaît à la fin de l’exécution du script.

La différence majeure entre une constante et une variable réside dans le fait que la première n’est pas modifiable une fois définie. C'est-à-dire qu’il est possible de se servir de sa valeur, de ce qu’elle contient, mais pas de modifier son contenu une fois défini.

Lors de l’apprentissage de la programmation, il n’est pas rare de se poser la question de l’intérêt des constantes, pourquoi donc utiliser autre chose qu’une variable ?

La réponse est souvent simple : il n’est pas obligatoire de s’en servir. Cependant, attention, même si l’utilisation des constantes reste optionnelle, elles permettent d’apporter de la sémantique et de la clarté dans le code. En effet, les valeurs des constantes n’étant pas modifiables en cours de script, l’utilisation de celles-ci survient généralement pour définir les différents paramètres des scripts et applications. En procédant de la sorte, il est possible d’un simple regard sur le code de déterminer si une variable est utilisée pour un algorithme précis, ou bien si une constante est utilisée de manière globale.

## Les constantes au sein du PHP

### Règles de nommage

Il existe quelques règles de nommage de vos constantes. Elles sont simples :

- Pas d’utilisation du symbole du dollar ```$``` - qui est réservé aux variables
- Pas de caractères spéciaux
- Tout doit être écrit en majuscule. Si plusieurs mots sont nécessaires pour nommer les constantes, il faut les séparer par le symbole “underscore” ```_```.

### Déclaration d’une constante

Il existe différentes façons de déclarer des constantes. La première méthode est d’utiliser “define” : 

```php
# déclaration d'une constante nommée "NOM", en lui affectant la valeur 
# "Microlead" :
define("NOM", "Microlead");
```

Une deuxième méthode est d’utiliser le mot-clé “const” juste avant de définir le nom de la constante. L’affectation de la valeur se fait alors de la même manière qu’une variable : 

```php
# déclaration d'une constante nommée "NOM", en lui affectant la valeur 
# "Microlead" :
const NOM = "Microlead";
```

### Affichage de la valeur d’une constante

Tout comme pour la déclaration, il existe différentes manières d’utiliser ou d’afficher la valeur d’une constante. La première est tout simplement d’utiliser le ```echo```, comme pour les variables, la deuxième est d’utiliser la fonction ```constant()``` : 

```php
# déclaration d'une constante nommée "NOM", en lui affectant la valeur 
# "Microlead" :
const NOM = "Microlead";

# Affichage de la valeur avec le "echo"
echo(NOM);
# affichera donc "Microlead"

# Affichage avec la fonction "constant()"
constant("NOM");
# affichera également "Microlead"
```

### Vérifier l’existence d’une constante

La fonction ```defined()``` de PHP permet de vérifier l’existence d’une constante par rapport à son nom. Voici un exemple :

```php
# déclaration d'une constante nommée "NOM", en lui affectant la valeur 
# "Microlead" :
const NOM = "Microlead";

# Vérification de la constante "NOM" :
defined("NOM");
# la ligne du dessus renverra "vrai"

# Vérification de la constante "MICROLEAD" :
defined("MICROLEAD");
# la ligne du dessus renverra "faux", car aucune constante "MICROLEAD" 
# n'a été déclarée.
```