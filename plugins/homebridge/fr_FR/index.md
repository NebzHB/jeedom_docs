---
layout: default
lang: fr_FR
title: Plugin Homebridge
description: Documentation du plugin Homebridge
---

Présentation Homebridge
=======================

*Le plugin Homebridge* est un démon qui permet d’interagir avec un système domotique via l’assistant vocal Siri sous iOS. Le HomeKit a été introduit depuis iOS 8, mais est véritablement opérationnel depuis iOS 10 via l’application Maison. 

![homekit-logo](../images/homekit-logo.jpg)

Le plugin Homebridge de Jeedom permet donc d’exposer des équipements Jeedom qui seront vus comme des accessoires compatibles au protocole *HomeKit*.

>Homebridge n'est pas officiellement supporté par Apple. A tout moment, Apple peut bloquer ce protocole.

Que peut-on faire avec Homebridge ?
---------------------------------

![schemaHomebrdige](https://market.jeedom.com/filestore/market/plugin/images/homebridge_screenshot1.png)

Homebridge peut s'utiliser avec une application compatible HomeKit ou avec l'assistant vocal Siri.

Depuis iOS 10, l'application Maison (inclue par défaut avec iOS) permet le pilotage d'équipements compatibles HomeKit. 

![cuisine-homekit](../images/cuisine-01.png) ![cuisine-homekit](../images/salon-01.png) ![cuisine-homekit](../images/salle-de-bain-01.png)

Les équipements peuvent être classés par pièce. Il est également possible de mettre des accessoires en favoris sur la page d'accueil. Une page spécifique indique l'ensemble des états des accessoires.

![piece-homekit](../images/piece-homekit.jpg) ![piece-homekit](../images/accueil-01.png) ![etat](../images/etat.png)

Beaucoup d'accessoires sont pris en charge.

![garage-homekit](../images/acchb.png)

Siri peut aussi interagir. Il répond aux questions et fait des actions.  

![siri-01](../images/siri-01.jpg) ![siri-02](../images/siri-02.jpg)

Le plugin prend en charge les scénarios. Il est possible de les exécuter directement depuis l'app Maison d'Apple.

HomeKit a l'avantage d'être utilisable à l'extérieur du domicile. Seule condition: il faut disposer d'un concentrateur. 
L'iPad, l'AppleTV et le HomePod peuvent servir de concentrateur. Pour cela, ils doivent être connectés au même compte iCloud.
>Pour un fonctionnement optimal, il est recommandé d'utiliser une AppleTV ou un Homepod en tant que concentrateur. Ces équipements étant alimentés sur secteur, ils sont beaucoup plus fiables. 

>HomeKit est le nom officiel du protocole développé par Apple. Homebridge est son équivalent Open Source développé par nfarina. Ce dernier a étendu le projet HAP-NodeJS qui est le moteur d'Homebridge.

Installation et activation du plugin Homebridge
==============================================

Le plugin Homebridge doit être installé via le market Jeedom.

![pluginHB](../images/pluginHB.png) ![pluginHB](../images/pluginHB2.png)

Une fois le plugin installé, il suffit de l'activer en cliquant sur "Activer".

![activationHB](../images/activationHB.png)

Installation des dépendances
----------------------------

Les dépendances sont installées automatiquement par Jeedom dans les 5 min. Elles seront également réinstallées lors d'une mise à jour du plugin si besoin.

![installationDep](../images/installationDep.png)

*Le temps d'installation des dépendances peut varier en fonction du matériel utilisé.*

*Systèmes compatibles avec Homebridge :*

* Raspberry Pi 3 et 4

* Box Jeedom smart

* Box Jeedom pro V2

* Tout système basé sur Debian 9 ou 10


>Les installations sous Docker, la Jeedom Mini+ et Raspberry Pi zero, 1 & 2 ainsi que Debian 8 (Jessie) et les système x86 32bits ne sont pas supportés.

Une fois les dépendances installées, le démon se lance (dans les 5 min). Si le statut n'est pas sur "OK", il faut cliquer sur "(Re)Démarrer".

![demon-homebridge](../images/demon-homebridge.png)

Mise à jour manuelle des dépendances
------------------------------------

Pour mettre à jour manuellement les dépendances, il faut cliquer sur "Relancer".

![dependances-homebridge](../images/dependances-homebridge.png)

Fichiers LOG
------------

Les fichiers log permettent d'analyser pas à pas l'activité interne du processus et ses interactions avec son environnement.

Ces fichiers peuvent être nécessaires en cas de dysfonctionnement du plugin.

![log](../images/log.png)

* Homebridge : Historise toutes les communications avec le démon homebridge.

* Homebridge_daemon : Historise les actions effectuées par Homebridge (par exemple si un accessoire est envoyé à Homebridge mais n'apparaît pas dans l'application Maison, c'est ici qu'il faut aller voir).

* Homebridge_dep : Historise toutes les étapes de l'installation des dépendances. Si le démon refuse de démarrer par exemple, un coup d'oeil peut aider).

* DebugInfo : Il ne s'agit pas vraiment d'un Log mais plutot d'informations de debuggage qui peuvent aider à diagnostiquer votre problème.  Pour avoir ces informations, il faut passer les logs du démon en "Debug" ou en "Info" puis actualiser la fenêtre (F5). A côté de "Configuration" dans le plugin Homebridge, vous avez l'icone DebugInfo qui est apparue. Il vous suffit de cliquer dessus et attendre que le relevé des informations s'effectue. Vous pouvez ensuite copier tout ou bien la catégorie qui vous est demandée.

![ExempleDebugInfo](../images/debugInfo.png)

Configuration du plugin Homebridge
=================================

Création du pont Homebridge
--------------------------

Pour créer le pont Homebridge, il faut aller dans la rubrique "Gestion", et cliquer sur "Configuration".

![gestion](../images/gestion.png)

Pour créer le pont, il suffit de lui donner un nom et un code "PIN".

![config-pluginhb](../images/config-pluginhb.png)

* *Nom Homebridge* : Permet de nommer le pont Homebridge. 


>Le changement de nom Homebridge obligera à reconfigurer les applications HomeKit.

* *PIN Homebridge* : Permet de personnaliser le code PIN Homebridge.


>Les PIN suivants ne sont pas acceptés par Apple : 000-00-000, 111-11-111 -> 999-99-999, 123-45-678, 876-54-321. Son changement obligera la reconfiguration des applications HomeKit.

* *Réparer* :  Permet une réparation de Homebridge en modifiant les identifiants. 


>Il faut retirer le bridge de l'application "Maison".

* *Réparer & réinstaller* : Supprime et réinstalle complètement Homebridge. 

>A n'effectuer que sur conseil d'un membre du forum et il faut retirer le pont de l'application "Maison".

* *Gérer les plugins pour Homebridge* : Permet de gérer les modules npm homebridge-xxx installés sur le système.

* *Importer Cameras du plugin Hikvision (BETA)* : Permet d'importer automatiquement les caméras du plugin Hikvision dans les plateformes supplémentaires (En test, à vérifier).

* *Importer Cameras de Synology Surveillance Station (BETA)* : Permet d'importer automatiquement les caméras du plugin Synology Surveillance Station dans les plateformes supplémentaires (En test, à vérifier).

* *Importer Cameras du plugin Camera (BETA)* : Permet d'importer automatiquement les caméras du plugin Camera dans les plateformes supplémentaires (En test, à vérifier).

>L'importation risque de vous faire un doublon si vous avez déjà inclu votre caméra précédemment, une fois importée, une caméra ne sera plus modifiée par cet import. (grace au "serialNumber"). Pour le plugin Camera, la caméra doit avoir le champ "URL de flux" remplis.

* *Plateforme Homebridge supplémentaire* : Permet de rajouter manuellement un plugin Homebridge de type plateforme (homebridge-camera-ffmpeg ou homebridge-nest par exemple).

* *Accessoire Homebridge supplémentaire* : Permet de rajouter manuellement un plugin Homebridge de type accessoire (homebridge-freemote par exemple).

* *Lancer l'interface de configuration Config-UI-X (Local seulement)* : Permet de lancer l'interface de homebridge-config-ui-x qui est maintenant pré-installé et configuré. Attention, toute modification dans un plugin ou config.json ne sera pas pris en compte pour l'instant. Peut-être plus tard. Si vous ne voyez pas l'interface, tentez avec http://votreIP:33221/

