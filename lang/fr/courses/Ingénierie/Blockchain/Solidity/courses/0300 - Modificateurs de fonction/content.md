Les modificateurs de fonction sont utilisés pour modifier le comportement d'une fonction. Par exemple pour ajouter une condition préalable à une fonction.

D'abord nous créons un modificateur avec ou sans paramètre.

```solidity
contract Owner {
    modifier onlyOwner {
        require(msg.sender == owner);
        _;
    }
    modifier costs(uint price) {
        if (msg.value >= price) {
            _;
        }
    }
}
```

Le corps de la fonction est inséré là où le symbole spécial "_ ;" apparaît dans la définition d'un modificateur. Ainsi, si la condition du modificateur est satisfaite lors de l'appel de cette fonction, la fonction est exécutée, sinon, une exception est levée.

Voir l'exemple ci-dessous :

```solidity
pragma solidity ^0.5.0;

contract Owner {
    address owner;
    constructor() public {
        owner = msg.sender;
    }
    modifier onlyOwner {
        require(msg.sender == owner);
        _;
    }
    modifier costs(uint price) {
        if (msg.value >= price) {
            _;
        }
    }
}
contract Register is Owner {
    mapping (address => bool) registeredAddresses;
    uint price;
    constructor(uint initialPrice) public { price = initialPrice; }
    
    function register() public payable costs(price) {
        registeredAddresses[msg.sender] = true;
    }
    function changePrice(uint _price) public onlyOwner {
        price = _price;
    }
}
```