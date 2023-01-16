Une expression régulière est une séquence spéciale de caractères qui vous aide à faire correspondre ou à trouver d'autres chaînes ou ensembles de chaînes, en utilisant une syntaxe spécialisée contenue dans un motif. Les expressions régulières sont largement utilisées dans le monde UNIX.

Le module ```re``` fournit un support complet des expressions régulières de type Perl en Python. Le module ```re``` soulève l'exception ```re.error``` si une erreur se produit lors de la compilation ou de l'utilisation d'une expression régulière.

Nous allons couvrir deux fonctions importantes, qui seront utilisées pour manipuler les expressions régulières. Néanmoins, une petite chose d'abord : Il existe plusieurs caractères qui ont une signification particulière lorsqu'ils sont utilisés dans une expression régulière. Pour éviter toute confusion lors du traitement des expressions régulières, nous utiliserons les chaînes brutes comme ```r'expression'```.

## Modèles de base qui correspondent à des caractères uniques

- ```a, X, 9, <``` : Les caractères ordinaires se correspondent exactement.
- ```. (un point)``` : Correspond à n'importe quel caractère unique, à l'exception de la nouvelle ligne '\n'.
- ```\w``` : Correspond à un caractère "mot" : une lettre, un chiffre ou une barre inférieure [a-zA-Z0-9_].
- ```\W``` : Correspond à tout caractère autre qu'un mot.
- ```\b``` : Limite entre le mot et le non-mot.
- ```\s``` : Correspond à un seul caractère d'espace -- espace, nouvelle ligne, retour, tabulation.
- ```\S``` : Correspond à tout caractère autre qu'un espace.
- ```\t, \n, \r``` : Tabulation, nouvelle ligne, retour.
- ```\d``` : Chiffre décimal [0-9].
- ```^``` : Correspond au début de la chaîne.
- ```$``` : Correspond à la fin de la chaîne de caractères.
- ```\N``` : Inhibe la "spécificité" d'un caractère.

## Indicateurs de compilation

Les indicateurs de compilation vous permettent de modifier certains aspects du fonctionnement des expressions régulières. Les drapeaux sont disponibles dans le module re sous deux noms, un nom long tel que ```IGNORECASE``` et une forme courte à une lettre telle que I.

- ```ASCII, A``` : Fait en sorte que plusieurs échappatoires comme \w, \b, \s et \d ne correspondent qu'aux caractères ASCII ayant la propriété respective.
- ```DOTALL, S``` : Fait correspondre n'importe quel caractère, y compris les nouvelles lignes.
- ```IGNORECASE, I``` : Effectuer des correspondances insensibles à la casse.
- ```LOCALE, L``` : Effectuer une correspondance locale.
- ```MULTILINE, M``` : Correspondance multi-lignes, affectant ^ et $.
- ```VERBOSE, X (pour 'extended')``` : Active les REs verbeux, qui peuvent être organisés de manière plus propre et plus compréhensible.

## La fonction match

Cette fonction tente de faire correspondre un motif RE à une chaîne de caractères avec des drapeaux optionnels.

Voici la syntaxe de cette fonction :

```python
re.match(pattern, string, flags = 0)
```

Voici la description des paramètres :

- ```pattern``` : C'est l'expression régulière à faire correspondre.
- ```string``` : C'est la chaîne de caractères, qui sera recherchée pour faire correspondre le motif au début de la chaîne.
- ```flags``` : Vous pouvez spécifier différents drapeaux en utilisant l'opérateur OU (|). Ce sont des modificateurs, qui sont énumérés dans le tableau ci-dessous.

La fonction re.match renvoie un objet ```match``` en cas de succès, None en cas d'échec. Nous utilisons la ```fonctiongroup(num)``` ou ```groups()``` de l'objet ```match``` pour obtenir les expressions correspondantes.

- ```group(num = 0)``` : Cette méthode renvoie la correspondance complète (ou un sous-groupe spécifique).
- ```groups()``` : Cette méthode renvoie tous les sous-groupes correspondants dans un tuple (vide s'il n'y en a pas).

### Exemple

```python
#!/usr/bin/python3
import re

line = "Cats are smarter than dogs"

matchObj = re.match( r'(.*) are (.*?) .*', line, re.M|re.I)

if matchObj:
    print("matchObj.group() :", matchObj.group())
    print("matchObj.group(1) :", matchObj.group(1))
    print("matchObj.group(2) :", matchObj.group(2))
else:
    print("No match!!")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
matchObj.group() : Cats are smarter than dogs
matchObj.group(1) : Cats
matchObj.group(2) : smarter
```

## La fonction de recherche

Cette fonction recherche la première occurrence du motif ```RE``` dans une chaîne de caractères avec des drapeaux optionnels.

