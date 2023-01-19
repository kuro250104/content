Le type de données SQLite est un attribut qui spécifie le type de données de tout objet. Chaque colonne, variable et expression a un type de données correspondant en SQLite.

Vous utiliserez ces types de données lors de la création de vos tables. SQLite utilise un système de type dynamique plus général. En SQLite, le type de données d'une valeur est associé à la valeur elle-même, et non à son conteneur.

## SQLite Storage Classes

Chaque valeur stockée dans une base de données SQLite possède l'une des classes de stockage suivantes -

**Classe de stockage et description**

- **NULL** - La valeur est une valeur NULL.
- **INTEGER** - La valeur est un nombre entier signé, stocké dans 1, 2, 3, 4, 6 ou 8 octets selon l'ampleur de la valeur.
- **REAL** - La valeur est une valeur à virgule flottante, stockée comme un nombre à virgule flottante IEEE de 8 octets.
- **TEXT** - La valeur est une chaîne de texte, stockée en utilisant l'encodage de la base de données (UTF-8, UTF-16BE ou UTF-16LE).
- **BLOB** - La valeur est un blob de données, stocké exactement comme il a été entré. La classe de stockage SQLite est légèrement plus générale qu'un type de données. La classe de stockage INTEGER, par exemple, comprend 6 types de données entières de longueurs différentes.

## SQLite Affinity Type

SQLite supporte le concept d'affinité de type sur les colonnes. Toute colonne peut toujours stocker n'importe quel type de données mais la classe de stockage préférée pour une colonne est appelée son affinité. Chaque colonne de table dans une base de données SQLite3 se voit attribuer une des affinités de type suivantes -

**Affinité et description**

- **TEXT** - Cette colonne stocke toutes les données en utilisant les classes de stockage NULL, TEXT ou BLOB.
- **NUMERIC** - Cette colonne peut contenir des valeurs utilisant les cinq classes de stockage.
INTEGER -Se comporte de la même manière qu'une colonne avec affinité NUMERIC, avec une exception dans une expression CAST.
- **REAL** - Se comporte comme une colonne avec affinité NUMERIC sauf qu'elle force les valeurs entières en représentation à virgule flottante.
- **NONE** - Une colonne avec une affinité NONE ne préfère pas une classe de stockage par rapport à une autre et aucune tentative n'est faite pour forcer les données d'une classe de stockage à une autre.

SQLite Affinity and Type Names

Le tableau suivant énumère les différents noms de types de données qui peuvent être utilisés lors de la création de tables SQLite3 avec l'affinité appliquée correspondante.

**Type de données et Affinité**

- **INTEGER** : 
    - INT
    - INTEGER
    - TINYINT
    - SMALLINT
    - MEDIUMINT
    - BIGINT
    - UNSIGNED BIG INT
    - INT2
    - INT8
- **TEXT** : 
    - CHARACTER(20)
    - VARCHAR(255)
    - VARYING CHARACTER(255)
    - NCHAR(55)
    - NATIVE CHARACTER(70)
    - NVARCHAR(100)
    - CLOB
    - TEXT
- **NONE** :
    - BLOB
    - no datatype specified
- **REAL** : 
    - REAL
    - DOUBLE
    - DOUBLE PRECISION
    - FLOAT
- **NUMERIC** :
    - NUMERIC
    - DECIMAL(10,5)
    - BOOLEAN
    - DATE
    - DATETIME

## Type de données booléen

SQLite ne dispose pas d'une classe de stockage booléenne distincte. Au lieu de cela, les valeurs booléennes sont stockées comme des entiers 0 (faux) et 1 (vrai).

## Date and Time Datatype

SQLite ne dispose pas d'une classe de stockage séparée pour stocker les dates et/ou les heures, mais SQLite est capable de stocker les dates et les heures sous forme de valeurs TEXT, REAL ou INTEGER.

**Classe de stockage et format de date**

- **TEXT** - Une date dans un format comme "AAAA-MM-JJ HH:MM:SS.SSS".
- **REAL** - Le nombre de jours depuis midi à Greenwich le 24 novembre 4714 avant J.-C.
- **INTEGER** - Le nombre de secondes depuis 1970-01-01 00:00:00 UTC

Vous pouvez choisir d'enregistrer les dates et les heures dans l'un de ces formats et convertir librement les formats à l'aide des fonctions intégrées de date et d'heure.
