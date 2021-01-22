# Photos

## Créer les sous-répertoires

### Tests (Windows)

```bash
exiftool -d "%m.%y/%d.%m - Abc/" "-testname<${DateTimeOriginal}$filename" "-testname<${MediaCreateDate}$filename" *
```

### Tests (MacOS)

```bash
exiftool -d "%m.%y/%d.%m - Abc/" "-testname<DateTimeOriginal" "-testname<MediaCreateDate" *
```

### Exécuter (Windows)

```bash
exiftool -d "%m.%y/%d.%m - Abc/" "-filename<${DateTimeOriginal}$filename" "-filename<${MediaCreateDate}$filename" *
```

### Exécuter (MacOS)

```bash
exiftool -d "%m.%y/%d.%m - Abc/" "-filename<DateTimeOriginal" "-filename<MediaCreateDate" *
```

## Lister les tags d'une image

Le param -s permet d'afficher le nom des tags à la places de leur description

```bash
exiftool -s image.jpg
```

## Vérifier la cohérence entre le NAS et les backups

- Compter le nombre de médias dans les albums

```bash
find . -type f -not -name "*.db" -not -name ".DS_Store" | wc -l
```

- Lister les médias dans les albums

```bash
find . -type f -not -name "*.db" -not -name ".DS_Store" | sort > find.txt
```