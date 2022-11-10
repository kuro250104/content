Le JavaScript pur est compatible avec l'Unicode, mais il ne l'est pas pour les données binaires. Lorsque l'on traite des flux TCP ou le système de fichiers, il est nécessaire de manipuler des flux d'octets. Node fournit la classe Buffer (Tampon) qui fournit des instances pour stocker des données brutes similaires à un tableau d'entiers mais qui correspond à une allocation de mémoire brute en dehors du tas V8.

La classe Buffer est une classe globale à laquelle on peut accéder dans une application sans importer le module buffer.

## Création de tampons

Le Node Buffer peut être construit de différentes manières.

### Méthode 1

La syntaxe suivante permet de créer un tampon non initié de 10 octets :

```js
var buf = new Buffer(10);
```

### Méthode 2

La syntaxe suivante permet de créer un tampon à partir d'un tableau donné :

```js
var buf = new Buffer([10, 20, 30, 40, 50]);
```

### Méthode 3

La syntaxe suivante permet de créer un tampon à partir d'une chaîne de caractères et d'un type d'encodage optionnel : 

```js
var buf = new Buffer("Simply Easy Learning", "utf-8");
```

Bien que "utf8" soit le codage par défaut, vous pouvez utiliser l'un des codages suivants : "ascii", "utf8", "utf16le", "ucs2", "base64" ou "hex".

## Écriture dans les tampons

Syntaxe

Voici la syntaxe de la méthode permettant d'écrire dans un Node Buffer :

```js
buf.write(string[, offset][, length][, encoding])
```

### Paramètres

Voici la description des paramètres utilisés :

- **string** - Il s'agit des données de la chaîne à écrire dans le tampon.
- **offset** - Il s'agit de l'index du tampon à partir duquel l'écriture doit commencer. La valeur par défaut est 0.
- **length** - Il s'agit du nombre d'octets à écrire. La valeur par défaut est buffer.length.
- **encoding** - Encodage à utiliser. utf8' est l'encodage par défaut.

### Valeur de retour

Cette méthode renvoie le nombre d'octets écrits. S'il n'y a pas assez d'espace dans le tampon pour contenir la chaîne entière, une partie de la chaîne sera écrite.

### Exemple

```js
buf = new Buffer(256);
len = buf.write("Simply Easy Learning");

console.log("Octets written : "+  len);
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant :

```bash
Octets written : 20
```

## Lecture de tampons

### Syntaxe

Voici la syntaxe de la méthode permettant de lire les données d'un Node Buffer :

```js
buf.toString([encoding][, start][, end])
```

### Paramètres

Voici la description des paramètres utilisés :

- **encoding** - Encodage à utiliser. 'utf8' est l'encodage par défaut.
- **start** - Index de début pour commencer la lecture, la valeur par défaut est 0.
- **end** - Index de fin pour terminer la lecture, la valeur par défaut est le tampon complet.

### Valeur de retour

Cette méthode décode et renvoie une chaîne de caractères à partir des données de la mémoire tampon codées à l'aide du jeu de caractères spécifié.

### Exemple

```js
buf = new Buffer(26);
for (var i = 0 ; i < 26 ; i++) {
    buf[i] = i + 97;
}

console.log( buf.toString('ascii'));       // outputs: abcdefghijklmnopqrstuvwxyz
console.log( buf.toString('ascii',0,5));   // outputs: abcde
console.log( buf.toString('utf8',0,5));    // outputs: abcde
console.log( buf.toString(undefined,0,5)); // encoding defaults to 'utf8', outputs abcde
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant :

```bash
abcdefghijklmnopqrstuvwxyz
abcde
abcde
abcde
```

## Convertir le tampon en JSON

### Syntaxe

Voici la syntaxe de la méthode permettant de convertir un Node Buffer en objet JSON :

```js
buf.toJSON()
```

### Valeur de retour

Cette méthode renvoie une représentation JSON de l'instance de Buffer.

### Exemple

