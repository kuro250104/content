Les index sont des tables de consultation spéciales que le moteur de recherche de la base de données peut utiliser pour accélérer la récupération des données. En termes simples, un index est un pointeur vers les données d'une table. Un index dans une base de données est très similaire à un index à la fin d'un livre.

Par exemple, si vous souhaitez faire référence à toutes les pages d'un livre traitant d'un certain sujet, vous devez d'abord consulter l'index, qui répertorie tous les sujets par ordre alphabétique, puis vous référer à un ou plusieurs numéros de page spécifiques.

Un index permet d'accélérer les requêtes **SELECT** et les clauses **WHERE** ; en revanche, il ralentit la saisie des données, avec les instructions **UPDATE** et **INSERT**. Les index peuvent être créés ou supprimés sans effet sur les données.

La création d'un index implique l'instruction **CREATE INDEX**, qui vous permet de nommer l'index, de spécifier la table et la ou les colonnes à indexer, et d'indiquer si l'index est en ordre croissant ou décroissant.

Les index peuvent également être uniques, comme la contrainte **UNIQUE**, en ce sens que l'index empêche les entrées en double dans la colonne ou la combinaison de colonnes sur laquelle il y a un index.

## The CREATE INDEX Command

La syntaxe de base de la commande **CREATE INDEX** est la suivante :

```sql
CREATE INDEX index_name ON table_name;
```

## Index Types

PostgreSQL fournit plusieurs types d'index : B-tree, Hash, GiST, SP-GiST et GIN. Chaque type d'index utilise un algorithme différent qui est mieux adapté à différents types de requêtes. Par défaut, la commande CREATE INDEX crée des index B-tree, qui conviennent aux situations les plus courantes.

### Single-Column Indexes

Un index à colonne unique est un index créé sur la base d'une seule colonne de la table. La syntaxe de base est la suivante :

```sql
CREATE INDEX index_name
ON table_name (column_name);
```

### Multicolumn Indexes

Un index multi colonne est défini sur plus d'une colonne d'une table. La syntaxe de base est la suivante :

```sql
CREATE INDEX index_name
ON table_name (column1_name, column2_name);
```

Qu'il s'agisse de créer un index à colonne unique ou un index multicolonne, il faut prendre en considération la ou les colonnes que vous risquez d'utiliser très fréquemment dans la clause **WHERE** d'une requête comme conditions de filtrage.

Si une seule colonne est utilisée, il convient de choisir un index à une seule colonne. Si deux colonnes ou plus sont fréquemment utilisées comme filtres dans la clause **WHERE**, l'index multicolonne est le meilleur choix.

## Unique Indexes

Les index uniques sont utilisés non seulement pour les performances, mais aussi pour l'intégrité des données. Un index unique ne permet pas l'insertion de valeurs en double dans la table. La syntaxe de base est la suivante :

```sql
CREATE UNIQUE INDEX index_name
on table_name (column_name);
```

## Partial Indexes

Un index partiel est un index construit sur un sous-ensemble d'une table ; le sous-ensemble est défini par une expression conditionnelle (appelée le prédicat de l'index partiel). L'index contient des entrées uniquement pour les lignes de la table qui satisfont le prédicat. La syntaxe de base est la suivante :

```sql
CREATE INDEX index_name
on table_name (conditional_expression);
```

## Implicit Indexes

Les index implicites sont des index qui sont automatiquement créés par le serveur de base de données lorsqu'un objet est créé. Les index sont automatiquement créés pour les contraintes de clé primaire et les contraintes uniques.

### Exemple

Voici un exemple dans lequel nous allons créer un index sur la table SOCIÉTÉ pour la colonne salaire :

```sql
# CREATE INDEX salary_index ON COMPANY (salary);
```

Maintenant, dressons la liste de tous les indices disponibles dans la table COMPANY en utilisant la commande ```\d``` company.

```sql
# \d company
```

Cela produira le résultat suivant, où ```company_pkey``` est un index implicite, qui a été créé lorsque la table a été créée :

```bash
      Table "public.company"
 Column  |     Type      | Modifiers
---------+---------------+-----------
 id      | integer       | not null
 name    | text          | not null
 age     | integer       | not null
 address | character(50) |
 salary  | real          |
Indexes:
    "company_pkey" PRIMARY KEY, btree (id)
    "salary_index" btree (salary)
```

Vous pouvez répertorier l'ensemble des index de la base de données en utilisant la commande ```\di``` :

## The DROP INDEX Command

Un index peut être abandonné en utilisant la commande **DROP** de PostgreSQL. Il faut faire attention lors de l'abandon d'un index car les performances peuvent être ralenties ou améliorées.

La syntaxe de base est la suivante :

```sql
DROP INDEX index_name;
```

Vous pouvez utiliser l'instruction suivante pour supprimer l'index précédemment créé :

```sql
# DROP INDEX salary_index;
```

## Quand faut-il éviter les index ?

Bien que les index soient destinés à améliorer les performances d'une base de données, il y a des moments où ils doivent être évités. Les directives suivantes indiquent quand l'utilisation d'un index doit être reconsidérée :

- Les index ne doivent pas être utilisés sur les petites tables.
- Les tables qui font l'objet de fréquentes et importantes opérations de mise à jour ou d'insertion par lots.
- Les index ne doivent pas être utilisés sur des colonnes qui contiennent un nombre élevé de valeurs NULL.
- Les colonnes qui sont fréquemment manipulées ne doivent pas être indexées.
