Le BOM, pour Browser Object Model (modèle d’objet navigateur), permet au JavaScript de “discuter” avec le navigateur. 

Il n’y a pas de standards officiels concernant le BOM, et bien que celui-ci soit implémenté sur la plupart des navigateurs modernes, cela se réfère tout de même souvent aux propriétés et méthodes du BOM.

## L’objet Windows

Cet objet est supporté par tous les navigateurs et représente la fenêtre du navigateur. Par conséquent, tous les objets globaux, variables et fonctions globales deviennent automatiquement membres de l’objet Windows.

Les variables globales sont des propriétés de l’objet **Windows**, et les fonctions globales sont des méthodes de cet objet.

Même l’objet ```document```, du DOM HTML, est une propriété de l’objet **Windows**. Ainsi, écrire ce code :

```js
window.document.getElementById("header");
```

Revient au même qu’écrire ceci :

```js
document.getElementById("header");
```

## Taille de la fenêtre

Deux propriétés peuvent être utilisées pour déterminer la taille de la fenêtre du navigateur. Toutes deux retournent la taille en pixels :

- ```window.innerHeight``` : La hauteur intérieure de la fenêtre du navigateur en pixels
- ```window.innerWidth``` : La largeur intérieure de la fenêtre du navigateur en pixels

Exemple :

```js
let w = window.innerWidth;
let h = window.innerHeight;
```

__Remarque__ : La fenêtre du navigateur n’inclut pas la barre d’outils et les barres de défilement.

## Autres méthodes utilisables avec Windows

Ci-dessous une liste dressant les autres méthodes utilisables avec ```Windows``` :

- ```window.open()``` : ouvre une nouvelle fenêtre
- ```window.close()``` : ferme la fenêtre actuelle
- ```window.moveTo()``` : bouge la fenêtre actuelle
- ```window.resizeTo()``` : redimensionne la fenêtre actuelle