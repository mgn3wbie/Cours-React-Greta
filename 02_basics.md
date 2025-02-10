# II - Bases
## 1. Create element

La méthode `createElement` est une fonction fondamentale de la bibliothèque React. 
Elle est utilisée pour créer et renvoyer des éléments React, 
qui sont les plus petites unités de construction des interfaces utilisateur React.

**Syntaxe de createElement :**
importation de React: 
```jsx
import React from 'react';
React.createElement(type, [props], [...children])
```

**type :**  élément que vous souhaitez créer. 
		Cela peut être une chaîne (pour les éléments DOM comme 'div', 'span', etc.) 

**props :** Un objet contenant les propriétés (ou "props") que vous souhaitez passer à l'élément. 
		Cela peut inclure des attributs comme className ou id pour les éléments DOM, 

**children :** Les éléments enfants qui doivent être imbriqués à l'intérieur de l'élément créé. 
		Cela peut être du texte, d'autres éléments React, ou un mélange des deux.

## 2. jsx
JSX est une extension de syntaxe pour JavaScript, recommandée par React pour décrire à quoi devrait ressembler l'interface utilisateur. Il ressemble à du HTML, mais il est intégré directement dans du JavaScript. Un élément JSX ressemble à une balise HTML.

#### Exercice 1 - Créer un titre avec JSX
Objectif : Utilisez JSX pour créer un titre (h1) .

##### Solution :
Ouvrez src/App.jsx dans votre éditeur de code.
Dans la fonction App, retournez le JSX suivant :

`<h1>Bienvenue à React !\</h1>`

#### Vérification :

Assurez-vous que votre serveur de développement est en cours d'exécution avec `npm run dev`.
Ouvrez votre navigateur et vous devriez voir le titre "Bienvenue à React !" affiché.

## 3. Snippets React/Redux/GraphQL/React-Native (ES7+)
Les snippets facilitent le développement en générant automatiquement des structures de code courantes. 

Voici les principaux :
**rcc :** Génère un composant React de classe avec un constructeur.
**rce :** Génère un composant React de classe avec une exportation.
**rfc :** Génère un composant React fonctionnel.
**rfce :** Génère un composant React fonctionnel avec une exportation.
**useState :** Génère le Hook useState pour la gestion de l'état.
**useEffect :** Génère le Hook useEffect.
