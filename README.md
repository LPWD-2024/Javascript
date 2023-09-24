# Javascript
**Sommaire**
- [1. Les types de variables](#1-les-types-de-variables)
  - [1.1 String](#11-string)
  - [1.2. Number](#12-number)
  - [1.3. Boolean](#13-boolean)
  - [1.4. Null](#14-null)
  - [1.5. Undefined](#15-undefined)
  - [1.6. Array](#16-array)
  - [1.7. Object](#17-object)
- [2. Le scope](#2-le-scope)
  - [2.1 var](#21-var)
  - [2.2 let](#22-let)
  - [2.3 const](#23-const)
- [3. Les fonctions](#3-les-fonctions)

# 1. Les types de variables 

Ces types nous les classons en deux grandes catégories de variables :

- **Variables primitives:** s*tring, number, boolean, undefined, null.*
On dit primitives car elles sont “simples”, elles ne contiennent qu’une seule valeur. Peu importe le type de la valeur primitive, une variable se déclare en lui donnant un nom et en lui affectant une valeur.
- **Variables complexes:** *Object, Array, Map, Set, ...*
On dit complexes car elles sont capables de stocker de multiples valeurs.

A noter : En JavaScript, toutes les variables complexes sont des Objets.  *Array, Map, Set,* etc… ne sont pas des types, mais des instances de *Object.*, elles héritent du prototype de *Object.*

## 1.1. String
*Variable primitive*

Un type string correspond à une chaine de caractères. La variable se déclare en mettant notre chaine de caractères entre 2 simple quotes ``` ' ``` ou 2 double quotes ``` " ```

```JS
// string

var prenom = 'Alex';

var nom = "Chautemps";

```
Les variables de type string peuvent être utilisées en concaténation
```JS
  console.log(prenom + nom)
  // AlexChautemps
  
  console.log(prenom + " " + nom)
  // Alex Chautemps

```

## 1.2. Number
*Variable primitive*

Un type number correspond à un nombre positif ou négatif. La variable se déclare en lui donnant simplement le nombre voulu.
```JS
// number
var age = 28;
```

Les variables de type number peuvent être utilisées pour faire des calculs.

```JS
var a = 10;
var b = 5;

console.log(a + b)
// 15

console.log(a - b)
// 5

console.log(a * b)
// 50

console.log(a / b)
// 2
```

Attention toutefois à ne pas faire de calculs avec des nombres à virgules, car vous risqueriez d'avoir un résultat non attendu. 
Je vous invite à lire ça si vous voulez savoir pourquoi https://ichi.pro/fr/pourquoi-0-1-0-2-0-3-en-javascript-237366067481202

## 1.3. Boolean
*Variable primitive*

Le type le plus simple. La variable se déclare en lui donnant simplement la valeur "false" ou "true"

```JS
// boolean
var estVieux = false;

```
Elles seront utilisées pour les conditions que nous verrons à la suite.

## 1.4. Null
*Variable primitive*

Ce type de variable nous servira rarement mais peut être utile dans quelques cas.

```JS
// null
var humour = null;

```
## 1.5. Undefined
*Variable primitive*

Ce type est attribué lorsqu'une variable est déclarée sans valeur.

```JS
// Undefined
var niveau;
```

## 1.6. Array
*Variable complexe*

Un type *Array* permettra de stocker plusieurs valeurs dans une même variable. Ce sera une liste d'élements ordonnés qui peut contenir tout types d'élements (*string*, *number*, *array*, *object*, ...).
Chaque élement du tableau aura une position numérique dans celui-ci, cette position est nommée : **index**.

> Il faut voir les tableaux comme un tiroir dans lequel on pourra mettre tout un tas de choses (stylos, post-its, ciseaux, etc). Nous pourrons chercher un stylo dans ce tiroir en trouvant sa position à l'intérieur de celui-ci (= index dans le tableau). Nous pourrons également vider le tiroir objet par objet pour voir tout ce qu'il contient (= boucler le tableau)

### Créer un tableau
Pour créer un tableau, nous avons 2 syntaxes : 
- Notion littérale : **[ ]**
- Constructeur Array : **new Array()**

```js
var monTableau = []

var monTableau2 = new Array()

//On peut mettre des valeurs à l'initialisation

var monTableau = ["Xavier", "David", "Pascal"]

var monTableau2 = new Array("Xavier", "David", "Pascal")
```

### Accèder aux valeurs d'un tableau
Pour acceder aux valeurs stockées dans un objet, il faut notez que les **Arrays** sont sur une **base 0**. C'est-à-dire que le premier élément commence à **index 0**


```js
  var monTableau = ["Xavier", "David", "Pascal"]
  console.log(monTableau[0]) //Xavier
  console.log(monTableau[2]) //Pascal
  console.log(monTableau[3]) //Undefined
```

Et si nous avons un tableau dans un tableau.
```js
  var monTableau = ["Homer", "Marge", ["Bart", "Lisa", "Maggie"]]
  console.log(monTableau[0]) //Homer
  console.log(monTableau[2][0]) //Bart
  console.log(monTableau[2][2]) //Maggie
```
### Ajouter une valeur dans un tableau
**Push - Ajouter une valeur à la fin**
```js
var monTableau = ["Xavier", "David", "Pascal"]
monTableau.push("Elodie")
console.log(monTableau) //["Xavier", "David", "Pascal", "Elodie"]
```
**Unshift - Ajouter une valeur au début**
```js
var monTableau = ["Xavier", "David", "Pascal"]
monTableau.unshift("Elodie")
console.log(monTableau) //["Elodie", "Xavier", "David", "Pascal"]
```

### Supprimer une valeur dans un tableau
**pop - Supprimer une valeur à la fin**
```js
var monTableau = ["Xavier", "David", "Pascal"]
monTableau.pop()
console.log(monTableau) //["Xavier", "David"]
```
**shift - Supprimer une valeur au début**
```js
var monTableau = ["Xavier", "David", "Pascal"]
monTableau.shift()
console.log(monTableau) //["David", "Pascal"]
```

**splice - Supprimer une/des valeur(s) en partiulier**
```js
var monTableau = ["Xavier", "David", "Pascal"]
/**
 * 1er paramètre : position du début
 * 2e paramètre : nombre d'élements à supprimer à partir de la position de début
 */
// Supprime 2 éléments à partir de la position 1
monTableau.splice(1, 2)
console.log(monTableau) //["xavier"]
```

###  Boucler dans un tableau
Les boucles vont nous permettre d'accéder aux valeurs d'un tableau, une par une, quelque soit la taille de celui-ci.
Vous avez 2 possibilités pour le faire :
- **for**
```js
var monTableau = ["Xavier", "David", "Pascal"]
for(var i = 0; i < monTableau.length; i++) {
  console.log("index :", i)
  console.log("Prof :", monTableau[i])
}
```
- **forEach**
```js
var monTableau = ["Xavier", "David", "Pascal"]
monTableau.forEach(function(valeur, index){
  console.log("index :", index)
  console.log("Prof :", valeur)
})
```
https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach

###  Quelques méthodes intéressantes pour les tableaux

**Array.map()**
La méthode ```map()``` va nous permettre de créer un nouveau tableau de même longueur avec des valeurs résultantes d'une fonction. La fonction doit toujours retourner l'élément courant et sa modification.
```js
var monTableau = ["Xavier", "David", "Pascal"]
var monTableauCool = monTableau.map(function(prof){
  return prof + " est cool"
})

console.log(monTableauCool) //['Xavier est cool', 'David est cool', 'Pascal est cool']
```
https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/map

**Array.filter()**
La méthode ```filter()``` va nous permettre de filtrer un tableau via une condition dans la fonction de callback. La fonction de filtrage doit return ```true```ou ```false```pour garder un élément ou non

```js
var monTableau = ["Xavier", "David", "Pascal", "Elodie"]
var monTableauFiltre = monTableau.filter(function(prof){
  return prof.includes("e")
})

console.log(monTableauFiltre) //['Xavier', 'Elodie']
```
https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/filter

**Array.find()**
La méthode ```find()``` va nous permettre de trouver la première valeur qui correspond à notre condition dans la fonction de callback. Cette fonction doit return ```true```ou ```false```

```js
var monTableau = ["Xavier", "David", "Pascal", "Elodie"]
var prenomAvecUnD = monTableau.find(function(prof){
  return prof.includes("d")
})
console.log(prenomAvecUnD) //David
```
https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/find


## 1.7. Object
*Variable complexe*

Tout comme le type *Array*, un type *Object* permettra de stocker plusieurs valeurs dans une même variable. 
La variable se déclare avec avec les accolades et une ou plusieurs paires "clé : valeur" séparées par une virgule.

> Il faut voir les Objets comme un tiroir également, mais à la différence des tableaux, ce tiroir est divisé en plusieurs compartiments. Chaque compartiment aura une étiquette pour nommé l'emplacement (clé) et nous mettrons l'objet associé dans ce compartiment (valeur). Lorsque nous rechercherons le stylo, cette fois, pas besoin de fouiller tout le tiroir pour trouver sa position, il suffira juste de lire l'étiquette du compartiment.

### Creer un objet

```JS
var monObjet = {
}

var monObjet2 = new Object()

var personne = {
  nom : "Chautemps",
  prenom: "Alex",
  age: 28,
  estVieux: false
}
```

### Accéder aux valeurs de l'objet
Pour acceder aux valeurs stockées dans un objet, vous avez 2 notations disponibles. 

Notez bien que les 2 sont importantes à apprendre. La seconde nous permettra de trouver une valeur via une variable.

```JS

  console.log(personne.prenom)
  // Alex
  
  personne.parler()
  // Bonjour à tous
  
  console.log(personne["prenom"])
  // Alex
  
  
  // Trouver la valeur en via une variable
  var cle = "nom"
  
  console.log(personne.cle)
  // Undefined
  
  console.log(personne[cle])
  // Chautemps

```

Nous pouvons également ajouter une ```function``` en tant que valeur pour une clé. Nous ne parlerons plus de *propriété* mais de *méthode"

```JS
var personne = {
  nom : "Chautemps",
  prenom: "Alex",
  age: 28,
  estVieux: false,
  parler: function(message){
    console.log(message)
  }
}

personne.parler("Je parle") // Je parle

```

### Attribuer une nouvelle valeur à une propriété
Comme pour les variables primitives, il suffit d'attribuer la nouvelle valeur via le signe ```=```
```JS
personne.prenom = "Bruno"
console.log(personne) // {nom: "Chautemps", prenom:"Bruno, ...}
```

Nous pouvons également ajouter une nouvelle propriété de la même façon
```JS
personne.qualite = "Gentil"
console.log(personne) // {nom: "Chautemps", ..., qualite: "Gentil"}
```

###  Quelques Méthodes intéressantes pour les Objets
#### Object.values()
Cette méthode retourne un tableau contenant toutes les **valeurs** de l'objet

```JS 
var personne = {
  nom : "Chautemps",
  prenom: "Alex",
  age: 28
}
var toutesLesValeursDePersonne = Object.values(personne)
console.log(toutesLesValeursDePersonne) // ['Chautemps', 'Alex', 28]
```

https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Object/values

#### Object.keys()
Cette méthode retourne un tableau contenant toutes les **clés** de l'objet

```JS 
var personne = {
  nom : "Chautemps",
  prenom: "Alex",
  age: 28
}
var toutesLesClesDePersonne = Object.keys(personne)
console.log(toutesLesClesDePersonne) // ['nom', 'prenom', 'age']
```
https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Object/keys

### Object.entries()
Cette méthode retourne un tableau contenant toutes les paires **clés/valeurs** de l'objet dans des "sous-tableaux"

```JS 
var personne = {
  nom : "Chautemps",
  prenom: "Alex",
  age: 28
}
var toutesLesPropsDePersonne = Object.entries(personne)
console.log(toutesLesPropsDePersonne) // [['nom', 'Chautemps'], ['prenom', 'Alex'], ['age', 28]]
```

Idéal pour faire une boucle dans un Objet

https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Object/entries

### Object.assign()
Cette méthode combine 2 objets.

```JS 
var personne = {
  nom : "Chautemps",
  prenom: "Alex",
  age: 28
}
var nouvellesInformations = {
  prenom: "Bruno",
  qualite : "Gentil"
}

var nouvellePersonne = Object.assign(personne, nouvellesInformations)
console.log(toutesLesPropsDePersonne) // {nom: 'Chautemps', prenom: 'Bruno', age: 28, qualite: 'Gentil'}
```

Notez que les propriétés similaires entre les 2 objets seront remplacé par celles du second objet dans les paramètres de la méthode.

https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Object/assign

> Notez bien que tout ce qu'il y'a dans ce document n'est qu'un aperçu de ce qui est possible de faire. Nous ne pouvons pas tout voir dans une seule et même page. Partez du principe que pour chaque besoin, il y aura une méthode adaptée pour les Objets et Tableaux. 
**ET mettez moi MDN en page d'accueil de vos navigateurs!**

# 2. Le Scope
Maintenant que nous avons vu tous les types de variables. Il faut prendre en compte que lorsque que nous déclarons une variable, celle-ci aura une portée dans notre code qu'on appelle **scope**.
Par exemple, si nous déclarons une nouvelle variable dans une fonction, elle sera utilisable uniquement dans cette dite fonction. On peut donc avoir des variables **globales** (utilisables partout dans notre code) et des variables **locales** (utilisables uniquement dans le même scope)


> Pour faire très simple, Une paire de ```{}``` = un scope

```JS
var a = "Alex" // Variable globale utilisable partout

function maFonction() {
  var b = "Romain" // Variable locale à la fonction maFoncion utilisable uniquement dans celle-ci
  console.log(a) // Alex
  console.log(b) // Romain
}

console.log(a) // Alex
console.log(b) // ERROR

```



## Déclaration des variables dans le scope
Nous avons vu précédement que pour déclarer une variable il faut utiliser, le mot clé ```var```. Cependant il n'est pas le seul utilisable, JavaScript met également à disposition les mots clés ```let``` et ```const```

## 2.1. var
Voyons concrètement ce que ```var``` fait réellement maintenant que nous avons la notion de **scope**.
Il va nous permettre de déclarer une variable en lui affectant (ou non) une valeur. Son scope sera soit global (tout le projet), soit locale (dans une fonction). Cependant vous pouvez avoir quelques problèmes lorsque vous déclarez plusieurs fois une variable du même nom dans un même scope "parent".

```JS
function varTest() {
  // Scope de la fonction
  var a = "Alex";
  if (true) {
    // Scope de la condition
    var a = "Romain";
    console.log(a); // Romain
  }
  //Scope de la fonction
  console.log(a); // Nous attendons "Alex" car nous sommes dans le scope de la fonction mais nous aurons "Romain"
}

```
Le scope de 'var' est la fonction varTest(), peu importe les blocks {}. La valeur change même si nous la déclarons dans un scope de condition au sein de la fonction.

> Sincérement, oubliez ```var``` et utilisez les 2 mots clés suivants. Vous serez certains de ne pas avoir de bug lié à des changements de valeur non voulus.

## 2.2. let
Le mot clé ```let``` reprend les mêmes principes fondamentaux que ```var``` cependant il va ajouter la notion de scope locale à tous les block ```{}```

```JS
function letTest() {
  // Scope de la fonction
  let a = Alex;
  if (true) {
    // Scope de la condition
    let a = "Romain";
    console.log(a); // Romain
  }
  console.log(a); // Alex
}

```
Le scope de ma première variable "a" est donc celui de la fonction letTest() et le scope de la seconde devient donc celui de la condition "if (true)"

> A partir de maintenant, remplacez moi tous vos "var" par "let" :)

## 2.3. const
Le mot clé ```const```reprend exactement les mêmes principes que ```let``` . Le scope de la variable est donc celle du block courant ```{}``` mais celle-ci sera en lecture seule. C'est donc une variable immuable.

```JS
const MA_CONSTANTE = 100;
MA_CONSTANTE = 50 // Erreur car on ne peut pas la redéfinir
console.log(MA_CONSTANTE) // 100
```

La convention veut que les constantes soient en majuscules.

Notez que pour les variables complexes. Nous pouvons changer leur contenu malgré le fait que ce soit une constante. 

```JS
const MA_CONSTANTE_ARR = ["Alex"];
MA_CONSTANTE_ARR.push("Romain")
console.log(MA_CONSTANTE_ARR) // ["Alex", "Romain"]
```
Ceci fonctionne car nous ne changeons pas le tableau qui reste le même, nous changeons le contenu de celui-ci.

# 3. Les Fonctions
Les fonctions vont nous permettre de stocker un ensemble d'instructions JavaScript que nous pourrons réutiliser dans notre code.

### Définir et utiliser une fonction
Pour définir une fonction il suffira d'utiliser le mot clé ```function``` suivi par :
- le nom de la fonction (qui décrit idealement le rôle de la fonction) ;
- les **( )** : signe distinctif de la fonction qui peut prendres des variables appelés **paramètres**. Les paramètres fonctionnent comme des variables, nous devrons leur donner un nom et seront séparés par une virgule ;
- les **{ }** : c'est entre ces 2 accolades que nous mettrons la liste des instructions à executer dans la fonction.

Pour l'utiliser, il suffira de mettre son nom suivi des **()**. Si la fonction possède des **paramètres**, il faudra mettre entre les parenthèses, les valeurs ou **arguments** qui correspondront à chaque paramètre. 

Fonction sans paramètre
```JS
function afficherUnMessage(){
  console.log("Affiche ce message")
}

afficherUnMessage() // Affiche ce message
afficherUnMessage() // Affiche ce message


```

Fonction avec paramètres
```JS
function afficherUnMessage(message){
  console.log("Message : " + message)
}
afficherUnMessage("Bonjour") // Message : Bonjour

function afficherDeuxMessages(message1, message2){
  console.log("Message 1 : " + message1)
  console.log("Message 2 : " + message2)
}

afficherDeuxMessages("Bonjour", "Au Revoir") 
// Message 1 : Bonjour  
// Message 2 : Au revoir

afficherDeuxMessages("S'il vous plait", "Merci")
// Message 1 : S'il vous plait
// Message 2 : Merci

```
Un paramètre de fonction peut être une fonction. Celui-ci sera nommé **callback**.

```JS
function afficherDeuxMessages(message, callback){
  console.log(message)
  callback()
}

afficherDeuxMessages("Bonjour", function(){
  console.log("Au revoir")
})
// Bonjour
// Au revoir
```
