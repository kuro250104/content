Express utilise le module Debug pour enregistrer en interne des informations sur la correspondance des routes, les fonctions du middleware, le mode d'application, etc.

Pour voir tous les journaux internes utilisés dans Express, définissez la variable d'environnement DEBUG à Express:* lors du démarrage de l'application -

```js
DEBUG = express:* node index.js
```

Le résultat suivant s'affiche :

```bash
express:application set "x-powered-by" to true +0ms
express:application set "etag" to 'weak' +3ms
express:application set
express:application set
express:application set
express:application set
express:application set
express:application set
express:application set
express:application set
```