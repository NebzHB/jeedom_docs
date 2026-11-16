---
layout: default
lang: fr_FR
title: Plugin HomeWizard Energy - Changelog
description: Changelog du plugin HomeWizard Energy
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour d'orthographe, de librairie ou pour la compatibilité Jeedom V4

# En Beta
- Migration des équipements vers la nouvelle API v2 de HomeWizard, à la demande et équipement par équipement, avec un assistant qui vous montre où appuyer sur l'équipement et attend votre appui (bouton "Migration API v2"). Voir la [documentation beta](index-beta#migration-vers-lapi-v2)
- La page Santé indique l'API utilisée par chaque équipement
- Migration possible pour : Compteur P1, kWh Meters 1 et 3 phases. Pas encore proposée par HomeWizard pour l'Energy Socket, le compteur d'eau et l'Energy Display
- En API v2 la connexion est chiffrée et l'équipement envoie ses mesures en temps réel (websocket), avec retour automatique à l'interrogation régulière si besoin
- Les commandes sont renommées avec les noms de l'API v2, l'historique, les scénarios et les designs sont conservés. Retour à l'API v1 possible depuis l'assistant
- Exception pour les kWh Meters : les commandes d'index par tarif (`Total_power_import_t1_kwh`, `Total_power_export_t1_kwh`) ne sont plus mises à jour en API v2, utilisez les totaux
- Un nouvel équipement peut être ajouté directement en API v2, sans activer l'API Locale : il apparait à sa découverte et il suffit de l'autoriser par un appui sur son bouton (même assistant, rien à migrer)
- Support de la Plug-In Battery (HWE-BAT) : elle n'existe qu'en API v2, donc pas de migration, il suffit d'autoriser Jeedom par un appui sur son bouton (même assistant)
- Jeedom restauré sur une autre machine : le plugin le détecte, vous prévient dans le centre de messages et évite que les deux Jeedom se coupent mutuellement leurs autorisations API v2
- Pilotage du groupe de Plug-In Batteries depuis le compteur P1 ou le kWh Meter en API v2 : mode, charge, décharge, charge complète, et état du groupe
- Gestion des utilisateurs autorisés sur un équipement en API v2 (bouton Utilisateurs de l'assistant) : qui a accès, et suppression
- La commande Online suit maintenant les messages reçus : hors ligne après 3 cycles sans nouvelles de l'équipement, et dès que le démon est arrêté. Le ping reste utilisé toutes les 5 minutes pour les équipements silencieux
- La suppression d'un équipement en API v2 retire aussi l'autorisation de Jeedom sur l'équipement
- Widget du plugin (dashboard et mobile) : mesure principale, totaux, phases, état, mis à jour en direct. Actif d'office sur les nouveaux équipements, à cocher dans l'équipement pour les autres
- Réglages de l'équipement depuis Jeedom : cloud HomeWizard (activer / désactiver) et luminosité de la led d'état (API v2)
- Commandes Identifier (fait clignoter la led) et Redémarrer (Compteur P1 et kWh Meters en API v2)
- Types génériques Puissance et Consommation posés d'office, cohérents avec le plugin Homebridge
- Autorisation API v2 perdue (équipement réinitialisé, utilisateur supprimé) : une alerte dans le centre de messages, une seule fois par équipement, retirée quand l'autorisation est refaite
- Démon plus solide : une coupure courte d'un équipement en API v2 se répare en silence, une erreur imprévue ne l'arrête plus
- Images des kWh Meters HWE-KWH1 et HWE-KWH3, de la Plug-In Battery et du Temperature Humidity Meter (pas encore d'API pour ce dernier)
- La librairie homewizard-energy-api est maintenant installée depuis mon fork GitHub (relance des dépendances nécessaire)

# 12-11-2026
- Mise à jour de librairies (request, axios)
- Configuration et Ajax requièrent d'être administrateur
  
# 28-09-2026
- Ajout du dossier resources/node_modules aux exclusions de backup

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
