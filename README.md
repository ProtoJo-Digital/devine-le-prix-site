# Devine le Prix – Jeu Famille — site

Site vitrine de l'application iOS « Devine le Prix – Jeu Famille », éditée par
ProtoJo Digital (Johan Quille), France.

**En ligne :** <https://devine-le-prix.protojo.fr/>

## Contenu du dépôt

| Fichier | Rôle |
| --- | --- |
| `index.html` | Page d'accueil : la partie d'essai, « Comment on joue », l'appel au téléchargement |
| `familles.html` | Pour les familles et les seniors : les cinq façons de jouer, ce qu'on gagne |
| `accessibilite.html` | Ce que le jeu suit des réglages d'accessibilité de l'iPhone |
| `questions.html` | Les onze questions fréquentes |
| `aide.html` | Aide et contact |
| `presse.html` | Espace presse : présentation, fiche, bannière à télécharger |
| `confidentialite.html` | Politique de confidentialité |
| `partage.jpg` | Aperçu du lien au partage (1200 × 630), et bannière de l'espace presse. Recadrée depuis `livrables/banniere-1920x1080.png` du projet Claude Design |
| `.nojekyll` | Fichier vide qui demande à GitHub Pages de publier les fichiers tels quels, sans passer par Jekyll |
| `CNAME` | Le domaine du site. Écrit par GitHub quand on renseigne le domaine personnalisé ; ne pas le modifier à la main |

## Comment ça marche

Site statique, sans étape de construction et sans outillage :

- **Aucune dépendance** : pas de CDN, pas de police externe, pas de script, pas
  de bibliothèque, pas de traceur ni de statistiques. Les pages sont
  autonomes.
- **Le CSS est intégré** dans une balise `<style>` au début de chaque page, et
  les sept feuilles sont volontairement **identiques**, à l'octet près : toute
  modification de style doit donc être reportée dans les sept fichiers. L'en-tête
  et le pied de page le sont aussi, à la marque de page courante près.
- **Publication** : GitHub Pages sert la branche `main`. Une fusion dans `main`
  met le site en ligne à jour en une minute environ. Rien n'est publié depuis
  une branche de travail ou une pull request.
- **Le dépôt doit rester public.** Pages depuis un dépôt privé exige un plan
  payant ; le passer en privé dépublie le site et efface la configuration de
  Pages, qui est alors à refaire à la main. Et cela ne protégerait rien : même
  depuis un dépôt privé, Pages sert tous les fichiers publiquement.
- **L'adresse publique passe par `devine-le-prix.protojo.fr`**, un domaine qui
  nous appartient, et non par l'adresse `github.io`. C'est ce qui permet de
  changer d'hébergeur sans casser le lien déclaré dans App Store Connect.

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

**La maquette du site vit dans le projet Claude Design « Devine le Prix – Jeu
Famille ! », fichier `Site web.dc.html`.** Elle fait référence pour la mise en
page, au même titre que la planche pour les couleurs. Le fichier
`design-tokens/devine-le-prix.tokens.json` du même projet, tiré de `Theme.swift`,
donne les valeurs exactes ; les jetons CSS du site les reprennent. Cette
maquette décrit huit pages ; le site en publie sept, les mentions légales
restant à écrire (voir « À faire »).

### Couleurs

| Variable | Valeur | Usage |
| --- | --- | --- |
| `--fond` | `#1B1240` | Fond de page, et encre dès qu'un fond clair est utilisé |
| `--fond-haut` | `#2C1E6B` | Haut du dégradé signature du bandeau |
| `--carte` | `#FFFFFF` | Cartes |
| `--nuit` | `#120B2E` | `ink-950` — ombres les plus profondes |
| `--clair` | `#F4F2FA` | Fond des sections de contenu |
| `--puits` | `#EEEBFA` | `well` — fond des pictogrammes, du sommaire et du signe « + » |
| `--encre-douce` | `#4E4773` | `ink-700` — texte secondaire (7,65:1 sur `--clair`) |
| `--encre-tendre` | `#676088` | `ink-600` — texte d'invite du champ de saisie (5,82:1 sur blanc) |
| `--texte` | `#FFFFFF` | Texte sur tous les fonds profonds |
| `--or` | `#FAB31A` | Titres de section, accroche, bouton principal |
| `--or-clair` | `#FFD36B` | `gold-300` — réserve de la planche |
| `--corail` | `#D63D2F` | « C'est plus ! », deuxième temps du jeu |
| `--vert` | `#1E7F46` | « Valider », public « Enfants » |
| `--bleu` | `#2A6FD0` | « C'est moins ! », public « Seniors » |
| `--violet` | `#994DCC` | Fourchette de prix, public « En famille » |
| `--accent` | `#6657D9` | `violet-500` — bordure du champ, premier temps du jeu |
| `--accent-fonce` | `#4F41C4` | `violet-700` — liens posés sur fond clair (7,28:1) |
| `--lavande` | `#B9AEFF` | `violet-200` — réserve de la planche |
| `--voile` | `rgba(255,255,255,.14)` | Pastilles posées sur le fond profond |

