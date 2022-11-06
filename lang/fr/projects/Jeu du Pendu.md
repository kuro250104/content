## Durée approximative

1 jour

## Prérequis

- <a href="https://microlead.fr/echelles/javascript" title="Prérequis en JavaScript" target="_blank">JavaScript niveau 5</a>

## Énoncé

### Description courte

Refaire le jeu du pendu sur une page web en JavaScript.

### Listing de fonctionnalités

- Le programme doit choisir un mot aléatoire parmi une liste de mots rentrée en dur dans l’application.
- Il faut ensuite compter le nombre de lettres du mot choisi et afficher la première suivie d’autant d’underscores (« _ ») que le reste de lettres.
- L’utilisateur doit pouvoir rentrer une lettre.
- Si celle-ci est présente dans le mot mystère, elle est dévoilée à chacun de ses emplacements et est ajoutée à une liste de suivi des lettres proposées.
- Si elle n’est pas présente dans le mot, l’utilisateur perd une vie (ce qui peut être symbolisé par un dessin de pendu qui s’incrémente à chaque erreur) et la lettre est aussi ajoutée à la liste.
- Si le mot est révélé complètement, l’utilisateur gagne et le programme lui fait savoir avant de s’arrêter.
- Si l’utilisateur n’a plus de vie (le dessin est complet), il perd et l’application lui indique avant de s’arrêter.

### Contraintes

L’utilisateur ne doit pas pouvoir rentrer autre chose qu’une lettre. Il ne doit pas non plus pouvoir rentrer une lettre déjà proposée.

### Pour aller plus loin

- Vous pouvez ajouter un chronomètre pour limiter le temps disponible pour proposer une lettre.
- Vous pouvez déporter la liste de mots aléatoires dans un fichier texte séparé.
- Vous pouvez ajouter une gestion de points relatives au nombre d’erreurs.
- Vous pouvez ajouter un système de compte, pour lier vos scores à un utilisateur. Dans cette optique nous vous conseillons de passer par le « localStorage » du navigateur.

### Critères de réussite

Le jeu est fonctionnel. Si l’utilisateur a entièrement révélé le mot, il gagne et le jeu s’arrête. S’il n’a plus de vie, il perd et le jeu s’arrête.

### Astuces

#### Astuce 1

Pour contrôler les entrées de caractères, vous pouvez vous servir des regex, ou intercepter les événements à l’appui des touches du clavier.