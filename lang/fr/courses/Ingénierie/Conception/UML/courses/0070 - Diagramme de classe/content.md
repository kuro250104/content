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

### La visibilité ou les modificateurs d’accès

Les modificateurs d’accès représentent ce qu’on appelle la “visibilité” au sein d’une classe en programmation orientée objet. Ils caractérisent les attributs et les méthodes d’une classe et sont à renseigner pour chacun des attributs, et chacune des méthodes décrites.

Le principe de visibilité nous permet de définir la manière d'accéder aux éléments décrits et de déterminer quelles entités vont pouvoir y accéder. Bien utilisée, la visibilité vous permettra non seulement de gagner en précision dans votre code, mais également de limiter les risques de mauvaise utilisation d’un attribut ou d’une méthode pouvant résulter en la création d’un bug applicatif.

On dénombre 5 différents modificateurs d’accès : “Public”, “Protected”, “private”, “package” et “dérivé”, détaillés ci-après. A part “dérivé”, tous sont applicables aux attributs comme aux méthodes d’une classe.

#### L’importance du NameSpace

En UML, un Namespace est un élément abstrait qui **contient** ou qui **est propriétaire** d’un ou plusieurs éléments nommés. On le compare souvent à un “conteneur”. La visibilité décrite en UML est basée sur cette notion de Namespace. Vous trouverez donc pour chaque modificateur d’accès ci-dessous 2 explications différentes : l’une correspondant au langage UML et l’autre correspondant à une “traduction” avec des termes génériques et concrets de programmation orientée objet.

#### Le modificateur d’accès “Public”

La visibilité *publique* est symbolisée par le caractère ```+```. UML définit cette visibilité comme accessible de tous les éléments qui disposent d’un accès au contenu du namespace propriétaire.

Cela signifie que l’élément décrit pourra être accessible de n’importe où dans votre programme, par n’importe quel objet ou élément de votre code qui pourra accéder à la classe en question. Son utilisation est donc recommandée uniquement lorsque l’élément concerné n’a qu’un faible impact en cas de modification de votre code.

#### Le modificateur d’accès “Protected”

La visibilité *protégée* est symbolisée par le caractère ```#```. l’UML définit ce type de visibilité par le fait d’être accessible aux éléments qui ont déjà des relations avec le Namespace qui en est propriétaire.

En d’autres termes, on considère qu’une propriété ou un attribut “protégé” au sein d’une classe sera visible par la classe ET ses classes enfants.

#### Le modificateur d’accès “private”

La visibilité *privée* est symbolisée par le caractère ```-```. Il est donc considéré que l’élément avec ce modificateur d’accès ne sera visible qu’au sein du Namespace courant. Autrement dit, chaque attribut ou méthode possédant une visibilité privée ne sera accessible que dans la classe où il est déclaré.

#### Le modificateur d’accès “package” (ou “paquetage”)

La visibilité de “*package*” est symbolisée par le caractère ```~```. Ce modificateur d’accès est particulier dans le sens où il ne peut être détenu que par des Namespace qui ne sont pas de type package (paquetage). La visibilité est traduite en UML par la visibilité pour tous les éléments contenus dans le paquetage dans lequel se trouve le Namespace propriétaire.

En clair, si votre élément de visibilité “*paquetage*” se trouve au sein d’un package, alors tous les autres éléments du package pourront accéder à celui-ci.

**Attention**, l’élément en question ne sera accessible QUE dans le package propriétaire. C’est-à-dire que si le package propriétaire est lui-même propriété d’un autre package (package “parent”), alors l’élément concerné ne sera pas pour autant visible depuis le package “parent” du fait qu’il se trouve dans le package “enfant”.

#### Récapitulatif

- l’accès à un élément “*privé*” est limité aux éléments de la même classe
- l’accès à un élément “*protected*” est limité à la classe et ses enfants
- l’accès à un élément “*package*” est limité aux éléments faisant partie du même package, mais pas à ses packages parents
- l’accès à un élément “*public*” n’est pas limité

#### Le modificateur d’accès “dérivé”

**Note** : ce modificateur d’accès n’existe plus dans l’UML 2.5, cependant il n’est pas rare de le retrouver dans des schémas provenant d’anciennes versions.

