# Bases de Données Relationnelles
[*Retour à l'accueil*](./../README.md)

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
  - [Transactions](#transactions)
    - [Propriétés ACID](#propriétés-acid)
    - [Etats d'une transaction](#etats-dune-transaction)
    - [Transactions Oracle](#transactions-oracle)
    - [Tolérance aux pannes](#tolérance-aux-pannes)
    - [Gestion de la concurence](#gestion-de-la-concurence)
      - [Niveaux d'isolation du verouillage :](#niveaux-disolation-du-verouillage-)
      - [RS](#rs)
      - [RX](#rx)
      - [S](#s)
      - [SRX (share row exclusive)](#srx-share-row-exclusive)
      - [X (exclusive)](#x-exclusive)


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



## Transactions
> Transaction : suite d'opérations dans la BDD
### Propriétés ACID
> Atomicité:  
> Cohérence:   
> Isolation: *Une transaction ne voit pas tout*   
> Durabilité: *Toute modification persiste*  

### Etats d'une transaction
> Annulée: on redémarre la transition ou on la tue.  
> Validée: l'effet de la transaction est entériné.

Commit: valide la transaction (elle passe à l'état **validé**).  
Rollback: annule la dernière transaction. 

### Transactions Oracle
Commence avec la première instruction SQL.  
Termine :
- Lors du commit ou rollback
- Déconnection (commit auto)
- Arret du processus (rollback auto)

### Tolérance aux pannes
Les algo de récup permettent de respecter les propriétés ACID.
Ils permettent de revenir à un état cohérent.

Un Journal contient toutes les actions exécutées.
- Démarrage
- Écriture
- Lecture
- Validation
- Annulation

Oracle utilise
- Fichier journal redo log (contient les commits)
- rollback segment (contient la table)

A chaque commit il faut :
- modifier le redo log,
- modifier le rollback segment,
- bloquer les lignes de la table.  

A chaque rollback il faut :
- annuler les actions faites dans le rollback segment, 
- débloquer les lignes de la table.

### Gestion de la concurence
Concurrence entre deux transactions qui accèdent en même temps aux mêmes données.

Un **système de concurrence** doit éviter les introductions d'incohérences.

**Verouillage :** variable binaire associée à une donnée qui décrit si elle est disponible.  
V=0 : la donnée est indisponible.   
C'est trop exclusif.

❗ Interblocage : quand chaque transaction attend une donnée verouillée par une autre transaction.  
✅ Si le sys détecte un interblocage, il peut :
- tuer une des transactions,
- arrêter les attentes des transactions par une **mises hors délai** (timeout).

#### Niveaux d'isolation du verouillage :
```SQL
SET TRANSACTION ISOLATION LEVEL X
```
- `X=SERIALIZABLE` transaction séquentielles.  
- `X=REAPETED READ` on voit les données des transac validées. Lectures multiples donnent le même résultat mais des tuples peuvent apparaître entre deux lectures.
- `X=READ COMMITED` in voit les données des modifs validées. On peut avoir un résult diff entre deux lectures.  
- `X=READ UNCOMMITED` on voit même les données non validées.

Niveaux de granularité : différentes tailles de verouillage
- ligne : on voit que ce qui est validé au `SELECT`
- tuple : verrou DML évite que d'autres transactions verouillent ce tuple. Il s'enlève si commit ou rollback. + verrou DDL


modes de verouillage :
exclusif X : les ressources verouillées ne peuvent pas être partagées.
sinon partagé S

types de verrous : rs, rx, ...

#### RS
Verrou sur les tuples d'une table. Les autres transac peuvent tout faire sauf avoir un verrou exclusif en écriture.

#### RX
Les autres peuvent obtenir RS et RX.

#### S
```SQL
LOCK TABLE tab IN SHARE MODE
```

#### SRX (share row exclusive)
```SQL
LOCK TABLE tab IN SHARE ROW EXCLUSIVE MODE
```

#### X (exclusive)
```SQL
LOCK TABLE tab IN EXCLUSIVE MODE
```