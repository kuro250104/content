Le **constructeur** est une fonction spéciale déclarée à l'aide du mot clé ```constructor```. Il s'agit d'une fonction facultative utilisée pour initialiser les variables d'état d'un contrat. Voici les principales caractéristiques d'un constructeur :

- Un contrat ne peut avoir qu'un seul constructeur.
- Un code constructeur est exécuté une fois lorsqu'un contrat est créé et il est utilisé pour initialiser l'état du contrat.
- Après l'exécution d'un code constructeur, le code final est déployé sur la blockchain. Ce code inclut les fonctions publiques et le code accessible par les fonctions publiques. Le code constructeur ou toute méthode interne utilisée uniquement par le constructeur ne sont pas inclus dans le code final.
- Un constructeur peut être soit public, soit interne.
- Un constructeur interne marque le contrat comme abstrait.
- Dans le cas où aucun constructeur n'est défini, un constructeur par défaut est présent dans le contrat.

```solidity
pragma solidity ^0.5.0;

contract Test {
    constructor() public {}
}
```

- Dans le cas où le contrat de base à un constructeur avec des arguments, chaque contrat dérivé doit les passer.
- Le constructeur de base peut être initialisé directement en utilisant la manière suivante :

```solidity
pragma solidity ^0.5.0;

contract Base {
    uint data;
    constructor(uint _data) public {
        data = _data;   
    }
}
contract Derived is Base (5) {
    constructor() public {}
}
```

- Le constructeur de base peut être initialisé indirectement en utilisant la manière suivante :

```solidity
pragma solidity ^0.5.0;

contract Base {
    uint data;
    constructor(uint _data) public {
        data = _data;   
    }
}
contract Derived is Base {
    constructor(uint _info) Base(_info * _info) public {}
}
```

- Les méthodes directes et indirectes d'initialisation du constructeur du contrat de base ne sont pas autorisées.
- Si le contrat dérivé ne passe pas d'argument(s) au constructeur du contrat de base, le contrat dérivé deviendra abstrait.