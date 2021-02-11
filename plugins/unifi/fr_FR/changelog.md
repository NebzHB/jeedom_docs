---
layout: default
lang: fr_FR
title: Plugin Unifi - Changelog
description: Changelog du plugin Unifi
---

# Version à venir (actuellement en beta)

* Mise à jour de la lib Unifi.
* Nom du modèle (court et long) téléchargé du controleur afin d'avoir toujours la liste la plus à jour.
* Tentative controleur en tant que variable de class pour limiter les reconnexion (à voir si ca tient sur la durée)
* retiré toHtml pour réactiver les onglets "Affichage" et "Disposition" dans les config avancées.
* Création des commandes en différé dans un cron +90s afin d'éviter les bugs de mémoire php
* les switchs non POE n'auront plus les commandes poe sur les ports ne le supportant pas

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

