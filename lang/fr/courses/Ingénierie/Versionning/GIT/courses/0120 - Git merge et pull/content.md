## Fusionner des branches

Imaginons qu’un dépôt contient 2 branches (test, master) et qui possèdent un commit en commun et qu’elles pointent chacune vers de nouveaux commits qui sont des modifications différentes d’un même dépôt. On souhaite fusionner la branche test avec la branche master, pour réaliser cela il faut se placer sur branche master avec la commande ```git checkout```. Puis taper la commande ```git merge``` suivis du nom de la branche qu’il faut fusionner.

exemple:

```git
git merge test
```

Dans ce cas, fusionner nous branches revient à placer la branche master au niveau du commit pointé par la branche test. 

Ensuite, il faut effacer la branche test, la commande ```git branch  -d``` suivie du nom de la branche, permet de réaliser cela. Enfin il faut utiliser la commande ```git pull``` pour mettre à jour le dépôt local avec les derniers commits présents sur le dépôt distant..

exemple:

```git
git pull
```