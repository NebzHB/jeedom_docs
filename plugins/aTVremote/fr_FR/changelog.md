---
layout: default
lang: fr_FR
title: Plugin aTVRemote - Changelog
description: Changelog du plugin aTVRemote
---

# 08/07/2022
- Mise à jour importante (oui je sais ça fait longtemps) :)
- Compatible uniquement Apple TV 4 et plus (les 3 j'en ai plus je peux pas vérifier et c'est pas la priorité !)
- Compatible uniquement Jeedom 4.2
- Compatible uniquement Debian Buster et plus (10+)
- Il FAUT supprimer vos AppleTv existantes et redécouvrir !
- Il FAUT réinstaller vos dépendances
- Le mode de fonctionnement a changé, il faut faire un appairage de l'apple TV en SSH (la commande à taper est visible dans l'équipement, copiez-collez-là dans SSH puis un code va s'afficher sur votre Apple TV, tapez-le dans l'invité de la commande et puis copiez la longue chaine affichée après "You may now use these credentials :" et collez-là dans l'équipement et sauvegardez.)
- **Pas necessaire de faire des retours de ceci ou cela fonctionne ou pas. on est au courant de tout ce qui fonctionne pas. Mais cette version est juste pour vous permettre d'avoir un minimum "vital"**

# 01/06/2022
- utilise nodejs 16

# 21/05/2020
Projet entièrement revisité !!
- Nouveau widget ! (Merci à @Wators)
- Démon pour quasi temps réel sur aTV4+
- Panel (Merci à @Wators)
- Plein de petites nouveautés à gauche et à droite et stabilisation de l'ensemble (Merci à @Wators)

Bugs connus :
- La fonction Repeat connait des problèmes, si OFF, la lecture s'arrette.
- Les états de repeat ne correspondent pas au états réels (décallage).

# 19/04/2020

- Revisite avec @Wators


# 23/08/2018

- Initialisation

