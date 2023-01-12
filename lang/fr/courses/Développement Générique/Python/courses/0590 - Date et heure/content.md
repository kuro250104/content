Un programme Python peut gérer la date et l'heure de plusieurs manières. La conversion entre les formats de date est une tâche courante pour les ordinateurs. Les modules de temps et de calendrier de Python permettent de suivre les dates et les heures.

## Qu'est-ce que Tick ?

Les intervalles de temps sont des nombres à virgule flottante exprimés en unités de secondes. Les instants particuliers dans le temps sont exprimés en secondes depuis le 1er janvier 1970 à 0h00 (époque).

Il existe un module de temps populaire disponible en Python qui fournit des fonctions pour travailler avec les temps, et pour convertir entre les représentations. La fonction ```time.time()``` renvoie l'heure actuelle du système en ticks depuis le 1er janvier 1970 (époque) à 0h00.

## Exemple

```python
#!/usr/bin/python3
import time;      # This is required to include time module.

ticks = time.time()
print("Number of ticks since 12:00am, January 1, 1970:", ticks)
```

Le résultat serait le suivant :

```bash
Number of ticks since 12:00am, January 1, 1970: 1455508609.34375
```

L'arithmétique des dates est facile à réaliser avec des ticks. Cependant, les dates antérieures à l'époque ne peuvent pas être représentées sous cette forme. Les dates dans un futur lointain ne peuvent pas non plus être représentées de cette manière - le point limite se situe en 2038 pour UNIX et Windows.

## Qu'est-ce que TimeTuple ?

De nombreuses fonctions temporelles de Python traitent le temps comme un tuple de 9 nombres, comme indiqué ci-dessous :

| **Index** | **Champ** | **Valeurs** |
| --- | --- | --- |
| 0 | Année (4 chiffres) | 2016 |
| 1 | Mois | 1 to 12 |
| 2 | Jour | 1 to 31 |
| 3 | Heure | 0 to 23 |
| 4 | Minute | 0 to 59 |
| 5 | Seconde | 0 à 61 (60 ou 61 sont des secondes bissextiles) |
| 6 | Jour de la semaine | 0 à 6 (0 est le lundi) |
| 7 | Jour de l'année | 1 à 366 (année bissextile) |
| 8 | L'heure d'été | -1, 0, 1 (-1 signifie que la bibliothèque détermine le DST) |

Par exemple :

```python
import time

print(time.localtime());
```

Le résultat serait le suivant :

```bash
time.struct_time(tm_year = 2016, tm_mon = 2, tm_mday = 15, tm_hour = 9, tm_min = 29, tm_sec = 2, tm_wday = 0, tm_yday = 46, tm_isdst = 0)
```

Le tuple ci-dessus est équivalent à la structure ```struct_time```. Cette structure a les attributs suivants :

| **Index** | **Champ** | **Valeurs** |
| --- | --- | --- |
| 0 | tm_year | 2016 |
| 1 | tm_mon | 1 to 12 |
| 2 | tm_mday | 1 to 31 |
| 3 | tm_hour | 0 to 23 |
| 4 | tm_min | 0 to 59 |
| 5 | tm_sec | 0 à 61 (60 ou 61 sont des secondes bissextiles) |
| 6 | tm_wday | 0 à 6 (0 est le lundi) |
| 7 | tm_yday | 1 à 366 (année bissextile) |
| 8 | tm_isdst | -1, 0, 1 (-1 signifie que la bibliothèque détermine le DST) |

## Obtention de l'heure actuelle

Pour traduire un instant de temps à partir des secondes depuis la valeur à virgule flottante de l'époque en un timetuple, passez la valeur à virgule flottante à une fonction (par exemple, localtime) qui renvoie un time-tuple avec les neuf éléments valides.

```python
#!/usr/bin/python3
import time

localtime = time.localtime(time.time())
print("Local current time :", localtime)
```

Cela produirait le résultat suivant, qui pourrait être formaté sous toute autre forme présentable :

```bash
Local current time : time.struct_time(tm_year = 2016, tm_mon = 2, tm_mday = 15, tm_hour = 9, tm_min = 29, tm_sec = 2, tm_wday = 0, tm_yday = 46, tm_isdst = 0)
```

## Obtenir l'heure formatée

Vous pouvez formater n'importe quelle heure en fonction de vos besoins, mais une méthode simple pour obtenir l'heure dans un format lisible est ```asctime()``` :

```python
#!/usr/bin/python3
import time

localtime = time.asctime( time.localtime(time.time()) )
print("Local current time :", localtime)
```

Cela donnerait le résultat suivant :

```bash
Local current time : Mon Feb 15 09:34:03 2016
```

## Obtenir le calendrier d'un mois

Le module ```calendar``` offre un large éventail de méthodes pour jouer avec les calendriers annuels et mensuels. Ici, nous imprimons un calendrier pour un mois donné (janvier 2008).

```python
#!/usr/bin/python3
import calendar

cal = calendar.month(2016, 2)
print("Here is the calendar:")
print(cal)
```

Cela donnerait le résultat suivant :

```bash
Here is the calendar:
February 2016
Mo Tu We Th Fr Sa Su
1  2  3  4  5  6  7
8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
29
```

## Le module time

Il existe un module populaire nommé ```time``` disponible en Python, qui fournit des fonctions pour travailler avec les temps et pour convertir entre les représentations. Voici la liste de toutes les méthodes disponibles:

