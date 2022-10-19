Ce document décrit une interface commune pour la journalisation des bibliothèques.

L'objectif principal est de permettre aux bibliothèques de recevoir un objet ```Psr\Log\LoggerInterface``` et d'y écrire des logs de manière simple et universelle.

Les frameworks et les CMS qui ont des besoins personnalisés **peuvent** étendre l'interface pour leur propre usage, mais **doivent** rester compatibles avec ce document. Cela garantit que les bibliothèques tierces qu'une application utilise peuvent écrire dans les journaux d'application centralisés.

## Caractéristiques

### Notion de base

- Le LoggerInterface propose huit méthodes pour écrire des rapports aux huit niveaux de la RFC 5424 (debug, info, notice, warning, error, critical, alert, emergency).
- Une neuvième méthode, le log, accepte un niveau de log comme premier argument. L'appel de cette méthode avec une des constantes de niveau log DOIT avoir le même résultat que l'appel de la méthode spécifique au niveau. L'appel de cette méthode avec un niveau non défini par cette spécification DOIT lancer un Psr\Log\InvalidArgumentException si l'implémentation ne connaît pas le niveau. Les utilisateurs NE DOIVENT PAS utiliser un niveau spécifique sans être sûrs que l'implémentation actuelle le supporte.

### Message

- Chaque méthode accepte une chaîne de caractères comme message ou un objet avec une méthode ```__toString()```. Les implémenteurs PEUVENT avoir un traitement spécial pour les objets passés. Si ce n'est pas le cas, les implémenteurs DOIVENT le transformer en une chaîne de caractères.
- Le message PEUT contenir des caractères de remplacement que les implémenteurs PEUVENT remplacer par des valeurs du tableau de contexte.

Les noms de remplacement DOIVENT correspondre aux clés dans le tableau de contexte.

Les noms de remplacement DOIVENT être délimités par une seule accolade ouvrante { et une seule accolade fermante }. Il NE DOIT PAS y avoir d'espace entre les délimiteurs et le nom de remplacement.

Les noms de remplacement DOIVENT être composés uniquement des caractères A-Z, a-z, 0-9, du trait de soulignement _ et des points… L'utilisation d'autres caractères est réservée aux modifications futures de la spécification des noms de remplacement.

Les implémenteurs PEUVENT utiliser les caractères de remplissage pour mettre en œuvre diverses stratégies et traduire les logs pour l'affichage. Les utilisateurs NE DEVRAIENT PAS pré-échapper les valeurs des caractères de remplacement, car ils ne peuvent pas savoir dans quel contexte les données seront affichées.

Voici un exemple de mise en œuvre de l'interpolation des caractères de remplacement, fourni à titre de référence uniquement :

``` php
<?php

/**
 * Interpole les valeurs de contexte dans les messages de     
 * remplacement.
 */
function interpolate($message, array $context = array())
{
    // construit un tableau de remplacement avec des crochets autour des clés de contexte
    $replace = array();
    foreach ($context as $key => $val) {
        // vérifie que la valeur peut être exprimée en chaîne de caractères
        if (!is_array($val) && (!is_object($val) || method_exists($val, '__toString'))) {
            $replace['{' . $key . '}'] = $val;
        }
    }

    // interpole les valeurs de remplacement dans le message et le retour
    return strtr($message, $replace);
}

// un message avec les noms de remplacement délimités par des accolades
$message = "Utilisateur {username} créé";

// un tableau contextuel de noms de remplacement => valeurs de remplacement
$context = array('username' => 'bolivar');

// écrit "Utilisateur bolivar créé"
echo interpolate($message, $context);
```

### Contexte

Chaque méthode accepte un tableau comme données de contexte. Celui-ci est destiné à contenir toute information étrangère qui ne s'inscrit mal dans une chaîne. Le tableau peut contenir n'importe quoi. Les implémenteurs DOIVENT s'assurer qu'ils traitent les données contextuelles avec autant d'indulgence que possible. Une valeur donnée dans le contexte NE DOIT PAS lancer d'exception ni provoquer d'erreur PHP ou encore d'avertissement.

Si un objet Exception est passé dans les données de contexte, il DOIT être dans la clé "exception". La journalisation des exceptions est un modèle courant et cela permet aux implémenteurs d'extraire une trace des exceptions lorsque le backend de journalisation le supporte. Les implémenteurs DOIVENT toujours vérifier que la clé "exception" est bien une Exception avant de l'utiliser en tant que telle, car elle PEUT contenir n'importe quoi.

### Classe d'assistants et interfaces

