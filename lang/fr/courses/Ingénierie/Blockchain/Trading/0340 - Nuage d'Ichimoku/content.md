Le nuage Ichimoku est une méthode d'analyse technique qui combine plusieurs indicateurs sur un seul graphique. Il est utilisé sur les graphiques en chandelier comme un outil de négociation qui fournit des informations sur les zones potentielles de soutien et de résistance des prix. Il est également utilisé comme un outil de prévision, et de nombreux traders l'emploient lorsqu'ils essaient de déterminer la direction des tendances futures et le momentum du marché.

Le nuage Ichimoku a été conceptualisé à la fin des années 1930 par un journaliste japonais nommé Goichi Hosada. Cependant, sa stratégie de trading innovante n'a été publiée qu'en 1969, après des décennies d'études et d'améliorations techniques. Hosada l'a appelée Ichimoku Kinko Hyo, ce qui se traduit du japonais par "graphique d'équilibre en un coup d'œil".

## Comment fonctionne-t-il ?

Le système Ichimoku Cloud affiche des données basées sur des indicateurs avancés et retardés, et le graphique est composé de cinq lignes :

- **Ligne de conversion (Tenkan-sen)** : moyenne mobile sur 9 périodes.
- **Ligne de base (Kijun-sen)** : moyenne mobile sur 26 périodes.
- **Leading Span A (Senkou Span A)** : moyenne mobile des lignes de conversion et de base projetée sur 26 périodes dans le futur.
- **Leading Span B (Senkou Span B)** : moyenne mobile sur 52 périodes projetée sur 26 périodes dans le futur.
- **Lagging Span (Chikou Span)** : le prix de clôture de la période actuelle projeté sur 26 périodes dans le passé.

![nuage d'ichimoku](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Ing%C3%A9nierie/Blockchain/Trading/0340%20-%20Nuage%20d'Ichimoku/images/image1.png)

L'espace entre la Leading Span A (3) et la Leading Span B (4) est ce qui produit le nuage (Kumo), qui est probablement l'élément le plus remarquable du système Ichimoku. Les deux lignes sont projetées 26 périodes dans le futur pour fournir des prévisions et, en tant que telles, sont considérées comme des indicateurs avancés. Le Chikou Span (5), quant à lui, est un indicateur retardé projeté 26 périodes dans le passé.

Par défaut, les nuages sont affichés en vert ou en rouge - pour faciliter la lecture. Un nuage vert est créé lorsque la Leading Span A (ligne verte du nuage) est supérieure à la Leading Span B (ligne rouge du nuage). Naturellement, un nuage rouge résulte de la situation inverse.

Il convient de noter que - contrairement aux autres méthodes - les moyennes mobiles utilisées par la stratégie Ichimoku ne sont pas basées sur les prix de clôture des bougies. Au lieu de cela, les moyennes sont calculées sur la base des points hauts et bas enregistrés au cours d'une période donnée (moyenne haute-basse). 

Par exemple, l'équation standard pour une ligne de conversion sur 9 jours est la suivante :

```bash
Conversion Line = (9d high + 9d low) / 2
```

### Paramètres Ichimoku

Après plus de trois décennies de recherches et de tests, Goichi Hosada a conclu que les réglages (9, 26, 52) donnaient les meilleurs résultats. À l'époque, l'emploi du temps des Japonais comprenait le samedi, le chiffre 9 représente donc une semaine et demie (6 + 3 jours). Les chiffres 26 et 52 représentent respectivement un et deux mois.

Si ces paramètres sont toujours privilégiés dans la plupart des contextes de trading, les chartistes sont toujours en mesure de les ajuster pour s'adapter à différentes stratégies. Sur les marchés des crypto-monnaies, par exemple, de nombreux traders ajustent les paramètres Ichimoku pour refléter les marchés 24/7 - passant souvent de (9, 26, 52) à (10, 30, 60). Certains vont même plus loin et ajustent les paramètres à (20, 60, 120) afin de réduire les faux signaux.

Cependant, le débat se poursuit sur l'efficacité de la modification des paramètres. Alors que certains soutiennent qu'il est logique de les ajuster, d'autres affirment que l'abandon des paramètres standard perturberait l'équilibre du système et produirait de nombreux signaux non valides.

## Analyser le graphique

### Signaux de trading Ichimoku

En raison de ses multiples éléments, le nuage Ichimoku produit différents types de signaux. Nous pouvons les diviser en signaux de momentum et signaux de suivi de tendance.

