---
layout: default
lang: fr_FR
title: Plugin aTVRemote - Changelog
description: Changelog du plugin aTVRemote
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour d'orthographe ou pour la compatibilité Jeedom V4.x

# Changelog

## 28-11-2026 - beta
Nouveau démon en Python (bêta) : à choisir dans la configuration du plugin (Type de démon : Python), puis redémarrer le démon.
- Un seul programme qui garde une connexion avec chaque appareil : beaucoup moins de mémoire
- Volume, veille et fonctions disponibles reçus en temps réel : Jeedom n'interroge plus les appareils toutes les minutes
- Pochette récupérée par le démon dès le changement de morceau, une par appareil
- Volume des HomePod réglable même hors lecture
- Vraies erreurs des commandes : notification si une fonction n'est pas disponible avec la source en cours (ex. aléatoire avec Apple Music sur HomePod), erreur si l'appareil refuse
- Détection des appareils par le démon
- Appairage des Apple TV depuis Jeedom avec un assistant pas à pas (aussi sur mobile), plus besoin de SSH ; un seul bouton et un état global « Appairée / À appairer »
- Détection des Apple TV trop récentes pour pyatv, dont la nouvelle Apple TV 4K (gen 4) de 2026 (OS inconnu et aucune commande créée avant)
- Notification quand on clique sur un bouton alors que le démon est arrêté
- Documentation mise à jour

## 27-11-2026 - beta
Gros travail sur les widgets, surtout celui du HomePod :
- Mobile : le widget mobile reprend celui du Dashboard (il n'affichait plus rien)
- Fond flouté propre sur iPhone / iPad : plus de bords nets au chargement ni au changement de chanson
- Le style des widgets n'est plus gardé en cache par Safari après une mise à jour
- Écran tactile : plus de bouton grisé « collé » après un appui ; précédent / suivant restent grisés jusqu'au changement de chanson
- Nouveau panneau Info (bouton i) : pochette floutée en fond, titre / artiste / album sur une ligne avec défilement si trop long (l'option de défilement fonctionne maintenant aussi sous Safari)
- À côté de la pochette : animation de chargement après précédent / suivant ou quand l'appareil charge (20 s maximum), et indication quand le démon est arrêté
- Barre de progression sous la pochette et dans le panneau Info (au survol : position, durée, pourcentage et temps restant)
- Icônes en SVG, nettes sur les écrans Retina
- Textes du widget traduits (anglais, allemand, espagnol, italien, portugais) et widget utilisable au clavier et avec un lecteur d'écran
- Aléatoire / répétition grisés quand la source ne les accepte pas (ex. Apple Music lu directement sur le HomePod), avec 2 nouvelles infos : Aléatoire disponible / Répétition disponible
- Lien « Ouvrir dans Apple Music » dans le panneau Info quand le morceau vient d'Apple Music (nouvelle info Identifiant iTunes)
- Thème noir par défaut si le thème configuré n'existe plus
- Ménage : anciens templates mobile, images et code inutilisés supprimés
- Mise à jour des traductions et de la dépendance axios

## 11-11-2026
- retrait des artworks des backups, gain de place non négligable

## 30-10-2026
- plein de mise à jour depuis 2024 mais celle du jour permet de supporter les nouveaux HomePods Mini 2 sortis aujourd'hui et on gère même leurs nouvelles couleurs :)

## 05-11-2024
- Mise à jour de la lib pyatv

## 06-10-2024
- Forcer la réinstallation du venv pour le problème chacha
- retiré un warning en php 8

## 12-09-2024
- Migration vers NodeJS 20

## 10-09-2024 - beta
- Mise à jour pour autoriser les mises à jour en debian > 12.0

## 29-08-2024 - beta
- Jeedom 4.4 Obligatoire
- Debian 11 Obligatoire

## 12-08-2024 - beta
- Traductions et mise à jour des traductions en Anglais, Allemand, Espagnol, Italien, Portugais

## 03-07-2024 - beta
- exclusion du venv pour le backup
- Ajout dans le market que Debian Buster (10) n'est plus supporté

## 05-04-2024 - beta
- Correction pour 4.4 sur le widget

## 14-09-2023 - beta
- ATTENTION MISE A JOUR NODEJS 18 en vue du 30 septembre : ne pas faire cette mise à jour avant cette date si vous avez d'autres plugins NodeJS, il est prévu que tous les plugins migreront le 30 Septembre, mais si vous mettez à jour avant, vous risque qu'ils ne fonctionnent plus d'ici là !!!

## 02-06-2023 - beta
- Ajout de la mise à jour de wheel avant installation du plugin
- Oublis dans les changelogs précédents : nouvelle version de la lib pour support du volume en temps réel

## 03-02-2023 - beta
- Support du Homepod 2 ajouté :)

## 16-08-2022 - beta

- 321 mises à jour, trop pour lister ici, c'est une beta donc voilà...

## 08-07-2022 - beta
- Mise à jour importante (oui je sais ça fait longtemps) :)
- Compatible uniquement Apple TV 4 et plus (les 3 j'en ai plus je peux pas vérifier et c'est pas la priorité !)
- Compatible uniquement Jeedom 4.2 et plus
- Compatible uniquement Debian Buster et plus (10+)
- Il FAUT supprimer vos AppleTv existantes et redécouvrir !
- Il FAUT réinstaller vos dépendances
- Le mode de fonctionnement a changé, il faut faire deux appairages (1 seul si atv 3) de l'apple TV en SSH (un pour airplay et l'autre pour des commandes avancées (vrai éteignage et pas combinaison de touches + possiblité plus tard de lancer certaines apps) (la commande à taper est visible dans l'équipement, copiez-collez-là dans SSH puis un code va s'afficher sur votre Apple TV, tapez-le dans l'invité de la commande et puis copiez la longue chaine affichée après "You may now use these credentials :" et collez-là dans l'équipement et sauvegardez.)
- **Pas necessaire de faire des retours de ceci ou cela fonctionne ou pas. on est au courant de tout ce qui fonctionne pas. Mais cette version est juste pour vous permettre d'avoir un minimum "vital"**
- Sur aTV4 et plus : creation des commandes « Lancer App xxxxx » qui permet de lancer les apps en question sur l’apple TV (appairage companion obligatoire !)

## 01-06-2022 - beta
- utilise nodejs 16

## 21-05-2020 - beta
Projet entièrement revisité !!
- Nouveau widget ! (Merci à @Wators)
- Démon pour quasi temps réel sur aTV4+
- Panel (Merci à @Wators)
- Plein de petites nouveautés à gauche et à droite et stabilisation de l'ensemble (Merci à @Wators)

Bugs connus :
- La fonction Repeat connait des problèmes, si OFF, la lecture s'arrette.
- Les états de repeat ne correspondent pas au états réels (décallage).

## 19-04-2020 - beta

- Revisite avec @Wators


## 23-08-2018 - beta

- Initialisation

