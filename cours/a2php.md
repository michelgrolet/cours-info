# PHP

[Retour à l'accueil](./../README.md)

Collections, patrons de conception.

<details>
<summary> Plan ✨</summary>
- [CPOA](#cpoa)
</details>

# Introduction

Balises php :
```php
<?php 
	echo 'hello'; // affiche hello
?> // balise de fin optionnelle si que du php dans le fichier
```

Php est faiblement typé. On récupère le type avec `gettype($var)`. On récupère des informations sur une variable avec `var_dump($var)`.

## Affichage
- Affichage avec `echo` ou `print`. on peut utiliser des simple ou double quotes
  - `echo()` peut prendre plusieurs paramètres séparés par des virgules. Plus rapide que print.
  - `print()` retourne 1.
  - `printf($objet)` affiche le `toString()` de `$objet`.
  - `print_r($array)` affiche le contenu d'un `array()`.
- Variables : commencent par `$`
- Les variables sont interprétées dans les doubles quotes

## Tableaux
```php
$array = array($val1, "val2", 3);
$assocArray = array("key1" => $val1);
$assocArray["key2"] = $val2;
```

On boucle sur un tableau avec `foreach()`:

```php
foreach($array as $val) { // ou as $key => val 
	echo $val
}
```

### Fonctions sur les tableaux
-  `count($array)` retourne le nombre d'éléments dans le tableau.
- `array_key_exists($key, $array)` retourne true si la clé existe dans le tableau.

### Tableaux superglobaux
- `$_GET` : tableau associatif des paramètres dans l'url.
- `$_POST` : tableau associatif des paramètres dans le formulaire.
-  `$_SERVER` : tableau associatif des informations sur le serveur.

## Classes
```php
class X {
	protected string $param;

	public function __construct(string $param) {
		$this->param=$param;
	}

	public function nomMethode(): void {
		return ...
	}
}
$p = new Personne('param', x, ...);
$p->nomMethode();
```
✍️ Les paramètres de type objet sont passés par référence (quand on les modifie l'objet est modifié hors de la fonction).  
Les paramètres de type simple et les arrays sont passés par valeur. On peut faire un passage par référence en utilisant `int & $param`.

✍️ On peut mettre une valeur par défaut à un paramètre. Le paramètre est alors optionnel dans la signature de la fonction.

> ⚠️Un fichier contient des classes/fonctions ou des opérations, jamais les deux.

## Typage
- Le typage n'est pas obligatoire mais recommandé.
- Le $this-> est **obligatoire**. 
- `declare(strict_types=1)` active le mode strict qui oblige à mettre les bons types des variables, paramètres et retours. Sinon php transtype automatiquement.

- `A === B` vrai si `A == B` et si `gettype(A) == gettype(B)`.
- `A <> B` équivaut à `A != B`.

## Conditions
- `elseif()`.
- switch, for, while : pareil que java.

## Inclusions de code
- `require()` inclus le fichier php.
- `require_once()` : une seule fois par fichier.

✍️ Les parenthèses sont optionnelles pour require, require_once, echo et print.

## Affectation de code
```php
$a = $b
```
Duplique les types simples et les tableaux. Copie la valeur mais la référence est différente.  
Pour des objets, cette opération copie aussi la référence.

```php
$a = &$b
```
ici, `$a` et `$b` référencent la même adresse mémoire.

## Variables dynamiques
La valeur d'une variable peut être utilisée comme nom de variable.
```php
$v2='test';
$var='v2';
echo ${$var} //affiche test
```

Cela marche aussi pour les noms d'attributs, de méthodes et de fonctions.

La dynamicité permet de créer des getter et setter génériques. On utilise alors `property_exists($objet, $propriete)` qui retourne vrai si `$propriete` (nom de methode ou d'attribut) existe.
```php
public function __get(string $attr):mixed {
	if (property_exists($this, $attr)) return $this->$attr;
	if ($attr == /*valeur*/) return /*attribut ou appel a methode*/ 
	throw new Exception("$attr : invalid expression");
}
```
Cette méthode permet l'accès automatique aux attributs d'un objet : `$attr = $obj->$attr` fonctionne même si l'attribut est privé.

## Interfaces
Elles fonctionnent comme en Java.

## Héritage
Pareil que Java. Seule différence, pour utiliser les méthodes de la classe parente : 
```java
parent::__construct();
```

## Exceptions
On peut créer des classes d'exceptions :
```php
class Exc extends Exception {}
try {
	throw new Exc("");
} catch (Exc $e) {
	echo $e->getMessage();
}
```

## Namespaces
Pour se repérer dans les classes d'un projet, on utilise les namespaces.
```php
// on définit le namespace dans lequel on se trouve :
namespace \personne\Enseignant;
class Enseignant {}
// dans un fichier php, on pourra utiliser :
$prof = new \personne\Enseignant("Guenego");
```

✍️ Les classes créées en dehors d'un namespace sont accessibles depuis le namespace `\`. 

### Alias de noms de classe : use
```php
use \personne\Enseignant as Ens;
use \personne\Enseignant; // as Enseignant est implicite
use \personne as p; // alias de namespace
```

✍️ Ne pas confondre les namespaces définis avec `\` des répertoires de fichiers définis avec `/`.

## Structures de fichiers
Une bonne pratique :
- src : classes non accessibles depuis une url (classes php, ...)
- public : fichiers accessibles, html et php


# Chargement automatique des classes

Si une classe n'est pas connue à son appel, l'interpréteur exécute des fonctions **autoloader** pour la charger. Ces fonctions peut être définie par le développeur.

## Programmation d'un autoloader

❗ Un autoloader ne doit pas bloquer l'exécution.

Ajout d'un autoloader avec :
```php
spl_autoload_register(function($nom_classe) {
/*
- calcule le chemin vers la classe
- ajoute ".php"
- remplace \ par le DIRECTORY_SEPARATOR de l'OS
*/
}); 
```

## Composer

On utilise [composer (gestionnaire de dépendances PHP)](https://getcomposer.org/) pour générer un autoloader automatiquement.

Composer se sert du fichier `composer.json` pour définir les dépendances.

pour l'autoload, on ajoute dans le fichier `composer.json` :
```json
"autoload": {
	"psr-4": {
		"namespace\\": "src/chemin/vers/namespace"
	}
}
```
L'autoloader est généré dans le répertoire `vendor`. On y accède avec :
```php
require_once "vendor/autoload.php";
```

## Cookies

On crée un cookie avec la fonction suivante :
```php
setcookie("nom", $valeur, time()+$duree, "/", "", false, true);
```
On peut passer des objets en valeur de cookie en utilisant les fonctions serialize et unserialize.

## Sessions

```php
session_start();
//utilisation du tableau superglobal $_SESSION
$_SESSION['nom'] = 'toto';
session_destroy();
```

## PDO

```php
$dsn = 'mysql:host=localhost;dbname=bdd';
$pdo = new PDO($dsn, 'uname', 'pwd', [
	PDO::ATTR_PERSISTENT => true,
	PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
	PDO::ATTR_EMULATE_PREPARES => false,
	PDO::ATTR_STRINGIFY_FETCHES => false,
]);

// statement
$s = $pdo->prepare('SELECT ... WHERE x=? and y=?');
$s->execute([$x, $y]);
while ($row = $s->fetch(PDO::FETCH_ASSOC)) {
	// traitement de la ligne
}
```

### ConnectionFactory
```php
// contient une méthode :
public static function setConfig(String $fichier) : void {
	self::$config = parse_ini_file($fichier);
}
```
On exécute ensuite `ConnectionFactory::setConfig('db.config.ini')` pour charger la configuration.

## ORM (Object-Relational Mapping) Eloquent de Laravel

### Configuration

D'abord installer [laravel (framework PHP)](https://laravel.com/)
```bash
composer require illuminate/database
```

```php
use \Illuminate\Database\Capsule\Manager as DB;
$db = new DB();
$db->addConnection(parse_ini_file('db.config.ini'));
```

### Select

```php
class Ville extends \Illuminate\Database\Eloquent\Model {
	protected $table = 'table';
	protected $primaryKey = 'id';
	public $timestamps = false;

	public function pays() {
		return $this->belongsTo('Pays', 'id_pays');
	}
}

$villes = Ville::select('*')
	->where('id', $id);
	->skip($offset)
	->take($limit)
	->get(); // ou first()
echo $villes->toJson();

// Association avec clé étrangère :
$pays = Ville::select('*')
	->get();
$pays->belongsTo('Pays', 'id_pays');

```

### Insert, update, delete

```php
$v = new Ville();
$v->nom = 'Paris';
$v->save();

$v->nom = 'Lyon';
$v->save();

$v->delete();
```

### Associations