* *Authentification Config-UI-X* : Active l'authentification dans Config-UI-X, si vous vous êtes déjà loggué dans cette interface avant, votre cookie reste valide tant que vous ne vous êtes pas déconnecté. Sinon par défaut, c'est : Utilisateur : admin et mot de passe : admin. Pour modifier, dans Config-UI-X, le menu trois points en haut à droite > Comptes Utilisateurs

>Réservé à un public averti. Il n'y aura aucun support pour ces configurations de plugins supplémentaires et imports.

* *Activer le debug intégré de homebridge (très verbeux) et de ses plugins* : Permet d'activer le mode de debug complet de Homebridge et des autres plugins, rarement nécessaire donc il est maintenant séparé pour augmenter la lisibilité du log, même en débug. (Il s'agit du mode DEBUG=* de Homebridge, un redémarrage du ddémon est nécessaire)

* *Envoyer les nouveaux équipements Jeedom dans Homebridge par défaut* : Nouveau comportement, en décochant cette case, tout nouvel équipement ajouté à Jeedom ne sera pas ajouté à Homebridge au prochain redémarrage du démon. Il faudra cocher manuellement la case devant le nom de l'équipement (voir chapitre suivant). Coché par défaut pour coller au précédent comportement.

* *Activer les graphiques dans Eve (Alpha)* : Permet de relever les données pour être utilisées dans Eve en tant que graphiques. (Aucun Support) Fonctionne seulement pour Température, Humidité, Pression, Porte/Fenêtre, Présence.  Les graphiques ont été développés par ingénierie inversée des composants Elgato Eve et il peut y avoir des incohérences. Les données des graphiques sont les données collectées lorsque le démon Homebridge est démarré, il peut donc manquer certaines informations. Les graphiques sont uniquement à titre informatif.


Une fois les cases *nom Homebridge et PIN Homebridge* correctement renseignées, la configuration se finalise en cliquant sur **Sauvegarder**. Le démon redémarre.


>Un QR code est généré automatiquement. Cela améliore l'intégration du pont jeedom dans Homekit. Voir la partie "Ajout de Jeedom dans HomeKit".

Ajout des accessoires et scénarios dans Homebridge
------------------------------------

Les équipements seront à ajouter manuellement. 

![config-piece](../images/config-piece.png)

Assurer-vous que la pièce soit bien activée. (Cocher la case activer la pièce case en haut)

![choix-acc](../images/choix-acc.png)

![scenario](../images/scenario.png)

