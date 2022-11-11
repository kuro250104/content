Les cookies sont de simples petits fichiers/données qui sont envoyés au client avec une requête du serveur et stockés du côté du client. Chaque fois que l'utilisateur recharge le site web, ce cookie est envoyé avec la demande. Cela nous aide à garder une trace des actions de l'utilisateur.

Voici les nombreuses utilisations des cookies HTTP -.

- Session management
- Personnalisation (systèmes de recommandation)
- Suivi des utilisateurs

Pour utiliser les cookies avec Express, nous avons besoin du middleware cookie-parser. Pour l'installer, utilisez le code suivant -

```bash
npm install --save cookie-parser
```

Maintenant, pour utiliser les cookies avec Express, nous aurons besoin du cookie-parser. cookie-parser est un middleware qui analyse les cookies attachés à l'objet de requête du client. Pour l'utiliser, nous le demanderons dans notre fichier index.js ; il peut être utilisé de la même manière que les autres intergiciels. Ici, nous utiliserons le code suivant.

```js
var cookieParser = require('cookie-parser');
app.use(cookieParser());
```

cookie-parser analyse l'en-tête Cookie et remplit req.cookies avec un objet dont la clé est le nom du cookie. Pour définir un nouveau cookie, définissons une nouvelle route dans votre application Express comme -

```js
var express = require('express');
var app = express();

app.get('/', function(req, res){
    res.cookie('name', 'express').send('cookie set'); //Sets name = express
});

app.listen(3000);
```

Pour vérifier si votre cookie est installé ou non, il suffit d'aller dans votre navigateur, de lancer la console et d'entrer -

```js
console.log(document.cookie);
```

Vous obtiendrez le résultat suivant (il se peut qu'il y ait plus de cookies définis, peut-être en raison des extensions de votre navigateur).

```js
"name = express"
```

Le navigateur renvoie également des cookies chaque fois qu'il interroge le serveur. Pour afficher les cookies de votre serveur, sur la console du serveur dans une route, ajoutez le code suivant à cette route.

```js
console.log('Cookies: ', req.cookies);
```

La prochaine fois que vous enverrez une demande à cette route, vous recevrez le résultat suivant.

```js
Cookies: { name: 'express' }
```

## Adding Cookies with Expiration Time

Vous pouvez ajouter des cookies qui expirent. Pour ajouter un cookie qui expire, il suffit de passer un objet dont la propriété 'expire' est définie sur l'heure à laquelle vous souhaitez qu'il expire. Par exemple,

```js
//Expires after 360000 ms from the time it is set.
res.cookie(name, 'value', {expire: 360000 + Date.now()});
```

Une autre façon de définir le délai d'expiration est d'utiliser la propriété "maxAge". En utilisant cette propriété, nous pouvons fournir un temps relatif au lieu d'un temps absolu. Voici un exemple de cette méthode.

```js
//This cookie also expires after 360000 ms from the time it is set.
res.cookie(name, 'value', {maxAge: 360000});
```

## Deleting Existing Cookies

Pour supprimer un cookie, utilisez la fonction clearCookie. Par exemple, si vous devez effacer un cookie nommé foo, utilisez le code suivant.

```js
var express = require('express');
var app = express();

app.get('/clear_cookie_foo', function(req, res){
    res.clearCookie('foo');
    res.send('cookie foo cleared');
});

app.listen(3000);
```