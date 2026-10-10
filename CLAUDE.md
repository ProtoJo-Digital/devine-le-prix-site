# Consignes pour Claude Code

Ce dépôt est le site vitrine de l'application iOS « Devine le Prix – Jeu Famille »
(ProtoJo Digital — Johan Quille) : un site statique publié sur GitHub Pages à
l'adresse <https://devine-le-prix.protojo.fr/>, sans outil de build.

`README.md` décrit le contenu du dépôt, l'identité visuelle, la palette et les
règles de fond. Ce fichier-ci dit comment travailler dessus.

## Le public d'abord

Les visiteurs sont des enfants et des personnes âgées. La simplicité prime sur
tout le reste : un seul message principal par écran, des boutons évidents, rien
de superflu. Mieux vaut ne rien changer qu'améliorer pour la forme.

## Référentiels

Travailler sur l'état 2026 des références, jamais sur de vieux souvenirs :
WCAG 2.2 niveau AA, Human Interface Guidelines d'Apple dans leur version
actuelle, HTML et CSS largement disponibles en 2026.

Ne jamais se fier à sa mémoire pour une valeur mesurable — contraste, taille,
largeur, débord : la mesurer. Si un point dépend d'une évolution récente et que
la réponse changerait la décision, le dire plutôt que de deviner.

## Ce qui ne change pas

- **Les faits** : liens App Store ou TestFlight, adresses de contact, dates,
  prix, noms. Et le fond juridique de `confidentialite.html` : seules les fautes
  de frappe et la mise en forme s'y corrigent librement, le sens reste
  identique.
- **L'identité visuelle et la palette** (voir `README.md`). Une teinte peut être
  ajustée pour atteindre un contraste suffisant ; la palette ne change pas.
- **Deux fichiers HTML autonomes, CSS intégré** : aucune dépendance externe,
  aucun CDN, aucune police téléchargée, aucun script tiers, aucun traceur,
  aucune étape de build. Ajouter un fichier au site se décide avec Johan.
- **Aucune fonctionnalité de l'application qui ne soit certaine.**
- **La feuille de style, l'en-tête et le pied de page sont identiques d'une page
  à l'autre** : toute retouche de l'une est reportée dans l'autre.

## Vérifications avant toute pull request

Un Chromium sans interface est disponible dans l'environnement :
`/opt/pw-browsers/chromium_headless_shell-1194/chrome-linux/headless_shell`
(`--no-sandbox --window-size=375,900`, puis `--screenshot` ou `--dump-dom`).
S'en servir pour mesurer et pour regarder les pages, plutôt que de raisonner sur
le CSS seul.

- **Contrastes** calculés par script dans le navigateur, sur les couleurs
  finales après transparence et superposition : 4,5:1 pour le texte, 3:1 pour
  les grands titres et les icônes.
- **HTML valide** : balises fermées, un seul `h1` par page, titres dans l'ordre,
  aucun identifiant en double, repères `header` / `nav` / `main` / `footer`.
- **Liens** : tous les liens internes et toutes les ancres.
- **Mobile** : aucun défilement horizontal à 375 px ni à 320 px, texte normal et
  texte agrandi, avant comme après une réponse dans la mini-partie d'accueil.
- **Typographie française** : espace insécable avant `:` `;` `?` `!`, guillemets
  « et ».
- **Rendu réel** : captures avant/après sur téléphone et sur ordinateur.

## Git

`main` ne reçoit jamais de commit direct. Chaque changement passe par une
branche `claude/…` et une pull request vers `main`, en français, structurée en
« Ce qui change », « Pourquoi » (avec les chiffres : « contraste passé de 3,2:1
à 7,1:1 ») et « Ce que j'ai vérifié », écrite pour quelqu'un qui n'est pas
développeur. Fusionner sa propre pull request est autorisé une fois toutes les
vérifications au vert, avec un commit de fusion.

La commande `gh` n'existe pas dans cet environnement : utiliser les outils du
serveur GitHub (`mcp__github__…`).

## Relecture quotidienne

Une tâche planifiée relit le site une fois par jour. Chaque relecture se termine
par une liste d'améliorations possibles, classées de la plus utile à la moins
utile pour les visiteurs, en distinguant ce qui peut être fait seul de ce qui
demande une décision ou une information de Johan. Cette liste est tenue à jour
dans la section « À faire » du `README.md` : les entrées faites en sortent, les
nouvelles y entrent.
