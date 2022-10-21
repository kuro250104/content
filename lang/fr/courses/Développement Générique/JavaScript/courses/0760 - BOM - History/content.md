Le BOM intègre un objet nommé ```history```. Comme son nom l’indique, il va nous permettre de manipuler l’historique du navigateur, et nous propose pour cela plusieurs propriétés et méthodes.

## Propriétés et méthodes

L’objet ```history``` possède plusieurs propriétés et méthodes que l’on peut utiliser, soit en passant par le préfixe “window” (```window.history```), soit en appelant directement “history” :

- L’attribut ```length``` retourne le nombre d’éléments dans l’historique, c’est-à-dire le nombre d’URL parcourues durant la session.
- La méthode ```go()``` nous permet de charger une page depuis l’historique de session. On peut ainsi lui passer un nombre en argument qui représente la place de la page qu’on souhaite atteindre dans l’historique par rapport à la page actuelle (-1 pour la page précédente et 1 pour la page suivante par exemple)
- La méthode ```back()``` nous permet de charger la page précédente dans l’historique de session par rapport à la page actuelle. Utiliser ```back()``` est équivalent à utiliser ```go(-1)```
- La méthode ```forward()``` nous permet de charger la page suivante dans l’historique de session par rapport à la page actuelle. Utiliser ```forward()``` est équivalent à utiliser ```go(1)```

Voici quelques exemples d’utilisation de l’objet ```history``` :

```js
// permet d’afficher le nombre de pages dans 
// l’historique du navigateur
console.log( history.length )

// permet de revenir une fois en arrière
history.back()

// permet d’avancer une fois dans l’historique
history.forward()

// permet d’avancer trois fois dans l’historique
history.go(3)

// permet de reculer deux fois dans l’historique
history.go(-2)
```