```js
var buf = new Buffer('Simply Easy Learning');
var json = buf.toJSON(buf);

console.log(json);
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant :

```json
{
    type: 'Buffer',
    data: 
    [ 
        83,
        105,
        109,
        112,
        108,
        121,
        32,
        69,
        97,
        115,
        121,
        32,
        76,
        101,
        97,
        114,
        110,
        105,
        110,
        103 
    ]
}
```

## Concaténation de tampons

### Syntaxe

Voici la syntaxe de la méthode permettant de concaténer les tampons de nœuds en un seul tampon de nœud :

```js
Buffer.concat(list[, totalLength])
```

### Paramètres

Voici la description des paramètres utilisés :

- **list** - Tableau Liste des objets Buffer à concaténer.
- **totalLength** - Il s'agit de la longueur totale des tampons une fois concaténés.

### Valeur de retour

Cette méthode renvoie une instance de Buffer.

### Exemple

```js
var buffer1 = new Buffer(Microlead ');
var buffer2 = new Buffer('Le Chemin Du Succès);
var buffer3 = Buffer.concat([buffer1,buffer2]);

console.log("buffer3 content: " + buffer3.toString());
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant :

```bash
buffer3 content: Microlead Le Chemin Du Succès
```

## Comparer les tampons

### Syntaxe

Voici la syntaxe de la méthode permettant de comparer deux tampons de nœuds :

```js
buf.compare(otherBuffer);
```

### Paramètres

Voici la description des paramètres utilisés :

**otherBuffer** - Il s'agit de l'autre tampon qui sera comparé avec **buf**

### Valeur de retour

Renvoie un nombre indiquant s'il vient avant ou après ou s'il est identique à **otherBuffer** dans l'ordre de tri.

### Valeur de retour

Renvoie un nombre indiquant s'il vient avant ou après ou s'il est identique à l'autreBuffer dans l'ordre de tri.

### Exemple

```js
var buffer1 = new Buffer('ABC');
var buffer2 = new Buffer('ABCD');
var result = buffer1.compare(buffer2);

if(result < 0) {
    console.log(buffer1 +" comes before " + buffer2);
} else if(result === 0) {
    console.log(buffer1 +" is same as " + buffer2);
} else {
    console.log(buffer1 +" comes after " + buffer2);
}
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant :

```bash
ABC comes before ABCD
```

## Tampon des tranches

### Syntaxe

Voici la syntaxe de la méthode permettant d'obtenir un sous-buffer d'un buffer de nœud :

```js
buf.slice([start][, end])
```

### Paramètres

Voici la description des paramètres utilisés :

- **start** - Nombre, Facultatif, Défaut : 0
- **end** - Nombre, Facultatif, Défaut : buffer.length

### Valeur de retour

Renvoie un nouveau tampon qui fait référence à la même mémoire que l'ancien, mais décalé et rogné par les indices de début (par défaut à 0) et de fin (par défaut à buffer.length). Les indices négatifs commencent à la fin du tampon.

### Exemple

```js
var buffer1 = new Buffer('MicroleadPathToSuccess');

//slicing a buffer
var buffer2 = buffer1.slice(0,9);
console.log("buffer2 content: " + buffer2.toString());
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant :

```bash
buffer2 content: Microlead
```

## Longueur de la mémoire tampon

### Syntaxe

Voici la syntaxe de la méthode permettant d'obtenir la taille d'une mémoire tampon de nœud en octets :

```js
buf.length;
```

### Valeur de retour

Renvoie la taille d'un tampon en octets.

### Exemple

```js
var buffer = new Buffer('MicroleadPathToSuccess');

//length of the buffer
console.log("buffer length: " + buffer.length);
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant :

```bash
buffer length: 22
```

## Méthodes Référence

Voici une référence du module Buffers disponible dans Node.js. Pour plus de détails, vous pouvez vous référer à la documentation officielle.

## Méthodes de classe

**Méthode et description :**

- ```Buffer.isEncoding(encoding)``` : Renvoie true si l'encodage est un argument d'encodage valide, false sinon.
- ```Buffer.isBuffer(obj)``` : Teste si obj est un Buffer.
- ```Buffer.byteLength(string[, encoding])``` : Donne la longueur réelle en octets d'une chaîne de caractères. L'encodage par défaut est 'utf8'. Ce n'est pas la même chose que String.prototype.length, puisque String.prototype.length renvoie le nombre de caractères dans une chaîne.
- ```Buffer.concat(list[, totalLength])``` : Renvoie un tampon qui est le résultat de la concaténation de tous les tampons de la liste.
- ```Buffer.compare(buf1, buf2)``` : Identique à buf1.compare(buf2). Utile pour trier un tableau de tampons.