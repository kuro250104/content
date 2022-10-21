Le BOM intègre un objet nommé ```navigator```. Celui-ci nous permet d'accéder à différentes informations relatives au navigateur et aux préférences connues de l’utilisateur.

## Attributs

L’objet Navigator nous donne accès à plusieurs attributs avec les caractéristiques du navigateur de l’utilisateur, ainsi que quelques méthodes utiles, parmis lesquels :

- L’attribut ```appCodeName``` retourne le nom de code du navigateur.
- L’attribut ```appName``` retourne le nom du navigateur.
- L’attribut ```appVersion``` retourne la version du navigateur.
- L’attribut ```cookieEnabled``` détermine si les cookies sont autorisés ou non en retournant true ou false.
- L’attribut ```geolocation``` retourne un objet Geolocation qui peut être utilisé pour définir la localisation de l’utilisateur.
- L’attribut ```language``` retourne la langue définie dans le navigateur.
- L’attribut ```onLine``` permet de détecter si le navigateur est en ligne ou non, c’est-à-dire s’il est connecté à internet.
- L’attribut ```plateform``` retourne la plateforme utilisée par le navigateur.
- L’attribut ```userAgent``` retourne l'user-agent envoyé en en-tête de requête par le navigateur
- La méthode ```javaEnable```()” renvoie un booléen (Vrai ou Faux) en fonction de si le javascript est activé ou non sur le navigateur de l’utilisateur

## Exemples

```js
// Affiche le nom de code du navigateur
console.log( appCodeName )

// Affiche le nom du navigateur
console.log( appName )

// Affiche la version du navigateur
console.log( appVersion )

// Affiche “Vrai” si les cookies sont activés, sinon “Faux”.
console.log( cookieEnabled )

// Affiche un objet “Geolocation” qui peut permettre
// de localiser un utilisateur
console.log( geolocation )

// Affiche la langue du navigateur
console.log( language )

// Affiche “Vrai” si le navigateur est connecté à
// internet, sinon “Faux”
console.log( onLine )

// Affiche la plateforme utilisée par l’utilisateur
console.log( plateform )

// Affiche le user-agent envoyé par le navigateur
// en en-tête de requête
console.log( userAgent )

// Affiche “Vrai” si le javascript est activé sur
// le navigateur, sinon “Faux”.
console.log( javaEnabled() )
```