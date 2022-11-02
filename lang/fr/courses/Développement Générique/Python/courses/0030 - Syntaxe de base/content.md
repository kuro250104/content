Le langage Python présente de nombreuses similitudes avec Perl, C et Java. Cependant, il existe des différences notables entre ces langages.

## Syntaxe Python

Un identifiant Python est un nom utilisé pour identifier une variable, une fonction, une classe, un module ou tout autre objet.

Les caractères autorisés sont les lettres sans accent, les chiffres et les caractères ‘-’ et ‘_’. Un identificateur peut avoir les formes suivantes:

- Une lettre seule ;
- Une lettre suivie d’un ou plusieurs caractères autorisés ;
- Le caractère ‘_’ suivi d’un ou plusieurs caractères  autorisés ;
- Le caractère ‘_’ seul (dans ce cas, il s'agit d'une variable dont le contenu est sans importance).

Python est un langage de programmation sensible à la casse. Ainsi, **Microlead** et **microlead** sont deux identifiants différents en Python.

## Mots réservés

La liste suivante présente les mots-clés Python. Ce sont des mots réservés et vous ne pouvez pas les utiliser comme constantes, variables ou tout autre nom d'identifiant. Tous les mots-clés Python contiennent uniquement des lettres minuscules.

- and
- exec
- try
- not
- continue
- as
- finally
- while
- or
- def
- assert
- for
- with
- pass
- del
- break
- from
- yield
- print
- if
- class
- global
- elif
- raise
- import
- except
- is
- else
- return
- in
- lambda

## Lignes et indentation

Les blocs de code sont indiqués par une indentation de ligne, qui est appliquée de manière rigide.

Le nombre d'espaces dans l'indentation doit être un multiple de 4. Par exemple:

```python
def microlead():
    print(‘Microlead est génial!’)
```

Cependant, le bloc suivant génère une erreur :

```python
def microlead():
    print(‘Microlead est génial!’)
```

Ainsi, en Python, toutes les lignes continues indentées avec le même nombre d'espaces forment un bloc. L'exemple suivant comporte plusieurs blocs d'instructions.

```python
#!/usr/bin/python3
def hello_you(name=Microlead):
    try:
        print(f’Bonjour, {name} !’)
    except:
        print(‘Nom saisit incorrect !’)
```

De plus, le nombre de caractères par ligne conseillé est de 79.

## Déclarations multi-lignes

Les instructions en Python se terminent généralement par une nouvelle ligne. Python permet toutefois d'utiliser le caractère de continuation de ligne (\) pour indiquer que la ligne doit se poursuivre. Par exemple :

```python
total = element_un + \
        element_deux + \
        element_trois
```

Les instructions contenues entre les crochets [], {} ou () n'ont pas besoin d'utiliser le caractère de continuation de ligne. Par exemple :
```python
jours = ['Lundi', 'Mardi', 'Mercredi', 
         'Jeudi', 'Vendredi']
```

## Chaînes de caractères en Python

Python accepte les guillemets simples ('), doubles (") et triples (''' ou """) pour désigner les chaînes de caractères, à condition que le même type de guillemet commence et finisse la chaîne.

Les guillemets triples sont à éviter, car ils servent à un autre usage dont on parlera un peu plus loin :

```python
mot = 'mot'
phrase = "Ceci est une phrase".
paragraphe = """Ceci est un paragraphe. Il est
composé de plusieurs lignes et phrases."""
```

Pour afficher une chaîne de caractère (appelée ‘string’) dans une console, nous pouvons utiliser une fonction qui s’appelle ```print()```.

Cette fonction permet également d’afficher le contenu de variable directement. Mais il est également possible d’afficher le contenu d’une variable en séparant les morceaux de phrase d’une virgule, ou bien en utilisant une structure spécifique :

```python
>>> a = Microlead
>>> print(‘Bonjour Microlead!’)
Bonjour Microlead!
>>> print(a)
Microlead
>>> print(‘Bonjour ’, a, ‘!’)
Bonjour Microlead!
>>> print(f’Bonjour {a}!’)
Bonjour Microlead!
```

## Commentaires en Python

Un signe dièse (#) qui n'est pas à l'intérieur d'une chaîne littérale est le début d'un commentaire. Tous les caractères après le #, jusqu'à la fin de la ligne physique, font partie du commentaire et l'interpréteur Python les ignore. A noter qu’un espace sépare le dièse du commentaire.

```python
# Premier commentaire
print("Bonjour Python !")  # Deuxième commentaire
```

Cela produit le résultat suivant :

```python
Bonjour, Python !
```

Vous pouvez taper un commentaire sur la même ligne après une déclaration ou une expression si vous le précéder de deux espaces :

```python
nom = "Microlead"  # Ceci est encore un commentaire
```

Python ne dispose pas de la fonction de commentaire sur plusieurs lignes. Vous devez commenter chaque ligne individuellement, comme suit :

```python
# Ceci est un commentaire.
# Ceci est aussi un commentaire.
# Ceci est aussi un commentaire.
```

## Utilisation de lignes vides

Une ligne ne contenant que des espaces, avec éventuellement un commentaire, est appelée une ligne vierge et Python l'ignore totalement.

Dans une session interactive de l'interpréteur, vous devez saisir une ligne physique vide pour mettre fin à une instruction multiligne.

Enfin, les scripts Python se terminent toujours par une ligne vide.