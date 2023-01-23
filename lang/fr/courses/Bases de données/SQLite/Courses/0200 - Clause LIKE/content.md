L'opérateur LIKE de SQLite est utilisé pour faire correspondre des valeurs de texte à un modèle en utilisant des caractères génériques. Si l'expression recherchée peut être comparée à l'expression du modèle, l'opérateur LIKE renvoie true, c'est-à-dire 1. Deux jokers sont utilisés en conjonction avec l'opérateur LIKE : - l'opérateur LIKE est utilisé pour rechercher des valeurs de texte.

- Le signe de pourcentage (%)
- Le trait de soulignement (_)

Le signe pour cent représente zéro, un ou plusieurs chiffres ou caractères. Le trait de soulignement représente un seul chiffre ou caractère. Ces symboles peuvent être utilisés en combinaison.

## Syntaxe

Voici la syntaxe de base de % et _.

```sql
SELECT FROM table_name
WHERE column LIKE 'XXXX%'
or 
SELECT FROM table_name
WHERE column LIKE '%XXXX%'
or
SELECT FROM table_name
WHERE column LIKE 'XXXX_'
or
SELECT FROM table_name
WHERE column LIKE '_XXXX'
or
SELECT FROM table_name
WHERE column LIKE '_XXXX_'
```

Vous pouvez combiner un nombre N de conditions en utilisant les opérateurs AND ou OR. Ici, XXXX peut être une valeur numérique ou une chaîne de caractères.

## Exemple

Le tableau suivant présente un certain nombre d'exemples de parties WHERE comportant différentes clauses LIKE avec les opérateurs '%' et '_'.*

**Déclaration et description**

- ```WHERE SALARY LIKE '200%'``` - Trouve toutes les valeurs qui commencent par 200.
- ```WHERE SALARY LIKE '%200%'``` - Trouve toutes les valeurs qui ont 200 dans n'importe quelle position.
- ```WHERE SALARY LIKE '_00%'``` - Trouve toutes les valeurs qui ont 00 en deuxième et troisième positions.
- ```WHERE SALARY LIKE '2 _%_%'``` - Trouve toutes les valeurs qui commencent par 2 et qui ont au moins 3 caractères de long.
- ```WHERE SALARY LIKE '%2'``` - Trouve toutes les valeurs qui se terminent par 2.
- ```WHERE SALARY LIKE '_2%3'``` - Trouve toutes les valeurs qui ont un 2 en deuxième position et qui se terminent par un 3.
- ```WHERE SALARY LIKE '2___3'``` - Trouve toutes les valeurs dans un nombre à cinq chiffres qui commence par 2 et se termine par 3.

Prenons un exemple réel, considérons une table de l'entreprise avec les enregistrements suivants.

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

Voici un exemple qui affichera tous les enregistrements de la table SOCIÉTÉ dont l'âge commence par 2.

```sql
sqlite> SELECT * FROM COMPANY WHERE AGE LIKE '2%';
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

Voici un exemple qui affichera tous les enregistrements de la table SOCIÉTÉ où ADRESSE aura un trait d'union (-) dans le texte.

```sql
sqlite> SELECT * FROM COMPANY WHERE ADDRESS LIKE '%-%';
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           Mark        25          Rich-Mond   65000.0
6           Kim         22          South-Hall  45000.0
```
