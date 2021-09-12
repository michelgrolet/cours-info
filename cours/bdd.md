# Bases de Données Relationnelles

[Retour à l'accueil](./../README.md)

## Menu

- [Bases de Données Relationnelles](#bases-de-données-relationnelles)
	- [Menu](#menu)
	- [1. Notations](#1-notations)
	- [2. Dépendances fonctionnelles](#2-dépendances-fonctionnelles)
		- [Décomposition binaire d'une relation](#décomposition-binaire-dune-relation)

---

## 1. Notations

| Définition | Notation |
|-|-|
| Colonne | t[attrr] |
| Tuple | <val1, val2> |
| Shéma de BDD | {TABLE1, TABLE2} |
| Shéma de relations | R(A1, A2) |
| Attribut A du schéma R | R.A |


## 2. Dépendances fonctionnelles
```
X -> Y
```
> Une valeur de X détermine alors *au plus* une valeur de Y.

X &rarr; ∅ est vrai pour tout X.

> ### Axiomes d'Armstrong
> **Réflexivité :** Y⊆X => X→Y\
> **Augmentation :** X→Y => X∪Z → Y∪Z\
> **Transitivité :** X→Y et Y→Z => X→Z

> ### Autres propiétés des DF
> **Pseudo-Transitivité :** X→Y et Y∪W→Z => X∪W→Z\
> **Union :** X→Y et X→Z => X→Y∪Z\
> **Décomposition :** X→Y et Z⊆Y => X→Z

### Décomposition binaire d'une relation
On décompose une relation sur les DF.
On sépare les colonnes redondantes.

> ### Dépendances Fonctionnelles particulières
> **DF Triviale :** X→Y => Y⊆X\
> **DF Canonique :** X→Y et X→Z => X→Y∪Z\
> **DF Élémentaire :** X→Y et Z⊆Y => X→Z
> **DF Directe :** X→Y et Z⊆Y => X→Z