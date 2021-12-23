# Python

## Créer un environnement virtuel dans le dossier `venv`

```bash
python -m venv venv
```

## Activer l'environnement `venv`

### Windows

```cmd
.\venv\Scripts\activate.bat
```

### MacOS

```bash
source venv/bin/activate
```

## Installer un package sans le cache afin de solutionner d'éventuelles erreurs

```bash
pip --no-cache-dir install face_recognition
```

## Installer un package depuis un fichier `my-package.tar.gz`

1. Décompresser le fichier dans le dossier `my-package`

2. Le dossier `my-package` doit contenir le fichier `setup.py`

3. Installer le package

```bash
pip install -e my-path/my-package
```
