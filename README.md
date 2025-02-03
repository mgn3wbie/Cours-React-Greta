# 1-installation

## 1-vite.js
Vite est un outil moderne pour créer des applications front-end rapides et légères, y compris des applications React.

Pour créer une application React avec Vite, exécutez les commandes suivantes :

npm create vite@latest my-app // Remplacez "my-app" par le nom que vous souhaitez donner à votre application.
cd my-app
npm install
npm run dev

Cela démarrera un serveur de développement local. Une URL sera affichée dans le terminal, généralement sous la forme suivante :
Local: http://localhost:5173/  Vous devrez copier et coller cette URL dans votre navigateur pour accéder à votre application.

(npm create vite@latest garantit que vous utilisez la dernière version de Vite à chaque fois que vous initialisez un nouveau projet.)


Une fois votre application React créée avec Vite, voici les dossiers et fichiers principaux que vous trouverez :  
my-app/  
├── node_modules/        # Dossier contenant toutes les dépendances installées via npm.  
├── public/              # Dossier contenant des fichiers publics statiques accessibles tels quels.  
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── vite.svg&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Exemple de fichier statique (logo Vite).  
├── src/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Dossier contenant le code source de l'application.  
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── App.css&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Fichier CSS pour styliser le composant App.  
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── App.jsx&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Composant principal de l'application.  
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── index.css&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Fichier CSS global pour les styles de l'application.  
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── main.jsx&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Point d'entrée de l'application. Monte le composant racine (App) dans le DOM.  
├── .gitignore&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Fichier spécifiant les dossiers/fichiers à ignorer par Git.  
├── index.html&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Page HTML principale contenant le conteneur où React est monté.  
├── package.json&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Fichier décrivant les dépendances, scripts et métadonnées du projet.  
├── README.md&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Fichier texte contenant des informations sur le projet.  
└── vite.config.js&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Fichier de configuration de Vite (modifiable si besoin pour personnaliser le projet).  
node_modules/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Contient toutes les dépendances installées via npm.  
public/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Contient des fichiers publics statiques accessibles directement dans le navigateur.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Les fichiers de ce dossier ne sont pas transformés par Vite.  
  
eslint.config.js&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Fichier de configuration pour ESLint, utilisé pour gérer les règles de style et détecter les erreurs dans le code.

## Create element.js

La méthode createElement est une fonction fondamentale de la bibliothèque React. 
Elle est utilisée pour créer et renvoyer des éléments React, 
qui sont les plus petites unités de construction des interfaces utilisateur React.

Syntaxe de createElement :
importation de React: import React from 'react';

React.createElement(type, [props], [...children])
    type :  élément que vous souhaitez créer. 
            Cela peut être une chaîne (pour les éléments DOM comme 'div', 'span', etc.) 

    props : Un objet contenant les propriétés (ou "props") que vous souhaitez passer à l'élément. 
            Cela peut inclure des attributs comme className ou id pour les éléments DOM, 

    children : Les éléments enfants qui doivent être imbriqués à l'intérieur de l'élément créé. 
            Cela peut être du texte, d'autres éléments React, ou un mélange des deux.

## 4-jsx.js
  * 
JSX est une extension de syntaxe pour JavaScript, 
recommandée par React pour décrire à quoi devrait ressembler l'interface utilisateur. 
Il ressemble à du HTML, mais il est intégré directement dans du JavaScript.
Un élément JSX ressemble à une balise HTML.
### Exercice
```
Exercice : Créer un titre avec JSX
Objectif : Utilisez JSX pour créer un titre (h1) .

Étapes :

Modification de App.jsx :

Ouvrez src/App.jsx dans votre éditeur de code.
Utiliser JSX :

Dans la fonction App, retournez le JSX suivant :

\<h1>Bienvenue à React !\</h1>  

Vérification :

Assurez-vous que votre serveur de développement est en cours d'exécution avec npm run dev.
Ouvrez votre navigateur et vous devriez voir le titre "Bienvenue à React !" affiché.
```

 *******
Snippets React/Redux/GraphQL/React-Native (ES7+)
Les snippets facilitent le développement en générant automatiquement des structures de code courantes. 
Voici les principaux :

    rcc : Génère un composant React de classe avec un constructeur.
    rce : Génère un composant React de classe avec une exportation.
    rfc : Génère un composant React fonctionnel.
    rfce : Génère un composant React fonctionnel avec une exportation.
    useState : Génère le Hook useState pour la gestion de l'état.
    useEffect : Génère le Hook useEffect.
