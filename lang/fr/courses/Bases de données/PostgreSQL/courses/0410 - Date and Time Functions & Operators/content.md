Nous avons discuté des types de données Date/Time dans le chapitre Types de données. Voyons maintenant les opérateurs et les fonctions Date/Time.

Le tableau suivant liste les comportements des opérateurs arithmétiques de base.

| **Opérateur** | **Exemple** | **Résultat** |
| --- | --- | --- |
| ``` + ``` | date '2022-09-28' + integer '7' | date '2022-10-05' |
| ``` + ``` | date '2022-09-28' + intervalle '1 hour' | horodatage '2022-09-28 01:00:00' |
| ``` + ``` | date '2022-09-28' + temps '03:00' | horodatage '2022-09-28 03:00:00' |
| ``` + ``` | intervalle '1 day' + intervalle '1 hour' | intervalle '1 day 01:00:00' |
| ``` + ``` | horodatage '2022-09-28 01:00' + intervalle '23 hours' | horodatage '2022-09-29 00:00:00' |
| ``` + ``` | temps '01:00' + intervalle '3 hours' | temps '04:00:00' |
| ``` - ``` | - intervalle '23 hours' | intervalle '-23:00:00' |
| ``` - ``` | date '2022-10-01' - date '2022-09-28' | entier '3' (days) |
| ``` - ``` | date '2022-10-01' - entier '7' | date '2022-09-24' |
| ``` - ``` | date '2022-09-28' - intervalle '1 hour' | horodatage '2022-09-27 23:00:00' |
| ``` - ``` | temps '05:00' - temps '03:00' | intervalle '02:00:00' |
| ``` - ``` | temps '05:00' - intervalle '2 hours' | temps '03:00:00' |
| ``` - ``` | horodatage '2022-09-28 23:00' - intervalle  '23 hours' | horodatage '2022-09-28 00:00:00' |
| ``` - ``` | intervalle '1 day' - intervalle '1 hour' | intervalle '1 day -01:00:00' |
| ``` - ``` | horodatage '2022-09-29 03:00' - horodatage '2022-09-27 12:00' | intervalle '1 day 15:00:00' |
| ``` * ``` | 900 * intervalle '1 second' | intervalle '00:15:00' |
| ``` * ``` | 21 * intervalle '1 day' | intervalle '21 days' |
| ``` * ``` | double precision '3.5' * interval '1 hour' | intervalle '03:30:00' |
| ``` * ``` | intervalle "1 heure" / double précision "1,5" | intervalle '00:40:00' |

Vous trouverez ci-dessous la liste de toutes les fonctions importantes liées à la date et à l'heure :

**Function & Description**

- **AGE()** - Soustraire les arguments.
- **CURRENT DATE/TIME()** - Date et heure actuelles.
- **DATE_PART()** - Obtenir une sous-zone (équivalent à extraire).
- **EXTRACT()** - Obtenir le sous-champ.
- **ISFINITE()** - Test pour la date, l'heure et l'intervalle finis (pas +/-infini).
- **JUSTIFY** - Ajuster l'intervalle.

## AGE(timestamp, timestamp), AGE(timestamp)

**Function & Description**

- ```AGE(timestamp, timestamp)``` - Lorsqu'il est invoqué avec la forme TIMESTAMP du second argument, AGE() soustrait les arguments, produisant un résultat "symbolique" qui utilise les années et les mois et est de type INTERVAL.
- ```AGE(timestamp)``` - Lorsqu'elle est invoquée avec le seul TIMESTAMP comme argument, AGE() soustrait de la date actuelle (à minuit).

Exemple de la fonction ```AGE(timestamp, timestamp)``` :

```sql
testdb=# SELECT AGE(timestamp '2001-04-10', timestamp '1957-06-13');
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
          age
-------------------------
 43 years 9 mons 27 days
```

Exemple de la fonction AGE(timestamp) :

```sql
testdb=# select age(timestamp '1957-06-13');
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```sql
          age
