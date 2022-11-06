Le modèle de retrait garantit que l'appel de transfert direct n'est pas effectué, ce qui constitue une menace pour la sécurité. Le contrat suivant montre l'utilisation non sécurisée de l'appel de transfert pour envoyer de l'éther.

```solidity
pragma solidity ^0.5.0;

contract Test {
    address payable public richest;
    uint public mostSent;

    constructor() public payable {
        richest = msg.sender;
        mostSent = msg.value;
    }
    function becomeRichest() public payable returns (bool) {
        if (msg.value > mostSent) {
            // Insecure practice
            richest.transfer(msg.value);
            richest = msg.sender;
            mostSent = msg.value;
            return true;
        } else {
            return false;
        }
    }
}
```

Le contrat ci-dessus peut être rendu inutilisable en faisant en sorte que le plus riche soit un contrat dont la fonction de repli échoue. Lorsque la fonction de repli échoue, la fonction ```becomeRichest()``` échoue également et le contrat reste bloqué pour toujours. Pour atténuer ce problème, nous pouvons utiliser le Withdrawal Pattern.

Dans le schéma de retrait, nous réinitialisons le montant en attente avant chaque transfert. Cela garantira que seul le contrat de l'appelant échoue.

```solidity
pragma solidity ^0.5.0;

contract Test {
    address public richest;
    uint public mostSent;

    mapping (address => uint) pendingWithdrawals;

    constructor() public payable {
        richest = msg.sender;
        mostSent = msg.value;
    }
    function becomeRichest() public payable returns (bool) {
        if (msg.value > mostSent) {
            pendingWithdrawals[richest] += msg.value;
            richest = msg.sender;
            mostSent = msg.value;
            return true;
        } else {
            return false;
        }
    }
    function withdraw() public {
        uint amount = pendingWithdrawals[msg.sender];
        pendingWithdrawals[msg.sender] = 0;
        msg.sender.transfer(amount);
    }
}
```