*****

# 2-component
## 1-fonctionnel.js

Un composant est une partie de l'interface utilisateur qui peut être réutilisée dans différentes parties de l'application. 
Les composants peuvent être des éléments simples comme des boutons ou des champs de texte, 
ou des éléments plus complexes comme des formulaires ou des tableaux. 

Les composants fonctionnels sont la manière la plus simple de créer un composant React. 
Ils sont appelés ainsi parce qu'ils sont littéralement des fonctions JavaScript.
exemple:
```javascript
const MonComposant = ( ) => {
return <p>coucou, !</p>;
} 
```

pour l'utiliser dans App.js:
```javascript
function App() {
return <MonComposant />  ;
}
```
Dans cet exemple, **MonComposant** commence par une majuscule,
 la majuscule est obligatoire pour les noms de composants.    
 React considère les composants commençant par des lettres minuscules comme des balises DOM. 
 Par exemple, **\<div />** représente une balise HTML **div**, mais **\<Welcome />** représente un composant, et exige que l’identifiant **Welcome** existe dans la portée courante."


### Exercice
```
Exercice : Création d'un Composant avec Vite
Objectif : Créer un composant fonctionnel qui affiche le message "Bonjour !" à l'écran.

Étapes :
Créer un projet avec Vite 

Ouvrez src/App.js dans votre éditeur de code.
Définissez un composant fonctionnel appelé MonComposant qui retourne dans un h1: Bonjour ! 

utilisez le composant MonComposant pour afficher le message à l'écran.
```

### solution : 
```javascript
const MonComposant = () => {
  return <h1>Hello,   !</h1>;
};

function App() {
  return <MonComposant />;
}

export default App;
```


## 2-class.js
COURS:
Un composant est une partie de l'interface utilisateur qui peut être réutilisée dans différentes parties de l'application. 
Les composants peuvent être des éléments simples comme des boutons ou des champs de texte, 
ou des éléments plus complexes comme des formulaires ou des tableaux. 

Contrairement aux composants fonctionnels, les composants de classe sont définis en utilisant la syntaxe de classe ES6.
Avant l'introduction des Hooks dans React 16.8, les composants de classe étaient le principal moyen de gérer l'état et le cycle de vie des composants.

Voici un exemple de composant de classe qui affiche le message "Bonjour !" à l'écran :

```javascript
// Importation de la bibliothèque React depuis le module 'react'.
import React from "react";

// Définition d'un composant de classe nommé 'MonComposantClass'.
// Ce composant étend la classe 'Component' de React, ce qui signifie qu'il hérite de toutes ses fonctionnalités.
class MonComposantClass extends React.Component {
  // La méthode 'render' est obligatoire pour tous les composants React.
  // Elle détermine ce qui sera affiché à l'écran lorsque le composant est utilisé.
  render() {
    // Retourne un élément JSX (ici, une balise <h1>) qui sera rendu à l'écran.
    // Lorsque ce composant est utilisé, il affichera "Bonjour !" dans un en-tête de niveau 1.
    return <h1>Bonjour !</h1>;
  }
}
```

### Exercice : Création d'un Composant de Class

```
reprenez l'exercice 1 
Définissez un composant de classe appelé MonComposantClass qui retourne un texte dans un <p> 
Utilisez le composant MonComposantClass pour afficher le message à l'écran sous le h1.
```

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
chaque composant React retourne un seul élément parent, il faut donc envelopper tous les éléments enfants dans un conteneur unique, 
que ce soit un élément DOM comme <div></div>, ou utiliser des Fragments de React <></> pour éviter d'ajouter des nœuds supplémentaires au DOM. 
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 


## 3-externe.js
Pour optimiser la structure de votre projet React, 
il est vivement conseillé de placer chaque composant dans un fichier distinct. 
Cette approche offre une meilleure organisation du code, le rend plus clair et simplifie la réutilisation des composants.

Lors de la création d'un fichier pour un composant, respectez les conventions suivantes :
    Nommez le fichier en suivant la règle de la majuscule initiale pour le nom du composant.
    N'oubliez pas d'importer React ainsi que toute autre dépendance requise en début de fichier.
    À la fin du fichier, exportez votre composant en utilisant la syntaxe : export default NomDuComposant.
