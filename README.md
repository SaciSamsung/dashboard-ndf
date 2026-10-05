# 📊 Dashboard NDF - Réparations

Dashboard interactif pour analyser les interventions de réparation.

## 🚀 Déploiement Express (2 minutes)

### Avec Netlify (Recommandé)

1. **Créer un compte GitHub** → https://github.com/signup
2. **Créer un nouveau repository** → https://github.com/new
   - Nom: `dashboard-ndf`
   - Public ✓
   - Create repository
3. **Télécharger les fichiers** sur GitHub
   - Cliquez "Add file" → "Upload files"
   - Sélectionnez:
     - `dashboard.html`
     - `full_data_repair.json`
   - Commit changes
4. **Allez sur** → https://netlify.com
5. **Sign up** avec GitHub
6. **New site from Git** → Sélectionnez `dashboard-ndf`
7. **Deploy** → ✅ C'est prêt!
8. **Votre URL** : `https://votrenomdutilisateur.netlify.app`

## ✨ Fonctionnalités

- 📈 4 graphiques interactifs
- 🔍 Filtres multiples (clients, modèles, mois)
- 📋 Tableau détaillé des interventions
- 📁 Chargement de fichier Excel
- 📊 Statistiques en temps réel

## 📥 Charger des données mises à jour

1. Préparez un fichier Excel avec:
   - Onglet "Void9" (données)
   - Onglet "Name _NPC" (mapping noms)
2. Cliquez "📤 Charger" sur le dashboard
3. Sélectionnez votre fichier
4. Les données se mettent à jour automatiquement ✨

## 🛠️ Pour développeurs

### En local
```bash
# Clonez le repo
git clone https://github.com/votre-username/dashboard-ndf.git
cd dashboard-ndf

# Ouvrez simplement le fichier HTML
open dashboard.html
# ou
start dashboard.html
```

### Structure
```
dashboard-ndf/
├── dashboard.html          # Application principale
├── full_data_repair.json   # Données
└── README.md              # Ce fichier
```

## 📝 Format des données requises

### Onglet "Void9"
- CUSTOMERTYPE : Client (BOULANGER, FNAC, etc.)
- MODEL : Modèle SKU
- DELIVERYDATE : Date de livraison
- REPAIRTYPE : Type de réparation

### Onglet "Name _NPC"
- SKU : Modèle
- Marketing Name : Nom marketing du modèle

## 🔧 Graphiques

- **Distribution par Client** : Répartition des interventions par client
- **Top 15 Client-Modèle** : Meilleures combinaisons
- **Types de Réparation** : Distribution des réparations
- **Interventions par Mois** : Tendance temporelle

## 📱 Responsive

✅ Fonctionne sur desktop, tablette, mobile

## 💡 Support

Besoin d'aide? Consultez le GUIDE_DEPLOIEMENT.md
