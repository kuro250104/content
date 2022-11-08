Malheureusement, nous n'avons pas de commande **TRUNCATE TABLE** en SQLite mais vous pouvez utiliser la commande SQLite **DELETE** pour supprimer les données complètes d'une table existante, bien qu'il soit recommandé d'utiliser la commande DROP TABLE pour supprimer la table complète et la recréer à nouveau.

## Syntaxe

Voici la syntaxe de base de la commande **DELETE**.

```sql
sqlite> DELETE FROM table_name;
```

Voici la syntaxe de base de **DROP TABLE**.

```sql
sqlite> DROP TABLE table_name;
```

Si vous utilisez la commande **DELETE TABLE** pour supprimer tous les enregistrements, il est recommandé d'utiliser la commande **VACUUM** pour vider l'espace inutilisé.

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

L'exemple suivant permet de tronquer le tableau ci-dessus.

```sql
SQLite> DELETE FROM COMPANY;
SQLite> VACUUM;
```

Maintenant, la table COMPANY est complètement tronquée et rien ne sera produit par l'instruction **SELECT**.