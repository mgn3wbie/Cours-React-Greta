# VIII - Routeur

React Router est une bibliothèque qui facilite la gestion de la navigation et des routes dans une application React. 
Elle permet de créer une application monopage (SPA) où le contenu affiché change dynamiquement en fonction de l'URL, sans avoir à recharger la page entière.

> **Les points clés à retenir :**
>  - **Navigation côté client :** 
    Permet de modifier l’URL et le contenu affiché sans recharger la page.
>  - **Composants dédiés :** 
    Offre des composants comme BrowserRouter, Routes, Route, Link, et des hooks comme useParams ou useNavigate pour faciliter la gestion des routes.
>  - **Routes imbriquées :** 
    Permet de structurer l’interface en sous-sections avec une hiérarchie de routes.

## 1. Installation :
Pour utiliser React Router, commencez par l'installer dans votre projet en exécutant la commande `npm install react-router-dom` dans le terminal à la racine du projet.

## 2. Organisation du projet:
  Une bonne organisation du code est primordiale, surtout dans des applications de grande envergure. 
  Créez vos pages dans le dossier src/routes ou src/pages. Par exemple :
  
my-react-app/
├── index.html
├── package.json
├── src
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── App.jsx
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── main.jsx
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── components
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── pages
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── Home.jsx
│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── Contact.jsx

**Les composants utilisés :**
  Le routage permet de définir comment votre application réagit aux différentes URL. 
  Il est essentiel d'afficher dynamiquement le contenu correspondant à l'URL sans recharger toute la page.

  Dans notre fichier principal, il faut définir notre routeur à l'aide des outils modernes de React Router :
    
- **BrowserRouter** (souvent renommé en **Router**): 
Ce composant crée un routeur qui utilise l'API d'historique du navigateur 
  
- **Routes :**
    Ce composant regroupe toutes vos définitions de routes, et permet de rechercher et d'afficher la première route correspondante à l'URL courante.

- **Route :**
    Chaque `<Route>` associe un chemin (path) à un composant à rendre (element). 
    Lorsque l'URL correspond au chemin défini, le composant associé s'affiche.

- **Link :**
    Ce composant permet de créer des liens de navigation dans votre application. 
    Il fonctionne comme une balise `<a>`, mais sans provoquer de rechargement complet de la page, ce qui assure une navigation fluide.

## 3. Mise en place du routage: 
  Nous allons intégrer le routage directement dans le composant principal, généralement nommé `App.jsx`

``` jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom"; // Importation des composants de React Router 

import Home from './pages/Home'; // Importation du composant Home
import About from './pages/About'; // Importation du composant About
import Contact from './pages/Contact'; // Importation du composant Contact

function App() {

  return (
    <Router>
      {/* La barre de navigation permet à l'utilisateur de se déplacer entre les pages */}
      <nav>
        <Link to="/">Accueil </Link>
        <Link to="/about">À propos </Link>
        <Link to="/contact">Contact </Link>
      </nav>

      {/* <Routes> contient l'ensemble des routes définies dans l'application  */}
      <Routes>
        {/* Définition de la route pour la page d'accueil  */}
        <Route path="/" element={<Home />} />
        {/* Définition de la route pour la page "À propos"  */}
        <Route path="/about" element={<About />} />
        {/* Définition de la route pour la page de contact  */}
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
}
export default App;
```

## 4. Explications détaillées :
- **Enveloppement avec `<Router>` :**
    Le composant `<Router>` (alias `<BrowserRouter>`) englobe toute l'application. 
    Cela signifie que tous les composants enfants ont accès aux fonctionnalités du routage, 
    telles que la modification de l'URL et l'accès aux informations de navigation.

- **La barre de navigation (`<nav>`) :**
    À l'intérieur de `<nav>`, nous utilisons `<Link>` pour créer des liens vers les différentes routes. Lorsque l'utilisateur clique sur un lien, React Router met à jour l'URL et affiche le composant correspondant sans recharger la page.

- **Définition des routes avec `<Routes>` et `<Route>` :**
    `<Routes>` agit comme un conteneur pour toutes vos routes.
    Chaque `<Route>` définit un chemin et l'élément à rendre lorsque ce chemin est visité. Par exemple :
      `path="/"` rend le composant `<Home />` pour la page d'accueil.
      `path="/about"` rend le composant `<About />` pour la page "À propos".
      `path="/contact"` rend le composant `<Contact />` pour la page de contact.

