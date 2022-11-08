L'instruction SQLite peut être précédée du mot clé "EXPLAIN" ou de l'expression "EXPLAIN QUERY PLAN" utilisée pour décrire les détails d'une table.

L'une ou l'autre de ces modifications fait que la déclaration SQLite se comporte comme une requête et renvoie des informations sur la façon dont la déclaration SQLite aurait fonctionné si le mot-clé ou la phrase EXPLAIN avait été omis.

- La sortie de EXPLAIN et EXPLAIN QUERY PLAN est destinée à l'analyse interactive et au dépannage uniquement.
- Les détails du format de sortie sont susceptibles de changer d'une version de SQLite à l'autre.
- Les applications ne devraient pas utiliser EXPLAIN ou EXPLAIN QUERY PLAN car leur comportement exact est variable et seulement partiellement documenté.

## Syntaxe

La syntaxe d'EXPLAIN est la suivante : -.

```sql
EXPLAIN [SQLite Query]
```

La syntaxe d'EXPLAIN QUERY PLAN est la suivante : -.

```sql
EXPLAIN  QUERY PLAN [SQLite Query]
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

Maintenant, vérifions la sous-requête suivante avec l'instruction SELECT -

```sql
sqlite> EXPLAIN SELECT * FROM COMPANY WHERE Salary >= 20000;
```

Cela donnera le résultat suivant.

```bash
addr        opcode      p1          p2          p3
----------  ----------  ----------  ----------  ----------
0           Goto        0           19
1           Integer     0           0
2           OpenRead    0           8
3           SetNumColu  0           5
4           Rewind      0           17
5           Column      0           4
6           RealAffini  0           0
7           Integer     20000       0
8           Lt          357         16          collseq(BI
9           Rowid       0           0
10          Column      0           1
11          Column      0           2
12          Column      0           3
13          Column      0           4
14          RealAffini  0           0
15          Callback    5           0
16          Next        0           5
17          Close       0           0
18          Halt        0           0
19          Transactio  0           0
20          VerifyCook  0           38
21          Goto        0           1
22          Noop        0           0
```

Maintenant, vérifions le **Explain Query Plan** suivant avec l'instruction SELECT -

```bash
SQLite> EXPLAIN QUERY PLAN SELECT * FROM COMPANY WHERE Salary >= 20000;

order       from        detail
----------  ----------  -------------
0           0           TABLE COMPANY
```