# Liste des modules installés

php -m

## Trouver php.ini

php -i | grep "Loaded Configuration File"
php -i | grep php.ini

## Valeur d'un paramètre PHP

php -i | grep upload_max_filesize
