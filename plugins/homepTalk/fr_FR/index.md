---
layout: default
lang: fr_FR
title: Plugin homepTalk
description: Documentation du plugin homepTalk
---

Présentation HomepTalk
=======================

Ce plugin permet de faire parler en TTS vos Apple Homepod.

>**Important** : Vos homepods ne doivent pas être protégés par mot de passe :

![config](../images/homepTalk-homekitConf.gif)

Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Si vous voullez aller plus vite, vous pouvez lancer les dépendances ou attendre ~5min.

>**Important** : L'installation des dépendances prend beaucoup de temps !!! soyez patient...

Configuration des équipements 
=============================

La configuration des HomePod est accessible à partir du menu
plugins puis Multimedia. Vous retrouvez ici :

-   un bouton pour chercher les homepods sur votre réseau (pas de routage, même réseau obligatoire)

-   un bouton pour créer un équipement manuellement (utilisez la découverte de préférence, sinon pas de support)

-   (si plusieurs homepods) un bouton pour créer un groupe

-   un bouton pour afficher la configuration du plugin

-   un bouton qui vous donne une vue d'ensemble de tous vos équipements

-   enfin en dessous vous retrouvez la liste de vos équipements

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

**Onglet Equipement** :
-----------------------

-   **Nom de l’équipement** : Nom de votre homepod

-   **Activer** : Permet de rendre votre équipement actif

-   **Visible** : Le rend visible sur le dashboard

-   **Objet parent** : Indique l’objet parent auquel appartient l’équipement

-   **Adresse IP** : L'ip du homepod en question

-   **Volume** : Le volume est un pourcentage (sans le signe pourcent). Utilisé si le champ Options ne donne pas d'autre information.
-   **Langue** : La langue a utiliser si le champ Options ne donne pas d'autre information.
-   **Multiplicateur de vitesse** : Valeur pour accélérer ou ralentir le flux de la voix, valeur de 0.5 à 2 (avec décimale point). Utilisé si le champ Options ne donne pas d'autre information.
-   **Système de TTS** : GoogleTTS est recommandé. Utilisé si le champ Options ne donne pas d'autre information.

**Onglet Commandes** :
----------------------

Il existe une commande **Parle**. Elle contient deux champs, un champ Options et un Message.

**Utilisation du Widget ou dans un Scénario** :
-----------------------------------------------

Exemple d'options pour le champ *Options* : *volume=10,vitesse=1.2,tts=picotts,lang=en_US*
>**Important** : Les options doivent être séparées par des virgules sans importance d'ordre. Aucune option n'est obligatoire, si elle n'est pas présente, la valeur de l'équipement sera utilisée.

