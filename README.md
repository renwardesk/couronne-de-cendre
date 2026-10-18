# Couronne de Cendre

Action-RPG 2D vu de dessus, **coop en ligne** : une ville-château partagée que tous les joueurs améliorent ensemble, des régions à explorer à monture, des donjons et des boss aux attaques télégraphiées (zones rouges, esquive).

**Jouer :** https://renwardesk.github.io/couronne-de-cendre/

## Installation sur l'écran d'accueil
- **Android (Chrome)** : ouvrir le lien → menu ⋮ → *Installer l'application* / *Ajouter à l'écran d'accueil*.
- **iPhone (Safari)** : ouvrir le lien → bouton Partager → *Sur l'écran d'accueil*.

## Contenu du jeu
- **Héros** : à la connexion, on choisit son héros ou on en crée un nouveau (bouton +, 3 au maximum). La classe (Lame, Gardien, Arcaniste) et l'apparence sont définitives.
- **Progression** : à chaque niveau, 3 points de caractéristique (Force, Dextérité, Mana) et 1 point de talent ; arbre de talents de 3 branches par classe.
- **Équipement** : 8 emplacements (arme, main gauche, tête, torse, mains, pieds, amulette, anneau), prérequis de caractéristiques, pièces réservées à une classe, 4 panoplies avec bonus à 2 et 4 pièces.
- **Monde** : 4 grandes régions avec routes, camps, ruines, lacs et forêts ; donjons de 5 salles (combat, pièges, trésor, vagues, boss).
- **Récolte** : bois, pierre, fer, herbes et cristal à ramasser dans les régions.
- **Quêtes** : une vingtaine de quêtes données par les personnages de la cité et des camps.

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
- Musiques : bande originale de [Flare](https://github.com/flareteam/flare-game) par Brandon Morris, CC-BY-SA 3.0.
- Sons : Ninja Adventure (CC0).
