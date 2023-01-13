Une fonction est un bloc de code organisé et réutilisable qui est utilisé pour effectuer une action unique et connexe. Les fonctions offrent une meilleure modularité à votre application et un haut degré de réutilisation du code.

Comme vous le savez déjà, Python vous offre de nombreuses fonctions intégrées comme ```print()```, etc. mais vous pouvez également créer vos propres fonctions. Ces fonctions sont appelées fonctions définies par l'utilisateur.

## Définition d'une fonction

Vous pouvez définir des fonctions pour fournir la fonctionnalité requise. Voici des règles simples pour définir une fonction en Python.

- Les blocs de fonction commencent par le mot-clé def suivi du nom de la fonction et de parenthèses ( ```( )``` ).
- Tout paramètre d'entrée ou argument doit être placé entre ces parenthèses. Vous pouvez également définir des paramètres à l'intérieur de ces parenthèses.
- La première déclaration d'une fonction peut être une déclaration facultative - la chaîne de documentation de la fonction ou docstring.
- Le bloc de code de chaque fonction commence par deux points (```:```) et est indenté.
- L'instruction ```return [expression]``` permet de quitter une fonction, en renvoyant éventuellement une expression à l'appelant. Une instruction ```return``` sans argument est identique à ```return None```.

### Syntaxe

```python
def functionname(parameters):
    "function_docstring"
    function_suite
    return [expression]
```

Par défaut, les paramètres ont un comportement positionnel et vous devez les renseigner dans l'ordre où ils ont été définis.

### Exemple

La fonction suivante prend une chaîne de caractères comme paramètre d'entrée et l'imprime sur l'écran standard.

```python
def printme(str):
    "This prints a passed string into this function"
    print(str)
    return
```

## Appeler une fonction

La définition d'une fonction lui donne un nom, spécifie les paramètres qui doivent être inclus dans la fonction et structure les blocs de code.

Une fois la structure de base d'une fonction finalisée, vous pouvez l'exécuter en l'appelant depuis une autre fonction ou directement depuis l'invite Python. Voici un exemple d'appel de la fonction ```printme()``` :

```python
#!/usr/bin/python3

# Function definition is here
def printme(str):
    "This prints a passed string into this function"
    print(str)
    return

# Now you can call printme function
printme("This is first call to the user defined function!")
printme("Again second call to the same function")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
This is first call to the user defined function!
Again second call to the same function
```

## Passage par référence ou par valeur

Tous les paramètres (arguments) du langage Python sont transmis par référence. Cela signifie que si vous modifiez la référence d'un paramètre dans une fonction, ce changement se répercute également dans la fonction appelante. Par exemple :

```python
#!/usr/bin/python3

# Function definition is here
def changeme(mylist):
    "This changes a passed list into this function"
    print("Values inside the function before change: ", mylist)
    
    mylist[2] = 50
    print("Values inside the function after change:", mylist)
    return

# Now you can call changeme function
mylist = [10,20,30]
changeme(mylist)
print("Values outside the function:", mylist)
```

Ici, nous maintenons la référence de l'objet passé et ajoutons les valeurs dans le même objet. Par conséquent, cela produirait le résultat suivant :

```bash
Values inside the function before change: [10, 20, 30]
Values inside the function after change: [10, 20, 50]
Values outside the function: [10, 20, 50]
```

Il existe un autre exemple où l'argument est transmis par référence et où la référence est écrasée dans la fonction appelée.

```python
#!/usr/bin/python3

# Function definition is here
def changeme(mylist):
    "This changes a passed list into this function"
    mylist = [1,2,3,4] # This would assi new reference in mylist
    print("Values inside the function:", mylist)
    return

# Now you can call changeme function
mylist = [10,20,30]
changeme(mylist)
print("Values outside the function:", mylist)
```

Le paramètre ```mylist``` est local à la fonction ```changeme```. Changer ```mylist``` dans la fonction n'affecte pas ```mylist```. La fonction n'accomplit rien et finalement cela produirait le résultat suivant :

```bash
Values inside the function: [1, 2, 3, 4]
Values outside the function: [10, 20, 30]
```

## Arguments de fonction

Vous pouvez appeler une fonction en utilisant les types d'arguments formels suivants :

- Arguments requis
- Arguments de mots-clés
- Arguments par défaut
- Arguments de longueur variable

Les arguments requis sont les arguments passés à une fonction dans un ordre positionnel correct. Ici, le nombre d'arguments dans l'appel de fonction doit correspondre exactement à la définition de la fonction.

Pour appeler la fonction ```printme()```, vous devez absolument passer un argument, sinon une erreur de syntaxe sera générée comme suit :

```python
#!/usr/bin/python3

# Function definition is here
def printme(str):
    "This prints a passed string into this function"
    print(str)
    return

# Now you can call printme function
printme()
```

When the above code is executed, it produces the following result −

```python
Traceback (most recent call last):
    File "test.py", line 11, in <module>
        printme();
TypeError: printme() takes exactly 1 argument (0 given)
```

## Arguments des mots-clés

Les arguments de type mot-clé sont liés aux appels de fonction. Lorsque vous utilisez des arguments par mot-clé dans un appel de fonction, l'appelant identifie les arguments par le nom du paramètre.

Cela vous permet de sauter des arguments ou de les placer dans le désordre, car l'interprète Python est capable d'utiliser les mots-clés fournis pour faire correspondre les valeurs aux paramètres. Vous pouvez également effectuer des appels de mots-clés à la fonction ```printme()``` de la manière suivante :

```python
#!/usr/bin/python3

# Function definition is here
def printme(str):
    "This prints a passed string into this function"
    print(str)
    return

# Now you can call printme function
printme(str = "My string")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
My string
```