La visibilité d’un élément dérivé est représentée par le caractère “/”. Elle n’est valable QUE pour les attributs et ne concerne donc aucunement les méthodes d’une classe.Ce modificateur sert à symboliser le fait que l’attribut en question est **calculé** de manière programmatique. La valeur qu’il contiendra sera donc issue d’un calcul qui s’effectuera souvent dans le constructeur de la classe.

#### La représentation “statique”

La visibilité *statique* se représente en __soulignant__ le nom de l’attribut ou de la méthode concernée. Aussi même si ce n’est à proprement parler pas un modificateur d’accès, il est souvent présenté en même temps que la visibilité.

L’utilisation de cette représentation déterminera donc si l’attribut ou la méthode concerné sera dit de “*classe*” ou “*d’instance*”.

### les contraintes

Les *contraintes* sont des éléments génériques de l’UML, utilisables dans différents types de schémas, mais importants dans les diagrammes de classe. Elles sont la représentation d’une condition, d’une restriction ou bien d’une assertion.

Pour que des éléments décrits à l’aide d’une ou plusieurs contraintes soient supposés “valides”, il faudra assurer l’une des trois possibilités suivantes :

- Dans le cas d’une *condition*, celle-ci devra être entièrement satisfaite pour que l’élément contraint soit valide.
- Dans le cas d’une *restriction*, l’élément contraint sera valide si et seulement si il n’entre pas dans le cadre de la restriction définie.
- Dans le cadre d’une *assertion*, celle-ci devra être “vrai” afin que l’élément contraint soit considéré comme valide.

Les contraintes ne sont liées à aucun langage en particulier; ainsi, même si elles peuvent être représentées via OCL (Object Constraint Language - une autre nomenclature régie par l’OMG), elles sont adaptables en fonction des stacks technologiques utilisés.

Les contraintes peuvent être représentées de 3 manières différentes selon les besoins : 

- Si la contrainte ne concerne qu’un seul élément, alors elle sera rédigée entre accolades sur l’élément concerné.
- Si elle concerne 2 éléments, alors elle sera représentée sur une ligne en pointillés qui liera les 2 éléments.
- Si elle concerne un regroupement d’éléments, alors elle sera représentée grâce au symbole de commentaire, qui sera lui-même relié au groupe par une ligne en pointillés.

![symbole de commentaire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image16.png)

### Les interactions

#### Introduction

Les diagrammes de classes incluent la représentation des interactions entre les classes ou les instances de classe. On distingue les associations génériques, les associations spécifiques ainsi que la représentation de l’héritage. Chaque type d’association a sa propre signification et concerne généralement les instances de classe.

#### Généralités sur les associations

Les associations schématisent la connaissance d’instances de classe par d’autres instances de classe. Pour une instance donnée, elles nous indiquent donc quelles autres instances lui sont connues.

La représentation d’une association se fait à l’aide d’un trait simple, qui pourra être agrémenté de quelques symboles tels que des losanges vides ou pleins, ou par des flèches selon la signification que l’on souhaite lui donner. Chaque association permet donc de relier deux ou plusieurs classes. Dans le cadre d’une liaison entre deux classes, le trait partira de la première pour joindre la seconde. Si par contre on souhaite en lier plusieurs, on doit relier chaque classe à un losange, qui représentera le groupement de la liaison.

Chaque association peut disposer d’un nom : on l’appelle alors une **relation nommée**. Le sens de lecture peut également être indiqué par une pointe de flèche à gauche ou à droite de ce nom. 

La notion de multiplicité - aussi appelée “cardinalité” - est également présente sur chaque association, et permet de contraindre le nombre d’objets intervenant dans les instanciations des associations. Chaque multiplicité est à représenter de chaque côté de l’association. 

Enfin, les associations peuvent également être précisées et explicitées par un rôle, qui sera décrit en toutes lettres (généralement un seul mot).


#### Association unidirectionnelle

Les associations unidirectionnelles sont des associations utilisées lorsque l’instance d’une classe doit avoir connaissance des instances d’une autre classe, mais sans réciproque. Par exemple, une telle association entre une classe A vers une classe B informera que les instances de B connaissent une ou plusieurs instances de A, mais que les instances de A n’auront aucune connaissance des instances de B.

