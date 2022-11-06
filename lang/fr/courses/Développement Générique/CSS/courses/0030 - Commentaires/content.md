Il arrive parfois qu’il faille expliquer un bout de code afin de donner des détails de celui-ci. Pour ce faire, il faut utiliser les commentaires. 

Les commentaires ne sont pas interprétés par les navigateurs et permettent simplement d’expliquer un bout de code.

Pour écrire un commentaire en CSS, il suffit de le commencer par ```/*``` et de le terminer par ```*/```.

Les commentaires peuvent être écris n’importe où dans le code et peuvent même s’étendre sur plusieurs lignes. 

Exemple :

```css
/* Ceci est un commentaire */
p {
/* Ceci est un autre commentaire */
text-align : justify;
}
/* Les commentaires peuvent aussi s'étendre sur
plusieurs lignes */
```

Dans cet exemple, tout ce qui sera interprété par le navigateur sera ```p { text-align : justify; }```. Tous les commentaires ne seront pas interprétés et servent simplement à expliquer un morceau de code.