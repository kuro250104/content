## Qu'est-ce que le SAR parabolique ?

L'analyste technique J. Welles Wilder Jr. a développé l'indicateur SAR (Parabolic Stop and Reverse) à la fin des années 1970. Il a été présenté dans son livre New Concepts in Technical Trading Systems, avec d'autres indicateurs populaires, tels que l'indice de force relative (RSI).

En fait, Wilder appelait cette approche le Parabolic Time/Price System, tandis que le concept du SAR était présenté comme suit : “SAR signifie Stop and Reverse. Il s'agit du point auquel une transaction longue est abandonnée et une transaction courte est ouverte, ou vice versa.”

Aujourd'hui, ce système est communément appelé l'indicateur SAR parabolique, qui est utilisé comme un outil pour identifier les tendances du marché et les points potentiels de retournement. Bien que Wilder ait développé manuellement de nombreux indicateurs d'analyse technique (TA - Technical Analysis), ils font désormais partie de la plupart des systèmes de trading numériques et des logiciels graphiques. Ainsi, ces techniques ne nécessitent plus de calculs manuels et sont relativement simples à utiliser.

## Comment fonctionne-t-il ?

L'indicateur SAR parabolique se compose de petits points qui sont placés soit au-dessus, soit au-dessous du prix du marché. La disposition des points crée une parabole, mais chaque point représente une seule valeur SAR.

En bref, les points sont placés en dessous du prix pendant une tendance à la hausse, et au-dessus pendant une tendance à la baisse. Ils sont également tracés pendant les périodes de consolidation, lorsque le marché évolue latéralement. Mais dans ce cas, les points passent d'un côté à l'autre beaucoup plus fréquemment. En d'autres termes, l'indicateur SAR parabolique est moins utile lorsque les marchés ne suivent pas une tendance.

## Avantages

Le SAR parabolique peut donner un aperçu de la direction et de la durée des tendances du marché, ainsi que des points potentiels de retournement. En tant que tel, il peut augmenter les chances des investisseurs de trouver de bonnes opportunités d'achat et de vente.

Certains traders utilisent également l'indicateur SAR parabolique pour déterminer des prix stop-loss dynamiques, afin que leurs stops suivent la tendance du marché. Cette technique est souvent appelée "trailing stop-loss". 

Essentiellement, elle permet aux traders de bloquer les profits déjà réalisés, car leurs positions sont fermées dès que la tendance s'inverse. Dans certaines situations, elle peut également empêcher les traders de fermer des positions rentables ou d'entrer dans une transaction trop tôt.

## Limites

Comme nous l'avons mentionné, le SAR parabolique est particulièrement utile dans les marchés à tendance, mais pas autant pendant les périodes de consolidation. En l'absence d'une tendance claire, l'indicateur est plus susceptible de fournir de faux signaux, ce qui peut entraîner des pertes importantes.

Un marché agité (qui monte et descend trop rapidement) peut également fournir de nombreux signaux trompeurs. Par conséquent, l'indicateur SAR parabolique a tendance à être plus efficace lorsque les prix changent à un rythme plus graduel.

Un autre élément à prendre en compte est la sensibilité de l'indicateur, qui peut être ajustée manuellement. Plus la sensibilité est élevée, plus les risques de faux signaux sont importants.

Dans certains cas, les faux signaux peuvent encourager les traders à clôturer trop tôt des positions gagnantes, en vendant des actifs qui ont encore un potentiel de gain. Pire encore, les fausses ruptures peuvent donner aux investisseurs un faux sentiment d'optimisme, les incitant à acheter trop tôt.

Enfin, comme l'indicateur ne tient pas compte du volume des transactions, il ne donne pas beaucoup d'informations sur la force d'une tendance. Bien que les grands mouvements du marché entraînent un élargissement de l'écart entre chaque point, cela ne doit pas être considéré comme l'indication d'une tendance forte.