Ces associations ont trois représentations possibles : 

- **un trait avec une croix d’un côté**. La croix renseigne sur le fait que la classe opposée ne contiendra aucune instance de la classe juxtaposée.

![symbole de représentation d’une association unidirectionnelle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image31.png)

- **un trait avec une flèche d’un côté**. La pointe de la flèche désigne la classe dont les instances seront stockées par l’autre classe.

![symbole de représentation d’une association unidirectionnelle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image27.png)

- **un trait avec une pointe de flèche d’un côté et une croix de l’autre**. La pointe de la flèche désigne la classe dont les instances seront stockées par l’autre classe. La croix renseigne sur le fait que la classe opposée ne contiendra aucune instance de la classe juxtaposée.

![symbole de représentation d’une association unidirectionnelle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image17.png)

Les associations unidirectionnelles peuvent également être nommées, disposer de multiplicités et être agrémentées d’un rôle.

#### Association bidirectionnelle

Ce sont les associations “standard” utilisées dans un diagramme de classe. Elles représentent une connaissance réciproque des instances des deux classes liées. Elles sont représentées par un simple trait.

Les associations bidirectionnelles peuvent également être nommées, disposer de multiplicités et être agrémenté d’un rôle.

#### La classe d’association

Les classes d’association peuvent être utilisées lorsque les multiplicités sont de type “*..*”. Si un tel cas de figure entraîne le besoin de spécifier des propriétés pour l’association, c’est qu’une classe dite “d’association” doit être créée. Ainsi l’ensemble des propriétés naissantes de la liaison des classes devra y figurer.

Deux étapes sont nécessaires afin de représenter une classe d’association : 

- En premier lieu, une association avec sa multiplicité doit être réalisée entre les classes concernées.
- Puis la classe d’association devra être schématisée, et liée au trait symbolisant l’association de l’étape 1 à l’aide d’un trait en pointillés.

Les classes d’associations ne sont souvent décrites qu’à l’aide d’attributs, mais il est également possible d’y inclure des méthodes.

#### Représentation des multiplicités sur une association

Les multiplicités sont représentées de chaque côté du trait symbolisant l’association. Le sens de l’écriture, et donc de la lecture, est à l’opposé de la classe concernée. C’est-à-dire qu’en cas de liaison entre une classe “A” et une classe “B”, les multiplicités propres à la classe “A” seront indiquées du côté de la classe “B”, tandis que celles propres à la classe “B” seront inscrites du côté de la classe “A”.

Ainsi :

- ```1``` : signifie que l’instance de la classe disposant de la multiplicité n’aura connaissance ou accès qu’à un, et un seul, objet de la classe associée.
- ```1..2``` : signifie que l’instance de la classe disposant de la multiplicité n’aura connaissance ou accès qu’à un ou deux, objet(s) de la classe associée.
- ```0..*``` : signifie que l’instance de la classe disposant de la multiplicité pourra avoir connaissance ou accès à aucun ou autant d’objets que souhaité de la classe associée.
- ```*``` : La notation d’étoile seule a la même signification que l’écriture ```0..*```. C’est à dire qu’une instance de classe pourra disposer de zéro, une, deux…, ou une infinité d’instance(s) d’une autre classe.
- ```1..1``` : Est un équivalent à la notation ```1```, c’est à dire que l’association ne concerne qu’une et une seule instance.

#### Composition

La **composition** est une association spécifique dite “*à forte dépendance*”. On distingue la classe **composite** de la classe **composante**. La première étant obligatoirement composée de une ou plusieurs instances de la classe composite. La dépendance est dite “forte” car l’instanciation d’une classe composite ne pourra pas se faire sans la création de sa ou ses classe(s) composantes. Il en va de même pour la destruction : la destruction d’une instance de la classe composite entraînera obligatoirement la destruction des instances des classes composantes. On simplifie souvent cette relation par la phrase “l’un ne peut pas vivre sans l’autre”. A titre d’exemple, un appartement ne peut exister indépendamment de l’immeuble. Si on détruit l’immeuble, alors l’appartement l’est aussi.

