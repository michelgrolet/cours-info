# Apprenez SQL
SQL est un **langage de définition, de contrôle et de manipulation de données.** Toute entreprise assez développée se sert de bases de données pour stocker ses informations. Le SQL est l'outil par excellence pour traiter la problématique du big data.

## Plan

[Vocabulaire BDD](#vocabulaire)

[Création de tables](#creation_de_table)

*   Types
*   Contraintes
*   Listes
*   Boucles

[Sélection de données](#selection_de_donnees)

*   Select
*   From
*   Where
*   Group by
*   Having
*   Order by

[La sélection en détails](#selection_en_details)

*   Union, intersection et différence
*   Conditions booléennes
*   Jointures
*   All & Any
*   Projections
*   Agrégation
*   Tri
*   Imbrication
*   Fonctions

[La modification de tables](#modification_de_tables)

[Redondance](#redondance)

[PL/SQL](#pl_sql)

*   Itérations
*   Conditionelle
*   Variables Record
*   Curseurs
*   Exceptions
*   Séquences
*   Procédures et fonctions

[Droits et privilèges](#droits_et_privileges)

*   Accorder l'accès à des tables
*   Accorder l'accès à des actions
*   Retirer des droits
*   Rôles prédéfinis

[JDBC](#jdbc)

## Vocabulaire

Voici les termes essentiels à maîtriser pour bien comprendre les bases de données :

|Terme|Définition|
|-- |-- |
|Table|une relation, un tableau. Plusieurs tables forment une base de données.|
|Tuple|ligne unique d'une table.|
|Attribut|titre d’une colonne.|
|Schéma|ensemble des attributs d'une table.|
|Domaine|Type des données d’une colonne.|
|Clé|groupe d’attributs permettant de sélectionner un seul tuple.|
|Clé primaire|clé contenant le moins d'attributs (la plus simple).|
|Clé étrangère|attribut liant deux tables.|
|Table d’association|contient au moins deux clés étrangères de tables qu’elle lie.|


## Création de tables
Pour créer une table à partir de rien :
```sql
CREATE TABLE x (  
 nomColonne type contraintes,  
 nomColonne type contraintes  
 );
```
Pour créer une table à partir d'une [sélection](#select) :
```sql
CREATE TABLE x AS SELECT…```
```

### Types
|Nom|Type SQL|
|-- |-- |
|Nombre|number(size)|
|Chaîne|varchar(size)|
|Binaire|varbinary(size)|
|Blob (grands binaires, comme des images)|blob(size)|
|Date (format YYYY-MM-DD)|date|


### Contraintes
Elles servent à réguler ce qu'une colonne peut contenir.
|Contrainte|Description|
|-- |-- |
|not null|interdit les valeurs nulles|
|unique|interdit les valeurs similaires|
|primary key|la colonne est une [clé primaire](#pk).|
|foreign key|la colonne est une [clé étrangère](#sk).|
|check(condition)|les valeurs doivent remplir une [condition](#condition).|


## Sélectionner des données

Maintenant qu'on sait créer des données, apprenons à les sélectionner :

```sql
select colonnes  
from tables  
where condition  
group by  
having  
order by colonnes
```
### Select

dans le select, on met des nom de colonnes séparés par des virgules.

Pour sélectionner avec plus de précision, un utilise les [projections](#projections).

### From

Dans le from, on met le nom de la table contenant les colonnes sélectionnées. Pour des colonnes venant de plusieurs tables, on utilise les [jointures](#join).

### Where

Dans le where, om met une [condition](#condition) qui filtre les lignes.

Pour les égalités et inégalités entre des **ensembles de lignes**, on utilise [all et any](#all-any).

### Group by

La clause GROUP BYproduit une ligne résultat pour chaque groupede lignes.

Un **groupe** est un ensemble de lignes qui ont même valeur pour les attributs sur lesquels le regroupement est construit.

### Having

Dans le having, on met une condition devant être vérifiée par le groupe.

### Order by

Dans le order by, on met les noms des colonnes sur lesquelles le tri doit être fait.

On peut ajouter le mot-clé `desc` qui trie les valeurs dans le sens inverse (décroissant pour des nombres, inverse de l'alphabet pour des chaines, du plus récent au plus vieux pour les dates...)

## La sélection en détails

### Union, intersection et différence

#### Union

L'union combine le résultat de deux sélections :

```sql
select x from y  
union  
select x from z```
```
#### Intersection

L'intersection renvoie ce qui est commun entre les renvois de deux sélections :

```sql
select x from y  
intersect  
select x from z```
```

#### différence

La différence renvoie le renvoi d'une sélection auquel on a retiré le renvoi d'une seconde sélection :

```sql
select x from y  
minus  
select x from z
```

### Conditions booléennes

Voici les opérateurs disponible en SQL pour construire des conditions :

|Condition|Description|
|-- |-- |
|a = b|a égal b|
|a >< b|a supérieur/inférieur à b|
|a like 'chaîne de caractères'|Jokers : **%** remplace n caractères et **_** en remplace un.|
|a is null|a n'a pas de valeur|
|or, and, not|Ou, et, non|
|a between b and c|a est compris entre b et c|
|a in (b1,b2,b3,...)|a est dans la liste (b1,b2,b3,...)|


### Jointures

Les jointures, c'est associer plusieurs tables dans un `select` pour faire des sélections sur l'ensemble.

Jointure interne : association entre 2 tables par 2 colonnes correspondantes.

`inner join x on ...`

Jointure externe : à droite ou à gauche, conservation des lignes qui n’ont pas de correspondance.

`left outer x join on ...`

Jointure interne : à droite et à gauche.

`outer x join on ...`

Jointure naturelle : choix automatique entre les 2 colonnes.

`natural join x`

### All & Any

#### All

```
where x > all(y)
Le x doit être au dessus de **tout** ce que contient le y.
```

#### Any

```
where x = any(y)
```

Le x doit être au dessus d'**une ligne** du y.

### Projections

On peut appliquer des [fonctions](#fonctions) sur des colonnes.

`Select abs(id*2)`

On peut ajouter `as` pour renommer une colonne, et appliquer des fonctions liées aux chaînes de caractères.

`Select name || ‘(‘ || status || ‘)’ as name_and_status`

On peut aussi appliquer des fonctions de booléens.

`Select CURRENT_DATE() > incorporation_date`

### Agrégation

#### Partitionnement

On fait un partitionnement sur une ou plusieurs colonnes. Ce partitionnement groupe les lignes qui ont la même valeur pour les colonnes sélectionnées. Chacun de ces groupes est appelé agrégat.

`Group by colonneY, colonneZ …`

#### Fonction d’agrégation

Cette fonction prend chaque agrégat et renvoie 1 unique valeur.

`Select count(*) from x`

Dans le select, on peut trouver soit des colonnes qui résultent d’une fonction d’agrégation, soit des colonnes qui sont dans le group by.

#### Restriction sur une agrégation

Having fonction d’agrégation comme `count(*)`

### Tri

```sql
order by x, y
```

Ajouter desc pour trier dans l’ordre décroissant.

### Imbrication

Z doit se trouver dans la sous-requête :

`Select x from y where z in ( Select … )`

Toutes les valeurs de la sous-requête doivent être inférieures à z :

`Select x from y where z > all ( Select … )`

Une des valeurs de la sous-requête doivent être inférieures à z :

`Select x from y where z > any ( Select … )`

La sous-requête doit contenir au moins une ligne :

`Select x from y where exists ( Select … )`

### Fonctions

|Description|Fonction SQL|
|-- |-- |
|Valeur absolue|ABS(a)|
|Exponentielle|EXP(a)|
|Plus petit entier supérieur ou égal|CEIL(a)|
|Plus grand entier inférieur ou égal|FLOOR(a)|
|Modulo|MOD(a,b)|
|Puissance|POWER(a,b)|
|Arrondi à b décimales|ROUND(a[,b])|
|Troncature à b décimales|TRUNC(a[,b])|
|Concaténation|CONCAT(a,b)|
|Première lettre des mots en maj|INITCAP(a)|
|Tout en minuscule|LOWER(a)|
|Remplace b par c dans a|REPLACE(a,b[,c])|
|Renvoie une portion d’une chaîne|SUBSTR(indiceDebut, nombreDeChar)|
|Convertit en entier|to_number()|
|Convertit en chaîne|to_string(date, 'YYYY')|
|Convertit en date|to_date(aConvertir, 'YYYY/MM/DD')|


## Modification de tables

```sql
Alter table  
{  
 ADD () | --pour ajouter un colonne  
 MODIFY () |  
 DROP () |  
 RENAME TO x  
}
```

`Insert into` : ajouter qqch dans une table  
`Commit` : valider les insertions/MAJ/suppressions  
`Rollback` : annule jusqu'au dernier commit

Il existe 4 opérateurs en algèbre relationnelle :
*   Union
*   Différence
*   Intersection
*   Produit Cartésien

## Redondance

Pour éviter la redondance, il faut diviser les tables. Tous les attributs « en double » peuvent être déplacés dans une nouvelle table.

## PL/SQL

PL/SQL est une extension de SQL qui permet de faire de la programmation avec des requêtes SQL.

Fonctionnement avec des scripts stockés sur le client, ou des fonctions stockées sur le serveur.

```sql
DECLARE ... --Lexique  
BEGIN ... --Instructions  
[EXCEPTION ... --Erreurs]  
END;
```

Types :
*   `BOOLEAN`
*   `BINARY_INTEGER`
*   `NATURAL`
*   `POSITIVE` (natural sans 0)
*   `nom colonne%rowtype` (type d'une col de la BDD)

Instructions (entre begin et end) :
*   Affectation d'une valeur à une variable avec `:=`
*   SQL

### Itérations

*   `LOOP ... EXIT WHEN ... END LOOP;`
*   `WHILE ... LOOP ... END LOOP;`
*   `FOR ... IN ... LOOP ... END LOOP;`

### Conditionelle

#### Fermeture

```sql
IF ... THEN  
  {...}  
ELSIF ... THEN  
  {...}  
ELSE  
  {...}  
END IF;
```

### Variables Record

```sql
DECLARE  
TYPE maVarComposee IS RECORD (  
  champ type [not null] [val par defaut]  
);
```

### Curseurs

Ils permettent de gérer les requêtes qui renvoient plusieurs lignes, en parcourant les lignes unes par unes.

#### Déclaration (dans le DECLARE)

```sql
CURSOR nomCurseur IS SELECT ... ;
```

#### Ouverture (Dans le BEGIN)

```
OPEN nomCurseur;```

#### Chargement d'une ligne

```



FETCH nomCurseur INTO v1, v2, ...;```

#### Fermeture

```



CLOSE nomCurseur;```

### Exceptions

```



WHEN nom_exception THEN instructions```

#### Exceptions prédéfinies

<table>

<tbody>

<tr>

<td>`DUP_VAL_ON_INDEX</td>

<td>Deux fois la même valeur dans une colonne contrainte à un index unique.</td>

</tr>

<tr>

<td>`NO_DATA_FOUND</td>

<td>Le SELECT ne renvoie rien.</td>

</tr>

<tr>

<td>`TOO_MANY_ROWS</td>

<td>SELECT renvoie plus d'une ligne dans un into.</td>

</tr>

<tr>

<td>`INVALID_NUMBER</td>

<td>Nombre invalide.</td>

</tr>

<tr>

<td>`VALUE_ERROR</td>

<td>Erreur de troncature ou de conversion.</td>

</tr>

</tbody>

</table>

#### Exception OTHERS

```



WHEN OTHERS THEN dbms_output.put_line('erreur: '||SQLCODE||SQLERRM);```

#### Erreurs applicatives

Elles ne sont pas liées à l'exécution du programme mais à sa logique.

##### Déclaration

`nom_exception EXCEPTION;

##### Déclenchement

`IF ... THEN RAISE nom_exception; END IF;

##### Traitement

`WHEN nom_exception THEN dbms_output.put_line('erreur: description');

### Séquences

Génération d'une suite d'entiers.

```



CREATE SEQUENCE seq START WITH ... INCREMENT BY ...;  
SELECT seq.nextval FROM dual;  
SELECT seq.currval FROM dual;```

*   Currval ne s'appelle qu'après nextval.
*   Nextval génère la même valeur pour une même ligne.

### Procédures et fonctions

Procédure : fonction sans retour.

#### Déclarées ou stockées ?

*   Déclarée : contenue dans un script PL/SQL et utilisables seulement dedans.
*   Stockées : sur le serveur, accessibles par tout programme.

#### Déclaration

```



[DECLARE/CREATE] _OR REPLACE_ [FUNCTION/PROCEDURE f_fonc(p_param TYPE) _RETURN TYPE IS v_var TYPE(taille)_;  
BEGIN ...  
EXCEPT ...  
END;  
_DROP PROCEDURE nom; -- si stockée_```

On ne spécifie pas la taille des paramètres.

Les paramètres des procédures peuvent être définis comme IN, OUT, ou IN OUT.

## Droits et privilèges

### Accorder l'accès à des tables

```



GRANT privilege ON table/vue TO utilisateur/rôle/public [WITH GRANT OPTION]```

PUBLIC permet d'accorder les privilèges à tous les utilisateurs.

All à la place de table/vue permet d'accorder l'accès avec tous les privilèges à toutes les données.

### Accorder l'accès à des actions

```



GRANT privilege TO utilisateurs [WITH GRANT OPTION]```

### Retirer des droits

```



GRANT [WITH GRANT OPTION]```

### Rôles prédéfinis

## JDBC

<div class="exemple">Attention :  
JDBC est une API de Java qui permet d'interagir avec des bases de données en SQL ! il est donc nécessaire de maîtriser le langage Java pour suivre cette partie. Pour cela, rien de plus simple : allez voir [mon cours](article6).

Étapes de JDBC :

*   Connexion à la base de données
*   Envoi des requêtes SQL
*   Traitement des résultats

```

### Connexion

```

<div class="lang">Java```

// Connexion de "nom" à la BDD oracle "sid" tournant sur "host" à travers le port 1521  
Connnexion connexionBdd=DriverManager.getConnexion(url, "nom", "mdp");  
String url="jdbc:oracle:thin:@host:1521:sid";```

### Requêtes

```

<div class="lang">Java```

// Création :  
Statement statementSql=connexionBdd.createStatement();  
// Exécution :  
ResultSet resultat=statementSql.executeQuery("SELECT...");  
ResultSet resultat=statementSql.executeUpdate("UPDATE... - INSERT... - DELETE...");  

connexionBdd.close();  
statementSql.close();  
resultat.close();```

### Requêtes préparées

```

<div class="lang">Java```

PreparedStatement ps=connexionBdd.prepareStatement("SELECT * FROM x WHERE y=**?**");  
ResultSet resultat=ps.executeQuery();  
// on passe ensuite un paramètre dans le ? :  
ps.setInt(1, 1000); // valeur 1000 au premier "?" de "ps"  
ps.close();```

Il existe des setters pour tous les types.

### Actions sur les resultSet

#### Si le résultat ne contient qu'une ligne

On interagit avec les resultSet par l'intermédiaire des getters auquels on fournit la colonne qui nous intéresse afin de parcourir le résultat de la requête :

```

<div class="lang">Java```

String colonne1=monResultSet.getString("colonne1");```

#### Si le résultat contient plusieurs lignes

On passe d'une ligne à la suivante avec `**monResultSet.next()** (à utiliser avec un while).

### Accès aux métadonnées d'un resultSet

*   `r.getColumnCount()
*   `r.getColumnTypeName(numColonne)
*   `r.getColumnName(numColonne)