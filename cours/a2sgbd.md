# Bases de Données Relationnelles

[Retour à l'accueil](./../README.md)

## Menu

- [Bases de Données Relationnelles](#bases-de-données-relationnelles)
  - [Menu](#menu)
  - [1. Notations](#1-notations)
  - [2. Dépendances Fonctionnelles](#2-dépendances-fonctionnelles)
    - [Axiomes d'Armstrong](#axiomes-darmstrong)
    - [Autres propiétés des DF](#autres-propiétés-des-df)
    - [Décomposition binaire d'une relation](#décomposition-binaire-dune-relation)
    - [Dépendances Fonctionnelles particulières](#dépendances-fonctionnelles-particulières)
    - [Fermeture Transitive des DF](#fermeture-transitive-des-df)
    - [Couverture Minimale](#couverture-minimale)
    - [Clés de R](#clés-de-r)
    - [X dépend de Y...](#x-dépend-de-y)
  - [3. Formes Normales](#3-formes-normales)
    - [1FN](#1fn)
    - [2FN](#2fn)
    - [3FN](#3fn)
      - [Méthodes pour obtenir une 3FN](#méthodes-pour-obtenir-une-3fn)
    - [BCFN](#bcfn)


---
## 1. Notations
| Définition             | Notation         |
| ---------------------- | ---------------- |
| Colonne                | t[attrr]         |
| Tuple                  | <val1, val2>     |
| Shéma de BDD           | {TABLE1, TABLE2} |
| Shéma de relations     | R(A1, A2)        |
| Attribut A du schéma R | R.A              |


---
## 2. Dépendances Fonctionnelles
```
attrX -> attrY
```
> Une valeur de X détermine alors *au plus* une valeur de Y.  
> X détermine fonctionellement Y.

X &rarr; ∅ est vrai pour tout X.
Quand X ne donne pas Y dans la relation R, on dit que **la dépendance fonctionelle n'est pas vérifiée sur R**.

### Axiomes d'Armstrong
> **Réflexivité :** Y⊆X => X→Y  
> **Augmentation :** X→Y => X∪Z → Y∪Z  
> **Transitivité :** X→Y et Y→Z => X→Z
> 
### Autres propiétés des DF
> **Pseudo-Transitivité :** X→Y et Y∪W→Z => X∪W→Z  
> **Union :** X→Y et X→Z => X→Y∪Z  
> **Décomposition :** X→Y et Z⊆Y => X→Z

### Décomposition binaire d'une relation
On peut décomposer une relation en suivant une DF.
On doit grouper les colonnes redondantes dans la même relation.

### Dépendances Fonctionnelles particulières
> **DF Triviale :** X→Y => Y⊆X  
> **DF Canonique :** X→Y avec Y: un seul attribut.  
> **DF Élémentaire :** X→Y X ne contient pas Y et X Minimum d'attributs donnant Y. 
> **DF Directe :** X→Y avec X→Z, Z→Y et *Z n'existant pas.*

### Fermeture Transitive des DF
> **F+** *(Sur l'ensemble F)* : ensemble des DFE pouvant être trouvées avec les [Axiomes d'Armstrong](#axiomes-darmstrong).

### Couverture Minimale
> **Couverture Minimale :** Ensemble **G** de DF canoniques non-redondantes élémentaires.

- On minimise le nombre de DF.
- Il ne faut pas perdre d'informations.
- On doit n'avoir qu'une fois un même attribut à droite. 
- On peut se servir des [Axiomes d'Armstrong](#axiomes-darmstrong) et des [Autres propiétés des DF](#autres-propiétés-des-df) pour trouver la couverture minimale.

### Clés de R

**Clés de R :** Ensembles X qui vérifient la relation : **X→R**. Autrement dit, ce sont les ensembles qui permettent d'isoler un tuple.

Si on a la DF **X→Clé**, x est une clé.

> **Clé Primaire :** Une des clés de R.  
> **Clé Étrangère :** Clé primaire de R2 appartenant à R.
> **Clé Minimale :** Clé comportant le minimum d'attributs.

### X dépend de Y...

> **Transitivement :** X⊆A | X→Y | X→A | non(Y→X) | Y⊆X  
> **Directement :** *Non-transitivement.*  
> **Pleinement :** Y→A : DFE  
> **Partiellement :** *Nom-pleinement.*

## 3. Formes Normales
> **Formes Normales :** propriétés souhaitables que doit posséder chaque schéma de relations.
Tout schéma passant une FN doit passer la FN précédente.

### 1FN

- Tous les attributs sont atomiques *(une seule info par colonne)*.
- Aucun attribut n'est répétitif.
- Il y a au moins *une* clé *(sinon ce n'est pas une relation)*.

### 2FN

- Les attributs dépendent [pleinement](#x-dépend-de-y) des clés *(clé→X doit contenir toute la clé. Autrement dit, les DF issues d'une clé sont élémentaires).*

### 3FN

- Les attributs dépendent [directement](#x-dépend-de-y) des clés *(non-clé→non-clé ne doit pas exister).*

#### Méthodes pour obtenir une 3FN
<details>
<summary>Par synthèse</summary>

> **L'algorithme synthétique** permet d'obtenir une 3FN.

1. On part de l'ensemble des attributs et des DF.
1. On construit la [couverture minimale](#couverture-minimale)
1. On regroupe dans une même relation les attributs ayant la même partie gauche dans le graphe des DF.
1. Si aucune des relations construites ne permet d'avoir la clé de la relation initiale, on ajoute une relation composée des attributs de cette clé.

</details>

<details>
<summary>Par décomposition</summary>

1. On part du schéma complet (appellé ***relation universelle***).
2. on décompose le schéma pour éviter les DF de la forme **non-clé → non-clé**.

</details>

### BCFN

- Seules les DFE doivent être de la forme clé→X.
- Il n'y a qu'une clé minimale.