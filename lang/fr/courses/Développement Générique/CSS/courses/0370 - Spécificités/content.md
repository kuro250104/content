Lorsque 2 règles CSS pointant vers un même élément entrent en conflit, la navigateur suit certaines règles pour déterminer laquelle des deux est la plus spécifique, et donc laquelle des deux doit être utilisée. 

Il est possible d’imaginer le système de spécificité comme un classement qui détermine quelle déclaration de style doit être appliquée de manière prioritaire à un élément.

Le sélecteur universel * a une spécificité basse, tandis que les sélecteurs **ID** ont une spécificité importante.

## Hiérarchie de spécificité 

Chaque sélecteur a une place dans la hiérarchie de la spécificité. Il y a en tout 4 catégories qui définissent le niveau d’un sélecteur :

- **Le style inline** : c’est le style qui est défini directement dans les balises d’un élément inline, tel que ```<p style="color: red;">```
- **Les ID** : C’est un identifiant unique pour les éléments de la page
- **Classes**, **attributs** et **pseudo-classes**
- **Éléments** et **pseudo-éléments**

## Calculer la spécificité

Voici comment calculer la spécificité :

- Partir de 0
- Ajouter 1000 points pour les attributs style inline
- Ajouter 100 points pour chaque ID
- Ajouter 10 points pour chaque classe, attribut et pseudo-classe
- Ajouter 1 point pour chaque élément et pseudo-élément

```html
1: <p>
2: #page p
3: <span style="color: red; font-family: sans-serif;">Texte</span>
```

Dans l’exemple ci-dessus, c’est le point 3 qui est plus haut dans la hiérarchie, car il a 1000 points grâce à l’attribut ```style``` ; tandis que le point 1 n’a qu’1 point puisque c’est un **élément** et le point 2 a 100 points comme c’est un **id**.

## Règles concernant la spécificité

En cas de spécificité égale, **la dernière “règle” compte**. Si la même ligne de code est écrite 2 fois, c’est la plus récente qui sera prise en compte. Dans l’ordre de lecture du fichier par le navigateur, la plus récente est donc la dernière écrite.

Exemple :

```css
p {
	color: red;
}

p {
	color: black;
}
```

Dans l’exemple ci-dessus, c’est la couleur noire qui s’applique aux paragraphes, car c’est le dernier style appliqué aux paragraphes qui sont pris en compte. 

### Sélecteurs ID

**Les sélecteurs ID ont une spécificité plus importante que les sélecteurs d’attribut.**

Exemple :

```css
p #quote {
	background-color: grey;
}

#quote {
	background-color: orange;
}

p [id="quote"] {
	background-color: red;
}
```

Dans cet exemple, la couleur d’arrière-plan assignée aux paragraphes ```#quote``` est le gris, car les sélecteurs ID ont une spécificité plus importante que les sélecteurs d’attribut. 

## Sélecteurs contextuels

**Les sélecteurs contextuels sont plus spécifiques que les sélecteurs seuls**. De plus, entre un code CSS écrit dans un fichier externe et un code CSS écrit entre les balises ```<style>``` d’une page HTML, le CSS le plus à proximité du code HTML sera plus spécifique. Ainsi c’est le code situé entre les balises ```<style>``` d’une page HTML qui sera pris en compte. 

Exemple :

Fichier CSS externe : 

```css
#intro h1 /* Est plus spécifique que #intro seul ou h1 seul */ {
	text-transform: uppercase;
}
```

Code CSS au sein d’une page HTML :

```html
<style>
	#intro h1 {
		text-transform: lowercase;
	}
</style>
```

Dans l’exemple ci-dessus, c’est le code CSS situé entre les balises ```<style>``` de la page HTML qui s’applique, car étant le plus proche du code HTML, il est plus spécifique que le code CSS externe. 

## Sélecteur de classe et sélecteurs d’éléments

**Le sélecteur de classe l’emporte sur n’importe quel sélecteur d'éléments.** 

Exemple :

```css
.titre {
	color: blue;
}

h1 {
	color: yellow;
}
```

Dans cet exemple, le titre est de couleur bleue, car le sélecteur de classe l’emporte sur tous les autres sélecteurs d’éléments. 

## Sélecteur universel et valeurs héritées

Le sélecteur universel (```*```) et les valeurs héritées ont une spécificité à 0.