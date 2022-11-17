Les opérateurs logiques sont un moyen d’enchaîner les opérateurs de comparaisons. De la même manière qu’en mathématiques, ils disposent chacun d’une priorité d’exécution. À l’image de certains opérateurs mathématiques comme la multiplication ou la division qui sont prioritaires face à des additions ou soustractions, les opérateurs logiques informatiques induisent des règles similaires qui leur sont propres.

## L’opérateur “et”

L’opérateur “**et**” permet de tester si plusieurs comparaisons sont vraies ou fausses. Cet opérateur suis la logique suivante : 

- “vrai” **et** “vrai” donnent un résultat “vrai”
- “vrai **et** “faux” donnent un résultat “faux”
- “faux” **et** “faux donnent un résultat “faux”

Il peut être symbolisé de deux façons différentes en PHP : soit par le symbole “**&&**”, soit par le mot-clé “**AND**”. Ces deux représentations sont presque équivalentes, à ceci près que le symbole “**&&**” disposera d’une priorité d’exécution plus élevée que le mot-clé “**AND**”.

Par ailleurs, l’utilisation de cet opérateur logique n'entraîne pas obligatoirement la vérification de toutes les comparaisons effectuées. En effet, si l’une d’entre elles est fausse, alors le retour sera obligatoirement faux. Ceci évitant à PHP d’opérer des comparaisons, et donc des calculs, pour rien.

```php
# Déclaration de deux variables afin de tester nos opérateurs logiques
$a = 0;
$b = 1;

# comparaison logique de "$a" et "$b"
echo( $a == 0 AND $b == 1 );
# Lors de la vérification de cet opérateur logique, PHP commencera par 
# vérifier la première # condition, "$a == 0". Le résultat étant vrai, 
# on pourrait schématiser l'opération comme suit :

# echo( vrai AND $b == 1 );

# Comme la première condition est vraie, alors PHP va vérifier la seconde condition "$b == 1".

# Étant donné que celle-ci est également vraie, alors on arrive à la 
# comparaison suivante : 

# echo( vrai AND vrai );

# ainsi en se référant aux logiques de cet opérateur, on arrive à un 
# résultat qui sera "vrai"

# seconde comparaison logique de "$a" et "$b"
echo( $a == 1 AND $b == 1 );
# PHP commencera ici par tester la première comparaison "$a == 1". 
# Celle-ci est fausse étant donné que "$a" est égal à zéro. Ainsi PHP ne 
# ne prendra pas la peine de vérifier la deuxième comparaison et
# renverra directement "faux" sur cette comparaison logique.

# troisième comparaison logique de "$a" et "$b"
echo( $a == 0 AND $b == 2 );
# La première comparaison "$a == 0" renverra "vrai". On obtiendra alors la transformation 
# suivante : 
# echo( vrai AND $b == 2 );
# La seconde comparaison "$b == 2" renverra "faux". La logique appliquée 
# de l'opérateur "AND" renverra donc “faux”.
```

Il est important de noter que dans tous les exemples présentés ci-dessus, le mot-clé “**AND**” est utilisé. Celui-ci aurait pu être remplacé par le double symbole “**&&**” sans qu’aucun changement ne s’opère et les résultats auraient été identiques.

## L’opérateur “ou”

L’opérateur “ou” permet de tester si au moins une des comparaisons effectuées est vraie ou fausse. Cet opérateur suis la logique suivante : 

- “vrai” **ou** “vrai” renvoie “vrai”
- “vrai” **ou** “faux” renvoie “vrai”
- “faux” **ou** “faux” renvoie “faux”

Cet opérateur renvoie ainsi “vrai” tant que l’un des éléments comparés est également “vrai”. Il est représenté de deux manières : avec le mot-clé “**OR**” ou bien avec le double symbole “**||**”.

