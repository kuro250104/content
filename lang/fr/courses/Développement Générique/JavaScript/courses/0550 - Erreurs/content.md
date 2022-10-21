Dans le monde du développement et particulièrement du développement Web, il y a toujours une probabilité que des erreurs se produisent. Elles peuvent avoir différentes origines :

- Elles peuvent provenir du développeur dans le cadre d’une erreur de syntaxe.
- Elles peuvent provenir du serveur si celui-ci est dans l’incapacité de fournir les ressources nécessaires.
- Elles peuvent provenir du navigateur.
- Elles peuvent également survenir du fait d’un utilisateur qui envoie une valeur non valide via un formulaire par exemple.

Laisser une erreur non traitée dans un code peut avoir de graves conséquences pour un site : dans le meilleur des cas, l’erreur n’est pas grave et sera ignorée. Dans d’autres cas, elle peut provoquer l’arrêt brutal d’un script et donc entraîner des dysfonctionnements au sein d’une ou plusieurs pages d’une application web. Dans le pire des cas, une erreur peut être utilisée comme faille de sécurité par des utilisateurs malveillants qui vont l’exploiter pour dérober des informations ou pour tromper les autres visiteurs.

## try…catch

Lorsqu’une erreur d’exécution survient dans un script, le JavaScript crée automatiquement un objet à partir de l’objet global ```Error```, qui permet la gestion des erreurs en JavaScript.

Le JavaScript dispose d’une syntaxe en deux blocs ```try``` et ```catch```.

Nous allons placer le code à tester au sein de notre bloc ```try``` puis “capturer” l’erreur potentielle dans le bloc ```catch``` et indiquer comment la gérer.

JavaScript va en premier tenter d’exécuter le code du bloc ```try```, si le code s’exécute normalement le bloc ```catch``` sera ignoré. Dans le cas contraire, le bloc ```catch``` sera exécuté et permettra de gérer l’erreur comme vous le souhaitez.

```js
try {
    console.log( “bloc try” );
} catch(err) {
    console.log( “bloc catch” );
}
```

Prenons un exemple concret en déclarant une variable qui n’existe pas afin de comprendre ce que le bloc ```catch``` nous fournit comme informations :

```js
try {
    prenom;
} catch(err) {
    console.log(‘Erreur rencontrée. ’ +
    ‘\nNom de l\’erreur : ’ + err.name +
    ‘\nMessage d\’erreur : ’ + err.message +
    ‘\nEmplacement de l\’erreur : ’ + err.stack);
}
```

L’exécution du bloc de code ci-dessus affichera :

```js
ReferenceError : prenom is not defined
```

## throw

Pour définir une exception, nous allons devoir créer un objet à partir de l’un des constructeurs d’erreurs prédéfinis en JavaScript en utilisant la syntaxe ```new Error()```, c'est-à-dire en instanciant un objet ```Error```.

Nous allons notamment pouvoir passer un message pour expliquer l’erreur lors de la création de celle-ci plutôt que d’utiliser le message standard proposé par le JavaScript. Voyons un exemple :

```js
let nombre = 10;
let diviseur = 0;
let resultat = 0;
 
if(diviseur == 0) {
    throw new Error('Impossible de diviser par 0');
} else {
    resultat = nombre / diviseur;
}
 
console.log(resultat);
```