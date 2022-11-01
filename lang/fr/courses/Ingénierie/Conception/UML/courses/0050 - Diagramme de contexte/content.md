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