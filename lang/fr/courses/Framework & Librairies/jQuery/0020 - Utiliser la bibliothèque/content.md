Dans ce nouveau cours, nous allons configurer notre environnement de travail pour utiliser les fonctionnalités de jQuery.

Comme en JavaScript, vous pouvez inclure jQuery dans l’élément head ou body. Cependant, il est toujours recommandé de l’inclure avant la fermeture de votre body.

De plus, votre code jQuery ne sera interprété par votre navigateur qu’uniquement s’il est écrit à la suite de l’appel de jQuery. Autrement dit, vous devez placer votre code jQuery après l’inclusion de la librairie jQuery.

Pour pouvoir utiliser jQuery, il est nécessaire de l’inclure dans vos pages web. Il existe différentes façons de faire cette inclusion

## Télécharger et inclure jQuery

La première est d'aller sur le site officiel de jQuery et de télécharger la dernière version de jQuery disponible. Sur la page de téléchargement, vous trouverez deux types de fichiers : les fichiers compressés et les fichiers non compressés.

La copie compressée de jQuery ne contient aucun espace entre le code. Le but est de réduire le poids total de la bibliothèque pour améliorer les performances du site. C'est la version que nous mettons habituellement sur un site en production.

Cependant, pour travailler dans un environnement de développement, nous vous recommandons d'utiliser la version non compressée à la place, qui est la version lisible de la bibliothèque.

Après avoir téléchargé le fichier, il est recommandé de le placer dans le même dossier que le fichier qui utilisera cette bibliothèque pour simplifier les opérations. Ensuite, nous devrons créer un lien entre notre fichier jQuery et le fichier qui l'utilisera. Pour cela, nous utiliserons l'élément script avec l'attribut “src”.

Créons maintenant un fichier HTML et incluons notre fichier jQuery dedans.

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>jQuery</title>
</head>
<body>
    <script src="jquery-3.5.1.js"></script>
</body>
</html>
```

Notez qu’à partir de là, la librairie sera utilisable après la ligne ```<script src="jquery-3.5.1.js"></script>```.

Attention, vous pourrez bien évidemment placer les fichiers de la bibliothèque à un autre endroit de votre projet. Vous devrez cependant pour cela modifier l’attribut “src” de la balise ```<script>``` afin de faire pointer le lien vers la librairie. Nous vous recommandons de vous renseigner sur le principe de fonctionnement des liens relatifs / absolus en cas de nécessité.

## Inclure jQuery via un CDN

Une autre façon d'utiliser jQuery est de l'inclure à partir du CDN au lieu de télécharger et d'héberger le fichier jQuery vous-même.

L'utilisation d'un CDN présente deux avantages importants : bien sûr, vous n'avez pas à stocker de fichiers, mais vous pouvez également optimiser les performances de votre site.

Si le visiteur a utilisé le même CDN pour visiter un autre site contenant le même fichier dans le passé, le fichier est susceptible d'être toujours mis en cache dans son navigateur, il n'est donc pas nécessaire de le télécharger à nouveau. Cela accélérera l'affichage de notre page.

Par conséquent, la plupart des sites ont tendance à utiliser des CDN lorsqu'ils incluent des ressources externes. Nous vous suggérons donc ici d'utiliser le CDN fourni par jQuery.

Cliquez simplement sur la ressource requise et incluez le code fourni dans la page HTML comme indiqué ci-dessous :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>jQuery</title>
</head>
<body>
    <script
    src="https://code.jquery.com/jquery-3.5.1.js"
    integrity="sha256-QWo7LDvxbWT2tbbQ97B53yJnYU3WhH/C8ycbRAkjPDc="
    crossorigin="anonymous"></script>
</body>
</html>
```

Vous êtes maintenant fin prêt à utiliser jQuery !