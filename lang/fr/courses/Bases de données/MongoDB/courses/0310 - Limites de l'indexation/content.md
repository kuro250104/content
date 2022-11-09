Dans ce chapitre, nous allons apprendre les limites de l'indexation et ses autres composants.

## Frais généraux supplémentaires

Chaque index occupe de l'espace et entraîne une surcharge à chaque insertion, mise à jour et suppression. Ainsi, si vous utilisez rarement votre collection pour des opérations de lecture, il est logique de ne pas utiliser d'index.

## Utilisation de la RAM

Les index étant stockés en RAM, vous devez vous assurer que la taille totale de l'index ne dépasse pas la limite de la RAM. Si la taille totale dépasse la taille de la RAM, certains index commenceront à être supprimés, ce qui entraînera une perte de performance.

## Limites des requêtes

L'indexation ne peut pas être utilisée dans des requêtes qui utilisent -

- Expressions régulières ou opérateurs de négation comme $nin, $not, etc.
- Opérateurs arithmétiques comme $mod, etc.
- clause $where

Il est donc toujours conseillé de vérifier l'utilisation de l'index pour vos requêtes.

## Limites de la clé d'indexation

À partir de la version 2.6, MongoDB ne créera pas d'index si la valeur du champ d'index existant dépasse la limite de la clé d'index.

## Insertion de documents dépassant la limite de la clé d'indexation

MongoDB n'insérera pas de document dans une collection indexée si la valeur du champ indexé de ce document dépasse la limite de la clé d'indexation. Il en va de même pour les utilitaires mongorestore et mongoimport.

## Maximum Ranges

- Une collection ne peut pas avoir plus de 64 index.
- La longueur du nom de l'index ne peut pas être supérieure à 125 caractères.
- Un index composé peut avoir un maximum de 31 champs indexés.