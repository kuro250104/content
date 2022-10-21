L’objet ```screen``` permet d’obtenir des informations concernant l’écran de l’utilisateur que l’on peut utiliser, soit en passant par le préfix “window” (```window.screen```), soit en appelant directement “screen”.

## L’objet screen

L’objet ```Screen``` est essentiellement utilisé pour ses attributs et les rares méthodes qu’il contient sont essentiellement destinées à gérer les attributs. En voici quelques-uns :

- L’attribut ```width``` retourne la largeur totale de l’écran en pixels.
- L’attribut ```availWidth``` retourne la largeur de l’écran moins celle de la barre de tâches, c’est-à-dire la largeur disponible de l’écran, toujours en pixels.
- L’attribut ```height``` retourne la hauteur totale de l’écran en pixels.
- L’attribut ```availHeight``` retourne la hauteur de l’écran moins celle de la barre de tâches en pixels, c’est-à-dire la hauteur disponible de l’écran.
- L’attribut ```colorDepth``` retourne la profondeur de la palette de couleur de l’écran en bits.
- L’attribut ```pixelDepth``` retourne la résolution de l’écran en bits par pixel.

Dans le cas où le navigateur ne peut pas déterminer les valeurs de ```colorDepth``` et ```pixelDepth```, il renvoie comme valeur par défaut “24”.

Moins utilisé, mais pouvant s’avérer utile, l’objet ```screen``` permet également de déterminer l’orientation de l’écran de votre utilisateur. Il dispose ainsi d’un attribut “orientation”, qui contient un objet de type ```ScreenOrientation``` dans lequel nous pouvons notamment retrouver un attribut “angle” stipulant l’angle en degré de l’écran de l’utilisateur. Ceci permettant donc de déterminer si ce dernier à un écran au format “portrait” ou “paysage”.

Voici quelques exemples de l’utilisation de l’objet “screen” :

```js
// Affiche la largeur totale de l’écran en pixels
console.log( screen.width );

// Affiche la hauteur totale de l’écran en pixels
console.log( screen.height );

// affiche la largeur totale disponible de l’écran
// pour l’affichage du site en pixels
console.log( screen.availWidth );

// affiche la hauteur totale disponible de l’écran
// pour l’affichage du site en pixels
console.log( screen.availHeight );

// affiche la profondeur de la palette de couleur
// de l’écran en bits
console.log( screen.colorDepth );

// affiche la résolution de l’écran en bits par pixels
console.log( screen.pixelDepth );
```