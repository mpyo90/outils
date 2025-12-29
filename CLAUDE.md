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

### Hébergement
- Les outils doivent pouvoir être hébergés sur GitHub Pages
- Pas de dépendance à un serveur backend

### Style de code
- Code lisible et maintenable
- Commentaires en français
- Noms de variables explicites

### Design et interface
- **Privilégier un design sobre et élégant** :
  - Éviter les couleurs criardes, saturées ou trop vives (ex : indigo)
  - Préférer des palettes neutres et douces
  - Assurer un bon contraste entre le fond et le contenu
- **Cohérence visuelle** :
  - Utiliser une palette de couleurs limitée et harmonieuse
  - Maintenir la cohérence dans les éléments similaires (boutons, notifications, focus)
- **Espacements suffisants** : prévoir des marges adéquates entre les sections pour une lecture confortable
- **Effets subtils** : privilégier les ombres douces et les transitions légères

## APIs externes
- Utiliser uniquement des APIs qui supportent CORS (Cross-Origin Resource Sharing)
- Avant d'intégrer une API, vérifier qu'elle autorise les appels depuis le navigateur
- Privilégier les APIs publiques sans authentification quand c'est possible
- Pour les APIs nécessitant une clé, stocker la clé dans localStorage (jamais en dur dans le code)

## Ce qu'il ne faut PAS faire
- Utiliser React, Vue, Angular ou tout framework nécessitant une compilation
- Séparer le code en plusieurs fichiers (HTML, CSS, JS séparés)
- Dépendre d'un serveur backend
- Créer des fichiers package.json ou des configurations de build
- Utiliser TypeScript (nécessite compilation)
