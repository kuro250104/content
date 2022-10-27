Il existe deux types de listes : les listes dites à puces (unordered lists, en anglais) dont les items sont précédés de ronds ou de carrés, et les listes ordonnées (ordered lists, en anglais) dont les items sont précédés de chiffres afin de marquer une certaine hiérarchie dans les éléments de la liste.

## Propriétés des listes en HTML et CSS

En langage HTML, il y a 2 types de listes :

- **Les listes à puces** : ces types de listes sont définies avec la balise ```<ul>``` (pour *unordered list*) en HTML. Les items des listes à puces sont précédés de ronds ou carrés.
- **Les listes dites ordonnées** : définies avec la balise ```<ol>``` (pour *ordered list*) en HTML. Les items de ces listes sont le plus souvent précédés de chiffres permettant de marquer un ordre d’importance entre les différents items de la liste.

Concernant les listes, les langages CSS permet :

De définir différents types de puces pour les listes à puces ```<ul>```
De définir différents types de puces pour les listes ordonnées ```<ol>```
D’utiliser des images pour remplacer les puces classiques
De définir des couleurs de fond pour les listes et les items de ces listes

## Différents types de puces

Pour définir un type de puce pour une liste, le CSS met à disposition la propriété ```list-style-type```.

L’une des utilisations les plus communes de cette propriété - outre le fait de changer le type de puce dans une liste - est de supprimer les puces dans une liste. Cela est par exemple utile dans un menu, pour lequel il n’est pas très joli d’avoir des puces qui précèdent les liens. Pour supprimer les puces d’une liste, la propriété ```list-style-type``` doit recevoir la valeur ```none```.

Exemple :

```css
ul {
	list-style-type : disc; /* Les items de la liste non-ordonnée sont précédés d'un cercle noir */
}

ol {
	list-style-type: upper-roman; /* Les items de la liste ordonnée sont précédé de chiffres romains en majuscule */
}

ul.a {
	list-style-type: none; /* Les items de la liste non-ordonnée de classe a ne sont pas précédé de puces */
}
```

## Utiliser une image comme type de puce

Afin de correspondre au design d’un site, le CSS permet également de faire précéder les items d’une liste d’une image. Pour cela, il faut utiliser la propriété ```list-style-image```. 

Cette propriété reçoit en valeur l’URL de l’image à utiliser. 

Exemple :

```css
ul {
	list-style-image : url('marker.gif'); /* Les items de la liste non-ordonnée sont précédés d'une image */
}
```

## Positionner la puce 

Le CSS permet de positionner le texte en fonction de la puce. Pour cela, le CSS met à disposition la propriété ```list-style-position```.

Cette propriété reçoit une des deux valeurs suivantes :

- ```outside``` : la puce sera positionnée à l’extérieur (*outside*, en anglais) de la liste. Avec cette valeur, le texte sera aligné verticalement.
- ```inside``` : la puce sera positionnée à l’intérieur (*inside*, en anglais) de la liste. Si la propriété reçoit cette valeur, le texte ne sera pas aligné verticalement. Il y aura un effet de décalage (la puce sera décalée vers la droite et le texte, lorsqu’il est multiligne, est aligné à gauche. Cela a un effet “tabulation”.)

Exemple :

```css
ul {
	list-style-type: circle; 
	list-style-position: outside;
}

ol {
	list-style-type : upper-roman;
	list-style-position: inside;
}
```

## Propriété raccourcie

Afin de rendre le code plus lisible et de gagner du temps, le langage CSS propose une propriété raccourcie, permettant de styliser les puces en une seule ligne. Cette propriété raccourcie est ```list-style```.

Cette propriété reçoit les différentes propriétés évoquées dans les points précédents, dans l’ordre suivant :

- ```list-style-type```
- ```list-style-position```
- ```list-style-image```

Si l’une des propriétés ci-dessus n’est pas passée en valeur, le navigateur y ajoutera la valeur par défaut. 

Exemple :

```css
ul {
	list-style: disc, inside; /* Ici, la valeur de list-style-image n'est pas spécifiée */
}
```