- **Utilisation des Composants de Navigation :**
  React Router fournit des composants de navigation tels que Link et NavLink pour créer des liens vers d'autres vues. 
  Le composant `NavLink` peut être utilisé pour créer des liens de navigation avec une classe CSS active lorsque le lien est actif :

- **Fonctionnalités Avancées :**
React Router offre des fonctionnalités avancées pour gérer la navigation comme la gestion des erreurs de routage.

---

#### Exercice 1 : Configuration de base du routage
**Objectif :**
Créez une application simple qui utilise React Router pour afficher trois pages distinctes : Accueil, À propos, et Contact.

**Instructions :**
- Créez un nouveau projet React 
- Installez React Router (`npm install react-router-dom`).
- Dans votre composant principal (ex. App.jsx), configurez `<BrowserRouter>`, `<Routes>` et `<Route>` pour définir les trois routes suivantes :
    `/ `→ Affichez le composant Home.
    `/about` → Affichez le composant About.
    `/contact` → Affichez le composant Contact.
- Ajoutez une barre de navigation avec des liens (utilisez <Link>).

En naviguant entre les liens, l’URL se met à jour et le contenu correspondant s’affiche sans recharger la page.


#### Solution :
!!! QUESTION _cf exemple précédent_

---

#### Exercice 2 : Utilisation de NavLink pour des liens actifs
**Objectif :**
Utilisez le composant NavLink pour styliser automatiquement le lien actif dans une barre de navigation.

**Instructions :**
- Dans votre barre de navigation, remplacez les `<Link>` par des `<NavLink>`.
Utilisez la propriété `className` avec une fonction pour retourner une classe "active" quand le lien correspond à l’URL actuelle.
- Créez un fichier CSS qui définit un style particulier pour la classe .active (par exemple, texte en gras ou en couleur différente).

**Résultat attendu :**
Lorsque vous naviguez, le lien correspondant à la page active s’affiche avec le style défini (ex. couleur différente).

#### Solution :
**App.jsx**
```jsx
import "./app.css"
import { BrowserRouter as Router, Routes, Route, NavLink } from "react-router-dom";
import Home from "./pages/Home";
import Profile from "./pages/Profile";
import About from "./pages/About";


function App() {
  return (

    <Router>
      <nav>
        <NavLink
          className={({ isActive }) => (isActive ? "active" : "")}
          to="/">Accueil</NavLink> |{" "}
        <NavLink
          className={({ isActive }) => (isActive ? "active" : "")}
          to="/profile">Profil</NavLink> |{" "}
        <NavLink
          className={({ isActive }) => (isActive ? "active" : "")}
          to="/about">À propos</NavLink>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/profile" element={<Profile />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </Router>
  );
}

export default App;
```

**app.css**
```css
.active {
  font-weight: bold;
  color: red;
}
```

---

## 3. Routes dynamiques avec paramètres

Lorsque des routes avec des segments dynamiques sont définies dans une application React, il est nécessaire de récupérer les valeurs transmises dans l'URL. Par exemple:
```jsx
<Route path="/articles/:id" element={<ArticleDetail />} />
```
!!! ATTENTION `:id` est un paramètre dynamique. 
    Pour accéder à la valeur de ce paramètre dans le composant `ArticleDetail`, il est recommandé d'utiliser le hook `useParams`.


Pour utiliser `useParams`, il convient de l'importer depuis react-router-dom :
    ```import { useParams } from 'react-router-dom';```

Dans le composant souhaité, l'appel à `useParams` permet d'obtenir un objet contenant les paramètres dynamiques définis dans la route.

```jsx
import React from 'react';
import { useParams } from 'react-router-dom';

function ArticleDetail() {
  // Récupère le paramètre "id" depuis l'URL
  const { id } = useParams();

// L'ID peut ensuite être utilisé pour effectuer des requêtes ou afficher des informations spécifiques
```

#### Exercice 1 - Routes avec param :
 
