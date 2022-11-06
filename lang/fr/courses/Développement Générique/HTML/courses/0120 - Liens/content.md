Les liens représentent un élément important d’un site web. En effet, ils permettent à l’utilisateur de naviguer entre les différentes pages d’un site, ou d’être redirigés vers un autre site en cliquant sur un lien en particulier. Les liens permettent aussi à l’utilisateur de contacter le propriétaire du site, entre autres.

## Créer des liens en HTML

Il existe différents types de liens :

- **Les liens externes** : ce sont des liens qui redirigent l’utilisateur vers un autre site web.
- **Les liens internes** :  ce sont les plus utilisés. En effet, ils permettent à l’utilisateur de naviguer entre les différentes pages d’un site internet.
- **Les liens d’ancres** : ce type de liens sont utilisés comme raccourci sur les pages webs particulièrement longues. Ils donnent la possibilité à l’utilisateur de se rendre à une section plus basse du site, sans que cet utilisateur n’ai besoin de faire défiler la page jusqu’à la partie qui l’intéresse. 

Peu importe le type de lien que le développeur souhaite utiliser pour le site qu’il est en train de construire, un lien en HTML se construit de la manière suivante :

```html
<a href="URL">Texte du lien</a>
```

L’attribut ```href``` est utilisé soit pour indiquer le chemin d’accès vers une autre page du site web, soit pour indiquer l’URL du site web sur lequel l’utilisateur doit être redirigé, soit pour indiquer la section de la page sur laquelle l’utilisateur va être redirigé, dans le cas d’un lien d’ancre. 

## Créer des liens externes

Les liens externes sont destinés à rediriger l’utilisateur vers un autre site web.

En HTML, pour créer un lien externe, il faut passer à l’attribut ```href``` l’URL du site web sur lequel l’utilisateur doit être redirigé.

Exemple :

```html
<body>
    <p>Lien externe</p>

    <!-- Redirige vers Google -->
    <a href="https://www.google.fr/">Lien externe vers Google</a>
</body>
```

## Créer des liens internes 

Le but des liens internes est de permettre à l’utilisateur de naviguer entre les différentes pages du site web.

Pour ce faire, l’attribut ```href``` reçoit en valeur le chemin d’accès qui mène au fichier HTML vers lequel l’utilisateur sera redirigé. 

Si le fichier HTML vers lequel l’utilisateur doit être redirigé se trouve dans le même dossier que le fichier actuel, la valeur passée à href ressemble à ceci :

```html
<a href="nom_du_fichier.html">
```

Cependant, pour des raisons d’organisation, il est possible que le fichier HTML vers lequel l’utilisateur doit être redirigé se trouve dans un autre dossier. Dans un tel cas, la valeur passée à href ressemble à ceci :

```html
<a href="dossier/nom_du_fichier.html">
```

Exemple avec un fichier HTML se trouvant dans le même dossier que le fichier actuel :

```html
<body>
    <p>Lien interne</p>

    <!-- Redirige vers le fichier contact.html -->
    <a href="contact.html">Lien interne vers la page contact</a>
</body>
```

Exemple avec un fichier HTML se trouvant dans un autre dossier :

```html
<body>
    <p>Lien interne</p>

    <!-- Redirige vers le fichier contact.html dans le répertoire dossier -->
    <a href="dossier/contact.html">Lien interne vers la page contact</a>
</body>
```

## Ouvrir un lien dans un nouvel onglet 

De manière générale, pour des raisons de confort et pour éviter à l’utilisateur de quitter le site web qu’il est en train de consulter, un lien externe ouvrira dans un nouvel onglet le site vers lequel l’utilisateur doit être redirigé.

Pour ce faire, l’attribut ```target``` est utilisé, et reçoit une des valeurs suivantes :

