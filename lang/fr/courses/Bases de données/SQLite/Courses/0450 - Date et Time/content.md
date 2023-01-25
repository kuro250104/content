## Introduction

SQLite supporte cinq fonctions de date et d'heure comme suit -

**Function et Exemple**

- ```date(timestring, modifiers...)``` - Cela renvoie la date dans ce format : AAAA-MM-JJ.
- ```time(timestring, modifiers...)``` - Cela renvoie l'heure sous la forme HH:MM:SS.
- ```datetime(timestring, modifiers...)``` - Cela donne YYYY-MM-DD HH:MM:SS.
- ```julianday(timestring, modifiers...)``` - On obtient le nombre de jours écoulés depuis midi à Greenwich le 24 novembre 4714 avant J.-C. .
- ```strftime(timestring, modifiers...)``` - Ceci renvoie la date formatée selon la chaîne de format spécifiée comme premier argument, formatée selon les formateurs expliqués ci-dessous.

Les cinq fonctions de date et d'heure ci-dessus prennent une chaîne de temps comme argument. La chaîne de temps est suivie de zéro ou plusieurs modificateurs. La fonction strftime() prend également une chaîne de format comme premier argument. La section suivante vous donnera des détails sur les différents types de chaînes de temps et de modificateurs.

## Time Strings

Une chaîne de temps peut être dans l'un des formats suivants -

**Chaîne de temps et Exemple**

- **YYYY-MM-DD** - 2010-12-30
- **YYYY-MM-DD HH:MM** - 2010-12-30 12:10
- **YYYY-MM-DD HH:MM:SS.SSS** - 2010-12-30 12:10:04.100
- **MM-DD-YYYY HH:MM** - 30-12-2010 12:10 
- **HH:MM** - 12:10
- **YYYY-MM-DDTHH:MM** - 2010-12-30 12:10
- **HH:MM:SS** - 12:10:01
- **YYYYMMDD HHMMSS** - 20101230 121001
- **now** - 2013-05-07

Vous pouvez utiliser le "T" comme un caractère littéral séparant la date et l'heure.

## Modifiers

La chaîne d'heure peut être suivie de zéro ou plusieurs modificateurs qui modifieront la date et/ou l'heure renvoyée par l'une des cinq fonctions ci-dessus. Les modificateurs sont appliqués de gauche à droite.

Les modificateurs suivants sont disponibles dans SQLite

- NNN days
- NNN hours
- NNN minutes
- NNN.NNNN seconds
- NNN months
- NNN years
- start of month
- start of year
- start of day
- weekday N
- unixepoch
- localtime
- utc

## Formatters

SQLite fournit une fonction très pratique, ```strftime()```, pour formater n'importe quelle date et heure. Vous pouvez utiliser les substitutions suivantes pour formater votre date et votre heure.

| **Substitution** | **Description** |
| --- | --- |
| ```%d``` | Jour du mois, 01-31 |
| ```%f``` | Secondes fractionnées, SS.SSS |
| ```%H``` | Heure, 00-23 |
| ```%j``` | Jour de l'année, 001-366 |
| ```%J``` | Numéro du jour julien, DDDD.DDDD |
| ```%m``` | Mois, 00-12 |
| ```%M``` | Minute, 00-59 |
| ```%s``` | Secondes depuis 1970-01-01 |
| ```%S``` | Secondes, 00-59 |
| ```%w``` | Jour de la semaine, 0-6 (0 c'est dimanche) |
| ```%W``` | Semaine de l'année, 01-53 |
| ```%Y``` | Année, YYYY |
| ```%%``` | % symbole |

### Exemples

Essayons maintenant plusieurs exemples en utilisant l'invite SQLite. La commande suivante calcule la date actuelle.

```sql
sqlite> SELECT date('now');
2022-11-08
```

La commande suivante calcule le dernier jour du mois en cours.

```sql
sqlite> SELECT date('now','start of month','+1 month','-1 day');
2022-11-30
```

La commande suivante calcule la date et l'heure pour un timestamp UNIX donné 1092941466.

```sql
sqlite> SELECT datetime(1092941466, 'unixepoch');
2004-08-19 18:51:06
```

La commande suivante calcule la date et l'heure pour un timestamp UNIX donné 1092941466 et compense pour votre fuseau horaire local.

```sql
sqlite> SELECT datetime(1092941466, 'unixepoch', 'localtime');
2004-08-19 13:51:06
```

La commande suivante calcule l'horodatage UNIX actuel.

```sql
sqlite> SELECT strftime('%s','now');
1393348134
```

La commande suivante calcule le nombre de jours depuis la signature de la Déclaration d'indépendance des États-Unis.

```sql
sqlite> SELECT julianday('now') - julianday('1776-07-04');
86798.7094695023
```

La commande suivante calcule le nombre de secondes depuis un moment donné en 2004.

```sql
sqlite> SELECT strftime('%s','now') - strftime('%s','2004-01-01 02:34:56');
295001572
```

La commande suivante calcule la date du premier mardi d'octobre pour l'année en cours.

```sql
sqlite> SELECT date('now','start of year','+9 months','weekday 2');
2022-10-04
```

La commande suivante calcule le temps depuis l'époque UNIX en secondes (comme strftime('%s','now') mais en incluant la partie fractionnaire).

```sql
sqlite> SELECT (julianday('now') - 2440587.5)*86400.0;
1367926077.12598
```

Pour convertir les valeurs de l'heure UTC en valeurs de l'heure locale lors du formatage d'une date, utilisez les modificateurs utc ou localtime comme suit :

```sql
sqlite> SELECT time('12:00', 'localtime');
05:00:00
sqlite> SELECT time('12:00', 'utc');
19:00:00
```
