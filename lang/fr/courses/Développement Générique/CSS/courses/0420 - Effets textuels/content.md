Le CSS met à disposition 4 propriétés permettant d’ajouter des effets textuels. 

## Text Overflow

La propriété ```text-overflow``` définit la manière dont un texte qui ne rentre pas dans un élément doit être disposé. 

Cette propriété prend deux valeurs :

- ```clip``` : le texte dépassant de l’élément ne sera tout simplement pas montré, même si un mot doit être coupé en plein milieu
- ```ellipsis``` : le texte en trop ne sera pas coupé, mais des points de suspension (...) seront ajoutés afin de montrer qu’il y a davantage de contenu à voir.

Exemple :

```css
#overflow1 {
    width: 100px;
    border: 1px solid black;
    overflow: hidden;
    text-overflow: clip;
}

#overflow2 {
    width: 100px;
    border: 1px solid black;
    overflow: hidden;
    text-overflow: ellipsis;
}
```

## word-wrap

La propriété ```word-wrap``` permet de couper les longs mots afin que ceux-ci soient renvoyés à la ligne. 

Exemple :

```css
p {
	word-wrap: break-word;
}
```

## Coupure de mots

La propriété CSS ```word-break``` permet de couper les mots au cas où ceux-ci sont trop longs.

Cette propriété prend 1 des deux paramètres suivants :

- ```keep-all``` : Les mots seront coupés là où il y a des tirets (-)
- ```break-all``` : Les mots sont coupés n’importe où

Exemple :

```css
#coupure1 {
	break-word: keep-all; /* Les mots sont coupés au niveau des tirets */
}

#coupure2 {
	break-word: break-all; /* Les mots sont coupés n'importe où */
}
```

## Les modes d’écriture

```writing-mode``` permet de définir si un mot ou un paragraphe doit être écrit verticalement ou horizontalement.

Cette propriété prend une des 2 valeurs suivantes :

- ```horizontal-tb``` :  Le mot ou le paragraphe est écrit horizontalement
- ```vertical-rl``` : Le mot ou le paragraphe est écrit verticalement

Exemple :

```css
.horizontal {
	writing-mode: horizontal-tb;
}

.vertical {
	writing-mode: vertical-rl;
}
```