# 🪄 PROMPT ULTIME - Créez votre Hub IA Personnel

Le prompt parfait pour guider un agent IA (vous-même ou un assistant) dans la création d'une application de chat multi-agents 100% personnelle, sécurisée et évolutive.

---

## 📝 INSTRUCTIONS D'UTILISATION

Copiez ce prompt complet dans votre outil IA préféré (Cursor, Copilot, ChatGPT avec Code Interpreter, etc.) et laissez-le vous guider étape par étape.

L'IA **doit vous poser des questions** avant de commencer à coder pour bien comprendre votre contexte spécifique.

---

# 🎯 CONTEXTE & OBJECTIF

**Tu es un expert en développement d'applications web modernes, spécialisé dans les architectures "local-first" et la protection de la vie privée.**

Je veux créer **"Mon Hub IA Personnel"** : une application web qui me permet de discuter en toute confidentialité avec mes agents IA personnalisés, hébergés sur mon instance n8n personnelle.

## 🔑 PRINCIPES NON NÉGOCIABLES

1. **Confidentialité absolue** : Aucune de mes données ne quitte mes appareils sans mon consentement explicite
2. **Propriété totale** : Je possède et contrôle 100% de l'application et de mes données
3. **Simplicité d'usage** : L'expérience doit être aussi fluide que discuter avec un ami
4. **Évolutivité** : Je dois pouvoir commencer simple et ajouter des fonctionnalités au fil du temps

---

## ❓ QUESTIONS OBLIGATOIRES (L'IA DOIT LES POSER)

Avant d'écrire une seule ligne de code, l'IA doit obtenir des réponses claires à ces questions:

### 1. 🔐 AUTHENTIFICATION & ACCÈS
```
[ ] Quelle méthode d'authentification préférez-vous?
    ☐ Simple mot de passe (pour usage personnel/familial)
    ☐ Authentification Google/GitHub (via Firebase ou Auth0)
    ☐ Microsoft Azure AD (environnement professionnel)
    ☐ Pas d'authentification (usage totalement personnel, déconseillé)

[ ] Voulez-vous un mode "invité" pour montrer l'app à quelqu'un sans lui donner accès à vos données?
```

### 2. 🤖 AGENTS IA & BACKEND
```
[ ] Quel type d'agents IA voulez-vous initialement configurer?
    ☐ Assistant général (comme ChatGPT)
    ☐ Expert dans un domaine spécifique (écriture, code, analyse données, etc.)
    ☐ Agent créatif (brainstorming, histoires, poèmes)
    ☐ Agent technique (débogage, explication de code, architecture)

[ ] Où hébergererez-vous vos workflows n8n?
    ☐ n8n.cloud (plan gratuit ou payant)
    ☐ Auto-hébergé sur votre serveur/VPS/Raspberry Pi
    ☐ Docker sur votre machine locale
    ☐ Non décidé - besoin de recommandations

[ ] Avez-vous déjà des workflows n8n fonctionnels que vous souhaitez connecter?
```

### 3. 💬 FONCTIONNALITÉS SOUHAITÉS
```
[ ] Quelles fonctionnalités sont importantes pour votre utilisation quotidienne?
    ☐ Streaming de réponse en temps réel (comme ChatGPT)
    ☐ Historique des conversations avec recherche
    ☐ Export/Import des conversations
    ☐ Modes de réponse (détaillé/concis/créatif/précis)
    ☐ Suggestions de démarrage basé sur l'agent sélectionné
    ☐ Organisation par catégories ou projets
    ☐ Partage sélectif de conversations spécifiques

[ ] Préférez-vous une interface:
    ☐ Ultra-minimaliste (comme une simple boîte de chat)
    ☐ Équilibrée (sidebar pour l'historique, zone principale pour le chat)
    ☐ Feature-rich (avec paramètres, thèmes, plugins, etc.)
```

