Ce PSR décrit une spécification pour l'auto-chargement de classes à partir de chemins de fichiers. Il est entièrement interopérable et peut être utilisé en complément de toute autre spécification d'auto-chargement, y compris le PSR-0. Ce PSR décrit également où placer les fichiers qui seront autochargés conformément à la spécification.

## Caractéristiques

1. Le terme "classe" fait référence aux classes, interfaces, traits et autres structures similaires.
2. Un nom de classe doit avoir la forme suivante : ```\<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>```
    1. Le nom de classe DOIT avoir un dossier (namespace) de premier niveau, aussi appelé "vendor namespace".
    2. Le nom de classe PEUT avoir un ou plusieurs sous-dossiers (subnamespace).
    3. Le nom de classe DOIT avoir un dossier de classe terminale.
    4. Les traits de soulignement n'ont aucune signification particulière dans aucune partie du nom de classe.
    5. Les caractères alphabétiques dans le nom de classe PEUVENT être une combinaison de minuscules et de majuscules.
    6. Tous les noms de classe DOIVENT être référencés en tenant compte de la sensibilité de la casse.
3. Lors du chargement d'un fichier qui correspond à un nom de classe...
    1. Une série consécutive d'un ou plusieurs dossiers et de sous-dossier, sans inclure le séparateur de dossier,  dans le nom de classe correspond à, au moins, un "répertoire de base".
    2. Les noms des sous-dossiers consécutifs après un préfixe de dossier correspondent à un sous-répertoire dans un "répertoire de base", dans lequel les séparateurs de nom représentent des séparateurs de répertoire. Le nom du sous-répertoire DOIT correspondre à la casse des noms des sous-dossiers.
    3. Le nom de la classe terminale correspond à un nom de fichier se terminant par .php. Le nom du fichier DOIT correspondre à la casse du nom de la classe terminale.
4. Les implémentations d'auto-chargeurs NE DOIVENT PAS lancer d'exceptions, NE DOIVENT PAS soulever d'erreurs de quelque niveau que ce soit, et NE DOIVENT PAS renvoyer de valeur.

## Exemples

Le tableau ci-dessous indique le chemin de fichier correspondant pour un nom de classe, un préfixe d'un dossier et un répertoire de base donnés.

| **Nom de la classe** | **Préfixe du dossier** | **Répertoire de base** | **Résultat du chemin** |
| --- | --- | --- | --- |
| ```\Acme\Log\Writer\File_Writer``` | ```Acme\Log\Writer``` | ```./acme-log-writer/lib/``` | ```./acme-log-writer/lib/File_Writer.php``` |
| ```\Aura\Web\Response\Status``` | ```Aura\Web``` | ```/path/to/aura-web/src/``` | ```/path/to/aura-web/src/Response/Status.php``` |
| ```\Symfony\Core\Request``` | ```Symfony\Core``` | ```./vendor/Symfony/Core/``` | ```./vendor/Symfony/Core/Request.php``` |
| ```\Zend\Acl``` | ```Zend``` | ```/usr/includes/Zend/``` | ```/usr/includes/Zend/Acl.php``` |