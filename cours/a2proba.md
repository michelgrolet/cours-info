{% include mathjax.html %}

# 2A - Modèle Probabiliste
[*Retour à l'accueil*](./../README.md)

## Menu

- [2A - Modèle Probabiliste](#2a---modèle-probabiliste)
  - [Menu](#menu)
  - [Système complet d'événements](#système-complet-dévénements)
  - [Probabilité](#probabilité)
  - [Indépendance](#indépendance)
  - [Probabilité Conditionelle](#probabilité-conditionelle)
  - [Variables aléatoires](#variables-aléatoires)
  - [Lois de probabilité continues](#lois-de-probabilité-continues)
      - [Espérance](#espérance)
      - [Variance](#variance)
  - [Lois de probabilité discrètes](#lois-de-probabilité-discrètes)
      - [Loi de Bernoulli](#loi-de-bernoulli)
      - [Loi binomiale](#loi-binomiale)
      - [Loi de Poisson](#loi-de-poisson)
      - [Formule de répartition](#formule-de-répartition)
- [Formules](#formules)
- [Lois](#lois)


___

> $$Ω$$ **Espace fondamental :** ensemble des résultats possibles d'une expérience aléatoire (totalité d'un diagramme de Venn).
> $$(Ω, P(Ω))$$ **Espace Probabilisable :** ensemble des événements de l'univers $$Ω$$.
> $$(Ω, P(Ω), p)$$ **Espace probabilisé :** probabilité $$p$$ sur l'univers $$Ω$$.


## Système complet d'événements
Un SCE est formé de toutes les parties de $$Ω$$.
📌 $$∪E_{i}=Ω$$  
les parties de $$Ω$$ ne sont prises qu'une fois : $$E₁∩E₂=∅$$  
> $$A$$ et $$\bar{A}$$ forment un SCE.  
> C'est pourquoi 📌$$P(B)=P(A∩B)+P(\bar{A}∩B)$$


## Probabilité
Une **probabilité** se définit par l'**application** :  
$$📌P: 
\begin{cases}
ε(Ω) → [0,1] \\
A → P(A)
\end{cases}$$ 

> Une **application** d’un ensemble A dans un ensemble B est une opération qui fait correspondre à tout élément x de A un élément y de B et un seul.

> Une probabilité vérifie :  
> $$P(A)⊂[0,1]$$  
> $$P(Ω)=1$$  
> 📌$$P(A)∪P(B) = P(A)+P(B)$$ *si compatibles :* $$-P(A)∩P(B)$$


Propriétés :
- Additivité : $$P(A∪\bar{A}) = P(A)+P(\bar{A})$$
- propriété de la réunion : $$A∪\bar{A}=Ω$$
- propriété de l'intersection : $$A∩\bar{A} = ∅$$

Soit les événements A, B et C :
- au moins un = $$A∪B∪C$$
- tous = $$A∩B∩C$$
- au plus 2 = tout sauf tous = $$(\overline{A∩B∩C})$$

> #### Formule des probabilités totales
> Si B₁, B₂, B₃ forment une partition de Ω, alors  
> 📌$$P(A)=P(A∩B₁)+P(A∩B₂)+P(A∩B₃)$$

> #### Équiprobabilité : règle de Laplace
> 📌$$P(A)=\frac{card(A)}{card(Ω)}$$  
> avec $$card(E)$$ : taille de l'ensemble E





## Indépendance
> #### Théorème de l'Indépendance
> 📌A et B indépendants ssi $$P(A∩B)=P(A)P(B)$$
> 
> Dans ce cas,
> $$P_{A}(B)=P(B)$$  
> $$P_{A}$$ et $$B$$ indépendants. 





## Probabilité Conditionelle
> La probabilité de B dépendant de A est notée $$P_{A}(B)$$.  
> 📌$$P_{A}(B)=\frac{P(A∩B)}{P(A)}$$

> #### Formule des probabilités composées
> 📌$$P(A∩B)=P(A)P_{A}(B)$$




## Variables aléatoires
$$📌x: 
\begin{cases}
Ω ⇒ ℝ \\
ωᵢ ⇒ x(ωᵢ)=xᵢ
\end{cases}$$ 


> **Espace Image** $$X(Ω)$$ : ensemble des valeurs prises par X. 
> - Si X(Ω) est discret : x est une **Variable aléatoire discrète**.
> - Si X(Ω) est continu : x est une **Variable aléatoire continue**. 





## Lois de probabilité continues
> **Loi de probabilité de X :** Probabilité que x prenne chacune des valeurs de X(Ω).
>
|xᵢ     |0  |1  |2  |
|--     |-- |-- |-- |
|P(X=xᵢ)|1/8|2/8|5/8|

✍🏻les événements X=xᵢ forment un [Système complet d'événements](#système-complet-dévénements).
C'est pourquoi $$\sum_{i}P(X=xᵢ)=1$$

#### Espérance
> **Espérance :** Somme des xᵢ pondérés par leur probabilité :  
>📌 $$E(X) = Σ(xᵢ) P(X=xᵢ)$$  

$$E(X+Y)=E(X)+E(Y)$$  
$$E(kX)=kE(X)$$  
$$E(X+a)=E(X)+a$$

#### Variance 
> **Variance :** Somme des carrés des écarts à la moyenne :   
> $$= Σ(xᵢ-E(X))² P(X=xᵢ)$$  
> $$= Σ(x² P(X=xᵢ))$$  
> $$= E(X²)-E(X)²$$  
> 📌$$V(X) = E[(X-E(X))²]$$

> **Écart-type :** 📌$$σ = √ V(X)$$

$$V(X+Y)=V(X)+V(Y)$$  
$$V(kX)=k²V(X)$$  
$$V(X+a)=V(X)$$






## Lois de probabilité discrètes
#### Loi de Bernoulli
> C'est la loi d'une **variable aléatoire discrète** qui ne prend que deux valeurs.  
> $$L(X)=B(p)$$

|X=xᵢ|0|1|
|--|--|--|
|P(X=xᵢ)|1-p|p|

>**Espérance d'une loi de Bernoulli :** 📌$$E(X)=p$$  
>**Variance d'une loi de Bernoulli :** 📌$$V(X)=p(1-p)$$


#### Loi binomiale
> Un ensemble de probabilités suit la loi binomiale B(n;p) **ssi** il forme un **schéma de Bernoulli** (expériences répétées, identiques et indépendantes).  
> $$B(n;p)$$ : 📌$$P(X=k) = \binom{n}{k} pᵏ(1-p)ⁿ⁻ᵏ$$

Une loi binomiale, s'applique par exemple
à un tirage avec remise. 

> Coefficient bionomial : 📌$$\binom{n}{k} = n! / k! (n-k)!$$ 
> - $$\binom{n}{k} = \binom{n}{n-k}$$ 
> - $$\binom{n}{k} + \binom{n}{k+1} = \binom{n+1}{k+1}$$ - *Formule de Pascal*
> - $$\binom{n}{0} = 1$$    
> - $$\binom{n}{1} = n$$    
> - $$\binom{n}{n} = 1$$    
> - $$\binom{0}{0} = 1$$    

>**Espérance d'une loi binomiale :** 📌$$E(X)=np$$  
>**Variance d'une loi binomiale :** 📌$$V(X)=np(1-p)$$

#### Loi de Poisson
> Pour les événements rares
> $$P(X=k) = \frac{e^{-λ} λ^{k}}{k!}$$

X suit la loi de poisson : $$L(X)=P(λ)$$

>**Espérance et variance d'une loi de poisson :** 📌$$E(X)=V(X)=λ$$




#### Formule de répartition
$$F(t) = P(X⩽t)$$
Sa représentation est un escalier toujours montantcar on inclut toujours les probabilités inférieures.




# Formules
- Incompatibilité | $$A∩B=∅$$
- Dans un SCE | $$P(B)=P(A∩B)+P(\bar{A}∩B)$$
- Probabilité | $$ε(Ω) → [0,1]$$ | $$A → P(A)$$
- Probabilités totales | $$P(A)=P(A∩B₁)+P(A∩B₂)+P(A∩B₃)$$
- règle de Laplace | $$P(A)=\frac{card(A)}{card(Ω)}$$
- Union | P(A∩B)=P(A)P(B)-P(A∪B)
- Indépendance | $$P(A∩B)=P(A)P(B)$$
- Probabilités composées | $$P(A∩B)=P(A)P_{A}(B)$$
- Variable Aléatoire | $$x: Ω ⇒ ℝ$$ | $$ωᵢ ⇒ x(ωᵢ)=xᵢ$$
- Espérance | $$Σ(xᵢ) P(X=xᵢ)$$
- Variance | $$E[(X-E(X))²]$$

# Lois
$$\begin{array} {|r|r|}\hline Nom & E(X) & V(X) & P(X=k) \\ \hline Bernoulli & p & p(1-p) & kn \\ \hline Binomiale & np & np(1-p) & \binom{n}{k} pᵏ(1-p)ⁿ⁻ᵏ \\ \hline Poisson & λ & λ & 3_3 \\ \hline  \end{array}$$