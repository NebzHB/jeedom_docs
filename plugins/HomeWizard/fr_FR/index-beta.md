---
layout: default
lang: fr_FR
title: Plugin HomeWizard Energy
description: Documentation du plugin HomeWizard Energy
---

Ce plugin permet de monitorer et exécuter quelques actions sur vos équipements [HomeWizard Energy](http://www.homewizard.com).

Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Si vous voullez aller plus vite, vous pouvez lancer les dépendances ou attendre ~5min.
Une fois les dépendances terminées, le démon démarrera dans les 5min également (ou vous pouvez le lancer à la main).

Le plugin demande NodeJS 22.19 ou plus récent : si votre version est plus ancienne, les dépendances la mettent à jour.

Le démon va détecter les périphériques HomeWizard Energy sur votre réseau automatiquement lors de son démarrage (multicast utilisé, routage non supporté !). Ensuite il continuera d'écouter les messages de vos équipements, ceux-ci doivent envoyer quand ils se connectent.  Pour forcer une découverte sur le réseau, relancez le démon (normalement pas nécessaire).

Vous pouvez régler la fréquence de questionnement des différents équipements déjà reconnus, par défaut c'est toutes les 5 secondes, le constructeur ne conseille pas de descendre sous la seconde (< 1000 ms).

Pour un équipement migré en API v2, il n'est plus questionné : c'est lui qui envoie ses mesures dès qu'elles changent. Cette fréquence devient alors le rythme maximum auquel Jeedom met à jour les commandes (un compteur P1 envoie une mesure par seconde).

Configuration des équipements 
=============================

La configuration des équipements HomeWizard Energy est accessible à partir du menu
plugins puis Objets connectés. Vous retrouvez ici :

-   un bouton pour afficher la configuration du plugin

-   un bouton Santé qui vous donne une vue d'ensemble de tous vos équipements à un moment donné, dont l'API utilisée par chacun (v1, v2, v2 à autoriser)

-   un bouton Migration API v2 qui ouvre l'assistant de migration (voir [Migration vers l'API v2](#migration-vers-lapi-v2)), qui sert aussi à autoriser Jeedom sur une Plug-In Battery

-   enfin en dessous vous retrouvez la liste de vos équipements HomeWizard Energy

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

-   **Adresse IP** (lecture seule) : L'adresse IP envoyée par votre équipement (non modifiable car les équipements sont découverts)

-   **API utilisée** (lecture seule) : v1 ou v2. Un bouton **Migrer vers l'API v2** apparait quand la migration est possible pour cet équipement (pour une Plug-In Battery ou un nouvel équipement ajouté directement en API v2, le bouton s'appelle **Autoriser Jeedom**).

**Onglet Commandes**
--------------------

Il existe de nombreuses commandes, elles sont différentes en fonction du type d'équipement. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non et les réorganiser. Vous pouvez aussi attribuer un widget au choix. Tout est standard.

Les noms viennent directement de l'équipement.

La valeur est affichée en temps réel et est modifiée en temps réel.

**Le widget du plugin**
-----------------------

Chaque équipement s'affiche sur le dashboard et en mobile avec le widget du plugin :

-   la mesure principale en grand : la puissance (en vert avec la mention **Injection** quand un compteur renvoie vers le réseau), ou le débit pour le compteur d'eau
-   les totaux : import, export, gaz, eau, tarif en cours, et pour une Plug-In Battery sa charge et ses cycles
-   le détail par phase (tension, courant, puissance) quand l'équipement a plusieurs phases
-   pour une Energy Socket, un bouton pour l'allumer et l'éteindre
-   les commandes action visibles (réglages, Identifier, pilotage des batteries...) avec leur widget Jeedom habituel
-   en bas : en ligne ou hors ligne, la qualité du wifi et l'API utilisée

Les valeurs se mettent à jour en direct, et un clic sur une valeur historisée ouvre son historique. Toutes les autres commandes info visibles se consultent dans un petit popup, par l'icône liste <i class="fas fa-list-ul"></i> (**Autres valeurs**) en bas du widget (rendez une commande non visible pour l'en retirer).

**Réglages de l'équipement, Identifier et Redémarrer**
-----------------------

Le plugin crée ces commandes quand l'équipement les propose :

