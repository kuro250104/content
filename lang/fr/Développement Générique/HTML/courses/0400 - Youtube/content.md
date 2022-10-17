YouTube permet l’intégration de vidéos au sein d’un site web par l’intermédiaire d’un code prêt à l’emploi qu’il n’y a plus qu’à coller dans le document HTML.

Ce cours présente d’abord comment intégrer une vidéo Youtube sur une page web, puis traite des différentes “options” pouvant être ajoutées.

## Intégrer une vidéo YouTube

Pour intégrer une vidéo sur un site web directement depuis YouTube, il suffit de se rendre sur la vidéo souhaitée, puis de cliquer sur “partager”, puis “intégrer”. À partir de là, YouTube fournit directement le code nécessaire pour l’inclusion. Il ne reste plus qu’à le copier/coller au sein du fichier HTML.

Exemple :

``` html
<iframe width="560" height="315" src="https://www.youtube.com/embed/tbg4EmIJ5pM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```

## Lecture automatique YouTube

La lecture automatique est activée par défaut dans le code fourni par YouTube. Cela signifie qu’au premier chargement de la page web, la vidéo va se lancer automatiquement. 

Pour désactiver cette option, il suffit d’effacer la valeur **autoplay** dans l’attribut ```allow```.

Exemple :

``` html
<iframe width="560" height="315" src="https://www.youtube.com/embed/tbg4EmIJ5pM" title="YouTube video player" frameborder="0" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```

## Désactiver les contrôles de la vidéo

Par défaut, dans le code fourni par YouTube, les contrôles sont activés. Pour les désactiver, il suffit de rajouter ```?controls=0```, à la fin de l’adresse définie dans l’attribut ```src```.

``` html
<iframe width="560" height="315" src="https://www.youtube.com/embed/tbg4EmIJ5pM?controls=0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```