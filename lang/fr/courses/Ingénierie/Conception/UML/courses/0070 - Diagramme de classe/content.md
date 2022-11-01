## Pré-requis

Les diagrammes de classes permettent de représenter des concepts de **programmation orienté objet**. Vous devez donc absolument connaître ces concepts génériques afin de comprendre l’ensemble des explications de ce document.

Par ailleurs, en UML, les “classes” sont des “objets” spécifiques. Ainsi, même si elle n’est pas obligatoire, la connaissance des **diagrammes d’objets** simplifiera grandement votre compréhension de cette micro formation.

## Informations génériques

- **Type** : Structurel
- **Périmètre** : Fonctionnel
- **Langage** : Tous les langages Objet

__Informations utiles__ : Les logiciels UML diffèrent souvent quant à la schématisation des éléments. Certains logiciels peuvent ainsi représenter un élément d’une manière qui n’est pas (ou plus) conforme à l’UML. Avant de vous lancer dans un projet, vérifiez donc que votre logiciel est toujours maintenu par son développeur et que les schémas sont conformes.

## Définition / Utilisation

### Généralités

Les diagrammes de classes font partie des fondamentaux de l’UML. Ce sont de loin les diagrammes les plus utilisés, mais également les plus méconnus. Ils ont pour but de décrire la structure d’un système d’un point de vue développement. Ils permettent donc entre autres de représenter des classes, des attributs, des méthodes, des relations, etc…

Comme bon nombre de diagrammes UML, ils peuvent être utilisés dans un but documentaire aussi bien que dans un but conceptuel. Lors du développement d’un système “from scratch” (en partant d’une feuille blanche, et sans framework), il est fortement recommandé de réaliser ce type de diagramme qui vous évitera de nombreuses erreurs.

Les utilisations de ce type de diagramme sont multiples. Ils permettent de modéliser l’organisation de données, d’offrir un aperçu général d’une structure d’application ou bien encore d’anticiper la totalité d’un code spécifique à réaliser lors de la conception d’un système.

### Représentation d’une classe

La représentation d’une classe se fait grâce à un rectangle décomposé en 3 parties. Chaque partie a sa propre signification, mais seule la première est obligatoire.

![Représentation d’une classe en UML](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image10.png)

#### Le nom

La première partie de la représentation identifie la classe décrite. Cette partie est elle-même décomposée en 5 parties ordonnées : 

1. le ```<<stéréotype>>``` : c’est un système permettant de spécifier des propriétés propres à un domaine particulier ou à un usage spécialisé. Par exemple, si la représentation schématique d’une classe correspond en réalité à une interface, alors il convient de commencer par le stéréotype ```<<interface>>```.
2. **la hiérarchie des packages** : Si vous décrivez une classe appartenant à un package (= *namespace*) spécifique, alors vous devez l’identifier avec l’ensemble de l’arborescence du package. Ainsi si la classe se trouve dans le package A, on indique ```PackageA::```, et si ce package A est lui-même contenu dans un package B, alors la syntaxe sera ```PackageB::PackageA::```. Remarquez qu’on ajoute le symbole ```::``` après chaque argument, y compris le dernier.
3. **le nom de la classe** : c’est la seule et unique partie de la déclaration du nom d’une classe qui est obligatoire.
L’UML étant un langage de modélisation à forte sensibilité sémantique, il conviendra de choisir avec soin le nom de vos classes, de manière à ce que celui-ci soit explicite sans être trop long.
Si vous avez renseigné des packages avant le nom de la classe, ce dernier devra figurer immédiatement après les derniers ```::```, sans espace.
N’oubliez pas les conventions d’écritures des classes : le nom ne comporte aucun espace, ni caractères spéciaux, uniquement des lettres. Chaque mot utilisé pour le définir commence par une majuscule, suivant la convention camelCase (PascalCase plus précisément, puisque la première lettre est également une majuscule). Par exemple : “**CeciEstLeNomDeMaSuperClasse**”.
4. ```{abstract}``` : S’il s’agit d’une classe abstraite, cette mention est à rajouter (accolades incluses) à la suite du nom.
5. Le dernier paramètre permet d’inclure des informations diverses sur la classe. Ce paramètre se présente sous la forme d’une liste de paires “clé : valeur”, chaque paire étant séparée des autres par une virgule, et l’ensemble étant placé entre accolades. On obtiendra donc la forme : ```{clé1 : valeur1, clé2 : valeur2}```. Cette partie permet souvent de spécifier un auteur, un état de conception, un état de réalisation, ou bien une affectation du travail à réaliser par un développeur.

