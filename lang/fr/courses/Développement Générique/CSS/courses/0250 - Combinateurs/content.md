Un combinateur est quelque chose qui explique la relation entre les sélecteurs CSS.

Il existe 4 type de combinateurs :

- Le sélecteur de descendance (un élément contenu dans un élément) : ``` ``` (espace)
- Le sélecteur enfant : ```>```
- Le sélecteur de frère adjacent : ```+```
- Le sélecteur de frère général : ```~```

## Le combinateur de descendance

Le combinateur de descendance (espace) est utilisé pour désigner tous les descendants d’un élément. 

En langage informatique, un descendant est un élément contenu dans un autre élément.

Exemple :

```css
div h1 { /* Tous les titres de niveau 1 présents dans la div */
	text-align: center;
}
```

Dans l’exemple ci-dessus, **tous** les titres de niveau un descendant de la ```<div>``` - donc tous les titres de niveau 1 contenu dans la ```<div>``` - se verront assigner le style défini.

## Le combinateur de sélecteur enfant 

Le sélecteur enfant ```>``` est utilisé pour désigner tous les éléments étant enfants directs d’un élément.

__Remarque__ : Ce sélecteur permet de désigner **uniquement** les **enfants directs** d’un élément.

Exemple :

```css
div > h1 { /* Tous les titres de niveau 1 enfant de l'élément parent div */
	text-align: center;
}
```

## Le sélecteur de frère adjacent

Le sélecteur de frère adjacent (```+```) est utilisé pour désigner un élément situé directement après un autre élément spécifique. 

Les éléments frères doivent avoir le même élément parent et adjacent signifie “à la suite immédiate de quelque chose.”

Exemple :

```css
div + h1 { /* Le premier titre de la div */
	text-align: center;
}
```

Dans cet exemple, seul le premier titre de la div est concerné. En effet, il est situé immédiatement à la suite de l’élément ```div```, qui est l’élément parent.

## Le sélecteur de frère général

Ce sélecteur désigne tous les sélecteurs qui sont frères d’un élément spécifique. Pour ce faire, il faut utiliser le signe ```~```.

Exemple :

```css
div ~p h1 { /* Tous les paragraphes frères de la div */
	text-align: center;
}
```

Phrase test pour résolution bug ```<p>``` encore un test

Dans l’exemple ci-dessus, tous les paragraphes contenus dans la ```<div>``` (qui est l’élément parent) sont concernés. En effet, ils ont tous le même élément parent : l'élément ```<div>```.