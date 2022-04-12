slow_query_log=1
slow_query_log_file=/var/log/mysql/...log
long_query_time=2 (en seconde)

query_cache_time = 0
innodb_buffer_pool_size = 2G 
innodb_buffer_pool_size = 1 instance par Giga de innodb_buffer_pool_size



Recherche du mot "test" dans tous les fichiers de toutes les sous répertoires
grep -R "test" .


Voir le détail d'un index (avec ses cardinalités):
    SHOW INDEX FROM tickets;

Mettre à jour les statistiques d'une table
    ANALYZE TABLE tickets;