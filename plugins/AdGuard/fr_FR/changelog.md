---
layout: default
lang: fr_FR
title: Plugin AdGuard Home - Changelog
description: Changelog du plugin AdGuard Home
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour d'orthographe ou pour la compatibilité Jeedom V4

# 14/11/2022

- Fix internet block/unblock et rêgles personnalisées (sur versions v0.107.14+), update sur v0.107.17+
- Nécessite donc une version d'AdGuard v0.107.17 minimum !

# 04/11/2022

- Depuis v0.107.17, AdGuard supporte des nouveaux services (iCloud Private relay, etc). Cette version demande la liste des services à AdGuard et met à jour les commandes si besoin.

# 08/09/2022

- Ajout du service BiliBili disponible dans v0.107.12
- Plus d'erreur si version.json n'est plus dispo sur AdGuard (car bug de leur coté)

# 28/06/2022

- Ajout du protocol https pour ceux qui utiliseraient un proxy ou autre

# 08/04/2021

- Ajout de la version actuelle et nouvelle version dans les commandes. s'il y a une nouvelle version au moment de la mise à jour, adguard ne m'envoi pas l'ancien numero de version, il sera donc vide... mais dès que vous mettez à jour, il sera modifié et ensuite ça sera bon.
- Traduction anglaise & espagnole
- Fix Liens commandes vers action Bloquer internet via DNS

# 21/09/2021

- Fix si un équipement est déjà existant dans la meme pièce que le client et désactivé

# 15/09/2021

- Initialisation

