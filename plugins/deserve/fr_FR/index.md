---
layout: default
lang: fr_FR
title: Plugin Mérite
description: Documentation du plugin Mérite (deserve)
---

## Présentation

Le plugin **Mérite** est un sémaphore pour Jeedom. Chaque équipement, appelé « Méritant », possède un compteur et un but. Des scénarios ou des actions ajoutent des points (**Mérite**) ou en retirent (**Démérite**). Quand le compteur atteint le but, l'équipement devient méritant et ses actions méritantes s'exécutent. Quand il repasse sous le but, il ne l'est plus et ses actions déméritantes s'exécutent.

L'intérêt est de simplifier les scénarios. Au lieu d'écrire une condition qui doit connaître l'état de tous les éléments concernés, chaque scénario se contente d'ajouter ou de retirer ses points. Toute la logique de « ce qui se passe quand le seuil est franchi » est rassemblée à un seul endroit : l'équipement Méritant.

## Configuration du plugin

Le plugin n'a ni dépendance ni démon. Il suffit de l'activer.

## Configuration d'un équipement

Dans **Plugins → Automatisme → Mérite**, cliquez sur **Ajouter** et donnez un nom à votre Méritant.

### Paramètres généraux

- **Nom de l'équipement**, **Objet parent**, **Catégorie**, **Activer**, **Visible** : paramètres habituels de Jeedom.
- **Remise à zéro** : si cette case est cochée, le compteur repasse à 0 dès que le but est atteint, juste après l'exécution des actions méritantes. *Est Méritant* repasse alors aussi à 0, **sans** lancer les actions déméritantes. Chaque franchissement du but se comporte donc comme une impulsion, ce qui convient bien à un système de paliers ou de récompenses.
- **Où sont utilisées les commandes** : liste des scénarios, vues, designs, etc. qui utilisent les commandes de cet équipement.

### Actions Méritantes et Déméritantes

- Les **actions méritantes** s'exécutent quand le compteur **atteint ou dépasse** le but (*Est Méritant* passe de 0 à 1).
- Les **actions déméritantes** s'exécutent quand le compteur **repasse sous** le but (*Est Méritant* passe de 1 à 0).

Les actions ne s'exécutent qu'au **franchissement** du but. Ajouter des points à un équipement déjà méritant ne relance pas les actions méritantes.

Les actions sont regroupées en **évènements** :

- Chaque évènement a une **condition** facultative. Si elle est fausse, l'évènement entier est ignoré. Si elle est laissée vide, l'évènement s'exécute toujours.
- Chaque évènement contient une ou plusieurs **actions**. Pour chacune, on peut choisir une commande action (bouton liste) ou un mot-clé de scénario : message, variable, scénario, attendre, alerte… (bouton mot-clé).
- Une action peut être désactivée sans être supprimée en décochant sa case.
- Les évènements sont exécutés dans l'ordre affiché, et les actions de chaque évènement aussi. Les actions peuvent être réordonnées avec la poignée.

## Commandes

| Commande | Type | Description |
|---|---|---|
| **Valeur** | info numérique | Valeur actuelle du compteur (jamais négative). |
| **Nécessite** | info numérique | But à atteindre (100 par défaut). |
| **Est Méritant** | info binaire | 1 si Valeur ≥ Nécessite, 0 sinon. |
| **Mérite** | action slider | Ajoute la valeur du slider au compteur. |
| **Démérite** | action slider | Retire la valeur du slider au compteur (minimum 0). |
| **Doit Nécessiter** | action slider | Change le but (minimum 1). |
| **Gagner** | action | Met directement le compteur à la valeur du but. |
| **Mise à zéro** | action | Remet le compteur à 0. |

Remarques :

- Mérite et Démérite sans valeur, ou avec 0, ne font rien.
- Les sliders du widget vont de 0 à 100. Depuis un scénario, on peut envoyer une valeur plus grande (par exemple *Doit Nécessiter* à 150).
- Si on baisse le but en dessous de la valeur actuelle, la valeur est ramenée au nouveau but. Elle n'est pas restaurée si on remonte le but ensuite.
- *Mise à zéro* et *Démérite* déclenchent les actions déméritantes si l'équipement était méritant. *Gagner* déclenche les actions méritantes s'il ne l'était pas encore.
- *Est Méritant* peut aussi servir de déclencheur ou de condition dans vos scénarios.

## Exemples d'utilisation

### Délestage électrique

On veut éviter que trop de gros consommateurs tournent en même temps : four, lave-linge, sèche-linge, lave-vaisselle, borne de recharge.

- Créez un Méritant « Gros consommateurs » avec un but à **3**.
- Pour chaque appareil, un petit scénario fait **Mérite 1** quand sa puissance dépasse un seuil et **Démérite 1** quand elle redescend. On peut pondérer : la borne peut compter pour 2.
- Actions méritantes : mettre la borne en pause, couper le chauffe-eau, envoyer une notification.
- Actions déméritantes : tout réactiver.

Chaque appareil ne gère que son +1 et son −1. Ajouter un appareil ne demande pas de modifier les autres scénarios.

### Compteur d'entretien

Pour le filtre d'une VMC, d'un adoucisseur ou d'une hotte, ou le bac d'un aspirateur robot.

- Le but est le seuil d'entretien (par exemple 50 cycles).
- À chaque cycle, un scénario fait **Mérite**, éventuellement pondéré : cycle court +1, cycle long +3.
- Actions méritantes : notification « Pensez à changer le filtre ». *Est Méritant* reste à 1 tant que l'entretien n'est pas fait, ce qui en fait un rappel persistant sur le dashboard.
- Après l'entretien, un clic sur **Mise à zéro** depuis le dashboard.

### Points de mérite

- Chaque tâche accomplie donne des points (**Mérite 10**, **Mérite 20**…) via un bouton, une interaction ou un scénario.
- Un oubli constaté retire des points (**Démérite 5**).
- But à 100, avec **Remise à zéro** cochée : chaque palier atteint déclenche une récompense (allumer une prise, envoyer une notification…).
- Un scénario hebdomadaire fait **Mise à zéro** pour repartir de zéro.

## Logs

Le log `deserve` indique, en niveau **info**, chaque franchissement du but. En niveau **debug**, il détaille aussi chaque changement de valeur, chaque condition évaluée et chaque action exécutée.
