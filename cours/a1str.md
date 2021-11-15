# Cours Structure de données

[Retour à l'accueil](./../README.md)

Une structure de données est une donnée abstraite dont le comportement est modélisé par des opérations abstraites. Elle peut être décrite par un TAD (Type Abstrait de données).

## Les structures linéaires

Les structures linéaires organisent les données en séquences. Tout élément d’une séquence, sauf le dernier, possède un successeur. Les opérations d’ajout et de suppression d’éléments sont les opérations de base des structures linéaires.

[Les listes](#liste)

[Les listes symétriques](#listesym)

[Les piles](#pile)

[Les files](#file)

[Les files avec priorité](#filepe)

[Les tables](#table)

### Les listes

Une liste est une **séquence finie d’éléments de même type repérés selon leur rang.**

**Suc**, fonction de succession, permet d'accéder à toutes les places en l'appliquant de manière répétée à partir de la première place de la liste. La première place est appellée <span class="code">Tête</span>.

#### Opérations sur les listes

**Légende :** l : liste - p : place - v : valeur

<table>

<tbody>

<tr>

<td><span class="code">tête(l)</span></td>

<td>Désigne le premier élément de la liste.</td>

</tr>

<tr>

<td><span class="code">val(l,p)</span></td>

<td>Désigne la valeur associée à une place.</td>

</tr>

<tr>

<td><span class="code">suc(l,p)</span></td>

<td>Renvoie le successeur d'une place.</td>

</tr>

<tr>

<td><span class="code">finliste(l,p)</span></td>

<td>Renvoie vrai si la place est nil (fin de la liste).</td>

</tr>

<tr>

<td><span class="code">lisvide()</span></td>

<td>Crée une liste vide.</td>

</tr>

<tr>

<td><span class="code">adjtlis(l,v)</span></td>

<td>Ajout en tête de liste.</td>

</tr>

<tr>

<td><span class="code">suptlis(l)</span></td>

<td>Suppression en tête de liste.</td>

</tr>

<tr>

<td><span class="code">adjqlis(l,v)</span></td>

<td>Ajout en queue de liste.</td>

</tr>

<tr>

<td><span class="code">supqlis(l)</span></td>

<td>Suppression en queue de liste.</td>

</tr>

<tr>

<td><span class="code">adjlis(l,v,p)</span></td>

<td>Ajout après une place.</td>

</tr>

<tr>

<td><span class="code">suplis(l,p)</span></td>

<td>Suppression à une place.</td>

</tr>

<tr>

<td><span class="code">chglis(l,p,v)</span></td>

<td>Changement de la valeur d'un élément.</td>

</tr>

</tbody>

</table>

Ceci est un algorithme logique mettant à notre disposition des foctions pour les listes. Mais ces fonctions sont **théoriques**. Elles n'ont pas d'existence réelle en programmation.  
Par contre, on a deux sortes de représentation des listes en programmation : contiguë et chainée.

#### Représentation contiguë des listes

La liste est stockée sur un tableau ou l'indice représente la place dans la liste. Le nombre d'élément du tableau est stocké dans une variable<span class="code">nb</span>. La représentation contiguë est plus lente pour ajouter/supprimer, car il faut tout décaler.

#### Représentation chainée des listes

La liste est stockée sur un tableau multidimensionnel représentant des couples valeur, successeur. L'indice de tête est stocké dans une variable<span class="code">tête</span>. La représentation chainée prends plus de place car des cases du tableau ne sont pas utilisées.

#### Algorithme de création de liste

<div class="code">

<div class="lang">Algorithmique</div>

fonction creerListe( ) : Liste(Trucs)  
  début  
    listeTrucs ← lisvide( )  
    nombreTrucs ← lire( )  
    pour i de 1 à nombreTrucs faire  
      truc ← lire( )  
      adjqlis (listeTrucs, truc)  
    fpour  
    retourne listeTrucs  
  fin</div>

#### Algorithme de parcours de liste

<div class="code">

<div class="lang">Algorithmique</div>

début  
  place ← tête (liste)  
  trouve ← faux  
  tantque non finliste (liste, place) et non trouve faire  
    valeur ← val (liste, place)  
    ...  
    si Condition (valeur) alors  
      ...  
      trouve ← vrai  
    sinon  
      ...  
      place ← suc (liste, place)  
    fsi  
  ftantque  
fin</div>

### Les piles

Structure LIFO, comme une pile d'assiettes.

**Légende :**  
p : pile

<table>

<tbody>

<tr>

<td><span class="code">estVidePile(p)</span></td>

<td>Renvoie vrai si la pile est vide.</td>

</tr>

<tr>

<td><span class="code">sommet(p)</span></td>

<td>Renvoie le sommet de la pile p</td>

</tr>

<tr>

<td><span class="code">pileVide()</span></td>

<td>Crée une pile vide.</td>

</tr>

<tr>

<td><span class="code">empiler(p)</span></td>

<td>Empile une valeur.</td>

</tr>

<tr>

<td><span class="code">depiler(p)</span></td>

<td>Dépile une valeur (elle disparait).</td>

</tr>

</tbody>

</table>

### Les files

Structure FIFO, comme une file d'attente.

**Légende :**  
f : file

<table>

<tbody>

<tr>

<td><span class="code">estVideFile(f)</span></td>

<td>Renvoie vrai si la file est vide.</td>

</tr>

<tr>

<td><span class="code">premier(f)</span></td>

<td>Renvoie la première valeur de la file f</td>

</tr>

<tr>

<td><span class="code">fileVide()</span></td>

<td>Crée une file vide.</td>

</tr>

<tr>

<td><span class="code">adjfil(f)</span></td>

<td>enfile une valeur.</td>

</tr>

<tr>

<td><span class="code">supfil(f)</span></td>

<td>défile une valeur (elle disparait).</td>

</tr>

</tbody>

</table>

### Les files avec priorité

Structure FIFO modifiée : chaque élément a une priorité, comme une file pour entrer en boite.  
La priorité varie de 1 à 5 (1 est la plus forte).

**Légende :**  
f : file  
p : priorité

<table>

<tbody>

<tr>

<td><span class="code">estVidefp(f)</span></td>

<td>Renvoie vrai si la file est vide.</td>

</tr>

<tr>

<td><span class="code">premierfp(f)</span></td>

<td>Renvoie la première valeur de la file f (la plus prioritaire).</td>

</tr>

<tr>

<td><span class="code">fpVide()</span></td>

<td>Crée une file vide.</td>

</tr>

<tr>

<td><span class="code">adjfp(f,p)</span></td>

<td>enfile une valeur.</td>

</tr>

<tr>

<td><span class="code">supfp(f,p)</span></td>

<td>défile la valeur la plus prioritaire (elle disparait).</td>

</tr>

</tbody>

</table>

### Les listes symétriques

Chaque élément désigne l'élément suivant et l'élément précédent.

<table>

<tbody>

<tr>

<td><span class="code">têtels(l)</span></td>

<td>Désigne la tête de la liste.</td>

</tr>

<tr>

<td><span class="code">queuels(l)</span></td>

<td>Désigne la queue de la liste.</td>

</tr>

<tr>

<td><span class="code">valls(l,p)</span></td>

<td>Désigne la valeur associée à une place.</td>

</tr>

<tr>

<td><span class="code">sucls(l,p)</span></td>

<td>Renvoie le successeur d'une place.</td>

</tr>

<tr>

<td><span class="code">precls(l,p)</span></td>

<td>Renvoie le précédent d'une place.</td>

</tr>

<tr>

<td><span class="code">finls(l,p)</span></td>

<td>Renvoie vrai si la place est nil (fin de la liste).</td>

</tr>

<tr>

<td><span class="code">lsvide()</span></td>

<td>Crée une liste vide.</td>

</tr>

<tr>

<td><span class="code">adjtls(l,v)</span></td>

<td>Ajout en tête de liste.</td>

</tr>

<tr>

<td><span class="code">suptls(l)</span></td>

<td>Suppression en tête de liste.</td>

</tr>

<tr>

<td><span class="code">adjqls(l,v)</span></td>

<td>Ajout en queue de liste.</td>

</tr>

<tr>

<td><span class="code">supqls(l)</span></td>

<td>Suppression en queue de liste.</td>

</tr>

<tr>

<td><span class="code">adjls(l,v,p)</span></td>

<td>Ajout après une place.</td>

</tr>

<tr>

<td><span class="code">supls(l,p)</span></td>

<td>Suppression à une place.</td>

</tr>

<tr>

<td><span class="code">chgls(l,p,v)</span></td>

<td>Changement de la valeur d'un élément.</td>

</tr>

</tbody>

</table>

## Les tables

Associe une valeur à une clé unique. Notation : T = Table [ Clé → Valeur ]

Les clés doivent être des entiers bornés.

Attention ! Les tables n'ont rien à voir avec les tableaux.

Équivalent hashtables en Java, dictionaires en Python.

<table>

<tbody>

<tr>

<td><span class="code">tabvide</span></td>

<td>Crée une table vide vide.</td>

</tr>

<tr>

<td><span class="code">dom(t)</span></td>

<td>Fournit l'ensemble des entrées de la table sous la forme ENS(V) où V est un type quelconque.</td>

</tr>

<tr>

<td><span class="code">accèstab(t, c)</span></td>

<td>Accès à la valeur associée à une clé. Si elle n'existe pas, accèstab retourne ω.</td>

</tr>

<tr>

<td><span class="code">adjtab(t, c, v)</span></td>

<td>Adjonction d'un couple dans une table.</td>

</tr>

<tr>

<td><span class="code">suptab(t)</span></td>

<td>Suppression d'une valeur dans la table.</td>

</tr>

<tr>

<td><span class="code">chtab(t, c, v)</span></td>

<td>Changement d'une valeur dans la table.</td>

</tr>

</tbody>

</table>

Pour itérer sur chaque élément de ENS(V) :

<div class="code">

<div class="lang">Algorithmique</div>

pour chaque élément dans ensemble faire  
  //traitement  
fin pour</div>

Fonction <span class="code">estDans(ensemble,element)</span> : renvoie vrai si element est dans ensemble.

### Les tables simples

Les tables simples ont pour clés un intervalle d'entiers.

#### Algorithmes de programmation de tabvide et dom

<div class="code">

<div class="lang">Algorithmique</div>

fonction tabvide( ) : TabTypeEl  
pour i de CLEMIN à CLEMAX faire  
  t[i] 🡐 omega  
fin pour  
retourne t</div>

<div class="code">

<div class="lang">Algorithmique</div>

fonction dom(t : TabTypeEl) : ENS(entier) ensClé 🡐 ensVide( )  
pour i de CLEMIN à CLEMAX faire  
  si t[i] ≠ omega alors  
    adjens(ensClé, i)  
  fin si  
fin pour  
retourne ensClé</div>

### Les tables « non simples »

Si les clés ne sont pas des compositions d'entiers, on ne peut pas accéder directement à la valeur associée.

#### Adressage calculé

L'adresse d'une clé est calculée à l'aide d'une fonction injective. Il faut donc que les clés soient des entiers.

#### Adressage associatif et découpage de la table

N'importe quelles clés (entiers, chaines...), mais pas toujours très efficace.

Pour accéder à une entrée, on doit rechercher la valeur correspondante dans la liste des entrées.

On veut garder l’adressage associatif mais diminuer l’intervalle de recherche. Pour cela, on va partager l’ensemble des clés en sous-ensembles et donc avoir des sous-tables.

Étapes de la recherche d'une entrée dans une table découpée :

1. On utilise une **table majeure** qui associe à chaque entrée i la sous-table à laquelle appartient i.
2. Ensuite on fait une recherche associative dans cette sous-table.

Pour que le temps de recherche soit de même ordre, il faut que les sous-tables soient approximativement de même taille.

L'avantage du partitionnement de tables est que si elle est immense, on peut mettre chaque sous-table en mémoire une par une.

Il y a 3 façons de ranger l'ensemble des entrées dans des sous-tables.

##### Rangement partitionné

On regroupe les clés ayant une propriété commune (par exemple un même préfixe).

##### Rangement indexé

Si l'ensemble des clés est ordonné et borné supérieurement, on le partage en intervalles.

##### Rangement dispersé (« hashing » en anglais)

On doit transformer les clés en nombres, afin de pouvoir les manipuler avec une fonction d'adressage dispersé.

**Rangement dispersé indirect :** La fonction d'adressage fournit une entrée dans la table majeure.

**Rangement dispersé direct :** On ne stocke pas la table majeure, la fonction d'adressage donne directement l'adresse du début de la sous-table. C'est comme une extension du rangement calculé.