Afin d'ajouter un équipement ou un scénario à Homebridge, il suffit de cocher la case "Envoyer à Homebridge" se trouvant en face de l'équipement. Ensuite, Pour sauvegarder, il suffit de cliquer sur la petite disquette verte ou le bouton Sauvegarder.
Les scénarios seront créés sous forme d'interrupteurs. En l'activant, vous lancerez le scénario. En le désactivant, vous le stopperez (s'il tournait toujours). L'interrupteur reste activé tant que le scénario tourne.

Il est possible de modifier le nom de l'équipement dans Homekit. Si celui-ci est déja installé sous l'ancien nom, il sera supprimé. Un nouvelle accessoire sera alors crée. Il apparaîtra dans la pièce où se situe le pont.

![newid](../images/newid.png)

>Si des modifications ont été faites, comme le changement du type générique, la modification d'un paramètre, l'ajout d'un accessoire, il faut impérativement redémarrer le Démon pour la prise en compte dans Homebridge.

Configuration des types génériques
=================================

Généralités
----------

En cliquant sur l'équipement, les types génériques utilisés pour la communication entre votre Jeedom et Homebridge apparaissent.

![typegen-1](../images/typegen-1.png)

La majorité des types génériques est déjà renseignée. Dans certains cas, une configuration manuelle sera nécessaire (pour le plugin Virtuel ou si le developpeur du plugin ne les a pas renseignés).

Voici les types génériques disponibles : 

Lumière
----------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:---------:|-------------|
|Info/Lumière Etat (Binaire)|`NON`|Ajout uniquement pour les lumières dont la luminosité ne change pas lorsqu’elle est éteinte (Yeelight, Ikea, …)<br/>0 = Eteint<br/>Autre que 0 = Allumé|
|Info/Lumière Etat|`OUI`|Luminosité<br/>0-100 Ou 0-99 ou 0-255<br/>(en fonction du max de Action/Lumière Slider)<br/>ou Binaire<br/>0 = Eteint<br/> autre que 0 = Allumé| 
|Info/Lumière Luminosité|`NON`|NE PAS UTILISER !!!<br/>Préférez Info/Lumière Etat|
|Action/Lumière Slider|`OUI`|Réf. vers Lumière Etat|
|Action/Lumière Bouton On|`OUI`|Réf. vers Lumière Etat :<br/>- Binaire s’il est présent<br/>- Etat sinon|
|Action/Lumière Bouton Off|`OUI`|Réf. vers Lumière Etat :<br/>- Binaire s’il est présent<br/>- Etat sinon|
|Info/Lumière Couleur|`NON`|Format #RRGGBB|
|Action/Lumière Couleur|`Si Info/Lumière Couleur `|Réf. vers Info/Lumière Couleur|
|Info/Lumière Température Couleur|`NON`|Format Mired (<=500) ou Kelvin (>500)|
|Action/Lumière Température Couleur|`Si Info/Lumière Température Couleur`|Réf. vers<br/>- Info/Lumière Température Couleur<br/>Min&Max Obligatoire|
|Action/Lumière Toggle|`NON Utilisé`|N/A|
|Action/Lumière Mode|`NON Utilisé`|N/A|

Prises
----------

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Info/Prise<br/>Etat|`OUI`|0 = Eteint<br/>1 = Allumé|
|Action/Prise<br/>Bouton On|`OUI`|Réf. vers Info/Prise Etat| 
|Action/Prise<br/>Bouton Off|`OUI`|Réf. vers Info/Prise Etat|
|Action/Prise<br/>Slider|`NON Utilisé`|N/A|

Ventilateur
----------

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Info/Ventilateur<br/>Etat|`OUI`|0 = Eteint<br/>1 = Allumé<br/>ou pourcentage si vitesse|
|Action/Ventilateur<br/>Bouton On|`OUI`|Réf. vers Info/Ventilateur Etat| 
|Action/Ventilateur<br/>Bouton Off|`OUI`|Réf. vers Info/Ventilateur Etat|
|Action/Ventilateur<br/>Vitesse<br/>Rotation|`NON`|0-100<br/>Réf. vers Info/Ventilateur Etat|

Valves
----------

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Info/Robinet<br/>Etat|`OUI`|0 = Eteint<br/>1 = Allumé|
|Action/Robinet<br/>Bouton On|`OUI`|Réf. vers Info/Robinet Etat| 
|Action/Robinet<br/>Bouton Off|`OUI`|Réf. vers Info/Robinet Etat|

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Info/Irrigation<br/>Etat|`OUI`|0 = Eteint<br/>1 = Allumé|
|Action/Irrigation<br/>Bouton On|`OUI`|Réf. vers Info/Irrigation Etat| 
|Action/Irrigation<br/>Bouton Off|`OUI`|Réf. vers Info/Irrigation Etat|

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Info/Valve<br/>Générique<br/>Etat|`OUI`|0 = Eteint<br/>1 = Allumé|
|Action/Valve<br/>Générique<br/>Bouton On|`OUI`|Réf. vers Info/Valve Générique Etat| 
|Action/Valve<br/>Générique<br/>Bouton Off|`OUI`|Réf. vers Info/Valve Générique Etat|
|Info/Valve<br/>générique<br/>Durée|`NON`|0-3600 Secondes|
|Info/Valve<br/>générique<br/>Durée Restante|`NON`|0-3600 Secondes|

Interrupteurs
----------

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Info/Interrupteur<br/>Etat|`OUI`|0 = Eteint<br/>1 = Allumé|
|Action/Interrupteur<br/>Bouton On|`OUI`|Réf. vers Info/Interrupteur Etat| 
|Action/Interrupteur<br/>Bouton Off|`OUI`|Réf. vers Info/Interrupteur Etat|

Bouton poussoir
----------

|Type générique  | Obligatoire | Valeurs possibles |
|----------------|:-----------:|------------|
|Action/Bouton<br/>poussoir|`NON`|type = "Défaut" dans jeedom|

Volets
--------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Volet Etat|`OUI mais état unique`|min du slider = Fermé<br/>max du slider = Ouvert|
|Info/Volet Etat Fermeture|`OUI mais état unique`|min du slider = Ouvert<br/>max du curseur = Fermé|
|Action/Volet Bouton Monter|`Si Descendre`|Réf. vers Info/Volet Etat| 
|Action/Volet Bouton Descendre|`Si Monter`|Réf. vers Info/Volet Etat|
|Action/Volet Bouton Stop|`NON Utilisé`|N/A|
|Action/Volet Bouton Slider|`Si seul`|Réf. vers Info/Volet Etat|
|Info/Volet Etat Inclinaison Horizontale|`NON`|Angle 0->90°|
|Action/Volet Slider Inclinaison Horizontale|`Si Etat Inclinaison H`|Angle 0->90°<br/>modifiable via min-max du slider|
|Info/Volet Etat Inclinaison Verticale|`NON`|Angle 0->90°|
|Action/Volet Slider Inclinaison Verticale|`Si Etat Inclinaison V`|Angle 0->90°<br/>modifiable via min-max du slider|

Volets BSO
----------

Pas encore supportés (mais possible via Volets normaux et les inclinaisons)

Fenêtres Motorisées
-------------------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Fenêtre Motorisée Etat|`OUI`|0 = Fermé<br/>100 = Ouvert|
|Action/Fenêtre Motorisée Monter|`Si Descendre`|Réf. vers Info/Fenêtre Motorisée Etat| 
|Action/Fenêtre Motorisée Descendre|`Si Monter`|Réf. vers Info/Fenêtre Motorisée Etat|
|Action/Fenêtre Motorisée Slider|`Si seul`|Réf. vers Info/Fenêtre Motorisée Etat|

Chauffage fil pilote
---------------------

Utiliser le plugin Thermostat.

Serrures
--------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Serrure Etat|`OUI`|pas 1 = Non Sécurisée<br/>1 = Sécurisée|
|Action/Serrure Bouton Ouvrir|`OUI`|Réf. vers Info/Serrure Etat| 
|Action/Serrure Bouton Fermer|`OUI`|Réf. vers Info/Serrure Etat| 

Alarme
------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Alarme état|`OUI`|1 = Déclenchée<br/>(prioritaire sur activée et modes)|
|Info/Alarme état activée|`OUI`|0 = Désarmée<br/>(prioritaire sur modes)|
|Info/Alarme mode|`OUI si associé mode homekit`|Exactement le nom d'une Action/Alarme Mode<br/> à associer à Nuit ou Present ou Absent|
|Action/Alarme armée|`OUI`|Arme l'alarme|
|Action/Alarme libérée|`OUI`|Désarme l'alarme|
|Action/Alarme Mode|`NON`|Mode à associer à un mode homekit (max 3)|

Sirènes
-------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Sirène Etat|`OUI`|pas 1 = Sonne pas<br/>1 = Sonne|

Thermostats
-------------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Thermostat Etat (BINAIRE)|`NON Utilisé`|0 = Eteint<br/>1 = Allumé|
|Info/Thermostat Etat (HUMAIN)|`NON`|'off' ou 'arrêté' ou 'arret'<br/>'heat' ou 'chauffage'<br/>'cool' ou 'climatisation'| 
|Info/Thermostat Mode|`OUI si associé mode homekit`|'Off' ou 'Arret' = OFF<br/>'Aucun' ou 'Thermostat' = AUTO<br/>Exactement le nom d'une Action/Thermostat Mode<br/> à associer à HEAT ou COOL|
|Action/Thermostat Mode|`NON`|Mode à associer à un mode homekit (max 2)|
|Info/Thermostat Température Extérieur|`NON utilisé`|N/A
|Info/Thermostat Température ambiante|`NON`|-50 → 100| 
|Info/Thermostat Consigne|`OUI`|10 → 38| 
|Action/Thermostat Consigne|`OUI`|10 → 38| 
|Info/Thermostat Verrouillage|`NON`|0 = Non Verrouillé<br/>1 = Verrouillé| 
|Action/Thermostat Verrouillage|`OUI si Info/Verrouillage`|N/A
|Action/Thermostat Déverrouillage|`OUI si Info/Verrouillage`|N/A

Portails ou Garages
--------------------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Portail état ouvrant<br/>Info/Garage état ouvrant<br/>(même traitement)|`OUI`|0 = Fermé<br/>252 = Fermeture en cours<br/>253 = Stoppé<br/>254 = Ouverture en cours<br/>255 = Ouvert<br/>(Configurable)|
|Action/Portail ou garage bouton toggle|`Si seul`|Réf. vers Info/Portail état ouvrant<br/>ou<br/>Réf. vers Info/Garage état ouvrant| 
|Action/Portail ou garage bouton d’ouverture|`Si pas Toggle`|Réf. vers Info/Portail état ouvrant<br/>ou<br/>Réf. vers Info/Garage état ouvrant
|Action/Portail ou garage bouton de fermeture|`Si pas Toggle`|Réf. vers Info/Portail état ouvrant<br/>ou<br/>Réf. vers Info/Garage état ouvrant

Haut-Parleurs (Eve Seulement)
-----------------------------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Haut-Parleur Mute|`NON`|1 = Pas de son<br/>0 = Son|
|Action/Haut-Parleur Mute|`Si pas Toggle`|Réf. vers Info/Haut-Parleur Mute| 
|Action/Haut-Parleur UnMute|`Si pas Toggle`|Réf. vers Info/Haut-Parleur Mute| 
|Action/Haut-Parleur Toggle Mute|`Si seul`|Réf. vers Info/Haut-Parleur Mute|
|Info/Haut-Parleur Volume|`OUI`|%| 
|Action/Haut-Parleur Volume|`OUI`|Réf. vers Info/Haut-Parleur Volume| 

Multimedia (Eve Seulement)
-----------------------------
|Info/Volume|`OUI`|Même chose que Info/Haut-Parleur Volume| 
|Action/Volume|`OUI`|Réf. vers Info/Volume<br/>ême chose que Action/Haut-Parleur Volume| 

Interrupteur programmable Multi-Valeurs
--------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Interrupteur programmable<br/>(multi-valeur)|`NON`|Valeurs correspondantes<br/>(une colonne par bouton)<br/>Séparer par ;|

Interrupteur programmable Binaires
--------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Interrupteur programmable "binaire"<br/>(Double Click)|`NON`|Numéro du bouton<br/>pour groupage|
|Info/Interrupteur programmable "binaire"<br/>(Long Click)|`NON`|Numéro du bouton<br/>pour groupage|
|Info/Interrupteur programmable "binaire"<br/>(Simple Click)|`NON`|Numéro du bouton<br/>pour groupage|

Generic
----------

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Puissance Electrique|`NON`|Watts (Eve Seulement)<br/><br/>*à ajouter à un équipement existant*<br/>*Pas seule commande d'un équipement*| 
|Info/Consommation Electrique|`NON`|KWh (Eve Seulement)<br/><br/>*à ajouter à un équipement existant*<br/>*Pas seule commande d'un équipement*| 
|Info/Température|`NON`|-50 → 300 °C| 
|Info/Luminosité|`NON`|0 → 100000 lux| 
|Info/Présence|`NON`|0 = Pas de mouvement<br/>1 = Mouvement|
|Info/Occupation|`NON`|0 = Personne<br/>1 = Quelqu'un|
|Info/Batterie|`NON`|%| 
|Info/Batterie en charge|`NON`|0 = NON<br/>1 = OUI<br/>Non présent = Non Rechargable| 
|Info/Détection de fumée|`NON`|0 = Pas de fumée<br/>Pas 0 = Fumée détectée| 
|Info/Inondation|`NON`|0 = Pas de fuite détectée<br/>Pas 0 = Fuite détectée| 
|Info/Humidité|`NON`|%| 
|Info/Porte<br/>Info/Fenêtre<br/>(même traitement)|`NON`|**Si pas inversé :**<br/>pas 1 = Pas de contact (ouvert)<br/>1 = Contact (fermé)<br/>**Si inversé :**<br/>pas 1 = Contact (fermé)<br/>1 = Pas de contact (ouvert)| 
|Info/Sabotage|`NON`|**Si pas inversé :**<br/>1 = Pas de sabotage<br/>0 = Sabotage<br/>**Si inversé :**<br/>0 = Pas de sabotage<br/>1 = Sabotage<br/><br/>*à ajouter à un équipement existant*<br/>*Pas seule commande d'un équipement*| 
|Info/Choc|`NON`|Générique (Eve Seulement)|
|Info/Pression|`NON`|Générique (Eve Seulement)|
|Info/Son (dB)|`NON`|Générique (Eve Seulement)|
|Info/Détecteur CO|`NON`|0 = CO normal<br/>1 = CO anormal|
|Info/CO2 (ppm)|`NON`|PPM|
|Info/UV|`NON`|Générique (Eve Seulement)|
|Info/Générique|`NON`|Valeur <64 charactères<br/>avec Unité indiquée ou pas<br/>(Eve Seulement)| 
|Action/Générique|`NON`|Type "Défaut"<br/>uniquement<br/><br/>Comme un Bouton poussoir|
|Info/Pluie (accumulation)|`NON`|Générique (Eve Seulement)|
|Info/Vent (direction)|`NON`|Générique (Eve Seulement)|
|Info/Vent (vitesse)|`NON`|Générique (Eve Seulement)|

Status d'équipements
----------
Ces types génériques s'ajoutent à un équipement, ils ne peuvent pas être seuls dans un équipement.

|Type générique  | Obligatoire | Valeurs possibles |
|---------------|:----------------:|----------------|
|Info/Actif|`NON`|0 = inactif<br/>1 = actif|
|Info/Online|`NON`|0 = hors ligne<br/>1 = en ligne|
|Info/Defectueux|`NON`|0 = non<br/>1 = oui|

*Des exemples de configurations sont disponibles à la fin de la documentation*

Pour valider, il faut aller dans la configuration du plugin et relancer le démon Homebridge en cliquant sur "(Re)Démarrer".

![demon-homebridge](../images/demon-homebridge.png)

Ajout de Jeedom dans HomeKit
===========================

Il existe plusieurs applications sur l'appstore compatibles HomeKit. L'application "Maison" d'Apple sera utilisée pour la rédaction de la documentation.

![app-domicile](../images/app-domicile.jpg)

Le pont peut être inclus manuellement en entrant ou scannant le code PIN et en sélectionnant le pont ou automatiquement en scannant le QR code.

Ajout du pont par QR code
-------------------------

Pour ajouter le pont dans Homekit, il suffit de scanner le QR code avec l'application "Appareil photo".  Une notification est affichée en haut de l'écran. Il suffit de cliquer dessus et le pont est inclus automatiquement dans Homekit. 

![qr-code](../images/qr-code.png)
![qr-code1](../images/qr-code1.png)
![qr-code21](../images/qr-code21.png)

>Comme expliqué plus haut dans la doc, Homebridge n'est pas reconnu officiellement par Apple. Un message indique que l'accessoire n'est pas certifié, il faut valider l'inclusion en cliquant sur "Poursuivre l'ajout".

Le pont est maintenant intégré dans Homekit.

Ajout manuel du pont
-------------------

L'inclusion de Jeedom dans HomeKit, se fait en ouvrant l'application "Maison" et en cliquant sur "Ajouter un accessoire". 

![home-1](../images/home-1.jpg)


>Dans l'exemple, le domicile s'appelle "Test". Son nom peut être modifié en allant dans les réglages de l'application.

Il faut scanner le code PIN et sélectionner le pont à inclure. Le pont Jeedom sera intégré à Homekit

![home-2](../images/home-2.jpg)
![home-3](../images/home-3.jpg)
![home-4](../images/home-4.png)


>Le code PIN peut être également rentré manuellement en cliquant sur "Code absent ou impossible à scanner ?"

>Les plateformes et accessoires supplémentaires doivent être inclus manuellement (pas via le QRcode)

>Il n'est pas possible d'inclure le pont Jeedom sur plusieurs appareils IOS. Pour utiliser Homebridge sur plusieurs appareils IOS, il suffit de partager le domicile en suivant la procédure suivante :

![partage](../images/partage.png)

Rangement des accessoires dans HomeKit
====================================

Les accessoires doivent être rangés correctement dans HomeKit. Il faudra créer des pièces pour y intégrer les accessoires.


>Les pièces dans Jeedom ne sont pas importées dans Homebridge. Ceci n'est pas dû à Jeedom mais à la gestion des pièces par Apple.

Le premier accessoire à "ranger" est le pont Jeedom. Il faut sélectionner la pièce où il sera installé. Si elle n'existe pas, il faudra la créer en cliquant sur "Créer". Ensuite, il faut définir le nom de la nouvelle pièce. Il est également possible de lui attribuer un fond d'écran dédié. Pour finaliser la création de la pièce, il faut cliquer sur "Enregistrer".

![home-5](../images/home-5.jpg)
![home-05](../images/home-05.jpg)
![home-051](../images/home-051.jpg)

Maintenant, il ne reste plus qu'à ranger tous les accessoires dans les différentes pièces.

![home-052](../images/home-052.jpg)


>La fonction "Inclure dans les favoris" permet d'afficher l'accessoire dans la page principale de l'application

![home-053](../images/home-053.jpg)

**Les accessoires doivent être "rangés" un par un. Si il y en a beaucoup, cette partie prendra du temps**.

La documentation complète de l'application "Maison" d'Apple est disponible à cette adresse : [https://support.apple.com/fr-fr/HT204893](https://support.apple.com/fr-fr/HT204893){:target="_blank" rel="noopener"}.

Installer des Plugins Pour Homebridge
=====================================

>Attention : réservé aux utilisateurs avancés et qui comprennent l'anglais.

Il arrive parfois que les types génériques ne suffisent pas pour intégrer votre équipement car celui-ci n'a pas un comportement **générique** mais vraiment **spécifique** ou bien encore qu'il n'existe pas de plugin dans jeedom pour l'intégrer, dans ces cas là, vous pouvez passer par un "*Plugin pour homebridge*".

>**Attention vocabulaire** : vous l'aurez compris, on risque vite de s'emmêler les pinceaux dans les termes plugins... de quel plugin parle-t-on ? Pour jeedom ? Pour homebridge ? Donc la dénomination suivante a été choisie :

* ***Plugin pour homebridge*** : module s'ajoutant à homebridge pour se connecter à votre équipement.
* ***Plugin homebridge*** : le plugin jeedom qui s'appelle homebridge installé sur jeedom via le Market.
* ***Plugin Jeedom xxx*** : un plugin xxx installé sur jeedom via le Market (ou autre)

En effet, le logiciel homebridge a été conçu de manière modulaire et vous pouvez ajouter à celui-ci des modules (plugins) qui se connectent directement à vos équipements (un exemple est le *plugin pour homebridge* nommé homebridge-caméra-ffmpeg qui est déjà intégré par les dépendances et permet d'importer vos camera du *plugin jeedom caméra*). Un autre exemple sont les plugins homebridge-gsh et homebridge-alexa (pré-installés également) qui sont un peu différents des autres, vous pouvez consulter le [Tutoriel pour homebridge-gsh sur Communauté](https://community.jeedom.com/t/tuto-homebridge-et-google-smart-home/13855){:target="_blank" rel="noopener"}.

![schema partiel](../images/partialSchema.png)

Première Méthode
----------------

Pour ajouter un *plugin pour homebridge*, il faut d'abord trouver le plugin qui vous convient... pour ce faire il faut faire une recherche dans cette liste : [http://www.homebridge.io](http://www.homebridge.io){:target="_blank" rel="noopener"} puis dans "Find a plugin" ( il y en a des centaines !!). Vous en trouverez peut être plusieurs, comparez les et regardez ceux qui ont été mis à jour récemment, ceux qui sont toujours actifs, ceux qui ont les fonctionnalités que vous désirez. 
![findAPlugin.png](../images/findAPlugin.png)

Une fois que vous avez trouvé celui qui vous convient, il faut aller dans la configuration du *plugin homebridge* et cliquer sur le bouton "Gérer les *plugins pour Homebridge*". ![manageHomebridgePlugins](../images/manageHomebridgePlugins.png) 

Le début est déjà noté (puisque tous les *plugins pour homebridge* commencent par le mot homebridge-), ajoutez donc le reste du nom du plugin derrière le homebridge- deja existant et cliquer sur "Installer".

![installPlugin](../images/installPlugin.png)

Première étape effectuée ;-) sur la page github du *plugin pour homebridge* que vous avez trouvé, il indique probablement une commande de type npm install ... **ne la faite pas !**, cette première étape l'a faite pour vous :-) (certains indiquent aussi comment installer homebridge, vous vous doutez que c'est déjà fait aussi...)

![noNPM](../images/noNPM.png)

Seconde étape on va devoir donner la configuration du *plugin pour homebridge*... sur leur github, la plupart des plugins indiquent une structure json de configuration, il faut la recopier dans les **Plateformes supplémentaires** ou **Accessoires supplémentaires** que vous trouverez dans la configuration du plugin homebridge.

![platformAccessories](../images/platformsAccessories.png)

Il est possible que le *plugin pour homebridge* ne soit pas une plateforme mais un accessoire

![thisIsAccessory](../images/thisIsAccessory.png)![thisIsPlatform](../images/thisIsPlatform.png)

Dans ce cas là, il faut l'ajouter dans les **Accessoires supplémentaires**

>Attention, il faut recopier uniquement l'objet platform (un objet commence par { et terminé par }), pas tout le tableau platforms (avec s !!). (Idem avec accessories et accessory)

![onlyPlatform](../images/onlyPlatform.png)![onlyAccessory](../images/onlyAccessory.png)

>Attention, si vous avez déjà d'autres plateformes (ou accessoires), il faut les séparer par le caractère \| (qui s'appelle pipe).

