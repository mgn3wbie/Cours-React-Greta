# V - Tools
## 1. Spread Operator:
Si vous avez un tableau et que vous souhaitez copier ses éléments dans un nouveau tableau, vous pouvez utiliser la syntaxe spread :
```js
	const arr = [1, 2, 3];
  const arr2 = [...arr];
  console.log(arr2) // [1, 2, 3]
```
pour ajouter un element:
```js
	const arr2 = [...arr,4];
  console.log(arr2); // [1, 2, 3, 4]
```
Sinon, comme les tableaux sont au même emplacement mémoire :
```js
	const arr3 = arr;
	arr3.push(5);
	console.log(arr3); // [1, 2, 3, 5]
	console.log(arr); // [1, 2, 3, 5]
```

---

#### Exercice 1 - Fusion de tableaux : 
Vous avez deux tableaux, utilisez le Spread Operator pour créer un nouveau tableau aliments qui contient tous les éléments des deux tableaux.
```js
const fruits = ["pomme", "banane", "cerise"];
const légumes = ["carotte", "brocoli"];
```

#### Solution
```js
const fruits = ["pomme", "banane", "cerise"];
const légumes = ["carotte", "brocoli"];
const aliments = [...fruits, ...légumes];
console.log(aliments);
```
---
#### Exercice 2 - Ajout d'éléments : 
Vous avez un tableau :  
```js
const nombres = [1, 2, 3];
```
Utilisez le Spread Operator pour ajouter les nombres 4, 5 et 6 à la fin du tableau sans modifier le tableau original.

#### Solution
```js
const nombres = [1, 2, 3];
const autresNombres = [...nombres, 4, 5, 6];
console.log(autresNombres); // [1, 2, 3, 4, 5, 6]
// possible de placer le spread operator où on veut 
const petitsNombres = [-2, -1, 0, ...nombres];
console.log(petitsNombres); // [-2, -1, 0, 1, 2, 3]
```
---

#### Exercice 3 - Clonage d'objets :
Vous avez un objet :  
```js
const voiture = { marque: "Toyota", modèle: "Corolla" };
```
Utilisez le Spread Operator pour créer un nouvel objet nouvelleVoiture qui est une copie de l'objet voiture, mais avec une propriété supplémentaire couleur: "rouge".

#### Solution
```js
const voiture = { marque: "Toyota", modèle: "Corolla" };
const voitureRouge = { ...voiture, couleur: "rouge" };
console.log(voiture); // {"marque":"Toyota","modèle":"Corolla"}
console.log(voitureRouge); // {"marque":"Toyota","modèle":"Corolla","couleur":"rouge"}
```
---

#### Exercice 4 - Fusion d'objets : 
Vous avez deux objets :  

```js
const infosPersonnelles = { nom: "Dupont", prénom: "Jean" };
const infosContact = { email: "jean.dupont@email.com", téléphone: "0123456789" };

```
Utilisez le Spread Operator pour fusionner ces deux objets en un seul objet infosComplètes.

#### Solution
```js
const infosCompletes = {...infosPersonnelles, ...infosContact};
console.log(infosCompletes); // {"nom":"Dupont","prénom":"Jean","email":"jean.dupont@email.com","téléphone":"0123456789"}
```
---
#### Exercice 5 - Input :
Créez un composant de classe qui contient un champ de saisie 
Lorsque l'utilisateur saisit une tâche et la valide,elle remplace l'ancienne valeur du state et s'affiché a l'ecran

**Aide :** 
> **Gestion des événements :**  
        Utilisez l'événement onChange sur l'élément \<input> pour détecter chaque modification du champ de saisie en utilisant une fonction de rappel qui prendra en argument l'événement lui-même, souvent désigné par event, permettant d'accéder à la valeur saisie via event.target.value. Cette fonction mettra à jour le state avec la nouvelle valeur.  
		  
> **Affichage de la valeur :**  
        Pour afficher la valeur actuelle de la tâche à l'écran, utilisez {this.state.task} dans votre méthode render. 

