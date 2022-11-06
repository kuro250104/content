Le langage HTML permet à un développeur d’incorporer du contenu provenant d’un autre site web sur son propre site web. C’est par exemple le cas avec les vidéos YouTube.

## L’élément ```<iframe>``` et ses attributs

L'élément ```<iframe></iframe>``` permet d'incorporer un contenu provenant d’autre site web externe dans le site web actuel. Cet élément est principalement utilisé pour intégrer des vidéos YouTube ou des cartes Google Maps dans un site web.

Voici la liste des attributs utilisables avec ```<iframe>```. Certains sont obligatoires, d’autres non :

- ```src``` : permet d'indiquer l'adresse du document à intégrer. Cet attribut est obligatoire.
- ```width``` et ```height``` sont utilisés pour définir la taille de l'élément iframe. Si on ne peut pas modifier la taille de l'iframe en CSS, on peut les utiliser
- ```allow``` est utilisé pour définir la politique de confidentialité de l’iframe. Cela signifie que le développeur peut autoriser ou non certaines fonctionnalités propres à l’élément important. Le but de cet attribut est de renforcer la sécurité du code.
- ```sandbox``` est relativement récent. Il permet de limiter les possibilités de l’iframe. Le but, ici encore, est de renforcer la sécurité du code.

## Intégrer une vidéo YouTube

L’intégration de vidéos Youtube au sein d’un site internet est relativement courant. Celle-ci s’effectue généralement grâce aux iframes.

Pour intégrer une vidéo sur un site internet grâce aux iframes, il faut se rendre sur une vidéo YouTube, cliquer sur le bouton “Partager”, puis sur “intégrer”. Youtube génère alors un code HTML comprenant une balise “iframe” qu’il suffit de copier-coller pour l’intégrer dans une page.

```html
<body>
    <!-- Vidéo youtube intégrée avec un iframe -->
    <iframe width="560" 
        height="315" src="https://www.youtube.com/embed/22GksMxZPBU" 
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen></iframe>
</body>
```

## Définir la hauteur et la largeur d’un iframe

Pour définir la largeur et la hauteur d’un iframe, les attributs ```width``` et ```height``` doivent être utilisés. Par défaut, la largeur et la hauteur sont en ```pixels```. Il est également possible d’utiliser les propriétés du même nom avec l’attribut ```style```.


Exemple avec ```width``` et ```height``` :

```html
<!-- Iframe avec une hauteur et largeur de 500px -->
<iframe src="#" height="500" width="500" title="Intégrer un iframe"></iframe>
```

Exemple avec l’attribut ```style``` :

```html
<!-- Iframe avec une hauteur et largeur de 500px -->
<iframe src="#" style="width: 500px; height: 500px;" title="Intégrer un iframe"></iframe>
```

## Supprimer la bordure

Par défaut, une iframe est affichée avec une bordure. Pour supprimer cette bordure, il faut utiliser l’attribut ```style``` et définir la propriété ```border``` à ```none```. Il est également possible de réaliser ceci en utilisant du CSS de manière plus conventionnelle. Référez-vous aux cours de CSS afin d’y parvenir.

Exemple :

```html
<!-- Supprime la bordure autour de l'iframe -->
<iframe src="#" style="border: none" title="Intégrer un iframe"></iframe>
```