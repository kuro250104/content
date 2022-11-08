La clause "**INDEXED BY** index-name" spécifie que l'index nommé doit être utilisé afin de rechercher des valeurs dans la table précédente.

Si nom-index n'existe pas ou ne peut pas être utilisé pour la requête, la préparation de la déclaration SQLite échoue.

La clause "**NOT INDEXED**" spécifie qu'aucun index ne doit être utilisé pour accéder à la table précédente, y compris les index implicites créés par les contraintes UNIQUE et PRIMARY KEY.

Cependant, la CLÉ PRIMAIRE INTÉGRALE peut toujours être utilisée pour rechercher des entrées même lorsque "**NOT INDEXED**" est spécifié.

## Syntaxe

Voici la syntaxe de la clause **INDEXED BY**, qui peut être utilisée avec les instructions **DELETE**, **UPDATE** ou **SELECT**.

```sql
SELECT|DELETE|UPDATE column1, column2...
INDEXED BY (index_name)
table_name
WHERE (CONDITION);
```

## Example

Considérons la table COMPANY Nous allons créer un index et l'utiliser pour effectuer l'opération INDEXED BY.

```sql
sqlite> CREATE INDEX salary_index ON COMPANY(salary);
sqlite>
```

Maintenant, pour sélectionner les données de la table COMPANY, vous pouvez utiliser la clause INDEXED BY comme suit -

```sql
sqlite> SELECT * FROM COMPANY INDEXED BY salary_index WHERE salary > 5000;
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
7           James       24          Houston     10000.0
2           Allen       25          Texas       15000.0
1           Paul        32          California  20000.0
3           Teddy       23          Norway      20000.0
6           Kim         22          South-Hall  45000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```