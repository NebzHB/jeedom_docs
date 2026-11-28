---
layout: default
lang: fr_FR
title: Plugin aTVRemote
description: Documentation du plugin aTVRemote
---

Ce plugin permet de suivre et de piloter depuis Jeedom vos **Apple TV** et vos **HomePod** : ce qui est en cours de lecture (titre, artiste, pochette, progression), lecture / pause / précédent / suivant, volume, aléatoire, répétition, et pour l'Apple TV la télécommande, la mise en veille et le lancement d'applications.

Il s'appuie sur la bibliothèque [pyatv](https://pyatv.dev/) (protocoles AirPlay et Companion).

Appareils pris en charge
========================

| Appareil | Modèles |
|---|---|
| Apple TV | Apple TV 3 (fonctions limitées), Apple TV HD, Apple TV 4K (1re à 4e génération, y compris celle de 2026) |
| HomePod | HomePod (1re et 2e génération), HomePod mini, HomePod mini 2 (toutes les couleurs) |

Les modèles trop récents pour pyatv (qui ne donne alors que l'identifiant Apple, par exemple `AppleTV18,1`) sont reconnus quand même.

Prérequis
=========

- **Jeedom 4.4** minimum et **Debian 12** minimum.
- Pas pris en charge : Debian 11 et plus ancien, Docker, Jeedom Mini+, Raspberry Pi 1 et 2, Raspberry Zero (armv6), systèmes 32 bits (i386).
- L'appareil doit être **dans le même réseau que Jeedom** (sans routage : il est découvert par Bonjour / mDNS).
- Donnez une **adresse IP fixe** à vos Apple TV et HomePod (réservation DHCP conseillée).
- Sur l'Apple TV : **Réglages > AirPlay et HomeKit > AirPlay : Oui**, et **Autoriser l'accès : « Tout le monde » ou « Toute personne sur le même réseau »**.

Ce qui n'est pas possible
-------------------------

- Le bouton « Micro » (Siri) de la télécommande.
- Sur Apple TV 3 : la mise en veille, les appuis longs, savoir si elle est en veille. Les infos de lecture ne sont relues que si la lecture a été lancée depuis Jeedom (sinon l'interroger la sortirait de veille). Conseil : activez sa mise en veille automatique.
- L'aléatoire et la répétition ne sont utilisables que si la source les accepte (voir la partie « Aléatoire et répétition »).

Configuration du plugin
=======================

Après installation, activez le plugin puis lancez les **dépendances** (et relancez-les après chaque mise à jour en beta).

Démon
-----

Le plugin utilise un démon Python, qui garde une connexion avec chaque appareil :
- l'état (lecture, volume, veille, fonctions disponibles) est reçu **en temps réel**, sans que Jeedom ait besoin d'interroger les appareils ;
- la **pochette** est récupérée dès le changement de morceau ;
- chaque commande renvoie son **vrai résultat** (voir la partie « Notifications ») ;
- peu de mémoire : environ 72 Mo pour un appareil, quelques Mo de plus par appareil.

Son log est **aTVremote_deamon**. Au démarrage, il indique la date de son fichier et la version de pyatv, puis « Connecté avec succès ! » pour chaque appareil.

Personnalisation du widget
--------------------------

**Mode de défilement des champs Titre, Artiste et Album** : *Alterné* (le texte va et vient) ou *Défilement* (le texte défile en boucle) quand il est trop long pour le widget. Fonctionne aussi sous Safari (iPhone, iPad, Mac).

Ajout des équipements
=====================

Lancez une **détection** depuis la page du plugin (Plugins > Multimédia > aTV Remote). Chaque appareil trouvé est ajouté **désactivé et invisible** : ouvrez-le, activez-le, rendez-le visible, placez-le dans une pièce et sauvegardez. Une nouvelle détection met à jour les équipements existants (IP, modèle, version de l'OS).

Les HomePod sont nommés « … (Airplay) ».

Onglet Équipement
-----------------

- **Nom**, **Objet parent**, **Activer**, **Visible** : comme pour tout équipement Jeedom.
- **Périphérique, Version, OS, Version de l'OS** : détectés automatiquement.
- **IP**, **MAC** : adresse de l'appareil (en lecture seule).
- **Couleur** (HomePod 1re génération, HomePod mini et mini 2) : couleur du HomePod sur le widget. HomePod : noir, blanc ; HomePod mini : noir, blanc, rouge, jaune, bleu ; HomePod mini 2 : noir, blanc, vert, rose, bleu.
- **Volume + / Volume -** (Apple TV) : commandes Jeedom à utiliser pour régler le volume de la télé (via un équipement infrarouge, Harmony…), quand l'Apple TV ne peut pas le faire elle-même.
- **Appairage** (Apple TV) : voir ci-dessous.

Appairage des Apple TV
======================

Les Apple TV demandent un appairage, une seule fois, pour autoriser Jeedom :

- **AirPlay** : télécommande, lecture, état, pochette ;
- **Companion** (Apple TV 4 et plus) : lancement des apps, allumer / éteindre, clavier.

Les HomePod n'ont pas besoin d'appairage.

La ligne **Appairage** de l'équipement indique l'état global : **Appairée** seulement si tous les protocoles demandés par l'Apple TV sont appairés, sinon **À appairer**, avec le détail (par exemple « AirPlay ✓ · Companion ✗ »).

1. Allumez la télé et l'Apple TV (pas en veille) et restez devant l'écran.
2. Cliquez sur **Appairer** : l'assistant explique les étapes et liste les protocoles à appairer.
3. Pour chaque protocole, l'Apple TV affiche un **code à 4 chiffres** : saisissez-le dans Jeedom (sur téléphone, le clavier numérique s'ouvre et le code est validé au 4e chiffre).
4. Les clés sont enregistrées et la connexion est relancée automatiquement, sans redémarrer le démon.

Si le code ne s'affiche pas : vérifiez que la télé affiche bien l'Apple TV, et les réglages AirPlay de l'Apple TV (voir la partie « Prérequis »). Le code reste valable environ 3 minutes ; le bouton **Nouveau code** en redemande un. Quand tout est appairé, le bouton devient **Refaire l'appairage**.

Le widget HomePod
=================

- **Pochette** du morceau sur un fond flouté. Elle est gardée quand la lecture s'arrête (Lecture relance ce morceau).
- **Barre de progression** sous la pochette ; au survol : position, durée, pourcentage et temps restant.
- **Indicateur** à côté de la pochette : égaliseur en lecture, animation de chargement après précédent / suivant ou quand l'appareil charge (20 s maximum), et indication quand le démon est arrêté.
- **Précédent / suivant** restent grisés jusqu'à ce que le morceau change.
- **Volume** : curseur circulaire et boutons + / -.
- **Panneau Info** (bouton *i*) : grande pochette, titre, artiste et album (défilement si trop long), progression, et un lien **Ouvrir dans Apple Music** quand le morceau vient d'Apple Music (pas pour Spotify, une radio ou un flux AirPlay). Se ferme d'un clic ou avec Échap.
- Utilisable **au clavier et avec un lecteur d'écran** ; textes traduits en anglais, allemand, espagnol, italien et portugais.
- Même widget sur le Dashboard et sur mobile ; sur écran tactile, les boutons ne restent plus « appuyés ».

Aléatoire et répétition
-----------------------

Ils ne sont utilisables que si la source les accepte. Par exemple, Apple Music lu directement sur un HomePod ne les accepte pas : le HomePod répond « ok » mais ne change rien. Le plugin relit les fonctions disponibles après chaque changement de morceau ou d'application, et **grise** les boutons quand ils sont indisponibles (ils restent cliquables : un clic revérifie).

Notifications
-------------

- Une commande indisponible pour la source en cours (bouton grisé) affiche une **notification** sur le Dashboard, sans erreur dans le log ; une vraie erreur (appareil qui refuse, pas de réponse, paramètre invalide) est une erreur de la commande, visible aussi dans le centre de messages et le log des scénarios.
- Une commande lancée alors que le démon est **arrêté** affiche « démon aTVremote arrêté, commande non envoyée ».

Onglet Commandes
================

Toutes les commandes ne sont pas affichées par défaut : vous pouvez les renommer, les afficher ou non, les réorganiser.

Infos
-----

- **Statut** : état en clair : Lecture en cours, En pause, Stoppé, Chargement en cours, Avance / Recul rapide, Inactif, Aucun Media.
- **Lecture en cours** : binaire, 1 si l'appareil joue.
- **Hors Veille** (Apple TV 4 et plus) : binaire, 1 si l'Apple TV est allumée.
- **Titre**, **Artiste**, **Album**, **Genre**, **Type Media** : informations sur la lecture en cours, si disponibles.
- **Position** : position et durée, par exemple `5s/03:50 (2%)`.
- **URL Artwork** : chemin de la pochette.
- **Répétition** / **Répétition Humain**, **Aléatoire** / **Aléatoire Humain** : état des modes.
- **App Active** : identifiant de l'application qui joue (par exemple `com.apple.Music`).
- **Info Volume** : volume de 0 à 100.
- **Hash** (masquée) : identifiant du morceau.
- HomePod, masquées, utilisées par le widget et utilisables en scénario :
  - **Aléatoire disponible**, **Répétition disponible** : 1 si la source en cours les accepte ;
  - **Identifiant iTunes** : identifiant Apple Music / iTunes Store du morceau (`-` pour les autres sources).

Actions
-------

- **Rafraichir** : relit l'état de l'appareil.
- **Bouton Lecture**, **Bouton Pause**, **Bouton Stop**, **Bouton Précédent**, **Bouton Suivant**.
- **Bouton Aléatoire ON / OFF**, **Bouton Répétition Tout / Piste / OFF**.
- **Bouton Volume + / -**, **Variateur Volume** (HomePod).
- Apple TV 4 et plus :
  - **Bouton On / Off** : sortie de veille, mise en veille ;
  - **Bouton Haut / Bas / Gauche / Droit / Sélection**, **Bouton Menu**, **Bouton Home** : télécommande ;
  - **Bouton Chaîne Haut / Bas** ;
  - **MàJ Liste App** et **Lancer App** : liste des applications installées et lancement de l'une d'elles (appairage Companion nécessaire).
- **Commande Personnalisée** (masquée) : envoie une ou plusieurs commandes pyatv brutes, séparées par `|` (par exemple `features`, ou `set_volume=30|volume`).

FAQ
===

**Le démon ne démarre pas ou rien ne remonte.**
Relancez les dépendances, redémarrez le démon en mode debug et regardez le log **aTVremote_deamon**. La ligne de démarrage indique la date de son fichier et la version de pyatv, puis chaque appareil doit afficher « Connecté avec succès ! ».

**Aléatoire / répétition ne font rien.**
La source ne les accepte pas (par exemple Apple Music joué directement sur le HomePod) : les boutons sont grisés. Voir la partie « Aléatoire et répétition ».

**Mon Apple TV récente apparaît avec un OS inconnu ou sans commandes.**
Relancez une détection après la mise à jour du plugin : les modèles trop récents pour pyatv sont maintenant reconnus.
