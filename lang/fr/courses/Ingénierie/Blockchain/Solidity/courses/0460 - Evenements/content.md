L'événement est un membre héritable d'un contrat. Un événement est émis, il stocke les arguments passés dans les journaux de transactions. Ces journaux sont stockés sur la blockchain et sont accessibles en utilisant l'adresse du contrat jusqu'à ce que le contrat soit présent sur la blockchain. Un événement généré n'est pas accessible depuis les contrats, pas même ceux qui l'ont créé et émis.

Un événement peut être déclaré en utilisant le mot clé **event**.

```solidity
//Declare an Event
event Deposit(address indexed _from, bytes32 indexed _id, uint _value);

//Emit an event
emit Deposit(msg.sender, _id, msg.value);
```

## Exemple

Essayez le code suivant pour comprendre comment fonctionne un événement dans Solidity. Tout d'abord, créez un contrat et émettez un événement :

```solidity
pragma solidity ^0.5.0;

contract Test {
    event Deposit(address indexed _from, bytes32 indexed _id, uint _value);
    function deposit(bytes32 _id) public payable {      
        emit Deposit(msg.sender, _id, msg.value);
    }
}
```

Accédez ensuite à l'événement du contrat dans le code JavaScript :

```solidity
var abi = /* abi as generated using compiler */;
var ClientReceipt = web3.eth.contract(abi);
var clientReceiptContract = ClientReceipt.at("0x1234...ab67" /* address */);

var event = clientReceiptContract.Deposit(function(error, result) {
    if (!error)console.log(result);
});
```

Il devrait imprimer des détails semblables à ceux qui suivent :

## Rendu

```solidity
{
    "returnValues": {
        "_from": "0x1111...FFFFCCCC",
        "_id": "0x50...sd5adb20",
        "_value": "0x420042"
    },
    "raw": {
        "data": "0x7f...91385",
        "topics": ["0xfd4...b4ead7", "0x7f...1a91385"]
    }
}
```