-   **Cloud activer** / **Cloud désactiver** : la communication de l'équipement avec le cloud HomeWizard. Attention, sans le cloud l'application HomeWizard ne reçoit plus les données de l'équipement. Non modifiable sur une Plug-In Battery.
-   **Luminosité led** (API v2) : la luminosité de la led d'état, de 0 à 100 %.
-   **API v1 activer** / **API v1 désactiver** (Compteur P1 et kWh Meters en API v2, commandes masquées par défaut, aussi dans l'assistant) : une fois l'équipement en API v2, vous pouvez couper son ancienne API v1. Il n'est alors plus accessible qu'aux applications autorisées par un appui sur son bouton (Jeedom, l'application HomeWizard...). Un retour à l'API v1 depuis l'assistant la réactive automatiquement.
-   **Identifier** : fait clignoter la led de l'équipement quelques secondes, pratique pour le repérer (Compteur P1 et Plug-In Battery en API v2, Compteur P1 et Energy Socket en API v1).
-   **Redémarrer** (Compteur P1 et kWh Meters en API v2) : redémarre l'équipement. La commande est masquée par défaut et demande une confirmation.

**Types génériques**
-----------------------

La puissance et la consommation totale reçoivent d'office les types génériques **Puissance** et **Consommation**, et la charge d'une Plug-In Battery le type **Batterie** (elle apparait comme niveau de batterie dans HomeKit) : ce sont ceux utilisés par le plugin Homebridge. Pour les équipements existants ils sont ajoutés une seule fois, sans toucher aux types que vous avez déjà choisis ; vous pouvez ensuite les changer librement.

**Activer l'api locale dans l'application HomeWizard**
=============

Afin que votre équipement soit visible dans le plugin en API v1 il est NECESSAIRE d'activer l'API Locale sur celui-ci. Ce n'est pas nécessaire pour un équipement que vous utilisez directement en API v2 (voir [Nouvel équipement directement en API v2](#nouvel-équipement-directement-en-api-v2)), ni pour la Plug-In Battery.

1. Ouvrez l'application HomeWizard sur votre téléphone
2. En haut à droite appuyez sur l'engrenage
3. Allez dans "Mesures" (sur iOS) ou "Compteurs" (sur Android)
4. Appuyez sur votre équipement
5. Tout en bas dans les Paramètres, activez "API Locale"
6. **Relancez le démon car l'activation/désactivation alors que le démon est lancé peut le planter**.

**Migration vers l'API v2**
=============

HomeWizard remplace progressivement son API locale (v1) par une nouvelle API (v2). Le plugin propose de migrer vos équipements un par un, quand vous le voulez. Rien n'est migré automatiquement et un équipement non migré continue de fonctionner comme avant.

Ce que l'API v2 apporte :

-   la connexion entre Jeedom et l'équipement est chiffrée (https) et protégée par une autorisation propre à votre Jeedom
-   l'équipement envoie ses mesures à Jeedom dès qu'elles changent (websocket), Jeedom ne l'interroge plus en boucle. Si cette liaison ne fonctionne pas, le plugin repasse tout seul en interrogation régulière.
-   c'est la seule API de la batterie Plug-In Battery (voir [Plug-In Battery](#plug-in-battery))

**Quels équipements ?**
---------------------

| Équipement | API v2 |
| --- | --- |
| Compteur P1 (HWE-P1) | Oui |
| kWh Meter 1 phase (HWE-KWH1, SDM230-wifi) | Oui |
| kWh Meter 3 phases (HWE-KWH3, SDM630-wifi) | Oui |
| Plug-In Battery (HWE-BAT) | Uniquement en API v2 : pas de migration, seulement une autorisation |
| Energy Socket (HWE-SKT) | Pas encore proposée par HomeWizard |
| Compteur d'eau (HWE-WTR) | Pas encore proposée par HomeWizard |
| Energy Display | Pas encore proposée par HomeWizard |

L'équipement doit avoir un firmware récent : le plugin détecte tout seul si votre équipement annonce l'API v2. Si l'assistant indique « L'équipement n'annonce pas l'API v2 », mettez son firmware à jour avec l'application HomeWizard puis relancez le démon.

**Migrer un équipement**
---------------------

Vous devez pouvoir aller jusqu'à l'équipement : il faut appuyer sur son bouton pour autoriser Jeedom.

1. Cliquez sur **Migration API v2** dans la page du plugin (ou sur **Migrer vers l'API v2** dans la page de l'équipement).
2. L'assistant liste vos équipements et leur état. Cliquez sur **Migrer** sur l'équipement voulu (ou **Enchainer tous les équipements possibles** pour les faire l'un après l'autre).
3. L'assistant affiche l'équipement avec l'emplacement du bouton et un décompte de 2 minutes. Appuyez sur le bouton de l'équipement :
    -   Compteur P1 : un appui
    -   kWh Meter : maintenez le bouton enfoncé entre 1 et 3 secondes, puis relâchez
4. Jeedom détecte l'appui tout seul et termine la migration. Si rien n'est détecté pendant le décompte, cliquez sur **Réessayer**.

Vous pouvez annuler ou fermer la fenêtre pendant l'attente, rien n'est modifié tant que le bouton n'a pas été appuyé.

**Ce qui change pour vos commandes**
---------------------

Les données ont changé de nom dans l'API v2 (par exemple `total_power_import_kwh` devient `energy_import_kwh`, `active_power_w` devient `power_w`). Le plugin renomme vos commandes existantes : ce sont les mêmes commandes, **l'historique, les scénarios, les designs et les virtuels sont conservés**. Le nom affiché n'est modifié que si vous ne l'aviez pas personnalisé.

Pensez à vérifier ce qui utiliserait le nom ou le logicalId d'une commande en dehors de Jeedom (appels API, autres box, interactions).

Quelques particularités :

-   **kWh Meters** : l'API v2 ne fournit plus les index par tarif, seulement les totaux. Les commandes `Total_power_import_t1_kwh` et `Total_power_export_t1_kwh` ne sont donc plus mises à jour après la migration (elles sont conservées avec leur historique). Utilisez à la place les commandes des totaux (`Energy_import_kwh` et `Energy_export_kwh`). L'assistant vous rappelle les commandes concernées avant et après la migration.
-   **Wifi** : la force du signal reste disponible en % (`Wifi_strength`), une commande `Wifi_rssi_db` (en dB) est ajoutée. Elles sont mises à jour toutes les minutes.
-   **Gaz** (compteur P1) : les commandes `Total_gas_m3` et `Gas_unique_id` continuent d'être mises à jour.
-   **Pic mensuel** (compteur P1 belge) : `Montly_power_peak_w` et `Montly_power_peak_timestamp` deviennent `Monthly_power_peak_w` et `Monthly_power_peak_timestamp`, `Active_power_average_w` devient `Average_power_15m_w`.

**Couper l'API v1 après la migration**
---------------------

Une fois un Compteur P1 ou un kWh Meter migré, Jeedom n'utilise plus son ancienne API v1. L'assistant propose alors **Couper l'API v1** (sur l'écran de fin de migration, et dans la liste pour un équipement déjà migré) : l'équipement n'est plus accessible qu'aux applications autorisées par un appui sur son bouton (Jeedom, l'application HomeWizard...). C'est plus sûr, mais une application qui lit encore l'API v1 (ancienne intégration, script...) ne recevra plus rien.

