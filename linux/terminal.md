# Linux | Commandes

## Symboles

### `.`

Répertoire en cours

Exemple :

* Mettre à jour les droits du répertoire en cours

```bash
chmod 777 .
```

### `$?`

Statut de la dernière commande

Exemple:

```bash
mkdir test
echo $? #imprime 0
mkdir test
echo $? #imprime 1
```

### `$0`

Nom de fichier du script en cours d'exécution

### `$1`, `$2`, ..., `$n`

Valeur de l'argument `n` passé en paramètre au script en cours d'exécution

### `$@`

Valeurs (séparés par un espace) de tous les arguments passés en paramètre au script en cours d'exécution

### `|`

Tuyau qui relie la sortie standard d'une première commande (=son résultat) à l'entrée standard d'une deuxième commande

Exemple :

```bash
cat test.txt | grep "hello"
```

### `>`

Chevron qui écrit la sortie standard d'une commande (=son résultat) dans un nouveau fichier texte (fichier écrasé si existant)

Exemple :

```bash
echo hello > test2.txt
```

### `>>`

Double chevron qui écrit la sortie standard d'une commande (=son résultat) à la fin d'un fichier texte existant (fichier créé si inexistant)

Exemple :

```bash
echo hello >> test2.txt
```

### `<`

Chevron qui écrit le contenu d'un fichier texte dans l'entrée standard d'une commande

Exemple :

```bash
cat < test.txt # pareil que cat test.txt
```

### `<<`

Double chevron qui écrit le contenu tapé par l'utilisateur dans l'entrée standard d'une commande

Syntaxe :

* `commande << <line>` = l'utilisateur tape le contenu dans la console jusqu'à l'écriture de la ligne `<line>`

Exemples :

* Ecrire le contenu tapé par l'utilisateur dans le fichier test.txt

    ```bash
    cat << EOF > test.txt
    ```

* Ecrire le contenu tapé par l'utilisateur dans le fichier test.txt
  * Création du script

    ```bash
    cat << EOF > config.ini
    [section]
    param1=$1
    param2=$2
    EOF
    echo "Config file was created successfully"
    ```

  * Exécution du script

    ```bash
    ./script.sh valeur1 valeur2
    ```

### `||`

Lien entre deux commandes qui exécute la deuxième uniquement si la première retourne une erreur

NB : la valeur de `$?` sera d'office `O` car pas d'erreur

Exemple :

```bash
mkdir test || echo "Ce dossier existe déjà"
```

### `&&`

Lien entre deux commandes qui exécute la deuxième uniquement si la première a réussi

Exemple :

```bash
mkdir test && echo "Le dossier a bien été créé"

```

### `;`

Lien entre deux commandes qui exécute la deuxième dans tous les cas

Exemple :

```bash
echo "Bonjour"; echo "Gui"
```

### `&`

Caractère en fin de commande permettant son exécution en arrière plan

Fonctionnement :

* Exécuter la commande avec `&` à la fin
* Le PID du processus est écrit dans la sortie standard
* Quand le processus est terminé et à la prochaine commande exécutée par l'utilisateur, le statut `Done` est écrit dans la sortie standard

Exemple :

```bash
sleep 10 &
```

## Raccourcis

### `CTRL + R`

Rechercher une commande dans l'historique des commandes

Fonctionnement :

* `CTRL + R` pour ouvrir la recherche
* Ecrire une recherche pour sélectionnr la dernière commande qui correspond à cette recherche
  * `enter` pour exécuter la commande sélectionnée
  * `up` | `down` pour naviguer dans l'historique de commande à partir de la commande sélectionnée
  * `CTRL + R` pour sélectionnr la dernière commande qui correspond à la recherche en partant de la commande sélectionnée

### `CTRL + A` & `CTRL + A`

Se positionner au début et à la fin d'une commande

### `ECHAP .`

Ecrire la valeur du dernier argument de la dernière commande exécutée

### `ECHAP #`

Commenter la commande en cours

Fonctionnement :

* `ECHAP #` pour ajouter `#` au début de la commande en cours et ouvrir une nouvelle commande
* Il est possible de revenir à la commande commentée grâce à l'historique des commandes

