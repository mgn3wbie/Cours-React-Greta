# IV - State
Le state est une manière pour les composants React de stocker des informations changeantes. 
C'est une donnée interne à un composant et elle peut changer au fil du temps, contrairement aux props qui sont immuables.

## 1. Initialisation du state :
Dans les composants de classe, le state est généralement initialisé dans le constructeur avec une structure comme celle-ci :
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
Dans cet exemple, j'ai créé un composant de classe appelé **MonComposant**. Le constructeur est utilisé pour initialiser le state du composant. 
Vous pouvez ajouter votre JSX ou d'autres méthodes à ce composant selon vos besoins.

## 2. Accéder au state :  
Vous pouvez accéder à la valeur actuelle du state en utilisant `this.state.nomDeLaVariable`    
    
## 3. Mise à jour du state :  
Pour mettre à jour le state, utilisez toujours la méthode `this.setState().` 
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

Dans React, la gestion des événements est très similaire à celle des éléments DOM, mais avec quelques différences syntaxiques. 
Par exemple, les événements React sont nommés en camelCase plutôt qu'en minuscules.

Au lieu d'utiliser une chaîne de caractères comme gestionnaire d'événements, 
comme c'est le cas en HTML pur, avec JSX, vous passez une fonction.
`<button onClick={() => this.uneFonction()}></button> `

---

#### Exercice 1 - Compteur simple :

Créez un composant de classe qui affiche un nombre (initialisé à 0 dans le state).  
Ajoutez un bouton "Incrémenter" qui, lorsqu'il est cliqué, augmente la valeur du compteur de 1 en utilisant `this.setState`.


#### Solution :
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
---
#### Exercice 2 - Interrupteur :

Créez un composant de classe qui affiche un interrupteur qui change d'etat On/Off quand on clique dessus.

#### Solution
```jsx
import React from "react";

class Interrupteur extends React.Component {
    // 1. Initialisation du state directement sans le constructeur
    state = {
        isOn: false,
    };

    // 2. Méthode pour changer l'état en utilisant une fonction fléchée
    toggleSwitch = () => {
        // this.setState avec une fonction garantit que vous utilisez l'état le plus récent pour calculer la nouvelle valeur.
        this.setState((prevState) => ({
            isOn: !prevState.isOn,
        }));
    };

    // 3. Rendu et Gestion des événements
    render() {
        return (
            <div>
                <p>{this.state.isOn ? "On" : "Off"}</p>
                <button onClick={this.toggleSwitch}>Basculer</button>
            </div>
        );
    }
}

export default Interrupteur;
```