![pipe](../images/pipe.png)

>Attention, le format json est assez difficile à écrire, recopiez bien les " et les , à la fin des lignes etc !!! Un validateur vous aidera.

![notValid](../images/notValid.png)

Une fois copié, il faut l'adapter à votre système... modifier des logins/pass ou des clés ou des ip's etc... (je ne peux pas vous aider pour cette partie... chaque *plugin pour homebridge* a sa propre spécificité... il faut bien lire la marche à suivre sur le github du plugin en question...). 

Quand c'est fait vous pouvez sauvegarder et relancer le démon... et prier ;-) non, en fait il faut regarder dans le log homebridge_daemon qui vous indiquera s'il y a des erreurs (normalement les lignes commenceront avec le nom du plugin entre crochets...). 

![logEx](../images/logEx.png)

Si vous avez des erreur, c'est généralement un problème de mot de passe ou de clé ou d'ip... vérifiez vos donnees et le github pour voir comment les obtenir. Si vous ne résolvez toujours pas vous pouvez faire un post dans communauté avec le tag **#plugin-homebridge** pour que je regarde si tout me semble cohérent ... si c'est cohérent il est fort probable que je vous redirige vers le github du *plugin pour homebridge* en question afin de leur poser des questions (en anglais...). **(Vous comprendrez que je ne peux pas faire le support pour des centaines de plugins développés par plein de gens dans le monde...)**

