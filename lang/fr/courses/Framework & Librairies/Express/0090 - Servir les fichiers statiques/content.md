Les fichiers statiques sont des fichiers que les clients téléchargent tels quels depuis le serveur. Créez un nouveau répertoire, public. Express, par défaut, ne vous permet pas de servir des fichiers statiques. Vous devez l'activer en utilisant l'intergiciel intégré suivant.

```js
app.use(express.static('public'));
```

__Note__ - Express recherche les fichiers par rapport au répertoire statique, le nom du répertoire statique ne fait donc pas partie de l'URL.

Notez que la route racine est maintenant définie sur votre répertoire public, donc tous les fichiers statiques que vous chargez seront considérés comme publics en tant que racine. Pour vérifier que tout fonctionne bien, ajoutez un fichier image dans votre nouveau répertoire public et changez son nom en "testimage.jpg". Dans vos vues, créez une nouvelle vue et incluez le fichier comme suit

```
html
    head
    body
        h3 Testing static file serving:
        img(src = "/testimage.jpg", alt = "Testing Image
```

## Répertoires statiques multiples

Nous pouvons également définir plusieurs répertoires d'actifs statiques à l'aide du programme suivant : -.

```js
var express = require('express');
var app = express();

app.use(express.static('public'));
app.use(express.static('images'));

app.listen(3000);
```

## Préfixe du chemin virtuel

Nous pouvons également fournir un préfixe de chemin pour servir les fichiers statiques. Par exemple, si vous voulez fournir un préfixe de chemin comme '/static', vous devez inclure le code suivant dans votre fichier index.js -

```js
var express = require('express');
var app = express();

app.use('/static', express.static('public'));

app.listen(3000);
```

Maintenant, chaque fois que vous avez besoin d'inclure un fichier, par exemple un fichier de script appelé main.js résidant dans votre répertoire public, utilisez la balise script suivante -

```html
<script src = "/static/main.js" />
```

Cette technique peut s'avérer utile lorsque vous fournissez plusieurs répertoires en tant que fichiers statiques. Ces préfixes peuvent aider à distinguer les différents répertoires.