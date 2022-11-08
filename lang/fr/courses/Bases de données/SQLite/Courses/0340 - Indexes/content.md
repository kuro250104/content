Les index sont des tables de consultation spéciales que le moteur de recherche de la base de données peut utiliser pour accélérer la récupération des données. En termes simples, un **index** est un pointeur vers les données d'une table. Un index dans une base de données est très similaire à un index à la fin d'un livre.

Par exemple, si vous souhaitez faire référence à toutes les pages d'un livre traitant d'un certain sujet, vous consultez d'abord l'index, qui répertorie tous les sujets par ordre alphabétique, puis vous vous référez à un ou plusieurs numéros de page spécifiques.

Un index permet d'accélérer les requêtes SELECT et les clauses WHERE, mais il ralentit la saisie des données, avec les instructions UPDATE et INSERT. Les index peuvent être créés ou supprimés sans effet sur les données.

La création d'un index implique l'instruction CREATE INDEX, qui vous permet de nommer l'index, de spécifier la table et la ou les colonnes à indexer, et d'indiquer si l'index est dans un ordre croissant ou décroissant.

Les index peuvent également être uniques, comme la contrainte UNIQUE, en ce sens que l'index empêche les entrées en double dans la colonne ou la combinaison de colonnes sur laquelle il y a un index.

## La commande CREATE INDEX

Voici la syntaxe de base de **CREATE INDEX**.

```sql
CREATE INDEX index_name ON table_name;
```

## Single-Column Indexes

Un index à colonne unique est un index créé sur la base d'une seule colonne de la table. La syntaxe de base est la suivante -

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

## Unique Indexes

Les index uniques sont utilisés non seulement pour les performances, mais aussi pour l'intégrité des données. Un index unique ne permet pas l'insertion de valeurs en double dans la table. La syntaxe de base est la suivante : -

```sql
CREATE UNIQUE INDEX index_name
on table_name (column_name);
```

## Composite Indexes

Un index composite est un index sur deux ou plusieurs colonnes d'une table. La syntaxe de base est la suivante -

```sql
CREATE INDEX index_name
on table_name (column1, column2);
```

Qu'il s'agisse de créer un index à une seule colonne ou un index composite, prenez en considération la ou les colonnes que vous risquez d'utiliser très fréquemment dans la clause WHERE d'une requête comme conditions de filtrage.

Si une seule colonne est utilisée, il faut choisir un index à une seule colonne. Si deux colonnes ou plus sont fréquemment utilisées comme filtres dans la clause WHERE, l'index composite est le meilleur choix.

## Implicit Indexes

Les index implicites sont des index qui sont automatiquement créés par le serveur de base de données lorsqu'un objet est créé. Les index sont automatiquement créés pour les contraintes de clé primaire et les contraintes uniques.

Voici un exemple dans lequel nous allons créer un index dans la table SOCIÉTÉ pour la colonne salaire.

```sql
sqlite> CREATE INDEX salary_index ON COMPANY (salary);
```

Maintenant, dressons la liste de tous les indices disponibles dans la table COMPANY en utilisant la commande .indices, comme suit -

```sql
sqlite> .indices COMPANY
```

Cela produira le résultat suivant, où sqlite_autoindex_COMPANY_1 est un index implicite qui a été créé lorsque la table elle-même a été créée.

```sql
salary_index
sqlite_autoindex_COMPANY_1
```

Vous pouvez dresser la liste de tous les index de la base de données comme suit -

```sql
sqlite> SELECT * FROM sqlite_master WHERE type = 'index';
```

## La commande DROP INDEX

Un index peut être supprimé à l'aide de la commande DROP de SQLite. Il convient d'être prudent lors de l'abandon d'un index car les performances peuvent être ralenties ou améliorées.

La syntaxe de base est la suivante -

```sql
DROP INDEX index_name;
```

Vous pouvez utiliser l'instruction suivante pour supprimer un index précédemment créé.

```sql
sqlite> DROP INDEX salary_index;
```

### Quand faut-il éviter les indices ?

Bien que les index soient destinés à améliorer les performances d'une base de données, il y a des cas où ils doivent être évités. Les directives suivantes indiquent quand l'utilisation d'un index doit être reconsidérée.

Les index ne doivent pas être utilisés dans -

- Petites tables.
- Les tables font l'objet d'opérations fréquentes et importantes de mise à jour ou d'insertion par lots.
- Colonnes qui contiennent un nombre élevé de valeurs NULL.
- Les colonnes qui sont fréquemment manipulées.