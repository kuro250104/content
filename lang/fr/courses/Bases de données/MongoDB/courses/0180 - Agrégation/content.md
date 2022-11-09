Les opérations d'agrégation traitent les enregistrements de données et renvoient des résultats calculés. Les opérations d'agrégation regroupent les valeurs de plusieurs documents et peuvent effectuer diverses opérations sur les données regroupées pour renvoyer un seul résultat. En SQL, count(*) et avec group by est un équivalent de l'agrégation MongoDB.

## La méthode aggregate()

Pour l'agrégation dans MongoDB, vous devez utiliser la méthode ```aggregate()```.

### Syntaxe

La syntaxe de base de la méthode ```aggregate()``` est la suivante -

```
>db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)
```

### Exemple

Dans la collection, vous avez les données suivantes -

```
{
   _id: ObjectId(7df78ad8902c)
   title: 'MongoDB Overview', 
   description: 'MongoDB is no sql database',
   by_user: 'Microlead',
   url: 'http://www.Microlead.fr,
   tags: ['mongodb', 'database', 'NoSQL'],
   likes: 100
},
{
   _id: ObjectId(7df78ad8902d)
   title: 'NoSQL Overview', 
   description: 'No sql database is very fast',
   by_user: 'Microlead',
   url: 'http://www.Microlead.fr,
   tags: ['mongodb', 'database', 'NoSQL'],
   likes: 10
},
{
   _id: ObjectId(7df78ad8902e)
   title: 'Neo4j Overview', 
   description: 'Neo4j is no sql database',
   by_user: 'Neo4j',
   url: 'http://www.neo4j.com',
   tags: ['neo4j', 'database', 'NoSQL'],
   likes: 750
}
```

Maintenant, à partir de la collection ci-dessus, si vous voulez afficher une liste indiquant combien de tutoriels ont été écrits par chaque utilisateur, alors vous utiliserez la méthode ```aggregate()``` suivante : -

```
> db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : 1}}}])
{ "_id" : “Microlead", "num_tutorial" : 2 }
{ "_id" : "Neo4j", "num_tutorial" : 1 }
>
```

La requête Sql équivalente pour le cas d'utilisation ci-dessus sera ```select by_user, count(*) from mycol group by_user```.

Dans l'exemple ci-dessus, nous avons regroupé les documents par le champ by_user et à chaque occurrence de by user, la valeur précédente de la somme est incrémentée. Vous trouverez ci-dessous une liste des expressions d'agrégation disponibles.

| **Expression** | **Description** | **Exemple** |
| --- | --- | --- |
| ```$sum``` | Additionne la valeur définie de tous les documents de la collection. | ```db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$sum : "$likes"}}}])``` |
| ```$avg``` | Calcule la moyenne de toutes les valeurs données de tous les documents de la collection. | ```db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$avg : "$likes"}}}])``` |
| ```$min``` | Obtient le minimum des valeurs correspondantes de tous les documents de la collection. | ```db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$min : "$likes"}}}])``` |
| ```$max``` | Obtient le maximum des valeurs correspondantes de tous les documents de la collection. | ```db.mycol.aggregate([{$group : {_id : "$by_user", num_tutorial : {$max : "$likes"}}}])``` |
| ```$push``` | Insère la valeur dans un tableau dans le document résultant. | ```db.mycol.aggregate([{$group : {_id : "$by_user", url : {$push: "$url"}}}])``` |
| ```$addToSet``` | Insère la valeur dans un tableau dans le document résultant mais ne crée pas de doublons. | ```db.mycol.aggregate([{$group : {_id : "$by_user", url : {$addToSet : "$url"}}}])``` |
| ```$first``` | Récupère le premier document des documents sources en fonction du regroupement. En général, cela n'a de sens qu'avec une étape "$sort" appliquée précédemment. | ```db.mycol.aggregate([{$group : {_id : "$by_user", first_url : {$first : "$url"}}}])``` |
| ```$last``` | Récupère le dernier document des documents sources en fonction du regroupement. En général, cela n'a de sens qu'avec une étape "$sort" appliquée précédemment. | ```db.mycol.aggregate([{$group : {_id : "$by_user", last_url : {$last : "$url"}}}])``` |

## Concept de pipeline

Dans les commandes UNIX, le pipeline shell signifie la possibilité d'exécuter une opération sur une entrée et d'utiliser la sortie comme entrée pour la commande suivante et ainsi de suite. MongoDB prend également en charge le même concept dans le cadre de l'agrégation. Il existe un ensemble d'étapes possibles et chacune d'entre elles est prise comme un ensemble de documents en entrée et produit un ensemble de documents (ou le document JSON final à la fin du pipeline). Celui-ci peut ensuite être utilisé à son tour pour l'étape suivante et ainsi de suite.

Voici les étapes possibles dans le cadre de l'agrégation.

- ```$project``` − Utilisé pour sélectionner certains champs spécifiques dans une collection.
- ```$match``` − Il s'agit d'une opération de filtrage, ce qui permet de réduire le nombre de documents qui sont transmis à l'étape suivante.
- ```$group``` − C'est elle qui effectue l'agrégation réelle, comme indiqué ci-dessus.
- ```$sort``` − Trie les documents.
- ```$skip``` − Il est ainsi possible d'avancer dans la liste des documents pour un nombre donné de documents.
- ```$limit``` − Cela limite le nombre de documents à examiner, par le nombre donné en partant des positions actuelles.
- ```$unwind``` − Cette opération est utilisée pour dérouler les documents qui utilisent des tableaux. Lors de l'utilisation d'un tableau, les données sont en quelque sorte pré-jointes et cette opération sera annulée pour obtenir à nouveau des documents individuels. Ainsi, avec cette étape, nous augmenterons la quantité de documents pour l'étape suivante.