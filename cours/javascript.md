# JavaScript

JavaScript est un langage de programmation interprété, orienté web et utilisateur (par le navigateur) et syntaxiquement libre. Il est responsable de la partie animée et vivante du Web. Certains critiquent la trop grande liberté qu'il nous donne (en dépit de son efficacité moindre à C par exemple) mais personellement je trouve cela très agréable.

## Bases

### Variables

Il y a deux façons de déclarer des variables :

* **var** : portée globale
* **let** : portée du scope

Note : le hoisting (remontée) fait que JS remonte toutes les déclarations en haut de fichier avant d'exécuter.

### Types

les types sont déterminés automatiquement par JavaScript. En général on n'a pas besoin de les manier. En cas de besoin, on accède au type avec la fonction typeof().

Voici la liste des types principaux :

* boolean
* number (flottants)
* string

Voici la liste des valeurs par défaut :

* undefined
* null
* NaN (not a number)
* infinity

#### String

Voici quelques méthodes associées des string :

* .length
* .toUpperCase()
* .toLowerCase()

Les string peuvent s'écrire entre " ou ' ou `. L'avantage de la dernière forme est de faciliter la concaténation.

<div class="code">

<div class="lang">JS</div>

let var=`lorem ${varIpsum}`;</div>

### Affichage

<div class="code">

<div class="lang">JS</div>

document.write("lorem ipsum"); // sur la page  
console.log("lorem ipsum"); // dans la console</div>

### Objets

Objets classiques : <span class="code">let obj = {var:val,var2:val2, func(){}, ...}</span>

Tableaux : <span class="code">[1,2,3]</span>

### Fonctions natives

#### Math

* .random()
* .ceil()

#### window

* .alert()
* .prompt()
* .confirm()

#### document

* write()

### Boucles

#### Foreach

<div class="code">

<div class="lang">JS</div>

monTab.forEach( i => { /*commandes utilisant i*/ } )</div>

## Accès au DOM

On accède à la page par l'objet<span class="code">document</span>.

#### accès à des id, class ou sélecteurs css

* La méthode <span class="code">getElementById()</span>prends en paramètre un id et le retourne si il existe.
* La méthode <span class="code">getElementByClassName()</span>prends en paramètre un nom de classe et retourne un array des occurences de cette classe.
* La méthode <span class="code">getElementByTagName()</span>prends en paramètre un nom de balise et retourne un array des occurences de cette balise.
* La méthode <span class="code">querySelector()</span>prends en paramètre un sélecteur similaire aux css et retourne le premier, ou retourne null.
* La méthode <span class="code">querySelectorAll()</span>prends en paramètre un sélecteur similaire aux css et retourne un array des occurences de ce sélecteur, ou retourne null.

#### Accès aux relatifs d'un élément

* <span class="code">children</span>
* <span class="code">parentElement</span>
* <span class="code">nextElementSibling</span>
* <span class="code">previousElementSibling</span>

## Modification du DOM

#### Modifiez le contenu d'un élément

* <span class="code">innerHTML</span>: Permet d'insérer du HTML dans l'élément.
* <span class="code">textContent</span>Permet d'insérer du texte dans l'élément.

#### Modifier des classes

* <span class="code">classList.add("c,...")</span>: ajoute la classe c à l'élément.
* <span class="code">classList.remove("c,...")</span>: supprime la classe c.
* <span class="code">classList.toggle(c) : inverse l'état de la classe c.</span>
* <span class="code">classList.contains("c")</span>: renvoie un booléen en fonction de la présence de la classe c dans l'élément.
* <span class="code">classList.replace("c1,c2")</span>: remplace c1 par c2.

#### Modifier le style

On utilise <span class="code">style.nomDeLaProprieteCSS</span>

#### Modifier les attributs

* <span class="code">setAttribute(attribut,valeur)</span>: ajoute un nouvel attribut ou change la valeur d'un attribut existant pour l'élément spécifié.
* <span class="code">getAttribute(attribut)</span>: retourne la valeur de l'attribut spécifié.
* <span class="code">removeAttribute(attribut)</span>: supprime l'attribut spécifié.

#### Créer des éléments

On utilise <span class="code">document.createElement("nom de la balise")</span>.  
Pour l'inclure dans le document, on peut l'ajouter comme enfant d'un élément du document avec<span class="code">appendChild("elementCree")</span>

<div class="code">

<div class="lang">JavaScript</div>

const new = document.createElement("div");  
let parent = document.getElementById("main");  
parent.appendChild(new);</div>

#### Supprimez et remplacez des éléments

* <span class="code">removeChild(child)</span>: supprime l'enfant.
* <span class="code">replaceChild(new,old)</span>: remplace l'enfant.

## Écoute d'événements

Un événement est une réaction à une action. Chaque fois que cette action arrive, la fonction<span class="code">callback</span>de l'événement est exécutée.  
L'événement s'applique à l'objet appellant, puis se **propage** à ses parents.  
La méthode <span class="code">addEventListener(event,callback(param))</span>Exécute automatiquement le callback quand l'événement arrive.

On peut utiliser plusieurs méthodes sur param :

* <span class="code">preventDefault()</span>: empêche le comportement par défaut du HTML.
* <span class="code">stopPropagation()</span>

Il existe des callbacks prédéfinis :

* <span class="code">click</span>: quand l'élément est cliqué.
* <span class="code">load</span>: quand la page a chargée.
* <span class="code">keypress</span>: quand une touche est pressée.
* <span class="code">mouseover</span>: quand souris survole.

#### L'événement mousemove

Il survient quand la souris se déplace.

Avec<span class="code">mousemove</span>, on dispose des fonctions suivantes (à utiliser dans le callback):

* <span class="code">clientX / clientY</span>: position de la souris dans les coordonnées locales.
* <span class="code">offsetX / offsetY</span> : position de la souris par rapport à l'élément actif.
* <span class="code">pageX / pageY</span>: position de la souris par rapport au document entier.
* <span class="code">screenX / screenY</span>: position de la souris par rapport à la fenêtre.
* <span class="code">movementX / movementY</span>: position de la souris par rapport à la position de la souris lors du dernier<span class="code">mousemove</span>.

#### L'événement change

Il survient quand l'utilisateur a rempli le champ d'un formulaire.  
<span class="code">target.value</span>: nouvelle valeur du champ.

#### L'événement input

Il survient quand l'utilisateur est en train de remplir le champ d'un formulaire.  
<span class="code">target.value</span>: nouvelle valeur du champ.

## Requêtes HTTP

<div class="code">

<div class="lang">JavaScript</div>

var request = new XMLHttpRequest(); //Création d'un objet AJAX  
request.open("GET", "http://...");  
request.send();</div>

#### Récupérer les données de la requête

Le plus pratique est de récupérer les données en JSON (JavaScript Object Notation) :

<div class="code">

<div class="lang">JSON</div>

{  
  "name":"Value",  
  "name":{"name":"value"},  
  "name":[  
    {"name":"value"},  
    {"name":"value"}  
  ]  
}  </div>

La fonction qui gère la requête sera sous la forme :

<div class="code">

<div class="lang">JavaScript</div>

var request = new XMLHttpRequest();  
request.onreadystatechange = function() {  
  // accès aux propriétés d'état  
}</div>

Pour passer du JSON à un objet JS :

<div class="code">

<div class="lang">JavaScript</div>

JSON.parse(texteJSON)</div>

Les propriétés d'état s'appliquent sur l'objet<span class="code">this</span>. Il en existe 3 :

* <span class="code">readyState</span>Elle correspond à l'état de la requête AJAX : voir au paragraphe suivant.
* <span class="code">status</span>2xx: pas d'erreur, 3xx: redirection, 4xx:erreur
* <span class="code">responseText</span>Réponse au format JSON.

<span class="code">XMLHttpRequest.état</span> avec état :

* <span class="code">UNSENT</span>Prêt mais open() pas appellé
* <span class="code">OPENED</span>open() appellé
* <span class="code">HEADERS_RECEIVED</span>send() appellé
* <span class="code">LOADING</span>Réception en cours
* <span class="code">DONE</span>Requête terminée

## Dessin dans une page web

<div class="code">

<div class="lang">JavaScript</div>

<canvas id='canvas' width='300' height='300'>Canvas non pris en charge !<canvas></div>

### Méthodes de canvas

On aplique toutes ces méthodes à un élément canvas auquel on applique <span class="code">getContext('2d')</span>.

Cet objet comprend deux variables pour les couleurs (on leur applique des couleurs avec le même format que css) :

* fillStyle
* strokeStyle

#### Rectangle

* fillRect(x, y, larg, haut) Dessine un rectangle rempli.
* strokeRect(x, y, larg, haut) Dessine un rectangle vide.
* clearRect(x, y, larg, haut) Efface la zone rectangulaire correspondante.

#### Trajet

* beginPath() Crée le traget.
* moveTo(x,y) Se place en (x, y).
* lineTo(x,y) Trace jusqu'en (x,y).
* arc(x, y, rayon, angleDébut, angleFin[, sensRotation] Trace l'arc correspondant (pas un camembert mais juste l'arc en lui-même).
* fill()
* closePath() Ferme le trajet.

<div class="exemple">Exemple (cliquez sur run pour tester) :  
<iframe height="800px" width="100%" src="https://replit.com/@MichelGrolet/ExempleCanvas?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe></div>

## Snippets

<div class="code">

<div class="lang">JS</div>

// Random boolean :  
const randomBoolean = () => Math.random() >= 0.5;  

// Si un jour est en semaine :  
const isWeekday = (date) => date.getDay() % 6 !== 0;  

// Inverser un String ;  
const reverse = str => str.split('').reverse().join('');  

// Si l'utilisateur est chez apple :  
const isAppleDevice = /Mac|iPod|iPhone|iPad/.test(navigator.platform);  

// Aller en haut de la page :  
const goToTop = () => window.scrollTo(0, 0);  

// Moyenne des arguments :  
const average = (...args) => args.reduce((a, b) => a + b) / args.length;</div>
