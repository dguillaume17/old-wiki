# Visual Studio Code

[Retour](../../README.md)

## Extensions pour Markdown

### Liste (Markdown)

1. Markdown Preview Enhanced

2. Markdown Preview VS Code Highlighting

3. Markdown Shortcuts

4. markdownlint

### Configuration spécifique (Markdown)

#### Markdown Preview Enhanced

Commande : `CTRL + SHIFT + P > Markdown Preview Enhanced: Customize CSS`

```json
/* Please visit the URL below for more information: */
/* https://shd101wyy.github.io/markdown-preview-enhanced/#/customize-css */

.markdown-preview.markdown-preview {
  // modify your style here
  // eg: background-color: blue;
  h3 {
    font-size: 18px;
  }
  h4 {
    font-size: 14px;
  }
}
```

#### markdownlint

Fichier : `\.markdownlint.json`

```json
{
    "line_length": false,
    "no-inline-html": {
        "allowed_elements": ["br"]
    }
}
```

## Extensions pour Angular

### Liste (Angular)

1. GitLens — Git supercharged

2. Angular Language Service

3. CSS Formatter

4. es6-string-html

5. TSLint

6. vsc-angular-cli

### Configuration spécifique (Angular)

Aucune pour le moment

## Extensions pour debug

### Liste (debug)

1. Debugger for Chrome

### Configuration spécifique (debug)

Aucune pour le moment