Voici la syntaxe de cette fonction :

```python
re.search(pattern, string, flags = 0)
```

Voici la description des paramètres :

- ```pattern``` : C'est l'expression régulière à faire correspondre.
- ```string``` : C'est la chaîne de caractères, qui sera recherchée pour faire correspondre le motif n'importe où dans la chaîne.
- ```flags``` : Vous pouvez spécifier différents drapeaux à l'aide de l'opérateur OU (|). Ce sont des modificateurs, qui sont énumérés dans le tableau ci-dessous.

La fonction ```re.search``` renvoie un objet ```match``` en cas de succès, none en cas d'échec. Nous utilisons la fonction ```group(num)``` ou ```groups()``` de l'objet ```match``` pour obtenir l'expression correspondante.

- ```groupe(num = 0)``` : Cette méthode renvoie la correspondance complète (ou un sous-groupe spécifique num).
- ```group()``` : Cette méthode renvoie tous les sous-groupes correspondants dans un tuple (vide s'il n'y en a pas).

### Exemple

```python
#!/usr/bin/python3
import re

line = "Cats are smarter than dogs";

searchObj = re.search( r'(.*) are (.*?) .*', line, re.M|re.I)

if searchObj:
   print("searchObj.group() :", searchObj.group())
   print("searchObj.group(1) :, searchObj.group(1))
   print("searchObj.group(2) :", searchObj.group(2))
else:
   print("Nothing found!!")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
matchObj.group() : Cats are smarter than dogs
matchObj.group(1) : Cats
matchObj.group(2) : smarter
```

## Correspondance et recherche

Python propose deux opérations primitives différentes basées sur les expressions régulières : ```match``` vérifie une correspondance uniquement au début de la chaîne, tandis que ```search``` vérifie une correspondance n'importe où dans la chaîne (c'est ce que fait Perl par défaut).

### Exemple

```python
#!/usr/bin/python3
import re

line = "Cats are smarter than dogs"

matchObj = re.match( r'dogs', line, re.M|re.I)
if matchObj:
    print("match --> matchObj.group() :", matchObj.group())
else:
    print("No match!!")

searchObj = re.search( r'dogs', line, re.M|re.I)
if searchObj:
    print("search --> searchObj.group() :", searchObj.group())
else:
    print("Nothing found!!")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
No match!!
search --> matchObj.group() : dogs
```

## Recherche et remplacement

L'une des plus importantes méthodes de ```re``` qui utilisent les expressions régulières est le remplacement.

### Syntaxe

```python
re.sub(pattern, repl, string, max=0)
```

Cette méthode remplace toutes les occurrences du motif ```RE``` dans la chaîne par ```repl```, en substituant toutes les occurrences, sauf si ```max``` est fourni. Cette méthode retourne la chaîne modifiée.

### Exemple

```python
#!/usr/bin/python3
import re

phone = "2004-959-559 # This is Phone Number"

# Delete Python-style comments
num = re.sub(r'#.*$', "", phone)
print("Phone Num :", num)

# Remove anything other than digits
num = re.sub(r'\D', "", phone)    
print("Phone Num :", num)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Phone Num : 2004-959-559
Phone Num : 2004959559
```

## Modificateurs d'expressions régulières : Drapeaux d'option

Les littéraux d'expression régulière peuvent inclure un modificateur facultatif pour contrôler divers aspects de la correspondance. Les modificateurs sont spécifiés sous la forme d'un drapeau optionnel. Vous pouvez fournir plusieurs modificateurs à l'aide de l'opérateur OU exclusif (```|```), comme indiqué précédemment, et ils peuvent être représentés par l'un des éléments suivants :