L’association se représente par un simple trait, agrémenté d’un losange “plein” (souvent noir) du côté du ou des composant(s).

De même que pour l’ensemble des associations, les rôles et les multiplicités peuvent être spécifiées sur une telle liaison. Si cette dernière n’est pas précisée, on considèrera cependant qu’elle est égale à ```1``` ou ```1..1```. Il faut également noter qu’un composant ne peut appartenir qu’à un et un seul composite.

En d’autres termes, un composite est un regroupement de composants. La relation de composition est représentative d’une **obligation** d’appartenance.

#### Agrégation

L’**association** est également une association spécifique. A l’inverse de la composition, elle est dite “à faible dépendance”. On distingue **l’agrégat** de **l’agrégé**. Le ou les agrégés sont contenus dans l’agrégat. La dépendance est dite “faible” car l’instanciation d’un agrégat ne sera pas conditionnée à l’instanciation d’un ou plusieurs agrégés. Il en va de même pour la destruction : la destruction d’une instance de la classe “agrégat” n'entraînera aucune obligation de destruction des instances des classes agrégés. Par exemple, si des salariés d’une entreprise partent pour une quelconque raison, l’entreprise n’est pas obligatoirement détruite.

L’association se représente par un simple trait, agrémenté d’un losange “vide” (souvent blanc) du côté du ou des agrégés.

De même que pour l’ensemble des associations, les rôles et les multiplicités peuvent être spécifiés sur une telle liaison. Si cette dernière n’est pas précisée, on considère qu’elle est égale à ```1``` ou ```1..1```.

En d’autres termes, un agrégat est un simple regroupement d’agrégés. La relation d’agrégation est représentative d’une **possibilité** d’appartenance.

#### Composition ou agrégation ?

Il est souvent difficile de déterminer s’il convient d’utiliser une composition ou une agrégation. C’est un problème récurrent des diagrammes de classes, mais il peut en général être résolu très simplement. La notion d’appartenance étant au cœur du problème, la manière la plus simple de le résoudre est de se demander si cette appartenance est possible (= éventuelle), ou bien si elle est nécessaire (= obligatoire). Si la relation est obligatoire, alors il conviendra d’utiliser la composition. Si elle est éventuelle, alors il faudra se servir de l’agrégation.

Il faut également garder en tête que la représentation de l’une ou l’autre de ces associations est liée à l’idée que l’on se fait de la situation. L’option que vous aurez choisie, si elle n’est pas argumentée, pourra presque toujours être contestée ! Dès lors, il est primordial de prévoir un argumentaire qui justifie votre choix. Il peut être verbal, lors d’une présentation, écrit dans un document, ou bien tout simplement notifié grâce au système de commentaires fourni par l’UML directement dans vos diagrammes.

Illustrons la divergence de point de vue pouvant se présenter à vous. Imaginez une classe “Voiture” ainsi qu’une classe “Moteur”. Lors de l’association de ces deux classes, deux possibilités : composition ou agrégation. Les deux sont à la fois fausses, et à la fois correctes :

- Si l’on se place du point de vue d’un gérant d’une casse, sans moteur, la voiture est encore une voiture, car il reste d’autres pièces qu’il peut revendre. Ainsi la relation appropriée serait une agrégation du fait de l’absence d’obligation d’appartenance.
- Si l’on se place du point de vue d’un concessionnaire, sans moteur, la voiture n’est plus une voiture : c’est juste un tas de ferraille qui ne roule pas, et qu’il ne pourra pas revendre. Ainsi pour que la voiture reste une voiture à ses yeux, il est obligatoire que celle-ci dispose d’un moteur. La relation à utiliser dans ce cas de figure est donc la composition.

Cet exemple illustre parfaitement la nécessité de justifier une relation de composition ou d’agrégation. Selon les différents points de vue, le choix peut s’avérer bon ou mauvais : il ne tient qu’à vous d’en prouver la pertinence.

#### Héritage

La dernière interaction possible entre une ou plusieurs classes est la schématisation de l’héritage. Celle-ci est conforme aux concepts standards de POO, aussi vous devez être parfaitement à l’aise avec afin de bien comprendre cette partie.

