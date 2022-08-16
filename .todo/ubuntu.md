# Liste des modules installés

php -m

## Trouver php.ini

php -i | grep "Loaded Configuration File"
php -i | grep php.ini

## Valeur d'un paramètre PHP

php -i | grep upload_max_filesize


/opt is for third-party applications that don't rely on any dependencies outside the scope of said package. /usr/local is for packages installed on this machine outside the scope of the distribution package manager.