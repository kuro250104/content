La boucle While de PHP peut être utilisée pour parcourir un ensemble de code comme pour une boucle.

Elle est utilisée si le nombre d’itérations n’est pas connu.

syntaxe :

``` php
while(condition){ 
    //code à exécuter 
}
```

autre syntaxe :

``` php
while(condition): 
    //code à exécuter 
endwhile;
```

exemple :

``` php
$n=1; 
while($n<=10){ 
    echo "$n<br/>"; 
    $n++; 
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

autre exemple :

``` php
$n=1; 
while($n<=10): 
    echo "$n<br/>"; 
    $n++; 
endwhile;
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

## Boucle WHILE imbriqué

On peut utiliser la boucle while dans une autre boucle while en PHP, on l’appelle imbriquée.

En cas de boucle While interne ou imbriquée, la boucle While imbriquée est exécutée intégralement pour une boucle While externe. Si la boucle While externe doit être exécutée 3 fois et imbriquée 3 fois, la boucle While imbriquée sera exécutée 9 fois (3 fois pour la 1ère boucle externe, 3 fois pour la 2ᵉ boucle externe et 3 fois pour la 3ᵉ boucle externe).

exemple :

``` php
$i=1; 
while($i<=3){ 
    $j=1; 
    while($j<=3){ 
        echo "$i   $j<br/>"; 
        $j++; 
    } 
    $i++; 
}
```

Dans cet exemple, le résultat renvoyé est :

``` php
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3
```