Le nom complet d’une classe a donc la structure suivante : 

```<<stéréotype>> Package1::Package2::NomClasse {abstract} {clé : valeur, ...}```

![Représentation complète de la déclaration du nom](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image7.png)

#### Les attributs

La deuxième partie de la représentation d’une classe sert à décrire ses attributs. Chaque ligne au sein de cette section représente donc un attribut, et réciproquement, chaque attribut de la classe schématisée devra disposer d’une ligne pour le décrire.

Tout comme pour le nom de la classe, la déclaration d’un attribut se décompose en plusieurs parties. Elles sont au nombre de 7, et seules les deux premières sont obligatoires.

1. **la visibilité** : le premier caractère de la ligne renseignera la visibilité de l’attribut. Il en existe 6 types différents, représentés par les symboles ```+```, ```-```, ```#```, ```~```, ```/``` ou __souligné__. Leur signification est détaillée dans la partie 3.3 de ce cours.
2. **Le nom** : le deuxième élément représente le nom de l’attribut.
Encore une fois, rappelez-vous l’aspect sémantique de l’UML : le choix des noms est crucial et déterminant sur la compréhension de votre diagramme aussi bien que de votre code.
Attention également à respecter les conventions de nommage. Contrairement au nommage de la classe qui ne dépend pas du langage, vous devrez ici vous adapter en fonction de la technologie visée. Un nom d’attribut ne s’écrit pas de la même manière en Python qu’en PHP, prenez donc en considération le choix technologique si vous le connaissez afin de coller au mieux à ses conventions.
3. **le symbole de spécification** “dérivé” ou “statique” : Ce troisième élément apporte une information importante concernant l’attribut en question. Si le symbole est “:”, cela signifie que l’attribut est dit “statique”, c’est-à-dire qu’il est défini sans calcul. A contrario si le symbole est “/”, cela veut dire que l’attribut est “dérivé” - c’est à dire calculé.
4. **le type** : cette partie de la description d’un attribut permet de définir son type : une chaîne de caractère, un nombre, une date, un booléen etc…
5. **La multiplicité** : cet aspect de la description d’un attribut est souvent méconnu, mais est pourtant très pratique. Elle permet d’éviter la redondance d’informations lorsque vous souhaitez signifier que l’attribut décrit pourra être “dupliqué” un certain nombre de fois. Cette multiplicité se représente entre crochets, et permet de renseigner un nombre précis ou bien un intervalle.
Par exemple, imaginons un attribut “phone1” (pour le téléphone fixe), et un autre “phone2” (pour le téléphone portable). Si les deux attributs possèdent une description identique, alors plutôt que de les déclarer sur deux lignes, vous pouvez les déclarer sur une seule ligne grâce à la multiplicité ```[2]```. De même, si jamais vous souhaitez ajouter davantage d’attributs “phone”, alors vous pourriez représenter un intervalle ```[2..*]``` signifiant “minimum 2 - maximum infini”. Voici donc deux manières d’illustrer la multiplicité d’un attribut :

![Représentation de deux classes identiques, à gauche sans multiplicité sur l’attribut “phone” et à droite avec](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image23.png)

6. **la valeur par défaut** : cet élément vous permettra de renseigner une valeur par défaut à un attribut si nécessaire. Pour cela, vous devrez précéder celle-ci du symbole ```=```. Par exemple si la valeur par défaut doit être ```False```, alors vous devrez ajouter ```= False```.
7. **Les contraintes** : elles permettent d’apporter davantage d’informations. elles sont à mettre entre accolades, séparées par des virgules : ```{contrainte1, contrainte2, ...}```. Vous trouverez une liste de plusieurs contraintes au points 3.4 de ce cours.