Quelle que soit la quantité d'informations dont disposent les traders et les investisseurs, les risques feront toujours partie des marchés financiers. Mais, beaucoup d'entre eux combinent le SAR parabolique avec d'autres stratégies ou indicateurs comme moyen de minimiser les risques et de compenser les limitations. 

Wilder recommande d'utiliser l'indice directionnel moyen avec le Parabolic SAR pour évaluer la force des tendances. En outre, les moyennes mobiles ou l'indicateur RSI peuvent également être inclus dans l'analyse avant de prendre une position.

## Le calcul du SAR parabolique

Aujourd'hui, les programmes informatiques effectuent les calculs automatiquement. Mais pour ceux qui sont intéressés, cette section donne une brève explication du calcul du SAR parabolique.

Les points SAR sont calculés sur la base des données existantes du marché. Ainsi, pour calculer le SAR d'aujourd'hui, nous utilisons le SAR d'hier, et pour calculer la valeur de demain, nous utilisons le SAR d'aujourd'hui.

Pendant une tendance haussière, la valeur SAR est calculée sur la base des sommets précédents. Lors d'une tendance baissière, on considère plutôt les creux précédents. Wilder a appelé les points les plus hauts et les plus bas d'une tendance les points extrêmes (EP). Cependant, l'équation n'est pas la même pour les tendances haussières et les tendances baissières.

Pour les tendances à la hausse :

```bash
SAR = SAR antérieur + AF x (EP antérieur - SAR antérieur)
```

Pour les tendances à la baisse :

```bash
SAR = SAR antérieur - AF x (SAR antérieur - EP antérieur)
```

AF est le facteur d'accélération (*Acceleration Factor*). Il commence à 0,02 et augmente de 0,02 chaque fois que le prix atteint un nouveau sommet (pour les tendances à la hausse) ou un nouveau creux (pour les tendances à la baisse). Toutefois, si la limite de 0,20 est atteinte, cette valeur est maintenue pour la durée de cette transaction (jusqu'à ce que la tendance s'inverse).

En pratique, certains chartistes ajustent manuellement l'AF pour modifier la sensibilité de l'indicateur. Un AF supérieur à 0,2 entraîne une sensibilité accrue (plus de signaux de retournement). Un AF inférieur à 0,2 fait l'inverse. Pourtant, Wilder a déclaré dans son livre que des augmentations de 0,02 donnaient les meilleurs résultats dans l'ensemble.

Bien que le calcul soit relativement simple à utiliser, certains traders ont demandé à Wilder comment calculer le premier SAR, considérant que l'équation nécessite les valeurs précédentes. Selon lui, le premier SAR peut être calculé sur la base du dernier EP avant un renversement de tendance du marché.

Wilder a recommandé aux traders de revenir en arrière dans leur graphique pour trouver un renversement clair, puis d'utiliser ce PE comme première valeur SAR. Les SAR suivants pourraient alors être calculés jusqu'à ce que les derniers prix du marché soient atteints. 

Par exemple, si le marché a une tendance à la hausse, un trader pourrait revenir en arrière de quelques jours ou semaines jusqu'à ce qu'il trouve une correction précédente. Ensuite, il trouve le plancher local (EP) de cette correction, qui peut alors être utilisé comme premier SAR pour la tendance haussière suivante.

## Conclusion

Bien qu'il date des années 1970, le SAR parabolique est encore largement utilisé aujourd'hui. Les investisseurs peuvent l'appliquer à de nombreuses alternatives d'investissement actuelles, notamment le Forex, les matières premières, les actions et les marchés de crypto-monnaies. 

Mais aucun outil d'analyse de marché ne peut garantir une précision à 100 %. Ainsi, avant d'utiliser le SAR parabolique ou toute autre stratégie, les investisseurs doivent s'assurer qu'ils ont une bonne compréhension des marchés financiers et de l'analyse technique. Ils devraient également avoir des stratégies de trading et de gestion des risques appropriées pour atténuer les risques inévitables.