En général, les instructions sont exécutées de manière séquentielle - la première instruction d'une fonction est exécutée en premier, suivie de la deuxième, et ainsi de suite. Il peut arriver que vous ayez besoin d'exécuter un bloc de code plusieurs fois.

Les langages de programmation fournissent diverses structures de contrôle qui permettent des chemins d'exécution plus complexes.

Une instruction de boucle nous permet d'exécuter une instruction ou un groupe d'instructions plusieurs fois. Le schéma suivant illustre une instruction de boucle :

![instruction de boucle](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0230%20-%20Boucles/images/image1.jpg)

Le langage de programmation Python propose les types de boucles suivants pour répondre aux besoins de bouclage.

- ```boucle while``` : Répète une instruction ou un groupe d'instructions pendant qu'une condition donnée est VRAIE. Elle teste la condition avant d'exécuter le corps de la boucle. 
- ```boucle for``` : Exécute une séquence d'instructions plusieurs fois et abrège le code qui gère la variable de la boucle. 
- ```boucles imbriquées``` : Vous pouvez utiliser une ou plusieurs boucles à l'intérieur d'une autre boucle while ou for. 

## Déclarations de contrôle de boucle

Les instructions de contrôle Loop modifient l'exécution de sa séquence normale. Lorsque l'exécution quitte une portée, tous les objets automatiques qui ont été créés dans cette portée sont détruits.

Python prend en charge les instructions de contrôle suivantes.

- **Instruction break** : Termine l'instruction de la boucle et transfère l'exécution à l'instruction qui suit immédiatement la boucle.
- **Instruction continue** : Permet à la boucle de sauter le reste de son corps et de tester à nouveau immédiatement sa condition avant de réitérer.
- **Instruction pass** : L'instruction ```pass``` en Python est utilisée lorsqu'une instruction est requise syntaxiquement mais que vous ne voulez pas qu'une commande ou un code soit exécuté.

Passons brièvement en revue les instructions de contrôle de la boucle.

## Itérateur et générateur

Un **itérateur** est un objet qui permet à un programmeur de parcourir tous les éléments d'une collection, quelle que soit son implémentation spécifique. En Python, un objet **itérateur** implémente deux méthodes, ```iter()``` et ```next()```.

Les objets ```String```, ```List``` ou ```Tuple``` peuvent être utilisés pour créer un ```Iterator```.

```python
#!/usr/bin/python3
import sys

list = [1,2,3,4]
it = iter(list) # this builds an iterator object
print(next(it)) #prints next available element in iterator
#Iterator object can be traversed using regular for statement
for x in it:
    print(x, end=" ")
#or using next() function
while True:
   try:
        print(next(it))
   except StopIteration:
        sys.exit()
```

Un **générateur** est une fonction qui produit ou donne une séquence de valeurs à l'aide de la méthode yield.

Lorsqu'une fonction de **générateur** est appelée, elle renvoie un objet **générateur** sans même commencer l'exécution de la fonction. Lorsque la méthode ```next()``` est appelée pour la première fois, la fonction commence à s'exécuter jusqu'à ce qu'elle atteigne l'instruction yield, qui renvoie la valeur produite. L'instruction yield garde la trace, c'est-à-dire qu'elle se souvient de la dernière exécution et le deuxième appel à la méthode ```next()``` reprend la valeur précédente.

### Exemple

L'exemple suivant définit un générateur, qui génère un itérateur pour tous les nombres de Fibonacci.

```python
#!usr/bin/python3

import sys
def fibonacci(n): #generator function
    a, b, counter = 0, 1, 0
    while True:
        if counter > n: 
            return
        yield a
        a, b = b, a + b
        counter += 1
f = fibonacci(5) #f is iterator object

while True:
   try:
        print(next(f), end=" ")
   except StopIteration:
        sys.exit()
```
