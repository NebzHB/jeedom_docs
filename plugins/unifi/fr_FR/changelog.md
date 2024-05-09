---
layout: default
lang: fr_FR
title: Plugin Unifi - Changelog
description: Changelog du plugin Unifi
---

# 09-05-2024

* Meilleure vérification des dépendances.
* Meilleur arret du démon.
* Ignorer led_enabled sur les controleurs qui ne le mettent pas à jour + message en debug dans le log.
* Passage des commandes en POST plutot qu'en GET pour être certain que tout passe sur les switchs avec beaucoup de ports (POE Enable etc)
* Optimisations diverses

# 18-03-2024

* Ajout d'un ignore sur les mises à jour d'une nouvelle valeur apparue en unifi 8.1.113 (wifi_tx_retries_percentage) sur les clients .

# 20-02-2024

* Fix d'un problème de détection des équipements du même nom dans la même pièce : permet d'éviter les doublons et erreurs de sql quand plusieurs équipements ont le même nom dans le controleur Unifi

# 22-01-2024

* FIN DU SUPPORT POUR JEEDOM < 4.2 ! LA MISE A JOUR NE VOUS SERA PAS PRESENTÉE PAR JEEDOM SI VOUS AVEZ UNE ANCIENNE VERSION
* On envoi plus toutes les configurations du démon en ligne de commande mais via un évènement de type configuration quand le démon a dit qu'il était prêt.
* Notification pour les configurations qui sont envoyées directement au démon quand il est allumé ou s'il faut le relancer (info contrôleur)
* Utilisation de axios dans le démon plutot que request qui est déprécié
* Optimisation de la file d'attente des évènements à envoyer à Jeedom
* Ajout du timing d'installation dans les dépendances

# 17-12-2023

