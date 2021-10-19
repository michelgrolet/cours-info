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
    - [Fonction de répartition](#fonction-de-répartition)
  - [Variables aléatoires discrètes](#variables-aléatoires-discrètes)
  - [Variables aléatoires continues](#variables-aléatoires-continues)
  - [Lois de probabilité Discrètes](#lois-de-probabilité-discrètes)
      - [Espérance](#espérance)
      - [Variance](#variance)
      - [Différentes lois de probabilité discrètes](#différentes-lois-de-probabilité-discrètes)
  - [Lois de probabilité continues](#lois-de-probabilité-continues)
      - [Fonction densité de probabilité](#fonction-densité-de-probabilité)
      - [Espérance, Variance](#espérance-variance)
      - [Différentes lois de probabilité continues](#différentes-lois-de-probabilité-continues)
- [Théorèmes limites et Approximations](#théorèmes-limites-et-approximations)
  - [Lois d'inégalités](#lois-dinégalités)
  - [Théorème central limite](#théorème-central-limite)
  - [Approximation de Lois](#approximation-de-lois)
    - [B par P](#b-par-p)
    - [B par N](#b-par-n)
- [Formules](#formules)
- [Échantillonnage, Estimation, Intervalle de confiance](#échantillonnage-estimation-intervalle-de-confiance)
  - [Distribution d'échantillonnage de proportion](#distribution-déchantillonnage-de-proportion)
  - [Estimation ponctuelle](#estimation-ponctuelle)
  - [Estimation par intervalle de confiance](#estimation-par-intervalle-de-confiance)


___
> $$Ω$$ **Espace fondamental :** ensemble des événements élémentaires d'une expérience aléatoire (P(Ω) = totalité d'un diagramme de Venn = 1).  
> $$(Ω, P(Ω))$$ **Espace Probabilisable :** ensemble des événements de l'univers $$Ω$$.  
> $$(Ω, P(Ω), p)$$ **Espace probabilisé :** probabilité $$p$$ sur l'univers $$Ω$$.

> **Expérience aléatoire :** expérience dont on ne connait le résultat qu'après l'avoir exécutée, mais dont on connaît toutes les issues.  
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
> 📌$$P(A)∪P(B) = P(A)+P(B)-P(A)∩P(B)$$

> **Événements incompatibles :** $$P(A)∩P(B) = ∅$$

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
Deux événements sont indépendants si la réalisation de l'un n'influence pas la réalisation de l'autre. 
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




## Variables aléatoires

### Fonction de répartition
$$📌x: 
\begin{cases}
ℝ → [0;1] \\
t ↦ F(t)=P(X≤t)
\end{cases}$$

📌$$F(t)=P(X≤t)$$

> **Propriétés :**
> - F est toujours croissante
> - $$\lim_{t→0}F(t)=0$$.
> - $$\lim_{t→∞}F(t)=1$$.

> $$P(a≤X≤b)=P(X≤b)-P(X≤a)=F(b)-F(a)$$
> P(X>a)=1-P(X≤a)=1-F(a)




___
## Variables aléatoires discrètes
Une VAD est une fonction qui associe à chaque résultat d'une expérience aléatoire un entier naturel.
Pour toute VAD $$X$$ :
$$📌x: 
\begin{cases}
Ω → ℕ \\
ωᵢ ↦ x(ωᵢ)=xᵢ
\end{cases}$$ 
___
## Variables aléatoires continues
Une VAC est une fonction qui associe à chaque résultat d'une expérience aléatoire un nombre réel.
Pour toute VAC $$X$$ :
$$📌x: 
\begin{cases}
Ω → \mathbb{R} \\
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
L'espérance représente ce que vaut X en moyenne, après beaucoup de répétitions.

Somme des xᵢ pondérés par leur probabilité.  
📌 $$E(X) = ∑ xᵢ×P(X=xᵢ)$$  

$$E(X+Y)=E(X)+E(Y)$$  
$$E(kX)=kE(X)$$  
$$E(X+a)=E(X)+a$$

#### Variance 
C'est la moyenne des carrés des écarts à l'espérance :   
📌$$V(X) = ∑ (xᵢ-E(X))² P(X=xᵢ)$$  
$$V(X) = ∑ (x² P(X=xᵢ))$$  
$$V(X) = E(X²)-E(X)²$$  
$$V(X) = E[(X-E(X))²]$$

> **Écart-type :** 📌$$σ=\sqrt{V(X)}$$

$$V(X+Y)=V(X)+V(Y)$$  
$$V(kX)=k²V(X)$$  
$$V(X+a)=V(X)$$

#### Différentes lois de probabilité discrètes

|Notation|Nom      |E(X)  |V(X)       |P(X=k)|
|--      |--       |--    |--         |--|
B(p\)     |Bernoulli|$$p$$ |$$p(1-p)$$ |$$kn$$
B(n;p)   |Binomiale|$$np$$|$$np(1-p)$$|$$\binom{n}{k} pᵏ(1-p)ⁿ⁻ᵏ$$
P(λ)     |Poisson  |$$λ$$ |$$λ$$      |$$\frac{e^{-λ}λ^{k}}{k!}$$

- **Loi de Bernoulli :** pour X ne prenant que 2 valeurs. On réalise des expériences de Bernoulli. 
  
|X=xᵢ|0|1|
|--|--|--|
|P(X=xᵢ)|1-p|p|

- **Loi binomiale :** Un ensemble de probabilités suit la loi binomiale **ssi** il forme un **schéma de Bernoulli** (EBRII, Expériences de Bernoulli Répétées, Identiques, Indépendantes).  

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

| Notation | Nom | E(X) | V(X) | FDP f(x) | f(x)⊂ | P(c≤X≤d) |
| -------- | --- | ---- | ---- | -------- | ----- | -------- |
U(a;b)  | Uniforme      | $$\frac{a+b}{2}$$ | $$\frac{(b-a)²}{12}$$ | $$\frac{1}{b-a}$$| $$[a;b]$$  | $$\frac{d-c}{b-a}$$
E(λ)    | Exponentielle | $$\frac{1}{λ}$$   | $$\frac{1}{λ²}$$      | $$λe^{-λx}$$     | $$[a;+∞[$$ | $$e^{-λc}-e^{-λd}$$
N(m;σ²) | Normale       | $$m$$             | $$σ²$$                | $$\frac{e^{-0,5(\frac{x-m}{σ})²}}{σ\sqrt{2\pi}}$$ | ℝ | $$\int_{a}^{b}f(x) \,dx$$
N(0;1)  | Normale Centrée Réduite | $$0$$ | $$1$$ | $$\frac{e^{x²/2}}{\sqrt{2\pi}}$$ | ℝ | $$\int_{a}^{b}f(x) \,dx$$

- **Loi normale centrée réduite :**   
Comme la FDP est paire (symétrique) : $$P(T≤-u) = P(T≥u) = 1-P(T≤u)$$





# Théorèmes limites et Approximations

## Lois d'inégalités
Soit $$X, a ⊂ ℝ^{+}$$
- On ne connait pas la loi de X
- On connaît E(X)

> 📌 Inégalité de Markov :      
> $$P(X≥a) = \frac{E(X)}{a}$$

> 📌 Inégalité de Bienaymé - Tchebychev :  
> $$P(|X-E(X)|≥a) ≤ \frac{V(X)}{a²}$$

## Théorème central limite
Soit n VA ~ L de même espérance.
> Soit $$Y = X_1+...+X_n$$
> Y ~ approx. $$N(m, σ)$$ avec
> - $$E(Y) = n×m$$
> - $$σ(Y) = σ×\sqrt{n}$$

> Soit $$\bar{Y}=\frac{X_1+...+X_n}{n}$$
> Y ~ approx. $$N(m, σ)$$ avec
> - $$E(\bar{X}) = m$$
> - $$σ(\bar{X}) = \frac{σ}{\sqrt{n}}$$

✍️ Il n'y a pas d'approximation quand $$X_i \sim N(M, σ)$$ d'après la stabilité de $$N$$.

## Approximation de Lois
### B par P
La table de $$B$$ n'existe pas pour $$n≥50$$, mais on peu approcher $$B(n, p)$$ par $$P(λ)$$ ssi :
- E et V de $$B(n, p)$$ et $$P(λ)$$ doivent être égales.
- $$λ=n×p$$
- $$λ≤16$$

📌 $$\underset{B(n,p)}{P(X=k)} = \underset{P(n×p)}{P(X=k)}$$  
📌 $$\underset{B(n,p)}{P(a≤X≤b)} = \underset{P(n×p)}{P(a≤X≤b)}$$

✍️ L'approximation est bonne dès que :
- P \< 0,1 
- N ≥ 30
- n×p \< 15

### B par N
On peut décomposer $$X \sim B(n, p)$$ en $$X_i$$ qui suivent la même loi avec :
- $$E(X_i)=p$$
- $$V(X_i)=p(1-p)$$

D'après le théorème central limite, $$X \sim N(n×p, σ)$$

📌 $$P(λ) ≈ N(λ, \sqrt{λ})$$

# Formules

Incompatibilité | $$A∩B=∅$$  

Probabilité | $$P: \begin{cases}Ω → [0,1] \\A ↦ P(A)\end{cases}$$

Probabilités totales | $$P(A)=P(A∩B₁)+P(A∩B₂)+P(A∩B₃)$$  

Équiprobabilité | $$P(A)=\frac{card(A)}{card(Ω)}$$  

Union | $$P(A∩B)=P(A)P(B)-P(A∪B)$$  

Indépendance | $$P(A∩B)=P(A)P(B)$$  

Probabilités composées | $$P(A∩B)=P(A)P_{A}(B)$$  

Variable Aléatoire discrète | $$x: \begin{cases}Ω → ℝ \\ωᵢ ↦ x(ωᵢ)=xᵢ\end{cases}$$   

Espérance | $$Σ(xᵢ) P(X=xᵢ)$$  

Variance | $$E[(X-E(X))²]$$  



# Échantillonnage, Estimation, Intervalle de confiance

Soit une **population** sur laquelle on a une Variable Aléatoire :
- de moyenne $$m$$
- d'écart-type $$σ$$
- de probabilité $$p$$

On suppose :
- La population infinie
- Les tirages sont avec remise

| Paramètre  | Population | Échantillon |
| ---------- | ---------- | ----------- |
| moyenne    | $$m$$      | $$\bar{x}$$ |
| écart-type | $$σ$$      | $$s$$       |
| proportion | $$p$$      | $$f$$       |
| taille     | $$N→∞$$    | $$n≥30$$    |

## Distribution d'échantillonnage de proportion

$$f_1$$ est la proportion d'individus possédant le caractère $$A$$ dans l'échantillon $$i$$.

$${f_1, f_2, ...}$$ est la distribution d'échantillonnage de proportion.

> Y : VA qui associe le nombre d'individus possédant le caractère A à un échantillon donné.
> - loi de Y : $$Y ∼ B(n,p)$$

> F : VA associant $$f_i$$ à chaque $$i$$.
> - lien avec Y : $$F=\frac{Y}{n}$$
> - Loi de F : on approche $$Y ∼ B(n,p)$$ par $$F ∼ N(p, \sqrt{p(1-p)/n}$$
> - Espérance de F : $$E(F) = E(Y/n) = E(Y)/n = p$$
> - Variance de F : $$V(F) = V(Y/n) = V(Y)/n² = \frac{p(1-p)}{n}$$

$${\bar{X_1}, \bar{X_2}, ...}$$ est la distribution d'échantillonnage des moyennes.

> $$\bar{X}$$ est une VA associant $$\bar{X_i}$$ à chaque échantillon $$i$$. $$\bar{X} = \frac{\sum_1^n x_i}{n}$$
> - Loi de $$\bar{X}$$ : d'après le **Théorème central limite**, $$\bar{X} ∼ N(m, σ/\sqrt{n}$$

> $$X_i$$ est une VA qui représente la valeur du $$i^ème$$ tirage.
> - Espérance : $$E(X_i) = ΣE(X)/n = m$$
> - Variance : $$V(X_i) = Σx_i/n² = σ²$$

## Estimation ponctuelle

Estimer la population (m, σ, p) à partir d'un échantillon (\bar{x}, s, f).

> Estimation ponctuelle de la moyenne : $$\hat{m} = \bar{x}$$

> Estimation ponctuelle de l'écart-type : $$\hat{σ} = s×\sqrt{\frac{n}{n-1}}>s$$
> avec $$\frac{n}{n-1}$$ coefficient de biais.

> Estimation ponctuelle de la proportion : $$\hat{p} = f$$

## Estimation par intervalle de confiance

On connaît $$\bar{x}$$ d'un échantillon.

> **Intervalle de confiance :** $$[\bar{x}-a, \bar{x}+a]$$ avec $$a ⊂ \R^+$$.
> Intervalle contenant $$m$$ avec un degré de confiance de 95%.
> $$I_{0,95} = [\bar{x}-\frac{1,96σ}{\sqrt{n}}, \bar{x}+\frac{1,96σ}{\sqrt{n}}]$$

✍️ Si on ne connaît pas σ on peut utiliser $$\hat{σ} = s×\sqrt{\frac{n}{n-1}}>s$$