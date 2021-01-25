# Linux | Utilisateurs

***

## Lister les utilisateurs

### Retourner les noms

```bash
less /etc/passwd | awk -F: '{print $1}'
```

