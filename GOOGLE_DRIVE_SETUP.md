# 🚀 Configuration Google Drive pour zaPlanna

Ce guide t'explique comment configurer la synchronisation Google Drive pour ton application de planification Instagram.

## 📋 Prérequis

- Un compte Google
- L'application déployée sur Netlify (ou accessible via un navigateur)
- Les API Keys sont déjà configurées dans l'application ✅

## 🎯 Étapes de configuration

### 1️⃣ Créer un fichier JSON sur Google Drive

1. Ouvre [Google Drive](https://drive.google.com)
2. Crée un nouveau fichier :
   - **Option A** : Clique droit → Google Docs → Document → puis File → Save as → Changer en `.json`
   - **Option B** : Crée un fichier texte sur ton ordinateur, puis télécharge-le sur Drive
3. Nomme-le comme tu veux (ex: `ma-planification-insta.json` ou `client-a.json`)
4. Place-le dans le dossier de ton choix sur Drive

**Contenu initial du fichier** (à copier-coller dans ton fichier) :
```json
{
  "posts": [],
  "themes": [],
  "nextPostId": 1,
  "nextThemeId": 1
}
```

> 💡 **Astuce** : Tu peux aussi laisser le fichier vide, l'application l'initialisera automatiquement lors de la première synchronisation.

### 2️⃣ Obtenir l'ID du fichier

Il y a **2 méthodes** pour obtenir l'ID :

#### Méthode A : Depuis l'URL (recommandée) ⭐
1. Ouvre ton fichier dans Google Drive (double-clic dessus)
2. Regarde l'URL dans la barre d'adresse de ton navigateur
3. L'URL ressemble à :
   ```
   https://drive.google.com/file/d/1a2b3c4d5e6f7g8h9i0j_ABC123/view
   ```
4. **L'ID est la partie entre `/d/` et `/view`** :
   ```
   1a2b3c4d5e6f7g8h9i0j_ABC123
   ```

#### Méthode B : Via le partage
1. Fais un clic droit sur ton fichier dans Google Drive
2. Sélectionne **"Partager"** ou **"Obtenir le lien"**
3. Clique sur **"Copier le lien"**
4. Le lien ressemble à : `https://drive.google.com/file/d/[ID_ICI]/view?usp=sharing`
5. L'ID est la partie entre `/d/` et `/view`

### 3️⃣ Connecter l'application à ton fichier

1. Ouvre ton application zaPlanna dans ton navigateur
2. En haut à droite, clique sur **"Connecter Drive"**
3. Une fenêtre Google s'ouvre : **Autorise l'accès à Google Drive**
4. Un champ input apparaît : **"ID ou URL du fichier Drive..."**
5. Colle **l'ID du fichier** (ou l'URL complète - l'app extrait l'ID automatiquement)
6. Clique sur **"Connecter au fichier"**

✨ **C'est fait !** L'application va automatiquement synchroniser tes données avec ton fichier Drive.

## 🔄 Fonctionnement de la synchronisation

### 🤖 Auto-sauvegarde intelligente
- Chaque modification (nouveau post, modification, suppression) est **automatiquement sauvegardée** sur Drive
- La sauvegarde se déclenche **2 secondes après** ton dernier changement
- Pas besoin de cliquer sur "Synchroniser" à chaque fois !

### 🔄 Synchronisation manuelle
Tu peux aussi forcer une synchronisation en cliquant sur **"Synchroniser"** :
- Si Drive contient des données → Tu choisis :
  - 📥 **Charger depuis Drive** : Remplace tes données locales par celles de Drive
  - 📤 **Envoyer vers Drive** : Envoie tes données locales vers Drive
- Si Drive est vide → Tes données locales sont automatiquement envoyées

### 📊 Indicateurs de statut

Le widget en haut à droite t'indique l'état de la connexion :

| Indicateur | Signification |
|------------|---------------|
| 🔴 **Gris** | Non connecté à Google Drive |
| 🟢 **Vert** | Connecté au fichier - Prêt à synchroniser |
| 🟠 **Orange animé** | Synchronisation en cours... |

Messages possibles :
- **"Non connecté"** → Clique sur "Connecter Drive"
- **"Authentifié - Entre l'ID du fichier"** → Colle l'ID de ton fichier
- **"Connecté: nom-fichier.json"** → Tout est prêt !
- **"Données envoyées ✓"** → Sauvegarde réussie
- **"Chargé depuis Drive ✓"** → Données récupérées avec succès

## 🤝 Partage et collaboration

### Partager avec ton équipe

Tu veux que ton assistant, ton community manager ou ton équipe accède au même planning ?

1. Sur Google Drive, fais un **clic droit** sur ton fichier JSON
2. Clique sur **"Partager"**
3. Ajoute les **emails** de tes collaborateurs
4. Donne-leur l'accès **"Éditeur"** (pour qu'ils puissent modifier)
5. Partage-leur **l'ID du fichier**
6. Ils n'ont qu'à :
   - Ouvrir l'application zaPlanna
   - Cliquer sur "Connecter Drive"
   - Autoriser l'accès
   - Coller le **même ID de fichier** que toi
   - Cliquer sur "Connecter au fichier"

🎉 **Vous travaillez maintenant tous sur le même fichier !** Chaque modification est visible par tout le monde en temps réel.

### 📁 Multi-projets

Tu gères plusieurs comptes Instagram ou plusieurs clients ?

Crée **un fichier différent** pour chaque projet :
- 📸 `perso-instagram.json` → Ton compte personnel
- 💼 `client-a.json` → Client A
- 🏢 `client-b.json` → Client B
- 🎨 `projet-special.json` → Projet spécial

