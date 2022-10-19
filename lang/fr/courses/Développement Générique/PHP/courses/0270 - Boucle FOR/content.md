La boucle for de PHP peut être utilisée pour parcourir un ensemble de codes pendant un nombre de fois spécifié.

Elle doit être utilisée si le nombre d’itérations est connu, sinon utiliser la boucle while.

## Syntaxe

``` php
for(initialization; condition; increment/decrement){ 
    //code à exécuter 
}
```

## Exemple

``` php
for($n=1;$n<=10;$n++){ 
    echo "$n<br/>"; 
}
```

Dans cet exemple, le résultat renvoyé est :

``` php
1
2
3
4
5
6
7
8
9
10
```

## Boucle For imbriqué

On peut utiliser une boucle for à l’intérieur d’une autre en PHP, on l’appelle boucle for **imbriquée**. En cas de boucle for interne ou imbriquée, la boucle for imbriquée est exécutée intégralement pour une boucle for externe. Si la boucle for externe doit être exécutée 3 fois et la boucle for interne 3 fois, la boucle for interne sera exécutée 9 fois (3 fois pour la première boucle externe, 3 fois pour la 2ᵉ boucle externe et 3 fois pour la 3ᵉ boucle externe).

### Exemple

``` php
for($i=1;$i<=3;$i++){ 
    for($j=1;$j<=3;$j++){ 
        echo "$i   $j<br/>"; 
    } 
}
```

Dans cet exemple, le résultat renvoyé est :

``` php
1  1
1  2
1  3
2  1
2  2
2  3
3  1
3  2
3  3
```