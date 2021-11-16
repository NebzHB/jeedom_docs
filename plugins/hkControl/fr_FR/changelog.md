---
layout: default
lang: fr_FR
title: Plugin hkControl - Changelog
description: Changelog du plugin hkControl
---

Changelog
=========

16-11-2021
----------

* Nouvelle méthode d'appairage, qui devrait permettre de nouveaux périphériques (prises Meross + autres ?).
* Compatibilité Jeedom 4.2
* A la découverte d'équipements, si l'équipement avec le même nom existe déjà (dans un autre plugin par ex), ajouter l'id derrière le nom

18-08-2021
----------

* Compatibilité Debian 11 (utilisation de node à la place de nodejs)

30-04-2021
----------

* Augmentation du timeout en cas d'action de 30sec à 60sec

26-04-2021
----------

* Caractéristique "Active" (pour les valves par exemple) n'est plus une commande de type select mais deux commandes Activer et Désactiver (afin de mieux coller aux types génériques Valve)

12-04-2021
----------------------

* Version Initiale en stable