La symbolisation de cette interaction se fait grâce à un trait, reliant les classes “mère” et “fille”, avec une flèche “vide” (blanche) du côté de la classe parente. Il faut noter également la possibilité de représenter de l’héritage multiple, que vous pourrez utiliser ou non en fonction de votre stack technologique.

## Formes et symboles

| Symboles | Signification |
| ![Représentation d’une classe](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image14.png) | Représentation d’une classe avec son nom, ses attributs et ses méthodes |
| ![Représentation d’association unidirectionnelle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image24.png) | Représentation d’association unidirectionnelle - la classe côté flèche partage ses instances avec celle opposée, tandis que la classe côté non fléché ne les partage pas |
| ![Représentation d’association bidirectionnelle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image3.png) | Représentation d’association bidirectionnelle |
| ![Représentation d’une composition](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image20.png) | Représentation d’une composition - le losange se situe côté de la classe composite |
| ![Représentation d’une agrégation](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image25.png) | Représentation d’une agrégation - le losange se situe côté de la classe agrégat |
| ![Symbole de commentaire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image16.png) | Symbole de commentaire |

## Exemples

### Représentation des noms de classe

Représentation d’une classe nommée “ClasseA” :

![Représentation d’une classe nommée “ClasseA”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image29.png)

Représentation d’une classe nommée “ClasseA”, contenue dans un package nommé “PackageA” :

![Représentation d’une classe nommée “ClasseA”, contenue dans un package nommé “PackageA”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image29.png)

Représentation d’une classe nommée “ClasseA”, contenue dans un package nommé “PackageB”, lui-même contenu dans un package nommé “PackageA” :

![Représentation d’une classe nommée “ClasseA”, contenue dans un package nommé “PackageB”, lui-même contenu dans un package nommé “PackageA”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image28.png)

Représentation d’une interface nommée “InterfaceA” :

![Représentation d’une interface nommée “InterfaceA”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image15.png)

Représentation d’une classe abstraite nommée “ClasseA” : 

![Représentation d’une classe abstraite nommée “ClasseA”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image9.png)

Représentation d’une classe nommée “ClasseA”, ayant pour auteur “Jean” : 

![Représentation d’une classe nommée “ClasseA”, ayant pour auteur “Jean”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image4.png)

### Représentation des attributs

![Représentation des attributs d’une classe “User”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image26.png)

Le schéma ci-dessus est une représentation d’une classe nommée “User”. Celle-ci contient 7 attributs :

- ```+ id : integer``` => défini un attribut de visibilité publique, qui pourra donc être utilisé par l’ensemble des autres éléments du programme qui aura connaissance de la classe User. Son nom est “id”, il est “statique” car non calculé et de type Integer. Cet attribut présentera vraisemblablement un identifiant permettant de distinguer les différents objets.
- ```+ name : String``` => défini un attribut public portant le nom “name”, “statique” car non calculé, et de type String. Le nom de cet attribut  nous laisse penser qu’il contiendra le nom de l’utilisateur.
- ```+ age / Integer {id “birthDate” has value}``` => définit un attribut de visibilité publique. Il est dérivé : c'est-à-dire que sa valeur est calculée à partir d’autres informations. Il est de type Integer et dispose d’une contrainte : ```{id “birthDate” has value}```. Celle-ci stipule que la valeur ne pourra être définie que si le champ “birthDate” est bien renseigné. On peut ici imaginer que l’attribut représente l’âge de l’utilisateur qui sera calculé à partir de sa date de naissance.
- ```# phone : String [2]``` => définit 2 attributs qui seront nommés “phone1” et “phone2”. Ils ont une visibilité privée, ce qui signifie que seule la classe “User” et les classes qui pourraient hériter directement de “User” pourront y accéder. Ces deux attributs possèdent les mêmes caractéristiques : ils ne sont pas dérivés et sont de type String.
On déduit ici la possibilité de deux numéros de téléphone, potentiellement un fixe et un mobile, ou bien deux mobiles.
- ```- birthDate : Date``` => définit un attribut de visibilité privée. Aucune autre classe que “User” ne pourra donc accéder à cette information.  Il n’est pas dérivé et est de type ```Date```. Cet attribut représente vraisemblablement la date de naissance de l’utilisateur. C’est de cette date que se servira la classe pour déterminer l’âge.
- ```- totalAmountOrdered : Float = 0``` => définit un attribut de visibilité privée. Il n’est pas dérivé et est de type “Float”. Sa valeur par défaut est “0”, c’est à dire que lors de l’instanciation d’un objet à partir de la classe, sa valeur sera zéro. Le nommage de cet attribut laisse entendre qu’il contiendra le montant total de commande effectué par l’utilisateur.
- ```- legalAge / Boolean {True if “age” > 18 else FALSE}``` => définit un attribut de visibilité privée. Il est dérivé (donc calculé) et est de type booléen. La contrainte exprimée nous informe d’une condition pour déterminer sa valeur. On comprendra donc ici que la valeur calculée sera fonction de la condition. Le nom de l’attribut nous permet de déduire qu’il renseignera quant à la majorité de l’utilisateur. Étant dérivé, on déduira ici que la classe se servira de la date de naissance ou bien de l’âge pour déterminer sa valeur.

