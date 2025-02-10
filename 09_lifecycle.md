# IX - Cycle de vie des composants

## 1. Introduction à useEffect
Le gestionnaire d'effets secondaires de React `useEffect` est l'un des hooks les plus puissants  en React. 
Il permet d'effectuer des opérations **après** le rendu d'un composant, telles que des appels à des API, la gestion d'événements ou la modification de l'état. 
Il est essentiel pour gérer les effets secondaire dans une application React.

## 2. Effets de bord
Avant de plonger dans `useEffect`, il est important de comprendre ce qu'est un effet de bord en programmation. 
Un effet de bord est toute opération qui affecte quelque chose en dehors de la portée immédiate de la fonction qui l'exécute.  

Dans le contexte de React, cela peut inclure :
- Modifier le titre du document
- Effectuer des requêtes réseau
- Manipuler directement le DOM
- Configurer des abonnements ou des timers

#### Exercice 1 - Declencher un effet de bord : 
Voici un exercice qui vous permettra de constater les problèmes liés à l'absence de `useEffect` pour la gestion des effets de bord, en particulier pour la création et le nettoyage d'intervalles.

Créer un composant React fonctionnel nommé ConsoleLogger qui affiche un message dans la console toutes les 2 secondes, en incrémentant un compteur à chaque fois.  

**Contraintes :**
Ne pas utiliser le hook useEffect dans votre solution.
Implémenter la logique de l'intervalle directement dans le corps du composant.
Afficher dans la console le message "Message affiché toutes les 2 secondes" suivi du nombre d'incrémentations effectuées.

#### Solution : 
```jsx
function ConsoleLogger() {
  var inc = 0
  setInterval(() => {
    inc++
    console.log("Message affiché toutes les 2 secondes" + inc);
  }, 2000);
  return (
    <div>
      <p>Regardez la console, un message s affiche toutes les 2 secondes.  </p>
    </div>
  );
}

export default ConsoleLogger;
```

## 3. Pourquoi cet exemple pose problème
**Exécution à chaque rendu :**
Dans un composant fonctionnel, le corps de la fonction s'exécute à chaque rendu. Cela signifie que chaque fois que le composant se rend (par exemple, lors d'un rechargement ou d'une mise à jour), un nouvel appel à `setInterval` est créé. Au fil du temps, plusieurs intervalles seront actifs simultanément, ce qui entraîne l'affichage multiple du message et un risque de fuite de mémoire
**Pas de nettoyage :**
Sans `useEffect`, il n'y a pas de mécanisme pour nettoyer (clear) l'intervalle lorsque le composant est démonté. Cela peut continuer à exécuter la fonction de rappel même après que le composant a été retiré de l'interface, ce qui n'est pas un comportement désirable.

## 4. Pourquoi useEffect ?
Dans les composants React, nous voulons souvent exécuter du code après que le composant ait été rendu à l'écran. 
`useEffect` nous permet de faire cela de manière déclarative, en nous assurant que notre code s'exécute au bon moment dans le cycle de vie du composant.

**Syntaxe de base:**
   ```jsx
   useEffect( () => {
    // Code de l'effet
  } , []  )
  ```
  
**Décomposons cette syntaxe :**
useEffect prend deux arguments:
- Une fonction( )
- Un tableau de dépendances [ ] (optionnel)

La fonction passée à useEffect sera exécutée après chaque rendu du composant.
Le tableau de dépendances permet de contrôler quand l'effet doit être ré-exécuté.

---

#### Exercice 1 : Message de montage dans la console
**Objectif :**
Afficher un message dans la console une seule fois, lors du montage du composant.

**Instructions :**
Créez un composant fonctionnel.
Utilisez useEffect avec un tableau de dépendances vide pour afficher un message ("Composant monté") dans la console après le premier rendu.

#### Solution :
```jsx
export default function Exercice() {
    useEffect(() => {
      console.log("Composant monté");
    }, []);
  return (
    <div>
      Regardez la console pour le message de montage.
    </div>
  )
}
```

---

#### Exercice 2 : Affichage et mise à jour d'un compteur
**Objectif :**
Utiliser useEffect pour surveiller un state (compteur) et afficher sa valeur dans la console à chaque changement.

**Instructions :**
- Créez un composant avec un compteur initialisé à 0.
- Ajoutez un bouton pour incrémenter le compteur.
- Utilisez `useEffect` avec le compteur comme dépendance pour afficher sa nouvelle valeur à chaque mise à jour.


!!! SUCCESS Dans ce cas précis, on pourrait obtenir un résultat similaire sans utiliser useEffect. Cependant, l'utilisation de useEffect dans cet exemple illustre des concepts importants :
    **Séparation des préoccupations :** `useEffect` permet de séparer la logique de rendu (ce qui est affiché) de la logique des effets secondaires (comme la journalisation).
    **Contrôle précis de l'exécution :** on peut contrôler exactement quand le log se produit (après le rendu et seulement quand count change).
    **Anticipation de cas plus complexes :** cette structure prépare à des scénarios plus complexes où `useEffect` devient essentiel.

#### Solution : 
```jsx
import React, { useEffect, useState } from 'react'

export default function Compteur() {
    const [compteur, setCompteur] = useState(0);
    useEffect(() => {
          console.log("Mon compteur = " + compteur);
        }, [compteur]); // L'effet se déclenche lorsque "compteur" change
        
    const incrementer = () => {
        setCompteur(compteur + 1);
    }
  return (
    <div>
        <p>Mon compteur = {compteur}</p>
      <button onClick={incrementer}>Incrémenter</button>
    </div>
  )
}
```
---

#### Exercice 3 : Timer avec nettoyage
**Objectif :**
Créer un timer qui incrémente une valeur toutes les secondes et nettoyer cet intervalle lors du démontage du composant.

**Instructions :**
- Créez un composant avec un état pour le temps (initialisé à 0).
- Utilisez useEffect pour démarrer un intervalle qui incrémente ce temps toutes  les secondes.
- Retournez une fonction de nettoyage qui efface l'intervalle.

#### Solution :
```jsx 
import React, { useEffect, useState } from 'react'

export default function IntervalComponent() {
    const [seconds, setSeconds] = useState(0);
    

    useEffect(() => {
        const interval = setInterval(() => {
            setSeconds(prev => prev + 1);
          }, 1000);

        return () => clearInterval(interval);
    }, []); // S'execute une seule fois


  return (
    <div>
      <h3>Temps passé sur cette page = {seconds} secondes</h3>
    </div>
  )
}
```
---
#### Exercice 4 : Synchronisation du titre du document
**Objectif :**
Modifier le titre de la page (`document.title`) en fonction d'un compteur.

**Instructions :**
Créez un composant avec un compteur.
Utilisez useEffect pour mettre à jour document.title chaque fois que le compteur change.

#### Solution :
```jsx
export default function Compteur() {
    const [compteur, setCompteur] = useState(0);
    useEffect(() => {
        console.log("Mon compteur = " + compteur);
        document.title = `Mon compteur = ${compteur}`
        }, [compteur]);
    const incrementer = () => {
        setCompteur(compteur + 1);
    }
  return (
    <div>
        <p>Mon compteur = {compteur}</p>
      <button onClick={incrementer}>Incrémenter</button>
    </div>
  )
}
```