Lorsque vous souhaitez utiliser ce composant dans un autre fichier, importez-le en utilisant la syntaxe :
```javascript
    import NomDuComposant from './CheminVersLeFichier';.

    // exemple: 
    // dans Salutation.js//
    import React from 'react';
    
    function Salutation(props) {
        return <h1>Bonjour, {props.nom} !</h1>;
    }
    
    export default Salutation;
    // 
    // dans App.js
    import React from 'react';
    import Salutation from './Salutation';  // Importation du composant
    
    function App() {
        return (
            <div>
            <Salutation />
            </div>
            );
        }

    export default App;
```
  
### Exercice
```
Exercice :  
    Séparation des Composants dans des Fichiers Externes

Objectif : 
    Déplacer les composants MonComposant et MonComposantClass dans des fichiers séparés et les importer dans le fichier App.js.
```

### Solution
```javascript
// Importation des bibliothèques et composants nécessaires
import React from "react"; // Importation de la bibliothèque React
import MonComposant from "./MonComposant"; // Importation du composant fonctionnel MonComposant
import MonComposantClass from "./MonComposantClass"; // Importation du composant de classe MonComposantClass

// Définition du composant principal App
function App() {
  return (
    // Utilisation de la syntaxe courte des Fragments pour regrouper les composants
    <>
      {/* Rendu du composant fonctionnel MonComposant*/}
      <MonComposant />
      {/* Rendu du composant de classe MonComposantClass */}
      <MonComposantClass />
    </>
  );
}

// Exportation du composant App pour qu'il puisse être utilisé dans d'autres parties de l'application
export default App;
***********MonComposant.jsx
// Importation de la bibliothèque React
import React from "react";

// Définition d'un composant fonctionnel nommé MonComposant
const MonComposant = () => {
  // Le composant retourne un élément h1 avec le texte "Hello, !"
  return <h1>Hello, !</h1>;
};

// Exportation du composant MonComposant pour qu'il puisse être utilisé dans d'autres fichiers
export default MonComposant;

******************** MonComposantClass.jsx
// Importation de la bibliothèque React
import React from "react";

// Définition d'un composant de classe nommé MonComposantClass
class MonComposantClass extends React.Component {
  // La méthode render est responsable de décrire ce que le composant doit afficher
  render() {
    // Le composant retourne un élément <p> avec le texte "MonComposantClass."
    return <p>MonComposantClass.</p>;
  }
}

// Exportation du composant MonComposantClass pour qu'il puisse être utilisé dans d'autres fichiers
export default MonComposantClass;

```

## 4-props.js

Les "props" sont des données que l'on passe d'un composant parent à un composant enfant dans React.

Définition d'un composant avec des props :
fonctionnel:
```js
    // Importation de la bibliothèque React (si ce n'est pas déjà fait)
    import React from 'react';
    // Définition du composant "Welcome" en tant que fonction fléchée
    const Welcome = (props) => {
        // Retourne un élément h1 qui affiche un message de bienvenue
        // en utilisant la prop "name" passée au composant
        return <h1>Bonjour, {props.name}</h1>;
    }
    // Exportation du composant Welcome pour qu'il puisse être utilisé dans d'autres fichiers
    export default Welcome;

class:    
    // Importation de la bibliothèque React
    import React from 'react';
    // Définition du composant "Welcome" en tant que composant de class
    class Welcome extends React.Component {
        // La méthode render est responsable de la description de ce que le composant doit afficher
        render() {
            // Retourne un élément h1 qui affiche un message de bienvenue en utilisant la prop "name" passée au composant
            return <h1>Bonjour, {this.props.name}</h1>;
        }
    }
    // Exportation du composant Welcome pour qu'il puisse être utilisé dans d'autres fichiers
    export default Welcome;
```

Utilisation du composant :
```js
import React from "react";
// Définition du composant "Welcome" en tant que composant de class
class Welcome extends React.Component {
    render() {
        return <h1>Bonjour, {this.props.name}</h1>;
    }
}
function App() {
  return (
    <>
        <Welcome name="Sara" />;
    </>
  );
}
export default App;
```

