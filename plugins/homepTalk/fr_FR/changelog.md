---
layout: default
lang: fr_FR
title: Plugin homepTalk - Changelog
description: Changelog du plugin homepTalk
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour d'orthographe ou pour la compatibilité Jeedom V4.x

Changelog
=========

En Beta
-------
* Changement de la qualité de conversion des mp3.
* Sur AirPlay2 et sur un HomePod individuel (qui n'est pas en groupe multi-room à ce moment là) : s'il joue de la musique, on garde son volume d'avant et après avoir joué notre son, on remet le volume et on fait play.
  (malheureusement ce n'est pas possible quand un HomePod est en groupe multi-room, le play lance autre chose et casse le multi-room).
* Corrigé OSX 27 qui posait problème avec la commande say.
* Nouvelle fonctionnalité jingle pour passer un son juste avant une annonce parlée. Permet d'éviter que le premier son soit coupé par le second son envoyé.
* Génération du son légèrement plus rapide.
* Nouveau son CFF des trains suisses.

18-09-2026
----------
* Harmonisation, on peut/doit maintenant choisir si on utilise AirPlay 1 ou 2 pour chaque périphérique et groupe (un groupe doit donc être homogène !!), plus de paramètre global.
* Par défaut tous les HomePods et les groupes sont en Airplay 2
* Par défaut tous les autres équipements sont en Airplay 1
* Fix du son alarme qui n'était pas en mp3
* Coupure des phrases plus intelligemment pour GoogleTTS qui est limité à 99 caractères, on coupe d’abord sur la ponctuation (sauf si c’est suivit d’un chiffre comme 53,2). Ce qui permet d’avoir des phrases plus naturelles, avec des pauses au bon moment

17-09-2026
----------
* Option pour forcer libroap sur un équipement (pour les compatibles AirPlay 1 seulement)

16-09-2026
----------
* Modification massive du plugin pour utiliser la lib atvremote à la place de libroap pour que le plugin continue à fonctionner en iOS/TVOS 27.
* Les groupes fonctionnent aussi.
* Dans la configuration du plugin atvremote est coché par défaut maintenant.

21-02-2025
----------
* Ajout reconnaissance Denon Home Sound Bar 550

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