- **_self** : Par défaut. Ouvre le document dans la même fenêtre ou le même onglet
- **_blank** : Ouvre le document dans une nouvelle fenêtre ou un nouvel onglet, c’est le plus couramment utilisé
- **_parent** : Ouvre le document dans le cadre parent
- **_top** : Ouvre le document dans le corps entier de la fenêtre

Exemple :

```html
<body>
    <p>Lien externe dans un nouvel onglet</p>

    <!-- Redirigé vers Google dans un nouvel onglet -->
    <a href="https://www.google.fr/" target="_blank">Lien externe vers Google</a>
</body>
```

## Créer des liens d’ancre

Pour rappel, un lien d’ancre est un lien menant vers une partie précise d’une même page web. Ce système est utilisé lorsqu’une page web est très longue et que le développeur souhaite éviter à l’utilisateur d’avoir à faire défiler la page jusqu’à la partie qui l’intéresse.

La création d’un lien d’ancre est assez particulière. Elle se fait en deux parties. 

Dans un premier temps, il faut donner une valeur à l’attribut ```id``` pour chaque élément qui est pointé par un lien. Ensuite, le nom de l’id donné à l’élément est passé comme valeur à l’attribut ```href``` en le précédant du symbole “**#**”.

Exemple :

```html
<body>
    <!-- Créer un lien vers #p1 -->
    <a href="#p1">Vers paragraphe 1</a>
    <!-- Créer un lien vers #p2 -->
    <a href="#p2">Vers paragraphe 2</a>
    <!-- Créer un lien vers #p3 -->
    <a href="#p3">Vers paragraphe 3</a>

    <p id="p1">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam accumsan arcu nisi, quis efficitur diam
        congue vel. Aliquam erat volutpat. Quisque sodales posuere dolor vitae tempus. Curabitur ligula sapien,
        consectetur non tincidunt et, sodales id dolor. Etiam in bibendum velit. Sed tristique bibendum eleifend. Etiam
        tincidunt justo pretium felis ultricies maximus.
    </p>
    <p id="p2">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam accumsan arcu nisi, quis efficitur diam
        congue vel. Aliquam erat volutpat. Quisque sodales posuere dolor vitae tempus. Curabitur ligula sapien,
        consectetur non tincidunt et, sodales id dolor. Etiam in bibendum velit. Sed tristique bibendum eleifend. Etiam
        tincidunt justo pretium felis ultricies maximus.
    </p>
    <p id="p3">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam accumsan arcu nisi, quis efficitur diam
        congue vel. Aliquam erat volutpat. Quisque sodales posuere dolor vitae tempus. Curabitur ligula sapien,
        consectetur non tincidunt et, sodales id dolor. Etiam in bibendum velit. Sed tristique bibendum eleifend. Etiam
        tincidunt justo pretium felis ultricies maximus.
    </p>
</body>
```

## Lien vers une adresse e-mail

Le langage HTML donne également la possibilité à l’utilisateur de pouvoir envoyer un mail au propriétaire d’un site web. Pour ce faire, l’attribut href reçoit en valeur un adresse mail, précédé de “**mailto:**”.

Exemple :

```html
<!-- Ouvre le logiciel de messagerie pour envoyer un mail directement à l'adresse mail john@doe.com -->
<a href="mailto:john@doe.com">Envoyer un mail</a>
```

## Ajouter une infobulle

Pour rappel, en HTML, une infobulle est une “bulle” contenant du texte, qui s’affiche lorsque l’utilisateur survole un lien avec la souris. 

Pour afficher une infobulle, l’attribut ```title``` doit être utilisé, avec pour valeur, le texte à afficher lorsque le lien sera survolé par la souris.

Cet attribut est, bien que non obligatoire, très utile à différentes fins : il permet de favoriser le référencement et joue également un rôle concernant l’accessibilité. Il est donc important de le considérer très fortement comme obligatoire.

Exemple :

```html
<!-- Redirigé vers Google et affiche "Go to google" au survol de la souris -->
<a href="https://www.google.com/" title="Go to Google">Faire une recherche</a>
```