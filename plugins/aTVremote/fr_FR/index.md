---
layout: default
lang: fr_FR
title: Plugin aTVRemote
description: Documentation du plugin aTVRemote
---

Ce plugin permet de monitorer et exécuter quelques actions sur vos AppleTV.

Veuillez Noter 
==============
- Compatible uniquement avec **Debian Stretch au minimum** mais Buster conseillé !! (Pas compatible Debian Jessie)
- Ce plugin utilise le protocole MRP pour communiquer avec votre AppleTV 4 et 4K. 
- Il n'est pas possible avec ce protocole de :
  - Modifier le volume (c'est votre TV qui s'en charge)
  - Effectuer le bouton "Micro" (Siri) de la télécommande :'(
- Ce plugin utilise le protocole DMAP pour communiquer avec votre AppleTV3.
- Il n'est pas possible avec ce protocole de :
  - Mettre en veille votre AppleTV3.
  - Effectuer des pressions longue sur les boutons (je vous ai vu venir...) de l'AppleTV3.
  - Modifier le volume (c'est votre TV qui s'en charge)
  - Effectuer le bouton "Micro" (Siri) de la télécommande :'(
  - Savoir si votre AppleTV3 est en Veille ou pas (Elle continue aussi à répondre aux pings dans les deux cas)
- Si votre AppleTV3 est en veille et vous cliquer sur une commande type Menu, elle sortira de veille. (ca dépends des touches...)
- Testé sur AppleTV 4 et 4K aussi. Pour l'AppleTV 3, les fonctionnalités sont limitées...
- **Le partage à Domicile DOIT être activé dans Réglages > Comptes > Partage à domicile.** (toujours nécessaire ?)
- **Votre AppleTV DOIT avoir une ip fixée (soit par réservation DHCP soit dans les Réglages)**
- **L'AppleTV DOIT être dans le même réseau que votre jeedom (sans routage !!, elle est découverte par le protocole Bonjour)**
- Sur AppleTV3, les données de lecture sont renouvellées toutes les minutes SI vous avez cliqué sur Play VIA JEEDOM (Jusqu'à avoir cliqué sur Pause ou Stop). Car si je scan ces données de lecture en permanance, votre AppleTV sort de veille :'( 
- Conseil AppleTV3 : activez la mise en veille automatique pour contrer l'impossibilité de mettre en veille.

Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer et de lancer les dépendances.

Configuration des équipements 
=============================

Ajout Rapide :
--------------
**SI** votre AppleTV a le Partage à domicile activé, Lancez un scan. Celle-ci s'ajoutera en désactivé et invisible.
Modifiez l'équipement créé et Activez-le + Placez le dans une pièce et visible.


Description Complète
--------------------
La configuration des équipements AppleTV est accessible à partir du menu
plugins puis Multimédia. Vous retrouvez ici :

-   un bouton pour lancer un scan.

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements

-   enfin en dessous vous retrouvez la liste de vos équipements

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

Onglet Equipement
-----------------

-   **Nom de l’équipement** : nom de votre équipement

-   **Activer** : permet de rendre votre équipement actif

-   **Visible** : le rend visible sur le dashboard

-   **Objet parent** : indique l’objet parent auquel appartient
    l’équipement

-   **Ip de l'AppleTV** : l'ip et port de votre AppleTV

-   **MAC** : Adresse mac de votre AppleTV


Onglet Commandes
----------------
Il existe de nombreuses commandes. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non les réorganiser. 

-   **Lecture en cours** : Binaire permettant de déterminer si la lecture est en cours ou pas.
-   **URL Artwork** : permet d'afficher l'image.
-   **Hors Veille** : Binaire permettant de déterminer si l'appleTV 4+ est allumée.
-   **Bouton On** : *turn_on* : permet d'allumer l'appleTV 4+.
-   **Bouton Off**: *turn_off*: permet de mettre en veille l'appleTV 4+.
-   **Bouton Lecture** : *play* : Effectue la même action que le bouton play/pause de la télécommande.
-   **Bouton Pause** : *pause* : Effectue la même action que le bouton play/pause de la télécommande.
-   **Bouton Stop** : *stop* : Effectue la même action que le bouton play/pause de la télécommande (idem bouton pause en fait).
-   **Bouton Précédent** : *previous* : Passe au morceau Précédent.
-   **Bouton Suivant** : *next* : Passe au morceau Suivant.

-   **Bouton Haut** : *up* : Effectue la même action que un swipe vers le haut sur la télécommande.
-   **Bouton Gauche** : *left* : Effectue la même action que un swipe vers la gauche sur la télécommande.
-   **Bouton Sélection** : *select* : Effectue la même action qu'un click sur la télécommande.
-   **Bouton Droit** : *right* : Effectue la même action que un swipe vers la gauche sur la télécommande.
-   **Bouton Bas** : *down* : Effectue la même action que un swipe vers le bas sur la télécommande.

-   **Bouton Menu** : *menu* : Effectue la même action que le bouton Menu sur la télécommande.
-   **Bouton Home** : *top_menu* : Effectue la même action que le bouton Home sur la télécommande.

-   **Bouton Aléatoire ON** : *set_shuffle=1* : Active le mode Aléatoire.
-   **Bouton Aléatoire OFF** : *set_shuffle=0* : Désactive le mode Aléatoire.

-   **Bouton Répétition Tout** : *set_repeat=2* : Répète tout.
-   **Bouton Répétition Piste** : *set_repeat=1* : Répète la piste.
-   **Bouton Répétition OFF** : *set_repeat=0* : Désactive le mode Répétition.

-   **Statut** : Affiche l'état en langage humain.
-   **Artiste** : Affiche l'artiste de la lecture en cours si disponible.
-   **Titre** : Affiche le titre de la lecture en cours si disponible.
-   **Album** : Affiche l'album de la lecture en cours si disponible.
-   **Genre** : Affiche le genre de la lecture en cours si disponible.
-   **Type Media** : Affiche le type de media de la lecture en cours si disponible. (souvent Unknown ou Music)
-   **Position** : Affiche la position dans la lecture en cours si disponible.

-   **Repeat** : Affiche l'état du mode Répétition.
-   **Shuffle** : Affiche l'état du mode Aléatoire.

-   **App Active** : Affiche l'application active (si possible...)






