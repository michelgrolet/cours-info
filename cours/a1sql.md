# SQL / PLSQL / JDBC
SQL est un **langage de définition, de contrôle et de manipulation de données.** Toute entreprise assez développée se sert de bases de données pour stocker ses informations. Le SQL est l'outil par excellence pour traiter la problématique du big data.

<details>
<summary> Plan ✨</summary>

- [SQL / PLSQL / JDBC](#sql--plsql--jdbc)
	- [Vocabulaire](#vocabulaire)
	- [Création de tables](#création-de-tables)
		- [Types](#types)
		- [Contraintes](#contraintes)
	- [Sélectionner des données](#sélectionner-des-données)
		- [SELECT](#select)
		- [FROM](#from)
		- [WHERE](#where)
		- [GROUP BY](#group-by)
		- [Having](#having)
		- [Order by](#order-by)
	- [La sélection en détails](#la-sélection-en-détails)
		- [Union, intersection et différence](#union-intersection-et-différence)
			- [Union](#union)
			- [Intersection](#intersection)
			- [Différence](#différence)
		- [Conditions booléennes](#conditions-booléennes)
		- [Jointures](#jointures)
		- [All & Any](#all--any)
			- [All](#all)
			- [Any](#any)
		- [Projections](#projections)
		- [Agrégation](#agrégation)
			- [Partitionnement](#partitionnement)
			- [Fonction d’agrégation](#fonction-dagrégation)
			- [Restriction sur une agrégation](#restriction-sur-une-agrégation)
		- [Tri](#tri)
		- [Imbrication](#imbrication)
		- [Fonctions](#fonctions)
	- [Modification de tables](#modification-de-tables)
	- [Redondance](#redondance)
	- [PL/SQL](#plsql)
		- [Itérations](#itérations)
		- [Conditionelle](#conditionelle)
			- [Fermeture](#fermeture)
		- [Variables Record](#variables-record)
		- [Curseurs](#curseurs)
			- [Déclaration (dans le DECLARE)](#déclaration-dans-le-declare)
			- [Ouverture (Dans le BEGIN)](#ouverture-dans-le-begin)
			- [Chargement d'une ligne](#chargement-dune-ligne)
			- [Fermeture](#fermeture-1)
		- [Exceptions](#exceptions)
			- [Exceptions prédéfinies](#exceptions-prédéfinies)
			- [Exception OTHERS](#exception-others)
			- [Erreurs applicatives](#erreurs-applicatives)
				- [Déclaration](#déclaration)
				- [Déclenchement](#déclenchement)
				- [Traitement](#traitement)
		- [Séquences](#séquences)
		- [Procédures et fonctions](#procédures-et-fonctions)
			- [Déclarées ou stockées ?](#déclarées-ou-stockées-)
			- [Déclaration](#déclaration-1)
	- [Droits et privilèges](#droits-et-privilèges)
		- [Accorder l'accès à des tables](#accorder-laccès-à-des-tables)
		- [Accorder l'accès à des actions](#accorder-laccès-à-des-actions)
		- [Retirer des droits](#retirer-des-droits)
	- [JDBC](#jdbc)
	- [Connection](#connection)
	- [Création d'un Statement](#création-dun-statement)
			- [Statement](#statement)
			- [PreparedStatement](#preparedstatement)
			- [CallableStatement](#callablestatement)
	- [Exécution d'un Statement](#exécution-dun-statement)
			- [consultation - SELECT](#consultation---select)
			- [modification - INSERT, UPDATE, DELETE, CREATE, DROP](#modification---insert-update-delete-create-drop)
	- [Traitement des données retournées dans un ResultSet](#traitement-des-données-retournées-dans-un-resultset)
		- [Actions sur les resultSet](#actions-sur-les-resultset)
			- [Si le résultat ne contient qu'une ligne](#si-le-résultat-ne-contient-quune-ligne)
			- [Si le résultat contient plusieurs lignes](#si-le-résultat-contient-plusieurs-lignes)
		- [Accès aux métadonnées d'un resultSet](#accès-aux-métadonnées-dun-resultset)
</details>

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
Pour créer une table à partir d'une [sélection](#SELECT) :
```sql
CREATE TABLE x AS SELECT…
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
SELECT colonnes  
FROM tables  
WHERE condition  
GROUP BY  
having  
order by colonnes
```
### SELECT

dans le SELECT, on met des nom de colonnes séparés par des virgules.

Pour sélectionner avec plus de précision, un utilise les [projections](#projections).

### FROM

Dans le FROM, on met le nom de la table contenant les colonnes sélectionnées. Pour des colonnes venant de plusieurs tables, on utilise les [jointures](#join).

### WHERE

Dans le WHERE, om met une [condition](#condition) qui filtre les lignes.

Pour les égalités et inégalités entre des **ensembles de lignes**, on utilise [all et any](#all-any).

### GROUP BY

La clause `GROUP BY` produit une ligne résultat pour chaque groupede lignes.

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
SELECT x FROM y  
union  
SELECT x FROM z
```
#### Intersection

L'intersection renvoie ce qui est commun entre les renvois de deux sélections :

```sql
SELECT x FROM y  
intersect  
SELECT x FROM z
```

#### Différence

La différence renvoie le renvoi d'une sélection auquel on a retiré le renvoi d'une seconde sélection :

```sql
SELECT x FROM y  
minus  
SELECT x FROM z
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

Les jointures, c'est associer plusieurs tables dans un `SELECT` pour faire des sélections sur l'ensemble.

Jointure interne : association entre 2 tables par 2 colonnes correspondantes.

`inner join x on ...`

Jointure externe : à droite ou à gauche, conservation des lignes qui n’ont pas de correspondance.

`left outer x join on ...`

Jointure interne : à droite et à gauche.

`outer x join on ...`

Jointure naturelle : choix automatique des 2 colonnes.

`natural join x`

### All & Any

#### All

```sql
WHERE x > all(y)
```
Le x doit être au dessus de **tout** ce que contient le y.


#### Any

```sql
WHERE x = any(y)
```

Le x doit être au dessus d'**une ligne** du y.

### Projections

On peut appliquer des [fonctions](#fonctions) sur des colonnes.

`SELECT abs(id*2)`

On peut ajouter `as` pour renommer une colonne, et appliquer des fonctions liées aux chaînes de caractères.

`SELECT name || ‘(‘ || status || ‘)’ as name_and_status`

On peut aussi appliquer des fonctions de booléens.

`SELECT CURRENT_DATE() > incorporation_date`

### Agrégation

#### Partitionnement

On fait un partitionnement sur une ou plusieurs colonnes. Ce partitionnement groupe les lignes qui ont la même valeur pour les colonnes sélectionnées. Chacun de ces groupes est appelé agrégat.

`GROUP BY colonneY, colonneZ …`

#### Fonction d’agrégation

Cette fonction prend chaque agrégat et renvoie 1 unique valeur.

`SELECT count(*) FROM x`

Dans le SELECT, on peut trouver soit des colonnes qui résultent d’une fonction d’agrégation, soit des colonnes qui sont dans le GROUP BY.

#### Restriction sur une agrégation

Having fonction d’agrégation comme `count(*)`

### Tri

```sql
order by x, y
```

Ajouter desc pour trier dans l’ordre décroissant.

### Imbrication

Z doit se trouver dans la sous-requête :

`SELECT x FROM y WHERE z in ( SELECT … )`

Toutes les valeurs de la sous-requête doivent être inférieures à z :

`SELECT x FROM y WHERE z > all ( SELECT … )`

Une des valeurs de la sous-requête doivent être inférieures à z :

`SELECT x FROM y WHERE z > any ( SELECT … )`

La sous-requête doit contenir au moins une ligne :

`SELECT x FROM y WHERE exists ( SELECT … )`

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









___
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

```sql
OPEN nomCurseur;
```

#### Chargement d'une ligne

```sql
FETCH nomCurseur INTO v1, v2, ...;
```

#### Fermeture

```sql
CLOSE nomCurseur;
```

### Exceptions

```sql
WHEN nom_exception THEN instructions
```

#### Exceptions prédéfinies

|Exception SQL|Description|
|-- |-- |
|`DUP_VAL_ON_INDEX`|Deux fois la même valeur dans une colonne contrainte à un index unique.|
|`NO_DATA_FOUND`|Le SELECT ne renvoie rien.|
|`TOO_MANY_ROWS`|SELECT renvoie plus d'une ligne dans un into.|
|`INVALID_NUMBER`|Nombre invalide.|
|`VALUE_ERROR`|Erreur de troncature ou de conversion.|


#### Exception OTHERS

```sql
WHEN OTHERS THEN dbms_output.put_line('erreur: '||SQLCODE||SQLERRM);
```

#### Erreurs applicatives

Elles ne sont pas liées à l'exécution du programme mais à sa logique.

##### Déclaration

`nom_exception EXCEPTION;`

##### Déclenchement

`IF ... THEN RAISE nom_exception; END IF;`

##### Traitement

`WHEN nom_exception THEN dbms_output.put_line('erreur: description');`

### Séquences

Génération d'une suite d'entiers.

```sql
CREATE SEQUENCE seq START WITH ... INCREMENT BY ...;  
SELECT seq.nextval FROM dual;  
SELECT seq.currval FROM dual;
```

*   Currval ne s'appelle qu'après nextval.
*   Nextval génère la même valeur pour une même ligne.

### Procédures et fonctions

Procédure : fonction sans retour.

#### Déclarées ou stockées ?

*   Déclarée : contenue dans un script PL/SQL et utilisables seulement dedans.
*   Stockées : sur le serveur, accessibles par tout programme.

#### Déclaration

```sql
[DECLARE/CREATE] _OR REPLACE_ [FUNCTION/PROCEDURE f_fonc(p_param TYPE) _RETURN TYPE IS v_var TYPE(taille)_;  
BEGIN ...  
EXCEPT ...  
END;  
DROP PROCEDURE nom; -- si stockée
```

On ne spécifie pas la taille des paramètres.

Les paramètres des procédures peuvent être définis comme `IN`, `OUT`, ou `IN OUT`.





___
## Droits et privilèges

### Accorder l'accès à des tables

```sql
GRANT privilege ON table/vue TO utilisateur/rôle/public [WITH GRANT OPTION]
```

`PUBLIC` permet d'accorder les privilèges à tous les utilisateurs.

`All` à la place de table/vue permet d'accorder l'accès avec tous les privilèges à toutes les données.

### Accorder l'accès à des actions

```sql
GRANT privilege TO utilisateurs [WITH GRANT OPTION]
```

### Retirer des droits

```sql
GRANT [WITH GRANT OPTION]
```













___
## JDBC

Librairie Java (`java.sql`) permettant un accès homogène à toute catégorie de base de donnée.  
✍🏻 Homogénéité grâce à des drivers propres à chaque SGBD (oracle, access, sqlite...) qui convertissent les requêtes JDBC dans le dialecte SQL du SGBD. Tout ce qui concerne le SQL est géré par le driver. Une erreur à ce niveau va lever une `SQLException`.

Interfaces JDBC     | Description
--                  |--
`Driver`            | renvoie une instance de Connection
`Connection`        | connection à une BDD
`Statement`         | instruction SQL
`PreparedStatement` | instruction SQL paramétrée
`CallableStatement` | procédure stockée dans la BDD
`ResultSet`         | tuples récupérés par une instruction SQL
`ResultSetMetadata` | description des tuples récupérés
`DatabaseMetadata`  | informations sur la BDD

Classes JDBC        | Description
--                  |--
DriverManager       | gère les drivers
Date                | date SQL
Time                | heures, minutes, secondes SQL
TimeStamp           | timestamp SQL
Types               | désigne les types SQL



```java
// Importer le package JDBC
import java.sql.*;

// Enregistrer le driver
Class.forName("oracle.jdbc.driver.OracleDriver")
// ou
Class.forName("driverName").newInstance();

// Connection à la BDD
String url="jdbc:oracle:thin:@host:1521:sid";
Connnexion connectionBdd=DriverManager.getConnection(url, "nom", "mdp");

// Gestion des commits
connectionBdd.setAutoCommit(false); // pour désactiver les commit auto.
connectionBdd.commit();
connectionBdd.rollback();

// Création d'une requête
Statement statementSql=connectionBdd.createStatement();  

// Exécution
ResultSet resultat=statementSql.executeQuery("SELECT...");  
ResultSet resultat=statementSql.executeUpdate("UPDATE... - INSERT... - DELETE...");

// Traitement des données
// TODO

// Fermer la connection
connectionBdd.close();  
statementSql.close();  
resultat.close();
```
✍🏻 Pendant la connection, le `DriverManager` essaye tous les drivers chargés en mémoire avec `Class.forName()` jusqu'à qu'il réussisse à se connecter.


___
## Connection
✍🏻 On ne peux pas réutiliser une connection dans plusieurs threads. A la place des threads on peut utiliser `java.lang.ThreadLocal`.

> Connection à la base de l'IUT :  
> `jdbc:oracle:thin:@charlemagne.iutnc.univ-lorraine.fr:1521:infodb`


___
## Création d'un Statement

#### Statement
```java
Statement req = connection.createStatement();
```

#### PreparedStatement
```java
PreparedStatement req = connection.prepareStatement("SELECT * FROM x WHERE y=**?**");  
ResultSet resultat=ps.executeQuery();  
// on passe ensuite un paramètre dans le ? :  
ps.setInt(1, 1000); // valeur 1000 au premier "?" de "ps"  
ps.close();
```
Il existe des setters pour tous les types.

#### CallableStatement
```java
CallableStatement req = connection.prepareCall("{? = call nomProcedure(?,?)}");
```
Le premier `?`, optionnel, correspond au retour de la procédure.






___
## Exécution d'un Statement

#### consultation - SELECT
```java
ResultSet res = req.executeQuery("SELECT ..."); // return ResultSet
```


#### modification - INSERT, UPDATE, DELETE, CREATE, DROP
```java
int tuplesAffectes = req.executeUpdate("INSERT INTO ..."); // return int : nombre de tuples affectés
```





___
## Traitement des données retournées dans un ResultSet
Si on a fait un `SELECT`, on récupère un `ResultSet` qu'il va falloir lire :
```java
// Parcours d'un ResultSet
while(rs.next()) {
	int c = rs.getInt("col1"); // c prends le "col1" du tuple courant.
	int d = rs.getInt(2); // d prends la valeur de la colonne 2 du tuple courant.
	if (rs.wasNull()){} // on peut faire des actions si la dernière donnée lue était nulle. 
	rs.previous(); // reviens au tuple précédent.
	rs.absolute(2); // va au tuple 2.
	rs.relative(2); // va au 2e tuple avant le tuple courant.
	rs.first(); // va au premier tuple.
}
```

### Actions sur les resultSet

#### Si le résultat ne contient qu'une ligne

On interagit avec les `resultSet` par l'intermédiaire des getters auquels on fournit la colonne qui nous intéresse afin de parcourir le résultat de la requête :

```java
String colonne1=monResultSet.getString("colonne1");
```

#### Si le résultat contient plusieurs lignes

On passe d'une ligne à la suivante avec `monResultSet.next()` (à utiliser avec un while).

### Accès aux métadonnées d'un resultSet

*   `r.getColumnCount()`
*   `r.getColumnTypeName(numColonne)`
*   `r.getColumnName(numColonne)`