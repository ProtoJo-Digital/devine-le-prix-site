# Devine le Prix – Jeu Famille — site

Site vitrine de l'application iOS « Devine le Prix – Jeu Famille », éditée par
ProtoJo Digital (Johan Quille), France.

**En ligne :** <https://protojo-digital.github.io/devine-le-prix-site/>

## Contenu du dépôt

| Fichier | Rôle |
| --- | --- |
| `index.html` | Page d'accueil : présentation du jeu, façons de jouer, contact |
| `confidentialite.html` | Politique de confidentialité |
| `.nojekyll` | Fichier vide qui demande à GitHub Pages de publier les fichiers tels quels, sans passer par Jekyll |

## Comment ça marche

Site statique, sans étape de construction et sans outillage :

- **Aucune dépendance** : pas de CDN, pas de police externe, pas de script, pas
  de bibliothèque, pas de traceur ni de statistiques. Les deux pages sont
  autonomes.
- **Le CSS est intégré** dans une balise `<style>` au début de chaque page, et
  les deux feuilles sont volontairement **identiques**. Toute modification de
  style doit donc être reportée dans les deux fichiers.
- **Publication** : GitHub Pages sert la branche `main`. Une fusion dans `main`
  met le site en ligne à jour en une minute environ. Rien n'est publié depuis
  une branche de travail ou une pull request.

## Prévisualiser en local

Ouvrir le fichier HTML directement dans un navigateur suffit. Pour être au plus
près du site publié :

```sh
python3 -m http.server 8000
# puis http://localhost:8000/
```

## Identité visuelle

Ambiance « plateau de jeu télé », fond violet profond. Les couleurs sont
déclarées en variables CSS dans `:root`, en haut de chaque page :

| Variable | Valeur | Usage |
| --- | --- | --- |
| `--fond` | `#1B1240` | Fond de page |
| `--carte` | `#261A55` | Fond des encadrés et des cartes |
| `--texte` | `#F3F0FF` | Texte courant |
| `--texte-doux` | `#CFC6F0` | Texte secondaire (dates, pied de page) |
| `--violet` | `#7668E2` | Bordures — le violet de marque `#6657D9`, éclairci pour atteindre 3:1 |
| `--or` | `#FAB31A` | Titres, liens, boutons |
| `--corail` | `#D63D2F` | Filet de séparation |
| `--rayon` | `18px` | Rayon des coins arrondis |

## Règles à respecter

Le public visé est composé d'enfants et de personnes âgées : la simplicité
prime sur tout le reste.

- **Accessibilité WCAG 2.2 niveau AA** : contraste d'au moins 4,5:1 pour le
  texte et 3:1 pour les grands titres et les bordures. Calculer les contrastes,
  ne jamais les estimer à l'œil.
- **Zones tactiles d'au moins 44 × 44 px** pour tout lien ou bouton isolé
  (recommandation des Human Interface Guidelines d'Apple). Les liens placés à
  l'intérieur d'une phrase font exception.
- **Texte d'au moins 16 px** : la base est fixée à `112.5%`, soit 18 px avec les
  réglages par défaut, tout en suivant la taille de texte choisie dans le
  navigateur.
- **Structure sémantique** : un seul `h1` par page, titres dans l'ordre, repères
  `header` / `nav` / `main` / `footer`, `lang="fr"`, lien d'évitement et focus
  clavier visible.
- **Mobile** : lecture confortable sur un écran de 375 px de large, sans
  défilement horizontal.
- **Impression** : un bloc `@media print` repasse les pages en texte foncé sur
  blanc, car les navigateurs n'impriment pas les fonds. À vérifier après toute
  modification de couleur.
- **Typographie française** : espace insécable (U+00A0) avant `:` `;` `?` `!`,
  guillemets `«` et `»` avec espace insécable à l'intérieur.

### Ne pas modifier sans validation

- Les faits : liens App Store ou TestFlight, adresses de contact, dates, prix,
  noms.
- Le fond juridique de `confidentialite.html`. Seules les fautes de frappe et la
  mise en forme s'y corrigent librement ; le sens doit rester identique.
- L'identité visuelle et la palette ci-dessus. Une teinte peut être ajustée pour
  atteindre un contraste suffisant, la palette ne change pas.
- Ne décrire aucune fonctionnalité dont l'existence dans l'application n'est pas
  certaine.

## Contribuer

`main` n'est pas modifiée directement : chaque changement passe par une branche
et une pull request.

## À faire

- Ajouter le bouton « Télécharger sur l'App Store » sur la page d'accueil, dès
  que l'adresse de la fiche App Store sera connue. L'emplacement prévu est
  signalé par un commentaire dans `index.html`.

## Relecture automatique

Une tâche Claude Code relit le site une fois par jour (interface, accessibilité,
affichage mobile, liens, typographie) et ouvre une pull request depuis une
branche `claude/site-AAAA-MM-JJ` lorsqu'une amélioration en vaut la peine.