La liste de l'assistant indique **API v1 coupée** et propose **Réactiver l'API v1**. Les commandes **API v1 activer** / **API v1 désactiver** de l'équipement font la même chose (pour un scénario par exemple). Un retour à l'API v1 la réactive automatiquement.

**Revenir à l'API v1**
---------------------

Dans l'assistant, un équipement migré propose **Revenir à l'API v1**. L'autorisation de Jeedom est supprimée de l'équipement et les commandes reprennent leurs noms d'origine, toujours avec leur historique. L'API Locale doit être activée dans l'application HomeWizard pour que l'équipement réponde en API v1.

**Nouvel équipement directement en API v2**
---------------------

Un nouvel équipement n'a pas besoin de passer par l'API v1 : s'il annonce l'API v2 (voir le tableau ci-dessus), il apparait dans le plugin dès qu'il est découvert sur le réseau, même sans activer l'API Locale dans l'application HomeWizard. Il est alors sans valeurs, en attente d'autorisation.

1. Ouvrez l'assistant **Migration API v2** (ou cliquez sur **Autoriser Jeedom** dans la page de l'équipement).
2. Cliquez sur **Autoriser** sur la ligne de l'équipement.
3. Appuyez sur le bouton de l'équipement pendant le décompte (kWh Meter : maintenez 1 à 3 secondes).