### Représentation des méthodes

![Représentation des méthodes d’une classe “User”](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image21.png)

Le schéma ci-dessus reprend la classe “User” donnée comme exemple au point 6.2 en y intégrant différentes méthodes : 

- ```+ setBirthDate() : Boolean``` => Méthode de visibilité publique portant le nom “setBirthDate”. Elle aura un retour de type Booléen. Le nom rappelle les “setters” (mutateurs) permettant de modifier des attributs privés d’une classe. On comprendra ici que si la modification a bien eu lieu, alors la méthode renverra “True”, sinon elle renverra “False”.
- ```+ getBirthDate() : Date``` => Méthode de visibilité publique portant le nom “getBirthDate()”. Elle a un retour de type Date. Le nom rappelle ici les “getters” (accesseurs) permettant d’accéder aux attributs privés d’une classe.
- ```+ getTotalAmountOrdered() : Float``` => Méthode de visibilité publique portant le nom de “getTotalAmountOrdered”. Elle a un retour de type Float et renverra donc un nombre à virgule. On imagine ici également un “setter” permettant d’accéder à l’attribut privé “totalAmountOrdered”.
- ```+ addOrderAmount() : Float``` =>  Méthode de visibilité publique portant le nom “addOrderAmount” et renvoyant un résultat de type Float. Le nom reste explicite quant à son but d’ajouter des valeurs à l’attribut “totalAmountOrdered”, cependant le type de retour laisse perplexe quant à la valeur retournée. On ne peut déterminer s’il s’agira de la nouvelle valeur de l’attribut concerné ou bien s’il s’agit de la valeur ajoutée. Dans le cadre d’une documentation écrite, il serait donc ici pertinent de détailler le point de vue adopté parmi les différentes possibilités existantes.
- ```+ calculateAge() : Integer``` => Méthode de visibilité publique nommée “calculateAge” et retournant un nombre entier (Integer). Si le nom est ici aussi explicite, on comprendra que cette méthode se sert de l’attribut privé “birthDate” afin de déterminer l’âge de l’utilisateur. La sémantique posée via ce schéma suggère donc l’impossibilité de connaître la date de naissance d’un utilisateur par les autres classes, mais la possibilité de connaître l’âge. Au-delà du développement, cela peut être représentatif d’un souhait de garder certaines informations confidentielles en amont. Si tel est le cas, alors cette schématisation est en parfaite corrélation avec la volontée initiale.
- ```+ setIsLegalAge() : Void``` => Méthode de visibilité publique nommée “isLegalAge” ne retournant rien (ou plutôt un résultat vide - *Void*). Son nom nous indique qu’elle permettra d’identifier les personnes majeures ou mineures. Le type de retour (vide) nous indique quant à lui que l’information ne sera pas renvoyée, on en déduira donc qu’elle sera stockée dans l’attribut “legalAge”.
- ```+ <<constructor>> __construct(name, phone1, phone2, birthDate) : Void``` => Méthode publique nommée ```__construct```. Cette méthode possède un stéréotype : ```<<constructor>>```, ce qui nous indique qu’il s’agit du constructeur de la classe. Le nommage avec le double suivi du mot “construct” est représentatif du langage PHP, il est donc vraisemblable que cette modélisation a été effectuée à cette destination. Quatre paramètres sont passés sans préciser la direction, on les considère donc en tant que “in”, c’est-à-dire qu’ils sont passés par l’entité qui appelle la méthode.
  - **name** => servira à définir l’attribut “name”.
  - **phone1** et **phone2** => serviront à définir les attributs “phone”
  - **birthDate** => servira à définir la date de naissance de l’utilisateur.
  - Le retour “*Void*” quant à lui nous informe qu’il n’y aura pas de retour (il sera vide). Ce qui est normal et très courant s’agissant du constructeur de la classe.

