Dans ce chapitre, nous allons parler des types de données utilisés dans PostgreSQL. Lors de la création d'une table, pour chaque colonne, vous spécifiez un type de données, c'est-à-dire le type de données que vous voulez stocker dans les champs de la table.

Cela permet plusieurs avantages :

- **Consistency** − Les opérations sur des colonnes de même type de données donnent des résultats cohérents et sont généralement les plus rapides.
- **Validation** − L'utilisation correcte des types de données implique la validation du format des données et le rejet des données hors de la portée du type de données.
- **Compactness** − Comme une colonne peut stocker un seul type de valeur, elle est stockée de manière compacte.
- **Performance** − Une utilisation appropriée des types de données permet un stockage plus efficace des données. Les valeurs stockées peuvent être traitées rapidement, ce qui améliore les performances.

PostgreSQL supporte un large ensemble de types de données. En outre, les utilisateurs peuvent créer leur propre type de données personnalisé en utilisant la commande SQL **CREATE TYPE**. Il existe différentes catégories de types de données dans PostgreSQL. Elles sont présentées ci-dessous.

## Types numériques

Les types numériques se composent d'entiers de deux, quatre et huit octets, de nombres à virgule flottante de quatre et huit octets et de décimales de précision sélectionnable. Le tableau suivant répertorie les types disponibles.

| **Nom** | **Taille de stockage** | **Description** | **Range** |
| --- | --- | --- | --- |
| smallint | 2 bytes | Petit nombre d'entiers | -32768 to +32767 |
| integer | 4 bytes | Choix typique pour les entiers | -2147483648 to +2147483647 |
| bigint | 8 bytes | Grand nombre d'entiers | -9223372036854775808 to 9223372036854775807 |
| decimal | variable | Précision spécifiée par l'utilisateur, exact | up to 131072 digits before the decimal point; up to 16383 digits after the decimal point |
| numeric | variable | Précision spécifiée par l'utilisateur, exact | up to 131072 digits before the decimal point; up to 16383 digits after the decimal point |
| real | 4 bytes | Précision variable, inexacte | 6 decimal digits precision |
| double precision | 8 bytes | Précision variable, inexacte | 15 decimal digits precision |
| smallserial | 2 bytes | Petit entier auto incrémenté | 1 to 32767 |
| serial | 4 bytes | Nombre entier auto-incrémenté | 1 to 2147483647 |
| bigserial | 8 bytes | Grand entier auto incrémenté | 1 to 9223372036854775807 |

## Types monétaires

Le type money stocke un montant en devise avec une précision fractionnaire fixe. Les valeurs des types de données numeric, int et bigint peuvent être converties en argent. L'utilisation de nombres à virgule flottante n'est pas recommandée pour gérer l'argent en raison du risque d'erreurs d'arrondi.

| **Nom** | **Taille de stockage** | **Description** | **Range** |
| --- | --- | --- | --- |
| money | 8 bytes | Montant en devise | -92233720368547758.08 to +92233720368547758.07 |

## Types de caractères

La liste ci-dessous énumère les types de caractères à usage général disponibles dans PostgreSQL.

**Name & Description**

- **character varying(n), varchar(n)** - Longueur variable avec limite.
- **character(n), char(n)** - Longueur fixe, rembourré en blanc.
- **text** - Longueur variable illimitée.

## Le types Binary Data

Le type de données bytea permet de stocker des chaînes de caractères binaires comme dans le tableau ci-dessous :

| **Nom** | **Taille de stockage** | **Description** |
| --- | --- | --- |
| bytea | 1 or 4 bytes plus the actual binary string | Chaîne binaire de longueur variable |

## Types de dates et de temps

PostgreSQL supporte un ensemble complet de types de dates et d'heures SQL, comme indiqué dans le tableau ci-dessous. Les dates sont comptées selon le calendrier grégorien. Ici, tous les types ont une résolution de 1 microseconde / 14 chiffres, sauf le type de date, dont la résolution est le jour.

