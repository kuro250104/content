Lorsqu’un développeur a besoin de lier un fichier, une page web ou une image au sein d’un fichier HTML, il a le choix entre préciser le chemin d’accès absolu, qui part du fichier racine et est plus précis, ou préciser le chemin d’accès relatif, moins précis mais beaucoup plus rapide à écrire.

Certains langages n’acceptent que des chemins absolus, car plus précis. D’autres, acceptent des chemins d’accès relatifs. Le langage HTML fait partie des langages informatiques qui acceptent les deux types de chemins d’accès.

## Chemin absolu

Un chemin d’accès à un fichier est dit **absolu** lorsqu’on utilise l’**adresse précise** - depuis le dossier racine - du fichier, du document ou de l’image. C’est le cas, par exemple, lorsqu’une image provenant d’un autre site est intégrée sur un autre site web. L’URL indiquée dans l’attribut ```src``` est absolue.

Exemple:

``` html
<body>
    <!-- L'URL de l'image indiquée dans l'attribut src est absolue -->
    <img src="https://cdn.pixabay.com/photo/2020/11/22/17/28/cat-5767334_960_720.jpg" alt="Un chat">
</body>
```

## Chemin relatif

Un **chemin relatif** est un chemin dont l’adresse **n’est pas précise**. Il s’agit simplement d’indiquer le nom du dossier dans lequel se trouve le fichier à inclure, suivi d’un slash et du nom du fichier à inclure, sans oublier de préciser l’extension du fichier.

**Un chemin relatif part toujours du fichier actuellement utilisé**. Le chemin relatif est donc écrit à partir du fichier actuel.

Exemple :

``` html
<body>
    <!-- Image avec chemin relatif -->
    <img src="images/picture.jpg" alt="Un chat">
</body>
```

Dans le cas où le fichier actuellement utilisé est situé dans un sous-dossier et que le fichier à inclure se trouve un dossier au-dessus, il suffit de rajouter ../ avant le nom du dossier et le nom du fichier.

Exemple :

``` html
<body>
    <!-- Image depuis un dossier au-dessus du dossier courant -->
    <img src="../images/picture.jpg" alt="Un chat">
</body>
```