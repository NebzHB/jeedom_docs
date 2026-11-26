---
layout: default
lang: fr_FR
title: Plugin AdGuard Home - Changelog
description: Changelog du plugin AdGuard Home
---
Si rien n'est indiqué, il s'agit probablement d'une petite mise à jour d'orthographe ou pour la compatibilité Jeedom V4.x

# Changelog

## En Beta
- Nouveau widget pour l'équipement AdGuard Home (dashboard et mobile), inspiré du tableau de bord d'AdGuard Home : protection avec menu des durées de pause et décompte, statistiques, pastilles cliquables (filtrage, sécurité de navigation, contrôle parental, recherche sécurisée, internet bloqué)
- Nouveau widget pour les équipements Client (dashboard et mobile) : internet autorisé ou bloqué avec bouton, pastilles cliquables (paramètres généraux, filtrage, sécurité de navigation, contrôle parental, recherche sécurisée, services bloqués généraux), identifiants et services bloqués
- Widgets : réglages en interrupteurs avec infobulle, actions intégrées sur une ligne (services, groupes, règles, identifiants, test de domaine avec son résultat, maintenance), mise à jour d'AdGuard Home depuis le badge du widget. Voir la [documentation beta](index-beta#widgets-en-beta)
- Widgets : services bloqués affichés en icônes, sur le serveur comme sur les clients
- Liste des services avec icônes, recherche et services rangés sous leur groupe ; choisir un groupe bloque ou débloque tout le groupe
- Confirmation avant de couper internet, désactiver le filtrage ou le contrôle parental, bloquer ou débloquer tous les services, et avant les actions de maintenance (cache DNS, filtres, statistiques, mise à jour d'AdGuard Home) : option « Confirmer l'action » de Jeedom, avec dans le widget une question propre à chaque action
- Widgets : largeur minimale de 320 px sur le dashboard avec mise en page qui s'adapte, pleine largeur en mobile
- Widgets : hauteur automatique selon le contenu, avec une option « Hauteur du widget : Fixe » sur l'équipement pour garder celle du mode édition
- Nouvelle info « Pause restante » : temps restant (en secondes) avant la reprise de la protection
- Nouvelles actions « Vider le cache DNS » et « Mettre à jour les filtres »
- Nouvelle action « Tester un domaine » (et l'info « Résultat du test de domaine ») sur l'équipement AdGuard Home, et « Tester un domaine pour ce client » sur les clients
- Nouvelles actions « Bloquer un groupe de services » et « Débloquer un groupe de services », globales et par client (AdGuard Home v0.107.68 minimum)
- Le planning des services bloqués défini dans AdGuard Home n'est plus effacé quand on bloque ou débloque un service depuis Jeedom
- Recherche sécurisée (globale et client) : seul l'état activé/désactivé change, les moteurs choisis dans AdGuard Home sont conservés (Ecosia compris)
- Sécurité de navigation et contrôle parental utilisent les appels de l'API récente d'AdGuard Home, avec repli sur les anciens appels pour les versions plus anciennes
- « Mettre à jour les filtres » et « Mise à jour AdGuard » attendent jusqu'à 120 s la réponse d'AdGuard Home (avant, la commande échouait et « En Ligne » passait à 0)
- Fiabilité : les actions affichent un message clair quand AdGuard Home ne répond pas, quand le client est introuvable ou quand la règle est vide, au lieu d'échouer en silence. Les règles personnalisées ne peuvent plus être effacées par erreur, et bloquer deux fois internet ne crée plus de doublon
- Correction des clients dont le nom contient un tiret
- Correction de la détection des erreurs réseau (PHP 8)
- La modification d'un client n'envoie plus que les champs modifiables à AdGuard Home
- Correction de la faute « globlaux » dans les noms des commandes client (« Utiliser les services bloqués globaux »)
- Textes d'aide des commandes traduits

## 26-11-2026
- Compatible avec AdGuard Home v1.0.0

## 12-11-2026
- Configuration requière d'être administrateur

## 30-01-2025
- Traduction des noms des commandes
- Correction d'un warning php si pas de user rules
- (Merci @TomiTomas) : Ajout du temps de désactivation de la protection (comme dans AdGuardHome)

## 07-10-2024
- Ajout Bouton Communauté pour obtenir une aide plus façilement

## 12-08-2024
- Traductions et mise à jour des traductions en Anglais, Allemand, Espagnol, Italien, Portugais

## 11-09-2023
- Version v0.107.37 obligatoire !
- Modification des blocked services à partir de la version v0.107.37

## 24-05-2023

- Modifications pour les nouveaux éléments de l'api dans la v0.107.28 (protection enabled + safesearch)
- pas de possibilité de choisir le moteur de recherche de la protection safesearch pour l'instant (est-ce nécessaire ??)
- pas de possibilité de définir un timing pour la désactivation de la protection pour l'instant (est-ce nécessaire avec jeedom ? car on peut réactiver via scénario ou autre...)
- Fix de la commande Update
- Encryption de vos mots de passes AdGuard dans la BDD de Jeedom
- **Nécessite donc une version d'AdGuard v0.107.28 minimum !**


## 14-11-2022

- Fix internet block/unblock et rêgles personnalisées (sur versions v0.107.14+), update sur v0.107.17+
- Nécessite donc une version d'AdGuard v0.107.17 minimum !

## 04-11-2022

- Depuis v0.107.17, AdGuard supporte des nouveaux services (iCloud Private relay, etc). Cette version demande la liste des services à AdGuard et met à jour les commandes si besoin.

## 08-09-2022

- Ajout du service BiliBili disponible dans v0.107.12
- Plus d'erreur si version.json n'est plus dispo sur AdGuard (car bug de leur coté)

## 28-06-2022

- Ajout du protocol https pour ceux qui utiliseraient un proxy ou autre

## 08-04-2021

- Ajout de la version actuelle et nouvelle version dans les commandes. s'il y a une nouvelle version au moment de la mise à jour, adguard ne m'envoi pas l'ancien numero de version, il sera donc vide... mais dès que vous mettez à jour, il sera modifié et ensuite ça sera bon.
- Traduction anglaise & espagnole
- Fix Liens commandes vers action Bloquer internet via DNS

## 21-09-2021

- Fix si un équipement est déjà existant dans la meme pièce que le client et désactivé

## 15-09-2021

- Initialisation

