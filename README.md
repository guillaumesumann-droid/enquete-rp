# Questionnaire de recherche — Radioprotection

**Mémoire d'ingénieur CNAM · Spécialité Radioprotection**  
**Auteur : Guillaume Sumann**

Sujet : *Le classement des travailleurs exposés aux rayonnements ionisants — accès occasionnel aux zones réglementées.*

---

## Structure du projet

```
enquete-rp/
├── index.html      ← Page unique du questionnaire (HTML + CSS + JS inline)
├── .nojekyll       ← Désactive le traitement Jekyll sur GitHub Pages
└── README.md       ← Ce fichier
```

---

## 1 · Configurer Formspree (collecte des réponses)

Formspree est le service qui réceptionne et stocke les réponses soumises par les participants.

### Étapes

1. Créer un compte gratuit sur [https://formspree.io](https://formspree.io)
2. Créer un **nouveau formulaire** (bouton "+ New Form")
3. Nommer le formulaire (ex. : `Questionnaire Radioprotection CNAM`)
4. Copier l'**endpoint** fourni, de la forme :  
   `https://formspree.io/f/xxxxxxxx`
5. Ouvrir `index.html` et remplacer la valeur de l'attribut `action` du formulaire :

```html
<!-- Ligne à modifier (~ligne 197) -->
<form id="questionnaire-form" action="https://formspree.io/f/VOTRE_ENDPOINT" ...>
```

Remplacer `VOTRE_ENDPOINT` par le code obtenu à l'étape 4.

### Paramètres Formspree recommandés

Dans le tableau de bord Formspree, activez :
- **Email notifications** — pour être notifié à chaque soumission
- **Spam filter** — déjà géré côté formulaire avec un champ honeypot

---

## 2 · Déployer sur GitHub Pages

### Prérequis

- Un compte [GitHub](https://github.com)
- Git installé localement
- Un dépôt GitHub vide créé au préalable (ex. : `enquete-rp`)

### Commandes

```bash
# 1 — Initialiser le dépôt local
git init

# 2 — Ajouter les fichiers
git add index.html README.md .nojekyll

# 3 — Premier commit
git commit -m "Initial commit — questionnaire radioprotection"

# 4 — Relier au dépôt GitHub distant
#     Remplacer VOTRE_PSEUDO par votre nom d'utilisateur GitHub
#     et enquete-rp par le nom de votre dépôt
git remote add origin https://github.com/VOTRE_PSEUDO/enquete-rp.git

# 5 — Pousser sur GitHub
git branch -M main
git push -u origin main
```

### Activer GitHub Pages

1. Aller sur votre dépôt GitHub
2. Cliquer sur **Settings** (onglet engrenage)
3. Dans le menu gauche : **Pages**
4. Sous *Source* : sélectionner **Deploy from a branch**
5. Branch : **main** · Dossier : **/ (root)**
6. Cliquer **Save**

GitHub Pages affiche l'URL publique sous la forme :  
`https://VOTRE_PSEUDO.github.io/enquete-rp/`

> Le déploiement prend 1 à 3 minutes. Rafraîchir la page Settings > Pages pour voir l'URL.

---

## 3 · Générer et partager le QR Code

Une fois la page déployée et l'URL connue :

1. Ouvrir la page du questionnaire dans un navigateur
2. Faire défiler jusqu'en bas de page
3. Cliquer sur **Générer un QR Code**
4. Le QR code apparaît — faire une capture d'écran ou imprimer la page

Vous pouvez distribuer ce QR code par email, affiche, ou document PDF.

---

## 4 · Notes techniques

| Élément | Détail |
|---|---|
| Référencement | `<meta name="robots" content="noindex, nofollow">` — page non indexée |
| Anonymat | Aucune collecte automatique d'IP ou d'email |
| Champ honeypot | `_gotcha` — filtre les soumissions automatiques |
| Bibliothèque QR | [qrcode.js](https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js) via CDN |
| Polices | [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts |
| Branchement Q5 | Non / Je ne sais pas → blocs 2–6 masqués, renvoi section finale |
| Branchement Q15 | Oui avec durée définie → affiche Q15b |
| Branchement Q20 | Oui avec constat → affiche Q20b |
| Branchement Q23 | Oui (fréquemment ou occasionnellement) → affiche Q23b |

---

## 5 · Mettre à jour le questionnaire

Pour modifier une question ou ajouter une option, éditer directement `index.html`.  
Puis pousser les modifications :

```bash
git add index.html
git commit -m "Mise à jour questionnaire — [description]"
git push
```

GitHub Pages se met à jour automatiquement en 1 à 2 minutes.

---

*Questions : guillaume.sumann@gmail.com*
