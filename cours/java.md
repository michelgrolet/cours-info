# CPOA

[Retour à l'accueil](./../README.md)

L'API Collection du package java.util.

## Menu

- [CPOA](#cpoa)
	- [Menu](#menu)
	- [Collection](#collection)
		- [List](#list)
		- [Set](#set)
			- [HashSet](#hashset)
			- [TreeSet](#treeset)
		- [Itérateurs](#itérateurs)
	- [Map<K,V>](#mapkv)
		- [HashMap<K,V>](#hashmapkv)
		- [TreeMap<K,V>](#treemapkv)
	- [classe Collections](#classe-collections)

---

## Collection

### List
Accès à partir de l'index.

### Set
Pas de doublons : permet de gérer des ensembles d'objets.
#### HashSet
Tableau qui associe une valeur à une clé.
Pas d'ordre.
#### TreeSet
Trie les éléments. Tous les objets doivent implémenter Comparable.

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
On peut aussi utiliser la boucle **foreach** avec un tableau ou une instance d'Iterable (comme les collections).

## Map<K,V> 
Map : table avec des clés uniques.
- put(K,V) associe V à K.
- get(K)
- remove(K)
- containsKey(K)
- containsValue(V)
- keySet() retourne l'ensemble de toutes les clés.
- values() retourne une collection contenant les valeurs.
- 
> On ne parcours pas une Map mais l'ensemble de ses clés.

### HashMap<K,V>
Implémente Cloneable.
**Nécessite la fonction hashCode()** qui génère K à partir de V.
- clone() duplique la table.

```java
new HashMap<K,V>([capacité],[tauxRemplissage])
```

### TreeMap<K,V>
Implémente SortedMap.

## classe Collections
Algorithmes génériques opérant sur certaines collections (souvent des listes).
- sort (List<T> [Comparator<T>]) tri avec compareTo de Comparable (ou de comparator si il est fourni).
- reverse(List<T>)
- fill(List<T>, T)
- copy(List<T> dest, List<T> src)