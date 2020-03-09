# 09-03-2020

* Non réécriture du schédule du cron à la mise à jour, si vous l'avez modifié, il restera.

# 19-01-2020

* contournement si deux commandes ont le même nom, renommage _1 _2 etc
* contournement du problème du controller 5.12 : lorsqu'un wifi est absent, quelques minutes après, il réapparait comme présent et étant cablé (on ignore maintenant le changement de présence s'il revient dans un autre état (était wifi -> cablé ou était cablé -> wifi)) + on ne met pas à jour le last_seen pour essayer d'avoir une valeur cohérente dans cette commande
* changement du format du last_seen pour etre utilisable avec time_diff dans un scénario

# 19-12-2019

* contournement si deux périphérique ont le même nom, renommage _mac
* correction orthographe

# 29-11-2019

* fix version_incompatible (+ autres) dans cron_execution 
* syncro selectif par type de device
* nouvelles images fournies avec le controleur (rescan nécessaire + relancer dépendances pour supprimer les anciennes)
* images différentes pour clients wifi et cablés
* commandes rxWAN et txWAN sur la gateway pour les débits en bps

# 15-10-2019

* compatibilité V4 (design)

# 09-09-2019

* version jeedom minimale : 3.3.24 (pour compatibilité V4)

# 24/07/2018

- Initialisation

