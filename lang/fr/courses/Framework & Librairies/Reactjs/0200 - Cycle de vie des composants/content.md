## Introduction

Dans React, le cycle de vie d'un composant représente les différentes étapes du composant au cours de son existence. React fournit des fonctions de callback pour attacher des fonctionnalités à chacune des étapes du cycle de vie de React. Dans ce chapitre, nous allons apprendre le cycle de vie (et l'API associée) d'un composant React.

### API du cycle de vie

Chaque composant React comporte trois étapes distinctes.

- **Mounting** − Le montage représente le rendu du composant React dans le nœud DOM donné.
- **Updating** − La mise à jour représente le nouveau rendu du composant React dans le nœud DOM donné pendant les changements d'état / mises à jour.
- **Unmounting** − Le démontage représente la suppression du composant React.

React fournit une collection d'événements du cycle de vie (ou API de rappel) pour attacher des fonctionnalités, qui seront exécutées au cours des différentes étapes du composant. La visualisation du cycle de vie et la séquence dans laquelle les événements du cycle de vie (APIs) sont invoqués comme indiqué ci-dessous.

