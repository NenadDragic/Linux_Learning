# L

## less – View file content on screen at a time

```bash
less filnavn.txt
```

### less – Top 5 mest brugte options

#### 1. Søg i filen

```bash
less filnavn.txt
# derefter: /søgeord
```

#### 2. Vis linjenumre

```bash
less -N filnavn.txt
```

#### 3. Følg fil i realtid (som tail -f)

```bash
less +F filnavn.txt
```

#### 4. Åbn ved bestemt linje

```bash
less +42 filnavn.txt
```

#### 5. Kombiner med pipe

```bash
ps aux | less
```

---

## ln – Create symbolic links to files

```bash
ln -s kilde link
```

### ln – Top 5 mest brugte options

#### 1. Opret symbolisk link

```bash
ln -s /sti/til/kilde linknavn
```

#### 2. Opret hårdt link

```bash
ln kilde link
```

#### 3. Overskriv eksisterende link

```bash
ln -sf /sti/til/kilde linknavn
```

#### 4. Vis hvad der oprettes

```bash
ln -sv /sti/til/kilde linknavn
```

#### 5. Verificer link

```bash
ls -la linknavn
```

---

## locate – Find file names quickly

```bash
locate filnavn
```

### locate – Top 5 mest brugte options

#### 1. Ignorer store/små bogstaver

```bash
locate -i filnavn
```

#### 2. Begræns antal resultater

```bash
locate -n 10 filnavn
```

#### 3. Opdater databasen

```bash
updatedb
```

#### 4. Vis kun eksisterende filer

```bash
locate -e filnavn
```

#### 5. Søg med regex

```bash
locate -r "\.txt$"
```

---

## ls – List directory contents

```bash
ls
```

### ls – Top 5 mest brugte options

#### 1. Vis alle filer inkl. skjulte

```bash
ls -a
```

#### 2. Detaljeret liste med rettigheder og størrelse

```bash
ls -la
```

#### 3. Sorter efter ændringstidspunkt

```bash
ls -lt
```

#### 4. Vis størrelse i menneskevenligt format

```bash
ls -lh
```

#### 5. Rekursiv liste

```bash
ls -R
```

---

## lsof – List open files

```bash
lsof
```

### lsof – Top 5 mest brugte options

#### 1. Vis åbne filer for en bestemt bruger

```bash
lsof -u brugernavn
```

#### 2. Vis hvilke processer bruger en port

```bash
lsof -i :80
```

#### 3. Vis åbne filer for en bestemt proces

```bash
lsof -p PID
```

#### 4. Vis alle netværksforbindelser

```bash
lsof -i
```

#### 5. Vis hvilken proces bruger en fil

```bash
lsof /sti/til/fil
```
