<script type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.3/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

# 2A - Modèle Probabiliste
[*Retour à l'accueil*](./../README.md)

## Menu

- [2A - Modèle Probabiliste](#2a---modèle-probabiliste)
  - [Menu](#menu)
  - [I. Événements](#i-événements)
      - [Système complet d'événements](#système-complet-dévénements)
  - [II. Probabilités](#ii-probabilités)
  - [III. Indépendance](#iii-indépendance)
  - [IV. Probabilité Conditionelle](#iv-probabilité-conditionelle)
  - [V. Variables aléatoires](#v-variables-aléatoires)
  - [VI. Lois de probabilité continues](#vi-lois-de-probabilité-continues)
      - [Espérance](#espérance)
      - [Variance](#variance)
  - [VII. Lois de probabilité discrètes](#vii-lois-de-probabilité-discrètes)
      - [Loi de Bernoulli](#loi-de-bernoulli)
      - [Loi binomiale](#loi-binomiale)
      - [Loi de Poisson](#loi-de-poisson)


___

> **Ω Espace fondamental :** ensemble des résultats possibles d'une expérience aléatoire. $$Ω=\bar{∅}$$

## I. Événements
> **Espace Probabilisable :** $(Ω, P(Ω))$  
> > $Ω$ : univers  
> > $P(Ω)$ : événements

> **Incompatibilité :** :pushpin:$A∩B=∅$  
> Dans ce cas $P(A)∪P(B) = P(A)+P(B)$

#### Système complet d'événements
> Est formé de toutes les parties de $$.
> > $∪E=Ω$  

les parties de $Ω$ ne sont prises qu'une fois : $E₁∩E₂=∅$

$A$ et $\bar{A}$ forment un SCE.  
C'est pourquoi :pushpin:$P(B)=P(A∩B)+P(\bar{A}∩B)$





## II. Probabilités
> **Probabilité :** [Application](#application) :  
> > $ε(Ω) → [0,1] \newline
> > A → P(A)$
> 
> Une probabilité vérifie :  
> - $P(A) ⊂ [0,1]$      
> - $P(Ω)=1$

> #### Application
> Une **application** d’un ensemble A dans un ensemble B est une opération qui fait correspondre à tout élément x de A un élément y de B et un seul.

Propriétés :
- Additivité : $P(A∪\bar{A}) = P(A)+P(\bar{A})$
- propriété de la réunion : $A∪\bar{A}=Ω$
- propriété de l'intersection : $A∩\bar{A} = ∅$

Soit les événements A, B et C :
- au moins un = $A∪B∪C$
- tous = $A∩B∩C$
- au plus 2 = tout sauf tous = $(\overline{A∩B∩C})$

> #### Formule des probabilités totales
> Si B₁, B₂, B₃ forment une partition de Ω, alors  
:pushpin:$P(A)=P(A∪B₁)+P(A∪B₂)+P(A∪B₃)$

> #### Équiprobabilité : règle de Laplace
> :pushpin:P(A)=card(A) / card(Ω)

card(E)=taille de l'ensemble E





## III. Indépendance
> #### Théorème de l'Indépendance
> A et B indépendants ssi :pushpin:P(A∩B)=P(A)P(B)

Si A et B indépendants Pₐ(B)=P(B).  
Si A et B indépendants ¬A et B indépendants. 


> **Pour A et B quelconques :**  
> :pushpin:P(A∩B)=P(A)P(B)-P(A∪B)





## IV. Probabilité Conditionelle
> La probabilité de B dépendant de A est notée **Pₐ(B)**.  
> :pushpin:P(A∩B) / P(A) Dépend de A.

> #### Formule des probabilités composées
> :pushpin:P(A∩B)=P(A)Pₐ(B)




## V. Variables aléatoires
> **Espace probabilisé :** (Ω, P(Ω), p)  
> Ω : univers  
> P(Ω) : Événement  
> p : probabilité

> **Variable aléatoire :**  :pushpin:  
> > x:  Ω  ⇒ ℝ  
> > ωᵢ ⇒ x(ωᵢ)=xᵢ

> **Espace Image :** X(Ω) ensemble des valeurs prises par X. 
> - Si X(Ω) est discret : x est une **Variable aléatoire discrète**.
> - Si X(Ω) est continu : x est une **Variable aléatoire continue**. 





## VI. Lois de probabilité continues
> **Loi de probabilité de X :** Probabilité que x prenne chacune des valeurs de X(Ω).
>
|X=xᵢ|0|1|2|
|--|--|--|--|
|P(X=xᵢ)|1/8|2/8|5/8|

✍🏻les événements X=xᵢ forment un [Système complet d'événements](#système-complet-dévénements).
C'est pourquoi Σ P(X=xᵢ) = 1

#### Espérance
> **Espérance :** Somme des xᵢ pondérés par leur probabilité :  
>:pushpin: E(X) = Σ(xᵢ) P(X=xᵢ)  

E(X+Y)=E(X)+E(Y)  
E(kX)=kE(X)  
E(X+a)=E(X)+a

#### Variance 
> **Variance :** Somme des carrés des écarts à la moyenne :   
> = Σ(xᵢ-E(X))² P(X=xᵢ)  
> = Σ(x² P(X=xᵢ))  
> = E(X²)-E(X)²  
> :pushpin:V(X) = E[(X-E(X))²]

> **Écart-type :** :pushpin:σ = √ V(X)

V(X+Y)=V(X)+V(Y)  
V(kX)=k²V(X)  
V(X+a)=V(X)






## VII. Lois de probabilité discrètes
#### Loi de Bernoulli
> C'est la loi d'une **variable aléatoire discrète** qui ne prend que deux valeurs.  
> L(X)=B(p\)

|X=xᵢ|0|1|
|--|--|--|
|P(X=xᵢ)|1-p|p|

>**Espérance d'une loi de Bernoulli :** :pushpin:E(X)=p  
>**Variance d'une loi de Bernoulli :** :pushpin:V(X)=p(1-p)


#### Loi binomiale
> Un ensemble de probabilités suit la loi binomiale B(n;p) **ssi** il forme un **schéma de Bernoulli** (expériences répétées, identiques et indépendantes).  
> B(n;p) : :pushpin:P(X=k) = (k \\ n) pᵏ(1-p)ⁿ⁻ᵏ

Une loi binomiale, s'applique par exemple
à un tirage avec remise. 

> Coefficient bionomial : :pushpin:(k \\ n) = n! / k! (n-k)! 
> - (k \\ n) = (n-k \\ n) 
> - (k \\ n) + (k+1 \\ n) = (k+1 \\ n+1) - *Formule de Pascal*
> - (0 \\ n) = 1    
> - (1 \\ n) = n    
> - (n \\ n) = 1    
> - (0 \\ 0) = 1    


>**Espérance d'une loi binomiale :** :pushpin:E(X)=np  
>**Variance d'une loi binomiale :** :pushpin:V(X)=np(1-p)

#### Loi de Poisson
> Pour les événements rares
> P(X=k) = e⁻λ λᵏ/k!

X suit la loi de poisson : L(X)=P(λ)

>**Espérance et variance d'une loi de poisson :** :pushpin:E(X)=V(X)=λ