Les fonctions PostgreSQL, également connues sous le nom de procédures stockées, vous permettent d'effectuer des opérations qui prendraient normalement plusieurs requêtes et allers-retours dans une seule fonction au sein de la base de données. Les fonctions permettent la réutilisation de la base de données car d'autres applications peuvent interagir directement avec vos procédures stockées au lieu de passer par un intermédiaire ou de dupliquer le code.

Les fonctions peuvent être créées dans le langage de votre choix comme SQL, PL/pgSQL, C, Python, etc.

## Syntaxe

La syntaxe de base pour créer une fonction est la suivante :

```sql
CREATE [OR REPLACE] FUNCTION function_name (arguments) 
RETURNS return_datatype AS $variable_name$
    DECLARE
        declaration;
        [...]
    BEGIN
        < function_body >
        [...]
        RETURN { variable_name | value }
    END; LANGUAGE plpgsql;
```

Où,

- nom-fonction spécifie le nom de la fonction.
- L'option [OR REPLACE] permet de modifier une fonction existante.
- La fonction doit contenir une clause de retour.
- La clause RETURN spécifie le type de données que vous allez retourner à partir de la fonction. Le type de données retourné peut être un type de base, composite ou de domaine, ou peut faire référence au type d'une colonne de table.
- function-body contient la partie exécutable.
- Le mot-clé AS est utilisé pour créer une fonction autonome.
- plpgsql est le nom du langage dans lequel la fonction est implémentée. Ici, nous utilisons cette option pour PostgreSQL, cela peut être SQL, C, interne, ou le nom d'un langage procédural défini par l'utilisateur. Pour des raisons de compatibilité ascendante, le nom peut être entouré de guillemets simples.

## Exemple

L'exemple suivant illustre la création et l'appel d'une fonction autonome. Cette fonction renvoie le nombre total d'enregistrements dans la table SOCIÉTÉ. Nous utilisons la table SOCIÉTÉ, qui contient les enregistrements suivants :

```bash
testdb# select * from COMPANY;
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

La fonction ```totalRecords()``` se présente comme suit :

```sql
CREATE OR REPLACE FUNCTION totalRecords ()
RETURNS integer AS $total$
declare
	total integer;
BEGIN
    SELECT count(*) into total FROM COMPANY;
    RETURN total;
END;
$total$ LANGUAGE plpgsql;
```

Lorsque la requête ci-dessus est exécutée, le résultat sera :

```sql
testdb# CREATE FUNCTION
```

Maintenant, exécutons un appel à cette fonction et vérifions les enregistrements dans la table SOCIÉTÉ :

```sql
testdb=# select totalRecords();
```

Lorsque la requête ci-dessus est exécutée, le résultat sera :

```bash
totalrecords
--------------
      7
(1 row)
```