L'exemple suivant donne une image plus claire. Notez que l'ordre des paramètres n'a pas d'importance.

```python
#!/usr/bin/python3

# Function definition is here
def printinfo(name, age):
    "This prints a passed info into this function"
    print("Name:", name)
    print("Age:", age)
    return

# Now you can call printinfo function
printinfo(age = 50, name = "Miki")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Name: Miki
Age: 50
```

## Arguments par défaut

Un argument par défaut est un argument qui prend une valeur par défaut si une valeur n'est pas fournie dans l'appel de la fonction pour cet argument. L'exemple suivant donne une idée des arguments par défaut, il imprime l'âge par défaut s'il n'est pas passé :

```python
#!/usr/bin/python3

# Function definition is here
def printinfo(name, age = 35):
    "This prints a passed info into this function"
    print("Name:", name)
    print("Age:", age)
    return

# Now you can call printinfo function
printinfo(age = 50, name = "Miki")
printinfo(name = "Miki")
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Name: Miki
Age: 50
Name: Miki
Age: 35
```

## Arguments de longueur variable

Vous pouvez être amené à traiter une fonction pour plus d'arguments que ceux que vous avez spécifiés lors de la définition de la fonction. Ces arguments sont appelés arguments de longueur variable et ne sont pas nommés dans la définition de la fonction, contrairement aux arguments requis et par défaut.

La syntaxe d'une fonction avec des arguments variables sans mot-clé est donnée ci-dessous :

```python
def functionname([formal_args,] *var_args_tuple):
    "function_docstring"
    function_suit
    return [expression]
```

Un astérisque ```*``` est placé devant le nom de la variable qui contient les valeurs de tous les arguments variables qui ne sont pas des mots clés. Ce tuple reste vide si aucun argument supplémentaire n'est spécifié lors de l'appel de la fonction. Voici un exemple simple :

```python
#!/usr/bin/python3

# Function definition is here
def printinfo(arg1, *vartuple):
    "This prints a variable passed arguments"
    print("Output is:")
    print(arg1)
    
    for var in vartuple:
        print(var)
    return

# Now you can call printinfo function
printinfo(10)
printinfo(70, 60, 50)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Output is:
10
Output is:
70
60
50
```

## Les fonctions anonymes

Ces fonctions sont dites anonymes parce qu'elles ne sont pas déclarées de manière standard à l'aide du mot-clé ```def```. Vous pouvez utiliser le mot-clé ```lambda``` pour créer de petites fonctions anonymes.

- Les formes lambda peuvent prendre un nombre quelconque d'arguments mais ne renvoient qu'une seule valeur sous la forme d'une expression. Elles ne peuvent pas contenir de commandes ou d'expressions multiples.
- Une fonction anonyme ne peut pas être un appel direct à l'impression car lambda nécessite une expression.
- Les fonctions lambda ont leur propre espace de noms local et ne peuvent pas accéder à des variables autres que celles de leur liste de paramètres et celles de l'espace de noms global.
- Bien qu'il semble que les lambda soient une version d'une fonction en une ligne, ils ne sont pas équivalents aux instructions ```inline``` en C ou C++, dont le but est d'allouer la pile en passant la fonction, pendant l'invocation pour des raisons de performance.

### Syntaxe

La syntaxe des fonctions lambda ne contient qu'une seule instruction, qui est la suivante :

```python
lambda[arg1 [,arg2,.....argn]]:expression
```

L'exemple suivant montre comment fonctionne la forme ```lambda``` d'une fonction :

```python
#!/usr/bin/python3

# Function definition is here
sum = lambda arg1, arg2: arg1 + arg2

# Now you can call sum as a function
print("Value of total :", sum(10, 20))
print("Value of total :", sum(20, 20))
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Value of total : 30
Value of total : 40
```

## L'instruction return

L'instruction ```return [expression]``` permet de quitter une fonction, en renvoyant éventuellement une expression à l'appelant. Une instruction ```return``` sans argument est identique à ```return None```.

Tous les exemples donnés ci-dessous ne renvoient aucune valeur. Vous pouvez retourner une valeur à partir d'une fonction comme suit :

```python
#!/usr/bin/python3

# Function definition is here
def sum(arg1, arg2):
    # Add both the parameters and return them."
    total = arg1 + arg2
    print("Inside the function :", total)
    return total

# Now you can call sum function
total = sum(10, 20)
print("Outside the function :", total )
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Inside the function : 30
Outside the function : 30
```

## Portée des variables

Toutes les variables d'un programme ne sont pas forcément accessibles à tous les endroits de ce programme. Cela dépend de l'endroit où vous avez déclaré une variable.

La portée d'une variable détermine la partie du programme où vous pouvez accéder à un identifiant particulier. Il existe deux champs d'application de base pour les variables en Python, à savoir

- Les variables globales
- Variables locales

## Variables globales et locales

Les variables définies à l'intérieur du corps d'une fonction ont une portée locale, et celles définies à l'extérieur ont une portée globale.

Cela signifie que les variables locales ne sont accessibles qu'à l'intérieur de la fonction dans laquelle elles sont déclarées, alors que les variables globales sont accessibles dans tout le corps du programme par toutes les fonctions. Lorsque vous appelez une fonction, les variables déclarées à l'intérieur de celle-ci sont mises en évidence. Voici un exemple simple :

```python
#!/usr/bin/python3

total = 0   # This is global variable.
# Function definition is here
def sum(arg1, arg2):
    # Add both the parameters and return them."
    total = arg1 + arg2; # Here total is local variable.
    print("Inside the function local total :", total)
    return total

# Now you can call sum function
sum(10, 20)
print("Outside the function global total :", total)
```

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Inside the function local total : 30
Outside the function global total : 0
```