Champ *Options* - choix valides :
-	**volume=** pourcentage du volume, valeur comprise entre *0* et *100* (sans le signe %).
-	**vitesse=** multiplicateur de vitesse, valeur comprise entre 0.5 et 2 (avec décimales possibles et un POINT !) pour parler plus vite ou plus lentement.
-	**tts=** choisir entre *picotts* (pas compatible mini+ ou rPI1/2) ou *googletts* (Recommandé) ou *jeedom* (Expérimental) ou *osx* (via SSH) ou *voicerss* (Besoin d'une clé API) ou *ttswebserver*.
- **cache=** permet avec une valeur *non* ou *no* de ne pas sauvegarder le texte dans le cache du plugin (utile si vous utilisez des variables dans le texte ou des conditionnelles ou des alternatives.)
-	**lang=** choisir parmis les langues suivantes : *fr_FR* ou *en_US* ou *en_GB* ou *de_DE* ou *es_ES* ou *it_IT*.
- **voix=** si *tts=osx* alors choisir parmis les voix suivantes : *Thomas* ou *Aurelie* ou *Audrey* (si installées)  (testé sur Mojave)
- **voix=** si *tts=ttswebserver* alors choisir parmis les voix listées dans l'interface (dépendant de ce que vous avez installé)
- **voix=** si *tts=voicerss* alors vous pouvez aussi ajouter la voix choisie en option (sinon c\'est *Bette*) : *Bette* ou *Iva* ou *Zola* ou *Alex*

>Sous Debian Jessie (deb8), les messages qui font plus de 100 caractères et qui utilisent *googletts* passeront en *picotts* à cause d'une limitation de *avconv* (le convertisseur audio). Sous Debian Stretch (deb9), ces messages seront fractionnés en parties de 100 caractères et joués à la suite pour votre plus grand plaisir !

Champ *Message* : Ecrivez le texte qui doit être prononcé par votre homepod.
Vous pouvez utiliser ces quelques astuces :

```
[Bonjour|Salut], ça va ? => Donnera soit “Bonjour, ça va ?” ou “Salut, ça va ?”
```

```
{(test) ?vrai:faux} => exemple : {(#[Maison][Météo][Température Max]# < 12) ?il va faire froid:il va faire beau !}
```

>Pour *tts=osx* vous devez avoir activé SSH sur votre mac dans Préférences système > Partages > Sessions Distantes et vérifiez que vous avez bien activé toutes les voix Personnalisées de votre langue dans Préférences système > Accessibilité > Parole  (testé sur Mojave et sur le plugin Jailbreak)

>Pour *tts=voicerss* vous avez besoin d'une clé API (gratuite pour moins de 350 TTS/jour) : http://www.voicerss.org/login.aspx

>Pour *tts=jeedom* vous pouvez écrire #idDeVotreSon# qui correspond à l'id de votre son dans le *plugin Officiel Son* dans le message et il sera lu (seul)


Il existe des commandes **Son natif ---**. Permet de jouer les sons natifs (trouvés dans le firmware Homepod par des Hackeurs).

Il existe des commandes **Son ---**. Permet de jouer les sons ajoutés au plugin.

Il existe une commande **Stop**. Elle joue en fait un son silencieux vide au volume par défaut de l'équipement.

**FAQ** :
---------

1. Quand je fait parler mon homepod avec le plug-in, ça coupe la musique
>Oui normal, le plug-in utilise AirPlay pour envoyer la voix sur votre Homepod. Et je n'ai pas accès à l'information de ce qui était en train d'être joué avant pour le remettre.
2. Quand je fais parler mon homepod avec le plug-in, ça change le volume actuel de mon homepod
>Oui normal, je n'ai aucun moyen de connaître le volume actuel de votre Homepod, d'où vous devez définir un volume par défaut dans le plug-in 
3. Je voudrais jouer de la voix sur un autre périphérique AirPlay, c'est possible ?
>Peut-être... mais je ne supporte rien d'autre que homepod, si vous y arrivez tant mieux, venez le partager sur le forum ! *Il est possible que certains haut-parleurs nécessitent la première fois de jouer une musique en airplay2 avec votre iDevice, pour ensuite lancer une voix (on dirait que les Sonos par exemple, nécessitent une "initialisation" de airplay2 via un périphérique Apple la première fois...). Mais normalement les fois suivantes ce n'est plus nécessaire (sauf reboot peut-être ?)*
4. Pouvez vous ajouter mon son personnel de canard qui croasse au plugin ?
>Non, par contre en utilisant le plug-in officiel "Sons", c'est possible ! Indiquez tts=jeedom dans les options et #idDeVotreSon# dans le message
5. Il y a un délai un peu trop long quand j'enchaîne deux sons
>Malheureusement, impossible de faire autrement, le homepod prend une seconde et un peu plus pour lâcher le flux AirPlay du premier son... et seulement après le deuxième son est généré.
6. Les homepod en groupe ne jouent pas en même temps ou pas du tout
>Vérifiez les paramètres NTP de votre jeedom, vous devez avoir l'heure exacte !
7. Pourquoi ça va plus vite le deuxième fois que je fais prononcer la même phrase ?
>Car le plug-in garde en cache 30 jours les messages pour une utilisation plus rapide la prochaine fois. Cette durée est prolongée de 30 jours à chaque utilisation (lecture). Vous pouvez supprimer ce comportement avec l'option cache=non (utile si variables dans le texte)
8. Pour le système de TTS OSX, dois-je laisser tout le temps mon mac allumé ?
>A chaque fois que vous prononcez une nouvelle phrase avec ce système TTS oui, pour les déjà prononcées (dans les 30 jours) pas besoin, il y a le cache! Ou alors une vm *Hackintosh*. Vous avez également la possibilité d'utiliser le plugin Jailbreak sur un iPad/iPhone Jailbreaké
9. J'ai envie de voix plus fun ou mieux faites
>Je vous invite à tester le plug-in ttswebserveur, il vous permet d'utiliser un android (ou une vm android) pour générer la voix, il existe plein de voix très expressives gratuites ou à bas prix chez *Voxygen*
10. Les mêmes phrases toujours prononcées c'est un peu monotone.
>Vous pouvez utiliser les alternatives :
```
[Bonjour|Hello|Salut] comment vas-tu ?
```
>Et les conditions :
```
Il fait #[domicile][meteo][temperature]# degrés, {(#[domicile][meteo][temperature]# >25) ? Il fait chaud : bonne journée }
```
>Mais évidemment, le cache a moins de chance d'exister dans ce cas...
11. Je parle une autre langue que celles proposées par le plug-in.
>Aucun problème, contactez moi je le ferai un plaisir de l'ajouter, il faudra juste espérer que votre système TTS préfèré la supporte....
12. Parfois je n'entends pas le debut de la phrase, on dirait que c'est coupé
>Ca peut arriver quand vous n'avez plus utilisé le homepod depuis un certain temps, je suppose qu'il passe en veille... la solution consiste a ajouter un mot (comme "Bonjour" ou "Cher Tim") avant le message important ou encore mieux faire un "Stop" juste avant de jouer votre phrase (ca joue un petit son silencieux).
13. Le plugin est compatible avec les (anciennes) bornes Airport Express modèle A1264 en Airplay 1
>Même si elle ne seront pas maintenues car obsolètes, pour info vous pouvez faire parler Jeedom sur une borne Aiport A1264. En firmware 7.8.1, il faut ajouter un équipement manuel avec l'adresse IP de votre borne sur votre réseau (exp. 192.168.1.X) et indiquer le port n°5000.

