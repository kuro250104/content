## Introduction

La définition correcte des champs d'une table est importante pour l'optimisation globale de votre base de données. 
Vous ne devez utiliser que le type et la taille de champ dont vous avez réellement besoin. Par exemple, ne définissez
pas un champ de 10 caractères de large, si vous savez que vous n'allez utiliser que 2 caractères. Ces types de champs 
(ou colonnes) sont également appelés types de données, en référence au type de données que vous allez stocker dans ces champs.

MySQL utilise un grand nombre de types de données différents, répartis en trois catégories : - le type de données 
(ou colonnes)

  - Numeric
  - Date and Time
  - String Types.

Nous allons maintenant les examiner en détail.

## Numeric Data Types

MySQL utilise tous les types de données numériques standard ANSI SQL, donc si vous venez à MySQL depuis un autre 
système de base de données, ces définitions vous seront familières.

La liste suivante présente les types de données numériques les plus courants et leur description.

  - **INT** − Un nombre entier de taille normale qui peut être signé ou non signé. S'il est signé, la plage autorisée est comprise entre -2147483648 et 2147483647. S'il est non signé, la plage autorisée est comprise entre 0 et 4294967295. Vous pouvez spécifier une largeur allant jusqu'à 11 chiffres.
  - **TINYINT** − Un très petit entier qui peut être signé ou non signé. S'il est signé, la plage autorisée va de -128 à 127. S'il est non signé, la plage autorisée est comprise entre 0 et 255. Vous pouvez spécifier une largeur allant jusqu'à 4 chiffres.
  - **SMALLINT** − Un petit nombre entier qui peut être signé ou non signé. S'il est signé, la plage autorisée est comprise entre -32768 et 32767. S'il est non signé, la plage autorisée est comprise entre 0 et 65535. Vous pouvez spécifier une largeur allant jusqu'à 5 chiffres.
  - **MEDIUMINT** − Un nombre entier de taille moyenne qui peut être signé ou non signé. S'il est signé, la plage autorisée est comprise entre -8388608 et 8388607. S'il est non signé, la plage autorisée est comprise entre 0 et 16777215. Vous pouvez spécifier une largeur allant jusqu'à 9 chiffres.
  - **BIGINT** − Un grand nombre entier qui peut être signé ou non signé. S'il est signé, la plage autorisée est comprise entre -9223372036854775808 et 9223372036854775807. S'il est non signé, la plage autorisée est comprise entre 0 et 18446744073709551615. Vous pouvez spécifier une largeur allant jusqu'à 20 chiffres.
  - **FLOAT(M,D)** − Un nombre à virgule flottante qui ne peut pas être non signé. Vous pouvez définir la longueur d'affichage (M) et le nombre de décimales (D). Cela n'est pas nécessaire et la valeur par défaut sera 10,2, où 2 est le nombre de décimales et 10 est le nombre total de chiffres (décimales comprises). La précision décimale peut aller jusqu'à 24 positions pour un FLOAT.
  - **DOUBLE(M,D)** − Un nombre à virgule flottante de double précision qui ne peut pas être non signé. Vous pouvez définir la longueur d'affichage (M) et le nombre de décimales (D). Cette option n'est pas obligatoire et la valeur par défaut sera 16,4, où 4 est le nombre de décimales. La précision décimale peut aller jusqu'à 53 positions pour un DOUBLE. REAL est un synonyme de DOUBLE.
  - **DECIMAL(M,D)** − Un nombre à virgule flottante non emballé qui ne peut pas être non signé. Dans les décimales non emballées, chaque décimale correspond à un octet. Il est nécessaire de définir la longueur d'affichage (M) et le nombre de décimales (D). NUMERIC est un synonyme de DECIMAL.

## Date and Time Types

Les types de données MySQL relatifs à la date et à l'heure sont les suivants :

  - **DATE** − Une date au format AAAA-MM-JJ, entre 1000-01-01 et 9999-12-31. Par exemple, le 30 décembre 1973 sera enregistré sous la forme 1973-12-30.
  - **DATETIME** − Une combinaison de date et d'heure au format AAAA-MM-JJ HH:MM:SS, entre le 1000-01-01 00:00:00 et le 9999-12-31 23:59:59. Par exemple, le 30 décembre 1973 à 3h30 de l'après-midi sera enregistré sous la forme 1973-12-30 15:30:00.
  - **TIMESTAMP** − Un horodatage entre le 1er janvier 1970 à minuit et 2037. Ce format ressemble à l'ancien format DATETIME, mais sans les traits d'union entre les chiffres. Ainsi, le 30 décembre 1973, à 3h30 de l'après-midi, le format 19731230153000 (AAAAMMJJHHMMSS) serait enregistré.
  - **TIME** − Enregistre l'heure au format HH:MM:SS.
  - **YEAR(M)** − Stocke une année dans un format à 2 ou 4 chiffres. Si la longueur est spécifiée comme 2 (par exemple YEAR(2)), YEAR peut être compris entre 1970 et 2069 (70 à 69). Si la longueur spécifiée est de 4, YEAR peut être compris entre 1901 et 2155. La longueur par défaut est de 4.

## String Types

Bien que les types numériques et de date soient amusants, la plupart des données que vous stockerez seront au format 
chaîne. Cette liste décrit les types de données de chaîne les plus courants dans MySQL.

  - **CHAR(M)** − Une chaîne de longueur fixe comprise entre 1 et 255 caractères (par exemple CHAR(5)), complétée à droite par des espaces jusqu'à la longueur spécifiée lors du stockage. Il n'est pas nécessaire de définir une longueur, mais la valeur par défaut est 1.
  - **VARCHAR(M)** − Une chaîne de caractères de longueur variable comprise entre 1 et 255 caractères. Par exemple, VARCHAR(25). Vous devez définir une longueur lorsque vous créez un champ VARCHAR.
  - **BLOB or TEXT** − Un champ dont la longueur maximale est de 65535 caractères. Les BLOB sont des "Binary Large Objects" et sont utilisés pour stocker de grandes quantités de données binaires, comme des images ou d'autres types de fichiers. Les champs définis comme TEXTE contiennent également de grandes quantités de données. La différence entre les deux est que les tris et les comparaisons sur les données stockées sont sensibles à la casse pour les BLOBs et ne le sont pas pour les champs TEXT. Vous ne spécifiez pas de longueur avec BLOB ou TEXT.
  - **TINYBLOB or TINYTEXT** − Une colonne BLOB ou TEXT dont la longueur maximale est de 255 caractères. Vous ne spécifiez pas de longueur avec TINYBLOB ou TINYTEXT.
  - **MEDIUMBLOB or MEDIUMTEXT** − Une colonne BLOB ou TEXT dont la longueur maximale est de 16777215 caractères. Vous ne spécifiez pas de longueur avec MEDIUMBLOB ou MEDIUMTEXT.
  - **LONGBLOB or LONGTEXT** − Une colonne BLOB ou TEXT dont la longueur maximale est de 4294967295 caractères. Vous ne spécifiez pas de longueur avec LONGBLOB ou LONGTEXT.
  - **ENUM** − Une énumération, qui est un terme fantaisiste pour liste. Lorsque vous définissez une ENUM, vous créez une liste d'éléments parmi lesquels la valeur doit être sélectionnée (ou elle peut être NULL). Par exemple, si vous voulez que votre champ contienne "A", "B" ou "C", vous définissez votre ENUM comme ENUM ('A', 'B', 'C') et seules ces valeurs (ou NULL) peuvent remplir ce champ.

Dans le chapitre suivant, nous verrons comment créer des tables dans MySQL.
