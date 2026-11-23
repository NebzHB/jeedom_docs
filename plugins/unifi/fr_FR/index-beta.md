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
> Attention, beaucoup se trompent ici, il faut bien indiquer *default* et pas l'url du controleur !!!!

-   **Bouton Rechercher les équipements Unifi** : Permet de scanner les équipements sur le controleur

-   **Pièce par défaut pour les Clients** : Lors du scan, les nouveaux clients wifi/cablés peuvent être ajoutés par défaut à une pièce.
-   **Bouton Gérer les clients ignorés** (En Beta, visible s'il y a des clients ignorés) : ouvre la liste des clients que vous avez supprimés avec la poubelle et qui sont donc ignorés aux scans. Pour chacun : son adresse MAC, et ce que le contrôleur en connaît encore (clients vus sur la dernière année) : nom, dernière IP, IP fixe, date de dernière connexion ; « Inconnu » sinon. Vous pouvez ne plus ignorer un client, une sélection (cases à cocher) ou tous les clients ; ils seront ajoutés au prochain scan s'ils sont connectés.
-   **Relevé Site et WLAN (secondes)** : Fréquence en secondes à laquelle le relevé des informations du Site et des WLANs doivent être fait.  Les autres mises à jour sont envoyées par le controleur en temps réel, malheureusement pas les informations du site et des wlans. Le plugin doit donc les consulter régulièrement.  Si les informations sont modifiées via le plugin (LED's ou désactiver un WLAN), elles sont mises à jour instantanément, mais si vous modifiez ces informations via l'interface UniFi ou un autre moyen, c'est ici que cette consultation régulière rentre en jeu. (60 secondes par défaut). À chaque relevé, le plugin vérifie aussi la liste des clients connectés au contrôleur pour corriger la présence des Clients activés si un évènement de connexion ou de déconnexion a été perdu (une présence qui vient de changer, moins de 2 minutes, n'est pas touchée).  Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)
-   **Limiter Messages Périphériques (secondes)** : Dans les dernières versions du controleur, les messages des périphériques arrivent beaucoup plus fréquemment.  Si c'est trop fréquemment pour vous (pas besoin, système ralenti, etc), vous pouvez limiter à un message par périphérique toutes les X secondes. Uniquement les messages concernant les périphériques seront affectés.

-   **Ignorer les évênements Last_Seen sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour l'information Last_Seen (vu dernièrement). En ignorant cette information (si elle n'est pas importante pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom. Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)

-   **Ignorer les évênements Satisfaction sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour l'information Satisfaction. En ignorant cette information (si elle n'est pas importante pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom. Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)

-   **Ignorer les évênements Uptime sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour l'information Uptime. En ignorant cette information (si elle n'est pas importante pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom. Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)

-   **Ignorer les évênements Up et Down sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour les informations UP et DOWN. En ignorant cette information (si elle n'est pas importante pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom. Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)

-   **Ignorer les évênements Signal sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour l'information Signal. En ignorant cette information (si elle n'est pas importante pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom. Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)

-   **Ignorer les évênements Powersave_Enabled sur les Clients** : le controleur envoi régulièrement des mises à jour des clients, surtout pour l'information Powersave_Enabled. En ignorant cette information (si elle n'est pas importante pour vous), vous allégez les mises à jour des équipements clients activés, et donc vous allégez la charge de votre Jeedom. Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)

-   **Afficher les évènements bruts du controleur dans un log séparé** (En Beta) : Permet d'envoyer tous les évènements reçus du controleur dans le log unifi_event (excepté les évènements Clients et Devices, il deviendrait illisible !). Cela vous permet de voir les évènements reçus (et connaitre leurs champs) pour les ajouter dans les Automatisation Evènements sur l'équipement Site. Pas besoin de relancer le démon après ce changement, il est directement pris en compte :)

-   **Bouton Réparation de NodeJS** : Ce bouton permet de réparer NodeJS sur votre système (désinstallation complête et réinstallation propre). Il n'est conseillé de le faire que sur conseil via le forum ou en dernier recours.

