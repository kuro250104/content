Le langage CSS permet d’utiliser des polices qui ne sont pas installées sur l’ordinateur de l’utilisateur. 

Pour ce faire, il faut télécharger une police sur internet et mettre le fichier police sur le serveur. Ensuite, il faut utiliser la règle ```@font-face``` pour pouvoir utiliser cette police.

## Différents formats de polices

Il existe différents formats de polices. Ces différents formats existent pour des raisons de compression et/ou de compatibilité sur les différents OS. 

### Format TrueTypeFont (TTF)

TrueType est un format standard créé à la fin des années 1980 par Apple et Microsoft. Ce format est le standard pour les systèmes d’exploitations macOS et Windows. 

### Format OpenTypeFont (OTF)

C’est un format de police évolutif. Ce format a été créé à partir du format TrueType et est une marque déposée par Microsoft. Ce format de police est le plus utilisé de nos jours sur tous les ordinateurs. 

### Format Web Open Font Format (WOFF)

Le WOFF est un format de police utilisé pour les pages web. Ce format a été développé en 2009 et a reçu la Recommandation W3C. Le format WOFF est principalement composé des format TTF ou OTF avec de la compression et des métadonnées additionnelles. Le but de ce format est de permettre la distribution d’une police du serveur jusqu’au client, sur un réseau avec de fortes contraintes en bande-passante. 

### Format Embedded OpenType Fonts (EOT)

Les polices au format EOT sont une forme compactée du format OTF, créé par Microsoft dont le but était de créer un format embarqué de police afin de pouvoir l’utiliser sur les pages web. 

## Utiliser la police trouvée sur le web

Pour pouvoir utiliser une police externe, téléchargée depuis le web, il faut d’abord la déclarer en utilisant la règle ```@font-face```. Un nom est donné à cette police en utilisant la propriété CSS ```font-family```, puis le fichier format (OET, WOFF, etc.) est pointé en utilisant la propriété ```src```.

Exemple :

```css
@font-face {
	font-family: "PolicePersonnelle";
	src: (PolicePersonnelle.woff);
}

p {
	font-family: "PolicePersonnelle"; /* Une fois déclarée dans @font-face, la police est utilisée dans le document, comme une police normale */
}
```