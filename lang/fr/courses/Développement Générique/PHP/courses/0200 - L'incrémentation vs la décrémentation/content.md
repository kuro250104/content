Parfois, il est nécessaire d’ajouter ou d’enlever 1 à un nombre. C’est le cas lorsque qu’un compteur est créé, par exemple. Dans un tel cas, il est nécessaire de pouvoir incrémenter ou décrémenter un nombre. 

Incrémenter signifie ajouter 1 à un nombre ; tandis que décrémenter signifie : ôter 1 à un nombre.

## Incrémentation

Il existe deux moyens d’incrémenter un nombre

### ++$a

```$a``` représente la variable à incrémenter et le double plus (```++```) est le signe d’incrémentation en PHP. 

Incrémenter un nombre en utilisant l’écriture ```++$a``` ajoute 1 au nombre **puis** le retourne.

Exemple :

``` php
$a = 0;
echo ++$a; # retourne 1
echo $a; # retourne 1
```

### $a++

Cette manière d’incrémenter un nombre fait l’exact contraire de la manière détaillée au point précédent. En d’autres termes, ici, le nombre est d’abord retourné, **puis** 1 est ajouté.

Exemple :

``` php
$a = 0;
echo $a++; # retourne 0
echo $a; # retourne 1
```

## Décrémentation

La décrémentation permet d’enlever 1 au nombre. Comme pour l’incrémentation, il existe, en PHP, deux façons de décrémenter un nombre, qui sont les mêmes que pour l’incrémentation.

### --$a 

Cette manière de décrémenter enlève 1 au nombre puis le retourne.

Exemple :

``` php
$a = 10;
echo $a--; # retourne 9
echo $a; # retourne 9
```

### --$a

Cette manière de décrémenter retourne le nombre **puis** enlève 1.

Exemple :

``` php
$a = 10;
echo --$a; # retourne 10
echo $a; # retourne 9
```