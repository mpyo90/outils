# Instructions pour Claude

## Règles strictes

### Structure des fichiers
- **Un seul fichier HTML par outil** : tout le JavaScript et CSS doit être inline dans le même fichier
- **Jamais de React** : pas de JSX, pas de build step, pas de frameworks avec compilation
- **Jamais de build step** : pas de webpack, vite, npm build, etc.

### Dépendances
- Charger les librairies externes uniquement depuis des CDN (cdnjs, jsdelivr, unpkg, etc.)
- Minimiser le nombre de dépendances
- Préférer le JavaScript vanilla

### Fonctionnalités recommandées
- Utiliser le copier/coller comme mécanisme d'entrée/sortie principal
- Ajouter des boutons "Copier dans le presse-papier" pour faciliter l'utilisation mobile
- Persister l'état dans l'URL quand c'est utile (ex : pour le partage et les bookmarks)
- Utiliser localStorage pour les secrets (clés API) ou les données volumineuses
- Permettre l'ouverture de fichiers locaux via `<input type="file">`
- Proposer le téléchargement de fichiers générés
- **Navigation** : toujours inclure un lien en bas de page pour revenir à l'index (`index.html`)
  - Le lien doit être **en orange** (#cc785c) et se souligner au survol
  - Exemple de style CSS :
    ```css
    .back-link a {
        color: #cc785c;
        text-decoration: none;
    }
    .back-link a:hover {
        text-decoration: underline;
    }
    ```
  - Texte recommandé : "← Retour à la liste des outils" ou "← Retour à l'index des outils"

### Gestion de l'index
Quand un nouvel outil est créé, **toujours mettre à jour `index.html`** :

1. **Ajouter l'outil dans le tableau JavaScript** `tools` :
   ```javascript
   {
       icon: '🔧',  // Emoji représentatif de l'outil
       title: 'Nom de l\'outil',
       description: 'Description courte et claire de l\'outil (1-2 phrases)',
       url: 'nom-fichier.html',
       keywords: ['mot-clé1', 'mot-clé2', 'mot-clé3']  // Pour la recherche
   }
   ```

2. **Bonnes pratiques** :
   - Choisir un emoji pertinent et unique pour l'icône
   - Rédiger une description concise (max 2 phrases)
   - Ajouter des mots-clés pertinents pour faciliter la recherche
   - Vérifier que l'URL du fichier est correcte
   - Respecter la syntaxe JavaScript (virgules, guillemets échappés)

### Hébergement
- Les outils doivent pouvoir être hébergés sur GitHub Pages
- Pas de dépendance à un serveur backend

### Style de code
- Code lisible et maintenable
- Commentaires en français
- Noms de variables explicites
- **Rédaction en français correct** :
  - Respecter les règles typographiques françaises
  - Pas de majuscules intempestives (ex : éviter "Cliquez sur le Bouton" → préférer "Cliquez sur le bouton")
  - Seuls les noms propres, débuts de phrase et titres prennent une majuscule
  - Utiliser les accents correctement (É, è, à, ù, etc.)
- **Style sobre** : privilégier un ton neutre et professionnel dans tous les textes d'interface

### Design et interface
- **Palette de couleurs inspirée de Claude** :
  - Fond : beige/crème clair (#f5f5f0 ou similaire)
  - Boutons primaires : orange terracotta (#cc785c ou #d97757)
  - Boutons secondaires : gris doux ou contours
  - Texte : gris foncé (#2d2d2d ou #333)
  - Design minimaliste, épuré et chaleureux
- **Privilégier un design sobre et élégant** :
  - Éviter les couleurs criardes, saturées ou trop vives (ex : indigo, bleu électrique)
  - Préférer des palettes neutres, douces et chaleureuses
  - Assurer un bon contraste entre le fond et le contenu
- **Cohérence visuelle** :
  - Utiliser une palette de couleurs limitée et harmonieuse
  - Maintenir la cohérence dans les éléments similaires (boutons, notifications, focus)
- **Espacements suffisants** : prévoir des marges adéquates entre les sections pour une lecture confortable
- **Effets subtils** : privilégier les ombres douces et les transitions légères
- **Design responsive obligatoire** :
  - Toujours utiliser `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
  - Utiliser des media queries pour adapter l'interface aux mobiles, tablettes et ordinateurs
  - Tester la lisibilité et l'utilisabilité sur tous les formats d'écran
  - Prévoir des boutons et zones tactiles suffisamment grandes pour mobile (minimum 44x44px)

## APIs externes
- Utiliser uniquement des APIs qui supportent CORS (Cross-Origin Resource Sharing)
- Avant d'intégrer une API, vérifier qu'elle autorise les appels depuis le navigateur
- Privilégier les APIs publiques sans authentification quand c'est possible
- Pour les APIs nécessitant une clé, stocker la clé dans localStorage (jamais en dur dans le code)

## Sécurité
- **Validation des entrées utilisateur** :
  - Toujours valider et nettoyer les données entrées par l'utilisateur
  - Ne jamais faire confiance aux données provenant de l'utilisateur ou d'APIs externes
- **Prévention XSS (Cross-Site Scripting)** :
  - Utiliser `textContent` au lieu de `innerHTML` pour afficher du contenu utilisateur
  - Si `innerHTML` est nécessaire, sanitiser le contenu avec DOMPurify ou équivalent
  - Éviter `eval()`, `Function()` et les gestionnaires d'événements inline avec données utilisateur
- **Prévention des injections** :
  - Ne jamais construire du HTML/SQL/code dynamiquement avec des concaténations de strings
  - Utiliser des méthodes sûres du DOM (createElement, setAttribute, etc.)
- **Gestion des données sensibles** :
  - Ne jamais stocker de mots de passe ou données sensibles en clair
  - Avertir l'utilisateur si des données sont stockées dans localStorage
  - Ne pas logger de données sensibles dans la console
- **Content Security Policy** :
  - Éviter les scripts inline quand c'est possible (bien que nécessaire pour nos outils)
  - Documenter les risques potentiels si applicable

## Ce qu'il ne faut PAS faire
- Utiliser React, Vue, Angular ou tout framework nécessitant une compilation
- Séparer le code en plusieurs fichiers (HTML, CSS, JS séparés)
- Dépendre d'un serveur backend
- Créer des fichiers package.json ou des configurations de build
- Utiliser TypeScript (nécessite compilation)