### Exercice 
```
Exercice : Affichage d'un Message Personnalisé avec Props
Objectif : Créer 2 composants (1 fonctionnel, 1 class) qui affichent un message personnalisé en utilisant les props.

Étapes :

Définissez 2 composants (1 fonctionnel, 1 class)  qui acceptent une prop .

Dans le composant principal App, utilisez les composants passez une valeur pour la prop .

Lancez votre application pour voir le message personnalisé affiché à l'écran.
```

# 3-state
## 0-cours.js
Le state est une manière pour les composants React de stocker des informations changeantes. 
C'est une donnée interne à un composant et elle peut changer au fil du temps, contrairement aux props qui sont immuables.

**Initialisation du state :**  
  > Dans les composants de classe, le state est généralement initialisé dans le constructeur avec une structure comme celle-ci :
```jsx
import React from 'react';

class MonComposant extends React.Component {
    constructor(props) {
        super(props);
        // Initialisation du state avec une propriété "nom" ayant la valeur "Marc"
        this.state = {
            nom: "Marc"
        };
    }

    render() {
        return (
            <div>
                {// Affichage de la valeur de la propriété "nom" du state }
                {this.state.nom}
            </div>
        );
    }
}
export default MonComposant;
```
_Dans cet exemple, j'ai créé un composant de classe appelé MonComposant. Le constructeur est utilisé pour initialiser le state du composant. 
Vous pouvez ajouter votre JSX ou d'autres méthodes à ce composant selon vos besoins._

**Accéder au state :**  
> Vous pouvez accéder à la valeur actuelle du state en utilisant this.state.nomDeLaVariable    
    
**Mise à jour du state :**  
> Pour mettre à jour le state, utilisez toujours la méthode this.setState(). 
    Elle informe React que le state a changé et que le composant doit être réaffiché.
    N'assignez jamais directement le state. Par exemple, `this.state.myVar = 123` est incorrect. 
    Utilisez plutôt `this.setState({ myVar: 123 })`  

**Exemple:**

```jsx
import React from 'react';

class MonComposant extends React.Component {
    constructor(props) {
        super(props);
        // Initialisation du state avec une propriété "nom" ayant la valeur "Marc"
        this.state = {
            nom: "Marc"
        };
    }
    // Méthode pour mettre à jour la propriété "nom" du state
    changerNom = () => {
        this.setState({
            nom: "Jean"
        });
    }

    render() {
        return (
            <div>
                {// Affichage de la valeur de la propriété "nom" du state }
                {this.state.nom}
                {// Bouton pour déclencher la mise à jour du state }
                <button onClick={this.changerNom}>Changer le nom</button>
            </div>
        );
    }
}

export default MonComposant;
```

## 1-compteurSimple.js

Gestion des événements onClick dans React
Dans React, la gestion des événements est très similaire à celle des éléments DOM, mais avec quelques différences syntaxiques. 
Par exemple, les événements React sont nommés en camelCase plutôt qu'en minuscules.

Au lieu d'utiliser une chaîne de caractères comme gestionnaire d'événements, 
comme c'est le cas en HTML pur, avec JSX, vous passez une fonction.
        <button onClick={() => this.uneFonction()}></button> 

### Exercice : 
```
1. Compteur simple :

Créez un composant de classe qui affiche un nombre (initialisé à 0 dans le state).
Ajoutez un bouton "Incrémenter" qui, lorsqu'il est cliqué, augmente la valeur du compteur de 1 en utilisant this.setState.
```

### Solution :
```jsx
import React from "react";

export default class Counter extends React.Component {
    // Constructeur de la classe
    constructor(props) {
        // Appel du constructeur de la classe parente (React.Component) avec les props
        super(props);
        // Initialisation du state avec une propriété "count" définie à 0
        this.state = { count: 0 };
    }

    // Méthode pour incrémenter la valeur de "count" dans le state
    incrementCount() {
        // Utilisation de setState pour mettre à jour la valeur de "count" en l'augmentant de 1
        this.setState({ count: this.state.count + 1 });
    }

    // Méthode render pour définir ce que le composant doit afficher
    render() {
        return (
            // Conteneur principal
            <div>
                {/* Affichage de la valeur actuelle de "count" du state*/}
                <div>Count: {this.state.count}</div>
                {/* Bouton qui, lorsqu'il est cliqué, appelle la méthode incrementCount pour augmenter le compteur*/}
                <button onClick={() => this.incrementCount()}>Incrémenter</button>
            </div>
        );
    }
}
```
