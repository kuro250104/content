Selon la documentation de MongoDB, Map-reduce est un paradigme de traitement des données permettant de condenser de grands volumes de données en des résultats agrégés utiles. MongoDB utilise la commande mapReduce pour les opérations map-reduce. MapReduce est généralement utilisé pour le traitement de grands ensembles de données.

## Commande MapReduce

Voici la syntaxe de la commande mapReduce de base -

```
>db.collection.mapReduce(
    function() {emit(key,value);},  //map function
    function(key,values) {return reduceFunction}, {   //reduce function
        out: collection,
        query: document,
        sort: document,
        limit: number
    }
)
```

La fonction map-reduce interroge d'abord la collection, puis mappe les documents de résultat pour émettre des paires clé-valeur, qui sont ensuite réduites en fonction des clés qui ont plusieurs valeurs.

Dans la syntaxe ci-dessus -

- **map** est une fonction javascript qui associe une valeur à une clé et émet une paire clé-valeur.
- **reduce** est une fonction javascript qui réduit ou regroupe tous les documents ayant la même clé
- **out** spécifie l'emplacement du résultat de la requête map-reduce
- **query** spécifie les critères facultatifs de sélection des documents
- **sort** spécifie les critères de tri facultatifs
- **limit** spécifie le nombre maximum facultatif de documents à renvoyer

## Utilisation de MapReduce

Considérons la structure de document suivante qui stocke les messages des utilisateurs. Le document stocke le nom d'utilisateur de l'utilisateur et le statut du message.

```
{
    "post_text": "Microlead is an awesome website for E-learning",
    "user_name": "mark",
    "status":"active"
}
```

Maintenant, nous allons utiliser une fonction mapReduce sur notre collection de messages pour sélectionner tous les messages actifs, les regrouper sur la base du nom de l'utilisateur et ensuite compter le nombre de messages de chaque utilisateur en utilisant le code suivant -.

```
>db.posts.mapReduce( 
    function() { emit(this.user_id,1); }, 

    function(key, values) {return Array.sum(values)}, {  
        query:{status:"active"},  
        out:"post_total" 
    }
)
```

La requête mapReduce ci-dessus produit le résultat suivant -

```
{
    "result" : "post_total",
    "timeMillis" : 9,
    "counts" : {
        "input" : 4,
        "emit" : 4,
        "reduce" : 2,
        "output" : 2
    },
    "ok" : 1,
}
```

Le résultat montre qu'un total de 4 documents correspond à la requête (status : "active"), la fonction map a émis 4 documents avec des paires clé-valeur et enfin la fonction reduce a regroupé les documents mappés ayant les mêmes clés en 2.

Pour voir le résultat de cette requête mapReduce, utilisez l'opérateur find -

```
>db.posts.mapReduce( 
    function() { emit(this.user_id,1); }, 
    function(key, values) {return Array.sum(values)}, {  
        query:{status:"active"},  
        out:"post_total" 
    }
).find()
```

La requête ci-dessus donne le résultat suivant qui indique que les utilisateurs tom et mark ont deux messages dans des états actifs -

```
{ "_id" : "tom", "value" : 2 }
{ "_id" : "mark", "value" : 2 }
```

De la même manière, les requêtes MapReduce peuvent être utilisées pour construire de grandes requêtes d'agrégation complexes. L'utilisation de fonctions Javascript personnalisées fait appel à MapReduce, qui est très flexible et puissant.