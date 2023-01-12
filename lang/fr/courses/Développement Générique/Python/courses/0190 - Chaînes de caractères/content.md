Les chaînes de caractères sont parmi les types les plus populaires en Python. Nous pouvons les créer simplement en mettant des caractères entre guillemets. Python traite les guillemets simples de la même manière que les guillemets doubles. La création de chaînes de caractères est aussi simple que l'attribution d'une valeur à une variable. Par exemple :

```python
var1 = 'Hello World!'
var2 = "Python Programming"
```

## Accès aux valeurs dans les chaînes de caractères

Python ne supporte pas de type de caractère ; ceux-ci sont traités comme des chaînes de longueur un, donc également considérés comme une sous-chaîne.

Pour accéder aux sous-chaînes, utilisez les crochets pour le découpage en tranches ainsi que l'indice ou les indices pour obtenir votre sous-chaîne. Par exemple :

```python
#!/usr/bin/python3

var1 = 'Hello World!'
var2 = "Python Programming"

print("var1[0]: ", var1[0])
print("var2[1:5]: ", var2[1:5])
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```python
var1[0]:  H
var2[1:5]:  ytho
```

## Mise à jour des chaînes de caractères

Vous pouvez "mettre à jour" une chaîne existante en (ré)affectant une variable à une autre chaîne. La nouvelle valeur peut être liée à sa valeur précédente ou à une chaîne complètement différente. Par exemple :

```python
#!/usr/bin/python3

var1 = 'Hello World!'
print("Updated String :- ", var1[:6] + 'Python')
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Updated String :-  Hello Python
```

## Caractères d'échappement

Le tableau suivant est une liste de caractères d'échappement ou non imprimables qui peuvent être représentés avec la notation backslash.

Un caractère d'échappement est interprété dans une chaîne de caractères entre guillemets simples ou doubles.

| **Notation du backslash** | **Caractère hexadécimal** | **Description** |
| --- | --- | --- |
| \a | 0x07 | Alerte |
| \b | 0x08 | Retour en arrière |
| \cx |  | Control-x |
| \C-x |  | Control-x |
| \e | 0x1b | Echappement |
| \f | 0x0c | Formfeed |
| \M-\C-x |  | Meta-Control-x |
| \n | 0x0a | Nouvelle ligne |
| \nnn |  | Notation octale, où n est compris dans l'intervalle 0,7 |
| \r | 0x0d | Retour à la ligne |
| \s | 0x20 | Espace |
| \t | 0x09 | Tabulation |
| \v | 0x0b | Tabulation verticale |
| \x |  | Caractère x |
| \xnn |  | Notation hexadécimale, où ```n``` est compris entre 0,9, a.f ou A.F. |

## Opérateurs spéciaux pour chaînes de caractères

Supposons que la variable ```a``` soit ```Hello``` et que la variable ```b``` soit ```Python```, alors :

| **Opérateur** | **Description** | **Exemple** |
| --- | --- | --- |
| ```+``` | Concaténation - Ajoute les valeurs de part et d'autre de l'opérateur. | a + b donne HelloPython |
| ```*``` | Répétition - Crée de nouvelles chaînes de caractères, en concaténant plusieurs copies de la même chaîne. | a*2 donne HelloHello |
| ```[]``` | Slice - Donne le caractère à partir de l'indice donné. | a[1] donne e |
| ```[ : ]``` | Range Slice - Donne les caractères de la gamme donnée. | a[1:4] donne ell |
| ```in``` | Adhésion - Retourne vrai si un caractère existe dans la chaîne donnée. | H donne 1 |
| ```not in``` | Adhésion - Renvoie vrai si un caractère n'existe pas dans la chaîne donnée | M ne donne pas 1 |
| ```r/R``` | Chaîne brute - Supprime la signification réelle des caractères d'échappement. La syntaxe des chaînes brutes est exactement la même que celle des chaînes normales, à l'exception de l'opérateur de chaîne brute, la lettre "r", qui précède les guillemets. Le "r" peut être minuscule (r) ou majuscule (R) et doit être placé immédiatement avant le premier guillemet. | print r'\n' donne \n et print R'\n' donne \n |
| ```%``` | Format - Effectue le formatage des chaînes de caractères. | Voir la section suivante |

## Opérateur de formatage de chaîne de caractères

L'une des fonctionnalités les plus intéressantes de Python est l'opérateur de formatage des chaînes de caractères ```%```. Cet opérateur est unique aux chaînes de caractères et compense l'absence de fonctions de la famille ```printf()``` du C. Voici un exemple simple :

```python
#!/usr/bin/python3