### Représentation des relations

#### Unidirectionnelle

Schématisation d’une association unidirectionnelle (1) :

![Schématisation d’une association unidirectionnelle (1)](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image6.png)

Schématisation d’une association unidirectionnelle (2) :

![Schématisation d’une association unidirectionnelle (2)](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image32.png)

Les deux schématisations ci-dessus représentent une association unidirectionnelle entre la classe “ClasseA” et la classe “ClasseB”.

Dans le schéma (1), l’association établit que la “ClasseA” pourra stocker des instances de “ClasseB”, mais que “ClasseB” n’aura aucune connaissance de “classeA”.

Le schéma (2) a exactement la même signification, il s’agit juste d’une autre possibilité de schématisation.

#### Bidirectionnelle

Schématisation d’une association bidirectionnelle :

![Schématisation d’une association bidirectionnelle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image11.png)

La schématisation ci-dessus représente une association bidirectionnelle entre “ClasseA” et “ClasseB”. Cela signifie que les instances de la classe “ClasseB” possèderont des instances de la classe “ClasseA” et vice-versa.

L’implémentation objet d’une association bidirectionnelle pourrait également être schématisée de la sorte : 

![Schématisation d’une implémentation d’une association bidirectionnelle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image19.png)

Ainsi une association bidirectionnelle pourrait être représentée sans utiliser de liaison. Ici “ClasseA” dispose d’un attribut de type “ClasseB” et “ClasseB” dispose d’un attribut de type “ClasseA”. Nous sommes bien dans le cadre d’une association bidirectionnelle.

Attention, même s’il est possible de représenter ces associations sans utiliser de liaison, il est fortement déconseillé de faire de la sorte. En effet, il est bien plus simple d’identifier des associations lorsque celles-ci sont représentées à l’aide de liaisons.

#### agrégation

![Schématisation d’une agrégation](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image8.png)

Dans le schéma ci-dessus, la classe “*Voiture*” est **l’agrégat** tandis que la classe “*Roue*” représente **l’agrégé**. Cette représentation induit le principe que la classe “Voiture” aura une dépendance faible avec la classe “Roue”, c’est-à-dire que la classe “Voiture” n’aura pas obligatoirement besoin de connaître ou de contenir une ou plusieurs instances de la classe “Roue”.

Cette illustration démontre parfaitement l’importance de la sémantique. Pour la majorité des gens elle serait fausse car une voiture sans roue est inutile puisqu’elle ne roule pas. Par contre, si on se positionne du point de vue d’un gérant d’une casse par exemple, alors une voiture, même sans roue, a de la valeur puisqu’on peut considérer que tout le reste du véhicule pourra être désossé puis revendu pour pièces.

Attention, dans le cadre d’une relation de composition, il est très souvent nécessaire d’apporter une courte explication précisant de quel point de vue l’on doit se situer lors de la lecture. Vous pouvez le faire soit de manière textuelle dans un document à la suite de votre schéma, soit utiliser l’UML qui vous propose un système de “note” : cette dernière n’ayant aucune valeur sémantique, elle vous permettra d’éclaircir certains points si nécessaire.

#### Composition

![Schématisation d’une composition](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image22.png)

Dans le schéma ci-dessus, la classe “Voiture” est le composite tandis que la classe “Roue” représente un composant. Cette représentation induit le principe que la classe “Voiture” aura une dépendance forte avec la classe “Roue”, c’est-à-dire que si une instance de “Voiture” est créée ou détruite, alors la ou les instance(s) de “Roue” qui y sont liées seront également soit créées soit détruites.

