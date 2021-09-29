# CPOA

[Retour à l'accueil](./../README.md)

Le framework Collection du package java.util.

## Menu

- [CPOA](#cpoa)
	- [Menu](#menu)
	- [Collection](#collection)
		- [List](#list)
		- [Set](#set)
		- [Itérateurs](#itérateurs)
	- [Map<K,V>](#mapkv)
		- [SortedMap ◦ TreeMap<K,V>](#sortedmap--treemapkv)
	- [classe Collections](#classe-collections)
- [Patrons de conception](#patrons-de-conception)
	- [Patron stratégie](#patron-stratégie)
	- [Patron adapter](#patron-adapter)
	- [Patron itérateur](#patron-itérateur)

___
## Collection
- `size()`
- `isEmpty()`
- `contains(e)`
- `clear()`
- `iterator()`
- `toArray([array])`

> Iterable ◦ Collection
> - List
>   - ArrayList
>   - LinkedList
>   - Vector ◦ Stack
> - Set
>   - HashSet
>   - SortedSet ◦ TreeSet

### List
Accès à partir de l'index.
> #### ArrayList - tableau de taille variable
> Constructeur : `ArrayList([taille]ou[collec])`
> - `get(i)`
> - `set(i,e)`
> - `add([i],e)`
> - `remove(i)`
> - `indexOf(e)` *Nécessite equals()*
> - `lastIndexOf(e)`
> - `listIterator([i])` *i (optionnel): index de départ*

> #### LinkedList - listes doublement chaînées
> - `addLast(e)`
> - `addFirst(e)`
> - `getLast()`
> - `getFirst()`
> - `removeLast()`
> - `removeFirst(e)`

### Set
Pas de doublons : permet de gérer des ensembles d'objets.
> - `s1.containsAll(s2)` return **true ssi s2∈s1**
> - `s1.addAll(s2)` **s1 ← s1∪s2**
> - `s1.retainAll(s2)` **s1 ← s1∩s2**
> - `s1.removeAll(s2)` **s1 ← s1-s2**

> #### HashSet - valeur→clé
> Constructeurs : `HashSet([collec])` ou `HashSet(taille, [loadFactor])`
> - `add(e)`
> - `remove(e)`
> - `clear()`
> - `contains(e)`
> - `isEmpty()`
> - `size()`
> - `iterator()`

> #### TreeSet - nécessite Comparable
> Constructeurs : `TreeSet([Comparator])` ou `TreeSet(Collection)` ou `TreeSet(SortedSet)`
> - `add(e)`
> - `addAll(Collection)`
> - `clear()`
> - `clone()`
> - `comparator()`
> - `contains(e)`
> - `first()`
> - `last()`
> - `remove(e)`
> - `size()`

### Itérateurs
Permet de parcourir une Collection élément par élément.
```java
Collection<Integer>
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
Map : table avec des clés uniques. Un parcours se fait sur les clés.
- put(K,V) associe V à K.
- get(K)
- remove(K)
- containsKey(K)
- containsValue(V)
- keySet() retourne un set contenant les clés.
- values() retourne une collection contenant les valeurs.

> Map
> - HashMap
> - SortedMap ◦ TreeMap

> ### HashMap<K,V> - Implémente Cloneable  
> Constructeurs : `HashMap([cap])` ou `HashMap(cap,load)` cap*2 quand (load)% de la table est atteint.
> - **hashCode()** (nécessaire) : génère K à partir de V
> - **equals()** (nécessaire) : permet de savoir la position dans la table. Deux éléments égaux doivent avoir le même hashCode.
> - containsValue(v)
> - containsKey(k)
> - get(k)
> - put(k,v)
> - remove(k)
> - values() retourne la Collection des valeurs
> - keySet() retourne le Set des clés
> - clone()

### SortedMap ◦ TreeMap<K,V>
Implémente SortedMap.

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
- `termine()` : booleen vrai si on est à la fin
- `elementCourant()` : dans Java, cette méthode est dans `suivant()`.