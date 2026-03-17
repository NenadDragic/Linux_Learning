# G

## grep – Search for a pattern and perform an action

```bash
grep "mønster" fil.txt
```

### grep – Top 5 mest brugte options

#### 1. Ignorer store/små bogstaver

```bash
grep -i "mønster" fil.txt
```

#### 2. Søg rekursivt i alle filer i en mappe

```bash
grep -r "mønster" mappe/
```

#### 3. Vis linjenumre

```bash
grep -n "mønster" fil.txt
```

#### 4. Vis kun filnavne med match

```bash
grep -l "mønster" *.txt
```

#### 5. Inverter søgning (vis linjer uden match)

```bash
grep -v "mønster" fil.txt
```

---

## gawk – Search fields for lines that match a pattern

```bash
gawk '{print $1}' fil.txt
```

### gawk – Top 5 mest brugte options

#### 1. Vis bestemt kolonne (felt)

```bash
gawk '{print $2}' fil.txt
```

#### 2. Brug brugerdefineret separator

```bash
gawk -F: '{print $1}' /etc/passwd
```

#### 3. Filtrer linjer der matcher et mønster

```bash
gawk '/mønster/ {print}' fil.txt
```

#### 4. Beregn sum af en kolonne

```bash
gawk '{sum += $1} END {print sum}' fil.txt
```

#### 5. Udskriv antal linjer

```bash
gawk 'END {print NR}' fil.txt
```

---

## groupadd – Create a new security group

```bash
groupadd gruppenavn
```

### groupadd – Top 5 mest brugte options

#### 1. Opret gruppe med specifikt GID

```bash
groupadd -g 1050 gruppenavn
```

#### 2. Opret systemgruppe

```bash
groupadd -r gruppenavn
```

#### 3. Tving oprettelse selv om GID eksisterer

```bash
groupadd -f gruppenavn
```

#### 4. Verificer oprettelse

```bash
getent group gruppenavn
```

#### 5. Vis alle grupper

```bash
cat /etc/group
```

---

## groupdel – Delete a security group

```bash
groupdel gruppenavn
```

### groupdel – Top 5 mest brugte options

#### 1. Slet gruppe

```bash
groupdel gruppenavn
```

#### 2. Verificer sletning

```bash
getent group gruppenavn
```

#### 3. Vis alle grupper

```bash
cat /etc/group
```

#### 4. Find grupper der tilhører en bruger

```bash
groups brugernavn
```

#### 5. Vis hjælp

```bash
groupdel --help
```

---

## groupmod – Modify a group

```bash
groupmod -n nyt_navn gammelt_navn
```

### groupmod – Top 5 mest brugte options

#### 1. Omdøb en gruppe

```bash
groupmod -n nyt_navn gammelt_navn
```

#### 2. Skift GID

```bash
groupmod -g 1100 gruppenavn
```

#### 3. Vis nuværende grupper

```bash
cat /etc/group
```

#### 4. Verificer ændring

```bash
getent group gruppenavn
```

#### 5. groupmod hjælp

```bash
groupmod --help
```

---

## gpasswd – Update group passwords

```bash
gpasswd gruppenavn
```

### gpasswd – Top 5 mest brugte options

#### 1. Tilføj bruger til gruppe

```bash
gpasswd -a brugernavn gruppenavn
```

#### 2. Fjern bruger fra gruppe

```bash
gpasswd -d brugernavn gruppenavn
```

#### 3. Sæt gruppeadministrator

```bash
gpasswd -A brugernavn gruppenavn
```

#### 4. Slet gruppe-adgangskode

```bash
gpasswd -r gruppenavn
```

#### 5. Lås gruppe-adgangskode

```bash
gpasswd -R gruppenavn
```
