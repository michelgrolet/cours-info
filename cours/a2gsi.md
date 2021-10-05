# Gestion des Systèmes d'information

## Structure du cours
- Projet informatique : répond à un besoin intégré à un process formel
- SS2I :centres de coûts qui doivent être rentabilisés → **Calcul des seuils de rentabilité**
- Environnement global technologique → **Cloud, Big data**

# Processus et ERP

> Processus : moyens et activités connexes qui transforment des éléments entrants en éléments sortants sous contrainte interne.

Un processus doit générer de la **valeur ajoutée**.

- Réponds à un besoin.
- Orienté client.
- Transversal entre les services de l'entreprise.

| Catégorie de processus | Description                                       | Exemples                           |
| ---------------------- | ------------------------------------------------- | ---------------------------------- |
| Métier                 | Réaliser les services et produits de l'entreprise | opération, conception, fabrication |
| Support                | Fournit les ressources                            | ressource, formation, logistique   |
| Transversal            | Gèrent les autres processus                       | stratégie, décisions, évaluations  |

> **Étapes du processus métier**  
> 1. Prise d'informations sur le prospect (client potentiel)
> 1. Production du bon de commande
> 1. Production du bon de livraison
> 1. Retour du bon de livraison
> 1. Émission d'une facture
> 1. Réception du réglement et d'un reçu

> **Parties du processus support**
> - Fonction achat : besoins, fournisseurs, études d'offres, contrats, pilotage
> - Fonction approvisionnement : demande, commande, paiment, mesure de performance.

# ERP - PGI

> ERP : Enterprise ressource planning
> PGI : Progiciel de gestion intégrée

> **Progiciel :** Logiciel applicatif générique, multifonctions, paramétrable.

Caractéristique d'un ERP :
- Application modulaire, modules indépendants mais compatibles.
- Partage d'une base de données commune.

Un ERP permet d'homogénéiser le Système d'information d'une entreprise, pour :
- achats
- ventes
- comptabilité
- gestion
- production
- stocks

Un ERP garantit la **piste d'audit :** on peut retrouver l'origine de chaque information.

Les tendances actuelles des ERP :
- Cloud computing
- BYOD (bring your own device)
- UI personnalisable
- Explosion des DBI pour tous (Data Business Intelligence)
- Dématerialisation

___
# Calculer des seuils de rentabilité - méthode des coûts partiels
On distingue les charges variables des charges fixes.


> **Charge fixe :** indépendante du niveau d'activité de l'entreprise, pour un palier donné.
> Exemple : le loyer tant qu'il ne faut pas louer un deuxième batiment.

> **Charge variable :** varient proportionellement au niveau d'activité.   
> Exemple : les amortissements, l'achat de matières, la consommation d'énergie en industrie

> **Charges semi-variables :** réparties en charges fixes et variables avant d'être traitées.   
> Exemple : les charges de personnel

## Compte de résultat différentiel

> **Chiffre d'affaire :** Total des ventes. $$CA=Charges Variables + Charges Fixes + Résultat$$

> **Résultat =** $$C.A.-Σ charges$$.

Comtpe de résultat différentiel :

|                           | Montant | Taux |
| ------------------------- | ------- | ---- |
| CA                        |         | 100% |
| - charges variable        |         | 56%  |
| = marge sur coût variable |         | 45%  |
| - charges fixes           |         |      |
| = Resultat                |         |      |

Taux de marge sur coût variable : $$= \frac{MCV}{CA}×100$$ 

avec $$MCV = CA - CV$$

> ✍️ Dans l'industrie, on veut maximiser la MCV. Dans le tertiaire (services) on a beaucoup de charges fixes. **La méthode des coûts partiels pert de sa pertinence.**

## Seuil de rentabilité


|             | CA   | CV  | CF  | Résultat |
| ----------- | ---- | --- | --- | -------- |
| hypothèse 1 | 100k | 60k | 30k | 10k      |
| hypothèse 2 | 75k  | 45k | 30k | 0        |
| hypothèse 3 | 50k  | 30k | 30k | -10k     |

Permet de savoir quel CA il faut avoir pour dégager un résultat positif.

> **Seuil de rentabilité :** CA pour lequel l'entreprise couvre la totalité de ses charges et dégage un résulat nul.  (=CA critique, =point mort)  
> SR en valeur : $$SR\ val=\frac{CF\ nettes}{Taux\ MCV}$$
> SR en quantités : $$SR\ q=\frac{SR\ val}{Prix\ unitaire}=\frac{Charges\ fixes\ nettes}{Marge\ sur\ CVU}$$

> **Point mort :** jour ou mois auquel le SR est atteint.  
> Nombre de mois pour atteindre le SR : $$=\frac{SR\ val}{CA\ mensuel}$$