Configuration des équipements 
=============================

La configuration des équipements Unifi est accessible à partir du menu
plugins puis Monitoring. Vous retrouvez ici :

-   un bouton pour scanner votre controleur

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements et leur état (Santé). Pour un Client (En Beta), l'IP est en vert avec une punaise si elle est réservée dans UniFi, en orange si l'IP réservée n'est pas la dernière vue.

-   enfin en dessous vous retrouvez la liste de vos équipements par catégories
    -   A coté de chaque titre de catégories, vous pouvez lancer le scan sur ce type uniquement
    -   A coté du titre des Clients, vous pouvez cliquer sur la poubelle pour supprimer les Clients (uniquement dans jeedom) qui sont en non-actif (où la case Actif n'est pas cochée) et les ignorer lors des prochains scans (pour ne plus les ignorer, Configuration du plugin > Bouton "Gérer les clients ignorés")

> **Image des clients (En Beta)** : lors d'un scan (et de celui fait automatiquement chaque nuit), chaque client prend l'icône qu'il a dans le contrôleur : l'image personnalisée que vous avez envoyée dans UniFi, sinon l'icône que vous y avez choisie, sinon celle détectée par UniFi. Elle est téléchargée chez UniFi, il faut donc un accès internet ; sinon le client garde l'image générique filaire ou Wi-Fi. Si vous changez l'icône d'un client dans UniFi, relancez un scan des Clients pour la voir dans Jeedom. Les images qui ne servent plus (image remplacée, client supprimé) sont effacées à ce même scan.


Equipement
==========

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

Onglet Equipement
-----------------

-   **Nom de l’équipement** : nom de votre équipement. Il est repris du contrôleur à chaque scan (et chaque nuit) : renommez-le dans UniFi. Exception (En Beta) : le nom du **Site** n'est repris qu'à sa création, vous pouvez ensuite le renommer ici, un scan ne l'écrasera plus (un site seul ne se renomme pas dans UniFi).

-   **Objet parent** : indique l’objet parent auquel appartient
    l’équipement

-   **Activer** : permet de rendre votre équipement actif

-   **Visible** : le rend visible sur le dashboard

-   **Catégorie** : catégorie (couleur) de l'équipement sur le dashboard

-   **Commentaire** : permet d'écrire un commentaire sur l'équipement.

-   **Informations diverses** : plusieurs informations sur l'équipement sont affichées. Pour un Client (En Beta) : son **IP fixe** si une adresse lui est réservée dans UniFi (« Non » sinon), reprise à chaque scan.


Onglet Commandes
----------------

-   Il existe de nombreuses commandes, elles sont différentes en fonction du type d'équipement. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non et les réorganiser. 
-   La valeur des commandes est maintenant affiché et modifié en temps réel sur cette page
Vous pouvez aussi attribuer un widget au choix. Tout est standard.

Widgets (En Beta)
=================

Chaque équipement s'affiche sur le dashboard et en mobile avec un widget du plugin, différent selon son type. Les valeurs se mettent à jour en direct, sans recharger la page.

-   **Site** : contrôleur à jour ou mise à jour disponible, nombre d'équipements UniFi en ligne et de clients présents (parmi ceux créés dans Jeedom), bouton **LED** du site et **Rescan Clients**.

-   **Client** : présent ou absent, adresse IP (avec la mention **fixe** si elle est réservée dans UniFi), réseau Wi-Fi, signal, satisfaction, canal, débits en réception et en envoi, boutons **Bloquer** et **Reconnecter**. Un client filaire n'a pas les informations Wi-Fi.

-   **WLAN** : activé ou désactivé, bande, réseau invités, et un interrupteur pour l'activer ou le désactiver.

-   **Point d'accès** : état, nombre de clients (au total et par bande radio), processeur, mémoire, boutons **LED**, **Localiser** et **Redémarrer**.

-   **Switch** : état, nombre de clients, processeur, mémoire, puissance PoE totale, température et ventilateur si le modèle les fournit, et une case par port.

-   **Passerelle** : comme le switch, avec en plus l'IP WAN, les débits, la disponibilité et la latence de la connexion internet, les températures et les stockages.

Une flèche orange dans l'entête indique qu'une mise à jour du firmware est disponible : un clic dessus lance la mise à jour.

Les ports
---------

Sur un switch ou une passerelle, chaque port est une case numérotée :

-   **verte** : un appareil est connecté
-   **grise** : le port est libre
-   **hachurée** : le port est désactivé
-   **soulignée en orange** : le port alimente un appareil en PoE
-   avec un petit **globe** : c'est le port WAN de la passerelle

Le nombre de ports connectés est rappelé au-dessus de la grille. La grille s'adapte à la largeur de la tuile, quel que soit le nombre de ports.

Un clic sur un port ouvre son détail : son nom, ses valeurs (activé, connecté, PoE, puissance PoE) et ses actions (**PoE** pour l'activer ou le couper, **PowerCycle**).

Autres valeurs
--------------

Toutes les commandes visibles restent accessibles : les plus utiles sont dans le widget, les autres dans un popup ouvert par l'icône <i class="fas fa-list-ul"></i> (liste) en bas à droite du widget, avec l'infobulle **Autres valeurs** (**Autres actions** s'il ne contient que des actions). Pour retirer une commande du widget ou du popup, rendez-la non visible dans l'onglet Commandes.

Un clic sur une valeur historisée ouvre son historique.

Confirmation
------------

Les actions qui coupent quelque chose demandent une confirmation : redémarrer, mettre à jour, couper le PoE d'un port, PowerCycle, désactiver un WLAN, bloquer un client.

Revenir à l'affichage standard de Jeedom
----------------------------------------

Si vous préférez l'ancien affichage (la liste des commandes, avec vos propres widgets de commandes), ouvrez la **configuration avancée** de l'équipement (la roue crantée en haut à droite de sa page) et décochez **Template de widget**. Le réglage se fait équipement par équipement.

Après la mise à jour
--------------------

La taille des tuiles que vous aviez réglée pour l'ancien affichage est conservée. Si une tuile est trop grande ou trop petite pour le nouveau widget, redimensionnez-la une fois en mode édition du dashboard.

Automatisations Évènements (En Beta)
====================================
Il s'agit d'une nouvelle fonctionnalité qui vous permet de traiter vous-même les évènements bruts reçus du controleur.
Il faut vous rendre dans l'équipement Site, onglet *Automatisations Évènements*.

![image](https://github.com/NebzHB/jeedom_docs/assets/28622481/c931ddc4-80cb-4670-8029-7c96d210fa9f)

![image](https://github.com/NebzHB/jeedom_docs/assets/28622481/b564667f-4d3c-415b-8116-b3f67d56fa6e)

Grâce au log *unifi_event* activable dans la configuration du plugin (voir plus haut), vous pouvez voir par exemple cet évènement :
```
evt_wg_connected :
{
    "guest": "ab:cd:ef:ab:cd:ef",
    "ssid": "Guest",
    "ap": "bb:cc:dd:ee:ff:aa",
    "radio": "ng",
    "channel": "11",
    "ap_model": "U7PG2",
    "ap_name": "APRez",
    "ap_displayName": "APRez",
    "key": "EVT_WG_Connected",
    "subsystem": "wlan",
    "is_negative": false,
    "site_id": "153457853a5b2542257785c2",
    "time": "1704652201104",
    "datetime": "2023-01-15T13:15:04Z",
    "msg": "Guest[ab:cd:ef:ab:cd:ef] has connected to AP[bb:cc:dd:ee:ff:aa] with SSID \"Guest\" on \"channel 11(ng)\"",
    "_id": "554c142be4b7bd788697c2a5"
}
```
C'est un évènement *w = wifi*, *g = guest* qui se connecte à votre réseau. 
> TIPS : Première lettre est la source : *l = lan* ou *w = wifi* / seconde lettre est le type : *g = guest*, *u = user* ou *c = client*.
Vous pouvez aussi y trouver *ad = interface admin*, *hs = hotspot*, *gw = gateway*, *sw = switch* et *ap = access point*. (il y en a peut-être d'autres ?)

Le plugin vous permet d'utiliser chaque champ de premier niveau comme un tag dans une commande ou à envoyer à un scénario. Ici donc vous pourriez utiliser *#guest#* pour l'adresse mac de l'invité, *#ap_name#* pour le nom du point d'accès où il se connecte ou encore *#time#* pour recevoir le datetime unix de la connexion (et tous les autres champs ! Attention cependant à msg qui contient des guillemets qui peuvent être mal interpretées parfois...). Le plugin vous permet également d'envoyer tout l'évènement en json avec le tag *#event#*. 
> **Ce tag *#event#* est aussi utile pour les évènements de type Device ou Client, car ils ont plusieurs niveaux dans le json, il est donc impossible de faire des tags qui dépassent le premier niveau pour ces évènements !**.

> Les évènements "Device" ou "Client" ne font pas partie du log *unifi_event* car il y en a beaucoup et souvent et ça le rendrait illisible, vous pouvez les voir si vous passez le log en debug dans le log *unifi_deamon* après le démarrage du démon.

> **Les évènements "Client : Mise à jour" font augmenter la charge de jeedom, car à partir du moment où vous l'ajoutez, le démon va envoyer tous les changements client à jeedom (donc dès qu'une vitesse change ou un last_seen !!). Et ce, même si vous avez décoché ces commandes dans la configuration du plugin!!! Préfèrez-lui l'évènement "Client Activé dans Jeedom : Mise à jour (sync.generic)" qui n'enverra que les évènements des clients activés dans Jeedom et prendra en compte les commandes ignorées de la configuration du plugin.**

Exemple
-------

![image](https://github.com/NebzHB/jeedom_docs/assets/28622481/2908ff03-a8a0-4cd4-86bf-3f149786db0c)

![image](https://github.com/NebzHB/jeedom_docs/assets/28622481/1ed8ad3c-90b8-4af9-8df1-a3bc9a9fb649)

![image](https://github.com/NebzHB/jeedom_docs/assets/28622481/8ede1182-8abf-4eb5-af4a-adafd3505ce2)

> Pour les champs plus complexes, vous pouvez passer par une variable qui supporte beaucoup mieux le contenu JSON et les guillemets

![image](https://github.com/user-attachments/assets/6f9ad369-7d1c-434c-8431-fde52d9f1f65)

![image](https://github.com/user-attachments/assets/4b2ff860-6ca4-4b45-a167-29475085482e)

![image](https://github.com/user-attachments/assets/927051a7-195a-45dc-a7e6-be458b3802a8)

> Exemple pour gérer les Vouchers, Dans le site, vous avez une commande "Créer un Voucher"

![image](https://github.com/user-attachments/assets/1f42478d-d9af-4f9e-b3a1-f6a063e409fe)

![image](https://github.com/user-attachments/assets/72c8397d-a479-44c2-878d-4ce21e26b75f)

Vous pouvez ensuite récupérer l'évènement via l'automatisations des évènements sur le même site :

![image](https://github.com/user-attachments/assets/3c748ab3-9123-4e24-8f84-509433e99270)

Voici un exemple d'event que vous recevez suite à cette commande : 

```
DEBUG  : Génération nouvel Event "custom.voucher_created_from_jeedom" : 
{
    "duration": 1440,
    "qos_overwrite": false,
    "name": "24hVoucher",
    "code": "38523-67242",
    "for_hotspot": false,
    "create_time": 1739698999,
    "quota": 2048,
    "multi": "no",
    "site_id": "abcdefghijklmnopqrstuvwxyz",
    "_id": "2245cfc04f4f2735491aa6b2",
    "admin_name": "jeedom",
    "used": 0,
    "status": "VALID_ONE",
    "status_expires": 0,
    "jeedomUser": "Nebz"
}
```



Astuces & FAQ
=============
-   Pour lancer un scan dans un scénario, via un bloc code, vous pouvez lancer : `unifi::syncUnifi();`

-   **Le démon s'arrête tout seul ?** Regardez le log *unifi_deamon* :
    -   « Identifiants refusés par le contrôleur » : l'utilisateur ou le mot de passe de la configuration du plugin est refusé par le contrôleur (mot de passe changé, compte bloqué, utilisateur non local…). Le démon s'arrête immédiatement pour ne pas faire bloquer le compte.
    -   « Contrôleur injoignable depuis 5 min » : le contrôleur ne répondait plus (éteint, en redémarrage, mauvaise IP ou mauvais port). Le démon réessaie pendant 5 minutes, au démarrage comme en cours de fonctionnement, avant de s'arrêter ; Jeedom le relance ensuite.

-   Pour la gestion des présences, assurez vous d'avoir coché ceci dans le contrôleur :

![image](https://user-images.githubusercontent.com/28622481/134291583-68965409-aa72-4086-9843-495b4e932c30.png)

![image](https://user-images.githubusercontent.com/28622481/154662386-d4d016c6-470f-4221-846d-12f7d70ee768.png)

-   Evidemment le websocket doit aussi être activé :

![image](https://user-images.githubusercontent.com/28622481/134291867-30121590-035f-454a-a42f-421e8f57b9b3.png)

-   Vérifiez que ceci est bien en Always (mieux) ou en Automatique (Mais du coup si congestion réseau, vous n'aurez plus de mises à jour des périphériques, mieux ou moins bien, à vous de voir)

![image](https://user-images.githubusercontent.com/28622481/223777175-2f60b743-ee66-4025-a946-d15d1b1611b6.png)

![image](https://github.com/NebzHB/jeedom_docs/assets/28622481/314244ec-a39f-4a90-9c8c-a54ac7564b44)


**Eviter les noms en doublon du coté du controleur Unifi :**

Jeedom n'accepte pas deux équipements du même nom dans une même pièce. Si deux équipements du contrôleur portent le même nom, le plugin crée le second avec son adresse MAC (ou son identifiant) ajoutée à la fin du nom, par exemple `iPhone_aa:bb:cc:dd:ee:ff`. Pensez quand même à avoir des noms différents dans le contrôleur, ce sera plus lisible dans Jeedom.

Ce cas, peut être également rencontré lorsque vous avez un équipement qui peut etre connecté de plusieurs façons différentes à votre réseau.
Par exemple avec un PC portable a généralement une inerface réseau filaire (ethernet) et une autre sans-fil (wifi). Par défaut, ce dernier peut apparaitre avec le même nom dans le controleur Unifi et causer l'erreur décrite ci-dessus dans Jeedom.
Dans le controleur Unifi, ajoutez un suffixe afin de les différencier (ex: ethernet ou wifi) et relancer un scan coté Jeedom.

**La présence d'un téléphone ne fonctionne pas (toujours absent, ou un nouveau Client apparaît) ?**

Les téléphones récents utilisent par défaut une **adresse Wi-Fi privée** qui peut changer. Pour le contrôleur, chaque nouvelle adresse est un nouveau client : l'équipement Jeedom du téléphone ne le voit plus, et un autre client apparaît au scan suivant. Sur le réseau Wi-Fi de la maison, réglez le téléphone pour qu'il garde toujours la même adresse :

-   **iPhone / iPad** : Réglages > Wi-Fi > (i) à côté du réseau > **Adresse Wi-Fi privée** sur **Fixe** ou **Désactivée** (pas **Rotation**).
-   **Android** : Paramètres > Wi-Fi > réseau > Confidentialité (ou Paramètres avancés) > **Utiliser l'adresse MAC de l'appareil** (le nom exact dépend du fabricant).

Après ce changement, le téléphone peut apparaître comme un nouveau client : relancez un scan des Clients et utilisez ce nouvel équipement (supprimez l'ancien si besoin).

