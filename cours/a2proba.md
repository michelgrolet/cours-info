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
	- [Loi binomiale](#loi-binomiale)
	- [Lois à densité](#lois-à-densité)

---

> **Ω Espace fondamental :** ensemble des résultats possibles d'une expérience aléatoire.  
> **Espace Probabiliste :** ΩP(Ω)

## Événements
> **Incompatibilité :** A∩B=∅

#### Système complet d'événements
Événements incompatibles 2 à 2.  
Σ∪=Ω
> A et ¬A forment un SCE.  
> C'est pourquoi P(B)=P(A∩B)+P(¬A∩B)

## Probabilités
> Une probabilité vérifie :  
> P(Ω) ⇒ ℝ*  
> A ⇒ p(A)

> P(A) ⊂ [0,1]      
> P(Ω)=1  
> Parmi A B et C :
> - au moins un = A∪B∪C
> - tous = A∩B∩C
> - au plus 2 = tout sauf tous = ¬(A∩B∩C)

#### Formule des probabilités totales
Si B₁, B₂, B₃ forment une partition de Ω, alors
P(A)=P(A∪B₁)+P(A∪B₂)+P(A∪B₃)

#### Équiprobabilité : règle de Laplace
P(A)=card(A) / card(Ω)
> card(E)=taille de l'ensemble E

## Probabilité Conditionelle
Une probabilité conditionelle dépend d'un événement.
> P(A∩B) / P(A) Dépend de A.

La probabilité de B dépendant de A est notée **Pₐ(B)**.

#### Théorème des probabilités composées
P(A∩B)=P(A)Pₐ(B)

#### Indépendance
A et B indépendants ssi P(A∩B)=P(A)P(B)
> Si A et B indépendants Pₐ(B)=P(B)

> Si A et B indépendants ¬A et B indépendants.

## Loi binomiale
(k parmi n) = n (n-1) ... (n-k+1)  / k !

Un ensemble de probabilités suit la loi binomiale ssi il forme un **shéma de Bernouilli** (expériences répétées, identiques et indépendantes).   
P(X=k) = (k parmi n) pᵏ (1-p)ᵏ 



## Lois à densité
> **Variable aléatoire continue :** Admet une infinité d'issues.

