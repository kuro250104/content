Il est des sites web sur lesquels il y a parfois besoin d’afficher des graphiques. L’élément ```<canvas>``` fait partie des balises HTML permettant de répondre à ce besoin.

__Remarque__ : L'élément ```<canvas>``` n'est qu'un conteneur pour les graphiques ; cela veut dire que cet élément n’est présent que pour afficher le graphique. Pour créer ce graphique, le langage JavaScript doit être utilisé.

## Prise en charge du navigateur

Voici la liste des versions de navigateurs prenant en charge l’élément ```<canvas>``` :

| **Navigateur** | **Version** |
| --- | --- |
| **Chrome** | 4.0 |
| **IE/Edge** | 9.0 |
| **Firefox** | 2.0 |
| **Safari** | 3.1 |
| **Opera** | 9.0 |

## Utilisation de l’élément <canvas>

En réalité, cet élément permet simplement de définir un zone rectangulaire sur une page web, permettant, lorsqu’il sera créé, d’afficher le graphique.

__Remarque__ : Cet élément est toujours accompagné des attributs ```id```, ```width``` et ```height```.

Exemple :

``` html
<canvas id="monCanevas" width="200" height="100"></canvas>
```