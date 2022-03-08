
modifier les droits du répertoire en cours et de son contenu
    chmod 777 -R .

modifier les droits du contenu du répertoire en cours
    chmod 777 -R *

copier un répertoire et son contenu vers un autre répertoire
    cp repertoire1 repertoire2

copier le contenu d'un répertoire vers un autre répertoire
    cp repertoire1/ repertoire2

imprimer le nom de l'utilisateur en cours
    echo "${USER}" # print "utilisateur"
    sudo su
    echo "${USER}" # print "root"

extraire le chemin du répertoire à partir du chemin d'un fichier
    dirname /var/www/api/coucou

extraire le nom d'un fichier à partir du chemin de ce fichier
    basename /var/www/api/coucou

Recherche tous les fichiers et exécuter une commande pour chacun d'eux
    find /backup -name '*.sql.gz' -mtime +7 -exec rm {} \;

Boucler avec un séparateur
    local test="un deux trois
    quatre cing six"
    while IFS= read -r -a mots; do
        echo "${mots[0]} - ${mots[1]} - ${mots[2]}"
    done <<< "${test}"

    local test="un deux trois
    quatre cing six"
    while IFS= read -r mot1 mot2 mot3; do
        echo "${mot1} - ${mot2} - ${mot3}"
    done <<< "${test}"

Imprimer un texte avec une tabulation
    echo -e "tableName\tcolumnName\tcolumnValue\treferencedTableName"

Comment changer les permissions par défaut à la création d'un ficher ou d'un répertoire?
    umask

    The umask is the value that is subtracted from the 666 (rw-rw-rw-) permissions when creating new files, or from 777 (rwxrwxrwx) when creating new directories. For example, if the default umask is 002, new files will be created with the 664 (rw-rw-r–) permissions, and new directories with the 775 (rwxrwxr-x) permissions.

    To dispay the current value of umask, run the umask command without any options.

    r=4, w=2 and x=1

Comment fonctionnent les ACLs?

    reset (Récursif) des ACLs
        setfacl -Rb /folder

    définir la permission par défaut rwx (Récursif)
        setfacl -Rm d::rwx /folder

        -> par défaut, la permission max pour un dossier créé est rwx et la permission max pour un fichier crée est rw-
        -> dans l'exemple, les nouveaux dossiers auront donc rwx mais les nouveaux fichiers auront rx-

    Additional Permissions Settings
        There are three advanced options for permissions: the setuid, setgid and sticky bit options.  The sticky bitis not really used much, but on shared directories, it affectively locks files within the directory from being modified by users other than the file creator.

        setuid bit -> uid -> user
        setgid bit -> gid -> group
        sticky bit -> other

    Explications
        La commande "id" permet de retourner les uid/gid/... de l'utilisateur en cours

        Si un fichier possède le "setuid bit", n'importe quel autre user pourra exécuter le fichier à la place de l'utilisateur défini dans les permissions
        Si un dossier possède le "setgid bit", tous les nouveaux sous-dossiers/fichiers créés auront le groupe du dossier

        A chaque fois qu'on crée un fichier ou un répertoire, l'utilisateur de la permission sera d'office l'utilisateur avec lequel le fichier ou le répertoire  a été créé

    Quand on déplace un fichier, les acls du fichier d'origine sont gardés
    Quand on copie un fichier, de nouveaux acls sont appliqués sur base du dossier de destination

Rechercher un mot dans tous les fichiers d'un dossier/sous-dossier

    grep -R mot /etc/*

Où se trouve les fichiers bashrc ?
    /etc/bash.bashrc

    /home/.../.bashrc

Permissions
    sur répertoire
        ll / ls -> doit avoir rx
        cd -> doit avoir r

    x = eXplore sur les dossiers
    x = eXecution sur les fichiers

Pattern
    https://www.linuxjournal.com/content/pattern-matching-bash

Find avec pattern
    find . -name "*680*"  -type d
    find . -path "*/customer-680/*"  -type d

Obtenir la taille en Go de tous les fichiers contenus dans les répertoires et sous-répertoires en utilisant un pattern

    find . -path "*/customer-680/*"  -type d -exec du -b {} \; | awk '{print $1}' | awk '{s+=$1} END {print s}' | awk '{print $1/1024/1024/1024}'
