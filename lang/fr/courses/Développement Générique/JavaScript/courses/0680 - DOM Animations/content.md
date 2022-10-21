En combinant le Javascript avec le langage CSS, il est possible de créer une animation. 

Ce cours montre pas à pas comment créer une animation en Javascript et CSS.

## Page web basique

Ci-dessous, le code HTML basique d’une page web :

```js
<!DOCTYPE html>
<html>
<body>

<h1>My First JavaScript Animation</h1>

<div id="animation">My animation will go here</div>

</body>
</html>
```

## Création d’un conteneur pour l’animation

Toutes les animations sont relatives à un élément conteneur :

```js
<div id ="container">
    <div id ="animate">My animation will go here</div>
</div>
```

## Styliser les éléments

Les éléments sont stylisés avec CSS :

```js
#container {
    width: 400px;
    height: 400px;
    position: relative;
    background: yellow;
}
#animate {
    width: 50px;
    height: 50px;
    position: absolute;
    background: red;
}
```

## Code de l’animation

En Javascript, les animations sont faites en changeant graduellement le style d’un élément. Ces changements sont appelés par un timer. Plus l'intervalle de temps est court, plus l’animation semble être en continu. 

Voici le code l’animation en Javascript :

```js
id = setInterval(frame, 5);

function frame() {
    if (/* test for finished */) {
        clearInterval(id);
    } else {
        /* code to change the element style */ 
    }
}
```

## Créer l’animation totalement en Javascript

Il est également possible de créer TOTALEMENT l’animation en utilisant seulement le Javascript.

Voici le code :

```js
function myMove() {
    let id = null;
    const elem = document.getElementById("animate");
    let pos = 0;
    clearInterval(id);
    id = setInterval(frame, 5);
    function frame() {
        if (pos == 350) {
           clearInterval(id);
        } else {
            pos++;
            elem.style.top = pos + 'px';
            elem.style.left = pos + 'px';
        }
    }
}
```

Dans cet exemple, la position des éléments est modifiée toutes les 5 secondes. 