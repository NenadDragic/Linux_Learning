# F

## find

```bash
find . -type f -iname "*.zipx"
```

### Top 5 mest brugte options

### 1. Find tomme mapper

```bash
find . -type d -empty
```

### 2. Find filer efter navn

```bash
find . -name "filnavn.txt"
```

### 3. Find filer efter størrelse

```bash
find . -type f -size +100M
```

### 4. Find filer ændret inden for X dage

```bash
find . -type f -mtime -7
```

### 5. Find filer og udfør en kommando på dem

```bash
find . -type f -name "*.log" -exec rm {} \;
```
