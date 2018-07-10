# Sommaire
1. [Hierarchie hôte - commands](#Hierarchie hôte - commands)
1. [Architecture de Centreon](#Architecture de Centreon)

<a name="Hierarchie hôte - commands"></a>
# Hierarchie hôte - commands

Centreon s'appuit sur des **templates** pour superviser les hôtes. Ces templates s'appuient sur des **services** et les ces services s'appuient sur des **commands**.

![centreon-01](images/2018-07-09_10-13-00_centreon-flux.png)

_Note_ : un hôte peut-être associé à plusieurs templates.

<a name="Architecture de Centreon"></a>
# Architecture de Centreon

Fonctionnement

L'installation de Centreon en standalone consiste à installer toutes les entités de Centreon sur une seule machine :

* L'interface web de Centreon
* La base de données (MySQL + RRD)
* Le moteur de supervision
* Le broker

Voici comment cette architecture se présente :

* Le serveur Apache est chargé d'héberger l'interface web de Centreon
* La base de données MySQL est chargée de stocker la configuration de Centreon, les informations de supervision ainsi que les données de performances
* Le moteur de supervision supervise le système d'informations
* Les informations de supervision sont envoyées via cbmod à Centreon Broker SQL
* Centreon Broker SQL est chargé d'insérer les données de supervision en base de données et de transmettre les données de performances à Centreon Broker RRD
* Centreon Broker RRD est chargé de générer les fichiers RRD (qui servent à générer les graphiques de performances)

![centreon-02](images/2018-07-09_10-28-00_centreon-flux.png)

Pour plus de détail sur les types d'architecture [voir la documentation de Centreon](https://documentation-fr.centreon.com/docs/centreon/fr/2.8.x/installation/architecture/03a.html).


