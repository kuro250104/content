SVG signifie en anglais *Scalable Vector Graphics* (graphiques vectoriels évolutifs). Cet élément est généralement utilisé en combinaison avec le langage CSS afin de créer des animations sur des images.

## L'élément HTML ```<svg>```

Cet élément est utilisé en tant que conteneur pour les images SVG.

L’élément ```<svg>``` met à disposition du développeur web plusieurs autres éléments afin de dessiner des cercles, rectangles, images graphiques, etc.

## Prise en charge

Ci-dessous, la liste des versions des navigateurs prenant en charge cet élément :

| **Navigateur** | **Version** |
| --- | --- |
| **Chrome** | 4.0 |
| **IE/Edge** | 9.0 |
| **Firefox** | 3.0 |
| **Safari** | 3.2 |
| **Opera** | 10.1 |

## Dessiner des cercles avec svg

SVG propose plusieurs méthodes pour dessiner des tracés, des boîtes, des cercles, du texte et des images graphiques.

Pour dessiner un cercle avec SVG, il faut d’abord ouvrir et fermer la balise ```<svg>```.

Pour tracer un cercle, l’élément ```<circle>``` doit être utilisé. Il peut être accompagné des attributs ```cx``` et ```cy``` afin de renseigner les coordonnées **x** et **y** du centre du cercle. Si ces attributs ne sont pas renseignés, ils seront par défaut définis à 0.

Il est également possible de renseigner l’attribut ```r```, permettant de définir le rayon du cercle.

Les attributs ```stroke``` et ```stroke-width``` peuvent également compléter l’élément ```<circle>```. Ces deux attributs permettent de définir un contour (une bordure) pour un élément. ```Stroke``` prend en paramètre le nom d’une couleur, tandis que ```stroke-width``` prend en valeur un chiffre définissant l’épaisseur de la bordure. 

Enfin, s’il est renseigné, l’attribut ```fill``` permet de définir une couleur de remplissage pour la forme dessinée.

Exemple :

```xml
<svg width="100" height="100">
    <circle cx="50" cy="50" r="40" stroke="red" stroke-width="4" fill="blue" />
</svg>
```

## Dessiner un rectangle en SVG

Pour dessiner un rectangle en SVG, il faut utiliser l’élément ```<rect>```. Cet élément peut être complété avec les mêmes attributs que pour les cercles.

Exemple :

```xml
<svg width="400" height="100">
    <rect width="400" height="100" style="fill:rgb(126, 126, 187);stroke-width:10;stroke:rgb(211, 15, 15)" />
</svg>
```

## Comparaison entre Canvas et SVG

### Canvas

- Dépendant de la résolution
- Pas de support pour les gestionnaires d'événements
- Mauvaises capacités de rendu du texte
- On peut enregistrer l'image résultante au format .png ou .jpg
- Bien adapté aux jeux à forte intensité graphique

### SVG

- Indépendant de la résolution
- Prise en charge des gestionnaires d'événements
- Idéal pour les applications avec de grandes zones de rendu (Google Maps)
- Rendu lent s'il est complexe 
- Ne convient pas aux applications de jeu