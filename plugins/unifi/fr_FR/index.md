---
layout: default
lang: fr_FR
title: Plugin Unifi
description: Documentation du plugin Unifi
---

Ce plugin permet de monitorer et exécuter quelques actions sur un **controleur** UniFi et les équipements supportés par celui-ci.


Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Il faut ensuite rentrer les informations de votre controleur dans la configuration.

-   **Controleur Unifi** : Indiquez l'adresse ip et le port (normalement 8443 ou 443 si UDM) de votre controleur Unifi
-   **Utilisateur Unifi** : Indiquez l'utilisateur du controleur (**Attention: pas celui du cloud ! Un utilisateur Local avec les droits Super Admin**)
-   **Mot de passe Unifi** : Indiquez votre mot de passe controleur
-   **Site Unifi** : si vous avez plusieurs sites, indique lequel le plugin doit gérer (default par défaut). Le nom correspond au nom dans l'url du site controleur, exemple : https://ip:8443/manage/site/**abc12345**/settings/site
-   **Bouton Rechercher les équipements Unifi** : Permet de scanner les équipements sur le controleur

-   **Pièce par défaut pour les Clients** : quand vous aurez ajouté vos équipements, les clients wifi/cablés peuvent être ajoutés par défaut à une pièce.
-   **Bouton Ne plus ignorer les clients supprimés** : Permet de montrer à nouveau les clients que vous auriez supprimés et ignorés dans la liste des équipements.
-   **Fréquence de rafraîchissement** : Fréquence à laquelle les informations sont récupérées de votre controleur. (3secondes par défaut)


Configuration des équipements 
=============================

La configuration des équipements Unifi est accessible à partir du menu
plugins puis Monitoring. Vous retrouvez ici :

-   un bouton pour scanner votre controleur

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements

-   enfin en dessous vous retrouvez la liste de vos équipements par catégories
    -   A coté de chaque titre de catégories, vous pouvez lancer le scan sur ce type uniquement
    -   A coté du titre des Clients, vous pouvez cliquer sur la poubelle pour supprimer les Clients (uniquement dans jeedom) qui sont en non-actif (ou la case Actif n'est pas cochée) et les ignorer lors des prochains scans (pour ne plus les ignorer, Configuration du plugin > Bouton "Ne plus ignorer les clients supprimés"


Equipement
==========

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

-   **Onglet Equipement** :

-   **Nom de l’équipement** : nom de votre équipement

-   **Activer** : permet de rendre votre équipement actif

-   **Visible** : le rend visible sur le dashboard

-   **Objet parent** : indique l’objet parent auquel appartient
    l’équipement
-   **Informations diverses** : plusieurs informations sur l'équipement sont affichées.


-   **Onglet Commandes** :

-   Il existe de nombreuses commandes, elles sont différentes en fonction du type d'équipement. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non et les réorganiser. 
Vous pouvez aussi attribuer un widget au choix. Tout est standard.

-   **Astuce** :
-   Pour lancer un scan dans un scénario, via un bloc code, vous pouvez lancer : `unifi::syncUnifi();`
