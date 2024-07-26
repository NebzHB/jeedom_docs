---
layout: default
lang: fr_FR
title: Plugin HomeWizard Energy
description: Documentation du plugin HomeWizard Energy
---

Ce plugin permet de monitorer et exécuter quelques actions sur vos équipements HomeWizard Energy.

Configuration du plugin 
=======================

Après installation du plugin, il vous suffit de l’activer. Si vous voullez aller plus vite, vous pouvez lancer les dépendances ou attendre ~5min.
Une fois les dépendances terminées, le démon démarrera dans les 5min également (ou vous pouvez le lancer à la main).

Le démon va détecter les périphériques HomeWizard Energy sur votre réseau automatiquement lors de son démarrage (multicast utilisé, routage non supporté !). Ensuite il continuera d'écouter les messages de vos équipements, ceux-ci doivent envoyer quand ils se connectent.  Pour forcer une découverte sur le réseau, relancez le démon (normalement pas nécessaire).

Configuration des équipements 
=============================

La configuration des équipements HomeWizard Energy est accessible à partir du menu
plugins puis Objets connectés. Vous retrouvez ici :

-   un bouton pour afficher la configuration du plugin

-   un bouton Santé qui vous donne une vue d'ensemble de tous vos équipements à un moment donné

-   enfin en dessous vous retrouvez la liste de vos équipements HomeWizard Energy

En cliquant sur un de vos équipements vous arrivez sur la page
configuration de votre équipement comprenant 2 onglets, équipement et
commandes.

**Onglet Equipement**
---------------------

-   **Nom de l’équipement** : Nom de votre équipement

-   **Objet parent** : Indique l’objet parent auquel appartient l’équipement

-   **Activer** : Permet de rendre votre équipement actif

-   **Visible** : Le rend visible sur le dashboard

-   **Catégrorie** : Indique la catégorie à laquelle appartient l’équipement

-   **Adresse IP** (lecture seule) : L'adresse IP envoyée par votre équipement (non modifiable car les équipements sont découverts)

**Onglet Commandes**
--------------------

Il existe de nombreuses commandes, elles sont différentes en fonction du type d'équipement. Toutes ne sont pas affichées par défaut. Vous pouvez les renommer, les afficher ou non et les réorganiser. Vous pouvez aussi attribuer un widget au choix. Tout est standard.

Les noms viennent directement de l'équipement.

La valeur est affichée en temps réel et est modifiée en temps réel.

**Activer l'api locale dans l'application HomeWizard**
=============

Afin que votre équipement soit visible dans le plugin il est NECESSAIRE d'activer l'API Locale sur celui-ci.

1. Ouvrez l'application HomeWizard sur votre téléphone
2. En haut à droite appuyez sur l'engrenage
3. Allez dans "Mesures"
4. Appuyez sur votre équipement
5. Tout en bas dans les Paramètres, activez "API Locale"
6. **Relancez le démon car l'activation/désactivation alors que le démon est lancé peut le planter**.

**Compatibilités**
==================

**En attente de tests (mais devraient être fonctionnel)**
----------------------

-    Compteur d'eau (HWE-WTR) (Seulement si branché en USB)
-    Wi-Fi kWh Meter (1 phase) (HWE-KWH1)
-    Wi-Fi kWh Meter (3 phases) (HWE-KWH3)

**Compatibles**
---------------

-    Compteur P1 (HWE-P1)
-    Prises connectées wifi (HWE-SKT)

**NON-Compatibles**
---------------

-    Compteur d'eau WIFI (HWE-WTR) (Sur pile)
-    Energy Display (pas d'API)
