---
layout: default
lang: fr_FR
title: Plugin UniFi Network
description: Documentation du plugin UniFi Network
---

Ce plugin permet de monitorer et exécuter quelques actions sur un **controleur** UniFi Network et les équipements supportés par celui-ci.


Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Il faut ensuite rentrer les informations de votre controleur dans la configuration.

-   **Controleur Unifi** : Indiquez l'adresse ip et le port (normalement 8443 ou 443 si UDM) de votre controleur Unifi
-   **Utilisateur Unifi** : Indiquez l'utilisateur du controleur (**Attention: pas celui du cloud ! Un utilisateur Local avec les droits Super Admin**)
-   **Mot de passe Unifi** : Indiquez votre mot de passe controleur
-   **Site Unifi** : si vous avez plusieurs sites, indique lequel le plugin doit gérer (*default* par défaut). Le nom correspond au nom dans l'url du site controleur, exemple : https://ip:8443/manage/**default**/dashboard
-   **Bouton Rechercher les équipements Unifi** : Permet de scanner les équipements sur le controleur

-   **Pièce par défaut pour les Clients** : Lors du scan, les nouveaux clients wifi/cablés peuvent être ajoutés par défaut à une pièce.
-   **Bouton Ne plus ignorer les clients supprimés** : Permet de montrer à nouveau les clients que vous auriez supprimés et ignorés dans la liste des équipements.
-   **Relevé Site et WLAN (secondes)** : Fréquence en secondes à laquelle le relevé des informations du Site et des WLANs doivent être fait.  Les autres mises à jour sont envoyées par le controleur en temps réel, malheureusement pas les informations du site et des wlans. Le plugin doit donc les consulter régulièrement.  Si les informations sont modifiées via le plugin (LED's ou désactiver un WLAN), elles sont mises à jour instantanément, mais si vous modifiez ces informations via l'interface UniFi ou un autre moyen, c'est ici que cette consultation régulière rentre en jeu. (60 secondes par défaut)

-   **Ignorer les évênements Last_Seen sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour les informations Last_Seen (vu dernièrement), Satisfaction et Uptime. En ignorant ces informations (si elles ne sont pas important pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom.

-   **Ignorer les évênements Satisfaction sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour les informations Last_Seen (vu dernièrement), Satisfaction et Uptime. En ignorant ces informations (si elles ne sont pas important pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom.

-   **Ignorer les évênements Uptime sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour les informations Last_Seen (vu dernièrement), Satisfaction et Uptime. En ignorant ces informations (si elles ne sont pas important pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom.

-   **Bouton Réparation de NodeJS** : Ce bouton permet de réparer NodeJS sur votre système (désinstallation complête et réinstallation propre). Il n'est conseillé de le faire que sur conseil via le forum ou en dernier recours.

Configuration des équipements 
=============================

La configuration des équipements Unifi est accessible à partir du menu
plugins puis Monitoring. Vous retrouvez ici :

-   un bouton pour scanner votre controleur

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements et leur état.

-   enfin en dessous vous retrouvez la liste de vos équipements par catégories
    -   A coté de chaque titre de catégories, vous pouvez lancer le scan sur ce type uniquement
    -   A coté du titre des Clients, vous pouvez cliquer sur la poubelle pour supprimer les Clients (uniquement dans jeedom) qui sont en non-actif (où la case Actif n'est pas cochée) et les ignorer lors des prochains scans (pour ne plus les ignorer, Configuration du plugin > Bouton "Ne plus ignorer les clients supprimés")


Equipement
==========

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

Onglet Equipement
-----------------

-   **Nom de l’équipement** : nom de votre équipement

-   **Objet parent** : indique l’objet parent auquel appartient
    l’équipement

-   **Activer** : permet de rendre votre équipement actif

-   **Visible** : le rend visible sur le dashboard

-   **Catégorie** : catégorie (couleur) de l'équipement sur le dashboard

-   **Commentaire** : permet d'écrire un commentaire sur l'équipement.

-   **Informations diverses** : plusieurs informations sur l'équipement sont affichées.


Onglet Commandes
----------------

-   Il existe de nombreuses commandes, elles sont différentes en fonction du type d'équipement. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non et les réorganiser. 
-   La valeur des commandes est maintenant affiché et modifié en temps réel sur cette page
Vous pouvez aussi attribuer un widget au choix. Tout est standard.

Astuces & FAQ
------
-   Pour lancer un scan dans un scénario, via un bloc code, vous pouvez lancer : `unifi::syncUnifi();`

-   Pour la gestion des présences, assurez vous d'avoir coché ceci dans le contrôleur :

![image](https://user-images.githubusercontent.com/28622481/134291583-68965409-aa72-4086-9843-495b4e932c30.png)

![image](https://user-images.githubusercontent.com/28622481/154662386-d4d016c6-470f-4221-846d-12f7d70ee768.png)

-   Evidemment le websocket doit aussi être activé :

![image](https://user-images.githubusercontent.com/28622481/134291867-30121590-035f-454a-a42f-421e8f57b9b3.png)

-   Vérifiez que ceci est bien en Always (mieux) ou en Automatique (Mais du coup si congestion réseau, vous n'aurez plus de mises à jour des périphériques, mieux ou moins bien, à vous de voir)

![image](https://user-images.githubusercontent.com/28622481/223777175-2f60b743-ee66-4025-a946-d15d1b1611b6.png)

![image](https://github.com/NebzHB/jeedom_docs/assets/28622481/314244ec-a39f-4a90-9c8c-a54ac7564b44)


**Eviter les noms en doublon du coté du controleur Unifi :**

Pensez à avoir des noms d'équipements différents sinon vous pourriez rencontrer une erreur du type "_[MySQL] Error code : 23000 (1062). Duplicate entry '[NOM DE L EQUIPEMENT EN DOUBLE]' for key 'unique' : ..._" dans Jeedom lorsque vous faites un scan des équipements. 

Ce cas, peut être également rencontré lorsque vous avez un équipement qui peut etre connecté de plusieurs façons différentes à votre réseau.
Par exemple avec un PC portable a généralement une inerface réseau filaire (ethernet) et une autre sans-fil (wifi). Par défaut, ce dernier peut apparaitre avec le même nom dans le controleur Unifi et causer l'erreur décrite ci-dessus dans Jeedom.
Dans le controleur Unifi, ajoutez un suffixe afin de les différencier (ex: ethernet ou wifi) et relancer un scan coté Jeedom.