print("My name is %s and weight is %d kg!" % ('Zara', 21))
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
My name is Zara and weight is 21 kg!
```

Voici la liste complète des symboles qui peuvent être utilisés avec ```%``` :

- ```%c``` : caractère
- ```%s``` : conversion de chaîne de caractères via str() avant le formatage
- ```%i``` : nombre entier décimal signé
- ```%d``` : nombre entier décimal signé
- ```%u``` : entier décimal non signé
- ```%o``` : nombre entier octal
- ```%x``` : entier hexadécimal (lettres minuscules)
- ```%X``` : entier hexadécimal (lettres majuscules)
- ```%e``` : notation exponentielle (avec 'e' minuscule)
- ```%E``` : notation exponentielle (avec 'E' majuscule)
- ```%f``` : nombre réel à virgule flottante
- ```%g``` : le plus court de %f et %e
- ```%G``` : la plus courte des valeurs %f et %E

Les autres symboles et fonctionnalités pris en charge sont répertoriés dans le tableau suivant :

- ```*``` : L'argument spécifie la largeur ou la précision.
- ```-``` : Justification à gauche.
- ```+``` : Afficher le signe.
- ```<sp>``` : Laisser un espace blanc devant un nombre positif.
- ```#``` : Ajoute le zéro de tête octal ('0') ou le zéro de tête hexadécimal '0x' ou '0X', selon que 'x' ou 'X' a été utilisé.
- ```0``` : Remplissage à partir de la gauche avec des zéros (au lieu d'espaces).
- ```%``` : '%%' vous laisse avec un seul littéral '%'.
- ```(var)``` : Variable de mappage (arguments du dictionnaire).
- ```m.n.``` : m est la largeur totale minimale et n est le nombre de chiffres à afficher après le point décimal (si applicable).

## Triples guillemets

Les triples guillemets de Python viennent à la rescousse en permettant aux chaînes de caractères de s'étendre sur plusieurs lignes, y compris les NOUVELLES LIGNES, les TAB et tout autre caractère spécial.

La syntaxe des guillemets triples consiste en trois guillemets **simples** ou **doubles** consécutifs.

```python
#!/usr/bin/python3

para_str = """this is a long string that is made up of
several lines and non-printable characters such as
TAB ( \t ) and they will show up that way when displayed.
NEWLINEs within the string, whether explicitly given like
this within the brackets [ \n ], or just a NEWLINE within
the variable assignment will also show up.
"""
print(para_str)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant. Notez comment chaque caractère spécial a été converti dans sa forme imprimée, jusqu'à la dernière NOUVELLE LIGNE à la fin de la chaîne entre le "up." et les guillemets fermants. Notez également que les NEWLINEs se produisent soit avec un retour chariot explicite à la fin d'une ligne, soit avec son code d'échappement (\n) : 

```bash
this is a long string that is made up of
several lines and non-printable characters such as
TAB (    ) and they will show up that way when displayed.
NEWLINEs within the string, whether explicitly given like
this within the brackets [
 ], or just a NEWLINE within
the variable assignment will also show up.
```

Les chaînes brutes ne traitent pas du tout la barre oblique inverse comme un caractère spécial. Chaque caractère que vous placez dans une chaîne de caractères brute reste tel que vous l'avez écrit : 

```python
#!/usr/bin/python3

print('C:\\nowhere')
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
C:\nowhere
```

Utilisons maintenant la chaîne brute. Nous mettons l'expression dans ```r'expression'``` comme suit :

```python
#!/usr/bin/python3

print(r'C:\\nowhere')
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
C:\\nowhere
```

## Chaîne Unicode

Dans Python 3, toutes les chaînes de caractères sont représentées en Unicode. Dans Python 2, elles sont stockées en interne en ASCII 8 bits, et il est donc nécessaire d'attacher 'u' pour les rendre Unicode. Ce n'est plus nécessaire maintenant.

### Méthodes intégrées pour les chaînes de caractères

Python intègre les méthodes suivantes pour manipuler les chaînes de caractères : 

- ```capitalize()``` : Met la première lettre de la chaîne en majuscule.
- ```center(width, fillchar)``` : Retourne une chaîne de caractères remplie de fillchar avec la chaîne originale centrée sur un total de colonnes de largeur.
- ```count(str, beg = 0,end = len(string))``` : Compte le nombre d'occurrences de str dans la chaîne ou dans une sous-chaîne de la chaîne si l'indice de départ beg et l'indice d'arrivée end sont donnés.
- ```decode(encoding = 'UTF-8',errors = 'strict')``` : Décode la chaîne en utilisant le codec enregistré pour l'encodage. L'encodage prend par défaut l'encodage de chaîne par défaut.
- ```encode(encoding = 'UTF-8',errors = 'strict')``` : Retourne la version encodée de la chaîne de caractères ; en cas d'erreur, la valeur par défaut est une ValueError, sauf si errors est donné avec 'ignore' ou 'replace'.
- ```endswith(suffixe, beg = 0, end = len(string))``` : Détermine si une chaîne de caractères ou une sous-chaîne de caractères (si l'indice de départ beg et l'indice d'arrivée end sont donnés) se termine par un suffixe ; renvoie true si c'est le cas et false sinon.
- ```expandtabs(tabsize = 8)``` : Étend les tabulations de la chaîne à plusieurs espaces ; par défaut, 8 espaces par tabulation si tabsize n'est pas fourni.
- ```find(str, beg = 0 end = len(string))``` : Détermine si str se trouve dans la chaîne ou dans une sous-chaîne de la chaîne si l'indice de départ beg et l'indice de fin end sont donnés ; renvoie l'indice si trouvé et -1 sinon.
- ```index(str, beg = 0, end = len(string))``` : Identique à find(), mais lève une exception si str n'est pas trouvé.
- ```isalnum()``` : Retourne vrai si la chaîne a au moins 1 caractère et que tous les caractères sont alphanumériques et faux sinon.
- ```isalpha()``` : Retourne vrai si la chaîne a au moins un caractère et que tous les caractères sont alphabétiques et faux sinon.
- ```isdigit()``` : Retourne vrai si la chaîne ne contient que des chiffres et faux sinon.
- ```islower()``` : Retourne vrai si la chaîne de caractères a au moins un caractère en minuscule et que tous les caractères en minuscule sont en minuscule et faux sinon.
- ```isnumeric()``` : Retourne vrai si une chaîne unicode ne contient que des caractères numériques et faux sinon.
- ```isspace()``` : Retourne vrai si une chaîne ne contient que des caractères d'espacement et faux sinon.
- ```istitle()``` : Retourne vrai si la chaîne est correctement "titrée" et faux sinon.
- ```isupper()``` : Retourne vrai si la chaîne a au moins un caractère en majuscule et que tous les caractères en majuscule sont en majuscule et faux sinon.
- ```join(seq)``` : Fusionne (concatène) les représentations des chaînes de caractères des éléments de la séquence seq en une chaîne de caractères, avec le séparateur string.
- ```len(string)``` : Retourne la longueur de la chaîne de caractères.
- ```ljust(width[, fillchar])``` : Retourne une chaîne de caractères avec des espaces, la chaîne originale étant justifiée à gauche pour un total de colonnes de largeur.
- ```lower()``` : Convertit toutes les lettres majuscules de la chaîne en minuscules.
- ```lstrip()``` : Supprime tous les espaces en tête de la chaîne.
- ```maketrans()``` : Retourne une table de traduction à utiliser dans la fonction translate.
- ```max(str)``` : Retourne le caractère alphabétique maximum de la chaîne de caractères str.
- ```min(str)``` : Retourne le caractère alphabétique minimum de la chaîne de caractères str.
- ```replace(old, new [, max])``` : Remplace toutes les occurrences de old dans la chaîne par new ou au maximum par max si max est donné.
- ```rfind(str, beg = 0,end = len(string))``` : Identique à find(), mais recherche en arrière dans la chaîne.
- ```rindex( str, beg = 0, end = len(string))``` : Identique à index(), mais recherche en arrière dans la chaîne.
- ```rjust(width,[, fillchar])``` : Retourne une chaîne de caractères avec des espaces, la chaîne originale étant justifiée à droite sur un total de colonnes de largeur.
- ```rstrip()``` : Supprime tous les espaces blancs de fin de chaîne.
- ```split(str="", num=string.count(str))``` : Divise une chaîne de caractères selon le délimiteur str (espace si non fourni) et retourne une liste de sous-chaînes ; divisée en un maximum de num sous-chaînes si donné.
- ```splitlines( num=string.count('\n'))``` : Scinde la chaîne de caractères à toutes (ou num) les NOUVELLES LIGNES et retourne une liste de chaque ligne avec les NOUVELLES LIGNES supprimées.
- ```startswith(str, beg=0,end=len(string))``` : Détermine si la chaîne ou une sous-chaîne de la chaîne (si l'indice de départ beg et l'indice d'arrivée end sont donnés) commence par la sous-chaîne str ; renvoie true si c'est le cas et false sinon.
- ```strip([chars])``` : Effectue à la fois lstrip() et rstrip() sur une chaîne de caractères.
- ```swapcase()``` : Inverse la casse pour toutes les lettres de la chaîne.
- ```title()``` : Retourne la version "titlecased" de la chaîne, c'est-à-dire que tous les mots commencent par une majuscule et le reste est en minuscule.
- ```translate(table, deletechars="")``` : Traduit la chaîne de caractères selon la table de traduction str(256 caractères), en supprimant ceux de la chaîne del.
- ```upper()``` : Convertit les lettres minuscules de la chaîne en majuscules.
- ```zfill (width)``` : Retourne la chaîne de caractères d'origine caviardée de zéros jusqu'à une largeur totale de caractères ; destiné aux nombres, zfill() conserve tout signe donné (moins un zéro).
- ```isdecimal()``` : Retourne vrai si une chaîne unicode ne contient que des caractères décimaux et faux sinon.
