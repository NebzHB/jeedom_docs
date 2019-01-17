Présentation XiaomiTalk
=======================

Ce plugin permet de faire parler vos passerelles xiaomi Mijia.

>Attention, ce plugin est compatible avec la version xiaomi Mijia de la passerelle et PAS la version HomeKit (Aqara) !

![comparaison](../images/xiaomiTalk_screenshot1.png)

Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Si vous voullez aller plus vite, vous pouvez lancer les dépendances ou attendre ~5min.

Configuration des équipements 
=============================

La configuration des équipements xiaomiTalk est accessible à partir du menu
plugins puis Multimedia. Vous retrouvez ici :

-   un bouton pour chercher les passerelles sur votre réseau (pas de routage, même réseau obligatoire)

-   un bouton pour créer un équipement manuellement

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements

-   enfin en dessous vous retrouvez la liste de vos équipements

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

**Onglet Equipement** :
-----------------------

-   **Nom de l’équipement** : Nom de votre équipement

-   **Activer** : Permet de rendre votre équipement actif

-   **Visible** : Le rend visible sur le dashboard

-   **Objet parent** : Indique l’objet parent auquel appartient l’équipement

-   **Ip de la passerelle** : L'ip de la passerelle en question

-   **Token** : Token (et pas Password) de la passerelle. Ainsi que la possiblité de vérifier s'il est correct.

![Voici comment le récupérer](../images/xiaomiTalk_screenshot2.gif)

-   **Volume par défaut** : Le volume est un pourcentage (sans le signe pourcent). Utilisé si le champ Options ne donne pas d'autre information.
-   **Langue par défaut** : La langue a utiliser si le champ Options ne donne pas d'autre information.
-   **Jingle par défaut** : Choisir le jingle qui doit être joué avant le message. Utilisé si le champ Options ne donne pas d'autre information.
-   **Système de TTS par défaut** : GoogleTTS est recommandé. Utilisé si le champ Options ne donne pas d'autre information.

**Onglet Commandes** :
----------------------

-   Il existe une seule commande **Parle**. Elle contient deux champs, un champ Options et un Message.

**Utilisation du Widget ou dans un Scénario** :
-----------------------------------------------

-	Exemple d'options pour le champ Options : *volume=10,jingle=non,tts=picotts,lang=en_US*
>**Important** : Les options doivent être séparées par des virgules sans importance d'ordre. Aucune option n'est obligatoire, si elle n'est pas présente, la valeur de l'équipement sera utilisée.
-	Champ *Options* - choix valides :
-	**volume=** pourcentage du volume, valeur comprise entre *0* et *100* (sans le signe %)
-	**jingle=** *oui* ou *non* pour utiliser le jingle par défaut (ou pas) ou *sncf*, sinon des valeurs entre *10-13* pour les sons intégrés à la passerelle
-	**tts=** choisir entre *picotts* ou *googletts* (Recommandé) ou *jeedom* (Expérimental)
-	**lang=** choisir parmis les langues suivantes : *fr_FR* ou *en_US* ou *en_GB* ou *de_DE* ou *es_ES* ou *it_IT*

-	Champ *Message* : Ecrivez le texte qui doit être prononcé par votre passerelle
