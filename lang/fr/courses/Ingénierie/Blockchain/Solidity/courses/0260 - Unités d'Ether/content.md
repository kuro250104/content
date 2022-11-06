Dans solidity, nous pouvons utiliser **wei**, **finney**, **szabo** ou **ether** comme suffixe à un littéral à utiliser pour convertir diverses dénominations basées sur l'éther. L'unité la plus basse est le **wei** et 1e12 représente 1 x 10^12.

```solidity
assert(1 wei == 1);
assert(1 szabo == 1e12);
assert(1 finney == 1e15);
assert(1 ether == 1e18);
assert(2 ether == 2000 fenny);
```

## Unités de temps

Tout comme la monnaie, Solidity possède des unités de temps où l'unité la plus basse est la seconde et nous pouvons utiliser les secondes, les minutes, les heures, les jours et les semaines comme suffixe pour désigner le temps.

```solidity
assert(1 seconds == 1);
assert(1 minutes == 60 seconds);
assert(1 hours == 60 minutes);
assert(1 day == 24 hours);
assert(1 week == 7 days);
```