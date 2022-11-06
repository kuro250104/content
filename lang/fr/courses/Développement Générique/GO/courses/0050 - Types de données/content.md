Dans le langage de programmation Go, les types de données font référence à un système étendu utilisé pour déclarer des variables ou des fonctions de différents types. Le type d'une variable détermine l'espace qu'elle occupe dans le stockage et la manière dont le modèle binaire stocké est interprété.

Les types de Go peuvent être classifiés comme suit :

**Types et description**

- **Types booléens** : Ce sont des types booléens et sont constitués des deux constantes prédéfinies : (a) vrai (b) faux
- **Types numériques** : Ce sont encore des types arithmétiques et ils représentent a) des types entiers ou b) des valeurs à virgule flottante tout au long du programme.
- **Types de chaîne de caractères** : Un type chaîne de caractères représente l'ensemble des valeurs des chaînes de caractères. Sa valeur est une séquence d'octets. Les chaînes de caractères sont des types immuables, c'est-à-dire qu'une fois créées, il n'est pas possible de modifier le contenu d'une chaîne de caractères. Le type de chaîne prédéclaré est string.
- **Types dérivés** : Ils comprennent (a) les types Pointeur, (b) les types Tableau, (c) les types Structure, (d) les types Union et (e) les types Fonction f) les types Tranche g) les types Interface h) les types Carte i) les types Canal

Les types de tableaux et les types de structures sont collectivement appelés types d'agrégats. Le type d'une fonction spécifie l'ensemble de toutes les fonctions ayant les mêmes types de paramètres et de résultats. Nous allons aborder les types de base dans la section suivante, tandis que les autres types seront traités dans les chapitres suivants.

## Types de nombres entiers

Les types d'entiers prédéfinis indépendants de l'architecture sont :

**Types et description**

- **uint8** : Entiers non signés de 8 bits (0 à 255)
- **uint16** : Entiers non signés de 16 bits (0 à 65535)
- **uint32** : Entiers non signés de 32 bits (0 à 4294967295)
- **uint64** : Entiers non signés de 64 bits (0 à 18446744073709551615)
- **int8** : Entiers signés de 8 bits (-128 à 127)
- **int16** : Entiers signés de 16 bits (-32768 à 32767)
- **int32** : Entiers signés de 32 bits (-2147483648 à 2147483647)
- **int64** : Entiers signés de 64 bits (-9223372036854775808 à 9223372036854775807)

## Types flottants

Les types de flotteurs prédéfinis, indépendants de l'architecture, sont :

**Types et description**

- **float32** : Nombres à virgule flottante 32 bits IEEE-754
- **float64** : Nombres à virgule flottante de 64 bits de la norme IEEE-754
- **complexe64** : Nombres complexes avec parties réelles et imaginaires de float32
- **complex128** : Nombres complexes avec parties réelles et imaginaires float64

La valeur d'un nombre entier de n bits est de n bits et est représentée par des opérations arithmétiques de complément à deux.

## Autres types de chiffres

Il existe également un ensemble de types numériques avec des tailles spécifiques à l'implémentation.

**Types et description**

- **octet** : identique à uint8
- **rune** : identique à int32
- **uint** : 32 ou 64 bits
- **int** : même taille que uint
- **uintptr** : un entier non signé pour stocker les bits non interprétés d'une valeur de pointeur