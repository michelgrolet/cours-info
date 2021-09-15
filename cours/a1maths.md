# Mathématiques

Cours de mathématiques discrètes (logique, ensembles, ...) et d'algèbre linéaire (pivot, matrices, ...).

#### Mathématiques discrètes

[Logique](#logique)

[Ensembles](#ensembles)

[Relations](#relations)

#### Algèbre linéaire

[Méthode du pivot](#pivot)

[Matrices](#matrices)

[Espaces Vectoriels](#espvect)

[Familles libres génératrices](#flg)

[Applications linéaires](#al)

[Noyau et image](#neti)

#### Analyse

[Majorer Minorer Encadrer](#majmin)

## Logique

On utilise une **table de vérité** pour représenter chaque possibilités pour chaque proposition.

### Opérateurs

* Et : ∧
* Ou : ∨
* OU exclusif : ⊕ (1 | 1 > 0)
* Négation : ¬

### Loi de Morgan

$$\neg(p \wedge q) = (\neg p) \vee (\neg q)$$ $$\neg(p \vee q) = (\neg p) \wedge (\neg q) $$

### Implication

* 1 1 ⇒ 1
* 1 0 ⇒ 0
* 0 1 ⇒ 1
* 0 0 ⇒ 1

$$¬(p ⇒ q) = p ∧ (¬q)$$

### Équivalence

* 1 1 ⇔ 1
* 1 0 ⇔ 0
* 0 1 ⇔ 0
* 0 0 ⇔ 1

$$¬(p ⇒ q) = p ∧ (¬q)$$

## Ensembles

Collection d'éléments définissable par la liste des éléments ou par des propriétés communes aux éléments.

Exemples : $N$, $Z$, $D$, $Q$, $R$, $Ø$, $\{1, 2, 3, 4\}$, $\{xcR | propriété\}$

Différence : $A\B=A∪\bar B$

Complémentaire de A : $A^c$ ou $\bar A$

## Relations

Une relation entre les éléments de deux ensembles E et F est un sous-ensemble G du produit cartésien ExF.  
Autrement dit, c'est un ensemble de couples dont le premier élément est dans E et le second dans F.  
Une relation est notée xRy.  
R peut désigner n'importe quelle définition mathématique : la divisibilité de y par rapport à x, l'infériorité de y par rapport à x... Donc **xRy != yRx**  
Si f est injective alors f(x)=f(y) => x=y  
E et F peuvent être n'importe quels ensembles.  
**Relation binaire :** E = F

### Représentation d'une relation

#### Par une liste

<div class="exemple">{(a,a),(a,b),(a,c),(b,d),(c,b),(c,d),(c,e),(d,d),(d,f),(e,a)}  
définit une relation binaire sur E = {a,b,c,d,e,f}.</div>

#### Par un tableau

Pour aRb, on coche la ligne a, colonne b.

#### Par un diagramme

(seulement pour les relations binaires)  
On trace des flèches vers les éléments en relation.  

### Ordonner des couples (a,b)

On ordonne a+b. Si deux a+b sont égaux, on les met à côté.  
Exemple : (1,1) < (1,2) (2,1) < (3,2)

### Relations d'équivalence

Exemple type : égalité sur R

#### R doit être transitive

xRy ∧ yRz ⇒ xRz

Sur un tableau : pour chaque case xRy, il faut que toutes les colonnes cochées sur la ligne b soient cochées sur la ligne a.

Avec = : si x=y et y=x alors x=z

#### R doit être reflexive

xRy

Sur un tableau : toute la diagonale est cochée.

Avec = : x=x

#### R doit être symétrique

xRy ⇒ yRx

Sur un tableau : lorsqu'une case hors diagonale est cochée, la case symétrique l'est aussi.

Avec <= : si x=y alors y=x

### Relations d'ordre

Relation d'ordre totale : pour tout x et y, si x<=y alors x est en relation d'ordre totale avec y.

Exemple type : inégalité <= sur R

#### R doit être transitive

xRy ∧ yRz ⇒ xRz

Sur un tableau : pour chaque case xRy, il faut que toutes les colonnes cochées sur la ligne b soient cochées sur la ligne a.

Avec <= : si x<=y et y<=x alors x<=z

#### R doit être reflexive

xRy

Sur un tableau : toute la diagonale est cochée.

Avec <= : x<=x

#### R doit être antisymétrique

xRy ∧ yRx ⇒ x = y

Sur un tableau : lorsqu'une case hors diagonale est cochée, la case symétrique ne l'est pas.

Avec <= : si x<=y et y<=x alors x=y

### Minorants et majorants d'un couple (a,b)

#### Minorants

Les minorants sont les couples (x,y) tels que (x,y)R(a,b)  
x <= a  
y <= b  
]-oo,a] x ]-oo,b]  
C'est un plan.

Sur un tableau : les minorants sont les lignes entièrement cochées.

#### Majorants

Les minorants sont les couples (x,y) tels que (a,b)R(x,y)  
a <= x  
b <= y  
]a,+oo] x ]b,+oo]  
C'est un plan.

Sur un tableau : les majorants sont les colonnes entièrement cochées.

## Résolution d'équations linéaires, méthode du pivot

Pour chaque ligne :

* On choisit dans la partie gauche du tableau un coefficient non nul (1 si il y en a un). c'est le **pivot**.
* Si le pivot n'est pas un 1, on divise tous les coefficients de la ligne par le pivot. ($L_{n} ← @L_{n}/p$)
* Dans les autres lignes, on cherche à faire apparaitre un 0 dans la colonne du pivot. ($L_{m} ← @L_{m} - x.L_{n}$)

Si tous les coefficients d'une ligne sont nuls, on passe à la suivante.

On peut obtenir une ligne ou une colonne **sans pivot** (si le nombre de lignes n'égale pas le nombre de colonnes). On s'arrête quand même. Les colonnes sans pivot sont alors appellées **inconnues auxillaires**. On a alors une infinité de solutions. Les autres inconnues sont dites **principales**. Dans la solution, on exprime les inconnues principales en fonction des auxillaires.

Si il n'y a pas d'inconnues auxillaires, le système admet une unique solution.

Si il y a toute une ligne de 0 dans la partie gauche :

* Si la partie droite est non nulle, le système est impossible.
* Sinon, on réécrit le système en oubliant ces lignes.

On peut aussi résoudre des systèmes simultanés. La partie de gauche est similaire aux deux systèmes, mais il y en a deux à droite. On obtient un résultat pour chaque système.

On peut aussi résoudre des systèmes avec des inconnues à droite. Le résultat sera simplement exprimé avec ces inconnues.

## Matrices

Élément à la ligne i colonne j : $m_{ij}$

Matrices particulères :

* Matrice ligne : 1xn
* Matrice colonne : nx1
* Matrice nulle : 0x0
* Matrice nombre : 1x1
* Matrice carrée : nxn
* Matrice identité d'ordre n : Matrice carrée avec une diagonale à 1 et le reste à 0, notée $I_{n}$

### Somme de matrices

Elles doivent avoir la même taille.

### Transposée

Symétrie par rapport à la diagonale (passant par l'élément $m_{11}$).

### Produit de matrices

Il faut que les matrices soient de forme $a_{n\textbf{p}}$ et $b_{\textbf{p}r}$. La matrice $p = a\times b$ qui en découle est de taille $(n\times r)$.

L'élément $p_{ij}$ est égal à la somme des valeurs successives de (ligne i de a) X (colonne j de b).

Si on multiplie $I_{n}$ par une matrice A d'ordre n, on obtient A. **Attention, pour des matrices : $a \times b ≠ b \times a$.**

### Propriétés

Si A, B et C sont de bonne taille : $A\times (B + C) = AB + AC$

Si $AB=BA$ et A et B matrices carrées, les identités remarquables s'appliquent aux matrices A et B.

Si $A_{nn}$, alors $A\times I_{n} = A$

### Inverse d'une matrice

Si $AB = I_{n}$ alors B et A sont inverses entre elles : $A^{-1} = B$

Ainsi, $A^{-1}\times A = I_{n}$

Une matrice n'a qu'une matrice inverse.

Si $A$ est inversible, $^{t}A$ est inversible.

#### Calcul de l'inverse de A

Il faut résoudre le système simultané comprenant à gauche les coefficients de A, et à droite les coefficients de $I_{n}$.

On obtient à gauche les coefficients de $I_{n}$, et à droite ceux de $A^{-1}$.

Si on n'obtiens pas les coefficients de $I_{n}$, c'est que A n'est pas inversible.

On peut vérifier ensuite que $A.A^{-1} = I_{n}$.

#### Inverse d'un produit

Si A et B sont inversibles, alors AB est inversible et $(AB)^{-1} = A^{-1}B^{-1}$

## Espaces vectoriels

Ensembles d’éléments munis de deux lois :

* Loi de composition interne : $x+y$ ($xcE$ et $ycE$)
  * Élément neutre : $0$ ou $\vec{0}$
  * Élément symétrique : $-x$
* Loi de composition externe : $x.λ$ ($xcE$ et $λcR$)

### Sous espace vectoriel

$F$ est un SEV de $E$ si :

* N'est pas vide, c'est à dire contient l'élément neutre de $E$.
* Est stable pour l'addition, c'est à dire pour $u ∈ F$ et $v ∈ F$ génériques, $u+v ∈ F$.
* Est stable pour la multiplication, c'est à dire pour un réel λ et $u ∈ F$ générique, $λu ∈ F$.

. $F$ est un SEV de E s'il est stable pour les deux lois définies sur E, c'est à dire si : $$\begin{cases}∀(x,y)\in F  x+y\in F \\ ∀x\in F, λ \in \mathbb{R}  λx\in F\end{cases}$$

### Intersection de SEVs

L'intersection de SEVs est aussi un SEV.

### SEV de $\mathbb{R}^{n}$

Tout système d'équations linéaire de second membre nul est un SEV de $\mathbb{R}^{n}$.

### Combinaison linéaire

Pour savoir si $\begin{pmatrix} a \\ m \end{pmatrix}$ s'écrit comme combinaison linéaire de $\begin{pmatrix} b \\ n \end{pmatrix}$ et $\begin{pmatrix} c \\ o \end{pmatrix}$ : résoudre le système $\begin{cases}ax+by = c \\ mx+ny = o\end{cases} $

### Écriture matricielle d'un système d'équations

$\begin{cases}ax+by = m \\ cx+dy = n\end{cases} $ Correspond à $\begin{pmatrix}a & b \\ c & d \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} m \\ n \end{pmatrix}$

## Familles libres génératrices

### Familles libres

Les vecteurs $(u1,u2,...,up)$ constituent une famille **libre** de F ssi  
$k1u1 + k2u2 + ... + kpup = \vec{0}$ admet une solution unique $k1=k2=...=kp=0$. Dans ce cas, $(u1,u2,...,up)$ Sont dit linéairement indépendants.

(Si la famille admet plusieurs solutions, elle n'est pas libre)/p>

Si une famille n'est pas libre elle est **liée**, mais on peut en extraire une famille libre, en enlevant les vecteurs ou aucun pivot n'est trouvé.

La plus grande famille libre qu'on peut extraire est appellée **famille libre maximale**.

### familles génératrices

Les vecteurs $(u1,u2,...,up)$ constituent une famille **génératrice** de f ssi tout vecteur de F peut s'écrire comme combinaison linéaire de $(u1,u2,...,up)$.  

## Applications linéaires

f est une application linéaire ssi

* $f(u+v) = f(u)+f(v)
* $f(ku) = kf(u)

Pour montrer que f est linéaire, on définit u(x1,y1) et v(x2,y2), puis on vérifie les deux égalités précédentes.

Si F est linéaire : f(k1u1+...+knun) = k1f(u1)+...+knf(un)

### Opérations sur les applications linéaires

Soit f et g deux applications linéaires.  
**Somme :** $(f+g)(u) = f(u) + g(u)$  
**Multiplication par un réel :** $(λf)(u) = λf(u)$  
**Composée :**$(gof)(u) = g[f(u)]$ ($gof$ est aussi une application linéaire.)  
**Matrices :**$(gof)(u) = g[f(u)]$ ($gof$ est aussi une application linéaire.)

## Noyau et Image d'une application linéaire

Valeur absolue -> distance entre deux nombres

### Identités remarquables

$(a+b)² = a² + 2ab + b²$

$(a-b)² = a² - 2ab + b²$

$a² - b² = (a-b)(a+b)$