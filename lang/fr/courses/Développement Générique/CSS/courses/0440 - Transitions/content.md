Les transitions permettent, en utilisant simplement du code CSS, de changer la valeur d’une propriété de manière douce, pendant une durée déterminée.

Pour ce faire, le langage CSS met à disposition 5 propriétés :

- ```transition```
- ```transition-delay```
- ```transition-duration```
- ```transition-property```
- ```transition-timing-function```

## Compatibilité avec les différents navigateurs internet

Voici le tableau résumant la compatibilité des propriétés de transition, en fonction du navigateur internet :

| **Propriété** | **Chrome** | **Edge** | **Firefox** | **Safari** | **Opéra** |
| --- | --- | --- | --- | --- | --- |
| **transition** | 26.0 | 10.0 | 16.0 | 6.1 | 12.1 |
| **transition-delay** | 26.0 | 10.0 | 16.0 | 6.1 | 12.1 |
| **transition-duration** | 26.0 | 10.0 | 16.0 | 6.1 | 12.1 |
| **transition-property** | 26.0 | 10.0 | 16.0 | 6.1 | 12.1 |
| **transition-timing-function** | 26.0 | 10.0 | 16.0 | 6.1 | 12.1 |

## Utiliser les transitions CSS

Pour utiliser les transitions CSS, il faut spécifier 2 choses :

- La **propriété** sur laquelle la transition doit s’appliquer
- La **durée** de la transition

__Remarque__ : Si aucune valeur n’est définie pour la durée, celle-ci n’aura pas d’effet, car la valeur attribuée par défaut est 0.

Exemple :

```css
div {
	width: 100px;
	height: 100px;
	background-color: red;
	transition: width 2s; /* La transition concerne la largeur de la div et prend 2 secondes */
}

div:hover {
	width: 300px; /* Au passage de la souris sur la div, la largeur s'étends à 300 pixels */
}
```

__Remarque__ : Dans l’exemple ci-dessus, lorsque la souris ne survole plus la ```<div>```, celle-ci reprend progressivement sa taille originelle. 

## Ajouter une transition sur plusieurs propriétés

Pour changer la valeur de plusieurs propriétés, il faut séparer chaque nom de propriété + durée par une virgule. 

Exemple :

```css
div {
    width: 100px;
    height: 100px;
    transition: height 2s, width 2s;
}

div:hover {
    height: 100px;
    width: 300px;
}
```

__Remarque__ : Pour les transitions, la règle doit être appliquée sur un élément **non-hover**, car, le cas échéant, elle ne s’effectuera que dans un sens. En effet, si la propriété ```transition``` est utilisée sur un élément ayant la pseudo-classe ```:hover```, la transition s’effectuera, mais, ensuite, l’élément ne reviendra pas à son état initial de manière progressive.

### transition: all

Lorsque toutes les propriétés définies dans un bloc sont modifiées lors de la transition, la valeur all peut être donnée à la propriété **transition**.

Exemple :

```css
div {
    width: 100px;
    height: 100px;
    transition: all;
}

div:hover {
    height: 100px;
    width: 300px;
}
```

Dans cet exemple, les propriétés ```width``` et ```height``` sont modifiées lors de la transition. La valeur ```all``` est donc passée à la propriété ```transition```.

## Définir la courbe de vitesse de la transition

La courbe de la vitesse signifie que la transition va passer par plusieurs vitesses, avant de terminer dans l’état spécifié. Pour définir la courbe de vitesse de transition, il faut utiliser la propriété ```transition-timing-function```.

Cette propriété reçoit une des 6 valeurs suivantes :

- ```ease``` : L’effet de transition commence doucement, puis devient plus rapide, puis finit doucement. C’est la valeur par défaut. 
- ```linear``` : Définit une transition avec la même vitesse du début à la fin. 
- ```ease-in``` : Définit une transition avec un début lent
- ```ease-out``` : Définit une transition avec une fin lente
- ```ease-in-out``` : Définit une transition avec un début et une fin lente
- ```cubic-bezier(n,n,n)``` : Permet au développeur de préciser ses propres valeurs

Exemple :

```css
div {
    width: 100px;
    height: 100px;
    transition: height 2s, width 2s;
}

div:hover {
	transition-timing-function: ease-in-out; /* La transition a un début et une fin lente */
    height: 100px;
    width: 300px;
}
```

## Retarder la transition

La propriété ```transition-delay``` permet de définir un “temps d’attente” avant que la transition commence. Cette propriété prend en valeur le temps d’attente avant de commencer la transition. 

Exemple :

```css
div {
    width: 100px;
    height: 100px;
    transition: height 3s, width 3s;
    transition-delay: 1s; /* Le navigateur attend une seconde avant de démarrer la transition */
}
```

## Transition et transformation

Le langage CSS permet également d’ajouter une transition à un effet de transformation. Pour ce faire, il faut simplement préciser que la transition s’applique également à la propriété ```transform``` et il faut également préciser la durée de la transition. 

Exemple :

```css
div {
    width: 100px;
    height: 100px;
    transition: height 2s, width 2s, transform 2s;
}
```

## Propriété raccourcie

Pour une transition, il est possible d’utiliser toutes les propriétés une par une. Cependant, pour économiser des lignes de code, il est possible d’utiliser la propriété raccourcie transition. 

Cette propriété prend, dans cet ordre, les valeurs suivantes :

- La propriété sur laquelle la transition s’applique
- La durée de la transition
- La courbe de durée
- La durée d’attente avant de démarrer la transition

Exemple :

```css
div {
	transition: width 4s ease-out 1s;
}
```