# La chasse au trésor de Julie

Page unique (HTML + CSS + JS, aucune dépendance externe hors polices Google Fonts) — un escape game d'anniversaire à 5 étapes, chacune validée par un code trouvé physiquement dans la maison.

## Déploiement

Cette page vit dans `julie/` pour ne pas entrer en conflit avec le questionnaire radioprotection publié à la racine du dépôt. Une fois cette branche fusionnée sur `main`, elle sera accessible via GitHub Pages à :

```
https://<compte>.github.io/enquete-rp/julie/
```

C'est cette URL qu'il faut envoyer par SMS.

## Photo manquante

`photo-frigo.jpeg` (affichée après validation du code de l'étape 2) doit être déposée dans ce dossier (`julie/photo-frigo.jpeg`) avant le jour J — elle n'est pas encore présente dans le dépôt.

## Principe de sécurité

- Aucun code n'est stocké en clair dans le JS : seule une empreinte (djb2) du code sert à la validation.
- Aucun message de transition (ni le message final) n'est stocké en clair : chacun est chiffré (XOR + base64) avec le code de son étape comme clé, et n'est déchiffré qu'après validation du hash, en utilisant le code que la joueuse vient de saisir.
- Les textes visibles *avant* la saisie d'un code (titres, consignes) restent volontairement neutres et ne contiennent aucune localisation ni indice, y compris si on clique en avance sur « Étape suivante » sans être passé par la cachette physique.
- Comparaison des codes insensible à la casse et aux espaces (trim + majuscules).

## Réinitialiser une partie de test

Un lien discret « réinitialiser la progression » en bas de page efface la progression stockée dans le `localStorage` du navigateur — pratique pour tester le parcours plusieurs fois avant le jour J.
