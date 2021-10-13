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
print 'hello'; // affiche print 'hello'; (hors des balises)
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
```
On boucle sur un tableau avec `foreach()`: 
```php
foreach($array as $var) {
	echo $var
}
```

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

✍️ Les parenthèses sont optionelles pour require, require_once, echo et print.

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
Pareil que Java. Seule différence pour utiliser les méthodes de la classe parente : 
```java
parent::__construct();
```

## 
On peut créer des classes d'exceptions
```php
class Exc extends Exception {}
try {
	throw new Exc("");
} catch (Exc $e) {
	echo $e->getMessage();
}
```