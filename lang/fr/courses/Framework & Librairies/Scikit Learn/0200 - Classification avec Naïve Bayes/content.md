## Introduction

Les méthodes de Naïve Bayes sont un ensemble d'algorithmes d'apprentissage supervisé basés sur l'application du théorème de Bayes avec l'hypothèse forte que tous les prédicteurs sont indépendants les uns des autres, c'est-à-dire que la présence d'une caractéristique dans une classe est indépendante de la présence de toute autre caractéristique dans la même classe. Il s'agit d'une hypothèse naïve, c'est pourquoi ces méthodes sont appelées méthodes Naïve Bayes.

Le théorème de Bayes établit la relation suivante afin de trouver la probabilité postérieure de la classe, c'est-à-dire la probabilité d'une étiquette et de certaines caractéristiques observées, P( Y⏐features ) : 

![Théorème de Bayes](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0200%20-%20Classification%20avec%20Na%C3%AFve%20Bayes/images/image1.png)

- **P( Y⏐features )** est la probabilité postérieure de la classe.
- **P( Y )** est la probabilité antérieure de la classe.
- **P( features⏐Y )** est la vraisemblance qui est la probabilité du prédicteur étant donné la classe.
- **P( features )** est la probabilité antérieure du prédicteur.

Scikit-learn fournit différents modèles de classificateurs Bayes naïfs, à savoir gaussien, multinomial, complémentaire et bernoullien. Tous ces modèles diffèrent principalement par l'hypothèse qu'ils font concernant la distribution de **P( features⏐Y )** c'est-à-dire la probabilité que le prédicteur soit donné à la classe.

**Modèle et description**

- **Gaussian Naïve Bayes** - Le classifieur gaussien de Naïve Bayes suppose que les données de chaque étiquette sont tirées d'une distribution gaussienne simple.
- **Multinomial Naïve Bayes** - Il suppose que les caractéristiques sont tirées d'une distribution multinomiale simple.
- **Bernoulli Naïve Bayes** - L'hypothèse de ce modèle est que les caractéristiques sont de nature binaire (0 et 1). Une application de la classification de Bernoulli Naïve Bayes est la classification de textes avec le modèle "sac de mots".
- **Complement Naïve Bayes** - Il a été conçu pour corriger les hypothèses sévères faites par le classificateur Multinomial Bayes. Ce type de classificateur NB est adapté aux ensembles de données déséquilibrés.

## Building Naïve Bayes Classifier

Nous pouvons également appliquer le classificateur Naïve Bayes au jeu de données Scikit-learn. Dans l'exemple ci-dessous, nous appliquons GaussianNB et ajustons le jeu de données breast_cancer de Scikit-leran.

### Exemple

```python
Import Sklearn
from sklearn.datasets import load_breast_cancer
from sklearn.model_selection import train_test_split
data = load_breast_cancer()
label_names = data['target_names']
labels = data['target']
feature_names = data['feature_names']
features = data['data']
    print(label_names)
    print(labels[0])
    print(feature_names[0])
    print(features[0])
train, test, train_labels, test_labels = train_test_split(
    features,labels,test_size = 0.40, random_state = 42
)
from sklearn.naive_bayes import GaussianNB
GNBclf = GaussianNB()
model = GNBclf.fit(train, train_labels)
preds = GNBclf.predict(test)
print(preds)
```

### Sortie

```python
[
    1 0 0 1 1 0 0 0 1 1 1 0 1 0 1 0 1 1 1 0 1 1 0 1 1 1 1
    1 1 0 1 1 1 1 1 1 0 1 0 1 1 0 1 1 1 1 1 1 1 1 0 0 1 1 
    1 1 1 0 0 1 1 0 0 1 1 1 0 0 1 1 0 0 1 0 1 1 1 1 1 1 0 
    1 1 0 0 0 0 0 1 1 1 1 1 1 1 1 0 0 1 0 0 1 0 0 1 1 1 0 
    1 1 0 1 1 0 0 0 1 1 1 0 0 1 1 0 1 0 0 1 1 0 0 0 1 1 1 
    0 1 1 0 0 1 0 1 1 0 1 0 0 1 1 1 1 1 1 1 0 0 1 1 1 1 1 
    1 1 1 1 1 1 1 0 1 1 1 0 1 1 0 1 1 1 1 1 1 0 0 0 1 1 0 
    1 0 1 1 1 1 0 1 1 0 1 1 1 0 1 0 0 1 1 1 1 1 1 1 1 0 1 
    1 1 1 1 0 1 0 0 1 1 0 1
]
```

La sortie ci-dessus consiste en une série de 0 et de 1 qui sont essentiellement les valeurs prédites des classes de tumeurs, à savoir maligne et bénigne.