Il n'y a rien à migrer dans ce cas : ses commandes sont créées directement avec les noms de l'API v2.

**Plug-In Battery**
---------------------

La Plug-In Battery n'existe qu'en API v2 : il n'y a rien à migrer. Elle se comporte comme un nouvel équipement ajouté directement en API v2 : elle apparait dans le plugin dès qu'elle est découverte sur le réseau, mais sans valeurs, il faut d'abord autoriser Jeedom en appuyant sur son bouton.

1. Ouvrez l'assistant **Migration API v2** (ou cliquez sur **Autoriser Jeedom** dans la page de la batterie).
2. Cliquez sur **Autoriser** sur la ligne de la batterie.
3. Appuyez une fois sur le bouton de la batterie pendant le décompte.

Ses commandes sont créées et mises à jour dès que l'appui est détecté. Il n'y a pas d'API Locale à activer dans l'application HomeWizard pour cet équipement.

**Piloter plusieurs batteries**
---------------------

Les Plug-In Batteries sont pilotées en groupe par le compteur auquel elles sont associées (compteur P1 ou kWh Meter). Quand ce compteur est en API v2 et qu'au moins une batterie lui est associée, le plugin ajoute sur le **compteur** :

-   des informations : nombre de batteries, mode, puissance actuelle et puissance visée du groupe, consommation et production maximales, charge autorisée, décharge autorisée, charge complète en cours
-   des actions : choisir le mode (Zéro, Charge complète, Veille, Prédictif), autoriser ou interdire la charge, autoriser ou interdire la décharge, lancer ou arrêter la charge complète

Chaque batterie reste aussi un équipement à part entière dans le plugin, avec ses propres mesures (niveau de charge, puissance, cycles).

Le mode Prédictif n'existe que sur les firmwares récents ; s'il est refusé par l'équipement, l'erreur apparait dans le log.

**Plusieurs Jeedom sur le même équipement**
---------------------

Un même équipement peut être utilisé en API v2 par plusieurs Jeedom en même temps (une box de production et une box de test par exemple). Chaque Jeedom doit faire sa propre autorisation, avec son propre appui sur le bouton : il reçoit sa propre autorisation, sous un nom qui lui est propre, et les deux cohabitent sur l'équipement.

La migration ne concerne que le Jeedom sur lequel vous la faites. L'équipement continue de répondre en API v1 tant que l'API Locale reste activée dans l'application HomeWizard : un autre Jeedom, ou une autre application, peut donc rester en API v1 sur le même équipement.

Si un Jeedom est une copie d'un autre (sauvegarde restaurée sur une autre machine), les deux partagent les mêmes autorisations et fonctionnent tous les deux. Le plugin le détecte au démarrage du démon et vous prévient dans le centre de messages. Il donne alors un nouveau nom d'autorisation à la copie : refaire une autorisation sur la copie ne coupe pas le Jeedom d'origine, et un retour à l'API v1 sur la copie ne supprime pas l'autorisation partagée de l'équipement.

Cette détection s'appuie sur l'identifiant de la machine. S'il n'est pas disponible (certaines installations en conteneur), le plugin affiche seulement un message après une restauration : dans ce cas, refaire une autorisation ou revenir à l'API v1 sur l'un des deux Jeedom coupe l'autre.

**Utilisateurs autorisés sur un équipement**
---------------------

Dans l'assistant, le bouton **Utilisateurs** d'un équipement en API v2 liste toutes les applications autorisées sur cet équipement et permet d'en supprimer. L'équipement ne donne que le nom de chaque utilisateur (ni adresse IP, ni date), le plugin en déduit l'origine :

-   **Ce Jeedom** : ne se supprime pas ici (utilisez **Revenir à l'API v1** ou supprimez l'équipement)
-   **Un autre Jeedom** : le nom contient le nom du Jeedom qui l'a créé (pour les autorisations faites à partir de cette version)
-   **Application HomeWizard (cloud)** : la supprimer peut couper l'application HomeWizard de cet équipement
-   **Autre application locale** : Home Assistant, etc.

Supprimer un utilisateur coupe immédiatement l'accès de l'application qui l'utilise.

**Si un équipement en API v2 ne remonte plus**
---------------------