| **Nom** | **Taille de stockage** | **Description** | **Valeur min** | **Valeur max** |
| --- | --- | --- | --- | --- |
| timestamp [(p)] [without time zone ] | 8 bytes | La date et l'heure (sans fuseau horaire) | 4713 BC | 294276 AD |
| TIMESTAMPTZ | 8 bytes | La date et l'heure, avec le fuseau horaire | 4713 BC | 294276 AD |
| date | 4 bytes | Date (pas d'heure de la journée) | 4713 BC | 5874897 AD |
| time [ (p)] [ without time zone ] | 8 bytes | Heure de la journée (sans date) | 00:00:00 | 24:00:00 |
| time [ (p)] with time zone | 12 bytes | Les heures de la journée uniquement, avec le fuseau horaire | 00:00:00+1459 | 24:00:00-1459 |
| interval [fields ] [(p) ] | 12 bytes | Intervalle de temps | -178000000 years | 178000000 years |

## Le type Boolean

PostgreSQL fournit le type SQL standard Boolean. Le type de données booléen peut avoir les états true, false, et un troisième état, unknown, qui est représenté par la valeur SQL null.

| **Nom** | **Taille de stockage** | **Description** |
| --- | --- | --- |
| boolean | 1 byte | L'état de vrai ou faux |

## Le type Enumerated

Les types énumérés (enum) sont des types de données qui comprennent un ensemble statique et ordonné de valeurs. Ils sont équivalents aux types énumérés pris en charge dans un certain nombre de langages de programmation.

Contrairement aux autres types, les types énumérés doivent être créés à l'aide de la commande CREATE TYPE. Ce type est utilisé pour stocker un ensemble statique et ordonné de valeurs. Par exemple, les directions de la boussole, c'est-à-dire NORD, SUD, EST et OUEST, ou les jours de la semaine, comme indiqué ci-dessous.

```sql
CREATE TYPE week AS ENUM ('Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun');
```

Une fois créés, les types énumérés peuvent être utilisés comme tous les autres types.

## Le type geométrique

Les types de données géométriques représentent des objets spatiaux bidimensionnels. Le type le plus fondamental, le point, constitue la base de tous les autres types.

| **Nom** | **Taille de stockage** | **Représentation** | **Description** |
| --- | --- | --- | --- |
| point | 16 bytes | Point sur un plan | (x,y) |
| line | 32 bytes | Ligne infinie (pas complètement implémentée) | ((x1,y1),(x2,y2)) |
| lseg | 32 bytes | Segment de ligne fini | ((x1,y1),(x2,y2)) |
| box | 32 bytes | Boîte rectangulaire | ((x1,y1),(x2,y2)) |
| path | 16+16n bytes | Chemin fermé (similaire à un polygone) | ((x1,y1),...) |
| path | 16+16n bytes | Chemin ouvert | [(x1,y1),...] |
| polygon | 40+16n | Polygone (similaire à un chemin fermé) | ((x1,y1),...) |
| circle | 24 bytes | Cercle | <(x,y),r> (center point and radius) |

## Le type Network Address

PostgreSQL offre des types de données pour stocker les adresses IPv4, IPv6 et MAC. Il est préférable d'utiliser ces types plutôt que des types de texte brut pour stocker les adresses réseau, car ces types offrent une vérification des erreurs d'entrée et des opérateurs et fonctions spécialisés.

| **Nom** | **Taille de stockage** | **Description** |
| --- | --- | --- |
| cidr | 7 or 19 bytes | Réseaux IPv4 et IPv6 |
| inet | 7 or 19 bytes | Hôtes et réseaux IPv4 et IPv6 |
| macaddr | 6 bytes | Adresses MAC |

## Le type Bit String

Les types de chaînes de bits sont utilisés pour stocker les masques de bits. Ils sont soit 0 soit 1. Il existe deux types de bits SQL : bit(n) et bit variant(n), où n est un nombre entier positif.

## Le type de recherche de texte

Ce type prend en charge la recherche en texte intégral, qui consiste à parcourir une collection de documents en langage naturel pour trouver ceux qui correspondent le mieux à une requête. Il existe deux types de données pour ce type :

**Nom et description**

- **tsvector** - Il s'agit d'une liste triée de mots distincts qui ont été normalisés pour fusionner différentes variantes d'un même mot, appelées "lexèmes".
- **tsquery** - Il stocke les lexèmes à rechercher, et les combine en respectant les opérateurs booléens & (AND), | (OR), et ! (NOT). Les parenthèses peuvent être utilisées pour imposer le regroupement des opérateurs.

## Le type UUID

Un UUID (Universally Unique Identifiers) s'écrit comme une séquence de chiffres hexadécimaux minuscules, en plusieurs groupes séparés par des traits d'union, plus précisément un groupe de huit chiffres, suivi de trois groupes de quatre chiffres, suivis d'un groupe de 12 chiffres, pour un total de 32 chiffres représentant les 128 bits.

Un exemple d'UUID est - 550e8400-e29b-41d4-a716-446655440000

## Le type XML

Le type de données XML peut être utilisé pour stocker des données XML. Pour stocker des données XML, vous devez d'abord créer des valeurs XML à l'aide de la fonction xmlparse, comme suit :

```sql
XMLPARSE (DOCUMENT '<?xml version="1.0"?>
<tutorial>
<title>PostgreSQL Tutorial </title>
    <topics>...</topics>
</tutorial>')

XMLPARSE (CONTENT 'xyz<foo>bar</foo><bar>foo</bar>')
```

## Le type JSON

Le type de données json peut être utilisé pour stocker des données JSON (JavaScript Object Notation). Ces données peuvent également être stockées sous forme de texte, mais le type de données json présente l'avantage de vérifier que chaque valeur stockée est une valeur JSON valide. Il existe également des fonctions de support associées, qui peuvent être utilisées directement pour manipuler le type de données JSON comme suit.

| **Exemple** | **Résultat** |
| --- | --- |
| ```array_to_json('{{1,5},{99,100}}'::int[])``` | ```[[1,5],[99,100]]``` |
| ```row_to_json(row(1,'foo'))``` | ```{"f1":1,"f2":"foo"}``` |

## Le type Array

PostgreSQL offre la possibilité de définir une colonne d'une table comme un tableau multidimensionnel de longueur variable. Des tableaux de n'importe quel type de base intégré ou défini par l'utilisateur, de type enum ou de type composite peuvent être créés.

## Déclaration de tableaux

Le type de tableau peut être déclaré comme ci-dessous :

```sql
CREATE TABLE monthly_savings (
    name text,
    saving_per_quarter integer[],
    scheme text[][]
);
```

ou en utilisant le mot clé "ARRAY" comme ci-dessous :

```sql
CREATE TABLE monthly_savings (
    name text,
    saving_per_quarter integer ARRAY[4],
    scheme text[][]
);
```

## Insertion de valeurs

Les valeurs d'un tableau peuvent être insérées comme une constante littérale, en enfermant les valeurs des éléments entre accolades et en les séparant par des virgules. Un exemple est présenté ci-dessous :

```sql
INSERT INTO monthly_savings 
VALUES ('Manisha', 
'{20000, 14600, 23500, 13250}', 
'{{"FD", "MF"}, {"FD", "Property"}}');
```

## Accès aux tableaux

Un exemple d'accès aux tableaux est présenté ci-dessous. La commande donnée ci-dessous sélectionnera les personnes dont l'épargne est plus importante au deuxième trimestre qu'au quatrième trimestre.

```sql
SELECT name FROM monhly_savings WHERE saving_per_quarter[2] > saving_per_quarter[4];
```

## Modification de tableaux

Un exemple de modification de tableaux est présenté ci-dessous :

```sql
UPDATE monthly_savings SET saving_per_quarter = '{25000,25000,27000,27000}'
WHERE name = 'Manisha';
```

ou en utilisant la syntaxe de l'expression ARRAY :

```sql
UPDATE monthly_savings SET saving_per_quarter = ARRAY[25000,25000,27000,27000]
WHERE name = 'Manisha';
```

## Recherche dans les tableaux

Un exemple de recherche dans des tableaux est présenté ci-dessous :

```sql
SELECT * FROM monthly_savings WHERE saving_per_quarter[1] = 10000 OR
saving_per_quarter[2] = 10000 OR
saving_per_quarter[3] = 10000 OR
saving_per_quarter[4] = 10000;
```

Si la taille du tableau est connue, la méthode de recherche donnée ci-dessus peut être utilisée. Sinon, l'exemple suivant montre comment rechercher lorsque la taille n'est pas connue.

```sql
SELECT * FROM monthly_savings WHERE 10000 = ANY (saving_per_quarter);
```

## Types composites

Ce type représente une liste de noms de champs et leurs types de données, c'est-à-dire la structure d'une ligne ou d'un enregistrement d'une table.

## Déclaration de types composite

L'exemple suivant montre comment déclarer un type composite :

```sql
CREATE TYPE inventory_item AS (
    name text,
    supplier_id integer,
    price numeric
);
```

Ce type de données peut être utilisé dans les tables de création comme ci-dessous :

```sql
CREATE TABLE on_hand (
    item inventory_item,
    count integer
);
```

## Valeurs composées

Les valeurs composées peuvent être insérées comme une constante littérale, en mettant les valeurs des champs entre parenthèses et en les séparant par des virgules. Un exemple est présenté ci-dessous :

```sql
INSERT INTO on_hand VALUES (ROW('fuzzy dice', 42, 1.99), 1000);
```

Ceci est valable pour l'inventaire_item défini ci-dessus. Le mot clé ROW est en fait facultatif tant que vous avez plus d'un champ dans l'expression.

## Accéder à un champ d'un type composite

Pour accéder à un champ d'une colonne composite, utilisez un point suivi du nom du champ, comme pour sélectionner un champ à partir d'un nom de table. Par exemple, pour sélectionner certains sous-champs de notre table d'exemple on_hand, la requête serait la suivante :

```sql
SELECT (item).name FROM on_hand WHERE (item).price > 9.99;
```

Vous pouvez même utiliser également le nom de la table (par exemple dans une requête multitable), comme ceci :

```sql
SELECT (on_hand.item).name FROM on_hand WHERE (on_hand.item).price > 9.99;
```

## Les types de plage

Les types de plage représentent des types de données qui utilisent une plage de données. Les types de plage peuvent être des plages discrètes (par exemple, toutes les valeurs entières de 1 à 10) ou des plages continues (par exemple, tout point dans le temps entre 10h00 et 11h00).

Les types de plage intégrés disponibles incluent les plages suivantes :

- **int4range** − Gamme d'entiers.
- **int8range** − Plage de bigint.
- **numrange** − Plage de valeurs numériques.
- **tsrange** − Plage d'horodatage sans fuseau horaire.
- **tstzrange** − Plage de l'horodatage avec le fuseau horaire.
- **daterange** − Plage de dates.

Il est possible de créer des types de plages personnalisés pour mettre à disposition de nouveaux types de plages, tels que des plages d'adresses IP utilisant le type inet comme base, ou des plages de valeurs flottantes utilisant le type de données float comme base.

Les types de plage prennent en charge les limites de plage inclusives et exclusives à l'aide des caractères [ ] et ( ), respectivement. Par exemple, '[4,9)' représente tous les entiers à partir de 4 inclus jusqu'à 9 non inclus.

## Identifiants d'objets

Les identifiants d'objets (OID) sont utilisés en interne par PostgreSQL comme clés primaires pour diverses tables système. Si WITH OIDS est spécifié ou si la variable de configuration default_with_oids est activée, alors seulement, dans ce cas, les OIDs sont ajoutés aux tables créées par l'utilisateur. Le tableau suivant répertorie plusieurs types d'alias. Les types d'alias OID n'ont pas d'opérations propres, à l'exception des routines d'entrée et de sortie spécialisées.

| **Nom** | **Références** | **Description** | **Exemple de valeur** |
| --- | --- | --- | --- |
| oid | any | Identifiant numérique de l'objet | 564182 |
| regproc | pg_proc | Nom de la fonction | sum |
| regprocedure | pg_proc | Fonction avec des types d'arguments | sum(int4) |
| regoper | pg_operator | Nom de l'opérateur | + |
| regoperator | pg_operator | Opérateur avec des types d'arguments | *(integer,integer) or -(NONE,integer) |
| regclass | pg_class | Nom de la relation | pg_type |
| regtype | pg_type | Nom du type de données | integer |
| regconfig | pg_ts_config | Configuration de la recherche de texte | English |
| regdictionary | pg_ts_dict | Recherche de texte dans un dictionnaire | simple |

## Pseudo Types

Le système de type PostgreSQL contient un certain nombre d'entrées à usage spécial qui sont collectivement appelées pseudo-types. Un pseudo-type ne peut pas être utilisé comme un type de données de colonne, mais il peut être utilisé pour déclarer le type d'argument ou de résultat d'une fonction.

Le tableau ci-dessous liste les pseudo-types existants.

**Nom et description**

- **any** - Indique qu'une fonction accepte tout type de données d'entrée.
- **anyelement** - Indique qu'une fonction accepte n'importe quel type de données.
- **anyarray** - Indique qu'une fonction accepte tout type de données de tableau.
- **anynonarray** - Indique qu'une fonction accepte tout type de données hors tableau.
- **anyenum** - Indique qu'une fonction accepte tout type de données d'énumération.
- **anyrange** - Indique qu'une fonction accepte tout type de données de plage.
- **cstring** - Indique qu'une fonction accepte ou renvoie une chaîne de caractères C à terminaison nulle.
- **internal** - Indique qu'une fonction accepte ou renvoie un type de données interne au serveur.
- **language_handler** - Un gestionnaire d'appel de langage procédural est déclaré pour renvoyer language_handler.
- **fdw_handler** - Un gestionnaire d'enveloppe de données étrangères est déclaré pour renvoyer fdw_handler.
- **record** - Identifie une fonction renvoyant un type de ligne non spécifié.
- **trigger** - Une fonction trigger est déclarée pour renvoyer trigger.
- **void** - Indique qu'une fonction ne renvoie aucune valeur.