#### Solution
```jsx
import React from "react";

// Définition d'un composant de classe nommé InputComponent
class InputComponent extends React.Component {
  // Constructeur du composant
  constructor(props) {
    super(props); // Appel du constructeur de la classe parente (React.Component)
    // Initialisation du state avec une propriété "task" vide
    this.state = {
      task: "",
    };
  }

  // Méthode pour gérer les changements dans le champ de saisie
  handleInputChange = (event) => {
    // Mise à jour de la propriété "task" du state avec la valeur saisie par l'utilisateur
    this.setState({
      task: event.target.value,
    });
  };

  // Méthode pour rendre le composant
  render() {
    return (
      <div>
        {/* Champ de saisie qui utilise la valeur de "task" du state comme valeur et appelle handleInputChange à chaque modification */}
        <input
          type="text"
          value={this.state.task}
          onChange={this.handleInputChange}
          placeholder="Saisissez une tâche"
        />
        {/* Affichage de la tâche saisie par l'utilisateur */}
        <div>Votre tâche : {this.state.task}</div>
      </div>
    );
  }
}

// Exportation du composant pour qu'il puisse être utilisé dans d'autres fichiers
export default InputComponent;
```

---

## 2. Map:  
La méthode map est une méthode intégrée des tableaux en JavaScript utilisée en React pour transformer un tableau de données en un tableau d'éléments JSX.
La méthode map crée un nouveau tableau avec les résultats de l'appel d'une fonction fournie sur chaque élément du tableau appelant.
```js
const tasks = ['Manger', 'Dormir', 'Coder'];  
function TaskList() {
	return (
	<ul>
		{tasks.map((task, index) => (
		<li key={index}>{task}</li>
		))}
	</ul>
	);
}
```
Dans cet exemple, pour chaque tâche dans le tableau tasks, map crée un élément `<li>` contenant cette tâche. Le résultat est un tableau d'éléments `<li>`, qui est ensuite rendu à l'intérieur de l'élément `<ul>`.

**Key**  
L'attribut key est un élément spécial dans React. 
Lorsque vous créez une liste d'éléments générés dynamiquement en React (par exemple, en utilisant la méthode `.map()`), React a besoin d'une manière de distinguer chaque élément individuel de la liste.

!!! NOTE Il est important de noter que l'utilisation de l'*index* comme *key* n'est généralement pas recommandée, sauf si la liste n'est pas modifiée (pas d'ajouts, suppressions ou réorganisations d'éléments)

---

#### Exercice 1 - Liste de tâches :

Créez un composant de classe qui contient un champ de saisie et une liste vide (définie dans le state).
Lorsque l'utilisateur saisit une tâche et appuie sur "Entrée", ajoutez la tâche à la liste en utilisant this.setState.
Chaque tâche doit être stockée dans le state sous forme d'un tableau.

#### Solution
```jsx
import React from "react";

class TodoList extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      tasks: [],
      currentTask: "",
    };
  }

  // Gère les changements dans le champ de saisie
  handleChange = (event) => {
    this.setState({ currentTask: event.target.value });
  };

  // Ajoute la tâche actuelle à la liste des tâches lors de la soumission du formulaire
  handleSubmit = (event) => {
    event.preventDefault();
    if (this.state.currentTask.trim()) {
      // Pour éviter d'ajouter des tâches vides
      this.setState((prevState) => ({
        tasks: [...prevState.tasks, prevState.currentTask],
        currentTask: "",
      }));
    }
  };

  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          <input
            type="text"
            value={this.state.currentTask}
            onChange={this.handleChange}
            placeholder="Ajoutez une tâche"
          />
          <button type="submit">Ajouter</button>
        </form>
        <ul>
          {this.state.tasks.map((task, index) => (
            <li key={index}>{task}</li>
          ))}
        </ul>
      </div>
    );
  }
}

export default TodoList;
```  
---
#### Exercice 2 - formulaire d'inscription :

Créez un composant de classe avec deux champs de saisie : "Nom d'utilisateur" et "Mot de passe" (définis dans le state).
Ajoutez un bouton "S'inscrire".
Lorsque l'utilisateur remplit les champs et clique sur "S'inscrire", 
stockez les informations saisies dans le state en utilisant this.setState et affichez un message de confirmation.
Assurez-vous d'ajouter une validation simple, comme vérifier que le champ du mot de passe n'est pas vide.

