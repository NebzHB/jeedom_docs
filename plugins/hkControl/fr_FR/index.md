---
layout: default
lang: fr_FR
title: Plugin hkControl
description: Documentation du plugin hkControl
---

>**Si vous cherchez à envoyer les périphériques Jeedom dans Homekit, ce n’est pas le bon plugin, dans ce cas, il faut utiliser [#plugin-homebridge](https://nebzhb.github.io/jeedom_docs/plugins/homebridge/fr_FR/){:target="_blank" rel="noopener"} !!**

Présentation Homekit Network Devices Control (hkControl)
========================================================

Ce plugin permet de connecter les périphériques Homekit réseaux à Jeedom et de les contrôler dans Jeedom.

![Schema](https://market.jeedom.com/filestore/market/plugin/images/hkControl_screenshot1.png)

>**Important** : les périphériques Homekit Bluetooth et ceux qui nécessitent NFC pour être appariés, ne sont pas compatibles. D'autres ne sont également pas compatibles pour différentes raisons (voir Compatibilités).

>**Important** : le protocole Homekit n'est pas un protocole routable, jeedom et votre équipement DOIVENT donc se retrouver sur le même réseau non routé !!!

>Pour certains d'entre eux, il est toujours nécessaire de posséder un iPhone, mais pas pour tous ! (voir tableau)

>Le but du plugin est de rendre compatible avec Jeedom les périphériques qui sont SEULEMENT Homekit, donc qui n’ont pas d’autres moyens d’être contrôlés (via un autre plug-in) dans Jeedom. Donc Pont Philips Hue,Gateway Ikea, ça sera du bonus si ça fonctionne mais ce n’est clairement pas le but !

Il y a trois types d'équipements dans Homekit, les **Accessoires**, les **Ponts** et les **Accessoires Pontés**.
- Les **Accessoires** sont des équipements uniques et communiquent directement avec le plugin
- Les **Ponts** sont des équipements qui contiennent un ou plusieurs **Accessoires Pontés** et communiquent avec le plugin
- Les **Accessoires Pontés** sont liés à un **Pont** et communiquent avec le plugin via celui-ci

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


Pour les Accessoires ou les Ponts :

-   **Adresse IP** : L'ip de l'équipement et le port (à titre informatif, en lecture seule)
-   **Pin** : Le code pin Homekit que vous trouverez sur votre équipment ou sa boite.
-   Bouton **Appairer**/**Désappairer** : permet de lier/délier jeedom avec votre équipement (un seul lien possible par équipement).
-   Bouton **Rafraîchir les équipements liés** (dans le cas d'un Pont) : permet de vérifier si de nouveaux accessoires ont été ajoutés ou retirés au pont. En cas d'ajout, ils seront ajoutés aux équipements. En cas de suppression, ils apparaîtrons barrés et vous pourrez les supprimer manuellement si vous ne comptez pas les ré-ajouter plus tard.


**Onglet Commandes**
--------------------

Il existe de nombreuses commandes, elles sont différentes en fonction du type d'équipement. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non et les réorganiser. Vous pouvez aussi attribuer un widget au choix. Tout est standard.

Les noms viennent directement de Homekit.  Les valeurs possibles de la commande sont également affichées si ce sont des valeurs connues.

La valeur est affichée en temps réel et est modifiée en temps réel.


**Appairage**
=============

Pour appairer votre équipement avec le plugin, il vous faut trouver le code PIN de celui-ci. Il se trouvera sur la boîte de l'équipement ou sur l'équipement lui-même (sur le Pont)

Une fois appairé avec ce plugin, les périphériques ne sont plus appairables avec « Maison ». Il faut donc (pour l’instant) les réinjecter dans homebridge manuellement avec des types génériques. 

>Plus tard ou jamais (pas de date prévue), ils seront automatiquement réinjectés dans homebridge sans configuration (pour l’instant il faut passer par les types génériques, parfois des virtuels et parfois vous ne trouverez pas de type générique…). Cette seconde étape est en développement mais demande enormément de boulot donc ca ne sera pas prêt tout de suite ! Soyez patient !

Pour certains périphériques, vous devez configurer votre périphérique Homekit comme habituellement avec l’app du constructeur (afin de le connecter au wifi) ou Maison et ensuite le supprimer proprement (le désappairer) de Maison. Il sera ensuite possible de le découvrir via ce plugin. D’autres périphériques n’ont pas besoin d’un iDevice et de Maison pour être compatibles (Céliane with Netatmo, iDiamant with Netatmo, …).

Certains périphériques possèdent un appairage propriétaire (uniquement via l’app propriétaire et pas via maison), ceux-là ne seront pas compatibles (Yeelight par ex).

Certains périphériques on un écran et y affichent le code pin une fois la procédure d’appairage commencée (Thermostat Netatmo), il faut donc lancer l’appairage sans code pin dans le plugin (bouton appairage habituel, mais sans avoir rentré le code pin) puis le code va s’afficher sur l’écran, le copier dans le plugin et cliquer sur le bouton « post-Appairage » pour terminer l’appairage.

Si le plugin dit que votre périphérique est déjà appairé (on le voit aussi dans le log hkControl après découverte), il faut effectuer un reset Homekit sur votre périphérique, suivez les instruction du constructeur pour l’effectuer.

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

| Equipement | Site | Nécessite<br/>iPhone/iPad? | Remarques |
|:---------- |:----:|:------------------:|:----------|
| Legrand iDiamant with Netatmo | [Voir Site Officiel](https://www.netatmo.com/fr-fr/partners/bubendorff){:target="_blank" rel="noopener"} | NON | |
| Legrand Céliane with Netatmo | [Voir Site Officiel](https://www.netatmo.com/fr-fr/partners/legrand){:target="_blank" rel="noopener"} | NON | |
| Velux Active with Netatmo | [Voir Site Officiel](https://www.netatmo.com/fr-fr/partners/velux){:target="_blank" rel="noopener"} | NON | Capteurs temperature/humidité/CO2 + Ouverture Velux + Volets extérieurs |
| Legrand Drivia with Netatmo | [Voir Site Officiel](https://www.netatmo.com/fr-fr/partners/drivia){:target="_blank" rel="noopener"} | NON | |
| Velux App Control (KIG 300) | [Voir Site Officiel](https://www.veluxshop.fr/tous-les-produits/maison-connectee/velux-app-control){:target="_blank" rel="noopener"} | NON | |
| Passerelle Xiaomi ZHWG11LM | [Voir Site Officiel](https://www.aqara.com/us/smart_home_hub.html){:target="_blank" rel="noopener"} | Peut-être<sup>3</sup> | |
| Passerelle Xiaomi ZNDMWG03LM | | Peut-être<sup>3</sup> | Tout firmware |
| Passerelle Xiaomi HM2-G01 | [Voir Site Officiel](https://www.aqara.com/eu/smart_hub_m2.html){:target="_blank" rel="noopener"} | Peut-être<sup>3</sup> | |
| Passerelle Xiaomi M1S ZHWG15LM | [Voir Site Officiel](https://www.aqara.com/en/smart_hub_m1s.html){:target="_blank" rel="noopener"} | Peut-être<sup>3</sup> | |
| Prises Koogeek | [Voir Site Officiel](https://www.koogeek.com/p-p1eu-1.html){:target="_blank" rel="noopener"} | OUI<sup>1</sup> | Doit être ajouté à Maison puis retiré |
| Light strip Koogeek | [Voir Site Officiel](https://www.koogeek.com/p-ls1-1.html){:target="_blank" rel="noopener"} | OUI<sup>1</sup> | Doit être ajouté à Maison puis retiré |
| Nice IT4WIFI | [Voir Site Officiel](https://www.niceforyou.com/fr/it4wifi){:target="_blank" rel="noopener"} | OUI<sup>1</sup> | Doit être ajouté à Maison puis retiré |
| VOCOlinc FlowerBud Smart Diffuser | [Voir Site Officiel](https://www.vocolinc.com/products/flowerbud-smart-diffuser){:target="_blank" rel="noopener"} | OUI<sup>1</sup> | Doit être ajouté à Maison puis retiré |
| Eve Extend | [Voir Site Officiel](https://www.evehome.com/fr/eve-extend){:target="_blank" rel="noopener"} | OUI<sup>2</sup> | Pont réseau vers Bluetooth<br/>Rend compatible [tous ces périphériques](https://www.evehome.com/fr/extend-compatibility){:target="_blank" rel="noopener"} Eve Bluetooth (max 8 par Extend)<br/>(Energy, Aqua, Weather, Motion, Button testés OK)<br/><br/>Nécessite de désappairer, repasser dans l'app Eve Homekit et réappairer à chaque ajout d'équipement<br/>(Mais sans perte de configuration) |
| Passerelle IKEA TRADFRI | [Voir Site Officiel](https://www.ikea.com/fr/fr/p/tradfri-passerelle-blanc-40337806/){:target="_blank" rel="noopener"} | NON | (sauf télécommandes, non remontées dans homekit) |
| Pont Philips Hue | [Voir Site Officiel](https://www.philips-hue.com/fr-fr/p/hue-hue-bridge/8719514342620){:target="_blank" rel="noopener"} | NON | (Ampoules, Interrupteur Tap OK) (Ampoules non-hue non remontées dans homekit) |
| ESP8266 | [Avec lib Arduino-Homekit-ESP8266](https://github.com/Mixiaoxiao/Arduino-HomeKit-ESP8266){:target="_blank" rel="noopener"} | NON | Elle intègre des exemples de led, sensor, switch et tout type d’accessoire.<br/>(modifier le pin par défaut qui est 111-11-111 et pas accepté par Apple) |
| Shelly Homekit Firmware | [Voir Site Officiel](https://github.com/mongoose-os-apps/shelly-homekit){:target="_blank" rel="noopener"} | NON | |
| Meross MSS210HK | [Voir Site Officiel](https://www.meross.com/Detail/3/Smart%20Wi-Fi%20Plug){:target="_blank" rel="noopener"} | OUI<sup>1</sup> | Doit être ajouté à Maison puis retiré<br />Prise FR testée (mais les autres devraient fonctionner aussi) |

<sup>1</sup> : Nécessite un iPhone ou iPad (et l'app Maison) pour mettre l'équipement sur le réseau la première fois ou en cas de problème.<br/>
<sup>2</sup> : Nécessite un iPhone ou iPad (et l'app Eve) pour mettre l'équipement sur le réseau la première fois et à chaque ajout d'équipement au Pont.<br/>
<sup>3</sup> : Pas certain (à tester...) mais l'app Xiaomi Home sur Android devrait suffire...

**Non-Compatibles**
----------------------------

-    Tado en Homekit (à creuser, si qqun l'a je suis intéressé de me connecter à votre jeedom)

**Ne seront jamais compatibles**
-------------------------------

-    Ampoules Yeelight homekit (sans code pin, code pin généré par l’app mais non affiché)
-    Flux Caméras
-    Flux vidéo des Sonnettes vidéo

**Autres Équipements**
----------------------

>Vous avez d'autres équipements Homekit Réseau et vous vous demandez s'ils sont compatibles avec ce plugin ? C'est possible, mais tant que quelqu'un ne l'aura pas testé, je ne peux le garantir... Les qqch With Netatmo semblent tous compatibles jusqu'ici et ne nécessitent pas d'iBidules pour être configurés sur le réseau. Si vous avez un retour (positif ou négatif) sur un équipement non listé, contactez-moi sur communauté (Voir Comment Aider ?)

**Comment aider ?**
===================

Si vous testez le plugin avec l’un de vos périphérique encore non listé dans la compatibilité et que ça fonctionne (même si ca ne fonctionne pas, c’est intéressant de le savoir), envoyez-moi (en privé, c’est mieux) la ligne complète « getAccessories » qui se trouve dans le log « hkControl » après l’appairage ou après une relance du démon.


**FAQ**
=======

**-> Il me manque une commande dans mon équipement si je compare à mon app android / l'interface web / autre...**

>Toutes les commandes reçues de Homekit sont dans le plugin.  Si vous ne la voyez pas, c'est que le constructeur ne l'envoi pas dans Homekit.

**-> La commande y est bien, mais je ne sais pas comment elle fonctionne car il faut écrire du texte ou qqch d'incompréhensible**

>Certains constructeurs utilisent des fonctions propriétaires et cryptent les données dans ces champs, c'est par exemple pour gérer un calendrier ou des fonctions particulières... Le plugin ne les gère pas si le constructeur ne les a pas documentées... Vous pouvez faire la recherche et tenter de comprendre comment elles fonctionnent et m'envoyer l'info si vous l'avez ! Je me ferai un plaisir d'intégrer (si possible) dans le plugin cette fonctionnalité.

**-> Mon périphérique n'est pas listé dans les Compatibilités, est-il compatible ?**

>Je ne sais pas... le seul moyen est d'essayer :) si c'est le cas, n'hésitez pas à me tenir au courant via Communauté !!! (si ce n'est pas le cas aussi :))

**-> J'ai une passerelle Netatmo ou Xiaomi, j'ai ajouté un accessoire dessus, je le vois dans mon app android / l'interface web / autre... mais pas dans le plugin, comment faire ?**

>Utilisez le bouton "**Rafraîchir les équipements liés**" dans l'*onglet Equipement* du **Pont**

**-> Je ne parviens pas à appairer mon équipement, il me dit que celui-ci est déjà appairé**

>Comme indiqué plus haut, il faut peut-être faire une réinitialisation Homekit de votre équipement, consultez la documentation du constructeur.  Parfois une réinitialisation complète n'est pas nécessaire, parfois oui, c'est le choix du constructeur.

**-> Le plugin ne voit pas mon équipement**

>Regardez dans le log "hkControl_daemon" en debug, s'il est bien sur le réseau, ce log vous donnera la raison du non-ajout.  Si vous ne le voyez pas dans le log, relancez le démon, il va demander une ré-annonce de tous les équipements du réseau.  Regardez à nouveau dans le log "hkControl_daemon".

**-> Le plugin ne voit pas mon équipement, il n'est pas dans log "hkControl" et je ne le vois pas même après relance du démon**

>Votre périphérique n'a peut-être pas été configuré sur le réseau, utilisez l'application du constructeur ou vérifiez la documentation de celui-ci pour voir comment le mettre sur le réseau. Ensuite, si vous avez du l'intégrer à Maison sur iOS, retirez-le, il deviendra découvrable pour le plugin !

**-> Malgré tout je ne vois pas l'équipement !**

>Les **Accessoires** et **Ponts** Homekit utilisent le protocole *Bonjour* de Apple pour s'annoncer sur le réseau (et donc au Plugin). Ce protocole n'est pas routable, il faut donc que votre jeedom soit sur le même réseau (non routé) que votre équipement.  Si c'est le cas, vérifiez vos équipements réseau, il faut activer tout ce qui touche à **mDNS**, **multicast DNS**, **IGMP Snooping** sur tout le trajet réseau entre votre équipement et jeedom.

**-> J'ai un Pont qui contient plusieurs Accessoires Pontés, j'aimerais en supprimer un mais je n'ai pas de bouton "Supprimer".**

>C'est logique, car si vous le supprimez dans le plugin uniquement, il va revenir au prochain rafraichissement ! Pour le retirer, vous devez le retirer d'abord de votre **Pont** (voir documentation constructeur). Une fois que c'est effectué, cliquez sur le bouton **Rafraîchir les équipements liés** dans le **Pont** et l'**Accessoire Ponté** concerné s'affichera maintenant en barré dans la liste des Accessoires. Cliquez dessus, il sera maintenant possible de le supprimer.

**-> J'ai une commande nommée "xxx (Manual Info)" et elle ne se met pas à jour toute seule**

>C'est une commande pour laquelle le constructeur a choisi de ne pas la mettre à jour automatiquement mais uniquement si vous executez la commande "Rafraichir" (probablement pour économiser de la batterie ou pour une autre raison).

**-> Pourquoi j'ai une commande On (Info), On (Allumer) et On (Eteindre) ?**

>Car ces trois commandes sont liées à la caractéristique Homekit nommée "On" (oui... Apple aurait pu être plus original sur ce coup là ;)). Cette caractéristique Homekit renvoi un état "*On (Info)*" et il est possible de la modifier via deux actions : *On (Allumer)* et *On (Eteindre)*. J'aurais pu les renommer en Etat/Allumer/Eteindre mais cela peut porter à confusion dans certains cas (multi-prises, etc). Vous pouvez évidemment renommer les commandes comme vous le désirez afin de vous y retrouver au mieux dans votre popre logique.

**-> Comment mettre à jour mon Equipement ? (Firmware / version logicielle interne / etc)**

>Il n'y a que les constructeurs qui peuvent mettre à jour leurs propres équipements.  Vous devez donc passer par l'application de celui-ci.  Pour certains équipements (Eve, Koogeek etc), il sera peut-être nécessaire de désappairer l'équipement de Jeedom, appairer dans Maison ou l'app constructeur, mettre à jour, retirer de Maison ou l'app constructeur, et réappairer à Jeedom (pas de perte de l'équipement).
Dans tous les cas, lancez un **Rafraîchir** pour charger les éventuelles nouveautés apportées par la mise à jour.
