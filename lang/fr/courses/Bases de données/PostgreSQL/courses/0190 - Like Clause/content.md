L'opérateur **LIKE** de PostgreSQL est utilisé pour faire correspondre des valeurs de texte à un modèle en utilisant des caractères génériques. Si l'expression recherchée peut être comparée à l'expression du motif, l'opérateur **LIKE** renvoie true, c'est-à-dire 1.

Il y a deux jokers utilisés en conjonction avec l'opérateur **LIKE** :

- L'expression de recherche et l'expression de motif.
- Le signe de pourcentage (%)
- Le trait de soulignement (_)

Le signe pour cent représente zéro, un ou plusieurs chiffres ou caractères. Le trait de soulignement représente un seul chiffre ou caractère. Ces symboles peuvent être utilisés en combinaison.

Si l'un de ces deux signes n'est pas utilisé en conjonction avec la clause **LIKE**, celle-ci se comporte comme l'opérateur égal.

## Syntaxe

La syntaxe de base de ```%``` et ```_``` est la suivante :

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

Vous pouvez combiner un nombre N de conditions en utilisant les opérateurs **AND** ou **OR**. Ici, XXXX peut être une valeur numérique ou une chaîne de caractères.

## Exemple

Voici plusieurs exemples montrant que la partie **WHERE** comporte une clause **LIKE** différente avec les opérateurs ```%``` et ```_```.

**Déclaration et description**

- ```WHERE SALARY::text LIKE '200%'``` - Trouve toutes les valeurs qui commencent par 200.
- ```WHERE SALARY::text LIKE '%200%'``` - Trouve toutes les valeurs qui ont 200 dans n'importe quelle position.
- ```WHERE SALARY::text LIKE '_00%'``` - Trouve toutes les valeurs qui ont 00 en deuxième et troisième positions.
- ```WHERE SALARY::text LIKE '2_%_%'``` - Trouve toutes les valeurs qui commencent par 2 et qui ont au moins 3 caractères de long.
- ```WHERE SALARY::text LIKE '%2'``` - Trouve toutes les valeurs qui se terminent par 2.
- ```WHERE SALARY::text LIKE '_2%3'``` - Trouve toutes les valeurs qui ont 2 en deuxième position et qui se terminent par un 3.
- ```WHERE SALARY::text LIKE '2___3'``` - Trouve toutes les valeurs d'un nombre à cinq chiffres qui commencent par 2 et finissent par 3.

La fonction **LIKE** de Postgres permet uniquement de comparer des chaînes de caractères. Par conséquent, nous devons explicitement convertir la colonne entière en chaîne de caractères comme dans les exemples ci-dessus.

Prenons un exemple réel, considérons la table SOCIÉTÉ, qui contient les enregistrements suivants :

```bash
# select * from COMPANY;
 id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
(7 rows)
```

L'exemple suivant affiche tous les enregistrements de la table SOCIÉTÉ dont l'âge commence par 2 :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE::text LIKE '2%' ;
```

Cela donnerait le résultat suivant :

```bash
id | name  | age | address     | salary
----+-------+-----+-------------+--------
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
  6 | Kim   |  22 | South-Hall  |  45000
  7 | James |  24 | Houston     |  10000
  8 | Paul  |  24 | Houston     |  20000
(7 rows)
```

Voici un exemple qui affichera tous les enregistrements de la table SOCIÉTÉ où ADRESSE aura un trait d'union (-) dans le texte :

```sql
testdb=# SELECT * FROM COMPANY WHERE ADDRESS  LIKE '%-%';
```

Cela donnerait le résultat suivant :

```bash
id | name | age |                      address              | salary
----+------+-----+-------------------------------------------+--------
  4 | Mark |  25 | Rich-Mond                                 |  65000
  6 | Kim  |  22 | South-Hall                                |  45000
(2 rows)
```