--------------------------
 55 years 10 mons 22 days
```

## CURRENT DATE/TIME()

PostgreSQL fournit un certain nombre de fonctions qui renvoient des valeurs liées à la date et à l'heure actuelles. Voici quelques fonctions :

**Fonction et description**

- **CURRENT_DATE** - Donne la date actuelle.
- **CURRENT_TIME** - Délivre des valeurs avec le fuseau horaire.
- **CURRENT_TIMESTAMP** - Délivre des valeurs avec le fuseau horaire.
- **CURRENT_TIME(precision)** - Le paramètre de précision est facultatif et permet d'arrondir le résultat à ce nombre de chiffres fractionnaires dans le champ des secondes.
- **CURRENT_TIMESTAMP(precision)** - Le paramètre de précision est facultatif et permet d'arrondir le résultat à ce nombre de chiffres fractionnaires dans le champ des secondes.
- **LOCALTIME** - Délivre des valeurs sans fuseau horaire.
- **LOCALTIMESTAMP** - Délivre des valeurs sans fuseau horaire.
- **LOCALTIME(precision)** - Le paramètre de précision est facultatif et permet d'arrondir le résultat à ce nombre de chiffres fractionnaires dans le champ des secondes.
- **LOCALTIMESTAMP(precision)** - Le paramètre de précision est facultatif et permet d'arrondir le résultat à ce nombre de chiffres fractionnaires dans le champ des secondes.

Exemples utilisant les fonctions du tableau ci-dessus :

```sql
testdb=# SELECT CURRENT_TIME;
       timetz
--------------------
 08:01:34.656+05:30
(1 row)


testdb=# SELECT CURRENT_DATE;
    date
------------
 2013-05-05
(1 row)


testdb=# SELECT CURRENT_TIMESTAMP;
              now
-------------------------------
 2013-05-05 08:01:45.375+05:30
(1 row)


testdb=# SELECT CURRENT_TIMESTAMP(2);
         timestamptz
------------------------------
 2013-05-05 08:01:50.89+05:30
(1 row)


testdb=# SELECT LOCALTIMESTAMP;
       timestamp
------------------------
 2013-05-05 08:01:55.75
(1 row)
```

PostgreSQL fournit également des fonctions qui renvoient l'heure de début de l'instruction courante, ainsi que l'heure courante réelle à l'instant où la fonction est appelée. Ces fonctions sont :

**Fonction et description**

- ```transaction_timestamp()``` - Il est équivalent à CURRENT_TIMESTAMP, mais il est nommé de manière à refléter clairement ce qu'il retourne.
- ```statement_timestamp()``` - Elle renvoie l'heure de début de la déclaration en cours.
- ```clock_timestamp()``` - Il renvoie l'heure actuelle, et sa valeur change donc même au sein d'une seule commande SQL.
- ```timeofday()``` - Il renvoie l'heure actuelle, mais sous la forme d'une chaîne de texte formatée plutôt que d'un horodatage avec valeur de fuseau horaire.
- ```now()``` - C'est un équivalent traditionnel de PostgreSQL à transaction_timestamp().

## DATE_PART et DATE_TRUNC

**Function & Description**

- ```DATE_PART('field', source)``` - Ces fonctions récupèrent les sous-champs. Le paramètre de champ doit être une valeur de chaîne, et non un nom.
Les noms de champs valides sont : century, day, decade, dow, doy, epoch, hour, isodow, isoyear, microseconds, millennium, milliseconds, minute, month, quarter, second, timezone, timezone_hour, timezone_minute, week, year.
- ```DATE_TRUNC('field', source)``` - Cette fonction est conceptuellement similaire à la fonction tronc pour les nombres. source est une expression de valeur de type timestamp ou interval. field sélectionne la précision avec laquelle la valeur d'entrée doit être tronquée. La valeur de retour est de type timestamp ou interval. Les valeurs valides pour field sont : microsecondes, millisecondes, seconde, minute, heure, jour, semaine, mois, trimestre, année, décennie, siècle, millénaire...

Voici des exemples de fonctions DATE_PART('field', source) :

```sql
testdb=# SELECT date_part('day', TIMESTAMP '2001-02-16 20:38:40');
 date_part