#### Solution
```jsx
import React from "react";

// Définition du composant SignupForm comme une classe étendant React.Component
class SignupForm extends React.Component {
  // Initialisation de l'état local du composant
  state = {
    username: "",
    password: "",
  };

  // Gestionnaire d'événement pour suivre les modifications des champs de saisie
  handleChange = (event) => {
    const name = event.target.name; // Récupération du nom du champ (username ou password)
    this.setState({
      [name]: event.target.value, // Mise à jour de l'état avec la nouvelle valeur saisie
    });
  };

  // Gestionnaire d'événement pour le formulaire lors de la soumission
  handleSubmit = (event) => {
    event.preventDefault(); // Empêche le comportement par défaut du formulaire (rechargement de la page)
    if (this.state.password === "") {
      alert("Veuillez entrer un mot de passe valide."); // Affiche une alerte si le mot de passe est vide
    } else {
      alert(
        "Inscription réussie avec le nom d'utilisateur : " + this.state.username // Affiche une alerte avec le nom d'utilisateur saisi
      );
    }
  };

  // Méthode de rendu du composant
  render() {
    return (
      // Formulaire avec un gestionnaire d'événement pour la soumission
      <form onSubmit={this.handleSubmit}>
        <label>
          Nom d'utilisateur:
          <input
            type="text"
            name="username"
            value={this.state.username}
            onChange={this.handleChange} // Gestionnaire d'événement pour suivre les modifications du champ
          />
        </label>
        <br />
        <label>
          Mot de passe:
          <input
            type="password"
            name="password"
            value={this.state.password}
            onChange={this.handleChange} // Gestionnaire d'événement pour suivre les modifications du champ
          />
        </label>
        <br />
        <input type="submit" value="S'inscrire" />{" "}
        {/* Bouton pour soumettre le formulaire */}
      </form>
    );
  }
}

// Exportation du composant pour pouvoir l'utiliser ailleurs dans l'application
export default SignupForm;
```
  
## 3. Hooks et UseState : 
Les **Hooks** sont une fonctionnalité introduite dans React 16.8 qui permettent d'utiliser des fonctionnalités de React telles que l'état et les effets sans avoir à écrire de classes.
#### Hooks : 
Les **Hooks** sont des fonctions qui permettent de *"s'accrocher"* aux fonctionnalités de l'état et du cycle de vie de React à partir de composants fonctionnels.   
Ils ne fonctionnent pas à l'intérieur des classes, mais permettent d'utiliser React sans classes. 
#### useState : 
Avant l'introduction des **Hooks** dans React, l'utilisation de l'état local était principalement limitée aux composants de classe.
Cependant, avec **useState**, les composants fonctionnels peuvent également avoir un état.  
Le **useState** est un **hook** de React qui permet de définir et de mettre à jour l'état d'un composant fonctionnel. Il est utilisé pour stocker des données qui peuvent être modifiées et qui doivent être conservées entre les rendus.   

La syntaxe de **useState** est la suivante :  
`const [state, setState] = useState(initialState);` où `state` est la variable qui contient l'état actuel, `setState` est la fonction qui permet de mettre à jour l'état et `initialState` est la valeur initiale de l'état.  
  
__Voici un exemple d'utilisation de useState :__
``` jsx
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}

useState peut également être utilisé avec des objets :
const [id, setId] = useState({ name: '', age: 0 });
```

Pour mettre à jour un objet, il est important de se rappeler que setState ne fusionne pas automatiquement l'objet. Vous devez le faire manuellement : 
`setId(prevState => ({ ...prevState, name: 'Alice' }));`
  
  
Il est tout à fait possible d'utiliser plusieurs appels useState dans un seul composant :
```jsx
const [age, setAge] = useState(0);
const [fruit, setFruit] = useState('banane');
const [todos, setTodos] = useState([{ text: 'Apprendre les Hooks' }]);
```
Les composants fonctionnels sont devenus de plus en plus populaires en raison de leur syntaxe plus concise et de leur facilité de développement, de compréhension et de test. De plus, l'équipe React continue d'introduire davantage de Hooks pour les composants fonctionnels, ce qui les rend encore plus puissants.

### Gestion des événements onClick dans React:
Dans React, la gestion des événements est très similaire à celle des éléments DOM, mais avec quelques différences syntaxiques. 
Par exemple, les événements React sont nommés en camelCase plutôt qu'en minuscules.

Au lieu d'utiliser une chaîne de caractères comme gestionnaire d'événements, 
comme c'est le cas en HTML pur, avec JSX, vous passez une fonction.  
        `<button onClick={() => this.uneFonction()}></button> `

---

#### Exercice 1. Compteur simple :

Créez un composant fonctionnel qui affiche un nombre (initialisé à 0 avec le Hook useState).
Ajoutez un bouton "Incrémenter" qui, lorsqu'il est cliqué, augmente la valeur du compteur de 1 en utilisant setCount (ou le nom que vous donnez à la fonction de mise à jour du Hook useState).

