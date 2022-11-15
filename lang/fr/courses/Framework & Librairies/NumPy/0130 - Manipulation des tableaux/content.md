## Introduction

Plusieurs routines sont disponibles dans le package NumPy pour la manipulation des éléments de l'objet ndarray. Elles peuvent être classées dans les types suivants -

## Changer de forme

**Forme et description**

- **reshape** - Donne une nouvelle forme à un tableau sans modifier ses données.
- **flat** - Un itérateur 1-D sur le tableau
- **flatten** - Renvoie une copie du tableau réduit à une seule dimension.
- **ravel** - Retourne un tableau contigu aplati

## Opérations de transposition

**Fonctionnement et description**

- **transpose** - Permute les dimensions d'un tableau
- **ndarray.T** - Identique à self.transpose()
- **rollaxis** - Fait reculer l'axe spécifié
- **swapaxes** - Intervertir les deux axes d'un tableau

## Changement de dimensions

**Dimension & Description**

- **broadcast** - Produit un objet qui imite la diffusion
- **broadcast_to** - Diffuse un tableau vers une nouvelle forme
- **expand_dims** - Développe la forme d'un tableau
- **squeeze** - Supprime les entrées unidimensionnelles de la forme d'un tableau

## Joindre des tableaux

**Tableau et description**

- **concatenate** - Joindre une séquence de tableaux le long d'un axe existant
- **stack** - Joindre une séquence de tableaux le long d'un nouvel axe
- **hstack** - Empile les tableaux en séquence horizontalement (par colonne).
- **vstack** - Empile les tableaux en séquence verticale (par rangée)

## Fractionnement des tableaux

**Tableau et description**

- **split** - Divise un tableau en plusieurs sous-réseaux.
- **hsplit** - Divise un tableau en plusieurs sous-réseaux horizontalement (par colonne).
- **vsplit** - Divise un tableau en plusieurs sous-réseaux verticalement (par rangée).

## Ajout / Suppression d'éléments

**Élément et description**

- **resize** - Renvoie un nouveau tableau avec la forme spécifiée
- **append** - Ajoute les valeurs à la fin d'un tableau
- **insert** - Insère les valeurs le long de l'axe donné avant les indices donnés.
- **delete** - Renvoie un nouveau tableau avec des sous-réseaux le long d'un axe supprimé.
- **unique** - Trouve les éléments uniques d'un tableau