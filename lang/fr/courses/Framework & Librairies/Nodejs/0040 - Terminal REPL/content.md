REPL est l'abréviation de Read Eval Print Loop (boucle de lecture, d'évaluation et d'impression) et représente un environnement informatique tel qu'une console Windows ou un shell Unix/Linux où l'on entre une commande et où le système répond par une sortie en mode interactif. Node.js ou Node est livré avec un environnement REPL. Il effectue les tâches suivantes −

- **Read** - Lit l'entrée de l'utilisateur, analyse l'entrée en structure de données JavaScript et la stocke en mémoire.
- **Eval** - Prend et évalue la structure de données.
- **Print** - Imprime le résultat.
- **Loop** - Fait tourner en boucle la commande ci-dessus jusqu'à ce que l'utilisateur appuie deux fois sur ctrl-c.

La fonction REPL de Node est très utile pour expérimenter les codes Node.js et pour déboguer les codes JavaScript.

## Terminal REPL

### Démarrage de REPL

REPL peut être lancé en exécutant simplement node sur le shell/console sans aucun argument comme suit.

```bash
$ node
```

Vous verrez l'invite de commande REPL > où vous pouvez taper n'importe quelle commande Node.js -

```bash
$ node
>
```

### Expression simple

Essayons une simple mathématique à l'invite de commande de Node.js REPL -

```bash
$ node
> 1 + 3
4
> 1 + ( 2 * 3 ) - 4
3
>
```

### Utiliser des variables

Vous pouvez utiliser des variables pour stocker des valeurs et les imprimer plus tard comme tout script conventionnel. Si le mot-clé var n'est pas utilisé, la valeur est stockée dans la variable et imprimée. Alors que si le mot-clé var est utilisé, la valeur est stockée mais pas imprimée. Vous pouvez imprimer les variables en utilisant console.log().

```bash
$ node
> x = 10
10
> var y = 10
undefined
> x + y
20
> console.log("Hello World")
Hello World
undefined
```

### Expression multiligne

Le REPL de Node prend en charge les expressions multilignes similaires à celles de JavaScript. Regardons la boucle do-while suivante en action -

```bash
$ node
> var x = 0
undefined
> do {
   ... x++;
   ... console.log("x: " + x);
   ... } 
while ( x < 5 );
x: 1
x: 2
x: 3
x: 4
x: 5
undefined
>
```

... vient automatiquement lorsque vous appuyez sur Entrée après la parenthèse ouvrante. Node vérifie automatiquement la continuité des expressions.

### Variable de soulignement

Vous pouvez utiliser le trait de soulignement (_) pour obtenir le dernier résultat -

```bash
$ node
> var x = 10
undefined
> var y = 20
undefined
> x + y
30
> var sum = _
undefined
> console.log(sum)
30
undefined
>
```

## Commandes REPL

- **ctrl + c** - termine la commande en cours.
- **ctrl + c deux fois** - termine le Node REPL.
- **ctrl + d** - termine le Node REPL.
Touches haut/bas : voir l'historique des commandes et modifier les commandes précédentes.
- **Touches de tabulation** - liste des commandes en cours.
- **.help** - liste de toutes les commandes.
- **.break** - quitte une expression multiligne.
- **.clear** - quitte l'expression multiligne.
- **.save filename** - enregistre la session Node REPL actuelle dans un fichier.
- **.load filename** - charge le contenu du fichier dans la session Node REPL actuelle.