- ```re.I``` : Effectue une correspondance insensible à la casse.
- ```re.L``` : Interprète les mots en fonction de la locale actuelle. Cette interprétation affecte le groupe alphabétique (\w et \W), ainsi que le comportement des limites de mots (\b et \B).
- ```re.M``` : fait correspondre $ à la fin d'une ligne (et pas seulement à la fin de la chaîne) et fait correspondre ^ au début de n'importe quelle ligne (et pas seulement au début de la chaîne).
- ```re.S``` : Le point correspond à n'importe quel caractère, y compris une nouvelle ligne.
- ```re.U``` : Interprète les lettres selon le jeu de caractères Unicode. Cet indicateur affecte le comportement de \w, \W, \b, \B.
- ```re.X``` : Permet d'utiliser une syntaxe d'expression régulière "plus mignonne". Elle ignore les espaces blancs (sauf à l'intérieur d'un ensemble [] ou lorsqu'ils sont échappés par une barre oblique inverse) et traite le # non encodé comme un marqueur de commentaire.

## Motifs d'expression régulière

À l'exception des caractères de contrôle, (+ ? . * ^ $ ( ) [ ] { } | \), tous les caractères se correspondent entre eux. Vous pouvez échapper à un caractère de contrôle en le faisant précéder d'une barre oblique inverse.

### Classes de caractères

- ```[Pp]ython``` : Correspond à "Python" ou "python".
- ```rub[ye]``` : Correspond à "ruby" ou "rube".
- ```[aeiou]``` : Correspond à une voyelle minuscule au choix.
- ```[0-9]``` : Correspond à n'importe quel chiffre ; identique à [0123456789].
- ```[a-z]``` : Correspond à n'importe quelle lettre ASCII minuscule.
- ```[A-Z]``` : Correspond à n'importe quelle lettre ASCII majuscule.
- ```[a-zA-Z0-9]``` : Correspond à n'importe laquelle des lettres ci-dessus.
- ```[^aeiou]``` : Correspond à tout ce qui n'est pas une voyelle minuscule.
- ```[^0-9]``` : Correspond à tout ce qui n'est pas un chiffre.

### Classes de caractères spéciaux

- ```.``` : Correspond à n'importe quel caractère sauf le saut de ligne.
- ```\d``` : Correspond à un chiffre : ```[0-9]```.
- ```\D``` : Correspond à un non-chiffre : ```[^0-9]```.
- ```\s``` : Correspond à un caractère d'espacement : ```[ \t\r\n\f]```.
- ```\S``` : Correspond à un caractère sans espace : ```[^ \t\r\n\f]```.
- ```\w``` : Correspond à un seul caractère de mot : ```[A-Za-z0-9_]```.
- ```\W``` : Correspond à un caractère non-mot : ```[^A-Za-z0-9_]```.

### Cas de répétition

- ```ruby ?``` : Correspond à "rub" ou "ruby" : le y est optionnel.
- ```ruby*``` : Correspond à "rub" plus 0 ou plus ys.
- ```ruby+``` : Correspond à "rub" plus 1 y ou plus.
- ```\d{3}``` : Correspond à 3 chiffres exactement.
- ```\d{3,}``` : Correspond à 3 chiffres ou plus.
- ```\d{3,5}``` : Correspond à 3, 4 ou 5 chiffres.

### Répétition non avortée

Cela correspond au plus petit nombre de répétitions :

- ```<.*>``` : Greedy repetition: matches ```<python>perl>```.
- ```<.*?>``` : Nongreedy: matches ```<python>``` in ```<python>perl>```.

### Regroupement avec parenthèses

- ```\D\d+``` : Pas de groupe : + répète ```\d```.
- ```(\D\d)+``` : Groupé : + répète la paire ```\D\d```.
- ```([Pp]ython(,) ?)+``` : Correspond à "Python", "Python, python, python", etc.

### Références de retour

Cette fonction permet de faire correspondre à nouveau un groupe précédemment apparié :

- ```([Pp])ython&\1ails``` : Match ```python&pails``` or ```Python&Pails```.
- ```(['"])[^\1]*\1``` : Single or double-quoted string. \1 matches whatever the 1st group matched. \2 matches whatever the 2nd group matched, etc.

### Alternatives

- ```python|perl``` : Correspond à "python" ou "perl".
- ```rub(y|le)``` : Correspond à "ruby" ou "ruble".
- ```Python(!+|\ ?)``` : "Python" suivi d'un ou plusieurs ! ou d'un ?

### Ancres

Il faut préciser la position du match.

- ```^Python``` : Correspond à "Python" au début d'une chaîne ou d'une ligne interne.
- ```Python$``` : Correspond à "Python" à la fin d'une chaîne ou d'une ligne.
- ```\APython``` : Correspond à "Python" au début d'une chaîne de caractères.
- ```Python\Z``` : Correspond à "Python" à la fin d'une chaîne de caractères.
- ```\bPython\b``` : Correspond à "Python" à la limite d'un mot.
- ```\brub\B``` : ```\B``` est une limite de non-mot : Correspond à "rub" dans "rube" et "ruby" mais pas seul.
- ```Python(?= !)``` : Correspond à "Python", s'il est suivi d'un point d'exclamation.
- ```Python( ?!!)``` : Correspond à "Python", s'il n'est pas suivi d'un point d'exclamation.

### Syntaxe spéciale avec parenthèses

- ```R(?#comment)``` : Correspond à "R". Le reste est un commentaire.
- ```R(?i)uby``` : Insensible à la casse lors de la recherche de "uby".
- ```R(?i:uby)``` : Idem que ci-dessus.
- ```rub(?:y|le))``` : Groupe seulement sans créer de référence arrière \1.