Deux règles de couleur, non négociables :

- **Texte blanc sur tous les fonds profonds. Encre `#1B1240` dès que l'or ou le
  blanc sert de fond.**
- **L'or ne se pose jamais sur blanc** : le contraste n'y est que de 1,82:1, très
  en dessous du minimum de 4,5:1. Sur fond clair, les liens passent à
  `--accent-fonce` (7,28:1) et les titres à l'encre (17,4:1).

### Typographie

Pile système, sans police à télécharger : `ui-rounded`, `-apple-system`,
`"SF Pro Rounded"`, `"SF Pro Display"`, puis les replis habituels. Sur les
appareils Apple, cela donne le SF Pro Rounded de la planche.

Graisses de la charte : **titres 900, boutons et pastilles 800, textes de carte
700**. La planche interdit tout corps sous 17 pt ; l'échelle du site commence donc
à 17 px.

| Échelle | Tokens |
| --- | --- |
| Espacement (multiples de 4 px) | `--e1` 4 · `--e2` 8 · `--e3` 12 · `--e4` 16 · `--e5` 20 · `--e6` 24 · `--e7` 28 · `--e8` 32 · `--e9` 40 · `--e10` 48 · `--e11` 56 · `--e12` 64 · `--e13` 80 |
| Typographie (base 18 px) | `--t0` 17 · `--t1` 18 · `--t2` 19 · `--t3` 21 · `--t4` 24 · `--t5` 26 · `--t6` 28 · `--t7` 34, plus `--t-titre`, `--t-section`, `--t-duo`, `--t-prix` et `--t-objet`, fluides entre les deux bornes de la maquette (téléphone 390 px, ordinateur 1280 px) |
| Rayons | `--rayon-focus` 6 · `--rayon-petit` 16 · `--rayon-champ` 18 · `--rayon-bouton` 22 · `--rayon` 24 · `--rayon-carte` 28 · `--rayon-grand` 32 · `--rayon-rond` (pastilles) |
| Tailles | `--touche` 44 (minimum tactile) · `--champ` 64 (champ et bouton du jeu) · `--gros-bouton` 66 |

Toutes les marges, tailles et rayons passent par un token. **Aucune valeur en
dur dans le CSS** : si un palier manque, on l'ajoute à l'échelle. Deux
exception assumée et commentée : la base `112.5%` sur `html`. Les dimensions
des dégradés décoratifs de la scène viennent telles quelles de la maquette.

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

Formulations officielles : le titre de l'accueil est celui de la maquette,
« Combien coûte cet objet, d'après toi ? » ; l'accroche de la planche,
« Trouve le prix des objets ! », reste celle de la fiche App Store. La formule
du jeu est « Pile le bon prix ! », et les prix s'écrivent au format français,
« 1 249 € ».

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
et une pull request. `CLAUDE.md`, à la racine, rassemble les consignes de
travail : référentiels, vérifications obligatoires avant une pull request,
conventions git.

## À faire

Liste tenue à jour par la relecture quotidienne, de la plus utile à la moins
utile pour les visiteurs. Les entrées faites en sortent, les nouvelles y
entrent.

### Ce qui attend une décision ou une information de Johan

- **Adresse de la fiche App Store.** L'application n'est pas encore envoyée en
  validation ; dès qu'elle est en ligne, le bouton est écrit **trois** fois dans
  `index.html`, aux trois endroits de la maquette : l'en-tête
  (`id="lien-app-store-haut"`), la carte du jeu juste après la révélation
  (`id="lien-app-store-jeu"`), et le bandeau de fin (`id="lien-app-store"`).
  Pour les allumer : remplacer l'adresse dans celui de l'en-tête et retirer son
  `hidden` ; celui de la carte s'allume alors tout seul, et il reste à retirer le
  `hidden` du bandeau de fin. Penser aussi à la date de sortie dans
  `presse.html`, qui dit aujourd'hui « pas encore publiée ».
