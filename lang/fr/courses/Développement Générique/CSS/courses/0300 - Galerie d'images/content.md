La galerie d’images est utilisée afin de mettre en forme plusieurs images, pour adapter l’affichage au design du site. 

## Galerie d’images 

Les codes HTML et CSS ci-dessous montrent un exemple permettant de réaliser une galerie d’images.

HTML :

```html
<!DOCTYPE html>
<html>
<head>
	<link rel="stylesheet" type="text/css" href="style.css" />
	<title>Mon site</title>
</head>
<body>

    <div class="gallery">
    <a target="_blank" href="image.jpg">
        <img src="image.jpg" alt="Cinque Terre" width="600" height="400">
    </a>
    <div class="desc">Description</div>
    </div>

    <div class="gallery">
    <a target="_blank" href="image.jpg">
        <img src="image.jpg" alt="Forest" width="600" height="400">
    </a>
    <div class="desc">Description</div>
    </div>

    <div class="gallery">
    <a target="_blank" href="image.jpg">
        <img src="image.jpg" alt="Northern Lights" width="600" height="400">
    </a>
    <div class="desc">Description</div>
    </div>

    <div class="gallery">
    <a target="_blank" href="image.jpg">
        <img src="image" alt="Mountains" width="600" height="400">
    </a>
    <div class="desc">Description</div>
    </div>

</body>
</html>
```

CSS :

```css
div.gallery {
    margin: 5px;
    border: 1px solid #ccc;
    float: left;
    width: 180px;
}

div.gallery:hover {
    border: 1px solid #777;
}

div.gallery img {
    width: 100%;
    height: auto;
}

div.desc {
    padding: 15px;
    text-align: center;
}
```