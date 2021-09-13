# CPOA

[Retour à l'accueil](./../README.md)

L'API Collection du package Java.util :
- Collection,
- List,
- Set,
- Map,
- Queue.

## Menu

- [CPOA](#cpoa)
	- [Menu](#menu)
	- [Collection](#collection)
		- [List](#list)
		- [Set](#set)
			- [HashSet](#hashset)
			- [TreeSet](#treeset)
		- [Itérateurs](#itérateurs)

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