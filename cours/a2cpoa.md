# CPOA

[Retour à l'accueil](./../README.md)

Collections, patrons de conception.

<details>
<summary> Plan ✨</summary>

- [CPOA](#cpoa)
- [Collections de java.util](#collections-de-javautil)
	- [List\<E\>](#liste)
		- [ArrayList\<E\>](#arrayliste)
		- [LinkedList\<E\> - listes doublement chaînées](#linkedliste---listes-doublement-chaînées)
	- [Set](#set)
		- [HashSet - valeur→clé](#hashset---valeurclé)
		- [TreeSet - nécessite Comparable](#treeset---nécessite-comparable)
	- [Itérateurs](#itérateurs)
	- [Map<K,V>](#mapkv)
		- [HashMap<K,V> - Implémente Cloneable](#hashmapkv---implémente-cloneable)
		- [SortedMap ◦ TreeMap<K,V>](#sortedmap--treemapkv)
	- [classe Collections](#classe-collections)
- [Patrons de conception](#patrons-de-conception)
	- [Patron stratégie](#patron-stratégie)
	- [Patron adapter](#patron-adapter)
	- [Patron itérateur](#patron-itérateur)
</details>

___
> ## Conventions de notation
> - noms de méthodes : **verbes**.
> - chaque fichier possède une **Javadoc** complète.
> - **commenter l'intérieur des méthodes** complexes.
> - **limiter le nombre de méthodes** par classe.
> - pas plus de **5 attributs** par classe.
> - pas plus de **30 lignes** par méthode.
> - pas plus de **4 boucles imbriquées**.
> - pas de **duplication de code**. Utiliser le [patron stratégie](#patron-stratégie).





___
# Collections de java.util

![Image : interfaces/classes implémentant Collection.](../assets/cpoa_collection.png)

> ❗ Les collections ne manipulent que des objets héritant de `Object`. Elles ne prennent pas les types de base java.  
> - Il faut utiliser les objets `Wrapper` (Integer, Boolean, Double, ...).  
> - Les types de base possèdent une méthode `typeValue()` qui retourne le Wrapper de l'objet.
> - Java passe automatiquement des wrappers aux types de base et inversement.

> **Généricité :** Permet à une classe d'accepter tous types d'objets. 
> ```java
> public class Generique<E>{}
> Generique<Integer> i;
> Generique j; //raw type ≈ Object
> ```

```java
interface Collection<E> {
	add(e);
	AddAll(Collection<E>);
	clear();
	contains(Object);
	containsAll(Collection<E>);
	hashCode();
	iterator();
	remove(Object);
	removeAll(Collection<E>); //enleve ce qui est en commun
	size();
	toArray();
}
```

## List\<E\>
Accès à partir de l'index.
```java
// Méthodes qui ne sont pas déjà dans Collection.
interface List<E> implements Collection<E> {
	add(i, E);
	addAll(i, Collection<E>);
	get(i);
	indexOf(Object);
	lastIndexOf(Object);
	listIterator([i]); //i : indice de départ
	remove(i);
	set(i, E); //remplace x par E en i.
	sort(Comparator);
	subList(from, to); //from inclus, to exclus.
}
```

### ArrayList\<E\>
```java
// Méthodes qui ne sont pas déjà dans List et Collection.
class ArrayList<E> implements List<E> {
	ArrayList(taille ou collectionInit);
	clone();
	forEach((x) -> /*action sur x*/);
}
```

### LinkedList\<E\> - listes doublement chaînées
```java
// Méthodes qui ne sont pas déjà dans List et Collection.
class LinkedList<E> implements List<E> {
	LinkedList([collectionInit]);
	addFirst(E);
	addLast(E);
	clone();
	descendingIterator();
	getFirst();
	getLast();
	removeLast();
	removeFirst();
}
```

## Set
Pas de doublons : permet de gérer des ensembles d'objets.

### HashSet - valeur→clé

```java
// Méthodes qui ne sont pas déjà dans Set et Collection.
class HashSet<E> implements Set<E> {
	HashSet();
	HashSet(Collection<E>);
	HashSet(taille, [loadFactor]);
}
```

### TreeSet - nécessite Comparable

```java
// Méthodes qui ne sont pas déjà dans Set et Collection.
class TreeSet<E> implements AbstractSet<E> {
	TreeSet();
	TreeSet(Collection<E>);
	TreeSet(Comparator<E>);
	TreeSet(SortedSet<E>);
	comparator();
	descendingIterator();
	descendingSet();
	first();
	last();
	ceiling(E); //element >=
	higher(E); //element >
	floor(E); //element <=
	lower(E); //element <
	subSet(E from, E to)
}
```


## Itérateurs
Les itérateurs permettent de parcourir une Collection élément par élément.
```java
Collection<Integer> maCollection;
Iterator<Integer> i = maCollection.iterator();
while(i.hasNext()) {
	System.out.println(i.next());
}
```
**ListIterator** permet de parcourir la liste dans les deux sens et de changer le sens pendant le parcours.  
```java
while(i.hasPrevious()) {
	System.out.println(i.previous());
}
```
On peut aussi utiliser la boucle **foreach** avec un tableau ou une instance d'Iterable (les collections par exemple).

## Map<K,V> 
![Image : classes implémentant Map.](../assets/cpoa_map.png)
Une Map est comme un dictionnaire. Un parcours se fait sur les clés.

```java
interface Map<E> {
	put(K,V);
	get(K);
	remove(K);
	containsKey(K);
	containsValue(V);
	keySet(); // set des clés
	values(); // set des valeurs
	entrySet(); // set double :getKey(), getValue().
}
```

### HashMap<K,V> - Implémente Cloneable  
> Constructeurs : `HashMap([cap])` ou `HashMap(cap,load)` cap*2 quand (load)% de la table est atteint.
```java
Class HashMap<E> {
	HashMap();
	HashMap(cap);
	HashMap(cap, load); //cap*2 quand (load)% de la table est atteint.
}
```

- **hashCode()** (nécessaire) : génère K à partir de V
- **equals()** (nécessaire) : permet de savoir la position dans la table. Deux éléments égaux doivent avoir le même hashCode.


### SortedMap ◦ TreeMap<K,V>
```java
Class TreeMap<E> {
	TreeMap();
	TreeMap(Comparator);
	TreeMap(Map);
	TreeMap(SortedMap);

}
```

## classe Collections
Algorithmes génériques opérant sur certaines collections (souvent des listes).
- sort (List<T> [Comparator<T>]) tri avec compareTo de Comparable (ou de comparator si il est fourni).
- reverse(List<T>)
- fill(List<T>, T)
- copy(List<T> dest, List<T> src)



# Patrons de conception
Bonnes pratiques de la COO.
Solutions de haut niveau : s'adaptent à tous les languages.

## Patron stratégie
- Classe Context : gère une référence à un objet Stratégie
- Interface Stratégie : implémentée par plusieurs classe concrètes.

## Patron adapter
- Une classe sert d'**adaptateur** entre le client et les classes à adapter.
- L'adaptateur peut se lier aux classes à adapter par 2 moyens :
  - Extends les classes à adapter
  - Prendre les classes à adapter en paramètre

## Patron itérateur
- L'itérateur fournit un objet qui permet de parcourir toute Collection indépendamment de sa structure.

4 Opérations :
- `premier()`
- `suivant()`
- `termine()` : booléen vrai si on est à la fin
- `elementCourant()` : dans Java, cette méthode est dans `suivant()`.