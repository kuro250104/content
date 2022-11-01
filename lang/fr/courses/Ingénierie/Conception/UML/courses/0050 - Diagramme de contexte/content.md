## Informations générique

- **Type** : Diagramme Structurel & comportemental
- **Périmètre** : Fonctionnel & technique
- **Langages** : Tous

## Définition / Utilisation

Le diagramme de contexte est souvent réalisé au tout début d’une conception, qu’elle soit technique ou fonctionnelle. Son rôle est principalement d’identifier les acteurs relatifs au projet décrit.

Ces acteurs sont en réalité des entités représentant un rôle au sein d’une application. Ils peuvent être humains, représenter un dispositif matériel physique, un dispositif immatériel ou encore plus simplement un autre système dont vous n’avez pas la maîtrise. Ces acteurs sont donc des entités, qui sont externes à votre système, mais qui vont pouvoir interagir avec celui-ci.

Chacun des acteurs doit être identifié. C’est-à-dire que vous devez leur donner un nom. Au-delà de l’identification, le nom doit permettre l’identifiabilité, à savoir permettre au lecteur de comprendre instantanément quel va être son rôle au sein du système.

L’ensemble du système principal est en général apparenté à une “boîte noire”. Elle est simplement représentée par un carré vide. L’ensemble des acteurs listés et / ou utilisés sur la totalité des documentations techniques ou fonctionnelles doivent être présents dans ce diagramme.

Afin de relier un acteur à la “boîte noire”, il suffit de le lier à cette dernière via un simple trait.

## Formes et symboles


| Symboles | Signification |
| --- | --- |
| ![représentation d'un acteur](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image6.png) | Acteur |
| ![représentation du système dans sa globalité](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image2.png) | “boîte noire” représentant le système dans sa globalité |
| ![lien d'interaction](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image7.png) | lien symbolisant une interaction entre un acteur et la boite noire |
| ![flèche de regroupement](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image8.png) | Flèche permettant d’effectuer un regroupement d’acteurs |

## Astuces

Il est très courant de ne pas identifier dès le début l’ensemble des acteurs. Ce problème n’est majoritairement pas dû à une impossibilité de les identifier, mais bien à l’attrait de ce type de diagramme. Étant le premier diagramme réalisé dans de nombreux cas, il semble souvent inutile de s’attarder sur celui-ci car il semble “simple” comparativement aux autres types de diagrammes.

Cette erreur peut avoir des répercussions notables sur la documentation. Il n’est pas rare de réaliser, lors de l’avancement sur la réalisation de différents diagrammes UML, qu’un ou plusieurs acteurs ont été oubliés. Il se peut même que vous ne vous en rendiez pas compte ! C’est pourquoi il est important, durant la réalisation de chaque diagramme UML, de vérifier si tous les acteurs sont bien présents dans le diagramme de contexte. Si ce n’est pas le cas, cela signifie que vous devrez modifier ce diagramme de contexte, et par conséquent revoir l’ensemble des autres diagrammes effectués en vous assurant que l’ajout de ce ou ces nouveaux acteurs n’a aucune incidence. Il est également fréquent dans le cas de l’oubli d’un acteur de ne pas penser à le réintégrer lorsque c’est nécessaire dans vos autres diagrammes, prêtez-y attention !

Il n’est pas rare de voir des regroupements d’acteurs dans d’autres types de diagrammes.

C’est ainsi le cas lorsque vous avez identifié plusieurs acteurs qui ont des rôles similaires. Il peut alors être judicieux de représenter un acteur plus général qui vous permettra d’éviter les nombreuses représentations de liens en amoindrissant la visibilité de votre schéma. Dans ce cadre, les acteurs identifiés jusqu’à présent seront représentés en dessous du nouvel acteur de “regroupement” et représenteront une spécialisation de cet acteur général. Il est important de noter que ce regroupement n’est pas forcément lié au diagramme de contexte, mais peut survenir dans d’autres diagrammes. Si vous réalisez ce type de groupement dans un diagramme de contexte, cela signifiera que le groupement présenté deviendra générique à l’ensemble de vos autres schémas (ces derniers pourront s’en resservir). A contrario, si vous effectuez un groupement dans un autre schéma, celui-ci ne sera valable que dans le schéma correspondant. Voici un exemple de regroupement d’acteur :

![Représentation d'un regroupement d'acteurs en UML](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image3.png)

## Exemples

### Exemple de lien entre un acteur et la boîte noire

![Représentation d'un lien entre un acteur et la boîte noire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image1.png)

Dans cet exemple, on distingue le lien qu’il y a entre un acteur “Acteur” sur la gauche et la boîte noire sur la droite grâce au trait plein reliant ces deux entités.

### Exemple de lien entre plusieurs acteurs et la boîte noire

![Représentation d'un lien entre plusieurs acteurs et la boîte noire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image4.png)

Cet exemple nous montre qu’il est possible de réaliser plusieurs liens vers une seule boîte noire provenant de plusieurs acteurs.

### Exemple de lien entre un regroupement d’acteur et la boîte noire

![Représentation d'un lien entre plusieurs acteurs et la boîte noire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Conception/UML/courses/0050%20-%20Diagramme%20de%20contexte/images/image5.png)

Dans cet exemple, on distingue un regroupement d’acteur : “Acteur 1” et “Acteur 2” sont regroupé en un acteur nommé ici “Regroupement d’acteurs”. Ce regroupement d’acteurs dispose d’un lien vers le système ou la boîte noire. Il en découle donc que les “Acteur 1” et “Acteur 2” ont tous deux des liens vers le système. Cette représentation évite de surcharger le schéma visuellement en représentant des liens depuis tous les acteurs vers le système ou la boîte noire.