- La classe ```Psr\Log\AbstractLogger``` vous permet d'implémenter très facilement l'interface de journalisation en l'étendant et en implémentant la méthode de journalisation générique. Les huit autres méthodes lui transmettent le message et le contexte.
- De même, l'utilisation de la classe ```Psr\Log\LoggerTrait``` nécessite seulement l'implémentation de la méthode de journalisation générique. Notez que puisque les traits ne peuvent pas implémenter les interfaces, dans ce cas, vous devez constamment implémenter ```LoggerInterface```.
- Le ```Psr\Log\NNLogger``` est fourni avec l'interface. Il PEUT être utilisé par les utilisateurs de l'interface pour fournir une implémentation de repli "trou noir" si aucun logger ne leur est fourni. Cependant, la journalisation conditionnelle peut être une meilleure approche si la création de données contextuelles est coûteuse.
- La ```Psr\Log\LoggerAwareInterface``` ne contient qu'une méthode ```setLogger(LoggerInterface $logger)``` et peut être utilisée par les frameworks pour connecter automatiquement des instances arbitraires avec un logger.
- Le trait ```Psr\Log\LoggerAwareTrait``` peut être utilisé pour implémenter facilement l'interface équivalente dans n'importe quelle classe. Il vous donne accès à ```$this->logger```.
- La classe ```Psr\Log\LogLevel``` contient des constantes pour les huit niveaux de journalisation.

## Paquet

Les interfaces et les classes décrites ainsi que les classes d'exception correspondantes et une suite de tests pour vérifier votre implémentation sont fournies dans le cadre du paquet ```psr/log```.

## Psr\Log\LoggerInterface

``` php
<?php

namespace Psr\Log;

/**
 * Décrit une instance de logger.
 *
 * Le message DOIT être une chaîne ou un objet implémentant 
 * __toString().
 *
 * Le message PEUT contenir des espaces réservés dans le formulaire :    
 * {foo} où foo sera remplacé par les données de contexte dans la clé 
 * "foo".
 *
 * Le tableau de contexte peut contenir des données arbitraires, la
 * seule hypothèse qui peut être faite par les implémenteurs est que si 
 * une instance d'Exception est donnée pour produire une trace, elle 
 * DOIT être dans une clé nommée "exception".
 *
 * Voir 
https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logg
er-interface.md
 * pour la spécification complète de l'interface.
 */
interface LoggerInterface
{
    /**
     * Le système est inutilisable.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function emergency($message, array $context = array());

    /**
     * Des mesures doivent être prises immédiatement.
     *
     * Exemple : Tout le site web est hors service, la base de données 
     * est indisponible, etc. Cela devrait déclencher les alertes SMS et 
     * vous réveiller.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function alert($message, array $context = array());

    /**
     * Conditions critiques.
     *
     * Exemple : Composante de la demande indisponible, exception 
     * inattendue.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function critical($message, array $context = array());

    /**
     * Les erreurs d'exécution qui ne nécessite pas de mesures 
     * immédiates, mais qui devraient généralement être enregistrées et 
     * surveillées.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function error($message, array $context = array());

    /**
     * Des événements exceptionnels qui ne sont pas des erreurs.
     *
     * Exemple : Utilisation d'API dépréciées, mauvaise utilisation 
     * d'une API, choses indésirables qui ne sont pas nécessairement 
     * mauvaises.
     *
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function warning($message, array $context = array());

    /**
     * Des événements normaux, mais significatifs.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function notice($message, array $context = array());

    /**
     * Événements intéressants.
     *
     * Exemple : L'utilisateur se connecte, les journaux SQL.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function info($message, array $context = array());

    /**
     * Informations détaillées sur le débogage.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function debug($message, array $context = array());

    /**
     * Des journaux avec un niveau arbitraire.
     *
     * @param mixed $level
     * @param string $message
     * @param array $context
     * @return void
     */
    public function log($level, $message, array $context = array());
}
```

## Psr\Log\LoggerAwareInterface

``` php
<?php

namespace Psr\Log;

/**
 * Décrit une instance compatible avec le logger.
 */
interface LoggerAwareInterface
{
    /**
     * Définit une instance de logger sur l'objet.
     *
     * @param LoggerInterface $logger
     * @return void
     */
    public function setLogger(LoggerInterface $logger);
}
```

## Psr\Log\LogLevel

``` php
<?php

namespace Psr\Log;

/**
 * Décrit les niveaux de journalisation.
 */
class LogLevel
{
    const EMERGENCY = 'emergency';
    const ALERT     = 'alert';
    const CRITICAL  = 'critical';
    const ERROR     = 'error';
    const WARNING   = 'warning';
    const NOTICE    = 'notice';
    const INFO      = 'info';
    const DEBUG     = 'debug';
}
```