Si tout se passe bien, voilà vous avez configuré votre *plugin pour homebridge* ! Enjoy ;-)

Seconde Méthode (avec en partie l'interface Config-UI-X)
--------------------------------------------------------

Depuis peu, l'interface **Config-UI-X** a été ajoutée au *plugin homebridge*, celle-ci est accessible via le bouton suivant :

![configuixButton](../images/configuixButton.png)

Le plugin peut aussi s'installer via l'onglet "Plugins" de cette interface, vous recherchez dans la barre supérieur :

![cuixPlugins](../images/cuix-plugins.png)

Et cliquez sur "installer".

![pluginEx](../images/pluginEx.png)

Une fois le *plugin pour homebridge* installé, soit il ne le prévoit pas de Réglages (dans ce cas, il faut utiliser la première méthode, à la main)

![manualPlugin](../images/manualPlugin.png)

soit celui-ci prévoit un bouton "Réglages" pour vous aider à le configurer (malheureusement en anglais pas encore traduisible) :

![pluginExOK](../images/pluginExOK.png)

Une fois que vous avez terminé la configuration cliquez sur Enregistrer en bas de cette fenêtre.

![enregistrer](../images/enregistrer.png)

Attention, pour l'instant la configuration (le fichier config) de cette interface n'est pas prise en compte, il faut copier la plateforme ou l'accessoire manuellement dans les plateformes (ou accessoires) supplémentaires pour que ça soit pris en compte.

![whatToCopy](../images/whatToCopy.png) -> ![accCopy](../images/accCopy.png)

Il vous reste à "**Sauvegarder les changements**" de la plateforme ou l'accessoire et **relancer le démon** (voir première méthode)

*(Je dois encore trouver le moyen de régénérer correctement la partie pour jeedom si vous la modifiez et la cassez via cette interface pour le permettre...)*

Troubleshooting
=================

Support
-------
**Merci de passer par le forum, de créer *un* sujet par demande et de lire les autres sujets s'ils ressemblent au votre (ceux créés après la sortie de ce plugin, c'est logique :-))**

Point important si multi-prise/multi-relay
------------------------------------------

>Les références vers l'état dans les actions sont primordiales dans le cas où vous avez un équipement avec des états semblables multiples (multi-prise, multi-relay) !! Sinon pas de lien entre l'état et ses actions liées possible.

Pour un "virtuel" : 

![RefEtat](../images/reference-etat.png)

Pour un accessoire physique (Dimmer 2 de Fibaro par exemple) : 

![Dimmer](../images/ref2.png)

FAQ
----

**-> Le pont Homebridge n'apparaît pas dans l'application Maison !**

>Vérifiez que le statut du démon Homebridge est sur OK.

![demon-homebridge.png](../images/demon-homebridge.png)

>Pour inclure votre Jeedom dans HomeKit, via une application compatible (par exemple Maison ou Eve), vérifiez que votre appareil iOS est connecté au même réseau que votre Jeedom. (Il ne peut y avoir **aucun routage** entre jeedom et votre appareil iOS)

![config-pluginhb](../images/config-pluginhb.png)

**-> Le démon Homebridge ne veut pas démarrer !**

>Vérifiez que vous disposez de la dernière version des dépendances. En cas de doute, il est possible de les réinstaller en cliquant sur "Relancer". Si la réinstallation des dépendances ne fonctionne pas ou indique une erreur dans le log des dépendances, cliquez sur "Réparer et Réinstaller".

![dependances-homebridge](../images/dependances-homebridge.png)

**-> Mon équipement n'apparaît pas dans Homebridge !**

>Vérifiez que la case "Envoyer à Homebridge" est cochée dans la configuration de la pièce du plugin Homebridge.

**-> La case "Envoyer à Homebridge" est bien cochée mais mon équipement n'apparaît toujours pas !**

>Vérifiez dans la configuration de votre équipement que celui-ci est activé, et dans une pièce.

<br/>

>Vérifiez que les types génériques sont bien configurés. Chaque équipement envoyé à Homebridge doit avoir au moins un type générique "Etat".

![ypegelumi](../images/ypegelumi.png)

**-> J'ai mon Homebridge qui n'exécute pas les commandes !**

>Il faut bien mettre à jour le plugin. Vérifiez le type générique de la commande.

**-> J'ai bien le retour d'état d'un équipement mais impossible de le piloter !**

>Vérifiez que les types génériques sont bien configurés. Il doit y avoir une cohérence entre les types. Si vous avez le type "Info Lumière Etat", vérifiez que les actions sont de types "Action / Lumière Bouton On" etc... Voir aussi la référence à l'état (le point important ci-dessus)

**-> Le message "sans réponse" apparaît dans l'application Maison ou Eve**

![sans-reponse](../images/sans-reponse.png)

1. Si vous n'avez pas de concentrateur HomeKit (iPad ou Apple TV), vérifiez que vous êtes connecté au même réseau que votre Jeedom. (Pas de routage)
2. Vérifiez que le démon est activé. Si ce n'est pas le cas, redémarrez le.
3. Relancez votre box.
4. Si malgré tout vous avez toujours ces états, lancez une réparation.
5. Si le problème n'est pas réglé, vous avez un problème réseau, veillez à activer IGMP Snooping, le multicast et mDNS sur tout le trajet entre Jeedom et votre iDevice et votre AppleTV/HomePod. Aucun routage entre ces trois périphériques n'est toléré.

>Beaucoup d'informations se trouvent dans les logs, le prochain chapitre vous expliquera comment les analyser.

Interprétation des LOGS Homebridge
-----------------------------------

<pre><code>----
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 1 (111)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Accessoire visible, pas coché pour Homebridge
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ KO : Accessoire Ignoré
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>

