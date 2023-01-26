L'instruction PostgreSQL **INSERT INTO** permet d'insérer de nouvelles lignes dans une table. On peut insérer une seule ligne à la fois ou plusieurs lignes comme résultat d'une requête.

## Syntaxe

La syntaxe de base de l'instruction **INSERT INTO** est la suivante :

```sql
INSERT INTO TABLE_NAME (column1, column2, column3,...columnN)
VALUES (value1, value2, value3,...valueN);
```

- Ici, colonne1, colonne2,...colonneN sont les noms des colonnes de la table dans laquelle vous voulez insérer des données.
- Les noms des colonnes cibles peuvent être énumérés dans n'importe quel ordre. Les valeurs fournies par la clause VALUES ou la requête sont associées à la liste explicite ou implicite des colonnes de gauche à droite.

Il n'est pas nécessaire de préciser le nom de la ou des colonnes dans la requête SQL si vous ajoutez des valeurs pour toutes les colonnes de la table. Cependant, assurez-vous que l'ordre des valeurs est le même que celui des colonnes de la table. La syntaxe de la requête SQL **INSERT INTO** serait la suivante :

```sql
INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);
```

## Output

Le tableau suivant résume les messages de sortie et leur signification :

**Message de sortie et description**

- **INSERT oid 1** - Message renvoyé si une seule ligne a été insérée. oid est l'OID numérique de la ligne insérée.
- **INSERT 0 #** - Message renvoyé si plus d'une ligne a été insérée. # est le nombre de lignes insérées.

## Exemples

Créons la table COMPANY dans ```testdb``` comme suit :

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL,
    JOIN_DATE	  DATE
);
```

L'exemple suivant insère une ligne dans la table SOCIÉTÉ :

```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (1, 'Paul', 32, 'California', 20000.00,'2001-07-13');
```

L'exemple suivant permet d'insérer une ligne ; ici la colonne salaire est omise et elle aura donc la valeur par défaut :

```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,JOIN_DATE) VALUES (2, 'Allen', 25, 'Texas', '2007-12-13');
```

L'exemple suivant utilise la clause **DEFAULT** pour la colonne **JOIN_DATE** au lieu de spécifier une valeur :

```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (3, 'Teddy', 23, 'Norway', 20000.00, DEFAULT );
```

L'exemple suivant insère plusieurs lignes à l'aide de la syntaxe **VALUES** multi-rangées :

```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00, '2007-12-13' ), (5, 'David', 27, 'Texas', 85000.00, '2007-12-13');
```

Toutes les instructions ci-dessus créent les enregistrements suivants dans la table COMPANY :

```bash
ID        NAME        AGE        ADDRESS     SALARY	  JOIN_DATE
----      ----------  -----      ----------  -------      --------
1         Paul        32         California  20000.0      2001-07-13
2         Allen       25         Texas                    2007-12-13
3         Teddy       23         Norway      20000.0
4         Mark        25         Rich-Mond   65000.0      2007-12-13
5         David       27         Texas       85000.0      2007-12-13
```
