Le langage CSS met à disposition de nombreuses unités pour définir une taille. 

__Remarque__ : Lorsqu’une longueur est définie en CSS, il ne doit pas y avoir d’espace blanc entre le chiffre et l’unité de longueur. 

Exemple :

```css
p {
	width: 500px; /* Manière correcte de définir la largeur des paragraphes */
	height: 300 px; /* Manière incorrecte de définir la hauteur des paragraphes, car il y a espace entre le 300 et le px */
}
```

Pour certaines propriétés CSS, telles que ```padding```, des longueurs négatives sont autorisées.

Il existe, en CSS, deux types d’unités de longueur : les unités **absolues** et les unités **relatives**.

## Les unités de longueur absolues

Les unités de longueur absolues sont fixes et lorsqu’une taille est définie avec une de ces unités, l’élément apparaît avec la taille exacte définie. 

__Remarque__ : Les unités de longueur absolues ne sont pas recommandées pour l’affichage sur écrans, car la taille de ces derniers varient d’un appareil à l’autre. En revanche, ces unités de longueur peuvent être utilisées pour des mises en pages d’impression, par exemple. 

Voici la liste des unités de longueur absolues disponibles en CSS :

- **mm** : millimètres
- **cm** : centimètres
- **in** : inches (1 in = 2.54 cm)
- **px** : pixels
- **pt** : points
- **pc** : picas (1 pc = 12 pt)

## Les unités de longueur relatives

Les unités de longueur relative permettent de spécifier une taille qui sera elle-même relative à la taille définie dans une autre propriété. L’utilisation de ces unités est recommandée pour les écrans. 

Ci-dessous, la liste des unités de longueur relatives en CSS :

- **em** : en relation avec la taille de la police d’un élément (2em signifie donc deux fois la taille actuelle de la police de l’élément)
- **ex** : en relation avec la taille X (x-height) de la police actuelle (rarement utilisé)
- **ch** : en rapport avec la largeur du 0
- **rem** : en rapport avec la taille de la police d’un élément racine
- **vw** : la relation est la suivante : 1% de la largeur de l’écran de l’appareil utilisé pour visionner le site web
- **vh** : la relation est la suivante : 1% de la hauteur de l’écran de l’appareil utilisé pour visionner le site web
- **vmin** : la relation est la suivante : 1% de la plus petite dimension de l’appareil utilisé pour visionner le site web
- **vmax** : la relation est la suivante : 1% de la plus grande dimension de l’appareil utilisé pour visionner le site web
- **%** : en relation avec l’élément parent