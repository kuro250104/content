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

