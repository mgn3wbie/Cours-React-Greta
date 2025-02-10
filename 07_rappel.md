# VII - Rappels
## 1. Destructuring

La destructuration en JavaScript est une fonctionnalité qui permet de décomposer des objets et des tableaux en éléments individuels. 
Cela facilite l'extraction de valeurs spécifiques et rend le code plus lisible
`const { prop1, prop2 } = objet;`
Vous définissez des variables `prop1` et `prop2` pour extraire les propriétés `prop1` et `prop2` de l'objet `objet`.
  
**Exemple :**
```jsx
const personne = { nom: "Alice", age: 30 };
const { nom, age } = personne;
console.log(nom);  // "Alice"
console.log(age);  // 30
Vous pouvez extraire plusieurs propriétés en une seule ligne.

const fruits = ["pomme", "banane", "raisin"];
const [premier, deuxieme] = fruits;
console.log(premier);  // "pomme"
console.log(deuxieme); // "banane"
```
Vous pouvez définir des valeurs par défaut pour les propriétés au cas où elles ne seraient pas définies dans l'objet.
```jsx
const personne = { nom: "Bob" };
const { nom, age = 25 } = personne;
console.log(nom);  // "Bob"
console.log(age);  // 25 (valeur par défaut)
```
Si la propriété age n'est pas définie dans l'objet, elle prendra la valeur par défaut de 25.

---

#### Exercice 1 : Destructuration d'objet simple
Créez un objet personne avec des propriétés telles que name, age, et country. 
Ensuite, utilisez la destructuration pour extraire ces propriétés et affichez-les dans la console.

#### Solution
```jsx 
const personne = { nom: "Alice", age: 30, pays: "USA" };
const {nom, age, pays} = personne;
console.log(nom) // Alice
console.log(age) // 30
console.log(pays) // USA
```

---

## 2. Key

```jsx
import React from 'react';
  function App() {
    const items = ['pomme', 'banane', 'orange'];

    return (
      <div>
        <h1>Liste d'éléments</h1>
        <ul>
          {items.map((item, index) => (
            <li key={index}>{item}</li>
          ))}
        </ul>
      </div>
    );
  }
  export default App;
  ```
  
Nous avons un tableau d'éléments ['pomme', 'banane', 'orange']. 
Nous utilisons .map() pour itérer dessus et renvoyer un nouveau tableau d'éléments `<li>` avec le nom de l'élément comme contenu textuel. 
La propriété key est utilisée pour identifier de manière unique chaque élément de la liste.

!!! NOTE Notez que la méthode .map() renvoie un nouveau tableau et ne modifie pas le tableau d'origine.
!!! ATTENTION La propriété key est importante pour des raisons de performance et doit être un identifiant unique pour chaque élément de la liste.


Il existe plusieurs façons de créer une clé unique pour chaque élément dans une liste. 
Voici quelques exemples :
> **Utiliser un identifiant unique provenant des données :**
    Si vous avez des données avec un identifiant unique, vous pouvez l'utiliser comme clé. Par exemple :
```jsx
const items = [ { id: 1, name: 'apple' }, { id: 2, name: 'banana' }, { id: 3, name: 'orange' }, ];
<ul> {items.map((item) => ( <li key={item.id}>{item.name}</li> ))} </ul>
```

> **Utiliser l'index de l'élément :**
> Si vous n'avez pas d'identifiant unique dans les données, vous pouvez utiliser l'index de l'élément dans le tableau comme clé.
> ```<ul> {items.map((item, index) => ( <li key={index}>{item}</li> ))}</ul>```
> Cependant, cela peut causer des problèmes si l'ordre des éléments dans le tableau change.
    
!!! SUCCESS Il existe des bibliothèques telles que UUID qui peuvent générer des clés uniques pour vous.
**Exemple :**
```jsx
    import { v4 as uuidv4 } from 'uuid';
    const items = ['apple', 'banana', 'orange'];
    <ul>{items.map((item) => (<li key={uuidv4()}>{item}</li>))}</ul>
```
---
#### Exercice 1 : Création d'une liste simple
Créez un composant React qui rend une liste de 3 ou 4 noms. 
Utilisez une boucle pour parcourir un tableau de noms et affichez-les à l'aide d'éléments JSX `<li>`. 
Ajoutez des clés uniques à chaque élément de la liste.

#### Solution :
```jsx
import React from 'react'

const ListComponent = () => {
    const copains = ['toto', 'tata', 'tutu', 'titi'];
  return (
    <div>
      <ul>
        {/* La clé unique peut être l'index, mais il est préférable d'utiliser une valeur unique si possible */}
        {copains.map((copain, index) => <li key={index}>{copain}</li>)}
      </ul>
    </div>
  )
}

export default ListComponent
```