Les signaux de momentum : sont générés en fonction de la relation entre le prix du marché, la ligne de base et la ligne de conversion. Les signaux de momentum haussiers sont générés lorsque la ligne de conversion et le prix du marché, ou les deux, dépassent la ligne de base. Les signaux de momentum baissiers sont générés lorsque la ligne de conversion et le prix du marché, ou les deux, passent en dessous de la ligne de base. Le croisement entre la ligne de conversion (Tenkan-sen) et la ligne de base (Kijun-sen) est souvent appelé croisement TK.

Signaux de suivi de tendance : ils sont générés en fonction de la couleur du nuage et de la position du prix du marché par rapport au nuage. Comme mentionné, la couleur du nuage reflète la différence entre les Leading Spans A et B.

En d'autres termes, lorsque les prix sont constamment au-dessus des nuages, il est plus probable que l'actif soit dans une tendance à la hausse. À l'inverse, des prix évoluant sous les nuages peuvent être interprétés comme un signe baissier, indiquant une tendance à la baisse. À quelques exceptions près, la tendance peut être considérée comme plate ou neutre lorsque les prix effectuent des mouvements latéraux à l'intérieur du nuage.

Le Lagging Span (Chikou Span) est un autre élément qui peut aider les traders à repérer et à confirmer les renversements de tendance potentiels. Elle donne un aperçu de la force de l'action des prix, confirmant éventuellement une tendance haussière lorsqu'elle est supérieure aux prix du marché, ou une tendance baissière lorsqu'elle est inférieure. Normalement, la Lagging Span est utilisée en conjonction avec les autres composants du nuage Ichimoku, et non pas seule.

En résumé :

- Signaux Momentum
    - Le prix du marché évolue au-dessus (haussier) ou au-dessous (baissier) de la ligne de base.
    - Croisement TK : La ligne de conversion se déplace au-dessus (haussier) ou au-dessous (baissier) de la ligne de base.
- Signaux de suivi de tendance
    - Le prix du marché se déplace au-dessus (haussier) ou au-dessous (baissier) du nuage.
    - La couleur du nuage passe du rouge au vert (haussier) ou du vert au rouge (baissier).
    - Lagging Span au-dessus (haussier) ou en dessous (baissier) des prix du marché.

### Niveaux de soutien et de résistance

Le graphique Ichimoku peut également être utilisé pour identifier les zones de support et de résistance. Typiquement, la Leading Span A (ligne verte du nuage) agit comme une ligne de support pendant les tendances haussières et comme une ligne de résistance pendant les tendances baissières. Dans les deux cas, les chandeliers ont tendance à se rapprocher de la Leading Span A, mais si le prix se déplace dans le nuage, la Leading Span B peut également agir comme une ligne de support/résistance. De plus, le fait que les deux Leading Spans soient projetées 26 périodes dans le futur permet aux traders d'anticiper les zones de support et de résistance potentielles à venir.

### Force du signal

La force des signaux générés par le nuage Ichimoku dépend fortement de leur adéquation avec la tendance générale. Un signal qui s'inscrit dans une tendance plus large et clairement définie sera toujours plus fort qu'un signal qui apparaît brièvement en opposition à la tendance dominante.

En d'autres termes, un signal haussier peut être trompeur s'il n'est pas accompagné d'une tendance haussière. Ainsi, chaque fois qu'un signal est généré, il est important de reconnaître la couleur et la position du nuage. Le volume d'échange est également un élément à prendre en compte.

N'oubliez pas que l'utilisation d'Ichimoku avec des délais plus courts (graphiques intrajournaliers) a tendance à générer beaucoup de bruit et de faux signaux. D'une manière générale, les périodes plus longues (graphiques quotidiens, hebdomadaires et mensuels) produisent des signaux de momentum et de suivi de tendance plus fiables.

## Conclusion

Goichi Hosada a consacré plus de 30 ans de sa vie à créer et à affiner le système Ichimoku, qui est désormais utilisé par des millions de traders dans le monde. En tant que méthode graphique polyvalente, les nuages Ichimoku sont utilisés pour identifier à la fois les tendances du marché et le momentum. De même, les Leading Spans permettent aux chartistes d'anticiper plus facilement les niveaux potentiels de soutien et de résistance qui doivent encore être testés.

Bien que les graphiques puissent sembler trop chargés et assez complexes au premier abord, ils ne reposent pas sur des données humaines subjectives comme d'autres méthodes d'analyse technique (par exemple, le tracé de lignes de tendance). Et malgré le débat permanent sur les paramètres Ichimoku, la stratégie est relativement facile à utiliser. 

Comme tout indicateur, cependant, il doit être utilisé en conjonction avec d'autres techniques pour confirmer les tendances et minimiser les risques de trading. La quantité d'informations qu'affiche ce graphique peut également être écrasante pour les débutants. Pour ces traders, il est généralement préférable de se familiariser avec des indicateurs plus basiques avant de s'attaquer au nuage Ichimoku.