#### Solution:  

```jsx
import { useState } from "react";

function CounterComponent() {
    // Initialisation de l'état "count" à 0
    const [count, setCount] = useState(0);

    return (
        <div>
            <p>{count}</p> {/* Affichage de la valeur actuelle du compteur */}
            <button onClick={() => setCount(count + 1)}>Incrémenter</button>
        </div>
    );
}

export default CounterComponent; 
```
---
#### Exercice 2. Interrupteur:

Créez un composant fonctionnel qui affiche "Off" initialement (initialisé avec le Hook useState).
Ajoutez un bouton qui, lorsqu'il est cliqué, change l'affichage entre "On" et "Off" en utilisant setToggle (ou le nom que vous donnez à la fonction de mise à jour du Hook useState).

#### Solution :  
```jsx
import { useState } from "react";

function Toggle() {
  // Utilisation du Hook useState pour initialiser l'état "toggle" à false
  // "toggle" représente l'état actuel (On/Off)
  // "setToggle" est la fonction qui permet de mettre à jour cet état
  const [toggle, setToggle] = useState(false);

  // Fonction pour gérer le clic sur le bouton
  // Elle inverse l'état actuel de "toggle" à chaque appel
  const handleClick = () => {
    setToggle(!toggle);
  };

  return (
    <div>
      {/* Bouton qui, lorsqu'il est cliqué, appelle la fonction handleClick */}
      <button onClick={handleClick}>Toggle</button>

      {/* Affichage conditionnel de l'état actuel :
           Si "toggle" est vrai, affiche "On", sinon affiche "Off" */}
      <p>{toggle ? "On" : "Off"}</p>
    </div>
  );
}

// Exportation du composant pour pouvoir l'utiliser ailleurs dans l'application
export default Toggle;
```
---
#### Exercice 3. Input :   

Créez un composant fonctionnel qui contient un champ de saisie.
Lorsque l'utilisateur saisit une valeur, elle remplace l'ancienne valeur initialisée avec le Hook useState et s'affiche à l'écran.

#### Solution : 
```jsx
import React, { useState } from "react";

const TaskInput = () => {
  // Initialisation de l'état "task" avec une chaîne vide
  const [task, setTask] = useState("");

  // Fonction pour gérer la saisie de l'utilisateur dans le champ de saisie
  const handleChange = (event) => {
    setTask(event.target.value);
  };

  return (
    <div>
      {/* Champ de saisie pour la tâche. La valeur et l'événement onChange sont liés à l'état "task" */}
      <input type="text" value={task} onChange={handleChange} />

      {/* Affichage de la tâche actuelle */}
      <p>Tâche actuelle : {task}</p>
    </div>
  );
}

export default TaskInput;
```

---

#### Exercice 4. Liste de taches :
Créez un composant fonctionnel qui contient un champ de saisie 
```jsx
<form onSubmit={}>
	<input
		type="text"
		value={}
		onChange={}
		placeholder="Ajoutez une tâche"
	/>
	<button type="submit">Ajouter</button>
</form>
```
et une liste vide (ul li).

Lorsque l'utilisateur saisit une tâche et appuie sur "Ajouter", la tâche doit être ajoutée à la liste. 
Les tâches doivent être stockées dans un tableau à l'aide du Hook useState

> La méthode `map()` parcourt chaque élément du tableau sur lequel elle est appelée, un par un, de gauche à droite
Pour chaque élément du tableau, map() applique une fonction de transformation . 
Cette fonction peut prendre jusqu'à trois arguments : 
  l'élément actuel du tableau, 
  l'index de l'élément actuel dans le tableau, 
  et le tableau lui-même. 
  Cette fonction retourne le nouvel élément transformé.

