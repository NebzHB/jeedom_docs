---
layout: default
lang: fr_FR
title: Plugin HomeWizard Energy - Changelog
description: Changelog du plugin HomeWizard Energy
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour d'orthographe ou pour la compatibilité Jeedom V4

# 07-04-2025
- Correction d'un problème de ExpressJS 5. (Breaking change, changing "query parser" to "extended")

# 13-02-2025
- Correction des unités pour le compteur d'eau
- Correction d'un warning php
- Correction pour isHistorized
- Changement icone pomme pour éclair

# 09-01-2025
- Ajout du pid du démon dans le fichier daemon.pid dans le dossier temp du plugin
- Modification des traductions
- Meilleure gestion des coupures d'équipement, si l'équipement perd le wifi et revient il se réannonce sur mdns et on recrée proprement le lien sans doublon.
- Gestion du changement d'ip d'un équipement même s'il est conseillé de fixer l'ip dans votre DHCP
- Mise à jour dernière version d'Axios
- Début de la préparation pour l'API v2 qui est encore en beta et en cours de développement chez HomeWizard (très impatient, car elle devrait permettre de s'affranchir du polling et de recevoir les changements directement en websocket :)), qui plus est, elle devrait aussi permettre de gérer l'écran Energy Display !!! par contre il faudra faire un appairage en deux étapes avec le bouton présent sur l'équipement, donc je vous proposerai une migration manuelle vers la nouvelle API v2.

![image](https://github.com/user-attachments/assets/b1029333-9984-4f1e-be2b-edec6a60df61)


# 28-09-2024
- Correction d'une mauvaise detection des Compteurs 1 et 3 phases

# 12-09-2024
- Migration vers NodeJS 20

# 10-09-2024
- Mise à jour pour autoriser les mises à jour en debian > 12.0

# 29-08-2024
- Jeedom 4.4 Obligatoire
- Debian 11 Obligatoire

# 12-08-2024
- Ajout de logs
- Correction d'une erreur en anglais
- Traductions et mise à jour des traductions en Anglais, Allemand, Espagnol, Italien, Portugais

# 08-08-2024
- Traduction du plugin en anglais

# 08-2024
- Version initiale