>L'Accessoire 1 est visible mais la case "Envoyer vers Homebridge" n'est pas cochée. L'accessoire ne sera donc pas ajouté dans Homebridge.

<pre><code>----
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 2 (222)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ Nouvel accessoire (Accessoire 2)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ OK : Ajout de l'accessoire (Accessoire 2)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>
ou
<pre><code>----
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 2 (222)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] │ OK :  Mise à jour de l'accessoire (Accessoire 2)
[Mon Jul 17 2017 19:35:08 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>

>L'Accessoire 2 est visible et la case "Envoyer vers Homebridge" est cochée. L'accessoire sera donc ajouté dans Homebridge.

<pre><code>----
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 3 (333)
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] [WARN] Pas de type générique "Info/Prise Etat"
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ Accessoire sans Type Générique
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] │ KO : Accessoire Ignoré
[Mon Jul 17 2017 19:45:27 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>

>L'Accessoire 3 est visible et la case "Envoyer vers Homebridge" est cochée. Mais il n'y a pas de type générique "Etat" (ou celui-ci n'est pas visible). L'accessoire ne sera donc pas intégré dans Homebridge. Pour corriger ce problème, ajoutez le type générique "Info / Prise Etat" à l'accessoire (ou cochez la case "visible").

<pre><code>----

[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] ┌──── Maison > Accessoire 4 (444)
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] [WARN] Pas de type générique "Info/Lumière Etat" ou "Info/Lumière Couleur"
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] [WARN] Pas de type générique "Action/Prise Bouton On" ou reférence à l'état non définie sur la commande On
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] │ Nouvel accessoire (Accessoire 4)
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] │ OK : Ajout de l'accessoire (Accessoire 4)
[Mon Jul 17 2017 19:49:49 GMT+0000 (UTC)] [Jeedom] └─────────
----</code></pre>

>Il y a une incohérence entre les types génériques. Les types "actions" ne correpondent pas au type "info". Pour corriger le problème, modifiez les types génériques de l'accessoire en gardant une cohérence entre les types actions et info.

<pre><code>----
HAP Warning: Characteristic E863F129-079E-48FF-8F27-9C2605A29F52 not in required or optional characteristics for service 00000080-0000-1000-8000-0026BB765291. Adding anyway.
----</code></pre>

>Cet avertissement peut être ignoré.

<pre><code>----
sh: 1: homebridge: not found
----</code></pre>

>Les dépendances Homebridge ne sont pas installées ou certains fichiers sont manquants. Cliquez sur "Relancer"

![dependances-homebridge](../images/dependances-homebridge.png)


Exemple de configuration
=========================

Lumière
-------

Type d'accessoire : Dimmer 2 de Fibaro (Z-Wave)

![lumiere](../images/lumiere.png)

Type d'accessoire : Double contact de Nodon (EnOcean)

![lumiere-2](../images/lumiere-2.png)

Si les deux contacts sont utilisés, copier-coller les types génériques On-1 sur On-2, Off-1 sur Off-2 et Etat-1 sur Etat-2.

Température et hydrométrie
---------------------------

Type d'accessoire : Sonde Oregon (RfxCom) et Xiaomi Aqara

![temperature](../images/temperature.png)

Détecteur d'ouverture
----------------------

Type d'accessoire : Détecteur Fibaro (Z-Wave)

### Fenêtre #

![fenetre](../images/fenetre.png)

Si un capteur de température est utilisé, mettre "Info / Température" sur le nom de la commande Température.

### Porte #

![porte](../images/porte.png)

Si un capteur de température est utilisé, mettre "Info / Température" sur le nom de la commande Température.

Détecteur de fuite
------------------

Type d'accessoire : Détecteur Fibaro (Z-Wave)

![fuite](../images/fuite.png)

Détecteur de fumées
--------------------

Type d'accessoire : Détecteur Fibaro (Z-Wave)

![fumee](../images/fumee.png)

Volets roulants
----------------- 

Type d'accessoire : Détecteur Fibaro FGR-222 (Z-Wave)

![volet](../images/volet.png)

Porte de garage
-----------------

Type d'accessoire : Aeotec - Contrôleur de porte de garage (GEN5) (Z-Wave)

![garage](../images/garage.png)

Interrupteur programmable
-----------------------

### Interrupteur programmable multi-valeur #

Type d'accessoire : NODON Interrupteur mural Z-Wave Plus

![bouton](../images/bouton.png)

La tableau ci dessus indique les valeurs renvoyées par l'interrupteur pour chaque type d'appuie. Il faudra reporter les valeurs dans les paramètres du plugin.

![tg-inter](../images/tg-inter.png)

Voici le résultat dans l'app maison : 

![inter01](../images/inter01.png)
![inter02](../images/inter02.png)

Type d'accessoire : Bouton simple Click XIAOMI Aquara

![bouton-xiaomi](../images/bouton-xiaomi.png)

### Interrupteur programmable binaire #

Ce type générique possède 3 options (Simple click, long click et double click). Il faut que l'accessoire possède une info par type générique. Cette action doit être binaire.

Type d'accessoire : NODON Interrupteur mural ENOCEAN

L'interrupteur enocean de NODON, possède 4 informations (bt1, bt2, bt3 et bt4). Chaque information est de type binaire : 

![enocean](../images/enocean.png)

Voici les paramètres pour cet accessoire : 

![tg-bouton02](../images/tg-bouton02.png)

Homebridge va créer 1 accessoires mais avec 4 boutons :

![bt01](../images/bt01.png)

Type d'accessoire : EDISIO interrupteur 4 boutons : 

Cet accessoire possède 2 actions par bouton mais avec 2 ID binaires différents (1 ID par action).

![edisio](../images/edisio.png)

Voici les paramètres pour cet accessoire : 

![edisio02](../images/edisio02.png)

Homebridge va créer 1 accessoires, avec 4 boutons et 2 actions par boutons :

![edisio03](../images/edisio03.png)

Bouton poussoir 
------------------------------------------------

Ce type générique est utilisé par des accessoires qui ne nécessites pas de retour d'état. Le bouton poussoir est le parfait exemple. 
Dans cet exemple, un simple appui sur le bouton poussoir permet de lancer un script (avec le plugin script).

Le Bouton poussoir sera crée à l'aide du plugin virtuel.

![BP](../images/bp.png)

Voici les paramètres pour cet accessoire : 

![TGBP](../images/tgbp.png)

Dans l'application Maison, le Bouton poussoir sera représenté comme un interrupteur. Un appui dessus permet le lancement du script et l'interrupteur repasse à OFF (0) tout seul.

>Les commandes de camera (Zoom, Dézoom, Haut, Bas, Gauche, Droite, Présets) et les Action/Générique (de type "Défaut") sont automatiquement créées comme des boutons poussoir.

Virtuel
--------

Type d'accessoire : Interrupteur bistable avec le plugin virtuel

![virtuel](../images/virtuel.png)

![virtuel-tg](../images/virtuel-tg.png)

Caméra
------

Homebrige prend en charge les caméras.

![camera2.](../images/camera2.png)

En touchant la capture de la caméra souhaitée, elle s'affiche en plein écran et en live !

![camera3](../images/camera3.png)

Suivant les configurations matérielles, la qualité de la transmission peut varier. Par exemple, sur un NUC gen7 core i7, c'est quasiment du live ! La latence est très faible.

### Notification Photo # 
Celles-ci peuvent afficher une notification lorsqu'un mouvement est détecté par un capteur de présence. 

![notif](../images/notif.jpg)

**Avant iOS 13** : Il fallait que la caméra et le capteur soient configurés dans la même pièce et que les notifications du capteur soient activées.

**Depuis iOS 13** : Le capteur de mouvement doit faire partie du même équipement. Pour contourner ce problème, il faut :
1. Ajouter *"motion":true,* dans le **json de votre camera** comme dans l'exemple (Cela va créer un détecteur de mouvement et un interrupteur "virtuels" dans votre caméra. En actionnant l'interrupteur, le détecteur intégré à la caméra s'active.).
2. Créer une **Automation** dans Maison pour activer l'interrupteur de la camera si votre détecteur de mouvement Jeedom est activé.
3. **Activer les notifications** dans la Caméra (roue crantée > Notification).
4. Faire déclencher votre détecteur de mouvement Jeedom, vous avez une notification