* Correction de la couleur des notifications d'ajout de devices et client en vert plutot que orange
* Aide à l'encodage du site dans la config, si on encode toute l'url (ce qu'il ne faut pas faire !!! voir doc !!!), on essaie de capturer le nom du site dans cette url.

# 15-12-2023

* Correction pour les UDM qui ne répondent pas au PING mais qui renvoient bien des évènements (plus de coupure du démon dans ce cas précis)
* Correction sur la réparation de NodeJS qui pouvait ne pas se lancer
* Obfuscation (on cache) du mot de passe d'adoption des devices dans les logs (et authentication key + guest token)
* Les configurations pour ignorer certaines commandes, pour la durée du cycle des relevés Site et WLAN et le log des évènements bruts n'ont plus besoin de relancer le démon pour être appliquées, elles sont directement envoyées au démon s'il est lancé !
* Il n'est plus nécessaire de relancer le démon lorsqu'on change le niveau de log ! merci @Bad  
* **Nouveauté !** Ajout de la gestion des évènements bruts dans l'équipement site > onglet "Automatisations Evènements" (voir doc : https://nebzhb.github.io/jeedom_docs/plugins/unifi/fr_FR/#tocAnchor-1-3-2)

# 13-12-2023

* On force la mise à jour des dépendances si on a une vieille version de la librairie unifi.

# 03-12-2023

* Affichage de tous les évenements reçus dans les logs en debug, même ceux qu'on gère pas. (pour aider au debug dans certains cas)
* Commande Powersave_Enabled est maintenant ignorable si on le désire
* Changement d'affichage des commandes clients ignorables dans la config du plugin (pour en afficher plus)
* On ignore certaines raisons de mises à jour des clients non utilisées de toute façon pour réduire la charge

# 02-12-2023

* Ajout commande Signal et mise à jour du signal optionnelle dans la configuration du plugin
* Gestion des nouveaux évènements clients (controleur 8+)

# 27-11-2023

* Prise en charge UXG-Lite
* Gestion des évenements de présence compatible avec controleur 8.0.7 (tout en restant compatible avec la v7)
* Mise à jour des images des équipements sur base du controleur 8.0.7.

# 30-09-2023

* Fix pour les infos poe des ports de switchs, ils ont retiré un identifiant sur les ports, il faut donc les supprimer à la main tous (ou le switch) et refaire une découverte pour qu'il prenne les nouveaux identifiants.
* ignore les modifs de tx_retry_burst_count
* NodeJS 18

# 10-05-2023

* Mise à jour pour gérer les connexions/déconnexions aux réseaux Invités

# 03-04-2023

* Petit fix pour ajax en Jeedom 4.4.

# 01-12-2022

* Reconnexion automatique du démon en cas de coupure du websocket par le controleur (sans redémarrer). Pour palier au plantage du websocket par le controleur sur UDM. (et pas sur le controleur software)
* Encryption login et pass dans la DB jeedom
* En cas de renommage d'équipement ou de client coté controleur, si le nom existe déjà dans la pièce, on affiche un warning dans le plugin.
* Update de la librairie mais qui ne change pas grand chose à part des mises à jour de ses propres librairies
* Optimisation pour Jeedom 4.4

# 26-08-2022

* Floutage du numéro de série sur la fiche équipement, sauf quand la souris passe dessus.

# 22-08-2022

* Correctif pour cmdNameExist en utilisant directement cmd::byEqLogicIdCmdName
* Ajout d'une ligne sur le hardware au début de l'install des dépendances pour aider au diagnostique
* Mémorisation de la version précédente à chaque mise à jour pour éviter les "depuis la dernière mise à jour" sans avoir d'où on vient.

# 08-08-2022

* Réduction de la mémoire nécessaire pour créer un équipement avec bcp de commande en utilisant getCmd(null,logicalId) à la place de getCmd(null)
* Utilisation d'un port libre aléatoire pour le démon
* Installation des dépendances plus rapide
* Ajout Gestion POE sur les UDM qui le supportent (le mieux est de supprimer l'équipement et le redécouvrir, les commandes seront mieux ordonnées)
* Retiré la commande powercycle sur les ports de switchs qui ne supportent pas le POE (supprimer et redécouvrir l'équipement ou supprimer à la main la commande)
* Arret de l'install des dépendances si erreur de sources apt

# 14-06-2022

* Message d'erreur plus explicite dans le log "unifi" si le démon n'est pas lancé au moment d'une commande

# 01-06-2022

* Sécurisation API
* Cacher satisfaction_real satisfaction_now et satisfaction_reason qui ne sont pas utilisés (arrivés probablement en 7.0.21)
* Forcer l'écoute du démon en IPv4 seulement.
* Correction pour le renommage automatique des équipements dans jeedom lorsqu'on renomme coté controleur.
* Correction fenetre santé : bloqué était inversé.
* Si EADDRINUSE on réessaie dans 1 seconde.
* Update des images venant du controleur
* Contournement problème Unifi sur cloudkey (erreur 403) on va chercher la liste des noms des périphériques la nuit sans bloquer (il y aura quand meme une erreur dans le log mais elle n'est plus bloquante)
* Utilise NodeJS 16

# 11-02-2022

* Messages d'erreurs plus explicites.
* Traductions anglaises
* Dernières images venant du controleur en 7.0.21
* Ajout Up Down sur les clients (pour voir si communique toujours)
* Ajout Powersave sur les clients

# 29-10-2021

* Fix pour les commandes UDM

# 15-10-2021

* Fix pour ne pas autoriser les reconnect sur un client bloqué (comme sur l'interface unifi)
* Fix pour ne pas autoriser les reconnect sur un client cablé (comme sur l'interface unifi)
* Fix pour gérer les blocages des clients LAN
* Fix image pour 4.2

# 22-09-2021

* Fix pour les nouvelles alertes dans le controleur 6.4.54 : gestion présence

# 21-09-2021

* Fix si un équipement est déjà existant dans la meme pièce que le client et désactivé

# 20-08-2021

* Quitte le démon en cas d'erreur lors du startListening (si le controleur n'est pas dispo). Le mécanisme de jeedom le relancera dans les 5 min.

# 18-08-2021

* Compatibilité Debian 11 (utilisation de node à la place de nodejs)

# 05-08-2021

* Changement du port du démon qui est déjà pris par le plugin siapro
* Fix Désactivation WLAN

# 24-07-2021

* Gestion des présences pour les clients cablés
* Ajout commandes température et stockage pour les UDM si elles existent

# 20-07-2021

* Fix problème de mot de passe contenant $ suivit d'un chiffre
* Fix commande controllerHasUpdate sur le site

# 17-07-2021

* Fix de message d'erreurs []- (debug)
* Fix de notices php

# 15-07-2021

* Retrait du démon PHP qui mangeait trop de ressources.
* Nouveau démon NodeJS en temps réel (websocket) avec le controleur. (Nécessite de ne pas avoir été désactivé dans l'interface Unifi (activé par défaut))
* Nécessite Debian Stretch et plus récent, plus compatible avec Debian Jessie, Jeedom Mini+, Raspberry Pi 1 & 2, Raspberry Zéro (armv6) et i386 32bit.
* Bouton de réinstallation de NodeJS en cas de problème.
* Wlan et Site sont mis à jour régulièrement car ils ne font malheureusement pas partie des messages en temps réel que le controleur envoi (60sec par def).
* Nouvelle installation des dépendances (pour NodeJS + plus claire).
* Présence en temps réel (comme les alertes dans le controleur !) beaucoup plus responsive !!!
* Possibilité d'ignorer les mises à jour de la Satisfaction, Last_seen et Uptime sur les clients wifi (pour avoir moins de messages/mises à jour/charge).
* Plus d'informations et d'aides lors de la configuration du plugin (cherchez les (?) et les tooltips quand vous survollez certains éléments).
* Petites corrections à gauche et à droite.
* En cas de déconnexion du controleur (mise à jour ou problème), le démon s'arrette, on se base sur le mecanisme de jeedom pour le relancer (5min après par défaut).
* Création des commandes des clients + site + point d'access + passerelles (ugw et udm) en temps réel, il n'y a plus que les switchs qui sont en décallés 90sec (car grand nombre de commandes).
* Mises à jour d'icones pour FontAwesome.
* Affichage des valeurs en temps réel directement dans la liste des commandes. (si l'équipement est activé !)
* Page Santé complètement revue et complêtée.
* Description Market plus précise et complète.
* Nom des équipements non modifiable dans jeedom (car mis à jour par le controleur), il faut donc renommer dans l'interface controleur pour le changer.

Modifications coté Dev :
* Mécanisme de vérification du code source automatique dans github (erreurs, optimisations)
* Refactoring complet
* Réécriture d'une grosse partie du code + optimisations

# 14-04-2021

* Si le controleur ne réponds pas (par exemple pendant une sauvegarde) le message n'est plus une erreur mais juste un warning
* Correction d'un warning si un equipement a été supprimé et que le démon n'a pas été relancé pour en prendre compte
* Correction si certaines commandes n'existent pas
* Correction ne pas mettre à jour un client si pas d'adresse mac

# 13-02-2021

* Mise à jour de la lib Unifi.
* Nom du modèle (court et long) téléchargé du controleur afin d'avoir toujours la liste la plus à jour.
* Controleur en tant que variable de class pour limiter les reconnexion
* Retiré toHtml pour réactiver les onglets "Affichage" et "Disposition" dans les config avancées.
* Création des commandes en différé dans un cron +90s afin d'éviter les bugs de mémoire php
* Les switchs non POE n'auront plus les commandes poe sur les ports ne le supportant pas
* Résolution des problèmes de perte de cookie pour les CloudKey.

# 10-01-2021

* Correction couleur entête du widget

# 05-01-2021

* Nouvelles images pour nouveau switchs et UAP wifi6

# 23-12-2020

* Fix php notice
* Nouvelle liste des pièces compat 4.1

# 17-12-2020

* Meilleur support et affichage des DreamMachines (pour l'instant comme une USG)
* Couper/activer le POE sur un port d'un switch
* Ajout des commandes info "MAC Point Accès", "MAC Switch" et "MAC Passerelle" sur les clients.
* Ajout des commandes info "Niveau Ventil", "Temp Générale" sur les switchs qui ont des ventilateurs et des capteurs température
* Ajout de la commande info binaire "Désactivé" sur un point d'accès.
* Fix sur des doublons de nom de périphérique.
* Fix de l'uptime et de la mémoire sur les flex.
* Nouvelle commande info binaire sur le site pour indiquer s'il y a une mise à jour du controleur.
* Meilleure information sur le site dans la config.
* Mise à jour de la lib Unifi. (relancez les dépendances !)

# 04-07-2020

* Fix détection dans certains cas qui ne remontait rien
* Fix mise à jour de certains périphérique qui pouvait ne pas se faire

# 09-03-2020

* Non réécriture du schédule du cron à la mise à jour, si vous l'avez modifié, il restera.

# 19-01-2020

* contournement si deux commandes ont le même nom, renommage _1 _2 etc
* contournement du problème du controller 5.12 : lorsqu'un wifi est absent, quelques minutes après, il réapparait comme présent et étant cablé (on ignore maintenant le changement de présence s'il revient dans un autre état (était wifi -> cablé ou était cablé -> wifi)) + on ne met pas à jour le last_seen pour essayer d'avoir une valeur cohérente dans cette commande
* changement du format du last_seen pour etre utilisable avec time_diff dans un scénario

# 19-12-2019

* contournement si deux périphérique ont le même nom, renommage _mac
* correction orthographe

# 29-11-2019

* fix version_incompatible (+ autres) dans cron_execution 
* syncro selectif par type de device
* nouvelles images fournies avec le controleur (rescan nécessaire + relancer dépendances pour supprimer les anciennes)
* images différentes pour clients wifi et cablés
* commandes rxWAN et txWAN sur la gateway pour les débits en bps

# 15-10-2019

* compatibilité V4 (design)

# 09-09-2019

* version jeedom minimale : 3.3.24 (pour compatibilité V4)

# 24/07/2018

- Initialisation

