## Durée approximative

2 jours

## Prérequis

- JavaScript - niveau 5
- React Native - niveau 7

## Énoncé

### Description courte

Construire et déployer une application mobile de création et de lecture de notes textuelles.

### Listing de fonctionnalités

Au lancement, l’application doit afficher la liste des notes précédemment rédigées (avec leurs titres) ainsi qu’un bouton « + » pour en ajouter de nouvelles.
Lorsque l’on appuie sur une note, on arrive sur une page contenant l’intégralité du contenu de cette dernière et la possibilité de la modifier.
Si l’on appuie sur le bouton « + », on est redirigé vers une page de création de note.
Les pages de modification/création de notes doivent comporter un bouton de sauvegarde et un bouton de retour.
A la sauvegarde d’une nouvelle note ou d’une note modifiée, on est redirigé vers la liste des notes.
Si l’on maintient un appui sur une note, l’application nous propose de la supprimer.

### Contraintes

- Il ne doit pas être possible de créer une note sans titre.
- Si l’utilisateur veut revenir sur la liste depuis la page de modification/création de note (via le bouton de retour) alors qu’il a modifier/rédiger un texte, l’application doit lui demander s’il veut sauvegarder ce texte ou revenir en arrière.

### Critères de réussite

L’application fonctionne et il est possible de la lancer depuis un « .apk » sur téléphone. Il est possible de voir les notes, les lire en intégralité, en ajouter, les modifier, et les supprimer.

### Astuces

#### Astuce 1

Pour sauvegarder les notes, vous pouvez passer par le système « AsyncStorage » de React.

#### Astuce 2

Pour stocker dynamiquement les états de vos différents champs (titre, texte, recherche … etc), vous pouvez vous servir du concept de « useState » en React Native.