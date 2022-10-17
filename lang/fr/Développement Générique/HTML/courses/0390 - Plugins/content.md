Les plugins, en informatique, sont des “ajouts” qui permettent d’étendre les fonctionnalités d’un langage, tout en facilitant la tâche d’un développeur qui n’a pas besoin de réécrire sans cesse le même code, encore et encore.

## Plug-ins

Avec le langage HTML, les plugins ont été créés afin de résoudre plusieurs problématiques (liste non-exhaustive) :

- Afficher des cartes
- Rechercher des virus
- Vérifier un identifiant bancaire

## L'élément <object>

L'élément ```<object></object>``` est pris en charge par tous les navigateurs. Il représente une source externe. Cette source externe peut être interprétée comme une image ou une ressource à traiter comme un plugin.

Sa principale utilisation est d’intégrer des plugins tels que des lecteurs PDF ou des images, par exemple, directement au sein d’une page web.

Cet élément est au moins accompagné de l’attribut ```data``` qui prend en valeur l’adresse de la ressource à intégrer, ainsi que de l’attribut ```type``` qui reçoit en valeur le type de ressource (*application/pdf*, par exemple pour un fichier PDF).

Exemple :

``` html
<object type="application/pdf" data="fichier/lecteur.pdf"></object>
```

## L'élément <embed>

Cet élément a exactement la même fonction et la même utilité que l’élément précédent : inclure un objet ou un plugin. 

La seule différence avec ```<object>``` est que l’élément ```<embed>``` n’est plus beaucoup pris en charge. Pour inclure un plugin, mieux vaut donc utiliser l’élément ```<object></object>```.

L’utilisation de ```<embed>``` est exactement la même que pour ```<object>```.

Exemple :

``` html
<embed type="image/jpg" data="images/chat.jpg" />
```