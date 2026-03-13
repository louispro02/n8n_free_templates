# 🚀 GETSTARTED - Construire son Hub IA Personnel

Guide complet pour créer votre propre interface de chat multi-agents IA, même si vous partez de zéro.

## 🎯 Ce que vous allez construire

Une application web **élégante, privée et personnelle** pour discuter avec vos agents IA préférés (comme un "ChatGPT personnel" mais 100% sous votre contrôle).

### Fonctionnalités clés
- ✅ **Interface moderne** - Design inspiré des meilleures apps (Claude, Linear)
- ✅ **100% privé** - Vos conversations restent dans votre navigateur (IndexedDB)
- ✅ **Multi-agents** - Basculez entre différents spécialistes (code, écriture, analyse...)
- ✅ **Compatible n8n** - Connectez-vous à vos workflows IA existants
- ✅ **Déploiement gratuit** - Hébergez sur Vercel/Netlify en 5 minutes
- ✅ **Aucun framework lourd** - Vanilla JS + Vite = lightning fast

## 📋 Prérequis absolus (5 minutes)

Avant de commencer, assurez-vous d'avoir:

1. **Node.js 18+** installé
   ```bash
   node --version  # Doit afficher v18.0.0 ou supérieur
   ```

2. **Un terminal** (Terminal sur Mac, PowerShell/CMD sur Windows, ou votre shell préféré)

3. **5 minutes de temps** - Oui, vraiment!

## 🚀 Installation guidée (copiez-collez ces commandes)

### Étape 1: Créer le projet
```bash
# Cela crée un nouveau dossier "mon-hub-ia" avec tout ce qu'il faut
npm init vite@latest mon-hub-ia -- --template vanilla

# Entrer dans le dossier
cd mon-hub-ia

# Installer les dépendances essentielles
npm install dexie marked dompurify
```

### Étape 2: Configurer vos secrets
```bash
# Créer le fichier de configuration
touch .env

# Ajouter vos credentials n8n (à personnaliser)
echo "VITE_N8N_USERNAME=votre_utilisateur_n8n
VITE_N8N_PASSWORD=votre_mot_de_passe_n8n" > .env
```

### Étape 3: Lancer pour voir
```bash
# Démarrer le serveur de développement
npm run dev

# Ouvrez http://localhost:5173 dans votre navigateur
# Vous devriez voir une page blanche - c'est normal pour l'instant!
```

## 🏗️ Structure du projet expliquée

Après l'installation, votre dossier ressemblera à ceci:

```
mon-hub-ia/
├── src/                  # Votre code va ici
│   ├── components/       # Boutons, fenêtres de chat, etc.
│   ├── services/         # Fonctions qui parlent à n8n et à la BDD
│   ├── db/               # Configuration de votre base de données locale
│   ├── styles/           # Le design et les couleurs
│   ├── utils/            # Petites fonctions utiles
│   ├── router.js         # Gère les URLs (#/chat, #/config, etc.)
│   └── main.js           # Le point de démarrage
├── public/               # Fichiers statiques (images, icônes)
├── index.html            # La page web principale
├── package.json          # Liste des dépendances
├── vite.config.js        # Configuration de Vite
├── .env                  # Vos secrets (NE JAMAIS PARTAGER CE FICHIER!)
└── README.md             # Ce fichier
```

## 🔐 Sécurité par conception (à ne jamais négliger)

### Ce qui reste PRIVÉ (jamais envoyé nulle part):
- **Tout votre historique de conversation** → Stocké dans IndexedDB (votre navigateur seulement)
- **La configuration de vos agents** → Aussi dans votre navigateur
- **Vos préférences personnelles** → Local storage

### Ce qui va vers n8n (votre serveur IA):
- **Les messages que vous envoyez** → Pour obtenir une réponse IA
- **Aucun donnée de compte** → Pas d'email, pas de nom d'utilisateur stocké côté client

### Protection obligatoire contre les attaques:
1. **Toujours sanitizer le HTML provenant de n8n** avec DOMPurify
2. **Ne jamais faire confiance aux données reçues** - valider tout
3. **Utiliser des variables d'environnement** pour les secrets (jamais dans le code)

## 🌐 Déploiement en 3 minutes

Une fois que ça marche en local:

### Option 1: Vercel (recommandé - gratuit)
```bash
npm i -g vercel
vercel
# Suivez les instructions, ajoutez vos VITE_* dans l'interface Vercel
```

### Option 2: Netlify (aussi excellent)
```bash
npm i -g netlify-cli
netlify deploy --prod
```

### Option 3: GitHub Pages (gratuit avec GitHub)
1. Poussez votre code sur GitHub
2. Dans les réglages du repo → Pages → Choisissez la branche `main`

## 🔧 Personnalisation immédiate

Après le `npm run dev` qui marche, commencez par:

1. **Changer le titre** dans `index.html`:
   ```html
   <title>Mon Hub IA Personnel</title>
   ```

2. **Modifier les couleurs** dans `src/styles/global.css`:
   ```css
   :root {
     --color-primary: #dc2626; /* Rouge Loret par défaut */
     /* Essayez: #2563eb (bleu), #059669 (vert), #7c3aed (violet) */
   }
   ```

3. **Ajouter votre logo** en remplissant le placeholder dans les composants

## 📚 Prochaines étapes suggérées

Une fois la base fonctionnelle:

1. **Ajoutez votre premier agent** en configurant un webhook n8n simple
2. **Implémentez la persistance** avec Dexie.js (tutoriel dans les commentaires du code)
3. **Ajoutez l'authentification** (mot de passe simple ou Firebase/Google)
4. **Améliorez l'UI** avec des animations subtiles
5. **Partagez avec un ami** pour tester en conditions réelles

## 💡 Philosophie du projet

> "Le meilleur outil IA est celui que vous contrôlez complètement."
> 
> Cette application vise à vous redonner le pouvoir sur vos interactions IA:
> - Vos données ne quittent jamais vos appareils
> - Vous décidez quels modèles utiliser
> - Vous pouvez l'héberger où vous voulez
> - Aucune abonnement surprise, aucune collecte de données

Commencez petit, itérez souvent, et surtout: amusez-vous bien!

---

*Vous êtes prêt? Lancez votre première commande ci-dessus et construisons quelque chose de génial ensemble.*
