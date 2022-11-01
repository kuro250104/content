## Introduction

Il existe deux façons simples de charger des données dans la base de données MySQL à partir d'un fichier préalablement
sauvegardé.

## Importing Data with LOAD DATA

MySQL fournit une instruction LOAD DATA qui agit comme un chargeur de données en masse. Voici un exemple 
d'instruction qui lit un fichier **dump.txt** dans votre répertoire actuel et le charge dans la table **mytbl**
de la base de données actuelle.

``` sql
mysql> LOAD DATA LOCAL INFILE 'dump.txt' INTO TABLE mytbl;
```

  - Si le mot clé **LOCAL** n'est pas présent, MySQL recherche le fichier de données sur l'hôte du serveur à l'aide de la commande **looking into absolute pathname**, qui spécifie entièrement l'emplacement du fichier, en commençant par la racine du système de fichiers. MySQL lit le fichier à partir de l'emplacement donné.
  - Par défaut, **LOAD DATA** suppose que les fichiers de données contiennent des lignes terminées par des sauts de ligne (newlines) et que les valeurs de données d'une ligne sont séparées par des tabulations.
  - Pour spécifier explicitement un format de fichier, utilisez une clause **FIELDS** pour décrire les caractéristiques des champs d'une ligne et une clause **LINES** pour spécifier la séquence de fin de ligne. L'instruction **LOAD DATA** suivante spécifie que le fichier de données contient des valeurs séparées par des deux-points et des lignes terminées par des retours chariot et un caractère de nouvelle ligne.

``` sql
mysql> LOAD DATA LOCAL INFILE 'dump.txt' INTO TABLE mytbl
   -> FIELDS TERMINATED BY ':'
   -> LINES TERMINATED BY '\r\n';
```

 - La commande LOAD DATA suppose que les colonnes du fichier de données ont le même ordre que les colonnes de la table. Si ce n'est pas le cas, vous pouvez spécifier une liste pour indiquer dans quelles colonnes de la table les colonnes du fichier de données doivent être chargées. Supposons que votre table comporte des colonnes a, b et c, mais que les colonnes successives du fichier de données correspondent aux colonnes b, c et a.

Vous pouvez charger le fichier comme indiqué dans le bloc de code suivant.


``` sql
mysql> LOAD DATA LOCAL INFILE 'dump.txt' 
   -> INTO TABLE mytbl (b, c, a);
```

## Importing Data with mysqlimport

MySQL inclut également un programme utilitaire nommé **mysqlimport** qui agit comme un emballage autour de LOAD DATA,
de sorte que vous pouvez charger les fichiers d'entrée directement à partir de la ligne de commande.

Pour charger les données du fichier **dump.txt** dans **mytbl**, utilisez la commande suivante à l'invite UNIX.

``` sql
$ mysqlimport -u root -p --local database_name dump.txt
password *****
```

Si vous utilisez mysqlimport, les options de ligne de commande fournissent les spécificateurs de format. Les 
commandes **mysqlimport** qui correspondent aux deux instructions **LOAD DATA** précédentes se présentent comme indiqué
dans le bloc de code suivant.

``` sql
$ mysqlimport -u root -p --local --fields-terminated-by = ":" \
   --lines-terminated-by = "\r\n"  database_name dump.txt
password *****
```

L'ordre dans lequel vous spécifiez les options n'a pas d'importance pour mysqlimport, sauf qu'elles doivent toutes précéder 
le nom de la base de données.

L'instruction **mysqlimport** utilise l'option **--columns** pour spécifier l'ordre des colonnes :

``` sql
$ mysqlimport -u root -p --local --columns=b,c,a \
   database_name dump.txt
password *****
```

## Handling Quotes and Special Characters

La clause FIELDS peut spécifier d'autres options de format que **TERMINATED BY**. Par défaut, LOAD DATA suppose que les
valeurs ne sont pas citées et interprète la barre oblique inversée (\) comme un caractère d'échappement pour les 
caractères spéciaux. Pour indiquer explicitement le caractère de citation de la valeur, utilisez la commande **ENCLOSED 
BY**. MySQL supprimera ce caractère à la fin des valeurs de données pendant le traitement des entrées. Pour 
modifier le caractère d'échappement par défaut, utilisez la commande **ESCAPED BY**.

Lorsque vous spécifiez ENCLOSED BY pour indiquer que les caractères de citation doivent être supprimés des valeurs de
données, il est possible d'inclure le caractère de citation littéralement dans les valeurs de données en le doublant ou 
en le faisant précéder du caractère d'échappement.

Par exemple, si les caractères guillemets et d'échappement sont " et \, la valeur d'entrée "a""b\"c" sera interprétée comme a "b "c.

Pour **mysqlimport**, les options de ligne de commande correspondantes pour spécifier les valeurs de citation et d'échappement sont 
**--fields-enclosed-by** et **--fields-escaped-by**.
