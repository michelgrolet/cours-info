# 2A - Modèle Probabiliste

[*Retour à l'accueil*](./../README.md)

## Menu

- [2A - Modèle Probabiliste](#2a---modèle-probabiliste)
  - [Menu](#menu)
  - [Événements](#événements)
      - [Système complet d'événements](#système-complet-dévénements)
  - [Probabilités](#probabilités)
      - [Formule des probabilités totales](#formule-des-probabilités-totales)
      - [Équiprobabilité : règle de Laplace](#équiprobabilité--règle-de-laplace)
  - [Probabilité Conditionelle](#probabilité-conditionelle)
      - [Théorème des probabilités composées](#théorème-des-probabilités-composées)
      - [Indépendance](#indépendance)
  - [Lois de probabilité](#lois-de-probabilité)
      - [Espérance](#espérance)
      - [Variance](#variance)
      - [Loi de Bernoulli](#loi-de-bernoulli)
      - [Loi binomiale](#loi-binomiale)


___

> **Ω Espace fondamental :** ensemble des résultats possibles d'une expérience aléatoire.  
> **Espace Probabiliste :** ΩP(Ω)

## Événements
> **Incompatibilité :** :pushpin:A∩B=∅

#### Système complet d'événements
> Événements incompatibles 2 à 2.  
> Σ∪=Ω

A et ¬A forment un SCE.  
C'est pourquoi :pushpin:P(B)=P(A∩B)+P(¬A∩B)

## Probabilités
Une probabilité vérifie :  
- P(Ω) ⇒ ℝ*  
- A ⇒ p(A)
- P(A) ⊂ [0,1]      
- P(Ω)=1

Parmi A B et C :
- au moins un = A∪B∪C
- tous = A∩B∩C
- au plus 2 = tout sauf tous = ¬(A∩B∩C)

#### Formule des probabilités totales
> Si B₁, B₂, B₃ forment une partition de Ω, alors
:pushpin:P(A)=P(A∪B₁)+P(A∪B₂)+P(A∪B₃)

#### Équiprobabilité : règle de Laplace
> :pushpin:P(A)=card(A) / card(Ω)
> 
card(E)=taille de l'ensemble E

## Probabilité Conditionelle
> La probabilité de B dépendant de A est notée **Pₐ(B)**.  
> :pushpin:P(A∩B) / P(A) Dépend de A.

#### Théorème des probabilités composées
> :pushpin:P(A∩B)=P(A)Pₐ(B)

#### Indépendance
> A et B indépendants ssi :pushpin:P(A∩B)=P(A)P(B)

Si A et B indépendants Pₐ(B)=P(B).  
Si A et B indépendants ¬A et B indépendants.

## Lois de probabilité

> **Variable aléatoire continue :** Admet une infinité d'issues.

> **Loi de probabilité de X :** Probabilité que x prenne chacune valeur de l'espace image X(Ω).

#### Espérance
> E(X) = Σ(xᵢ-E(X)²) P(X=xᵢ)  
E(X+Y)=E(X)+E(Y)  
E(kX)=kE(X)  
:pushpin:E(X+a)=E(X)+a

#### Variance 
> **Variance :** Somme des carrés des écarts à la moyenne.   
> = Σ(xᵢ-E(X))² P(X=xᵢ)  
> = Σ(x² P(X=xᵢ))  
> :pushpin:V(X) = E(X-E(X))²

> **Écart-type :** σ = √ V(X)

V(X+Y)=V(X)+V(Y)
V(kX)=k²V(X)
V(X+a)=V(X)

#### Loi de Bernoulli
> C'est la loi d'une **variable aléatoire discrète**.  
> L(X)=B(p )

P(X=1)=p  
P(X=0)=1-p

>**Espérance d'une loi de Bernoulli :** E(X)=p
>**Variance d'une loi de Bernoulli :** V(X)=p(1-p)


#### Loi binomiale
> Un ensemble de probabilités suit la loi binomiale B(n;p) **ssi** il forme un **schéma de Bernoulli** (expériences répétées, identiques et indépendantes).  
> B(n;p) : P(X=k) = (k parmi n) pᵏ(1-p)ⁿ⁻ᵏ
 
(k parmi n) = n! / k! (n-k)!

>**Espérance d'une loi binomiale :** E(X)=np  
>**Variance d'une loi binomiale :** V(X)=np(1-p)