- ```time.altzone``` : Le décalage du fuseau horaire DST local, en secondes à l'ouest de UTC, s'il est défini. Il est négatif si le fuseau horaire DST local est à l'est d'UTC (comme en Europe occidentale, y compris le Royaume-Uni). Utilisez ceci si la lumière du jour est non nulle.
- ```time.asctime([tupletime])``` : Accepte un tupletime et renvoie une chaîne de 24 caractères lisible telle que 'Tue Dec 11 18:07:14 2008'.
- ```time.clock( )``` : Renvoie le temps actuel du processeur sous la forme d'un nombre de secondes à virgule flottante. Pour mesurer les coûts de calcul de différentes approches, la valeur de ```time.clock``` est plus utile que celle de ```time.time()```.
- ```time.ctime([secs])``` : Comme ```asctime(localtime(secs))``` et sans arguments comme ```asctime()```.
- ```time.gmtime([secs])``` : Accepte un instant exprimé en secondes depuis l'époque et retourne un time-tuple t avec l'heure UTC. Note - ```t.tm_isdst``` est toujours 0.
- ```time.localtime([secs])``` : Accepte un instant exprimé en secondes depuis l'époque et renvoie un time-tuple t avec l'heure locale (```t.tm_isdst``` est 0 ou 1, selon que l'heure d'été s'applique à l'instant secs selon les règles locales).
- ```time.mktime(tupletime)``` : Accepte un instant exprimé sous la forme d'un tuple de temps en temps local et renvoie une valeur à virgule flottante avec l'instant exprimé en secondes depuis l'époque.
- ```time.sleep(secs)``` : Suspend le thread appelant pendant secs secondes.
- ```time.strftime(fmt[,tupletime])``` : Accepte un instant exprimé sous forme de tupletime en temps local et renvoie une chaîne représentant l'instant tel que spécifié par la chaîne fmt.
- ```time.strptime(str,fmt = '%a %b %d %H:%M:%S %Y')``` : Analyse ```str``` selon le format de la chaîne fmt et renvoie l'instant au format time-tuple.
- ```time.time( )``` : Renvoie l'instant actuel, un nombre de secondes en virgule flottante depuis l'époque.
- ```time.tzset( )``` : Réinitialise les règles de conversion du temps utilisées par les routines de la bibliothèque. La variable d'environnement TZ spécifie comment cela est fait.

Il y a deux attributs importants disponibles avec le module de temps. Il s'agit de :

- ```time.timezone``` : L'attribut ```time.timezone``` est le décalage en secondes du fuseau horaire local (sans DST) par rapport à UTC (>0 dans les Amériques ; <=0 dans la plupart des pays d'Europe, d'Asie et d'Afrique).
- ```time.tzname``` : L'attribut ```time.tzname``` est une paire de chaînes de caractères dépendant du lieu, qui sont les noms du fuseau horaire local sans et avec DST, respectivement.

## Le module calendrier

Le module calendrier fournit des fonctions liées au calendrier, notamment des fonctions permettant d'imprimer un calendrier texte pour un mois ou une année donnés.

Par défaut, le calendrier prend le lundi comme premier jour de la semaine et le dimanche comme dernier jour. Pour changer cela, appelez la fonction ```calendar.setfirstweekday()```.

Voici une liste des fonctions disponibles avec le module ```calendar``` :

- ```calendar.calendar(année,w = 2,l = 1,c = 6)``` : Renvoie une chaîne multiligne contenant un calendrier pour l'année année formatée en trois colonnes séparées par des espaces c. w est la largeur en caractères de chaque date ; chaque ligne a une longueur de 21*w+18+2*c. l est le nombre de lignes pour chaque semaine.
- ```calendar.firstweekday( )``` : Renvoie le paramètre actuel pour le jour de la semaine qui commence chaque semaine. Par défaut, lorsque le calendrier est importé pour la première fois, il est égal à 0, ce qui signifie lundi.
- ```calendar.isleap(year)``` : Renvoie True si l'année est bissextile ; sinon, False.
- ```calendar.leapdays(y1,y2)``` : Renvoie le nombre total de jours bissextiles dans les années comprises dans l'intervalle(y1,y2).
- ```calendar.month(année,mois,w = 2,l = 1)``` : Renvoie une chaîne multiligne contenant un calendrier pour le mois de l'année, une ligne par semaine plus deux lignes d'en-tête. w est la largeur en caractères de chaque date ; chaque ligne a une longueur de 7*w+6. l est le nombre de lignes pour chaque semaine.
- ```calendar.monthcalendar(année,mois)``` : Renvoie une liste de listes d'ints. Chaque sous-liste désigne une semaine. Les jours en dehors du mois de l'année sont définis à 0 ; les jours à l'intérieur du mois sont définis à leur jour du mois, 1 et plus.
- ```calendar.monthrange(année,mois)``` : Renvoie deux entiers. Le premier est le code du jour de la semaine pour le premier jour du mois du mois de l'année de l'année ; le second est le nombre de jours dans le mois. Les codes des jours de la semaine vont de 0 (lundi) à 6 (dimanche) ; les numéros des mois vont de 1 à 12.
- ```calendar.prcal(année,w = 2,l = 1,c = 6)``` : Comme l'impression de ```calendar.calendar(year,w,l,c)```.
- ```calendar.prmonth(année,mois,w = 2,l = 1)``` : Impression similaire à ```calendar.month(année,mois,w,l)```.
- ```calendar.setfirstweekday(jour de la semaine)``` : Définit le premier jour de chaque semaine au code de jour de semaine weekday. Les codes de jour de semaine vont de 0 (lundi) à 6 (dimanche).
- ```calendar.timegm(tupletime)``` : L'inverse de ```time.gmtime``` : accepte un instant sous forme de tupletime et renvoie le même instant sous la forme d'un nombre de secondes en virgule flottante depuis l'époque.
- ```calendar.weekday(année,mois,jour)``` : Renvoie le code du jour de la semaine pour la date donnée. Les codes de jour de semaine vont de 0 (lundi) à 6 (dimanche) ; les numéros de mois vont de 1 (janvier) à 12 (décembre).
