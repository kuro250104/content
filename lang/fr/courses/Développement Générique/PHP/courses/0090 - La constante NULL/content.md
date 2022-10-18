Il est recommandé de toujours initialiser une variable lors de sa déclaration. Cela évite des erreurs ou des résultats inattendus dus au fait qu’une valeur au hasard a été attribuée à la variable par la mémoire de l’ordinateur. 

Seulement voilà, se pose le problème suivant : comment faire si une variable doit être déclarée, mais que sa valeur n’est pas connue de suite par le programme - principalement parce que c’est une valeur fournie par l’utilisateur ?

C’est justement pour résoudre ce problème que la constante **NULL** entre en jeu. **NULL**, en fait, représente la valeur 0 - ou null. Cette valeur **ne peut pas être modifiée** (ce qui est le principe fondamental d’une constante). 

Ainsi, en PHP, **NULL** est passé en valeur à une variable lors de sa déclaration, lorsque la vraie valeur n’est pas connue par avance. 

Exemple :

``` php
$variable = NULL;
```