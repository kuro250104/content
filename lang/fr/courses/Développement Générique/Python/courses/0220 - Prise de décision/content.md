La prise de décision est l'anticipation des conditions qui se produisent pendant l'exécution d'un programme et les actions spécifiées prises en fonction de ces conditions.

Les structures de décision évaluent plusieurs expressions, qui produisent VRAI ou FAUX comme résultat. Vous devez déterminer l'action à entreprendre et les instructions à exécuter si le résultat est VRAI ou FAUX sinon.

Voici la forme générale d'une structure de décision type que l'on trouve dans la plupart des langages de programmation :

![Forme générale de structure de décision type](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/Python/courses/0220%20-%20Prise%20de%20d%C3%A9cision/images/image1.png)

Le langage de programmation Python considère toute valeur non nulle comme VRAIE, et toute valeur nulle comme FAUX.

Le langage de programmation Python fournit les types d'instructions décisionnelles suivants :

- ```instruction if``` : Une instruction if consiste en une expression booléenne suivie d'une ou plusieurs instructions. 
- ```instruction if...else``` : Une instruction if peut être suivie d'une instruction else facultative, qui s'exécute lorsque l'expression booléenne est FALSE. 
- ```instruction emboîté if``` : Vous pouvez utiliser une instruction if ou else if à l'intérieur d'une ou plusieurs autres instructions if ou else if. 

Passons rapidement en revue chaque relevé décisionnel.

## Suites d'énoncés uniques

Si la suite d'une clause if ne comporte qu'une seule ligne, elle peut figurer sur la même ligne que l'instruction d'en-tête.

### Exemple

Voici un exemple de clause if d'une seule ligne :

```python
#!/usr/bin/python3

var = 100
if var  == 100: print("Value of expression is 100")
print("Good bye!")
```

### Sortie

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Value of expression is 100
Good bye!
```