A contrario de l’agrégation, la sémantique de la composition induit qu’aucune Voiture ne peut exister sans Roue. Du point de vue d’un utilisateur de véhicule, cela semble correct, cependant du point de vue d’un ferrailleur l’un peut tout à fait exister sans l’autre. De la même manière que pour les agrégations, il est vivement recommandé soit de joindre un bref texte à votre schéma dans un document rédigé à part, soit d’intégrer une note informative comme le permet l’UML directement au sein du diagramme.

#### Relations nommées

![Schématisation d’une relations nommée](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image13.png)

Deux classes sont reliées dans le schéma ci-dessus : “Bibliotheque” et “Livre”. La relation est ici nommée “contient” et la flèche sur le côté symbolise le sens de lecture. On doit donc dire “La classe Bibliotheque **contient** un ou plusieurs Livre”.

Attention, à noter ici qu’il n’y a aucune multiplicité de représentée, il ne convient donc pas de s’attarder sur le nombre de livres dans la bibliothèque, mais bien sur le terme “**contient**”.

#### Multiplicité

![Schématisation de multiplicités dans un diagramme de classe](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image12.png)

Le diagramme de classe ci-dessus représente 3 différentes classes : « Journaliste », « Article » et « Sujet ». Les relations entre les classes disposent toutes de multiplicités. Dans l’ordre, de gauche à droite : 

- La multiplicité « 1 » à droite de la classe « Journaliste » concerne la classe opposée de la relation, soit « Article ». Une lecture possible est « Un Article est obligatoirement réalisé par un et un seul Journaliste ». Cette relation induit donc qu’un article ne pourra pas être lié à plusieurs journalistes, et donc que si un article est écrit par plusieurs personnes, une seule sera associée à l’article.
- La multiplicité « 1..n » à gauche de la classe « Article » concerne la classe opposée de la relation, soit « Journaliste ». Une lecture possible est « Un journaliste possède obligatoirement au moins un article et peut en posséder autant que souhaité ». La subtilité ici est qu’on ne considère sémantiquement une personne comme journaliste qu’à partir du moment où elle a déjà écrit au moins 1 article.
- La multiplicité « 0..n » à droite de la classe « Article » concerne la classe opposée de la relation,soit « Sujet ». Une lecture possible est « Un sujet peut concerner autant d’article que souhaité ou aucun ». Si dans la sémantique cela ne semble pas correct car en pratique un article a forcément un sujet, on peut imaginer qu’on souhaite aussi avoir la possibilité de créer un article sans sujet, par exemple pour réserver son emplacement dans un prochain numéro de journal. Cette multiplicité laisse penser qu’autant de sujets que souhaités peuvent être créés, sans pour autant qu’un ou plusieurs articles y soient liés.
- La multiplicité « 1 » a droite de la classe « Sujet » concerne la classe opposée de la relation, soit « Article ». Une lecture possible est « Un article concerne obligatoirement un et un seul sujet ». La multiplicité nous indique ici qu’un article doit impérativement concerner un sujet, mais ne peut pas en concerner plusieurs.

#### rôle

![Schématisation de rôles au sein d’une association](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image18.png)

Dans le diagramme de classe ci-dessus, nous distinguons deux classes : “Personne” et “Entreprise”. Ces classes sont associées par une relation bidirectionnelle qui spécifie deux rôles. Cette information supplémentaire permet deux choses :

1. Faciliter la compréhension de la relation. Le nom du rôle permet ici de comprendre la relation entre Personne et Entreprise : la Personne est considérée comme un employé alors que l’Entreprise est considéré comme l’employeur. Sans cette information, il est impossible de définir si la Personne représente un client, un employé ou encore un prestataire de service pour l’entreprise. L’utilisation du rôle peut donc être déterminante dans la compréhension du diagramme.
2. La dénomination choisie de chaque rôle permet en général d’identifier le nom des attributs lors de l’implémentation de l’association. Ainsi, comme le montre le schéma ci-dessous, la classe Personne disposera d’un attribut nommé “employeur” de type “Entreprise”, et la classe Entreprise disposera d’un attribut nommé “employé” de type “Personne”.


![Schématisation de l’implémentation de rôles au sein d’une association](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0070%20-%20Diagramme%20de%20classe/images/image30.png)