A contrario de l’opérateur “et”, l’opérateur “ou” renverra vrai, même si une seule des conditions comparées est vraie. Ainsi PHP testera chacune des comparaisons à tour de rôle jusqu’à obtenir un résultat de comparaison “vrai”, ou bien renverra “faux” si aucune n’est trouvée.

```php
# Déclaration de deux variables afin de tester nos opérateurs logiques
$a = 0;
$b = 1;

# comparaison logique de "$a" ou "$b"
echo( $a == 0 OR $b == 1 );
# Lors de la vérification de cet opérateur logique, PHP commencera par 
# vérifier la première # condition, "$a == 0". Le résultat étant vrai, 
# PHP ne testera pas la seconde comparaison, il retournera directement 
#"vrai".

# seconde comparaison logique de "$a" ou "$b"
echo( $a == 1 OR $b == 1 );
# PHP commencera ici par tester la première comparaison "$a == 1". 
# Celle-ci est fausse 
# Étant donné que "$a" est égal à zéro. Ainsi PHP va tester la prochaine 
# comparaison afin 
# de déterminer si au moins une est vraie : 
# "$b == 1" étant vrai, alors la comparaison logique renverra "vrai"

# troisième comparaison logique de "$a" ou "$b"
echo( $a == 1 OR $b == 2 );
# La première comparaison "$a == 1" renverra "faux". PHP testera donc la 
# comparaison 
# suivante "$b == 2". Celle-ci étant "fausse" également, alors la 
# comparaison logique renverra la valeur "faux".
```

À noter ici aussi que le mot-clé utilisé pour ces exemples est le “**OR**”. Celui-ci pourrait être remplacé par le double symbole “**||**” sans qu’aucun changement n’apparaisse.

## L’opérateur “ou exclusif”

L’opérateur “ou exclusif” permet de tester si une des comparaisons effectuées est vraie ou fausse, mais que les deux soient différentes ! Ainsi l’opérateur plus communément appelé par son mot-clé “**XOR**” suit la logique suivante : 

- “vrai” **XOR** “vrai” renvoie “faux”
- “vrai” **XOR** “faux” renvoie “vrai”
- “faux” **XOR** “faux” renvoie “faux”

Le principe d’utilisation de cet opérateur logique est donc de déterminer si deux comparaisons ont des résultats semblables ou non.

```php
# Déclaration de deux variables afin de tester nos opérateurs logiques
$a = 0;
$b = 1;

# premier test du "XOR"
echo( $a == 0 XOR $b == 1 );
# La première comparaison "$a == 0" est vraie. La seconde comparaison 
# "$b == 1" l'est également. Ainsi en suivant la logique de l'opérateur, 
# un résultat "faux" sera renvoyé.

# second test du "XOR"
echo( $a == 3 XOR $b == 1 );
# La première comparaison "$a == 3" est vraie. La seconde comparaison 
# "$b == 1" est fausse. En suivant la logique de l'opérateur "XOR", un 
# résultat "vrai" sera donc renvoyé.
```

## L’opérateur “NON”

L’opérateur “NON” est un opérateur de négation. Il s’exprime avec un point d’exclamation (!) et permet de tester l’inverse d’un état. Il présente ainsi la logique suivante : 

- **NON** “vrai” renverra “faux”
- **NON** “faux” renverra “vrai”

```php
# Déclaration d'une variable "$a" ayant pour valeur "0"
$a = 0;
$b = 1;

# Premier test avec l'opérateur "NON"
echo( !$a == 1 );
# L'exécution de la ligne ci-dessus, entraînera le test de la 
# comparaison "$a == 1". Cette comparaison est "fausse". Ainsi l'inverse 
# de la comparaison exercée par l'opérateur logique "NON" renverra 
# "vrai"

# Deuxième test
echo( !$b == 1 );
# De la même manière que dans le premier exemple, la première 
# comparaison effectuée sera "$b == 1", qui est donc "vraie". Ainsi 
# l'inverse de la comparaison étant testée du fait de l'opérateur 
# logique "NON" ( ! ), le résultat retourné sera "faux"
```