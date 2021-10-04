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
  - [Variables aléatoires discrètes](#variables-aléatoires-discrètes)
  - [Lois de probabilité Discrètes](#lois-de-probabilité-discrètes)
      - [Espérance](#espérance)
      - [Variance](#variance)
      - [Fonction de répartition](#fonction-de-répartition)
      - [Différentes lois de probabilité discrètes](#différentes-lois-de-probabilité-discrètes)
  - [Lois de probabilité continues](#lois-de-probabilité-continues)
      - [Fonction densité de probabilité](#fonction-densité-de-probabilité)
      - [Espérance, Variance](#espérance-variance)
      - [Différentes lois de probabilité continues](#différentes-lois-de-probabilité-continues)
- [Formules](#formules)


___
> $$Ω$$ **Espace fondamental :** ensemble des résultats possibles d'une expérience aléatoire (totalité d'un diagramme de Venn).
> $$(Ω, P(Ω))$$ **Espace Probabilisable :** ensemble des événements de l'univers $$Ω$$.
> $$(Ω, P(Ω), p)$$ **Espace probabilisé :** probabilité $$p$$ sur l'univers $$Ω$$.

> **Expérience aléatoire :** expérience dont on ne connait le résultat qu'après l'avoir exécutée, mais dont on connait toutes les issues.
> **Événement :** sous-ensemble de l'univers d'une expérience aléatoire.




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
Ω → [0,1] \\
A ↦ P(A)
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
## Variables aléatoires discrètes
Pour toute VA $$X$$ :
$$📌x: 
\begin{cases}
Ω → ℝ \\
ωᵢ ↦ x(ωᵢ)=xᵢ
\end{cases}$$ 




___
## Lois de probabilité Discrètes

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
$$📌x: 
\begin{cases}
ℝ → ℝ \\
t ↦ F(t)=P(X≤t)
\end{cases}$$ 
> ✍🏻 Sa représentation est un escalier toujours montant car on inclut toujours les probabilités inférieures.
> $$F⊂ℝ$$
> $$F↗$$
> $$0≤F(t)≤1$$
> $$\lim_{t→0}F(t)=0$$
> $$\lim_{t→∞}F(t)=1$$

> $$P(a≤X≤b)=P(X≤b)-P(X≤a)=F(b)-F(a)$$
> P(X>a)=1-P(X≤a)=1-F(a)

#### Différentes lois de probabilité discrètes

|Notation|Nom      |E(X)  |V(X)       |P(X=k)|
|--      |--       |--    |--         |--|
B(p\)     |Bernoulli|$$p$$ |$$p(1-p)$$ |$$kn$$
B(n;p)   |Binomiale|$$np$$|$$np(1-p)$$|$$\binom{n}{k} pᵏ(1-p)ⁿ⁻ᵏ$$
P(λ)     |Poisson  |$$λ$$ |$$λ$$      |$$\frac{e^{-λ}λ^{k}}{k!}$$

- **Loi de Bernoulli :** pour X ne prenant que 2 valeurs.  
  
|X=xᵢ|0|1|
|--|--|--|
|P(X=xᵢ)|1-p|p|

- **Loi binomiale :** Un ensemble de probabilités suit la loi binomiale **ssi** il forme un **schéma de Bernoulli** (EBRII).  

✍🏻 Une loi binomiale s'applique par exemple à un tirage avec remise. 

> Coefficient bionomial : 📌$$\binom{n}{k}=\frac{n!}{k!(n-k)!}$$ 
> - $$\binom{n}{k} = \binom{n}{n-k}$$, 
> - $$\binom{n}{k} + \binom{n}{k+1} = \binom{n+1}{k+1}$$ - *Formule de Pascal*,
> - $$\binom{n}{0} = 1$$,    
> - $$\binom{n}{1} = n$$,    
> - $$\binom{n}{n} = 1$$,    
> - $$\binom{0}{0} = 1$$.    

- **Loi de Poisson :** s'applique aux événements rares.






___
## Lois de probabilité continues

#### Fonction densité de probabilité
On suppose que $$F'(t)=f(t)$$.

✍🏻 F(t) est la densité de la loi *continue* de X.

$$f(t)≥0$$  
$$\begin{align}
P(a≤X≤b) &= F(b)-F(a) \\
         &= \int_{a}^{b} f(x) \,dx
\end{align}$$  
$$\begin{align}
P(X≤b) &= \int_{-∞}^{b}f(x) \,dx \\
       &= \lim_{a→+∞} \int_{a}^{b}f(x) \,dx \\
       &= F(b)-\lim_{a→-∞}F(a)
\end{align}$$  

#### Espérance, Variance
$$E(X)=\int_{-∞}^{+∞}xf(x) \,dx$$  
$$V(X)=E(X²)-E(X)²$$ avec $$E(X²)=\int_{-∞}^{+∞}x²f(x) \,dx$$

#### Différentes lois de probabilité continues
Notation|Nom            | E(X)              | V(X)                  | FDP f(x)         | f(x)⊂      | P(c≤X≤d)
--      |--             |--                 |--                     |--                |--          |--   
U(a;b)  | Uniforme      | $$\frac{a+b}{2}$$ | $$\frac{(b-a)²}{12}$$ | $$\frac{1}{b-a}$$| $$[a;b]$$  | $$\frac{d-c}{b-a}$$
E(λ)    | Exponentielle | $$\frac{1}{λ}$$   | $$\frac{1}{λ²}$$      | $$λe^{-λx}$$     | $$[a;+∞[$$ | $$e^{-λc}-e^{-λd}$$
N(m;σ²) | Normale       | $$m$$             | $$σ²$$                | $$\frac{e^{-0,5(\frac{x-n}{σ})²}}{σ\sqrt{2\pi}}$$|$$\R$$|$$\int_{a}^{b}f(x) \,dx$$
N(0;1)|Normale Centrée Réduite|$$0$$|$$1$$|$$\frac{e^{x²/2}}{\sqrt{2\pi}}$$|$$\R$$|$$\int_{a}^{b}f(x) \,dx$$

- **Loi normale centrée réduite :**   
Comme la FDP est paire (symétrique) : $$P(T≤-u) = P(T≥u) = 1-P(T≤u)$$





# Formules

Incompatibilité | $$A∩B=∅$$  

Probabilité | $$ε(Ω) → [0,1]$$ | $$A → P(A)$$  

Probabilités totales | $$P(A)=P(A∩B₁)+P(A∩B₂)+P(A∩B₃)$$  

Équiprobabilité | $$P(A)=\frac{card(A)}{card(Ω)}$$  

Union | $$P(A∩B)=P(A)P(B)-P(A∪B)$$  

Indépendance | $$P(A∩B)=P(A)P(B)$$  

Probabilités composées | $$P(A∩B)=P(A)P_{A}(B)$$  

Variable Aléatoire | $$x: Ω ⇒ ℝ$$ | $$ωᵢ ⇒ x(ωᵢ)=xᵢ$$  

Espérance | $$Σ(xᵢ) P(X=xᵢ)$$  

Variance | $$E[(X-E(X))²]$$  
