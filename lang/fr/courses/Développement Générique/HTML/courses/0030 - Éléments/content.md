Ce cours aborde plus en détails les notions d’éléments et de balises, en HTML.

## Les éléments

Tout le principe du HTML est basé sur la notion d’élément. Lorsque cette notion est comprise, l’essentiel du langage HTML est également compris. 

Les éléments HTML vont permettre de créer la structure de la page HTML, de définir chaque contenu de la page, et de transmettre certaines informations utiles au navigateur pour afficher la page.

En HTML, les éléments permettent à la fois de définir la **structure d’une page web**, en l’organisant avec un en-tête, un corps de page et un pied de page, des titres, des sous-titres, des paragraphes, etc., et également de définir chaque contenu de la page tel que les titres, les paragraphes, les liens (etc…), mais également de **transmettre des informations** au navigateur afin que ce dernier affiche la page correctement. Par exemple lorsque l’attribut **lang** est défini dans la balise ```<html>```, cela informe le navigateur de la langue utilisée sur la page qu’il affiche, ou encore l’encodage qui permet d’indiquer au navigateur la manière dont il va devoir afficher les accents, etc...

Dans un document HTML, les éléments sont utilisés pour **baliser** le contenu, d’où la seconde dénomination : **les balises**.

## Les balises

En HTML, il existe deux types de balises :

- Les balises doubles, composées d’une balise ouvrante et d’une balise fermante
- Les balises orphelines, dont la particularité est qu’elles n’ont pas de balises fermantes

La balise ouvrante est composée de deux chevrons (```<>```) et du nom de l'élément placé entre ces deux chevrons. La balise fermante est quasiment similaire, à ceci près qu’il faut ajouter un slash (```/```) avant le nom de l’élément. Le contenu est placé entre ces deux balises. 

Pour les balises orphelines, qui n’ont pas de balises fermantes, il est d’usage courant d’ajouter un slash juste avant le deuxième chevron, pour indiquer que la balise est orpheline. Cependant, cela n’est pas obligatoire.

Exemple d’une balise double :

```html
<p>Je suis un paragraphe</p>
```

Exemple d’une balise orpheline : 

```html
<img src="photo.jpg" alt="logo" />
```

Ainsi, en ce qui concerne les balises standard (ou non orpheline), ne faut-il jamais oublier de fermer la balise afin d’éviter de perturber l’affichage du contenu par la suite. 

Voici un exemple complet :

```html
<body>
	<h1>Titre principal</h1>
	<p>Je suis un paragraphe</p>
	<img src="illustration.jpg" alt="illustration" />
</body>
```