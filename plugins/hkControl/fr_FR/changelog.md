---
layout: default
lang: fr_FR
title: Plugin hkControl - Changelog
description: Changelog du plugin hkControl
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour d'orthographe ou pour la compatibilité Jeedom V4.x

Changelog
=========

10-11-2026 (beta)
--------
**Nouveau : exposer les équipements dans Maison via Homebridge (BETA)**
* Option **Exposer dans Maison** sur la fiche d'un accessoire ou d'un pont appairé : l'équipement est exposé à l'identique dans l'app Maison, par son propre pont Homebridge. Nécessite le plugin homebridge à jour (voir la documentation, section « Exposer dans Maison »).
* QR code et code d'appairage affichés sur la fiche ; l'appairage dans Maison est détecté tout seul, sans recharger la page.
* État de l'exposition dans la page **Santé** (colonne Maison) et icône sur les vignettes des équipements.
* Supprimer un équipement exposé : avertissement, puis proposition de relancer Homebridge pour retirer son pont.
* Les dépendances installent le module homebridge-hkcontrol de la même branche que le plugin (beta ou stable).

**Appairage**
* Refus d'appairage expliqués en clair : code PIN incorrect, accessoire déjà appairé ailleurs, trop de tentatives, accessoire occupé…
* Un accessoire désappairé en dehors de Jeedom est détecté : un message le signale et il peut être réappairé depuis la même fiche, sans perdre ses commandes.
* Bouton **Oublier quand même** quand le désappairage échoue (accessoire hors service ou déjà réinitialisé).
* Supprimer un équipement appairé le désappaire, ou oublie ses clés s'il ne répond pas : plus d'appairage orphelin.
* Pré-appairage (équipements à écran) relançable après un mauvais code ou un redémarrage du démon ; un double clic ne lance plus deux appairages.
* Un appairage qui aboutit après le délai d'attente est conservé (avant : l'accessoire restait appairé à des clés perdues).

**État « En Ligne » et connexions**
* « En Ligne » reflète la connexion réelle avec l'équipement (et non plus un ping) : hors ligne 60 s après une perte de connexion, 10 s si l'équipement est injoignable sur le réseau, 5 s s'il annonce son départ. Tout passe hors ligne quand le démon est arrêté.
* Reconnexion automatique (après 30 s, 1 min, 2 min puis toutes les 5 min) et immédiate dès que l'équipement s'annonce de nouveau. Une coupure est détectée en 40 s environ.
* Changement d'adresse IP ou de port suivi automatiquement ; adresse IPv4 utilisée de préférence.
* Les valeurs sont relues toutes les heures, pour rattraper les changements perdus pendant une indisponibilité de Jeedom.

**Commandes**
* Une commande qui échoue l'affiche (et fait échouer le scénario), avec la raison donnée par l'équipement.
* Sauvegarder un équipement ne réécrit plus les valeurs, l'unité ni l'affichage des commandes.
* Binaires à plusieurs états (0/50/100, 1/2…) corrects ; Ouvrir / Fermer / Stop envoient les valeurs réelles de l'équipement.
* Commande Éteindre ajoutée aux interrupteurs qui ne remontent pas leur état tout seuls (Manual Info).

**Fiabilité**
* Le démon ne plante plus et ne gèle plus sur une réponse anormale d'un équipement ; un démon qui ne répond plus est détecté et relancé par Jeedom ; arrêt propre.
* Fichier des appairages protégé : écriture sûre, copie de secours et récupération automatique (avec message) s'il est abîmé ou supprimé. Un échec d'écriture (disque plein) est signalé et réessayé.
* Le démon se relance tout seul si son port est occupé au démarrage.
* Les appels au démon passent par l'IP interne de Jeedom (fonctionne sous Docker).

**Sécurité et interface**
* Les noms et informations venant des équipements du réseau sont nettoyés avant affichage.
* La clé privée et le code PIN n'apparaissent plus dans les logs.
* Erreurs du serveur affichées (ex. « Le démon n'est pas démarré ») au lieu d'une alerte vide.
* Log du démon allégé (plus de ligne toutes les 5 s pour le test de vie).

28-09-2026
--------
* Meilleur arret du démon
* Désactivation du bouton Appairage (et Rafraichir) pendant l'appairage pour éviter les doubles clicks
* Message plus clair quand on reçoit une erreur EHOSTUNREACH : Périphérique injoignable sur le réseau
* Quand on essaie de désappairer un équipement qui ne l'est plus, repasser le bouton à "Appairer"
* Beaucoup moins de blocages possibles dans le démon, même si le périphérique ne réponds pas, on affiche un timeout mais ça ne gèle plus le démon.
* Si un périphérique perd sa connection aux évènements, on réessaie 3x et puis on ne refait pas à chaque fois la reconnexion aux évènements, il devrait la refaire de lui même... (pour pas charger les petits périphériques peu puissants)
* Moins d'écritures disque et mise en async pour ne pas bloquer le démon
* Ajout du dossier resources/node_modules aux exclusions de backup
* Mise à jour librairies

01-04-2026
----------
* Mise à jour des dépendances et NodeJS 22 par défaut

07-04-2025
----------
* Correction d'un problème de ExpressJS 5. (Breaking change, changing "query parser" to "extended")

24-03-2025
----------
* Correction de messages d'erreurs dans certains cas

31-10-2024
----------
* Mise à jour de la librairie homekit : permet d'installer le plugin sur docker sans problème (ou sur LXC).

09-10-2024
----------
* Ajout de l'option "Inverser" sur les binaires.

07-10-2024
----------
* Ajout Bouton Communauté pour obtenir une aide plus façilement

12-09-2024
-------------
* Migration vers NodeJS 20

10/11-09-2024
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
