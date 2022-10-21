Le terme de “cookie” est aujourd’hui dans toutes les bouches, mais reste néanmoins trop souvent méconnu. Nous allons ici vous présenter ce qu’ils sont, et découvrir comment les créer, les modifier, ou encore les supprimer.

## Un cookie, c’est quoi ?

Les cookies sont des fichiers stockés directement dans le navigateur qui contiennent des données sous forme de clé-valeur. La partie “clé” permet de donner un nom à la “valeur” qui est stockée et y est donc associée.

Ils permettent de conserver des informations envoyées par l’utilisateur et donc de pouvoir s’en resservir, et cela, de manière relativement simple. Par exemple, ils permettent souvent de se connecter plus facilement à un site en gardant en mémoire les informations de connexion. Ce sont eux qui vous évitent les fastidieuses tâches d’écriture d’identifiants et de mots de passe.

## Sont-ils dangereux ?

Non, vous l’aurez compris, ce ne sont que des fichiers stockés par le navigateur. Il faut également savoir une chose importante : chaque site ne peut normalement accéder qu’à ses propres cookies. De telle sorte que lorsque vous visitez un site web, alors celui-ci ne pourra pas disposer des informations que vous avez stockées à propos d’autres sites web.

En revanche, il existe tout de même un danger qui réside dans la gestion des cookies par l’utilisateur. Étant stockés dans le navigateur de l’utilisateur, c’est ce dernier qui va devoir les gérer et ne pas faire n’importe quoi avec. Si un seul site web ne peut pas accéder à l’ensemble des cookies, un programme malveillant installé sur l’ordinateur peut tout de même réussir à intercepter des cookies et donc des informations parfois sensibles qu’ils contiennent.

Aussi l’un des enjeux des développeurs en termes de gestion des cookies va consister à ne laisser aucune information sensible stockée dans les cookies, du moins dans la mesure du possible. Par ailleurs, vous devrez sécuriser vos cookies afin qu’ils ne soient disponibles que sur votre application, sans quoi leurs contenus pourront être exploités par n’importe qui !

## Créer un cookie

Bien que la majorité des cookies soient initiés côté serveur, il reste possible de créer des cookies côté client grâce au JavaScript. Pour cela, nous pouvons utiliser l’objet ```document.cookie```.

Comme présenté ci-dessus, les cookies sont un système de clé-valeur. Ainsi, afin de créer un cookie, il faudra passer une clé (par exemple : “website”), ainsi qu’une valeur (par exemple : “microlead”. Cette paire de clé-valeur devra être présentée sous forme de chaîne de caractères, et la clé et la valeur devront être séparées par le symbole “=”. Par exemple :

```js
document.cookie = "website=microlead"
```

Il est également possible d’afficher la liste des cookies avec un simple ```console.log()``` :

```js
console.log( document.cookie )
```


En plus d’une paire clé-valeur, il est aussi possible de définir des options lors de la création de cookies comme leur domaine de validité ou encore leur date d’expiration (aucun cookie n’est stocké définitivement dans un navigateur).

Nous allons donc pouvoir préciser en premier lieu le répertoire dans lequel le cookie est accessible avec l’option ```path```. Pour le rendre accessible pour toutes les pages, on utilise ```path=/```.

L’option “**domain**” permet de préciser le domaine sur lequel le cookie est accessible. Exemple :

```js
document.cookie = "website=microlead; path=/; domain=microlead.fr";
```

## Expiration d’un cookie

Par défaut, un cookie est supprimé dès que le navigateur est fermé. Cependant, l’option ```expires``` permet de préciser une date d’expiration pour un cookie, afin que celui-ci persiste davantage dans le temps et soit réutilisable.

Pour que cette option fonctionne correctement, il faudra bien fournir un format de date spécifique ainsi que le fuseau horaire GMT. Vous pouvez vous référer au cours sur l’objet ```Date``` en cas de besoin.

Une image valant mille mots, voici un exemple de définition d’un cookie qui expirera exactement 24 h après sa création :

```js
let custom_date = new Date(Date.now() + 86400000);
custom_date = custom_date.toUTCString();
document.cookie = "website=microlead; path=/; domain=microlead.fr; expires=" + custom_date;
```

## Sécurité

Pour davantage de sécurité, il est possible d’indiquer au navigateur de n’envoyer un cookie qu’exclusivement via le protocole HTTPS. Il suffit pour cela d’ajouter le mot-clé ```secure``` de la sorte : 

```js
// Ajout du mot-clé “secure”
document.cookie = "website=microlead; path=/; domain=microlead.fr; secure; expires=" + custom_date;
```

## Modifier ou supprimer un cookie

Pour modifier un cookie, il suffit de le réécrire en utilisant une clé déjà existante et en changeant les autres informations.

Il n’existe pas de méthode spécifique permettant la suppression d’un cookie en JavaScript. Cependant, il existe une astuce qui consiste à réécrire la valeur à “vide”, en précisant une date passée, et non future comme date d’expiration. De la sorte le cookie sera supprimer :

```js
// suppression d’un cookie en vidant sa valeur, et 
// en définissant sa date d’expiration à une date
// passée.
document.cookie = "website=; expires=Thu, 01 Jan 1970 00:00:00 UTC; secure"
```

