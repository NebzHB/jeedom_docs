---
layout: default
lang: fr_FR
title: Plugin hkControl
description: Documentation du plugin hkControl
---

...**En cours de Rédaction**...

Présentation hkControl
=======================

Ce plugin permet de connecter les périphériques Homekit réseaux à Jeedom et de les contrôler dans Jeedom.

![Schema](https://market.jeedom.com/filestore/market/plugin/images/hkControl_screenshot1.png)

>**Si vous cherchez à envoyer les périphériques Jeedom dans Homekit, ce n’est pas le bon plugin, dans ce cas, il faut utiliser #plugin-homebridge !!**

>**Important** : les périphériques Homekit Bluetooth et ceux qui nécessitent NFC pour être appariés, ne sont pas compatibles. D'autres ne sont également pas compatibles pour différentes raisons (voir Compatibilités).

>Pour certains d'entre eux, il est toujours nécessaire de posséder un iPhone, mais pas pour tous ! (voir tableau)

>Le but du plugin est de rendre compatible avec Jeedom les périphériques qui sont SEULEMENT Homekit, donc qui n’ont pas d’autres moyens d’être contrôlés (via un autre plug-in) dans Jeedom. Donc Pont Philips Hue,Gateway Ikea, ça sera du bonus si ça fonctionne mais ce n’est clairement pas le but !

Il y a trois types d'équipements dans Homekit, les Accessoires, les Ponts et les Accessoires Pontés.
- Les Accessoires sont des équipements uniques et communiquent directement avec le plugin
- Les Ponts sont des équipements qui contiennent un ou plusieurs Accessoires Pontés et communiquent avec le plugin
- Les Accessoires Pontés sont liés à un Pont et communiquent avec le plugin via celui-ci

Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Si vous voullez aller plus vite, vous pouvez lancer les dépendances ou attendre ~5min.
Une fois les dépendances terminées, le démon démarrera dans les 5min également (ou vous pouvez le lancer à la main).

Le démon va détecter les périphériques Homekit sur votre réseau automatiquement lors de son démarrage (multicast utilisé, routage non supporté !). Ensuite il continuera d'écouter les messages de vos équipements, ceux-ci doivent envoyer quand ils se connectent.  Pour forcer un Bonjour sur le réseau, relancez le démon (normalement pas nécessaire).


Configuration des équipements 
=============================

La configuration des équipements est accessible à partir du menu
*Plugins* puis *Protocole domotique*. Vous retrouvez ici :

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements

-   enfin en dessous vous retrouvez la liste de vos équipements

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

**Onglet Equipement**
---------------------

-   **Nom de l’équipement** : Nom de votre équipement

-   **Objet parent** : Indique l’objet parent auquel appartient l’équipement

-   **Activer** : Permet de rendre votre équipement actif

-   **Visible** : Le rend visible sur le dashboard

-   **Catégrorie** : Indique la catégorie à laquelle appartient l’équipement

-   **Adresse IP** : L'ip de l'équipement et le port (à titre informatif, en lecture seule)

Pour les Accessoires ou les Ponts :
-   **Pin** : Le code pin Homekit que vous trouverez sur votre équipment ou sa boite.
-   Bouton **Appairer**/**Désappairer** : permet de lier/délier jeedom avec votre équipement (un seul lien possible par équipement).

-   **Rafraîchir les équipements liés** (dans le cas d'un Pont) : permet de vérifier si de nouveaux accessoires ont été ajoutés ou retirés au pont. En cas d'ajout, ils seront ajoutés à la liste. En cas de suppression, ils apparaîtrons barrés et vous pourrez les supprimer manuellement si vous ne comptez pas les ré-ajouter plus tard.


**Onglet Commandes**
--------------------

Il existe de nombreuses commandes, elles sont différentes en fonction du type d'équipement. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non et les réorganiser. Vous pouvez aussi attribuer un widget au choix. Tout est standard.

Les noms viennent directement de Homekit.  Les valeurs possibles de la commande sont également affichées si ce sont des valeurs connues.

La valeur est affichée en temps réel et est modifiée en temps réel.


**Appairage**
=============

EXPLIQUER APPAIRAGE ET CODE PIN

Pour appairer votre équipement avec le plugin, il vous faut trouver le code PIN de celui-ci. Il se trouvera sur la boîte de l'équipement ou sur l'équipement lui-même (sur le Pont)

Une fois appairé avec ce plugin, les périphériques ne sont plus appairables avec « Maison ». Il faut donc (pour l’instant) les réinjecter dans homebridge manuellement avec des types génériques. 

>Plus tard ou jamais (pas de date prévue), ils seront automatiquement réinjectés dans homebridge sans configuration (pour l’instant il faut passer par les types génériques et parfois des virtuels…). Cette seconde étape est en développement mais demande enormément de boulot donc ca ne sera pas prêt tout de suite ! Soyez patient !


**Compatibilités**
==================

**En attente de tests**
----------------------

-    Tous les accessoires Philips Hue
-    Tous les accessoires IKEA
-    Autres accessoires Eve Home
-    Autres * with Netatmo

**Compatibles**
---------------

| Equipement | Site | Nécessite iBidule? | Remarques |
|:---------- |:----:|:------------------:|:----------|
| Legrand iDiamant with Netatmo | [Voir Site Officiel](https://www.netatmo.com/fr-fr/partners/bubendorff){:target="_blank" rel="noopener"} | NON | |
| Legrand Céliane with Netatmo | [Voir Site Officiel](https://www.netatmo.com/fr-fr/partners/legrand){:target="_blank" rel="noopener"} | NON | |
| Velux Active with Netatmo | [Voir Site Officiel](https://www.netatmo.com/fr-fr/partners/velux){:target="_blank" rel="noopener"} | NON | capteurs temperature/humidité/CO2 + Ouverture Velux + Volets extérieurs |
| Passerelle Xiaomi ZHWG11LM | [Voir Site Officiel](https://www.aqara.com/us/smart_home_hub.html){:target="_blank" rel="noopener"} | Peut-être? | |
| Passerelle Xiaomi ZNDMWG03LM | | Peut-être? | Tout firmware |
| Passerelle Xiaomi HM2-G01 | [Voir Site Officiel](https://www.aqara.com/eu/smart_hub_m2.html){:target="_blank" rel="noopener"} | Peut-être? | |
| Passerelle Xiaomi M1S ZHWG15LM | [Voir Site Officiel](https://www.aqara.com/en/smart_hub_m1s.html){:target="_blank" rel="noopener"} | Peut-être? | |
| Prises Koogeek | [Voir Site Officiel](https://www.koogeek.com/p-p1eu-1.html){:target="_blank" rel="noopener"} | OUI | Doit être ajouté à Maison puis retiré |
| Light strip Koogeek | [Voir Site Officiel](https://www.koogeek.com/p-ls1-1.html){:target="_blank" rel="noopener"} | OUI | Doit être ajouté à Maison puis retiré |
| Nice IT4WIFI | [Voir Site Officiel](https://www.niceforyou.com/fr/it4wifi){:target="_blank" rel="noopener"} | OUI | |
| VOCOlinc FlowerBud Smart Diffuser | [Voir Site Officiel](https://www.vocolinc.com/products/flowerbud-smart-diffuser){:target="_blank" rel="noopener"} | OUI | Doit être ajouté à Maison puis retiré |
| Eve Extend | [Voir Site Officiel](https://www.evehome.com/fr/eve-extend){:target="_blank" rel="noopener"} | OUI | Rend compatible tous [ces périphériques](https://www.evehome.com/fr/extend-compatibility){:target="_blank" rel="noopener"} Eve Bluetooth (max 8 par Extend)<br/>(Energy, Aqua, Weather, Motion, Button testés OK)<br/>Nécessite de désappairer, repasser dans l'app Eve Homekit et réappairer à chaque ajout d'équipement<br/>(Mais sans perte de configuration) |
| Passerelle IKEA TRADFRI | [Voir Site Officiel](https://www.ikea.com/fr/fr/p/tradfri-passerelle-blanc-40337806/){:target="_blank" rel="noopener"} | NON | (sauf télécommandes, non remontées dans homekit) |
| Pont Philips Hue | [Voir Site Officiel](https://www.philips-hue.com/fr-fr/p/hue-hue-bridge/8718696511800){:target="_blank" rel="noopener"} | NON | (Ampoules, Interrupteur Tap OK) (Ampoules non-hue non remontées dans homekit) |
| ESP8266 | [Avec lib Arduino-Homekit-ESP8266](https://github.com/Mixiaoxiao/Arduino-HomeKit-ESP8266){:target="_blank" rel="noopener"} | NON | Elle intègre des exemples de led, sensor, switch et tout type d’accessoire.<br/>(modifier le pin par défaut qui est 111-11-111 et pas accepté par Apple) |

**Non-Compatibles**
----------------------------

-    prises Meross MSS210HK (pas de réponse à l’appairage)
-    Shelly Firmwares alternatifs homekit (M4: Empty TLV)

**Ne seront jamais compatibles**
-------------------------------

-    Ampoules Yeelight homekit (sans code pin, code pin généré par l’app mais non affiché)
-    Flux Caméras
-    Flux vidéo des Sonnettes vidéo


**Utilisation**
===============

Pour certains périphériques, vous devez configurer votre périphérique Homekit comme habituellement avec l’app du constructeur (afin de le connecter au wifi) ou Maison et ensuite le supprimer proprement (le désappairer) de Maison. Il sera ensuite possible de le découvrir via ce plugin. D’autres périphériques n’ont pas besoin d’un iDevice et de Maison pour être compatibles (Céliane with Netatmo, iDiamant with Netatmo, …).

Certains périphériques possèdent un appairage propriétaire (uniquement via l’app propriétaire et pas via maison), ceux-là ne seront pas compatibles (Yeelight par ex).

Certains périphériques on un écran et y affichent le code pin une fois la procédure d’appairage commencée (Thermostat Netatmo), il faut donc lancer l’appairage sans code pin dans le plugin (bouton appairage habituel, mais sans avoir rentré le code pin) puis le code va s’afficher sur l’écran, le copier dans le plugin et cliquer sur le bouton « post-Appairage » pour terminer l’appairage.

Si le plugin dit que votre périphérique est déjà appairé (on le voit dans le log hkControl après découverte), il faut effectuer un reset Homekit sur votre périphérique, suivez les instruction du constructeur pour l’effectuer.


**Comment aider ?**
===================

Si vous testez le plugin avec l’un de vos périphérique encore non listé dans la compatibilité et que ça fonctionne (même si ca ne fonctionne pas, c’est intéressant de le savoir), envoyez-moi (en privé, c’est mieux) la ligne complète « getAccessories » qui se trouve dans le log « hkControl » après l’appairage ou après une relance du démon.


**FAQ**
=======

à venir