#### Solution: 
```jsx
import React, { useState } from "react";

function TaskList() {
  // Déclaration de la variable d'état tasks avec le Hook useState
  const [tasks, setTasks] = useState([]);

  // Fonction appelée lors de la soumission du formulaire
  const handleSubmit = (event) => {
    event.preventDefault(); // Empêche le comportement par défaut du formulaire
    const newTask = event.target.elements.task.value; // Récupère la valeur saisie dans le champ de saisie
    setTasks([...tasks, newTask]); // Ajoute la nouvelle tâche au tableau tasks en utilisant la fonction setTasks et la syntaxe de propagation de tableau
    event.target.reset(); // Réinitialise le formulaire
  };

  // Retourne un élément div qui contient un formulaire avec un champ de saisie et un bouton "Add", ainsi qu'une liste non ordonnée (ul) qui affiche chaque tâche saisie par l'utilisateur en utilisant la méthode map pour parcourir le tableau tasks et créer un élément li pour chaque tâche.
  return (
    <div>
      <form onSubmit={handleSubmit}>
        <input type="text" name="task" placeholder="Enter task" />
        <button type="submit">Add</button>
      </form>
      <ul>
        {tasks.map((task, index) => (
          <li key={index}>{task}</li>
        ))}
      </ul>
    </div>
  );
}

export default TaskList;
```
---
#### Exercice 5 - Formulaire d'inscription :  
Créez un composant fonctionnel qui contient deux champs de saisie : "Nom d'utilisateur" et "Mot de passe". Ajoutez un bouton "S'inscrire". Lorsque l'utilisateur saisit des informations et clique sur le bouton, ces informations doivent être stockées et un message de confirmation doit être affiché.  
N'oubliez pas d'ajouter une validation pour les entrées, par exemple, en vous assurant que le mot de passe n'est pas laissé vide.

#### Solution
```jsx
import React, { useState } from "react";

// Définition du composant fonctionnel Signup
function Signup() {
  // Initialisation des états pour le nom d'utilisateur, le mot de passe et le message
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");
  const [message, setMessage] = useState("");

  // Fonction pour gérer la soumission du formulaire
  const handleSubmit = (event) => {
    event.preventDefault(); // Empêche le rechargement de la page lors de la soumission du formulaire

    // Vérifie si le mot de passe est vide
    if (password.trim() === "" || username.trim() === "") {
      setMessage("champs"); // Affiche un message d'erreur
    } else {
      setMessage(`Bienvenue ${username} !`); // Affiche un message de bienvenue
      setUsername(""); // Réinitialise le champ du nom d'utilisateur
      setPassword(""); // Réinitialise le champ du mot de passe
    }
  };

  return (
    <div>
      {/* Formulaire d'inscription */}
      <form onSubmit={handleSubmit}>
        <label>
          Nom d'utilisateur:
          {/* Champ de saisie pour le nom d'utilisateur */}
          <input
            type="text"
            value={username}
            onChange={(event) => setUsername(event.target.value)}
          />
        </label>
        <label>
          Mot de passe:
          {/* Champ de saisie pour le mot de passe */}
          <input
            type="password"
            value={password}
            onChange={(event) => setPassword(event.target.value)}
          />
        </label>
        {/* Bouton pour soumettre le formulaire */}
        <button type="submit">S'inscrire</button>
      </form>
      {/* Affichage du message (erreur ou bienvenue) */}
      <p>{message}</p>
    </div>
  );
}

// Exportation du composant pour pouvoir l'utiliser ailleurs dans l'application
export default Signup;
```
---
#### Exercice 6 - Methodes :
- Créez un composant ParentComponent qui contient une méthode handleClick qui affiche un message dans la console lorsque le bouton est cliqué.
- Créez un composant ChildComponent qui affiche un bouton.
- Passez la méthode handleClick en tant que prop à ChildComponent.
- Utilisez la méthode handleClick en tant que gestionnaire d'événements pour le bouton dans ChildComponent.
- Lorsque vous cliquez sur le bouton dans ChildComponent, la méthode handleClick dans ParentComponent sera appelée et le message sera affiché dans la console. 

#### Solution
**ChildComponent.jsx**
``` jsx
import PropTypes from 'prop-types';
const ChildComponent = ({ handleClick }) => {
    return (
        <div>
            <button onClick={handleClick}>Click me</button>
        </div>
    );
};
ChildComponent.propTypes = {
    handleClick: PropTypes.func.isRequired,
};
export default ChildComponent;
```
**ParentComponent.jsx**
``` jsx
import ChildComponent from "./ChildComponent";

const ParentComponent = () => {
    const handleClick = () => {
        console.log("Button clické dans ParentComponent");
    };

    return (
        <div>
            <ChildComponent handleClick={handleClick} />
        </div>
    );
};

export default ParentComponent;
```
**App.jsx**
```jsx
import ParentComponent from './components/ParentComponent'

function App() {
  return (
    <>
      <ParentComponent />
    </>
  )
}
export default App
```