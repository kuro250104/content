Nous utilisons l’éditeur en ligne **Remix IDE** pour compiler et exécuter notre base de code Solidity. Nous vous recommandons d’utiliser le même pour le bon déroulement du suivi de l’ensemble des cours sur Solidity.

**Étape 1** - Copiez le code donné dans la section Code de Remix IDE.

```solidity
pragma solidity ^0.5.0;
contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1;
        uint b = 2;
        uint result = a + b;
        return result;
    }
}
```

**Étape 2** - Sous l'onglet Compile, cliquez sur le bouton **Start to Compile**.

**Étape 3** - Sous l'onglet Run, cliquez sur le bouton **Deploy**.

**Étape 4** - Sous l'onglet Run, sélectionnez **SolidityTest at 0x**... dans la liste déroulante.

**Étape 5** - Cliquez sur le bouton **getResult** pour afficher le résultat.

Sortie :

```solidity
0: uint256: 3
```