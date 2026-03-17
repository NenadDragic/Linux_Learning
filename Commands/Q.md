# Q

## quota – Display disk usage and limits for users

```bash
quota
```

### Top 5 mest brugte options

### 1. Vis quota for en bestemt bruger

```bash
quota -u brugernavn
```

### 2. Vis quota for en gruppe

```bash
quota -g gruppenavn
```

### 3. Vis i menneskevenligt format

```bash
quota -s
```

### 4. Vis quota for alle brugere (root)

```bash
repquota -a
```

### 5. Vis quota på bestemt filsystem

```bash
quota -u brugernavn /home
```
