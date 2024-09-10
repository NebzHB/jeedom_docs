---
layout: default
lang: fr_FR
title: Plugin hkControl - Changelog
description: Changelog du plugin hkControl
---

Changelog
=========

10-09-2024
----------
* Mise à jour pour autoriser les mises à jour en debian > 12.0

29-08-2024
----------
* Jeedom 4.4 Obligatoire
* Debian 11 Obligatoire

12-08-2024
----------
* Traductions et mise à jour des traductions en Anglais, Allemand, Espagnol, Italien, Portugais
* Correction d'un niveau de log par défaut qui passait pas dans le démon

03-07-2024
----------
* Affichage dans le market que Debian Buster (10) n'est plus supporté
* Fix pour éviter une division par zéro si un équipement ne renvoi pas son minStep

12-06-2024
----------
* Rien n'a été mis à jour, juste pour vous informer que si vous êtes toujours en Debian 10 Buster, à partir du 1er juillet 2024, votre système ne sera plus supporté. Vous ne pourrez donc plus faire appel au support pour ce plugin. Mettez à jour en Debian 11.

31-05-2024
----------
* Retiré une commande en double des dépendances.

30-05-2024
----------
* Forcer les dépendances en IPv4 pour les réseaux mal configurés en IPv6

28-05-2024
----------
* Ne plus forcer à installer les dépendances sur buster après le 30 juin 2024 (fin du support de buster). Cela permet que le démon continue de tourner comme il est sans forcer les dépendances s'il y a des mises à jour de libraires. A partir de cette date, buster ne sera plus supporté par le plugin, mais il devrait continuer à fonctionner tel quel grace à cette modification. Sauf pour les nouvelles installations sous buster, mais ça ne devrait pas arriver.
* Mise à jour Axios

23-05-2024
-------
* Ajout de la gestion de la version de NPM
* Meilleur arret du démon
* Si un équipement envoi une "Déconnexion des Events", lorsqu'on tente de se reconnecter, on redemande les dernières valeurs à l'équipements pour les envoyer à Jeedom (des fois qu'on aurait loupé des évènements pendant cette coupure). 

22-03-2024
--------
* FIN DU SUPPORT DES VERSIONS DE JEEDOM < 4.2 ! VOUS NE VERREZ PAS L'UPDATE SI VOUS AVEZ UNE VIEILLE VERSION
* Passage en JSONRPC plutot que event (plus robuste)
* Fix sur certains booléens suite au passage en JSONRPC
* Passage du démon en axios plutot que request qui est obsolète
* Ajout du timing dans l'installation des dépendances
* Plus besoin de redémarrer le démon quand on change le niveau de log dans la config du plugin, l'info est envoyée au démon directement.
* Correction pour les équipements qui ont le même nom qu'un équipement déjà existant
* Meilleure vérification des dépendances, toutes les libs doivent être à la bonne version !

02-12-2023
----------
* Correctif gestion couleurs pour les ampoules.

28-11-2023
----------
* Si on recoit 100 sur une valeur binary, c'est true (Volets Celiane nouvelle version)
* Transformation des détecteurs d'occupation en binaires (pour l'Aqara FP2, pour pouvoir l'utiliser dans le plugin alarme), plutot qu'un numérique avec 0 et 1 comme valeur (comme le fait Apple).
* Meilleure gestion si le fichier d'appairage est vide, on ne quitte pas tout, on fait avec.

14-10-2023
----------
* Correction du message : PHP Notice:  Undefined index: serviceOriginalName in /var/www/html/plugins/hkControl/core/class/hkControl.class.php on line 711

30-09-2023
-----------
* NodeJS 18

26-05-2023
----------
* Fix orthographe + statistiques

05-05-2023
----------
* Augmentation du timeout à 90sec à la place de 60sec (le Aqara FP2 est lent à répondre)
* Affichage du nom du service (s'il est fourni) dans la liste des commandes
* Bouton Rafraichir pour accessoires en plus que pour les ponts

03-04-2023
----------

* Petit fix pour erreurs ajax en Jeedom 4.4 + version minimale jeedom 4.0 (les jeedom v3 ont toujours accès à l'ancienne version du plugin avant 14-02-2022)

27-03-2023
----------

* Mise à jour librairies
* Correction sur commande refresh dans certains cas
* Fix pour support Ikea Dirigera (à confirmer)

(les dépendances devraient se relancer toutes seules)

16-10-2022
----------

* Utilisation d'un port libre aléatoire pour le démon
* Installation des dépendances plus rapide
* Ajout d'un timeout si la souscription aux évènements d'un équipement prend plus de 10sec + reconnexion + renvoi de la commande après reconnexion
* Ajout d'une ligne sur le hardware au début de l'install des dépendances pour aider au diagnostique
* Correctif pour cmdNameExist en utilisant directement cmd::byEqLogicIdCmdName
* Correction du désappairage lorsqu'on supprime un équipement appairé
* Mémorisation de la version précédente à chaque mise à jour pour éviter les "depuis la dernière mise à jour" sans avoir d'où on vient.
* Pour les booléens, on fait un getValue et si la valeur est différente de l'event, on utilise cette valeur. (fix pour certaines lumières meross)
* On stop les dépendances si erreur dans les sources
* Rediscover si "ServiceChanged"
* On floute le code pin et le numéro de série (défloute si on passe la souris par dessus ou rentre dans le champ ou s'il est vide (pour les captures d'écran etc)
* Bouton de redécouverte (pour ne pas avoir à relancer le démon)
* En cas de déconnexion d'un périphérique, on tente de se reconnecter toutes les 1 min pendant 5 min, puis toutes les 5 min. (Permet un temps plus court sur les périphériques qui ont des problèmes wifi)

03-06-2022
----------

* Message d'erreur plus clair si on veut faire une action et que l'équipement n'a pas dit de "Bonjour"

01-06-2022
----------

* Utilise NodeJS 16
* Correction pour les unités qui pouvaient ne pas passer

29-05-2022
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
