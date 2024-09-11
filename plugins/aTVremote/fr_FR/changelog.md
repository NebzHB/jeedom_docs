---
layout: default
lang: fr_FR
title: Plugin aTVRemote - Changelog
description: Changelog du plugin aTVRemote
---

# Changelog

## Bientot !!!
- Migration vers NodeJS 20

## 10/09/2024 - beta
- Mise à jour pour autoriser les mises à jour en debian > 12.0

## 29/08/2024 - beta
- Jeedom 4.4 Obligatoire
- Debian 11 Obligatoire

## 12/08/2024 - beta
- Traductions et mise à jour des traductions en Anglais, Allemand, Espagnol, Italien, Portugais

## 03/07/2024 - beta
- exclusion du venv pour le backup
- Ajout dans le market que Debian Buster (10) n'est plus supporté

## 05/04/2024 - beta
- Correction pour 4.4 sur le widget

## 14/09/2023 - beta
- ATTENTION MISE A JOUR NODEJS 18 en vue du 30 septembre : ne pas faire cette mise à jour avant cette date si vous avez d'autres plugins NodeJS, il est prévu que tous les plugins migreront le 30 Septembre, mais si vous mettez à jour avant, vous risque qu'ils ne fonctionnent plus d'ici là !!!

## 02/06/2023 - beta
- Ajout de la mise à jour de wheel avant installation du plugin
- Oublis dans les changelogs précédents : nouvelle version de la lib pour support du volume en temps réel

## 03/02/2023 - beta
- Support du Homepod 2 ajouté :)

## 16/08/2022 - beta

- 321 mises à jour, trop pour lister ici, c'est une beta donc voilà...

## 08/07/2022 - beta
- Mise à jour importante (oui je sais ça fait longtemps) :)
- Compatible uniquement Apple TV 4 et plus (les 3 j'en ai plus je peux pas vérifier et c'est pas la priorité !)
- Compatible uniquement Jeedom 4.2 et plus
- Compatible uniquement Debian Buster et plus (10+)
- Il FAUT supprimer vos AppleTv existantes et redécouvrir !
- Il FAUT réinstaller vos dépendances
- Le mode de fonctionnement a changé, il faut faire deux appairages (1 seul si atv 3) de l'apple TV en SSH (un pour airplay et l'autre pour des commandes avancées (vrai éteignage et pas combinaison de touches + possiblité plus tard de lancer certaines apps) (la commande à taper est visible dans l'équipement, copiez-collez-là dans SSH puis un code va s'afficher sur votre Apple TV, tapez-le dans l'invité de la commande et puis copiez la longue chaine affichée après "You may now use these credentials :" et collez-là dans l'équipement et sauvegardez.)
- **Pas necessaire de faire des retours de ceci ou cela fonctionne ou pas. on est au courant de tout ce qui fonctionne pas. Mais cette version est juste pour vous permettre d'avoir un minimum "vital"**
- Sur aTV4 et plus : creation des commandes « Lancer App xxxxx » qui permet de lancer les apps en question sur l’apple TV (appairage companion obligatoire !)

## 01/06/2022 - beta
- utilise nodejs 16

## 21/05/2020 - beta
Projet entièrement revisité !!
- Nouveau widget ! (Merci à @Wators)
- Démon pour quasi temps réel sur aTV4+
- Panel (Merci à @Wators)
- Plein de petites nouveautés à gauche et à droite et stabilisation de l'ensemble (Merci à @Wators)

Bugs connus :
- La fonction Repeat connait des problèmes, si OFF, la lecture s'arrette.
- Les états de repeat ne correspondent pas au états réels (décallage).

## 19/04/2020 - beta

- Revisite avec @Wators


## 23/08/2018 - beta

- Initialisation

