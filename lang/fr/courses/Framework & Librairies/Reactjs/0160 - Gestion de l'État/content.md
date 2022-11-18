## Introduction

La gestion des états est l'une des caractéristiques importantes et inévitables de toute application dynamique. React fournit une API simple et flexible pour prendre en charge la gestion de l'état dans un composant React. Comprenons comment maintenir l'état dans une application React dans ce chapitre.

## Qu'est-ce que le state?

L'état (le *state*) représente la valeur d'une propriété dynamique d'un composant React à une instance donnée. React fournit un magasin de données dynamiques pour chaque composant. Les données internes représentent l'état d'un composant React et peuvent être accédées en utilisant la variable membre this.state du composant. Chaque fois que l'état du composant est modifié, le composant se rendra à nouveau en appelant la méthode ```render()``` avec le nouvel état.

Un exemple simple pour mieux comprendre la gestion des états est l'analyse d'un composant horloge en temps réel. La tâche principale du composant horloge est d'afficher la date et l'heure d'un lieu à une instance donnée. Comme l'heure actuelle change toutes les secondes, le composant horloge doit maintenir la date et l'heure actuelles dans son état. Comme l'état du composant horloge change toutes les secondes, la méthode ```render()``` de l'horloge sera appelée toutes les secondes et la méthode ```render()``` affichera l'heure actuelle en utilisant son état actuel.

La représentation simple de l'état est la suivante -

```js
{ 
    date: '2020-10-10 10:10:10' 
}
```

Nous allons créer un nouveau composant Horloge plus tard dans ce chapitre.

Ici,

- API de gestion des états
- Composant apatride
- Gestion de l'état à l'aide de React Hooks
- Cycle de vie des composants
- Cycle de vie des composants à l'aide de React Hooks
- Mise en page dans le composant
- Pagination
- Material UI