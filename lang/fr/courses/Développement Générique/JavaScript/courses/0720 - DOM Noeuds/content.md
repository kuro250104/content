Le JavaScript et le DOM permettent d’ajouter ou de supprimer des nœuds - c’est-à-dire des éléments HTML.

## Créer de nouveaux éléments HTML

Pour ajouter un nouvel élément au DOM HTML, il faut d’abord le créer - créer l’élément nœud -, puis l’ajouter à un élément existant.

Exemple :

```js
<div id="div1">
    <p id="p1">This is a paragraph.</p>
    <p id="p2">This is another paragraph.</p>
</div>

<script>
const para = document.createElement("p");
const node = document.createTextNode("This is new.");
para.appendChild(node);

const element = document.getElementById("div1");
element.appendChild(para);
</script>
```

Explication de l’exemple :

Pour commencer, un nouvel élément paragraphe (```<p>```) est créé. Ensuite, un nœud texte est créé ayant pour valeur “this is new”. Ensuite, ce nœud est ajouté à l’élément paragraphe, puis le paragraphe est lui-même ajouté à l’élément ```div1```.

## Créer des éléments HTML - insertBefore()

La méthode ```.appendChild()```., dans l’exemple précédent, ajoute un élément comme dernier enfant de l’élément parent. Pour ajouter un élément comme premier enfant de son parent, il faut utiliser la méthode ```.insertBefore()```..

Exemple :

```js
<div id="div1">
    <p id="p1">This is a paragraph.</p>
    <p id="p2">This is another paragraph.</p>
</div>

<script>
    const para = document.createElement("p");
    const node = document.createTextNode("This is new.");
    para.appendChild(node);

    const element = document.getElementById("div1");
    const child = document.getElementById("p1");
    element.insertBefore(para, child);
</script>
```

## Supprimer des éléments HTML existants

Pour supprimer des éléments HTML existants, la méthode remove() est utilisée.

Exemple :

```js
<div>
    <p id="p1">This is a paragraph.</p>
    <p id="p2">This is another paragraph.</p>
</div>

<script>
    const elmnt = document.getElementById("p1"); 
    elmnt.remove();
</script>
```

Dans cet exemple, l’élément à supprimer est d’abord recherché avec ```getElementById()```, puis est supprimé en invoquant la méthode ```element.remove()```.

__Remarque__ : ```remove()``` n’est pas supporté par les anciennes versions de navigateurs. Pour régler ce problème, la méthode ```removeChild()``` doit être utilisée.

## Supprimer un nœud enfant

Cette méthode est utilisée pour les navigateurs ne supportant pas la méthode ```remove()```. Avec ```removeChild()```, le nœud parent doit d’abord être trouvé pour ensuite supprimé le nœud enfant.

Exemple :

```js
<div id="div1">
    <p id="p1">This is a paragraph.</p>
    <p id="p2">This is another paragraph.</p>
</div>

<script>
    const parent = document.getElementById("div1");
    const child = document.getElementById("p1");
    parent.removeChild(child);
</script>
```

Dans cet exemple, l’élément parent est d’abord recherché avec ```getElementById()```. Une fois trouvé, c’est l'élément enfant à supprimer qui est recherché avec cette même méthode. Enfin, une fois trouvé, le nœud enfant est supprimé du nœud parent avec ```parent.removeChild(child)```.

## Remplacer des éléments HTML

Pour remplacer un élément HTML dans le DOM, la méthode ```replaceChild()``` est utilisée. 

Cette méthode fonctionne exactement comme ```removeChild()```, à savoir qu’il faut rechercher le nœud parent, puis le nœud enfant, et enfin, remplacer l’enfant dans le parent en utilisant la syntaxe ```parent.remplaceChild(enfant)```.

Exemple :

```js
<div id="div1">
    <p id="p1">This is a paragraph.</p>
    <p id="p2">This is another paragraph.</p>
</div>

<script>
    const para = document.createElement("p");
    const node = document.createTextNode("This is new.");
    para.appendChild(node);

    const parent = document.getElementById("div1");
    const child = document.getElementById("p1");
    parent.replaceChild(para, child);
</script>
```