**Objectif :**
Créez une route dynamique qui affiche des informations basées sur un paramètre d’URL (par exemple, un identifiant d’utilisateur).

**Instructions :**
- Ajoutez une route comme /user/:id dans votre configuration de routes.
- Créez un composant User qui utilise le hook useParams pour récupérer le paramètre id.
- Affichez l’id dans le composant.

**Résultat attendu :**
En naviguant vers, par exemple, /user/42, le composant User affiche "42" ou un message indiquant l’ID de l’utilisateur.

---

#### Exercice 2 - Création d’une page 404
**Objectif :**
Implémentez une page `NotFound` pour gérer les URL qui ne correspondent à aucune route définie.

**Instructions :**
- Créez un composant `NotFound` qui affiche un message d’erreur 404.
- Ajoutez une route avec `path="*"` dans votre configuration de `<Routes>` qui rend le composant `NotFound`.
- 
**Résultat attendu :**
Lorsque vous accédez à une URL non définie, la page 404 s’affiche.

#### Solution :

**App.jsx**
```jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";
import Contact from "./pages/Contact";
import NotFound from "./pages/NotFound";

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Accueil</Link> |{" "}
        <Link to="/about">À propos</Link> |{" "}
        <Link to="/contact">Contact</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </Router>
  );
}

export default App;
```

**NotFound.jsx**

```jsx
function NotFound() {
  return <h2>404 - Page non trouvée</h2>;
}

export default NotFound;
```

---

#### Exercice 2 : Routes imbriquées avec Outlet
Lorsque vous définissez une route parent avec des routes enfants, `<Outlet>` indique où le composant correspondant à la route enfant sera rendu dans le layout commun.

**Objectif :**
Utilisez des routes imbriquées pour créer un layout commun avec des sous-pages.

**Instructions :**
Créez un composant `Dashboard` qui sert de layout. Dans ce composant, incluez une navigation interne (par exemple, pour "Profil" et "Paramètres") et utilisez `<Outlet>` pour afficher le contenu des routes enfants.
Configurez des routes imbriquées sous la route /dashboard :
`/dashboard/profile` → Affichez le composant Profile.
`/dashboard/settings` → Affichez le composant Settings.

**Résultat attendu :**
Lorsque vous naviguez dans le dashboard, la partie commune (ex. navigation) reste visible et le contenu spécifique s’affiche dans l’Outlet.

#### Solution : 
**App.jsx**
```jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import Dashboard from "./pages/Dashboard";
import Profile from "./pages/Profile";
import Settings from "./pages/Settings";

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Accueil</Link> |{" "}
        <Link to="/dashboard">Dashboard</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        
        <Route path="/dashboard/*" element={<Dashboard />}>
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
        
      </Routes>
    </Router>
  );
}

export default App;
```

**src/pages/Dashboard.jsx**
```jsx
import { Outlet, Link } from "react-router-dom";

function Dashboard() {
    return (
        <div>
            <h2>Dashboard</h2>
            <nav>
                <Link to="/dashboard/profile" >Profil</Link> |{" "}
                <Link to="/dashboard/settings" >Paramètres</Link>
            </nav>
            {/* Outlet affiche le contenu des routes enfants */}
            <Outlet />
        </div>
    );
}

export default Dashboard;
```

---

## 4. Redirection avec Navigate

`useNavigate` est un hook fourni par React Router (version 6 et ultérieure) qui permet de naviguer de manière programmatique dans l'application. 
Il est utile pour effectuer des redirections après des actions spécifiques (par exemple, après la soumission d'un formulaire ou lors d'un événement utilisateur) sans recourir à des liens statiques.

**Pour utiliser Le hook useNavigate:**
```jsx
import { useNavigate } from 'react-router-dom';
```
**dans le component :**
```jsx
const navigate = useNavigate();
navigate('/dashboard');  // Redirige vers la route /dashboard
```

!!! SUCCESS Le hook renvoie une fonction que l'on peut appeler avec un chemin en argument afin de rediriger l'utilisateur vers la route correspondante.

#### Exercice 1 - useNavigate:

**Objectif :**
Implémentez une redirection d’une ancienne URL vers une nouvelle.

**Instructions :**
Créez une route pour `/old` qui utilise le composant `<Navigate>` pour rediriger vers `/new`.
Créez un composant simple pour la route `/new` afin de vérifier que la redirection fonctionne.

