# Guide de Déploiement - Dashboard NDF en Ligne

## Option 1 : GitHub Pages (Gratuit ⭐ Recommandé)

### Étapes :

1. **Créer un compte GitHub** (si vous n'en avez pas)
   - Allez sur https://github.com
   - Inscrivez-vous

2. **Créer un nouveau repository**
   - Cliquez sur "+" → "New repository"
   - Nommez-le `dashboard-ndf`
   - Cochez "Public"
   - Cliquez "Create repository"

3. **Télécharger les fichiers**
   - Cliquez sur "Add file" → "Upload files"
   - Téléchargez :
     - `dashboard.html`
     - `full_data_repair.json`

4. **Activer GitHub Pages**
   - Allez dans "Settings"
   - Scroll down à "GitHub Pages"
   - Dans "Source" sélectionnez "main"
   - Cliquez "Save"

5. **Accéder au dashboard**
   - Votre dashboard est accessible à :
   - `https://votre-username.github.io/dashboard-ndf/dashboard.html`

✅ **Avantages :**
- Gratuit
- Accessible partout
- Pas de limite de bande passante
- Facile à mettre à jour

⚠️ **Limitation :**
- Le chargement de fichiers Excel peut avoir des restrictions CORS

---

## Option 2 : Vercel (Très facile, Gratuit)

### Étapes :

1. **Allez sur** https://vercel.com
2. **Cliquez** "Sign Up"
3. **Créez avec GitHub** (connectez votre compte)
4. **Créez un nouveau projet** → "Add New..." → "Project"
5. **Importez votre repo GitHub** (dashboard-ndf)
6. **Cliquez Deploy**
7. **Accédez via** `https://votre-nom.vercel.app`

✅ **Avantages :**
- Super simple
- Déploiement automatique des mises à jour
- Gratuit
- Domaine personnalisé possible

---

## Option 3 : Netlify (Très simple, Gratuit)

### Étapes :

1. **Allez sur** https://netlify.com
2. **Cliquez** "Sign up"
3. **Choisissez GitHub**
4. **Autorisez Netlify** à accéder à vos repos
5. **Sélectionnez** `dashboard-ndf`
6. **Deploy**
7. **Accédez via** `https://votre-nom.netlify.app`

✅ **Avantages :**
- Interface très user-friendly
- Gratuit
- Support SSL automatique
- Forms intégrés (si besoin)

---

## Option 4 : Serveur Personnel / VPS

Si vous avez un serveur avec Apache ou Nginx :

1. **Copiez les fichiers** sur votre serveur
2. **Placez-les dans** `/var/www/html/dashboard/`
3. **Accédez via** `https://votre-domaine.com/dashboard/dashboard.html`

---

## Mettre à Jour les Données en Ligne

### Problème :
Le chargement de fichier Excel en ligne a des restrictions CORS dans le navigateur.

### Solutions :

#### Solution A : Backend simple (Recommandé pour uploads)
Créer un petit serveur Python/Node pour traiter les uploads :

**Exemple avec Node.js :**
```javascript
const express = require('express');
const fileUpload = require('express-fileupload');
const XLSX = require('xlsx');

const app = express();
app.use(fileUpload());

app.post('/upload', (req, res) => {
    const file = req.files.file;
    const workbook = XLSX.read(file.data);
    const data = XLSX.utils.sheet_to_json(workbook.Sheets['Void9']);
    
    // Traiter et sauvegarder...
    res.json({success: true, count: data.length});
});
```

#### Solution B : Utilisateur télécharge manuellement
- L'utilisateur télécharge le fichier Excel sur son ordinateur
- Il le dépose sur le dashboard
- Le traitement se fait en local (ça marche déjà ! 🎉)

#### Solution C : Google Sheets
- Connecter les données à une Google Sheet
- Lire directement depuis l'API Google Sheets
- Aucun upload nécessaire

---

## Résumé des Coûts

| Option | Coût | Facilité | Upload Fichier |
|--------|------|---------|---|
| GitHub Pages | Gratuit | ⭐⭐⭐ | Limité |
| Vercel | Gratuit | ⭐⭐⭐⭐ | Limité |
| Netlify | Gratuit | ⭐⭐⭐⭐ | Limité |
| Heroku | Gratuit (limité) | ⭐⭐⭐ | ✅ Oui |
| VPS Personnel | 5-20€/mois | ⭐⭐ | ✅ Oui |

---

## Recommandation Finale

✨ **Pour commencer :** 
→ **Vercel ou Netlify** (super simple, gratuit, upload basique marche)

🚀 **Avec backend :**
→ **Heroku** (gratuit mais limité) ou **VPS personnel** (pays, évolutif)