Une coupure courte (redémarrage de l'équipement, wifi) se répare toute seule : le plugin se reconnecte en continu. Si elle dure, la commande **Online** passe à 0 avec un avertissement dans le log du démon, puis revient à 1 au retour de l'équipement (voir [La commande Online](#la-commande-online)).

Si l'équipement a été réinitialisé ou si l'autorisation de Jeedom a été supprimée, une alerte apparait dans le centre de messages (une seule fois, elle disparait quand l'autorisation est refaite), et l'assistant comme la page Santé indiquent « Token refusé » : cliquez sur **Refaire l'autorisation** dans l'assistant et appuyez de nouveau sur le bouton de l'équipement. Vos commandes ne changent pas.

**La commande Online**
=============

Un équipement est en ligne tant qu'il a envoyé un message pendant les 3 derniers cycles de la fréquence configurée pour son type (au minimum 10 secondes). Avec le réglage par défaut de 5 secondes, il passe donc hors ligne après 15 secondes sans nouvelles, et revient en ligne dès le message suivant.

Pour un équipement en API v2, qui n'envoie que ce qui change, la liaison ouverte avec lui compte aussi comme un signe de vie : un équipement dont les valeurs ne bougent pas reste en ligne. S'il ne répond réellement plus, il est vu hors ligne au plus tard après une minute environ.

Toutes les 5 minutes, le plugin vérifie aussi par un ping les équipements silencieux : sans réponse, ils passent hors ligne.

Quand le démon est arrêté, plus aucune valeur ne remonte : tous les équipements passent hors ligne, et reviennent en ligne à leur premier message après le redémarrage.

**Suppression d'un équipement**
=============

Quand vous supprimez de Jeedom un équipement en API v2, le plugin retire aussi l'autorisation de Jeedom sur l'équipement HomeWizard. Si l'équipement n'est pas joignable à ce moment-là, l'autorisation y reste (un avertissement est écrit dans le log), sans conséquence pour Jeedom.

Un équipement supprimé mais toujours présent sur le réseau sera redécouvert au prochain démarrage du démon.

**Compatibilités**
==================

**En attente de tests (mais devraient être fonctionnels)**
----------------------

-    Plug-In Battery (HWE-BAT) (API v2 uniquement : elle apparait dans le plugin dès sa découverte, ses valeurs arrivent une fois Jeedom [autorisé par un appui sur son bouton](#plug-in-battery)) [https://www.homewizard.com/fr-be/boutique/plug-in-battery/](https://www.homewizard.com/fr-be/boutique/plug-in-battery/)
-    Wi-Fi kWh Meter (1 phase) (HWE-KWH1) [https://www.homewizard.com/fr-be/boutique/compteur-wi-fi-kwh-mid-1-phase/](https://www.homewizard.com/fr-be/boutique/compteur-wi-fi-kwh-mid-1-phase/)
-    Wi-Fi kWh Meter (3 phases) (HWE-KWH3) [https://www.homewizard.com/fr-be/boutique/compteur-wi-fi-kwh-mid-3-phases/](https://www.homewizard.com/fr-be/boutique/compteur-wi-fi-kwh-mid-3-phases/)

**Compatibles**
---------------

-    Compteur d'eau (HWE-WTR) (Seulement si branché en USB) [https://www.homewizard.com/fr-be/boutique/compteur-deau-wi-fi/](https://www.homewizard.com/fr-be/boutique/compteur-deau-wi-fi/)
-    Compteur P1 (HWE-P1) [https://www.homewizard.com/fr-be/boutique/compteur-wi-fi-p1/](https://www.homewizard.com/fr-be/boutique/compteur-wi-fi-p1/)
-    Prises connectées wifi (HWE-SKT) [https://www.homewizard.com/fr-be/boutique/energy-socket-wi-fi/](https://www.homewizard.com/fr-be/boutique/energy-socket-wi-fi/)

**NON-Compatibles**
---------------

-    Compteur d'eau WIFI (HWE-WTR) (Sur pile) [https://www.homewizard.com/fr-be/boutique/compteur-deau-wi-fi/](https://www.homewizard.com/fr-be/boutique/compteur-deau-wi-fi/)
-    Temperature Humidity Meter (HWE-TMP) (pas d'API locale, HomeWizard étudie seulement la possibilité)
-    Energy Display (pas encore d'API publiée par HomeWizard) [https://www.homewizard.com/fr-be/boutique/energy-display/](https://www.homewizard.com/fr-be/boutique/energy-display/)
