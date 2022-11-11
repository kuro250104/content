Dans ce cours, nous allons comprendre ce qu'est Scikit-Learn ou Sklearn, l'origine de Scikit-Learn et d'autres sujets connexes tels que les communautés et les contributeurs responsables du développement et de la maintenance de Scikit-Learn, ses conditions préalables, son installation et ses fonctionnalités.

## Qu'est-ce que Scikit-Learn (Sklearn) ?

Scikit-learn (Sklearn) est la bibliothèque la plus utile et la plus robuste pour l'apprentissage automatique en Python. Elle fournit une sélection d'outils efficaces pour l'apprentissage automatique et la modélisation statistique, notamment la classification, la régression, le regroupement et la réduction de la dimensionnalité, via une interface cohérente en Python. Cette bibliothèque, qui est en grande partie écrite en Python, s'appuie sur NumPy, SciPy et Matplotlib.

## Origine de Scikit-Learn

Il s'appelait à l'origine scikits.learn et a été initialement développé par David Cournapeau dans le cadre d'un projet Google summer of code en 2007. Plus tard, en 2010, Fabian Pedregosa, Gaël Varoquaux, Alexandre Gramfort et Vincent Michel, de FIRCA (Institut français de recherche en informatique et en automatique), ont porté ce projet à un autre niveau et ont fait la première version publique (v0.1 beta) le 1er février 2010.

Jetons un coup d'oeil à l'historique de ses versions :

- Mai 2019 : scikit-learn 0.21.0
- Mars 2019 : scikit-learn 0.20.3
- Décembre 2018 : scikit-learn 0.20.2
- Novembre 2018 : scikit-learn 0.20.1
- Septembre 2018 : scikit-learn 0.20.0
- Juillet 2018 : scikit-learn 0.19.2
- Juillet 2017 : scikit-learn 0.19.0
- Septembre 2016 : scikit-learn 0.18.0
- Novembre 2015. scikit-learn 0.17.0
- Mars 2015. scikit-learn 0.16.0
- Juillet 2014. scikit-learn 0.15.0
- Août 2013. scikit-learn 0.14

## Communauté et contributeurs

Scikit-learn est un effort communautaire et tout le monde peut y contribuer. Ce projet est hébergé sur https://github.com/scikit-learn/scikit-learn. Les personnes suivantes sont actuellement les principaux contributeurs au développement et à la maintenance de Sklearn :

- Joris Van den Bossche (Data Scientist)
- Thomas J Fan (Software Developer)
- Alexandre Gramfort (Machine Learning Researcher)
- Olivier Grisel (Machine Learning Expert)
- Nicolas Hug (Associate Research Scientist)
- Andreas Mueller (Machine Learning Scientist)
- Hanmin Qin (Software Engineer)
- Adrin Jalali (Open Source Developer)
- Nelle Varoquaux (Data Science Researcher)
- Roman Yurchak (Data Scientist)

Diverses organisations comme Booking.com, JP Morgan, Evernote, Inria, AWeber, Spotify et bien d'autres utilisent Sklearn.

## Conditions préalables

Avant de commencer à utiliser la dernière version de scikit-learn, nous avons besoin de ce qui suit :

- Python (>=3.5)
- NumPy (>= 1.11.0)
- Scipy (>= 0.17.0)
- Joblib (>= 0.11)
- Matplotlib (>= 1.5.1) est nécessaire pour les capacités de traçage de Sklearn.
- Pandas (>= 0.18.0) est nécessaire pour certains des exemples scikit-learn utilisant la structure et l'analyse des données.

## Installation

Si vous avez déjà installé NumPy et Scipy, voici les deux façons les plus simples d'installer scikit-learn

### Utilisation de pip

La commande suivante peut être utilisée pour installer scikit-learn via pip -.

```bash
pip install -U scikit-learn
```

### Utilisation de conda

La commande suivante peut être utilisée pour installer Scikit-learn via Conda

```bash
conda install scikit-learn
```

D'autre part, si NumPy et Scipy ne sont pas encore installés sur votre station de travail Python, vous pouvez les installer en utilisant pip ou conda.

Une autre option pour utiliser scikit-learn est d'utiliser des distributions Python comme Canopy et Anaconda car elles fournissent toutes deux la dernière version de scikit-learn.

## Caractéristiques

Plutôt que de se concentrer sur le chargement, la manipulation et la synthèse des données, la bibliothèque Scikit-learn se concentre sur la modélisation des données. Certains des groupes de modèles les plus populaires fournis par Scikit-learn sont les suivants :

- **Algorithmes d'apprentissage supervisé** - Presque tous les algorithmes d'apprentissage supervisé les plus populaires, comme la régression linéaire, la machine à vecteur de support (SVM), l'arbre de décision, etc. font partie de Scikit-learn.
- **Algorithmes d'apprentissage non supervisé** - D'autre part, scikit-learn comprend également tous les algorithmes d'apprentissage non supervisé les plus courants, tels que le regroupement, l'analyse factorielle, l'ACP (analyse en composantes principales) et les réseaux neuronaux non supervisés.
- **Regroupement** - Ce modèle est utilisé pour regrouper les données non étiquetées.
- **Validation croisée** - Elle est utilisée pour vérifier la précision des modèles supervisés sur des données non identifiées.
- **Réduction de la dimensionnalité** - Ce modèle est utilisé pour réduire le nombre d'attributs dans les données, qui peuvent ensuite être utilisés pour le résumé, la visualisation et la sélection des caractéristiques.
- **Méthodes d'ensemble** - Comme son nom l'indique, cette méthode est utilisée pour combiner les prédictions de plusieurs modèles supervisés.
- **Extraction de caractéristiques** - Elle est utilisée pour extraire les caractéristiques des données afin de définir les attributs dans les données d'image et de texte.
- **Sélection des caractéristiques** - Elle est utilisée pour identifier les attributs utiles afin de créer des modèles supervisés.
- **Open Source** - Il s'agit d'une bibliothèque open source qui peut également être utilisée commercialement sous licence BSD.