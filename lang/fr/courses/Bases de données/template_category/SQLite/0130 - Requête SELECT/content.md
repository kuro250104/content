## Introduction

L'instruction SQLite **SELECT** est utilisée pour extraire les données d'une table de base de données SQLite qui renvoie les données sous la forme d'un tableau de résultats. Ces tableaux de résultats sont également appelés **result sets**.

## Syntaxe

Voici la syntaxe de base de l'instruction SQLite SELECT.

```sql
SELECT column1, column2, columnN FROM table_name;
```

Ici, column1, column2 ... sont les champs d'une table, dont vous voulez récupérer les valeurs. Si vous voulez récupérer tous les champs disponibles dans le champ, vous pouvez utiliser la syntaxe suivante -

```sql
SELECT * FROM table_name;
```

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

Voici un exemple pour récupérer et afficher tous ces enregistrements à l'aide de l'instruction SELECT. Ici, les trois premières commandes ont été utilisées pour obtenir une sortie correctement formatée.

```sql
sqlite>.header on
sqlite>.mode column
sqlite> SELECT * FROM COMPANY;
```

Enfin, vous obtiendrez le résultat suivant.

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

Si vous souhaitez récupérer uniquement les champs sélectionnés de la table COMPANY, utilisez la requête suivante -

```sql
sqlite> SELECT ID, NAME, SALARY FROM COMPANY;
```

La requête ci-dessus produira le résultat suivant.

```bash
ID          NAME        SALARY
----------  ----------  ----------
1           Paul        20000.0
2           Allen       15000.0
3           Teddy       20000.0
4           Mark        65000.0
5           David       85000.0
6           Kim         45000.0
7           James       10000.0
```

## Réglage de la largeur des colonnes de sortie

Parfois, vous serez confronté à un problème lié à la sortie tronquée dans le cas de la ```.mode column``` qui se produit en raison de la largeur par défaut de la colonne à afficher. Ce que vous pouvez faire, c'est définir la largeur de la colonne à afficher à l'aide de la commande ```.width num, num....```, comme suit -

```sql
sqlite>.width 10, 20, 10
sqlite>SELECT * FROM COMPANY;
```

La commande ```.width``` ci-dessus définit la largeur de la première colonne à 10, la largeur de la deuxième colonne à 20 et la largeur de la troisième colonne à 10. Enfin, l'instruction **SELECT** ci-dessus donnera le résultat suivant.

```bash
ID          NAME                  AGE         ADDRESS     SALARY
----------  --------------------  ----------  ----------  ----------
1           Paul                  32          California  20000.0
2           Allen                 25          Texas       15000.0
3           Teddy                 23          Norway      20000.0
4           Mark                  25          Rich-Mond   65000.0
5           David                 27          Texas       85000.0
6           Kim                   22          South-Hall  45000.0
7           James                 24          Houston     10000.0
```

## Informations sur les schémas

Comme toutes les commandes dot sont disponibles à l'invite SQLite, en programmant avec SQLite, vous utiliserez l'instruction **SELECT** suivante avec la table **sqlite_master** pour répertorier toutes les tables créées dans votre base de données.

```sql
sqlite> SELECT tbl_name FROM sqlite_master WHERE type = 'table';
```

En supposant que vous n'avez qu'une table COMPANY dans votre testDB.db, cela produira le résultat suivant.

```bash
tbl_name
----------
COMPANY
```

Voici une liste d'informations complètes sur le tableau de la SOCIÉTÉ : - le tableau de la SOCIÉTÉ.

```sql
sqlite> SELECT sql FROM sqlite_master WHERE type = 'table' AND tbl_name = 'COMPANY';
```

En supposant que vous n'avez qu'une table COMPANY dans votre testDB.db, cela produira le résultat suivant.

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
)
```