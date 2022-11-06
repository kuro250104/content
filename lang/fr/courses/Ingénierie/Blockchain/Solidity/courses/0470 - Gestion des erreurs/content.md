Solidity fournit diverses fonctions pour la gestion des erreurs. En général, lorsqu'une erreur se produit, l'état est rétabli à son état initial. D'autres contrôles visent à empêcher l'accès au code non autorisé. Voici quelques-unes des principales méthodes utilisées pour la gestion des erreurs :

- ```assert(bool condition)``` - Dans le cas où la condition n'est pas remplie, cet appel de méthode provoque un opcode invalide et toutes les modifications apportées à l'état sont annulées. Cette méthode doit être utilisée pour les erreurs internes.
- ```require(bool condition)``` - Si la condition n'est pas remplie, l'appel de cette méthode ramène l'état original. - Cette méthode doit être utilisée pour les erreurs dans les entrées ou les composants externes.
- ```require(bool condition, string memory message)``` - Si la condition n'est pas remplie, l'appel de cette méthode revient à l'état initial. - Cette méthode doit être utilisée pour les erreurs dans les entrées ou les composants externes. Elle offre la possibilité de fournir un message personnalisé.
- ```revert()``` - Cette méthode interrompt l'exécution et rétablit toutes les modifications apportées à l'état.
- ```revert(string memory reason)``` - Cette méthode interrompt l'exécution et annule tout changement apporté à l'état. Elle offre la possibilité de fournir un message personnalisé.

## Exemple

Essayez le code suivant pour comprendre comment la gestion des erreurs fonctionne dans Solidity :

```solidity
pragma solidity ^0.5.0;

contract Vendor {
    address public seller;
    modifier onlySeller() {
        require(
            msg.sender == seller,
            "Only seller can call this."
        );
        _;
    }
    function sell(uint amount) public payable onlySeller { 
        if (amount > msg.value / 2 ether)
            revert("Not enough Ether provided.");
        // Perform the sell operation.
    }
}
```

Lorsque revert est appelé, il renvoie les données hexadécimales comme suit :

## Rendu

```solidity
0x08c379a0                     // Function selector for Error(string)
0x0000000000000000000000000000000000000000000000000000000000000020 // Data offset
0x000000000000000000000000000000000000000000000000000000000000001a // String length
0x4e6f7420656e6f7567682045746865722070726f76696465642e000000000000 // String data
```