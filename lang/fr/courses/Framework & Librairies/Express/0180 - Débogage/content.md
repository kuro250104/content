Express utilise le module Debug pour enregistrer en interne des informations sur la correspondance des routes, les fonctions du middleware, le mode d'application, etc.

Pour voir tous les journaux internes utilisés dans Express, définissez la variable d'environnement DEBUG à Express:* lors du démarrage de l'application -

```js
DEBUG = express:* node index.js
```

Le résultat suivant s'affiche :

```bash
express:application set "x-powered-by" to true +0ms
express:application set "etag" to 'weak' +3ms
...
```

Ces journaux sont très utiles lorsqu'un composant de votre application ne fonctionne pas correctement. Cette sortie verbeuse peut être un peu écrasante. Vous pouvez également restreindre la variable DEBUG à une zone spécifique à enregistrer. Par exemple, si vous souhaitez restreindre la journalisation à l'application et au routeur, vous pouvez utiliser le code suivant.

```bash
DEBUG = express:application,express:router node index.js
```

Debug est désactivé par défaut et est automatiquement activé dans un environnement de production. Debug peut également être étendu pour répondre à vos besoins, vous pouvez en savoir plus à ce sujet sur sa page npm.