### 4. 🎨 PERSONNALISATION & STYLE
```
[ ] Avez-vous des préférences de design?
    ☐ Couleurs spécifiques à utiliser (votre charte graphique personnelle)
    ☐ Logo ou symbole particulier à intégrer
    ☐ Police de caractères préférée
    ☐ Mode sombre/clair automatique ou manuel
    ☐ Accessibilité (contraste, taille de police ajustable)

[ ] Souhaitez-vous que l'application:
    ☐ Rappelle une application spécifique que vous aimez (Notion, Linear, Claude, etc.)
    ☐ Soit totalement unique et personnelle
    ☐ Suive les tendances du design actuel
```

### 5. 🚀 DÉPLOIEMENT & MAINTENANCE
```
[ ] Où prévoyez-vous d'héberger l'application finale?
    ☐ Vercel (recommandé pour la simplicité)
    ☐ Netlify
    ☐ GitHub Pages
    ☐ Votre propre serveur/VPS
    ☐ Non décidé

[ ] Quel niveau de maintenance êtes-vous prêt à assurer?
    ☐ "Je veux que ça marche et j'oublie" (mises à jour automatiques préférées)
    ☐ "Je suis à l'aise pour mettre à jour occasionnellement"
    ☐ "J'aime comprendre et maintenir mon code moi-même"

[ ] Avez-vous des contraintes techniques?
    ☐ Budget mensuel maximal pour l'hébergement
    ☐ Restrictions réseau ou de sécurité (entreprise, école)
    ☐ Nécessité de fonctionner hors ligne partiellement
```

---

## 🏗️ ARCHITECTURE DE BASE RECOMMANDÉE

L'IA doit proposer cette structure comme point de départ, adaptable selon les réponses:

```
mon-hub-ia/
├── src/
│   ├── auth/                 # Selon choix: simple pwd, Firebase, MSAL
│   │   ├── auth-service.js
│   │   └── [firebase-config.js | msal.js | pwd-service.js]
│   │
│   ├── components/           # Composants réutilisables
│   │   ├── layout/           # Header, footer, sidebar communs
│   │   ├── chat/             # Interface de conversation principale
│   │   │   ├── chat-controller.js
│   │   │   ├── chat-view.js  # Séparation logique/présentation si complexe
│   │   │   ├── chat.css
│   │   │   └── chat-markdown.css
│   │   ├── login/            # Page d'authentification
│   │   ├── agent-selector/   # Sélection et découverte des agents
│   │   ├── agent-config/     # Gestion/configuration des agents (admin)
│   │   ├── conversation-list/# Historique avec recherche/filtrage
│   │   ├── message-input/    # Zone de saisie avec suggestions
│   │   └── settings/         # Préférences utilisateur
│   │
│   ├── services/             # Services métier
│   │   ├── api/              # Communication avec n8n
│   │   │   ├── chat-service.js       # Envoi/reception messages
│   │   │   ├── agent-service.js      # Gestion des agents
│   │   │   └── auth-service.js       # Si gestion auth côté client
│   │   ├── db/               # Services IndexedDB
│   │   │   ├── database.js           # Schéma Dexie
│   │   │   ├── agent-store.js        # CRUD agents
│   │   │   ├── conversation-store.js # CRUD conversations
│   │   │   └── message-store.js      # CRUD messages
│   │   └── utils/            # Fonctions transversales
│   │       ├── helpers.js            # Format dates, aléatoires, etc.
│   │       ├── security.js           # escapeHtml, validation inputs
│   │       └── storage.js            # Abstraction localStorage/sessionStorage
│   │
│   ├── styles/               # Design system
│   │   ├── global.css        # Variables CSS, reset, base
│   │   ├── animations.css    # Transitions et animations
│   │   ├── themes/           # Thèmes clair/sombre, personnalisables
│   │   └── components/       # CSS spécifique aux composants si besoin
│   │
│   ├── router.js             # Routage SPA (hash-based ou history)
│   ├── main.js               # Point d'entrée: init auth, router, services
│   └── app.js                # État global de l'application (optionnel)
│
├── public/                   # Assets statiques
│   ├── icons/                # SVG, favicons
│   └── images/               # Logo, illustrations
│
├── tests/                    # Si tests ajoutés plus tard
│   ├── unit/
│   └── integration/
│
├── .env                      # Variables d'environnement (gitignored!)
├── .env.example              # Template pour les autres
├── index.html                # Point d'entrée HTML
├── package.json              # Dépendances et scripts
├── vite.config.js            # Configuration Vite
├── README.md                 # Documentation du projet
└── CHANGELOG.md              # Historique des versions (à maintenir)
```

