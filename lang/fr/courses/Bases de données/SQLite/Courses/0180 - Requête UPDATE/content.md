## Introduction

La requête SQLite UPDATE est utilisée pour modifier les enregistrements existants dans une table. Vous pouvez utiliser la clause WHERE avec la requête UPDATE pour mettre à jour les lignes sélectionnées, sinon toutes les lignes seront mises à jour.

## Syntaxe

Voici la syntaxe de base d'une requête **UPDATE** avec la clause **WHERE**.


```sql
UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];
```

Vous pouvez combiner un nombre N de conditions en utilisant les opérateurs **AND** ou **OR**.

## Exemple

Considérons une table de l'entreprise avec les enregistrements suivants -

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

L'exemple suivant permet de mettre à jour l'ADRESSE d'un client dont l'ID est 6.

```sql
sqlite> UPDATE COMPANY SET ADDRESS = 'Texas' WHERE ID = 6;
```

Maintenant, la table SOCIÉTÉ aura les enregistrements suivants.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          Texas       45000.0
7           James       24          Houston     10000.0
```

Si vous voulez modifier toutes les valeurs des colonnes ADRESSE et SALAIRE dans la table SOCIÉTÉ, vous n'avez pas besoin d'utiliser la clause **WHERE** et la requête **UPDATE** sera la suivante -

```sql
sqlite> UPDATE COMPANY SET ADDRESS = 'Texas', SALARY = 20000.00;
```

Maintenant, la table SOCIÉTÉ aura les enregistrements suivants -

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          Texas       20000.0
2           Allen       25          Texas       20000.0
3           Teddy       23          Texas       20000.0
4           Mark        25          Texas       20000.0
5           David       27          Texas       20000.0
6           Kim         22          Texas       20000.0
7           James       24          Texas       20000.0
```