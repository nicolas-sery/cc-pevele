# Migration centreon même version.

-> Pré-requis sur le centreon cible:
* Version identique de centreon.
* Conf mySQL semblable.
* Arrêt de tous les services. (mysql compris)

-> Exportation et importation des bases:

```
# mysqldump -u root -p --all-databases > centreondb.sql
# mysql -u root -p < centreon.sql
```

-> Recréer l'utilisateur centreon dans la bdd:

```
# mysql -u root -p
> CREATE USER 'centreon'@'domain.com' IDENTIFIED BY PASSWORD 'XXXXXX';
> GRANT USAGE ON *.* TO 'centreon'@'domain.com' IDENTIFIED BY PASSWORD 'XXXXXX' WITH 
MAX_QUERIES_PER_HOUR 0
MAX_CONNECTIONS_PER_HOUR 0
MAX_UPDATES_PER_HOUR 0 MAX_USER_CONNECTIONS 0 ;
> GRANT ALL PRIVILEGES ON 'centstorage' .* TO 'centreon'@'domain.com' WITH GRANT OPTION;
> GRANT ALL PRIVILEGES ON 'centreon' .* TO 'centreon'@'domain.com' WITH GRANT OPTION;
> GRANT ALL PRIVILEGES ON 'centstatus' .* TO 'centreon'@'domain.com' WITH GRANT OPTION;
```

-> Relancer l'ensemble des services.

## Troubleshooting:


## Liens:

http://www.lolokai.com/blog/2015/03/23/importer-et-exporter-sa-configuration-avec-centreon-clapi/

https://alexnogard.com/centreon-migration-base-mysql-sql/

