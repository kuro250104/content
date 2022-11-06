Les **enums** limitent une variable à l'une des quelques valeurs prédéfinies. Les valeurs de cette liste énumérée sont appelées **enums**.

Grâce à l'utilisation des **enums**, il est possible de réduire le nombre de bogues dans votre code.

Par exemple, si nous considérons une application pour un magasin de jus de fruits frais, il serait possible de limiter la taille du verre à petit, moyen et grand. Cela permettrait de s'assurer que personne ne puisse commander une taille autre que petite, moyenne ou grande.

## Exemple

Essayez le code suivant pour comprendre comment l'**enum** fonctionne dans Solidity.

```solidity
pragma solidity ^0.5.0;

contract test {
    enum FreshJuiceSize{ SMALL, MEDIUM, LARGE }
    FreshJuiceSize choice;
    FreshJuiceSize constant defaultChoice = FreshJuiceSize.MEDIUM;

    function setLarge() public {
        choice = FreshJuiceSize.LARGE;
    }
    function getChoice() public view returns (FreshJuiceSize) {
        return choice;
    }
    function getDefaultChoice() public pure returns (uint) {
        return uint(defaultChoice);
    }
}
```

Exécutez le programme ci-dessus pour tester le fonctionnement des **enums**.

Cliquez d'abord sur le bouton **setLarge** pour définir la valeur **LARGE** puis cliquez sur **getChoice** pour obtenir le choix sélectionné.

## Rendu

```solidity
uint8: 2
```

Cliquez sur le bouton **getDefaultChoice** pour obtenir le choix par défaut.

```solidity
uint256: 1
```