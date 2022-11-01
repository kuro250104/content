## Informations génériques

- **Type** : Diagramme Structurel
- **Périmètre** : Fonctionnel
- **Langages** : Tous

## Définition / Utilisation

Le diagramme de packages est un diagramme qui permet de représenter un **regroupement** de différents éléments. Il est généralement utilisé en lien avec les diagrammes de classe (par exemple pour organiser les classes par fonctionnalités) et les diagrammes de cas d’utilisation (par exemple pour trier ceux-ci par champ d’action). Il peut cependant être utilisé avec n’importe quel élément répertorié en UML.

Les diagrammes de packages peuvent également s’imbriquer entre eux (un package peut contenir un autre package, et ainsi de suite…). Ces diagrammes incluent trois types de relation : 

- **Import** : Permet de mettre en évidence l’import de tous les éléments publics d’un package depuis un autre. Les éléments ainsi importés pourront donc être retransmis aux autres packages par la suite, étant alors considérés comme “publics” également dans le package d’import.
- **Access** : Symbolise l’accès aux éléments publics d’un package de la part d’un autre. L’accès aux éléments diffère de l’import dans le sens où les éléments accessibles ne pourront pas être retransmis par la suite à d’autres packages, puisqu’ils seront considérés “privés” lors de l’accès.
- **Merge** : Symbolise la fusion des éléments de deux packages différents.

## Formes et symboles

| Symboles | Signification |
| --- | --- |
| ![Symbole du package](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image11.png) | Symbole du package |
| ![Symbole d’appartenance à un package](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image1.png) | Symbole d’appartenance à un package. Le rond est positionné sur le package “conteneur”, tandis que la flèche pointe vers l’élément qui lui appartient. |
| ![Symbole d’import](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image2.png) | Symbole d’import. La pointe de la flèche désigne le package dont les éléments seront importés. |
| ![Symbole d’accès](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image8.png) | Symbole d’accès. La pointe de la flèche désigne le package contenant les éléments rendus accessibles. |
| ![Symbole de fusion](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image3.png) | Symbole de fusion. La pointe de la flèche désigne le package dont le contenu sera fusionné. |

## Astuces

Lors de la création d’un diagramme de packages, il peut s’avérer difficile d’identifier les différents packages à mettre en place au sein d’un projet. Il n’existe aucune règle particulière limitant le nombre de ceux-ci, il peut donc également devenir compliqué de distinguer le niveau de découpage nécessaire à la réalisation de votre projet. Devez-vous créer davantage de packages ? Devez-vous au contraire faire un regroupement de ceux-ci ?

Il n’y a pas de “bonne” réponse à ces questions. Tout dépendra de votre projet, du temps dont vous disposez pour le réaliser, des technologies utilisées, et bien d’autres facteurs seront à prendre en considération.

Il reste néanmoins une méthode qui permet de découper de manière propre vos packages, elle consiste tout simplement à dresser une liste **exhaustive** des fonctionnalités concernées par votre projet. Faites bien attention lors de cette étape à la sémantique des mots que vous utilisez, celle-ci est cruciale et déterminera la complexité de découpage de votre application. Une fois cette liste réalisée, commencez à identifier des points communs entre chaque fonctionnalité. Une méthode simple pour ce découpage consiste simplement à regrouper chaque fonctionnalité grâce à un système de couleur.

Chacun des regroupements de fonctionnalités ainsi obtenus représentera ainsi vos packages. Il ne vous restera plus qu’à identifier une sémantique correcte pour chaque groupe, ce qui vous donnera le nom de votre package.

## Exemples

### Exemple de représentation de deux packages au sein d’un système

![représentation de deux packages au sein d’un système](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image6.png)

Dans cet exemple, deux packages sont créés et représentés dans un système. Les packages sont identifiables par leurs noms :  “package 1” et “package 2”.

### Exemple de modélisation de l’import entre packages

![représentation de l’import entre packages au sein d’un système](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image10.png)

Dans cet exemple, le “package 2” importe l’ensemble des éléments publics depuis le “package 3”. Ces éléments importés sont donc assimilés comme “appartenant” aussi au “package 2” de manière publique. Le “package 1” important l’ensemble des éléments publics du “package 2”, il disposera donc des éléments publics du “package 3” par extension.

### Exemple de modélisation de l’accessibilité entre packages

![représentation de l’accessibilité entre packages au sein d’un système](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image5.png)

Dans cet exemple, le “package 2” a accès au “package 3”. Cela signifie qu’il obtiendra un accès sous la forme privée de tous les éléments publics du “package 3”.
Le “package 1” à lui accès au “package 2”, il disposera donc aussi de tous les éléments publics du “package 2”.

Cependant, contrairement au cas de l’import, les éléments publics du “package 3” ne sont pas accessibles dans le “package 1” puisqu’ils sont intégrés au “package 2” sous forme privée.

### Exemple de modélisation de fusion de package

![représentation de fusion de package au sein d’un système](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image9.png)

Dans cet exemple, le package 1 et le package 2 sont “mergés”. C'est-à-dire que l’on va créer une fusion de l’ensemble du contenu des deux packages. Ici, le résultat de la fusion sera le “package 2”. L’ensemble des éléments du “package 1” seront donc intégrés au “package 2”.

### Exemple de représentation d’appartenance entre packages

![représentation d’appartenance entre packages au sein d’un système](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image12.png)

Dans cet exemple, le “package 2” et le “package 3” sont considérés comme étant inclus DANS le “package 1”. Une autre représentation est possible sans les flèches d’appartenance : 

![représentation d’appartenance entre packages au sein d’un système](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image4.png)

### Exemple d’accessibilité et de fusion entre différents packages

![représentation d’accessibilité et de fusion entre différents packages au sein d’un système](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0060%20-%20Diagramme%20de%20package/images/image7.png)

Dans cet exemple, nous considérons 5 packages différents, numérotés de 1 à 5. __Cet exemple comporte volontairement des erreurs dont vous trouverez le détail et les explications plus bas__. Voici ce que l’on peut déduire d’un diagramme tel que celui-ci :

Le package 1 importe le package 2. Cela signifie qu’il intègre l’ensemble de ses éléments publics et en disposera de manière publique également.

Le package 2 a accès à l’ensemble des éléments publics du package 3. Ainsi il en dispose de manière privée.

Le package 4 dispose de 2 relations : 

- il importe le contenu public du package 3, et l’a donc à disposition en son sein de manière publique.
- il accède aux éléments publics du package 2, qu’il a donc à disposition de manière privée.

Notons ici que la relation d’accès au package 2 n’implique aucune relation directe avec le package 3. La relation d’import du package 3 n’est donc pas superflue et est nécessaire si le package 4 doit contenir les mêmes éléments que le package 3.

Le package 5 dispose également de 2 relations : 

- il importe le package 1, et donc tous les éléments publics de celui-ci.
- il accède à tous les éléments publics du package 2 en les rendant privés dans son sein.

Notons ici que le package 1 importe déjà le package 2. L’ensemble des éléments publics du package 2 sont également présents dans le package 1. De ce fait, l’import du package 1 par le package 5 rend la relation d’accès vers le package 2 nulle. En effet, l’import du package 1 entraîne la mise à disposition de manière publique l’ensemble de ses éléments. Or ceux-ci sont composés des éléments publics du package 2. Ainsi le fait de représenter une relation d’accès au package 2 n’est pas bonne, puisqu’elle est implicite du fait de l’import du package 1.