# Couronne de Cendre

Action-RPG 2D vu de dessus, **coop en ligne** : une ville-château partagée que tous les joueurs améliorent ensemble, des régions à explorer à monture, des donjons et des boss aux attaques télégraphiées (zones rouges, esquive).

**Jouer :** https://renwardesk.github.io/couronne-de-cendre/

## Installation sur l'écran d'accueil
- **Android (Chrome)** : ouvrir le lien → menu ⋮ → *Installer l'application* / *Ajouter à l'écran d'accueil*.
- **iPhone (Safari)** : ouvrir le lien → bouton Partager → *Sur l'écran d'accueil*.

## Architecture
- Client : un seul `index.html` (canvas + JS vanilla), `atlas.png`, `snd/`. PWA (manifest + service worker).
- Serveur : **Supabase** (projet `couronne-de-cendre`).
  - Auth : pseudo + mot de passe (le pseudo est converti en e-mail interne, « Confirm email » désactivé).
  - Tables : `cendre_players` (sauvegarde perso), `cendre_world` (ville partagée), `cendre_plots` (terrains).
  - Fonctions RPC (`cendre_upgrade`, `cendre_buy_plot`, `cendre_build`, `cendre_set_furn`) qui vérifient les coûts côté serveur.
  - Realtime : changements de la ville/terrains + présence des joueurs par zone.
- Le monde persiste même quand personne n'est connecté.

## Crédits
- [Ninja Adventure](https://pixel-boy.itch.io/ninja-adventure-asset-pack) — Pixel-boy & AAA, CC0.
- [Pixel Art Top Down – Basic](https://cainos.itch.io/pixel-art-top-down-basic) — Cainos.
- Assets [ansimuz](https://ansimuz.itch.io/) et pack d'interface fourni par l'auteur.
- Musiques et sons : Ninja Adventure (CC0).