-----------
        16
(1 row)


testdb=# SELECT date_part('hour', INTERVAL '4 hours 3 minutes');
 date_part
-----------
         4
(1 row)
The following are examples for DATE_TRUNC('field', source) functions −
testdb=# SELECT date_trunc('hour', TIMESTAMP '2001-02-16 20:38:40');
     date_trunc
---------------------
 2001-02-16 20:00:00
(1 row)


testdb=# SELECT date_trunc('year', TIMESTAMP '2001-02-16 20:38:40');
     date_trunc
---------------------
 2001-01-01 00:00:00
(1 row)
```

## EXTRACT(field from timestamp), EXTRACT(field from interval)

La fonction EXTRACT(field FROM source) récupère des sous-champs tels que l'année ou l'heure à partir de valeurs de date/heure. La source doit être une expression de valeur de type timestamp, time ou interval. Le champ est un identifiant ou une chaîne de caractères qui sélectionne le champ à extraire de la valeur source. La fonction EXTRACT renvoie des valeurs de type double précision.

Les noms de champ suivants sont valides (similaires aux noms de champ de la fonction DATE_PART) : century, day, decade, dow, doy, epoch, hour, isodow, isoyear, microseconds, millennium, milliseconds, minute, month, quarter, second, timezone, timezone_hour, timezone_minute, week, year.

Voici des exemples de la fonction EXTRACT('field', source) :

```sql
testdb=# SELECT EXTRACT(CENTURY FROM TIMESTAMP '2000-12-16 12:21:13');
 date_part
-----------
        20
(1 row)


testdb=# SELECT EXTRACT(DAY FROM TIMESTAMP '2001-02-16 20:38:40');
 date_part
-----------
        16
(1 row)
```

### ISFINITE(date), ISFINITE(timestamp), ISFINITE(interval)

**Function & Description**

- ```ISFINITE(date)``` - Teste pour la date limite.
- ```ISFINITE(timestamp)``` - Teste l'horodateur fini.
- ```ISFINITE(interval)``` - Tests pour un intervalle fini.

Les exemples suivants illustrent les fonctions ```ISFINITE()``` -

```sql
testdb=# SELECT isfinite(date '2001-02-16');
 isfinite
----------
 t
(1 row)


testdb=# SELECT isfinite(timestamp '2001-02-16 21:28:30');
 isfinite
----------
 t
(1 row)


testdb=# SELECT isfinite(interval '4 hours');
 isfinite
----------
 t
(1 row)
```

### JUSTIFY_DAYS(interval), JUSTIFY_HOURS(interval), JUSTIFY_INTERVAL(interval)

**Function & Description**

- ```JUSTIFY_DAYS(interval)``` - Ajuste l'intervalle pour que les périodes de 30 jours soient représentées comme des mois. Retourne le type d'intervalle.
- ```JUSTIFY_HOURS(interval)``` - Ajuste l'intervalle pour que les périodes de 24 heures soient représentées par des jours. Retourne le type d'intervalle.
- ```JUSTIFY_INTERVAL(interval)``` - Ajuste l'intervalle en utilisant JUSTIFY_DAYS et JUSTIFY_HOURS, avec des ajustements de signes supplémentaires. Retourne le type d'intervalle.

Les exemples suivants concernent les fonctions ISFINITE() :

```sql
testdb=# SELECT justify_days(interval '35 days');
 justify_days
--------------
 1 mon 5 days
(1 row)


testdb=# SELECT justify_hours(interval '27 hours');
 justify_hours
----------------
 1 day 03:00:00
(1 row)


testdb=# SELECT justify_interval(interval '1 mon -1 hour');
 justify_interval
------------------
 29 days 23:00:00
(1 row)
```
