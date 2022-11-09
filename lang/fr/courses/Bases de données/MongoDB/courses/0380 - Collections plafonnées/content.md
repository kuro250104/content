Les collections plafonnées sont des collections circulaires de taille fixe qui suivent l'ordre d'insertion afin d'offrir des performances élevées pour les opérations de création, de lecture et de suppression. Par circulaire, cela signifie que lorsque la taille fixe allouée à la collection est épuisée, elle commence à supprimer le document le plus ancien de la collection sans fournir de commande explicite.

Les collections plafonnées limitent les mises à jour des documents si la mise à jour entraîne une augmentation de la taille du document. Comme les collections plafonnées stockent les documents dans l'ordre du stockage sur le disque, elles garantissent que la taille du document n'augmente pas la taille allouée sur le disque. Les collections plafonnées sont idéales pour stocker des informations de journal, des données de cache ou tout autre volume de données élevé.

## Création d'une collection plafonnée

Pour créer une collection plafonnée, nous utilisons la commande normale createCollection mais avec l'option plafonnée à true et en spécifiant la taille maximale de la collection en octets.

```
>db.createCollection("cappedLogCollection",{capped:true,size:10000})
```

En plus de la taille de la collection, nous pouvons également limiter le nombre de documents dans la collection en utilisant le paramètre max -.

```
>db.createCollection("cappedLogCollection",{capped:true,size:10000,max:1000})
```

Si vous voulez vérifier si une collection est plafonnée ou non, utilisez la commande isCapped suivante : -.

```
>db.cappedLogCollection.isCapped()
```

Si vous envisagez de convertir une collection existante en une collection plafonnée, vous pouvez le faire avec le code suivant -

```
>db.runCommand({"convertToCapped":"posts",size:10000})
```

Ce code convertirait nos postes de collecte existants en une collecte plafonnée.

## Interrogation d'une collection plafonnée

Par défaut, une requête de recherche sur une collection plafonnée affichera les résultats dans l'ordre d'insertion. Mais si vous souhaitez que les documents soient récupérés dans l'ordre inverse, utilisez la commande sort comme le montre le code suivant -

```
>db.cappedLogCollection.find().sort({$natural:-1})
```

Il y a quelques autres points importants concernant les collections plafonnées qui méritent d'être connus.
- Nous ne pouvons pas supprimer les documents d'une collection plafonnée.
- Il n'y a pas d'index par défaut dans une collection plafonnée, pas même sur le champ _id.
- Lors de l'insertion d'un nouveau document, MongoDB n'a pas besoin de chercher un emplacement pour le nouveau document sur le disque. Il peut insérer aveuglément le nouveau document à la fin de la collection. Cela rend les opérations d'insertion dans les collections plafonnées très rapides.
- De même, lors de la lecture de documents, MongoDB renvoie les documents dans l'ordre où ils se trouvent sur le disque. Cela rend l'opération de lecture très rapide.