<pre><code>
{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Camera-Salon",
	 "motion":true,
         "videoConfig":{
            [...]
         }
      }
   ]
}
</code></pre>

> Plus d'informations (en anglais) ici : [Wiki Homebridge-Camera-FFMPEG](https://sunoo.github.io/homebridge-camera-ffmpeg/automation/switch.html)

### Exemples de configuration # 

Les caméras décrites ci-dessous ont été testées. Elles sont donc fonctionnelles dans Homebridge.

L'intégration des caméras se fait via la bouton rouge "Plateforme Homebridge supplémentaire".

![plateforme-hb](../images/plateforme-hb.png)

Il suffira ensuite d'ajouter les caméras configurées depuis le menu "Maison" de l'application "Maison" : sélectionner le bouton "+", puis "Ajouter un accessoire". Il faut alors scanner le code PIN Homebridge du plugin et sélectionner la caméra à ajouter (Attention, il ne faut pas scanner le QR Code sinon le message "Accessoire déjà ajouté" apparaîtra et l'ajout ne sera donc pas possible).

>Depuis homebridge-camera-ffmpeg > 2.0.0 les cameras sont ajoutées automatiquement, plus besoin de faire l'ajout manuel !!!

### Foscam C1 #

>Cette caméra pose problème à cause d'une taille de pixel non conforme, il est donc quasi impossible de la faire fonctionner correctement, elles est déconseillée !

<pre><code>{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Camera-Salon",
         "videoConfig":{
            "source":"-rtsp_transport tcp -i rtsp://login:password@xxx.xxx.xxx.xxx:554/videoMain",
            "stillImageSource":"-i http://192.168.1.121:88/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30,
            "vcodec": "h264"
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Foscam C1 V2 # 

>Cette caméra pose problème à cause d'une taille de pixel non conforme, il est donc quasi impossible de la faire fonctionner correctement, elles est déconseillée !

<pre><code>{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Son nom",
         "videoConfig":{
            "source":"-rtsp_transport tcp -i rtsp://login:password@xxx.xxx.xxx.xxx:Portrtsp/videoMain",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx:Port/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Foscam FI9821P #

<pre><code>{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"son nom",
         "videoConfig":{
            "source":"-rtsp_transport tcp -i rtsp://login:password@xxx.xxx.xxx.xxx:Port/videoMain",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx:Port/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Foscam FI9803 V3 #

<pre><code>{
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Son nom",
         "videoConfig":{
            "source":"-rtsp_transport tcp -i rtsp://login:password@xxx.xxx.xxx.xxx:Portrtsp/videoMain",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx:Port/cgi-bin/CGIProxy.fcgi?cmd=snapPicture2&usr=login&pwd=password",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30
         }
      }
   ]
}</code></pre>

### wanscam rtsp HW0043 #

<pre><code>{
 "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Camera-Arrière",
         "videoConfig":{
            "source":"-rtsp_transport tcp -i rtsp://login:password@xxx.xxx.xxx.xxx:554/1",
            "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx/web/tmpfs/snap.jpg",
            "maxStreams":2,
            "maxWidth":1280,
            "maxHeight":720,
            "maxFPS":30,
            "vcodec": "h264"
         }
      }
   ]
}</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### Dlink DCS-5020L #

<pre><code>{
  "platform": "Camera-ffmpeg",
  "cameras": [
	{
	  "name": "Camera Cellier",
	  "videoConfig": {
		"source": "-f mjpeg -i http://login:password@xxx.xxx.xxx.xxx/mjpeg.cgi",
		"stillImageSource": "-f mjpeg -i http://login:password@xxx.xxx.xxx.xxx/image/jpeg.cgi",
		"maxStreams": 2,
		"maxWidth": 640,
		"maxHeight": 480,
		"maxFPS": 30,
		"vcodec": "h264"
	  }
	}
  ]
}
</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra.

### DCS-932L #

<pre><code> {
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Camera Garage1",
         "videoConfig":{
            "source":"-i http://login:password@xxx.xxx.xxx.xxx:port/video.cgi",
 "stillImageSource":"-i http://login:password@xxx.xxx.xxx.xxx:port/image.jpg",
           "maxStreams":5,
     "maxWidth": 1280,
      	"maxHeight": 720,
"vcodec": "h264_omx",
      "maxFPS":30
         }
      }
   ] 
} 
</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra. Merci à gui59169 pour l'intégration de cette caméra.

###  Synology Surveillance Station #

<pre><code> {
   "platform":"Camera-ffmpeg",
   "cameras":[
      {
         "name":"Camera-Salon",
         "videoConfig":{
            "source":"-rtsp_transport tcp -i rtsp://login:password@xxx.xxx.xxx.xxx:554/Sms=CAMID.unicast",
            "stillImageSource":"-rtsp_transport tcp -i rtsp://login:password@IP:554/Sms=CAMID.unicast -updatefirst",
            "maxStreams":2,
            "maxWidth":2688,
            "maxHeight":1520,
            "maxFPS":20,
            "vcodec": "h264"
         }
      }
   ]
}
</code></pre>

Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP de la caméra, login par le login de connexion à la caméra et password par le mot de passe de connexion à la caméra. Merci à mguyard pour l'intégration de cette caméra.

Dans Surveillance Station, clic droit sur la caméra et puis choisir "Share streaming Path"

### Netatmo Welcome #

Cette caméra deviendra officielement compatible HomeKit courant 2018. 
Son intégration dans Homebridge est néanmoins possible.

<pre><code>{
	"platform": "Camera-ffmpeg",
	"cameras": [
		{
		"name": "Camera Name",
		"videoConfig": {
			"source": "-i http://xxx.xxx.xxx.xxx/Local_Access_Key/live/files/high/index.m3u8",
			"stillImageSource": "-i http://xxx.xxx.xxx.xxx/Local_Access_Key/live/snapshot_720.jpg",
			"maxStreams": 2,
			"maxWidth": 1280,
			"maxHeight": 720,
			"maxFPS": 30
			}
		}
	]
}</code></pre>


Remplacer les valeurs xxx.xxx.xxx.xxx par l'adresse IP la caméra et Local_Access_Key -> voir dans le plugin Caméra l'URL de capture /Local_Access_Key/live/snapshot_720.jpg.

![camera](../images/camera.png)

### Configurer plusieurs caméras (ou plateformes) #

Pour configurer plusieurs plateformes, il suffit de mettre une barre &#124; entre les deux configurations.
Pour configurer plusieurs caméras, il faut les placer toutes les deux dans le tableau "**cameras**" séparées par une virgule (ou par simplicité, dans une nouvelle platform: "Camera-ffmpeg", elles seront fusionnées automatiquement.

<pre><code>{
  "platform": "Camera-ffmpeg",
  "cameras": [
	{
	  "name": "Cellier 1",
	  "videoConfig": {
		"source": "-f mjpeg -i http://login:password@adresseIP/mjpeg.cgi",
		"stillImageSource": "-f mjpeg -i http://login:password@adresseIP/image/jpeg.cgi",
		"maxStreams": 2,
		"maxWidth": 640,
		"maxHeight": 480,
		"maxFPS": 30,
		"vcodec": "h264"
	  }
	},{
	  "name": "Salon 1",
	  "videoConfig": {
		"source": "-i http://adresseip/xxxxxxx/live/files/high/index.m3u8",
		"stillImageSource": "-i http://adresseIP/xxxxxx/live/snapshot_720.jpg",
		"maxStreams": 2,
		"maxWidth": 1280,
		"maxHeight": 720,
		"maxFPS": 30
	  }
	}
  ]
}
|
{
    "platform": "Alexa",
    "name": "Alexa",
    "username": "....",
    "password": "...."
}</code></pre>

**Cela est également valable pour toute autre plateforme comme le thermostat NEST, alexa ou google smarthome par exemple.**

**Si vous avez un &#124; quelque part dans votre plateforme, celui-ci peut être donc confondu avec une séparation de plateforme, dans ce cas, il faut le remplacer par [pipe]**

### Migration des caméras dans homebridge-camera-ffmpeg > 2.0.0 #

Depuis la dernière version du plugin homebridge-camera-ffmpeg, les caméras s'affichent automatiquement dans maison sans besoin de les ajouter manuellement dans maison.  Néanmoins, si vous les aviez déjà ajoutées manuellement, vous allez avoir des doublons.  Voici la procédure pour détecter l'ancienne caméra et la supprimer de Maison :

![ProcedureMigrationCameras](../images/migrationCameras.png)

(cette procédure s'affichera également dans la configuration de homebridge si le démon est démarré et que vous n'avez pas encore cliqué sur "J'ai fait ces modifications, merci!")


Station météo NETATMO
---------------------

Type d'accessoires : Module intérieur, module extérieur et module intérieur additionnel. 

### Module intérieur #

![netatmo-1](../images/netatmo-1.png)

### Module extérieur #

![netatmo-2](../images/netatmo-2.png)

### Module intérieur additionnel #

![netatmo-3](../images/netatmo-3.png)

Représentation graphique dans Maison : 

![netatmo-4](../images/netatmo-4.png)

Représentation graphique dans Eve avec les courbes : 

![netatmo-5](../images/netatmo-5.png)

Type Générique Info/Générique
---------------------

Le type générique "Info/Générique" permet de faire remonter n'importe quelle valeur "info" de tout type dans Homebridge. **Quelques exemples sont décris dans ce chapitre.**

**L'information à remonter dans Homebridge ne doit pas dépasser 64 caractères.**

>**Seule l'application d'Elgato Eve est compatible avec ce type générique. Les équipements utilisant ce type générique n'apparaitront pas dans l'application Maison d'Apple.**

>**Les interactions avec Siri ainsi que les automations ne sont pas possibles avec ce type générique**

>**Il est n'est pas possible de renommer l'accessoire**


![custom-2](../images/custom-2.png)


### Utilisation avec le plugin vigilance méteo #

![custom-7](../images/custom-7.png)

![custom-6](../images/custom-6.png)

Plugins spécifiques
===================

Plugin "Thermostat"
---------------------

>Pour configurer le plugin "Thermostat", il faut se référer à la documentation du plugin à cette adresse : (https://doc.jeedom.com/fr_FR/plugins/wellness/thermostat/).

### Configuration #

Seuls les modes "Chauffer" et "Refroidir" sont à configurer. Il faut attribuer un mode du plugin "Thermostat" à un mode de HomeKit.

![thermostat](../images/thermostat.png)


### Présentation #

![thermostat1](../images/thermostat1.png)

* **A** : Température Cible ou Consigne : Température envoyée au plugin Thermostat (Passe en mode Auto sur Maison et Eve / Mode Aucun sur widget Thermostat)
* **B** : Température Ambiante : Température de référence pour le plugin Thermostat.
* **C** : Commande de modification de la Consigne A : Augmenter ou diminuer la température à l’aide du curseur. Cela aura pour action de modifier également le mode du chauffage E qui passera à AUCUN dans le dashboard Jeedom.
* **D** : Statut du thermostat retourné par le plugin Thermostat : Arrêté (ou Désactivé ou Eteint) (Rond vert dans Maison) / Chauffage (Rond Orange dans Maison) / Climatisation (Rond Bleu dans Maison).

* **E** : Mode Auto (dans Maison ou Eve) : correspond au mode Aucun dans Jeedom où le Plugin Thermostat décide de ce qu'il doit faire en fonction de la température qu'on lui envoie. Ce mode permet de régler une température cible via le curseur C

* **F** : Mode Clim / Refroidir : Mode customisé associé manuellement dans la configuration du Thermostat dans le Plugin Homebridge. Permet de lancer le mode associé dans le plugin Thermostat. (Repasse en mode AUTO, si une température cible est donnée)

* **G** : Mode Chauf / Chauffer : Mode customisé associé manuellement dans la configuration du Thermostat dans le Plugin Homebridge. Permet de lancer le mode associé dans le plugin Thermostat. (Repasse en mode AUTO, si une température cible est donnée)

* **H** : Eteint / Off : permet d'éteindre le thermostat.
* **I** : Verrouillage/Protection Enfants (uniquement dans Eve) : permet de verrouiller le thermostat. (modifié)

### Utilisation #

En cliquant sur "CHAUF" ou "Chauffer", on active le mode du thermostat associé. Idem pour "CLIM" ou "Refroidir".

Plugin "Alarme"
---------------

>La fonctionnalité de l'alarme dans Homebridge est compatible uniquement (pour l'instant) avec le plugin Jeedom "Alarme". Pour configurer le plugin "Alarme", il faut se référer à la documentation du plugin disponible à cette adresse : https://jeedom.github.io/plugin-alarm/fr_FR/.

**Ce mode fonctionne avec l'application d'Apple Maison et celle d'Elgato Eve.**

### Configuration #

Dans HomeKit, la fonction alarme est gérée suivant 4 modes : "Désactivée", "Nuit", "A distance" et "Domicile".

![alarme](../images/alarme.png)
![alarmeeve](../images/alarmeeve.png)

Le mode "Désactivé", inhibe l'ensemble des modes d'alarme du plugin "Alarme". Les actions de l'onglet "Désactivation OK" sont lancées (en fonction du mode de sortie).

![inhibe](../images/inhibe.png)

Les 3 autres modes, sont à définir dans la configuration du plugin Homebridge.


![configalarme](../images/configalarme.png)


>Le "mode Jeedom" correspond aux modes du plugin "Alarme".

![modealarme](../images/modealarme.png)

Il suffit d'affecter le "mode Jeedom" au mode Homebridge choisi.

### Utilisation #

Il suffit de cliquer sur l'icone "Alarme" dans l'application Maison.

![iconealarme](../images/iconealarme.png)

Et de sélectionner le mode.

![selmodealarme](../images/selmodealarme.png)

L'alarme est activée.

Sur le dashboard : 

![alarmeactive](../images/alarmeactive.png)

Sur l'application Maison : 

![alarmeactive2](../images/alarmeactive2.png)

Pour la désactiver, il suffit de sélectionner "Désactivée". Les actions définies dans la partie "Désactivation OK" du plugin "Alarme" vont s'exécuter.

![desactivationok](../images/desactivationok.png)

En cas de déclenchement de l'alarme, une notification apparaît sur le téléphone.

![alarmedeclanchee](../images/alarmedeclanchee.png)
![reinitialiseralarme](../images/reinitialiseralarme.png)

Pour la désarmer, il faut cliquer sur l'icône "Alarme" et sélectionner "Désactivée".


Les actions définies dans la partie "Réinitialisation" du plugin "Alarme" vont s'éxécuter.

![reinitialisation](../images/reinitialisation.png)


Plugin "Méteo"
---------------

Le plugin météo est compatible avec les applications Maison et Eve. Cependant, dans Maison, seules la température et l'humidité sont remontées. Dans Eve, l'ensemble des informations sont disponibles.

![config-meteo](../images/config-meteo.png)

Pour activer le plugin météo, il suffit de cocher la case "Envoyer à Homebridge". Le configuration se fait tout seule.

![meteo-eve](../images/meteo-eve.png)
![meteo-home](../images/meteo-home.png)

Plugin "Mode"
---------------------

le plugin mode est auto configuré par le plugin. 
![mode](../images/mode.png)

Dans l'app Maison, les modes sont représentés avec des interrupteurs. 

![modehk](../images/modehk.png)

Pour activer un mode, il suffit de basculer l'interrupteur sur ON sur le mode souhaité. L'interrupteur du mode précédent, passe automatiquement sur OFF. En basculant un mode actif sur OFF, le mode précédent repasse sur ON.

Les modes fonctionnent avec Siri. Dans l'exemple ci dessus, les noms des modes sont les suivants : 

* **1** : Je suis présent.
* **2** : Je suis absent.
* **3** : Nuit.

Le plugin, ajoute automatiquement le terme "mode" avant. Ce qui donne au niveau des interrupteurs : 
* **1** : Mode je suis présent.
* **2** : Mode je suis absent.
* **3** : Mode nuit.

Si dans le nom du mode d'origine contient déjà le terme "mode" (ou "modo" en espagnol), il n'est pas ajouté.

Pour activer le mode "je suis absent" il faut demander à Siri:  "Dis Siri, Active le mode je suis absent".

![modesiri](../images/modesiri.png)

>Certains modes ne fonctionneront pas avec Siri, le mode Nuit et le mode Jour par exemple. Si vous demandez à Siri d'activer le mode nuit, il activera Night Shift. Vous pouvez contourner ceci en demandant explicitement : "Dis Siri, active l'interrupteur Mode Nuit" ou en associant l'interrupteur à la Scène "Bonne nuit".


Changelog
=========
[Voir ici](changelog)