Chaque ligne de description d’un attribut peut donc se représenter, en comprenant l’ensemble des éléments facultatifs, de la manière suivante : 

```visibilité nom symbole_spécification type [multiplicité] = valeur_initiale {contraintes}```

![Représentation complète de la déclaration d’un attribut](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image2.png)

#### les méthodes

La dernière partie de représentation d’une classe sert à identifier ses méthodes. Pour chaque méthode à décrire, une ligne sera créée.

Les lignes de description des méthodes sont également divisées en plusieurs parties, on en dénombre 6 : 

1. **la visibilité** : le premier caractère de la ligne renseignera la visibilité de la méthode. Il en existe 5 types différents pour les méthodes, représentés par les symboles ```+```, ```-```, ```#```, ```~``` ou __souligné__. Vous retrouverez le détail de ces informations dans la partie 3.3 de ce cours.
2. **le stéréotype d’opération** : il est représenté entre double chevrons ```<<stéréotype>>``` et renseigne des spécificités d’une méthode. Il sert souvent à indiquer que la méthode est le constructeur (```<<construct>>```) ou le destructeur (```<<destruct>>```) de la classe. Cependant vous pourrez ici exposer davantage d’information en fonction de votre stack technologique. Les mots clés utilisés pour ces stéréotypes sont en général ceux utilisés dans le langage de programmation choisi. On pourra citer par exemple les “méthodes magiques” pour du PHP ou les “méthodes spéciales” pour du Python.
3. **le nom** de la méthode est le deuxième élément de description. Souvenez vous ici aussi des bonnes pratiques du langage et de l’aspect sémantique.
4. **une liste de paramètres**, placée entre parenthèses. Celle-ci représentera l’ensemble des paramètres de la méthode concernée. Leur description sera divisée en 4 sous-parties : 
   1. La direction : quatre possibilités différentes ici : “*in*”, “*out*”, “*inout*”, “*return*”.
    “*in*” indique que les valeurs des paramètres sont transmises par l’appelant. C’est également la valeur considérée par défaut. Si l’information n’est pas précisée, on considérera donc qu’elle vaut “in”.
    “*out*” indique que les valeurs des paramètres sont transmises à l’appelant.
    “*inout*” indique que les valeurs des paramètres sont transmises par l’appelant, et que ces valeurs (éventuellement modifiées) sont ensuite transmises à l’appelant.
    “*return*” indique que les valeurs des paramètres sont transmises en tant que valeurs de retour à l’appelant.
    __Note 1__ : “l’appelant” est ici l’entité qui fait appel à la méthode. Cela peut être un objet, une variable, un évènement, ou n’importe quelle entité existante en UML.
    __Note 2__ : une seule direction peut être renseignée par paramètre.
    2. le **nom** du paramètre
    3. le **type de retour**, présenté sous la forme ```: type```
    4. une **valeur par défaut** présentée après le symbole ```=``` : ```= valeur-défaut```
5. **le type de retour** : il sera présenté sous la forme ```: type-retour```. Il représentera le type des données renvoyées par la méthode.
6. **Les contraintes** : elles permettent d’apporter davantage d’informations. elles sont à mettre entre accolades, séparées par des virgules : ```{contrainte1, contrainte2, ...}```. Vous trouverez une liste de plusieurs contraintes au points 3.4 de ce cours.

Sous sa forme totale, la représentation d’une méthode se renseigne donc de la manière suivante : 

```visibilité <<stéréotype>> nom (liste-paramètres) : type-retour {contraintes}```

où ```liste-paramètres``` prendra la forme suivante : 

```direction nom : type = valeur-défaut```

![Représentation complète de la déclaration d’une méthode](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image5.png)

## La visibilité ou les modificateurs d’accès