**Résultat attendu :**
En accédant à `/old`, l’utilisateur est automatiquement redirigé vers `/new`.

#### Solution : 
**src/App.jsx**
```jsx
import { BrowserRouter as Router, Routes, Route, Link, Navigate } from "react-router-dom";
import NewPage from "./pages/NewPage";

function App() {
  return (
    <Router>
      <nav>
        <Link to="/old">Ancienne page</Link> |{" "}
        <Link to="/new">Nouvelle page</Link>
      </nav>
      <Routes>
        <Route path="/old" element={<Navigate to="/new" />} />
        <Route path="/new" element={<NewPage />} />
      </Routes>
    </Router>
  );
}

export default App;
```
**src/pages/NewPage.jsx**
```jsx
-------
function NewPage() {
  return <h2>Ceci est la nouvelle page</h2>;
}

export default NewPage; 
```

---

#### Exercice 2 - Navigation programmée avec useNavigate :

**Objectif :**
Utilisez le hook `useNavigate` pour rediriger l’utilisateur après une action 

**Instructions :**
Créez un composant avec un formulaire simple.
Dans le gestionnaire de soumission du formulaire, utilisez `useNavigate` pour naviguer vers une page de confirmation (ex. `/confirmation`).

**Résultat attendu :**
Après avoir soumis le formulaire, l’utilisateur est redirigé vers la page de confirmation sans rechargement de la page.

#### Solution :
**FormPage.jsx**
```jsx
import { useNavigate } from "react-router-dom";

function FormPage() {
    const navigate = useNavigate();

    const handleSubmit = (e) => {
        e.preventDefault();
        // Traitement du formulaire ici...
        // Puis redirection vers la page de confirmation
        navigate("/confirmation");
    };

    return (
        <div>
            <h2>Formulaire</h2>
            <form onSubmit={handleSubmit}>
                <input type="text" placeholder="Votre nom" />
                <button type="submit">Envoyer</button>
            </form>
        </div>
    );
}

export default FormPage;
```
**Confirmation.jsx**
```jsx
function Confirmation() {
    return <h2>Merci, votre formulaire a été soumis !</h2>;
}

export default Confirmation;
```
**App.jsx**
```jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import FormPage from "./pages/FormPage";
import Confirmation from "./pages/Confirmation";

function App() {
  return (
    <Router>
      <nav>
        <Link to="/form">Formulaire</Link>
      </nav>
      <Routes>
        <Route path="/form" element={<FormPage />} />
        <Route path="/confirmation" element={<Confirmation />} />
      </Routes>
    </Router>
  );
}

export default App;
```

---

#### Exercice 3 - Création d’un layout global :

**Objectif :**
Créez un layout global qui inclut un header, un footer et un espace pour le contenu (utilisez `<Outlet>`).

**Instructions :**
Créez un composant `Layout` qui contient un header (ex. logo, barre de navigation), un footer, et un `<Outlet>` pour le contenu principal.
Configurez vos routes pour que le composant `Layout` enveloppe toutes vos pages.

**Résultat attendu :**
Toutes les pages de votre application affichent le header et le footer, avec le contenu spécifique au milieu.

#### Solution :
**src/pages/Layout.jsx**
```jsx
import { Outlet, Link } from "react-router-dom";

function Layout() {
    return (
        <div>
            <header>
                <h1>Mon Application</h1>
                <nav>
                    <Link to="/">Accueil</Link> |{" "}
                    <Link to="/about">À propos</Link> |{" "}
                    <Link to="/contact">Contact</Link>
                </nav>
            </header>
            <main>
                <Outlet />
            </main>
            <footer>
                <p>&copy; 2025 Mon Application</p>
            </footer>
        </div>
    );
}

export default Layout;
```

**src/App.jsx**
```jsx
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Layout from "./pages/Layout";
import Home from "./pages/Home";
import About from "./pages/About";
import Contact from "./pages/Contact";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Layout />}>
          <Route index element={<Home />} />
          <Route path="about" element={<About />} />
          <Route path="contact" element={<Contact />} />
        </Route>
      </Routes>
    </Router>
  );
}

export default App;
```