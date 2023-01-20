## Introduction

L'instruction SQLite **DROP TABLE** est utilisée pour supprimer la définition d'une table et toutes les données, index, déclencheurs, contraintes et spécifications de permission associés à cette table.

Vous devez être prudent lorsque vous utilisez cette commande car une fois qu'une table est supprimée, toutes les informations disponibles dans la table sont également perdues à jamais.

## Syntaxe

Voici la syntaxe de base de l'instruction DROP TABLE. Vous pouvez éventuellement spécifier le nom de la base de données en même temps que le nom de la table comme suit -

```sql
DROP TABLE database_name.table_name;
```

## Exemple

Vérifions d'abord la table COMPANY et ensuite nous la supprimerons de la base de données.

```sql
sqlite>.tables
COMPANY       test.COMPANY
```

Cela signifie que la table COMPANY est disponible dans la base de données, alors nous allons la déposer comme suit -

```sql
sqlite>DROP TABLE COMPANY;
sqlite>
```

Maintenant, si vous essayez la commande ```.tables```, vous ne trouverez plus la table COMPANY.

```sql
sqlite>.tables
sqlite>
```

Il ne montre rien, ce qui signifie que la table de votre base de données a été supprimée avec succès.
