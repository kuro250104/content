Un tableau (*Array*) est une structure de données qui stocke une collection séquentielle de taille fixe d'éléments du même type. Un tableau est utilisé pour stocker une collection de données, mais il est souvent plus utile de considérer un tableau comme une collection de variables du même type.

Au lieu de déclarer des variables individuelles, telles que nombre0, nombre1, ..., et nombre99, vous déclarez une variable de tableau telle que nombres et utilisez ```nombres[0], nombres[1], etc ..., nombres[99]``` pour représenter les variables individuelles. On accède à un élément spécifique d'un tableau par un index.

Dans Solidity, un tableau peut avoir une taille fixe au moment de la compilation ou une taille dynamique. Pour un tableau de mémoire, il peut également avoir différents types d'éléments. Dans le cas d'un tableau de mémoire, le type d'élément ne peut pas être un mapping et s'il doit être utilisé comme paramètre de fonction, le type d'élément doit être un type ABI.

Tous les tableaux sont constitués d'emplacements mémoire contigus. L'adresse la plus basse correspond au premier élément et l'adresse la plus haute au dernier élément.

## Déclaration des tableaux

Pour déclarer un tableau de taille fixe dans Solidity, le programmeur spécifie le type des éléments et le nombre d'éléments requis par un tableau, comme suit :

```solidity
type arrayName [ arraySize ];
```

On appelle cela un tableau unidimensionnel. Le **arraySize** doit être une constante entière supérieure à zéro et le type peut être n'importe quel type de données Solidity valide. Par exemple, pour déclarer un tableau de 10 éléments appelé balance de type uint, utilisez l'instruction :

```solidity
uint balance[10];
```

Pour déclarer un tableau de taille dynamique dans Solidity, le programmeur spécifie le type des éléments de la manière suivante :

```solidity
type[] arrayName;
```

## Initialisation des tableaux

Vous pouvez initialiser les éléments d'un tableau Solidity un par un ou à l'aide d'une seule instruction, comme suit :

```solidity
uint balance[3] = [1, 2, 3];
```

Le nombre de valeurs entre accolades ```[ ]``` ne peut pas être supérieur au nombre d'éléments que nous déclarons pour le tableau entre crochets ```[ ]```. L'exemple suivant permet d'assigner un seul élément du tableau - ```[1]```.

Si vous omettez la taille du tableau, un tableau juste assez grand pour contenir l'initialisation est créé. Par conséquent, si vous écrivez :

```solidity
uint balance[] = [1, 2, 3];
```

Vous créerez exactement le même tableau que dans l'exemple précédent.

```solidity
balance[2] = 5;
```

L'instruction ci-dessus attribue à l'élément numéro 3 du tableau une valeur de 5.

## Création de tableaux de mémoire dynamique

Les tableaux de mémoire dynamique sont créés à l'aide du mot-clé **new**.

```solidity
uint size = 3;
uint balance[] = new uint[](size);
```

## Accès aux éléments d'un tableau

On accède à un élément en indexant le nom du tableau. Pour ce faire, on place l'indice de l'élément entre crochets après le nom du tableau. Par exemple :

```solidity
uint salary = balance[2];
```

L'instruction ci-dessus prend le troisième élément du tableau et affecte la valeur à la variable salaire. L'exemple suivant utilise les trois concepts susmentionnés, à savoir la déclaration, l'affectation et l'accès aux tableaux.

## Attributs

- ```length``` - length renvoie la taille du tableau. length peut être utilisé pour changer la taille du tableau dynamique en la fixant.
- ```push``` - push permet d'ajouter un élément à un tableau de stockage dynamique à la fin. Il renvoie la nouvelle longueur du tableau.

Essayez le code suivant pour comprendre comment les tableaux fonctionnent dans Solidity :

```solidity
pragma solidity ^0.5.0;

contract test {
    function testArray() public pure{
        uint len = 7; 
        
        //dynamic array
        uint[] memory a = new uint[](7);
        
        //bytes is same as byte[]
        bytes memory b = new bytes(len);
        
        assert(a.length == 7);
        assert(b.length == len);
        
        //access array variable
        a[6] = 8;
        
        //test array variable
        assert(a[6] == 8);
        
        //static array
        uint[3] memory c = [uint(1) , 2, 3];
        assert(c.length == 3);
    }
}
```