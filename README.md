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

Le site suit la **planche de direction artistique de la fiche App Store** de
l'application. Cette planche fait référence : en cas de désaccord entre le site
et elle, c'est le site qui a tort.

Ambiance : « un plateau télé chaleureux : fond profond, projecteurs très
discrets, objets en emoji sur cartes blanches. »

### Couleurs

| Variable | Valeur | Usage |
| --- | --- | --- |
| `--fond` | `#1B1240` | Fond de page, et encre dès qu'un fond clair est utilisé |
| `--fond-haut` | `#2C1E6B` | Haut du dégradé signature du bandeau |
| `--carte` | `#FFFFFF` | Cartes |
| `--encre-douce` | `#5B5680` | Texte secondaire sur carte blanche |
| `--texte` | `#FFFFFF` | Texte sur tous les fonds profonds |
| `--or` | `#FAB31A` | Titres de section, accroche, bouton principal |
| `--corail` | `#D63D2F` | Public « Enfants » |
| `--vert` | `#1E7F46` | Public « Seniors » |
| `--bleu` | `#2A6FD0` | Public « En famille » |
| `--violet` | `#994DCC` | Réserve de la planche, pas encore utilisée sur le site |
| `--accent` | `#6657D9` | Liens posés sur fond clair |
| `--lavande` | `#B9AEFF` | Sous-titre « – Jeu Famille » |
| `--voile` | `rgba(255,255,255,.14)` | Pastilles posées sur le fond profond |
| `--lilas` | `#EFEBFF` | Fond du pictogramme « Tout seul » |
| `--menthe` | `#E4F3EA` | Fond du pictogramme « Sur ce téléphone » |
| `--ciel` | `#E4ECFA` | Fond du pictogramme « Avec d'autres téléphones ». **Hors planche** : ajoutée par analogie avec les deux précédentes |

Deux règles de couleur, non négociables :

- **Texte blanc sur tous les fonds profonds. Encre `#1B1240` dès que l'or ou le
  blanc sert de fond.**
- **L'or ne se pose jamais sur blanc** : le contraste n'y est que de 1,82:1, très
  en dessous du minimum de 4,5:1. Sur carte blanche, les liens passent à
  `--accent` (5,34:1) et les titres à l'encre (17,4:1).

### Typographie

Pile système, sans police à télécharger : `ui-rounded`, `-apple-system`,
`"SF Pro Rounded"`, `"SF Pro Display"`, puis les replis habituels. Sur les
appareils Apple, cela donne le SF Pro Rounded de la planche.

Graisses de la charte : **titres 900, boutons et pastilles 800, textes de carte
700**. La planche interdit tout corps sous 17 pt ; l'échelle du site commence donc
à 17 px.

| Échelle | Tokens |
| --- | --- |
| Espacement (multiples de 4 px) | `--e1` 4 · `--e2` 8 · `--e3` 12 · `--e4` 16 · `--e5` 20 · `--e6` 24 · `--e7` 32 · `--e8` 48 |
| Typographie (base 18 px) | `--t0` 17 · `--t1` 18 · `--t2` 20 · `--t3` 23 · `--t4` 27 · `--t5` 54, plus `--t-titre` et `--t-titre-page` qui sont fluides |
| Rayons | `--rayon-focus` 6 · `--rayon-petit` 16 · `--rayon` 24 (cartes) · `--rayon-grand` 32 (grandes cartes) · `--rayon-rond` (pastilles) |

Toutes les marges, tailles et rayons passent par un token. **Aucune valeur en
dur dans le CSS** : si un palier manque, on l'ajoute à l'échelle. Deux
exceptions assumées et commentées : la base `112.5%` sur `html`, et les
dimensions du halo décoratif.

### Marque

L'icône retenue sur la planche est un **anneau doré avec un « ? » blanc sur fond
profond**. Elle est redessinée en CSS dans l'en-tête (`.sceau`) et en SVG dans la
favicon, sans fichier image.

### Registre

**Le site tutoie.** C'est le registre de l'application et de la planche :
« Trouve le prix des objets ! ». Les textes de l'accueil suivent, y compris le
pied de page, commun aux deux pages.

**Une exception : la politique de confidentialité reste au vouvoiement.** C'est un
document juridique ; en changer le registre reviendrait à le réécrire, ce que la
règle « ne pas modifier le fond » interdit.

### Formulations

Formulations officielles : l'accroche est « Trouve le prix des objets ! », la
formule du jeu est « Pile le bon prix ! », et les prix s'écrivent au format
français, « 1 249 € ».

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
