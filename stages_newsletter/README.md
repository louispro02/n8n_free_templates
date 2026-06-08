# Offres de stages 🛜 — Workflow n8n

Automatise ta recherche de stage en Corporate Finance (ou tout autre domaine) : scraping quotidien des offres publiées depuis moins de 24h, filtrage par IA, base de données Google Sheets, et newsletter dans ta boîte mail chaque matin.

---

## Demo & tuto

▶️ [Voir le tutoriel complet sur YouTube](https://www.youtube.com/watch?v=dMFFVp0DcII&pp=0gcJCQMKAYcqIYzv)

---

## Comment ça marche

```
Schedule Trigger (7h)
    │
    ▼
Google Dork (définition des critères de recherche)
    │
    ├──▶ SerpAPI → LinkedIn
    ├──▶ SerpAPI → Indeed
    ├──▶ SerpAPI → Welcome to the Jungle
    ├──▶ SerpAPI → JobTeaser
    └──▶ SerpAPI → Sainoo
         │
         ▼
    Merge (toutes les offres)
         │
         ▼
    Compare vs Google Sheets (déduplication)
         │
         ▼
    AI Agent — Gemini 2.0 Flash
    "Cette offre correspond à mes critères ? Oui/Non"
         │
         ▼ (Oui seulement)
    Google Sheets — Ajout à la base de données
         │
         ▼
    Déclenchement du sous-workflow email
         │
         ▼
    Agrégation des offres non envoyées
         │
         ▼
    Envoi email (Microsoft Outlook) + Marquage "Envoyé"
```

---

## Prérequis

| Outil | Usage | Lien |
|-------|-------|------|
| **n8n** | Moteur du workflow | [n8n.io](https://n8n.io) |
| **SerpAPI** | Scraping Google (résultats structurés) | [serpapi.com](https://serpapi.com) |
| **Google Sheets** | Base de données des offres | Google Drive |
| **Google Gemini API** | Filtrage IA des offres | Google AI Studio |
| **Microsoft Outlook** | Envoi de la newsletter | Compte Microsoft |

---

## Installation

### 1. Héberger n8n

Trois options :

- **Essai gratuit 2 semaines** — directement sur [n8n.io](https://n8n.io)
- **Auto-hébergement local** (Raspberry Pi, etc.) — voir le tuto YouTube
- **Serveur en ligne** — ex. Hostinger (recommandé pour une utilisation continue)

### 2. Importer le workflow

1. Télécharge le fichier `Offres de stages 🛜.json`
2. Dans n8n : **Settings → Import workflow** → sélectionne le fichier JSON
3. Le workflow s'ouvre dans l'éditeur

### 3. Configurer les credentials

Dans n8n, va dans **Settings → Credentials** et crée :

- **Google Sheets OAuth2** — pour lire/écrire dans ton Google Sheet
- **Google Gemini (PaLM) API** — clé API depuis [Google AI Studio](https://aistudio.google.com)
- **Microsoft Outlook OAuth2** — pour l'envoi des emails

Remplace ensuite chaque credential dans les nœuds concernés par les tiens.

### 4. Configurer SerpAPI

Dans chaque nœud `HTTP Request`, remplace la valeur du paramètre `api_key` par ta propre clé SerpAPI (disponible sur [serpapi.com](https://serpapi.com) après inscription).

### 5. Créer le Google Sheet

Crée une feuille Google Sheets avec les colonnes suivantes :

| Date ajout | title | snippet | link | date | snippet_highlighted_words | source | Com mail |
|------------|-------|---------|------|------|--------------------------|--------|----------|

Dans les nœuds Google Sheets, remplace le `documentId` par l'ID de ta feuille (visible dans l'URL de ton Sheet).

### 6. Adapter le Google Dork

Le nœud **Edit Fields** contient deux dorks :

- `dork` — recherche de postes de **professeur de FLE** (Français Langue Étrangère)
- `dork2` — recherche de stages en **Corporate Finance / M&A / Transaction Services**

Modifie les dorks selon ton domaine cible. Pour t'aider à en rédiger un, tu peux demander à ChatGPT ou Claude de générer un Google Dork adapté à ton profil.

### 7. Activer le workflow

1. Active le **Schedule Trigger** (désactivé par défaut) pour lancer le scraping chaque matin à 7h
2. Active le workflow principal (toggle en haut à droite dans n8n)

---

## Structure du Google Sheet

| Colonne | Description |
|---------|-------------|
| `Date ajout` | Date/heure d'ajout de l'offre |
| `title` | Titre de l'offre |
| `snippet` | Extrait de la description |
| `link` | URL de l'offre |
| `date` | Date de publication selon Google |
| `snippet_highlighted_words` | Mots-clés mis en avant |
| `source` | Site source (LinkedIn, Indeed, etc.) |
| `Com mail` | `Non envoyé` → `Envoyé` après la newsletter |

---

## Personnalisation

- **Ajouter des sites** : duplique un nœud `HTTP Request` + `Split Out` et connecte-le au `Merge`. Change le paramètre `q` avec le nouveau `site:`.
- **Changer l'heure de déclenchement** : modifie le `Schedule Trigger` (nœud désactivé par défaut).
- **Changer le canal de notification** : remplace le nœud `Send a message1` (Outlook) par Gmail, Slack, Telegram, etc.
- **Changer le modèle IA** : remplace le nœud `Google Gemini Chat Model` par n'importe quel LLM supporté par n8n (OpenAI, Mistral, Claude, etc.).

---

## Questions / Support

N'hésite pas à ouvrir une **Issue** sur ce repo ou à me contacter directement.