- **Mentions légales** : la page manque, et elle est obligatoire pour un site
  édité depuis la France (LCEN, article 1-1 depuis la loi SREN de mai 2024).
  Il faut : la forme juridique et, s'il y a lieu, le capital ; l'adresse du
  siège ; le SIREN ou SIRET, et le RCS s'il y a lieu ; un moyen de contact
  (l'adresse e-mail du pied de page convient) ; le nom du directeur de la
  publication ; le nom, l'adresse et le téléphone de l'hébergeur. L'hébergeur
  est GitHub : reprendre l'adresse et le téléphone depuis une page officielle
  de GitHub plutôt que de mémoire, les sources publiques divergent sur le code
  postal. « ProtoJo Digital » seul ne suffit pas.
- **« D'où viennent les prix ? »**, la seule question de la maquette encore sans
  réponse. Les dix autres sont écrites dans `questions.html`.
- **Les trois affirmations reprises de la maquette et pas encore vues ailleurs** :
  les mini-jeux « Plus cher ou moins cher ? », « Dans l'ordre » et « Escalade
  des prix » ; « Le défi du jour » ; et « le classement récompense aussi le plus
  proche du jour ». Elles viennent du projet Claude Design, pas du site : à
  confirmer ou à retirer de `familles.html`.
- **Icône d'écran d'accueil iOS (`apple-touch-icon`)** : ajouté à l'écran
  d'accueil d'un iPhone, le site prend une capture de la page en guise d'icône,
  iOS n'acceptant pas le favicon SVG actuel. Le dossier `livrables/` du projet
  Claude Design propose trois icônes (A, B, C) : il faut en choisir une.
- **Le reste du dossier de presse** : l'icône 1024 et les six captures d'écran.
  Elles arrivent avec la publication sur l'App Store, et peuvent encore changer
  d'ici là. `presse.html` le dit et propose d'écrire en attendant.
- **Page 404** : une adresse erronée affiche la page par défaut de GitHub
  Pages, en anglais. Un `404.html` aux couleurs du site réglerait ça.
- **Adresse du site** : la maquette est titrée « Site web · devineleprix.fr »,
  le site est publié sur `devine-le-prix.protojo.fr`, l'adresse du `CNAME` et
  celle à déclarer dans App Store Connect. Rien n'a été changé.
- **Registre** : tout le site tutoie, la politique de confidentialité vouvoie.
  Ce n'est pas choquant pour un texte juridique, mais c'est visible dans le
  pied de page, commun à toutes les pages.

### Ce qui peut être fait sans décision préalable

- **Les onglets disparaissent sur téléphone.** Sous 46 rem, l'en-tête n'affiche
  plus que la marque : à trois lignes, les onglets repoussaient la partie
  d'essai hors du premier écran. Les six liens sont au pied de page, au
  complet, mais il faut descendre toute la page pour les atteindre. La maquette
  règle cela par un menu « ☰ » ; reste à juger si un menu qui s'ouvre est une
  bonne idée pour des enfants et des personnes âgées.
- **Sur un écran de 667 px de haut (iPhone SE), le bouton « Valider » finit
  24 px sous le bord.** Le champ de saisie, lui, est visible. Gagner ces 24 px
  demanderait de réduire le titre, ce que la maquette veut grand.
- **Les emojis du catalogue sont parfois énigmatiques hors contexte** :
  🍱 pour un four à micro-ondes, 👔 pour un fer à repasser, 🧺 pour un
  lave-linge. Ils viennent du catalogue de l'application et le nom de l'objet
  est toujours écrit juste en dessous, donc rien n'est ambigu à la lecture ;
  mais le choix des 28 objets montrés sur le site pourrait privilégier ceux
  dont l'emoji se reconnaît seul.
- **La feuille de style est recopiée dans les sept pages.** C'est la règle
  « pages autonomes », et elle tient tant qu'un script vérifie l'égalité à
  chaque relecture. Si le site grandit encore, un `style.css` unique servi
  depuis le même domaine — ce n'est pas une dépendance externe — deviendra plus
  sûr qu'une copie à maintenir sept fois.


## Relecture automatique

Une tâche Claude Code relit le site une fois par jour (interface, accessibilité,
affichage mobile, liens, typographie) et ouvre une pull request depuis une
branche `claude/site-AAAA-MM-JJ` lorsqu'une amélioration en vaut la peine.
Chaque relecture se termine par une liste d'améliorations possibles, reportée
dans la section « À faire » ci-dessus — y compris les jours où rien ne change.
