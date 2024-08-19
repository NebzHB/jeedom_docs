---
layout: default
lang: fr_FR
title: Plugin homepTalk - Changelog
description: Changelog du plugin homepTalk
---

Changelog
=========

19-08-2024
----------
* Traductions oubliées (onglet commandes)
  
12-08-2024
----------
* Traductions et mise à jour des traductions en Anglais, Allemand, Espagnol, Italien, Portugais

04-07-2024
----------
* Ajout bouton Communauté pour jeedom 4.4
* Correction warning sur debian 12 php 8
* Le démon de aTVremote n'a pas besoin d'etre lancé pour utiliser la lib dans la configuration (alpha !! ne fonctionne probablement pas !)
* Augmentation de 100ms de la synchronisation entre plusieurs homepods quand on envoi un son à un groupe.
* Affichage de la liste des équipements en lignes si désiré.
* Modification de l'icone, on retire le nom du plugin.
* Changement de mise en page pour moderniser un peu

03-05-2023
----------
* re-fix pour raspberry 64bit (certains fonctionnent différemment... je m'adapte aux deux)
* affichage hardware dans les dep

29-04-2023
----------
* mise à jour pour raspberry 64bit (pas supporté par jeedom mais on essaie quand même...)

28-04-2023
--------
* install des dépendances bcp plus courtes et bcp plus fiables !!!
* dernière lib existante
* fix pour jeedom 4.4
* option dans la config du plugin pour utiliser la lib de atvremote s'il est installé quand on parle sur un seul homepod (fonctionne pas, c'est de l'ALPHA pour jouer)

03-02-2023
----------
* Support du Homepod 2

15-02-2021
----------
* Fix TTs jeedom avec 4.2 (possible que jeedom 3 ne soit plus compatible du coup... je ne le supporte plus de toute façon)

15-10-2021
----------
* Fix images 4.2

18-01-2021
----------
* Ajout des voix dans voiceRSS

11-01-2021
----------
* Discover pour le Yamaha WX-021
* Nouvelle liste des pièces imbriquées

21-12-2020
----------
* Discover pour les Sonos Play:1 Play:3 Play:5

17-11-2020
----------
* Détection et logo Homepod Mini

14-06-2020
-------------
* FFMPEG est installé par le core, suppression de l'install de celui-ci dans les dépendances
* tag v4 das info.json

14-06-2020
-------------
* Fix double install

26-05-2020
-------------
* Compatibilité avec le plugin jeedom Jailbreak pour générer la voix sur un iPhone/iPad jailbreaké
* Installation des dépendances plus claires

06-02-2020
-------------
* Support Airplay2 Tiers : Ajout de détection Sonos One et Yamaha RX-A880 et IKEA Symfonisk
* Gestion du port d'airplay (nécessaire pour players tiers)
* Forcer la communication sur l'IPv4
* ajout avahi-browse oublié dans les dep

19-11-2019
-------------

* Fix ffmpeg à la place de avconv

14-11-2019
-------------

* Version Initiale
