La requête SQLite DELETE est utilisée pour supprimer les enregistrements existants d'une table. Vous pouvez utiliser la clause WHERE avec la requête DELETE pour supprimer les lignes sélectionnées, sinon tous les enregistrements seront supprimés.

## Syntaxe

Voici la syntaxe de base de la requête DELETE avec la clause WHERE.

```sql
DELETE FROM table_name
WHERE [condition];
```

Vous pouvez combiner un nombre N de conditions en utilisant les opérateurs **AND** ou **OR**.

## Exemple

Considérons une table de l'entreprise avec les enregistrements suivants.

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

L'exemple suivant permet de SUPPRIMER un client dont l'ID est 7.

```sql
sqlite> DELETE FROM COMPANY WHERE ID = 7;
```

Maintenant, la table COMPANY aura les enregistrements suivants.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
```

Si vous voulez SUPPRIMER tous les enregistrements de la table SOCIÉTÉ, vous n'avez pas besoin d'utiliser la clause **WHERE** avec la requête SUPPRIMER, qui sera la suivante : -.

```sql
sqlite> DELETE FROM COMPANY;
```

Maintenant, la table COMPANY ne contient plus d'enregistrement car tous les enregistrements ont été supprimés par l'instruction **DELETE**.