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
  - [Lois de probabilité](#lois-de-probabilité)
      - [Espérance](#espérance)
      - [Variance](#variance)
      - [Fonction de répartition](#fonction-de-répartition)
      - [Différentes lois de probabiilté](#différentes-lois-de-probabiilté)
- [Formules](#formules)


___
> $$Ω$$ **Espace fondamental :** ensemble des résultats possibles d'une expérience aléatoire (totalité d'un diagramme de Venn).
> $$(Ω, P(Ω))$$ **Espace Probabilisable :** ensemble des événements de l'univers $$Ω$$.
> $$(Ω, P(Ω), p)$$ **Espace probabilisé :** probabilité $$p$$ sur l'univers $$Ω$$.






___
## Système complet d'événements
Un SCE est formé de toutes les parties de $$Ω$$.
📌 $$∪E_{i}=Ω$$  
les parties de $$Ω$$ ne sont prises qu'une fois : $$E₁∩E₂=∅$$  
✍🏻 $$A$$ et $$\bar{A}$$ forment un SCE. C'est pourquoi 📌$$P(B)=P(A∩B)+P(\bar{A}∩B)$$.







___
## Probabilité
Une **probabilité** se définit par l'**application** :  
$$📌P: 
\begin{cases}
P(Ω) → [0,1] \\
A → P(A)
\end{cases}$$ 

✍🏻 Une **application** $$A→B$$ est une opération qui fait correspondre à tout élément x de A **un seul** élément y de B.

> Une probabilité vérifie :  
> $$P(A)⊂[0,1]$$  
> $$P(Ω)=1$$  
> 📌$$P(A)∪P(B) = P(A)+P(B)$$ *(si compatibles :)* $$-P(A)∩P(B)$$

✍🏻 Propriétés :
- Additivité : $$P(A∪\bar{A}) = P(A)+P(\bar{A})$$
- propriété de la réunion : $$A∪\bar{A}=Ω$$
- propriété de l'intersection : $$A∩\bar{A} = ∅$$

✍🏻 Soit les événements A, B et C :
- au moins un = $$A∪B∪C$$
- tous = $$A∩B∩C$$
- au plus 2 = tout sauf tous = $$(\overline{A∩B∩C})$$

> #### Formule des probabilités totales
> Si B₁, B₂, B₃ forment une partition de Ω, alors  
> 📌$$P(A)=P(A∩B₁)+P(A∩B₂)+P(A∩B₃)$$

> #### Équiprobabilité
> 📌$$P(A)=\frac{card(A)}{card(Ω)}$$  
> avec $$card(E)$$ : taille de l'ensemble E






___
## Indépendance
> #### Théorème de l'Indépendance
> 📌A et B indépendants ssi $$P(A∩B)=P(A)P(B)$$
> 
> ✍🏻 Dans ce cas,
> $$P_{A}(B)=P(B)$$  
> $$P_{A}$$ et $$B$$ indépendants. 






___
## Probabilité Conditionelle
> La probabilité de B dépendant de A est notée $$P_{A}(B)$$.  
> 📌$$P_{A}(B)=\frac{P(A∩B)}{P(A)}$$

> #### Formule des probabilités composées
> 📌$$P(A∩B)=P(A)P_{A}(B)$$





___
## Variables aléatoires
$$📌x: 
\begin{cases}
Ω ⇒ ℝ \\
ωᵢ ⇒ x(ωᵢ)=xᵢ
\end{cases}$$ 

> **Espace Image** $$X(Ω)$$ : ensemble des valeurs prises par X. 
> - Si X(Ω) est discret : x est une **Variable aléatoire discrète**.
> - Si X(Ω) est continu : x est une **Variable aléatoire continue**. 






___
## Lois de probabilité

> **Loi de probabilité de X :** Probabilité que x prenne chacune des valeurs de X(Ω).
>
|xᵢ     |0  |1  |2  |
|--     |-- |-- |-- |
|P(X=xᵢ)|1/8|2/8|5/8|

✍🏻 Les événements X=xᵢ forment un [Système complet d'événements](#système-complet-dévénements). C'est pourquoi $$\sum_{i}P(X=xᵢ)=1$$.

#### Espérance
Somme des xᵢ pondérés par leur probabilité. 
📌 $$E(X) = Σ(xᵢ) P(X=xᵢ)$$  

$$E(X+Y)=E(X)+E(Y)$$  
$$E(kX)=kE(X)$$  
$$E(X+a)=E(X)+a$$

#### Variance 
> Somme des carrés des écarts à la moyenne :   
> $$= \sum(xᵢ-E(X))² P(X=xᵢ)$$  
> $$= \sum(x² P(X=xᵢ))$$  
> $$= E(X²)-E(X)²$$  
> 📌$$V(X) = E[(X-E(X))²]$$

> **Écart-type :** 📌$$σ=\sqrt{V(X)}$$

$$V(X+Y)=V(X)+V(Y)$$  
$$V(kX)=k²V(X)$$  
$$V(X+a)=V(X)$$

#### Fonction de répartition
$$F(t) = P(X⩽t)$$
✍🏻 Sa représentation est un escalier toujours montant car on inclut toujours les probabilités inférieures.


#### Différentes lois de probabiilté
$$\begin{array} {|r|r|}
\hline Nom & E(X) & V(X) & P(X=k) \\ 
\hline B(p) Bernoulli & p & p(1-p) & kn \\ 
\hline B(n;p) Binomiale & np & np(1-p) & \binom{n}{k} pᵏ(1-p)ⁿ⁻ᵏ \\ 
\hline P(λ) Poisson & λ & λ & 3_3 \\ 
\hline  \end{array}$$

- **Loi de Bernoulli :** C'est la loi d'une **variable aléatoire discrète** qui ne prend que deux valeurs.  
|X=xᵢ|0|1|
|--|--|--|
|P(X=xᵢ)|1-p|p|

- **Loi binomiale :** Un ensemble de probabilités suit la loi binomiale **ssi** il forme un **schéma de Bernoulli** (EBRII).  

✍🏻 Une loi binomiale s'applique par exemple à un tirage avec remise. 

> Coefficient bionomial : 📌$$\binom{n}{k} = n! / k! (n-k)!$$ 
> - $$\binom{n}{k} = \binom{n}{n-k}$$, 
> - $$\binom{n}{k} + \binom{n}{k+1} = \binom{n+1}{k+1}$$ - *Formule de Pascal*,
> - $$\binom{n}{0} = 1$$,    
> - $$\binom{n}{1} = n$$,    
> - $$\binom{n}{n} = 1$$,    
> - $$\binom{0}{0} = 1$$.    

- **Loi de Poisson :** s'applique aux événements rares.







# Formules
Incompatibilité | $$A∩B=∅$$  
Dans un SCE | $$P(B)=P(A∩B)+P(\bar{A}∩B)$$  
Probabilité | $$ε(Ω) → [0,1]$$ | $$A → P(A)$$  
Probabilités totales | $$P(A)=P(A∩B₁)+P(A∩B₂)+P(A∩B₃)$$  
Équiprobabilité | $$P(A)=\frac{card(A)}{card(Ω)}$$  
Union | $$P(A∩B)=P(A)P(B)-P(A∪B)$$  
Indépendance | $$P(A∩B)=P(A)P(B)$$  
Probabilités composées | $$P(A∩B)=P(A)P_{A}(B)$$  
Variable Aléatoire | $$x: Ω ⇒ ℝ$$ | $$ωᵢ ⇒ x(ωᵢ)=xᵢ$$  
Espérance | $$Σ(xᵢ) P(X=xᵢ)$$  
Variance | $$E[(X-E(X))²]$$  