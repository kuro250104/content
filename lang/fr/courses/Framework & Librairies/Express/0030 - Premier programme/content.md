Nous avons mis en place le développement, il est maintenant temps de commencer à développer notre première application en utilisant Express. Créez un nouveau fichier appelé index.js et tapez ce qui suit dans ce fichier.

```js
var express = require('express');
var app = express();

app.get('/', function(req, res){
    res.send("Hello world!");
});

app.listen(3000);
```

Sauvegardez le fichier, allez dans votre terminal et tapez ce qui suit.

```bash
nodemon index.js
```

Cela va démarrer le serveur. Pour tester cette application, ouvrez votre navigateur et allez sur ```http://localhost:3000``` et le message "Hello world!" s'affichera.

## Comment fonctionne l'application ?

La première ligne importe Express dans notre fichier, nous y avons accès par la variable Express. Nous l'utilisons pour créer une application et l'affecter à la variable app.

### app.get(route, callback)

Cette fonction indique ce qu'il faut faire lorsqu'une requête get à la route donnée est appelée. La fonction de rappel a 2 paramètres, ```request(req)``` et ```response(res)```. L'objet ```request(req)``` représente la requête HTTP et possède des propriétés pour la chaîne de requête, les paramètres, le corps, les en-têtes HTTP, etc. De même, l'objet response représente la réponse HTTP que l'application Express envoie lorsqu'elle reçoit une requête HTTP.

### res.send()

Cette fonction prend un objet en entrée et l'envoie au client demandeur. Ici, nous envoyons la chaîne "Hello World !".

### app.listen(port, [host], [backlog], [callback]])

Cette fonction lie et écoute les connexions sur l'hôte et le port spécifiés. Le port est le seul paramètre requis ici.

**Argument et description**

- **port** - Un numéro de port sur lequel le serveur doit accepter les demandes entrantes.
- **host** - Nom du domaine. Vous devez le définir lorsque vous déployez vos applications dans le nuage.
- **backlog** - Le nombre maximum de connexions en attente dans la file d'attente. La valeur par défaut est 511.
- **callback** - Une fonction asynchrone qui est appelée lorsque le serveur commence à écouter les demandes.