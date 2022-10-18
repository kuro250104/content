## Qu’est-ce qu’une variable ?

Une *“variable”* est une sorte de conteneur qui permet de stocker une information. Elle peut stocker un nombre, un texte, une date, une heure, ou bien tous types d’informations existants en programmation. 

Les variables sont souvent amenées à évoluer dans le temps, au fur et à mesure de l’exécution du code par la machine. Ainsi, une variable peut changer de valeur autant de fois souhaité au cours du script, tout aussi bien qu’elle peut garder une seule et même valeur tout du long de l’exécution du programme.

Les variables ont cependant une durée de vie : elles sont automatiquement supprimées à la fin de l’exécution du script dans lequel elles sont utilisées.

## À quoi sert une variable ?

Les variables représentent à elles seules les bases de la programmation, et ce sont grâce à elles que vous allez pouvoir mettre en place votre logique au sein d’un script. La première utilisation qu’un développeur est amené à faire lors de son apprentissage concerne la manipulation de données.

Imaginons par exemple un programme demandant un nombre à un utilisateur et lui renvoyant ensuite la valeur du carré de ce nombre. Voici un exemple d’algorithme simple en 3 étapes qui pourrait être utilisé pour un tel script : 

1. demande de saisie d’un nombre à l’utilisateur
2. réalisation du calcul
3. affichage du résultat du calcul à l’utilisateur

Lors de l’étape (2), le calcul en lui-même est simple : il suffit de multiplier le nombre par lui-même. La difficulté ici réside dans le fait que lors de l’écriture du programme, le nombre saisi par l’utilisateur n’est pas connu. Ainsi, il n’est pas possible de prévoir un calcul à l’aide de nombres. Par exemple, nous ne pouvons pas faire “2*2” sans savoir si le nombre qu’aura choisi l’utilisateur est bien “2”. Idem, il n'est pas possible de prévoir des calculs pour tous les nombres existants.

C’est donc ce genre de problèmes et questionnements que les variables vont nous permettre de résoudre. Nous allons pouvoir déclarer une variable (que nous appellerons *“nombre”* pour l’exemple), et ainsi transformer les étapes de l’algorithme précédent de la sorte : 

1. demande de saisie d’un nombre à l’utilisateur et **stockage de ce nombre dans la variable “*nombre*”**
2. réalisation du calcul : “**nombre * nombre**”
3. affichage du résultat du calcul à l’utilisateur

De cette manière, et grâce à l’utilisation des variables, nous allons donc pouvoir commencer à mettre en place une logique, avec des données inconnues stockées dans des variables.

Les variables vont également nous permettre de faire passer certaines valeurs d’une page d’un site web à une autre. De la même façon que pour l’exemple de calcul ci-dessus, nous pourrons stocker des valeurs au sein de variables, puis les “envoyer” vers d’autres pages web, de telle sorte à faire transiter des informations d’une page à une autre. Nous pourrions illustrer ce fait par exemple avec la réalisation d’un formulaire de connexion. L’utilisateur renseigne son adresse mail ainsi que son mot de passe, et ceux-ci sont ensuite transmis à une autre page qui va se charger de faire la vérification des éléments.

Dans le cadre d’un développement web en PHP, les variables peuvent aussi vous permettre de dynamiser l’apparence de votre site internet. Vous pourrez par exemple créer une variable “*couleur*”, qui pourra changer selon certaines conditions que vous aurez définies, et indiquer à votre site web d’afficher telle ou telle partie de votre site selon la couleur définie dans votre variable.

## Les variables dans du code PHP

### Règles de nommage

Tout comme chaque langage de programmation, il existe de nombreuses normes, règles et conventions en PHP, et les variables en font pleinement  partie. Voici donc quelques règles de base :

- En PHP, la déclaration d’une variable doit toujours s’effectuer avec le symbole ```$``` qui précède le **nom** de la variable. Par exemple : ```$name```.
- Le premier caractère suivant le symbole du dollar ```$``` doit être obligatoirement **une lettre ou un underscore**. Par exemple : ```$_var``` ou ```$var```.
- Le nom de la variable ne doit pas contenir de caractères spéciaux à l’exception de tirets. Sont autorisés les tirets ```-```, les underscores ```_```, et les lettres et chiffres.
- Les noms des variables sont dits “sensibles à la casse”, c'est-à-dire qu’une variable ne dispose que d’un nom, et si un des caractères composants ce nom est en majuscule, alors il devra l’être également pour la réutilisation de cette variable. Notez par exemple que ```$variable``` et ```$variAble``` sont deux noms de variables distinctes, et par conséquent que l’utilisation de ceux-ci entraînera l’utilisation de 2 variables obligatoirement (et non une seule).
- Certains noms de variables sont réservés, par exemple les variables appelées “Superglobales” que nous apprendrons à utiliser plus tard.
- En PHP, le nommage des variables doit être effectué selon le principe du camelCase.

### Utilisation

#### Déclaration et stockage de variable

Comme vu précédemment, pour déclarer une variable, il faut commencer par le symbole ```$```, puis y accoler le nom souhaité. De la sorte, si l’on souhaite créer une variable qui s’appelle “variable”, et qui contient le mot “Bonjour”, alors il faudra faire de la sorte : 

``` php
$variable = "Bonjour";
```

Si on souhaite créer une variable “nombre”, et lui affecter la valeur “0” (zéro), alors il faudra faire : 

``` php
$nombre = 0;
```

#### Affichage de variable

Il existe deux différentes méthodes afin d’afficher une variable en PHP. En effet, ce dernier nous livre deux fonctions : ```echo()``` et ```print()```

Reprenons les mêmes exemples qu’au-dessus, si l’on souhaite créer une variable qui s’appelle “variable”, et qui contient le mot “Bonjour”, et ensuite afficher le contenu de cette variable, il sera possible de faire : 

``` php
# déclaration de la variable et affectation de la
# valeur "Bonjour"
$variable = "Bonjour"


# méthode 1
print($variable)

# méthode 2
echo($variable)
```