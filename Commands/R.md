# R

## read – Read from standard input

```bash
read variabel
```

### read – Top 5 mest brugte options

#### 1. Læs med prompt-tekst

```bash
read -p "Skriv dit navn: " navn
```

#### 2. Skjul input (til adgangskoder)

```bash
read -s -p "Adgangskode: " password
```

#### 3. Sæt timeout på input

```bash
read -t 10 -p "Du har 10 sekunder: " svar
```

#### 4. Begræns antal tegn

```bash
read -n 1 -p "Tryk en tast: " tast
```

#### 5. Læs flere variabler på én linje

```bash
read fornavn efternavn
```

---

## rm – Remove files

```bash
rm filnavn.txt
```

### rm – Top 5 mest brugte options

#### 1. Slet mappe rekursivt

```bash
rm -r mappe/
```

#### 2. Tving sletning uden bekræftelse

```bash
rm -f filnavn.txt
```

#### 3. Spørg inden sletning

```bash
rm -i filnavn.txt
```

#### 4. Vis hvad der slettes

```bash
rm -v filnavn.txt
```

#### 5. Slet alle filer med bestemt endelse

```bash
rm *.log
```

---

## rmdir – Remove directories

```bash
rmdir mappenavn
```

### rmdir – Top 5 mest brugte options

#### 1. Slet tom mappe

```bash
rmdir mappenavn
```

#### 2. Slet hele mappestien hvis tom

```bash
rmdir -p mappe/undermappe/
```

#### 3. Vis hvad der slettes

```bash
rmdir -v mappenavn
```

#### 4. Slet flere tomme mapper

```bash
rmdir mappe1 mappe2 mappe3
```

#### 5. Slet ikke-tom mappe (brug rm)

```bash
rm -r mappenavn
```

---

## rename – Rename files

```bash
rename 's/gammelt/nyt/' *.txt
```

### rename – Top 5 mest brugte options

#### 1. Omdøb filendelse

```bash
rename 's/\.txt$/.md/' *.txt
```

#### 2. Skift til lowercase

```bash
rename 'y/A-Z/a-z/' *
```

#### 3. Preview uden at udføre

```bash
rename -n 's/gammelt/nyt/' *.txt
```

#### 4. Vis hvad der omdøbes

```bash
rename -v 's/gammelt/nyt/' *.txt
```

#### 5. Erstat mellemrum med underscore

```bash
rename 's/ /_/g' *
```

---

## rsync – Remote file copy

```bash
rsync kilde destination
```

### rsync – Top 5 mest brugte options

#### 1. Synkroniser mappe lokalt

```bash
rsync -av kildemappe/ destinationsmappe/
```

#### 2. Kopiér til fjernserver via SSH

```bash
rsync -avz mappe/ bruger@server:/remote/sti/
```

#### 3. Slet filer i destination der ikke er i kilde

```bash
rsync -av --delete kilde/ destination/
```

#### 4. Tør kørsel (vis hvad der ville ske)

```bash
rsync -av --dry-run kilde/ destination/
```

#### 5. Fortsæt afbrudt overførsel

```bash
rsync -av --partial kilde/ destination/
```
