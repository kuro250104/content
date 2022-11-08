SQLite possède de nombreuses fonctions intégrées pour effectuer des traitements sur des chaînes de caractères ou des données numériques. Vous trouverez ci-dessous une liste de quelques fonctions SQLite intégrées utiles. Toutes sont sensibles à la casse, ce qui signifie que vous pouvez utiliser ces fonctions soit en minuscules, soit en majuscules, soit sous une forme mixte. Pour plus de détails, vous pouvez consulter la documentation officielle de SQLite.

**Fonction et description**

- **SQLite COUNT Function** - La fonction agrégée COUNT de SQLite est utilisée pour compter le nombre de lignes dans une table de base de données.
- **SQLite MAX Function** - La fonction d'agrégation MAX de SQLite nous permet de sélectionner la valeur la plus élevée (maximale) pour une certaine colonne.
- **SQLite MIN Function** - La fonction d'agrégation MIN de SQLite nous permet de sélectionner la valeur la plus basse (minimale) pour une certaine colonne.
- **SQLite AVG Function** - La fonction d'agrégation AVG de SQLite sélectionne la valeur moyenne pour une certaine colonne de la table.
- **SQLite SUM Function** - La fonction d'agrégation SUM de SQLite permet de sélectionner le total d'une colonne numérique.
- **SQLite RANDOM Function** - La fonction RANDOM de SQLite retourne un entier pseudo-aléatoire entre -9223372036854775808 et +9223372036854775807.
- **SQLite ABS Function** - La fonction SQLite ABS renvoie la valeur absolue de l'argument numérique.
- **SQLite UPPER Function** - La fonction UPPER de SQLite convertit une chaîne de caractères en lettres majuscules.
- **SQLite LOWER Function** - La fonction SQLite LOWER convertit une chaîne de caractères en lettres minuscules.
- **SQLite LENGTH Function** - La fonction SQLite LENGTH renvoie la longueur d'une chaîne de caractères.
- **SQLite sqlite_version Function** - La fonction sqlite_version de SQLite renvoie la version de la bibliothèque SQLite.

Avant de commencer à donner des exemples sur les fonctions susmentionnées, considérons une table de la SOCIETE avec les enregistrements suivants.

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

## Fonction COUNT de SQLite

La fonction agrégée **COUNT** de SQLite est utilisée pour compter le nombre de lignes dans une table de base de données. Voici un exemple -

```sql
sqlite> SELECT count(*) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```bash
count(*)
----------
7
```

## Fonction MAX de SQLite

La fonction d'agrégation **MAX** de SQLite nous permet de sélectionner la valeur la plus élevée (maximale) pour une certaine colonne. Voici un exemple -

```sql
sqlite> SELECT max(salary) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```bash
max(salary)
-----------
85000.0
```

## Fonction MIN de SQLite

La fonction d'agrégation **MIN** de SQLite nous permet de sélectionner la valeur la plus basse (minimale) pour une certaine colonne. Voici un exemple -

```sql
sqlite> SELECT min(salary) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```bash
min(salary)
-----------
10000.0
```

## Fonction AVG SQLite

La fonction d'agrégation **AVG** de SQLite sélectionne la valeur moyenne pour une certaine colonne de la table. Voici un exemple -

```sql
sqlite> SELECT avg(salary) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```sql
avg(salary)
----------------
37142.8571428572
```

## Fonction SUM de SQLite

La fonction d'agrégation **SUM** de SQLite permet de sélectionner le total d'une colonne numérique. Voici un exemple -

```sql
sqlite> SELECT sum(salary) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```sql
sum(salary)
-----------
260000.0
```

## Fonction RANDOM de SQLite

La fonction **RANDOM** de SQLite retourne un entier pseudo-aléatoire entre -9223372036854775808 et +9223372036854775807. Voici un exemple -

```sql
sqlite> SELECT random() AS Random;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```sql
Random
-------------------
5876796417670984050
```

## Fonction ABS SQLite

La fonction SQLite **ABS** renvoie la valeur absolue de l'argument numérique. Voici un exemple -

```sql
sqlite> SELECT abs(5), abs(-15), abs(NULL), abs(0), abs("ABC");
```

L'instruction SQLite ci-dessus produira ce qui suit.

```bash
abs(5)      abs(-15)    abs(NULL)   abs(0)      abs("ABC")
----------  ----------  ----------  ----------  ----------
5           15                      0           0.0
```

## Fonction SQLite UPPER

La fonction **UPPER** de SQLite convertit une chaîne de caractères en lettres majuscules. Voici un exemple -

```sql
sqlite> SELECT upper(name) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```bash
upper(name)
-----------
PAUL
ALLEN
TEDDY
MARK
DAVID
KIM
JAMES
```

## Fonction SQLite LOWER

La fonction SQLite **LOWER** convertit une chaîne de caractères en lettres minuscules. Voici un exemple -

```sql
sqlite> SELECT lower(name) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```sql
lower(name)
-----------
paul
allen
teddy
mark
david
kim
james
```

## Fonction SQLite LENGTH

La fonction SQLite **LENGTH** renvoie la longueur d'une chaîne de caractères. Voici un exemple -

```sql
sqlite> SELECT name, length(name) FROM COMPANY;
```

L'instruction SQLite ci-dessus produira ce qui suit.

```bash
NAME        length(name)
----------  ------------
Paul        4
Allen       5
Teddy       5
Mark        4
David       5
Kim         3
James       5
```

## Fonction SQLite sqlite_version

La fonction **sqlite_version** de SQLite renvoie la version de la bibliothèque SQLite. Voici un exemple -

```sql
sqlite> SELECT sqlite_version() AS 'SQLite Version';
```

L'instruction SQLite ci-dessus produira ce qui suit.

```bash
SQLite Version
--------------
3.6.20
```