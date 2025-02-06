# VI - Style
## 1. Inline style
Dans React, les styles en ligne ne sont pas écrits comme des chaînes de caractères, mais comme des objets JavaScript. 
Cela diffère de la manière dont nous définissons généralement les styles en ligne en HTML pur.

**Avantages des styles en ligne :**
>**Isolation :** Les styles en ligne sont spécifiques à un élément, ce qui évite les conflits de styles.
**Dynamisme :** Il est facile de manipuler les styles en fonction de l'état ou des props du composant.
**Regroupement :** Pas besoin d'ajouter des fichiers CSS supplémentaires, tout est dans le fichier JS.

**Définir un objet de style :**
```jsx
    function App() {
        return <button style={{backgroundColor: 'blue'}}>Cliquez-moi</button>;
    }
```
  
**OU**
  
Créez un objet JavaScript où les propriétés sont en camelCase:
```jsx
const buttonStyle = {
    backgroundColor: 'blue',
    color: 'white',
    padding: '10px 20px',
    borderRadius: '5px'
};
```
Appliquer le style à un élément :
```jsx
function App() {
    return <button style={buttonStyle}>Cliquez-moi</button>;
}
``` 
**Limitations des styles en ligne :**
> **Pas de pseudo-classes ou pseudo-éléments :** on ne peut pas utiliser :hover, ::before, etc. avec des styles en ligne.
**Pas de médias queries :** les styles en ligne ne les prennent pas en charge .
**Verbosité :** pour des styles complexes, les styles en ligne peuvent rendre le composant verbeux et difficile à lire. 

---

#### Exercice 1 - Simple :
Créer un composant qui affiche un paragraphe de texte et utiliser des styles en ligne pour définir la couleur du texte et la taille de la police 

#### Solution
```jsx
import React, { Component } from 'react'

export default class InlineStyle extends Component {
  render() {
    const style = {
        color: 'green',
        fontSize: '60px',
    };

    return (
      <div>
        <p style={{
            color: 'red',
            fontSize: '20px',
            textDecoration: 'underline'
        }}>Superbe</p>
        <p style={style}>Superbe</p>
      </div>
    )
  }
}
```

---

#### Exercice 2 - Conditionnel :
Créez un composant MyButton qui accepte une prop isActive.
Si isActive est true, le bouton doit avoir un arrière-plan vert. Sinon, il doit être gris.
Utilisez des styles en ligne pour définir ces couleurs en fonction de la prop.
Vous souhaitez utiliser ce composant bouton dans un parent.
Le composant MyParent doit avoir un state local isActive qui détermine si le bouton est actif ou non.
Il doit également afficher le composant Button et lui passer la valeur de isActive comme prop.
Ajoutez un autre bouton dans MyParent qui, lorsqu'il est cliqué, bascule la valeur de isActive entre true et false.
Lorsque vous cliquez sur le bouton dans MyParent, le state isActive doit changer, 
ce qui à son tour change la couleur d'arrière-plan du composant Button.

#### Solution
**App.jsx**
```jsx
import MyParent from './components/MyParent'

function App() {

  return (
    <>
      <MyParent />
    </>
  )
}

export default App
```

**MyParent.jsx**
```jsx
import React, { useState } from "react";
import MyButton from "./Mybutton";

const MyParent = () => {
    const [active, setActive] = useState(false);

    return (
        <div>
            <MyButton isActive={active} />
            <hr></hr>
            <button onClick={() => setActive(!active)}>Je suis {active ? "actif" : "inactif"}</button>
        </div>
    );
};

export default MyParent;
```

**MyButton.jsx**
```jsx
import PropTypes from 'prop-types';

const MyButton = ({isActive}) => {
  const styleActive = {
      backgroundColor: 'green',
  };
  const styleInactive = {
      backgroundColor: 'grey',
  }
  return (
    <button style={isActive ? styleActive : styleInactive}>Mon bouton</button>
  );
};

MyButton.propTypes = {
  isActive: PropTypes.bool.isRequired,
};

export default MyButton;
```

---

#### Exercice 3 - Externe :
Créez un composant simple, comme un bouton .
Créez un fichier CSS externe pour ce composant.
Utilisez des sélecteurs CSS pour appliquer des styles spécifiques à ce composant.
Importez le fichier CSS dans votre composant React et appliquez-le.

#### Solution : 
**my-button.css**
```css
.my-button {
    background-color: blue;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
}
```

**MyButtonExt.jsx**
```jsx
import React from "react";
import "./my-button.css";

const MyButtonExt = () => {
  return (
    <div>
      <button className="my-button">Click me</button>
    </div>
  );
};
```

---

#### Exercice 4 - Menu de navigation :
Créez un composant de menu de navigation avec plusieurs liens.
Utilisez un fichier CSS externe pour styliser le menu.
Ajoutez des styles de survol pour les liens et assurez-vous que les styles changent au survol.


#### Solution
**Navigation.jsx**

```jsx
import React from "react";
import "./navigation.css";

const Navigation = () => {
  return (
    <nav>
      <ul>
        <li>
          <a href="#">Accueil</a>
        </li>
        <li>
          <a href="#">À propos</a>
        </li>
        <li>
          <a href="#">Services</a>
        </li>
        <li>
          <a href="#">Contact</a>
        </li>
      </ul>
    </nav>
  );
};

export default Navigation;
```

**navigation.css**
```css
nav {
  background-color: #333;
  color: #fff;
  display: flex;
  justify-content: center;
}

ul {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #fff;
  text-decoration: none;
}

a:hover {
  color: #f00;
}
```

---

#### Exercice 5 - Theme :
Créez un composant React qui permet à l'utilisateur de basculer entre un thème sombre et un thème clair.
Créez un fichier CSS externe contenant les styles appropriés pour les deux thèmes.
Lorsque l'utilisateur bascule entre les thèmes en cliquant sur un bouton, utilisez JavaScript pour ajouter ou supprimer les classes CSS correspondant au thème actuel sur l'ensemble de la page, ce qui changera dynamiquement le style de l'application en fonction du thème sélectionné.