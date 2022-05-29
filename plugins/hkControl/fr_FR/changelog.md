---
layout: default
lang: fr_FR
title: Plugin hkControl - Changelog
description: Changelog du plugin hkControl
---

Changelog
=========

29/05/2022
--------------------

* Ajout d'un timeout de 10sec pour setAccessorries (les actions venant de jeedom).
* Traduction en Anglais.
* Repasser en connexion non permanente car cela semble poser problème à certains équipements

14-02-2022
----------

* Version de Jeedom 4.0 MINIMUM !!! le plugin sur une V3 ne recevra plus de mise à jour et n'est plus supporté !
* Connexions permanente pour les équipements (commandes actions plus rapides)
* Correctif pour les problèmes de double souscriptions ou de plantage après refresh
* Divers correctifs pour gérer les déconnexions des équipements et les reprendre automatiquement quand ils reviennent.
* Logs plus clairs et plus détaillés en cas de problème

12-02-2022
----------

* Freeze de la version du plugin pour Jeedom V3 sur la stable du 16-11-2021. La V3 n'aura plus d'update du plugin. Fin du support pour la V3. Si vous avez reçu cette mise à jour, vous êtes toujours en V3, mettez à jour en V4 minimum au plus vite !

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