**Pour switcher entre projets** :
1. Clique sur **"Déconnecter"** en bas du widget
2. Clique sur **"Connecter Drive"**
3. Colle l'ID du **nouveau fichier**
4. Voilà ! Tu es sur un autre projet

> 💡 **Astuce** : Garde une note avec tous tes IDs de fichiers pour switcher rapidement !

## 🔒 Sécurité et permissions

### 🛡️ Permissions requises

L'application demande uniquement l'accès **`drive.file`** qui permet de :
- ✅ Lire et écrire **uniquement** les fichiers que TU as créés ou auxquels tu as donné l'accès
- ✅ Modifier les fichiers que tu as partagés avec l'app
- ❌ **NE PEUT PAS** accéder aux autres fichiers de ton Drive
- ❌ **NE PEUT PAS** voir tes documents, photos, etc.
- ❌ **NE PEUT PAS** supprimer de fichiers (sauf ceux créés par l'app)

C'est l'accès **le plus limité** possible pour Google Drive - super sécurisé ! 🔐

### 🎛️ Gérer les permissions

Tu contrôles **tout** :
- **Qui peut accéder** : Gère les partages via Google Drive
- **Révocation** : Tu peux révoquer l'accès à tout moment sur [Google Account Permissions](https://myaccount.google.com/permissions)
- **Token local** : L'application stocke ton token d'accès **uniquement localement** (dans ton navigateur)

## ❓ Résolution de problèmes

### 🚫 "Impossible d'accéder au fichier"

**Causes possibles** :
- ❌ L'ID du fichier est incorrect ou mal copié
- ❌ Le fichier n'existe plus sur Drive
- ❌ Le fichier a été supprimé ou déplacé dans la corbeille
- ❌ Tu n'as pas les permissions sur ce fichier

**Solutions** :
1. Vérifie que l'ID est correct (copie-le à nouveau depuis Drive)
2. Vérifie que le fichier existe toujours dans ton Drive
3. Si c'est un fichier partagé, vérifie que tu as l'accès "Éditeur"

### ⚠️ "Erreur de synchronisation"

**Causes possibles** :
- ❌ Pas de connexion Internet
- ❌ Token expiré
- ❌ Permissions révoquées

**Solutions** :
1. Vérifie ta connexion Internet
2. Déconnecte-toi et reconnecte-toi à Google Drive
3. Vérifie que le fichier n'a pas été supprimé

### 🔄 "Les données ne se synchronisent pas automatiquement"

**Causes possibles** :
- Le fichier Drive n'est pas configuré
- Le token a expiré

**Solutions** :
1. Vérifie que le widget affiche "Connecté au fichier"
2. Clique manuellement sur "Synchroniser" pour forcer
3. Si ça ne marche pas, déconnecte et reconnecte

### 🔁 Réinitialiser complètement la connexion

Si rien ne fonctionne :
1. Clique sur **"Déconnecter"** dans le widget
2. Recharge la page (F5)
3. Clique sur **"Connecter Drive"**
4. Autorise à nouveau l'accès
5. Entre l'ID du fichier
6. Clique sur **"Connecter au fichier"**

## 💡 Astuces et bonnes pratiques

### 📁 Organisation recommandée

Crée un dossier dédié dans ton Drive :
```
📁 Mon Drive
  └─ 📁 zaPlanna
      ├─ 📄 perso-instagram.json
      ├─ 📄 client-a.json
      ├─ 📄 client-b.json
      └─ 📄 backup-2024.json
```

### 🔄 Utilise le même fichier sur plusieurs appareils

Tu peux accéder à ton planning depuis :
- 💻 Ton ordinateur au bureau
- 🏠 Ton ordinateur à la maison
- 📱 Ton téléphone
- 📟 Ta tablette

Il suffit de te connecter avec le **même ID de fichier** partout !

### 💾 Backup manuel (sécurité)

Même si tout est sur Drive, tu peux faire des backups :
1. Dans l'app, clique sur **"Exporter"** (dans la vue Calendrier)
2. Sauvegarde le fichier JSON sur ton ordinateur
3. Tu peux l'importer plus tard si besoin

### 🎯 Nommer tes fichiers intelligemment

Exemples de noms clairs :
- ✅ `instagram-mode-2024.json`
- ✅ `client-nike-posts.json`
- ✅ `perso-reels-ideas.json`
- ❌ `fichier.json` (trop vague)
- ❌ `data.json` (tu ne sauras plus ce que c'est)

---

## 🎓 En résumé

1. **Crée** un fichier JSON sur Drive
2. **Copie** l'ID du fichier (depuis l'URL)
3. **Connecte** l'app à Google Drive
4. **Colle** l'ID dans l'app
5. **C'est tout** ! La sync automatique est activée ✨

---

## 🆘 Besoin d'aide ?

**Checklist de dépannage** :
- [ ] Je suis connecté à Internet
- [ ] J'ai autorisé l'accès à Google Drive
- [ ] L'ID du fichier est correct (re-vérifié)
- [ ] Le fichier existe sur mon Drive
- [ ] Le fichier n'est pas dans la corbeille
- [ ] J'ai les permissions "Éditeur" sur le fichier (si partagé)

**Pour aller plus loin** :
- 📚 [Documentation Google Drive API](https://developers.google.com/drive/api/guides/about-sdk)
- 🔐 [Gérer les permissions Google](https://myaccount.google.com/permissions)

---

Bon planning ! 🎨📸✨
