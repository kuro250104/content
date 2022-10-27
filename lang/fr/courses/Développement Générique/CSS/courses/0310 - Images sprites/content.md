Une image “sprite” est un ensemble d’images qui sont regroupées en plusieurs. Une page web avec beaucoup d’images peut prendre plus de temps à charger, car il va générer plus de requêtes serveur afin d’aller récupérer les images.

Utiliser une image “sprite” va générer moins de requêtes serveur et réduire les besoins de téléchargement lors de l’affichage par le navigateur.

## Mise en application

Au lieu de prendre trois images séparées, il est possible de prendre un ensemble d’images et de n’afficher que celle qui est nécessaire.

Exemple :

```css
#page {
	width: 46px;
	height: 44px;
	background: url("image.gif") 0 0;
}
```

Dans l’exemple ci-dessus, l’image est générée avec la propriété ```background```. Ensuite, la portion d’image à utiliser est définie avec ```width``` et ```height```. Enfin, la position de l’image est définie (ici, 0 pixel à gauche et 0 pixel à droite) toujours dans la propriété ```background```.

__Remarque__ : Depuis le passage au protocole HTTP 2, l’utilisation de cette pratique n’entraîne plus de gains de performance aussi importants qu’avant. Cette technique est de plus en plus rarement utilisée, mais il reste possible de la retrouver si vous êtes amenés à travailler sur d’anciens projets.