---

## 🔧 STACK TECHNIQUE RECOMMANDÉE

### Frontend (obligatoire)
- **Vite** - Build tool moderne et rapide
- **Vanilla JavaScript (ES Modules)** - Pas de framework pour légèreté et contrôle total
- **Dexie.js** - Wrapper simple pour IndexedDB (stockage local hors ligne)
- **Marked.js** - Conversion Markdown → HTML sécurisée
- **DOMPurify** - Protection XSS obligatoire pour le contenu IA
- **CSS Puriste** - Variables CSS, BEM-like, pas de CSS-in-JS complexe

### Backend IA (vous fournissez)
- **n8n** - Plateforme d'automatisation pour vos workflows IA
- **Webhooks n8n** - Endpoints que l'app va appeler
- **Credentials Basic Auth** - Sécurisation des webhooks (username/password dans .env)

### Authentification (selon choix)
- **Simple**: Mot de passe stocké en local (avec salt/hash)
- **Intermédiaire**: Firebase Auth (Google, GitHub, email/pass)
- **Avancé**: MSAL pour Azure AD (professionnel)

### Déploiement
- **Vercel/Netlify** - Hébergement static gratuit avec CDN
- **Variables d'environnement** - Pour les secrets (jamais dans le code!)

---

## 🔐 PROTOCOLE DE SÉCURITÉ (À SUIVRE RELIGIEUSEMENT)

### 1. Protection XSS (Non négociable)
```javascript
// Pour le contenu provenant de n8n (peut contenir du HTML dangereux)
import DOMPurify from 'dompurify';
import { marked } from 'marked';

function renderAssistantResponse(markdownText) {
  const html = marked.parse(markdownText);
  return DOMPurify.sanitize(html);
}

// Pour les entrées utilisateur (toujours considérer comme potentiellement dangereuses)
function escapeHtml(text) {
  const div = document.createElement('div');
  div.textContent = text;
  return div.innerHTML;
}
```

### 2. Gestion des credentials
- **Jamais** de credentials en clair dans le code ou commités
- **.env.example** avec placeholders, **.env** dans .gitignore
- Variables frontend doivent commencer par `VITE_` pour Vite
- Utiliser `import.meta.env.VITE_*` pour y accéder

### 3. Validation des entrées
- Toujours valider/sanitizer les données reçues de n8n
- Utiliser des whitelists pour les types de données attendues
- Limiter la taille des messages reçus/envoyés

### 4. Stockage local sécurisé
- Chiffrer les données sensibles si nécessaire (clé dérivée du mot de passe)
- Jamais stocker les tokens d'authentification en localStorage sans protection
- Prévoir une déconnexion qui efface proprement les données sensibles

### 5. Communications sécurisées
- HTTPS obligatoire en production
- Vérifier les certificats si auto-hébergé
- Timeout appropriés sur les requêtes fetch
- Gérer les erreurs réseau gracieusement

---

## 🚀 PLAN DE DÉVELOPPEMENT ITÉRATIF

L'IA doit suggérer cette approche itérative:

### Phase 0: Fondation (Jour 1)
- [ ] Projet Vite + Vanilla JS configuré
- [ ] Structure de dossiers créée
- [ ] .env.example créé
- [ ] Router basique avec #/login et #/chat
- [ ] Page de login simple (mot de passe ou choix auth)
- **Objectif**: Pouvoir lancer `npm run dev` et voir une page de login

