# C

## cal – Show calendar

```bash
cal
```

### cal – Top 5 mest brugte options

#### 1. Vis specifik måned og år

```bash
cal 3 2026
```

#### 2. Vis hele året

```bash
cal -y
```

#### 3. Vis tre måneder (forrige, nuværende, næste)

```bash
cal -3
```

#### 4. Vis mandag som første dag

```bash
cal -m
```

#### 5. Vis uge-numre

```bash
cal -w
```

---

## cat – Display file content

```bash
cat filnavn.txt
```

### cat – Top 5 mest brugte options

#### 1. Vis linjenumre

```bash
cat -n filnavn.txt
```

#### 2. Sammensæt to filer

```bash
cat fil1.txt fil2.txt > samlet.txt
```

#### 3. Vis ikke-printbare tegn

```bash
cat -A filnavn.txt
```

#### 4. Undertrykk gentagne tomme linjer

```bash
cat -s filnavn.txt
```

#### 5. Opret ny fil med indhold

```bash
cat > nyfil.txt
```

---

## chgrp – Change group ownership

```bash
chgrp gruppenavn fil.txt
```

### chgrp – Top 5 mest brugte options

#### 1. Skift gruppe rekursivt

```bash
chgrp -R gruppenavn mappe/
```

#### 2. Vis ændringer

```bash
chgrp -v gruppenavn fil.txt
```

#### 3. Brug gruppe fra en referencefil

```bash
chgrp --reference=reference.txt fil.txt
```

#### 4. Skift gruppe på symbolisk link

```bash
chgrp -h gruppenavn link
```

#### 5. Skift kun hvis nuværende gruppe matcher

```bash
chgrp --from=gammelgruppe nygruppe fil.txt
```

---

## chmod – Change access permissions

```bash
chmod 755 fil.txt
```

### chmod – Top 5 mest brugte options

#### 1. Giv alle læse/skrive/kør rettigheder

```bash
chmod 777 fil.txt
```

#### 2. Rekursivt på en mappe

```bash
chmod -R 755 mappe/
```

#### 3. Giv ejeren kørselstilladelse

```bash
chmod u+x script.sh
```

#### 4. Fjern skriveadgang for alle

```bash
chmod a-w fil.txt
```

#### 5. Vis ændringer

```bash
chmod -v 644 fil.txt
```

---

## chown – Change file owner and group

```bash
chown bruger fil.txt
```

### chown – Top 5 mest brugte options

#### 1. Skift ejer og gruppe

```bash
chown bruger:gruppe fil.txt
```

#### 2. Skift ejer rekursivt på en mappe

```bash
chown -R bruger:gruppe mappe/
```

#### 3. Vis ændringer

```bash
chown -v bruger fil.txt
```

#### 4. Brug ejer fra referencefil

```bash
chown --reference=reference.txt fil.txt
```

#### 5. Skift kun gruppe

```bash
chown :gruppe fil.txt
```

---

## cp – Copy files or directories

```bash
cp kilde.txt destination.txt
```

### cp – Top 5 mest brugte options

#### 1. Kopier mappe rekursivt

```bash
cp -r kildemappe/ destinationsmappe/
```

#### 2. Bevar rettigheder og tidsstempel

```bash
cp -p fil.txt backup/
```

#### 3. Spørg inden overskrivning

```bash
cp -i fil.txt destination/
```

#### 4. Vis hvad der kopieres

```bash
cp -v fil.txt destination/
```

#### 5. Opdater kun nyere filer

```bash
cp -u fil.txt destination/
```

---

## cron – Schedule tasks to run at specified times

```bash
crontab -e
```

### cron – Top 5 mest brugte options

#### 1. Vis nuværende cron jobs

```bash
crontab -l
```

#### 2. Kør job hvert minut

```bash
* * * * * /sti/til/script.sh
```

#### 3. Kør job hver dag kl. 02:00

```bash
0 2 * * * /sti/til/script.sh
```

#### 4. Kør job hver mandag

```bash
0 0 * * 1 /sti/til/script.sh
```

#### 5. Slet alle cron jobs

```bash
crontab -r
```

---

## curl – Transfer data from or to a server

```bash
curl https://example.com
```

### curl – Top 5 mest brugte options

#### 1. Gem output til fil

```bash
curl -o filnavn.html https://example.com
```

#### 2. Følg redirect automatisk

```bash
curl -L https://example.com
```

#### 3. Send POST request med data

```bash
curl -X POST -d "key=value" https://example.com/api
```

#### 4. Send med header

```bash
curl -H "Authorization: Bearer token" https://example.com/api
```

#### 5. Vis HTTP statuskode

```bash
curl -o /dev/null -s -w "%{http_code}" https://example.com
```
