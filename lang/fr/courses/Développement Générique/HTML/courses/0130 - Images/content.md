Il n'y a pas de sites web qui n’affichent pas d’images. Que ce soit pour le logo ou à des fins d’illustration, chaque site affiche au moins une image.

## Insérer des images

Pour afficher des images sur une page web, le langage HTML met à disposition l’élément ```<img></img>```. Cet élément est obligatoirement accompagné de l’attribut ```src```, qui sert à préciser le chemin d’accès de l’image à afficher.

Pour des raisons d’accessibilité, il est recommandé d’ajouter l’attribut ```alt```. Celui-ci reçoit en valeur un texte alternatif - court - décrivant l’image. Ce texte a deux utilités. La première est de permettre au navigateur d’afficher le texte alternatif en cas de problème d’affichage de l’image. La seconde, primordiale, permet de rendre le site web accessible à des personnes malvoyantes ou malentendantes. En effet, le texte alternatif sera littéralement lu par une voix artificielle lorsque l’utilisateur malvoyant ou aveugle se rendra sur le site web.

Comme pour les liens internes, évoqués dans le cours précédent, une image peut être soit enregistrée dans le même dossier que le fichier HTML, soit dans un dossier différent. 

Pour le premier cas, l’attribut ```src``` reçoit en valeur le nom de l’image à afficher, suivi de son extension (image.jpg, par exemple). 

Dans le second cas, l’attribut ```src``` reçoit d’abord le nom du dossier contenant l’image, suivi d’un slash (/), suivi du nom de l’image et de son extension (dossier/image.jpg, par exemple).

Exemple :

```html
<body>
    <!-- Affiche de l'image fond.png -->
    <img src="fond.png" alt="L'image est un fond">
</body>
```

## Lier une image depuis un site web externe

Afin de rendre un fichier HTML moins lourd et d’optimiser le temps d’affichage d’une page web, le langage HTML rend possible le fait d’afficher une image provenant directement d’un autre site web.

Pour ce faire, l’attribut ```src``` reçoit en valeur **l’URL complète** de l’image à afficher.

Exemple :

```html
<body>
    <!-- Affiche une image externe à l'aide d'une url -->
    <img src="https://cdn.pixabay.com/photo/2020/11/22/17/28/cat-5767334_960_720.jpg" alt="Un chat">
</body>
``` 

## Largeur et hauteur

Il existe deux moyens de définir la taille d’une image en HTML. La première consiste à utiliser les propriétés ```width``` et ```height``` au sein de l’attribut ```style```, la seconde consiste à utiliser directement les attributs HTML ```width``` et ```height```.

**Remarque** : 

- Lorsque les attributs ```width``` et ```height``` sont spécifiés, cela permet au navigateur de réserver un espace correspondant à la largeur et à la hauteur spécifiées au moment du chargement de la page. Cela permet notamment d’éviter un changement de mise en page lors du chargement de la page. 
- Depuis la version 5 du langage HTML, l’attribut ```width``` accepte seulement les largeurs en **pixels** et non plus en pourcentage.

Exemple avec l’attribut ```style``` :

```html
<!-- Affiche l'image moto.png et spécifiant la hauteur et la largeur -->
<img src="moto.png" alt="Il s'agit d'une photo de moto"  style="width: 500px; height: 600px;">
```

Exemple avec les attributs ```width``` et ```height``` :

```html
<!-- Affiche l'image moto.png et spécifiant la hauteur et la largeur -->
<img src="moto.png" alt="Il s'agit d'une photo de moto"  width="500" height="600">
```