### Phase 1: Chat basique (Jours 2-3)
- [ ] Service de communication avec n8n webhook (mock d'abord)
- [ ] Interface de chat minimaliste (zone messages + input)
- [ ] Envoi/reception de messages simples (JSON)
- [ ] Persistance basique avec Dexie (une seule conversation)
- [ ] Affichage sécurisé des réponses (DOMPurify + marked)
- **Objectif**: Pouvoir discuter avec un agent factice

### Phase 2: Multi-agents & Auth (Jours 4-5)
- [ ] Sélection d'agents avec stockage local
- [ ] Gestion vraie de l'authentification (selon choix)
- [ ] Création/switch entre conversations
- [ ] Historique des conversations dans sidebar
- [ ] Nettoyage du code, séparation des préoccupations
- **Objectif**: Pouvoir changer d'agent et voir son historique

### Phase 3: Fonctionnalités avancées (Semaine 2+)
- [ ] Streaming de réponse (EventSource ou polling intelligent)
- [ ] Suggestions de démarrage contextuelles
- [ ] Mode détaillé/concise toggleable
- [ ] Export/import des conversations
- [ ] Paramètres utilisateur (thème, notifications, etc.)
- [ ] Gestion des erreurs réseau avec retry et notifications
- **Objectif**: Expérience presque parfaite pour usage quotidien

### Phase 4: Polish & Deployment (Fin)
- [ ] Design raffiné avec animations subtiles
- [ ] Accessibilité au niveau WCAG AA
- [ ] Performance optimisée (lazy loading, code splitting)
- [ ] Documentation utilisateur intégrée
- [ ] Déploiement sur Vercel/Netlify avec variables d'environnement
- [ ] Tests de base sur les flux critiques
- **Objectif**: Application prête à partager avec proches/famille

---

## 📚 RESSOURCES ESSENTIELLES

### Apprentissage
- [Vite Documentation](https://vitejs.dev/guide/)
- [Dexie.js Tutorial](https://dexie.org/docs/Tutorial/)
- [Modern Vanilla JS Patterns](https://github.com/bevacqua/js-modules)
- [CSS Variables Guide](https://css-tricks.com/updating-a-css-variable-with-javascript/)

### Sécurité
- [DOMPurify Documentation](https://github.com/cure53/DOMPurify)
- [OWASP XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [Secure Password Storage](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)

### n8n & IA
- [n8n Webhooks Documentation](https://docs.n8n.io/integrations/builtin/webhooks/)
- [Building AI Agents with n8n](https://n8n.io/ai-agents/)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)

### Déploiement
- [Vite + Vercel Guide](https://vitejs.dev/guide/static-deploy.html#vercel)
- [Vite + Netlify Guide](https://vitejs.dev/guide/static-deploy.html#netlify)
- [Environment Variables in Vite](https://vitejs.dev/guide/env-and-mode.html)

---

## 💡 CONSEILS DE PRO

1. **Commencez TRÈS petit** - Une seule fonction qui marche vaut mieux que dix à moitié faites
2. **Committez souvent** - Chaque petite victoire mérite un commit
3. **Testez sur vrai appareil** - Ce qui marche sur localhost peut échouer sur mobile
4. **Documentez en construisant** - Un README qui évolue avec le projet vaut son pesant d'or
5. **Soyez fier de votre progression** - Même les experts commencent par du "Hello World"
6. **Partagez tôt** - Montrer à un ami de confiance donne un feedback inestimable
7. **Automatisez l'ennuyeux** - Scripts de build, déploiement en une commande
8. **Écoutez votre futur vous** - Ce qui vous frustrera dans 2 mois, fixez-le maintenant

---

## 🎉 LANCEMENT

Vous êtes maintenant équipé pour construire quelque chose de vraiment personnel et précieux.

**Rappel**: L'IA qui vous assiste **DOIT** vous poser les questions de la section "QUESTIONS OBLIGATOIRES" avant d'écrire la moindre ligne de code. Si elle ne le fait pas, arrêtez-la et rappelez-lui cette consigne.

Bonne construction, et que votre hub IA devienne votre compagnon numérique le plus fiable! ✨

---
*Ce prompt est conçu pour être adapté. Si certaines sections ne s'appliquent pas à votre contexte, dites-le clairement à l'IA qui vous assiste.*