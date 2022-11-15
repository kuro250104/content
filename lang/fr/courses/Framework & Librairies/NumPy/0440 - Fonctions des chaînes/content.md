## Introduction

Les fonctions suivantes sont utilisées pour effectuer des opérations vectorielles sur des tableaux de type numpy.string_ ou numpy.unicode_. Elles sont basées sur les fonctions standard de la bibliothèque intégrée de Python.

**Fonction et description**

- ```add()``` - Renvoie la concaténation de chaînes par éléments pour deux tableaux de str ou Unicode.
- ```multiply()``` - Renvoie la chaîne de caractères avec concaténation multiple, par éléments.
- ```center()``` - Renvoie une copie de la chaîne de caractères donnée avec des éléments centrés dans une chaîne de caractères de longueur spécifiée.
- ```capitalize()``` - Renvoie une copie de la chaîne de caractères avec seulement le premier caractère en majuscule.
- ```title()``` - Renvoie la version casée par élément de la chaîne ou de l'unicode
- ```lower()``` - Retourne un tableau dont les éléments sont convertis en minuscules.
- ```upper()``` - Retourne un tableau dont les éléments sont convertis en majuscules.
- ```split()``` - Renvoie une liste des mots de la chaîne, en utilisant le séparateur de mots.
- ```splitlines()``` - Renvoie une liste des lignes de l'élément, avec une rupture aux limites de la ligne.
- ```strip()``` - Renvoie une copie dont les caractères de tête et de queue ont été supprimés.
- ```join()``` - Renvoie une chaîne qui est la concaténation des chaînes de la séquence
- ```replace()``` - Renvoie une copie de la chaîne avec toutes les occurrences de la sous-chaîne remplacées par la nouvelle chaîne.
- ```decode()``` - Appelle str.decode par élément
- ```encode()``` - Appelle str.encode par élément

Ces fonctions sont définies dans la classe des tableaux de caractères (```numpy.char```). L'ancien paquetage Numarray contenait la classe chararray. Les fonctions ci-dessus dans la classe ```numpy.char``` sont utiles pour effectuer des opérations vectorielles sur les chaînes de caractères.