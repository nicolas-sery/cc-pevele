# Migration de la configuration (hors bdd) d'un centreon avec CLAPI.


## Utilisation clapi:

```
# centreon -u USER -p PWD -o OBJET -a ACTION
```

Avec pour paramètres:

* -u : Utilisateur identique que pour l'interface Web.
* -p : Le mot de passe.
* -o : Objet à superviser: poller, hôte, service ou template.
* -a : Action à réaliser: ajout, suppression, update

liens: Liste des actions: https://documentation-fr.centreon.com/docs/centreon/en/2.8.x/api/clapi/objects/index.html


## Commandes de base:

* Export de conf: centreon -u USER -p PWD -o OBJET -e > fichier_export.txt
* Import de conf: centreon -u USER -p PWD -o OBJET -i fichier_export.txt

note: L'import/export se réalise sur les hôtes et groupes d'hôtes, ainsi que les templates.
note: Ne réimporte pas les doublons.


todo: à vérifier pour les templates perso.



## liens:

http://www.sugarbug.fr/atelier/techniques/ihmweb/centreon/clapi/
