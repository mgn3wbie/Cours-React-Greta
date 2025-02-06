# III - Components
## 1. Composant Fonctionnel
Un composant est une partie de l'interface utilisateur qui peut être réutilisée dans différentes parties de l'application. 
Les composants peuvent être des éléments simples comme des boutons ou des champs de texte, ou des éléments plus complexes comme des formulaires ou des tableaux. 

Les composants fonctionnels sont la manière la plus simple de créer un composant React. 
Ils sont appelés ainsi parce qu'ils sont littéralement des fonctions JavaScript.

**Exemple :**
```jsx
const MonComposant = ( ) => {
return <p>coucou, !</p>;
} 
```

pour l'utiliser dans App.js:

```jsx
function App() {
return <MonComposant />  ;
}
```

Dans cet exemple, **MonComposant** commence par une majuscule, la majuscule est obligatoire pour les noms de composants.    
React considère les composants commençant par des lettres minuscules comme des balises DOM. 
Par exemple, `<div />` représente une balise HTML **div**, mais `<Welcome />` représente un composant, et exige que l’identifiant **Welcome** existe dans la portée courante.

---

#### Exercice 1 - Création d'un Composant avec Vite :  
Objectif : Créer un composant fonctionnel qui affiche le message "Bonjour !" à l'écran.

Étapes :
- Ouvrez src/App.js dans votre éditeur de code.
- Définissez un composant fonctionnel appelé **MonComposant** qui retourne dans un h1: Bonjour ! 
- Utilisez le composant **MonComposant** pour afficher le message à l'écran.

##### Solution :
```jsx
const MonComposant = () => {
  return <h1>Hello,   !</h1>;
};

function App() {
  return <MonComposant />;
}

export default App;
```

---

## 2. Composant Class
Un composant est une partie de l'interface utilisateur qui peut être réutilisée dans différentes parties de l'application. 
Les composants peuvent être des éléments simples comme des boutons ou des champs de texte, ou des éléments plus complexes comme des formulaires ou des tableaux. 

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

#### Exercice 1 : Création d'un Composant de Class

Reprenez l'exercice précédent
Définissez un composant de classe appelé **MonComposantClass** qui retourne un texte dans un `<p>` 
Utilisez le composant **MonComposantClass** pour afficher le message à l'écran sous le h1.

!!! NOTE Chaque composant React retourne un seul élément parent, il faut donc envelopper tous les éléments enfants dans un conteneur unique, que ce soit un élément DOM comme `<div></div>`, ou utiliser des Fragments de React `<></>` pour éviter d'ajouter des nœuds supplémentaires au DOM. 

---

## 3. Composant externe
Pour optimiser la structure de votre projet React, 
il est vivement conseillé de placer chaque composant dans un fichier distinct. 
Cette approche offre une meilleure organisation du code, le rend plus clair et simplifie la réutilisation des composants.

Lors de la création d'un fichier pour un composant, respectez les conventions suivantes :
- Nommez le fichier en suivant la règle de la majuscule initiale pour le nom du composant.
- N'oubliez pas d'importer React ainsi que toute autre dépendance requise en début de fichier.
- À la fin du fichier, exportez votre composant en utilisant la syntaxe : export default NomDuComposant. 
- Lorsque vous souhaitez utiliser ce composant dans un autre fichier, importez-le en utilisant la syntaxe :
```jsx
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
  
#### Exercice 1 : Séparation des Composants dans des Fichiers Externes
Objectif : 
    Déplacer les composants MonComposant et MonComposantClass dans des fichiers séparés et les importer dans le fichier App.js.

#### Solution
```jsx
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
```
```jsx
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
```
```jsx
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
---

## 4. Props
Les "props" sont des données que l'on passe d'un composant parent à un composant enfant dans React.

Définition d'un composant avec des props :
**- Fonctionnel :**
```jsx
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
```
**- Class :**    
```jsx
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

**- Utilisation du composant :**
```jsx
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

---

#### Exercice 1 - Affichage d'un Message Personnalisé avec Props :
Objectif : Créer 2 composants (1 fonctionnel, 1 class) qui affichent un message personnalisé en utilisant les props.

Étapes :
- Définissez 2 composants (1 fonctionnel, 1 class)  qui acceptent une prop .
- Dans le composant principal App, utilisez les composants passez une valeur pour la prop.
- Lancez votre application pour voir le message personnalisé affiché à l'écran.
