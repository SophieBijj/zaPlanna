# 🔧 Configuration Google Drive pour zaPlanna

Pour activer la synchronisation Google Drive, vous devez obtenir des clés API de Google Cloud Console.

## 📋 Étapes de configuration

### 1. Créer un projet Google Cloud
1. Aller sur [Google Cloud Console](https://console.cloud.google.com/)
2. Cliquer sur **"Créer un projet"**
3. Nommer le projet : `zaPlanna Instagram Planner`
4. Cliquer sur **"Créer"**

### 2. Activer l'API Google Drive
1. Dans le menu de gauche, aller à **"APIs & Services"** → **"Library"**
2. Chercher **"Google Drive API"**
3. Cliquer dessus et cliquer sur **"Enable"** (Activer)

### 3. Créer les identifiants OAuth 2.0

#### A. Configurer l'écran de consentement
1. Aller à **"APIs & Services"** → **"OAuth consent screen"**
2. Choisir **"External"** (Externe) → Cliquer sur **"Create"**
3. Remplir les informations :
   - **App name** : `zaPlanna Instagram Planner`
   - **User support email** : Votre email
   - **Developer contact** : Votre email
4. Cliquer sur **"Save and Continue"**
5. Dans **"Scopes"**, cliquer sur **"Add or Remove Scopes"**
   - Chercher et cocher : `https://www.googleapis.com/auth/drive.file`
   - Cliquer sur **"Update"** puis **"Save and Continue"**
6. Dans **"Test users"**, ajouter votre adresse Gmail
7. Cliquer sur **"Save and Continue"**

#### B. Créer le Client ID OAuth
1. Aller à **"APIs & Services"** → **"Credentials"**
2. Cliquer sur **"+ Create Credentials"** → **"OAuth client ID"**
3. Type d'application : **"Web application"**
4. Nom : `zaPlanna Web Client`
5. **Authorized JavaScript origins** (origines autorisées) :
   ```
   https://votre-site.netlify.app
   http://localhost:8080
   ```
   *(Remplacez par l'URL réelle de votre site Netlify)*
6. **Authorized redirect URIs** : Laisser vide pour l'instant
7. Cliquer sur **"Create"**
8. **IMPORTANT** : Copier le **Client ID** qui s'affiche (format : `xxxxx.apps.googleusercontent.com`)

### 4. Créer une clé API
1. Dans **"Credentials"**, cliquer sur **"+ Create Credentials"** → **"API key"**
2. **IMPORTANT** : Copier la **API Key** générée
3. Cliquer sur **"Restrict Key"** pour sécuriser :
   - Dans **"API restrictions"**, choisir **"Restrict key"**
   - Cocher **"Google Drive API"**
   - Cliquer sur **"Save"**

### 5. Configurer votre fichier HTML

Ouvrir `index.html` (ou `index-zaplanna.html`) et trouver cette section (ligne ~942) :

```javascript
const GOOGLE_CONFIG = {
    CLIENT_ID: 'VOTRE_CLIENT_ID_ICI.apps.googleusercontent.com',
    API_KEY: 'VOTRE_API_KEY_ICI',
    DISCOVERY_DOCS: ['https://www.googleapis.com/discovery/v1/apis/drive/v3/rest'],
    SCOPES: 'https://www.googleapis.com/auth/drive.file',
    FILE_NAME: 'zaplanna-instagram-planner.json'
};
```

**Remplacer** :
- `VOTRE_CLIENT_ID_ICI.apps.googleusercontent.com` → Par votre **Client ID** (étape 3B)
- `VOTRE_API_KEY_ICI` → Par votre **API Key** (étape 4)

### 6. Déployer et tester

1. Sauvegarder le fichier
2. Commiter et pusher vers GitHub
3. Netlify va automatiquement déployer
4. Ouvrir votre site : `https://votre-site.netlify.app`
5. Cliquer sur **"Connecter Google Drive"**
6. Autoriser l'accès à Google Drive

---

## ✅ C'est fait !

Maintenant, tous vos posts Instagram seront automatiquement sauvegardés dans un fichier `zaplanna-instagram-planner.json` dans votre Google Drive.

Vous pourrez accéder à votre planner depuis :
- 📱 Votre téléphone mobile
- 💻 Votre ordinateur
- 📟 Votre tablette

Tout sera synchronisé automatiquement !

---

## 🔒 Sécurité

- Le fichier est **privé** et stocké dans **VOTRE** Google Drive
- Personne d'autre ne peut y accéder
- Vous pouvez révoquer l'accès à tout moment depuis [Google Account Permissions](https://myaccount.google.com/permissions)

---

## ⚠️ Dépannage

**Erreur "Invalid Client ID"** :
- Vérifier que vous avez bien copié le Client ID complet
- Vérifier que l'URL de votre site est dans "Authorized JavaScript origins"

**Erreur "Access Blocked"** :
- Vérifier que votre email est bien dans les "Test users" de l'écran de consentement

**Le fichier ne se synchronise pas** :
- Ouvrir la console du navigateur (F12) et vérifier les erreurs
- Vérifier que l'API Google Drive est bien activée
