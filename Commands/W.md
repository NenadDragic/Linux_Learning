# W

## wc

```bash
wc -l
```

### Top 5 mest brugte options

### 1. Tæl antal linjer i en fil

```bash
wc -l filnavn.txt
```

### 2. Tæl antal ord i en fil

```bash
wc -w filnavn.txt
```

### 3. Tæl antal tegn i en fil

```bash
wc -c filnavn.txt
```

### 4. Tæl linjer fra output af en anden kommando

```bash
ls | wc -l
```

### 5. Tæl linjer i flere filer på én gang

```bash
wc -l *.txt
```

---

## weectl – Konfigurer og administrer WeeWX vejrstation

```bash
weectl
```

### weectl – Top 5 mest brugte options

#### 1. Vis WeeWX-konfiguration

```bash
weectl station show
```

#### 2. Opret ny vejrstationsopsætning

```bash
weectl station create
```

#### 3. Vis databaseoplysninger

```bash
weectl database info
```

#### 4. Importer vejrdata

```bash
weectl import --import-config=import.conf
```

#### 5. Vis tilgængelige stationstyper

```bash
weectl station show --driver
```

---

## wget – Download filer fra nettet

```bash
wget https://example.com/fil.zip
```

### wget – Top 5 mest brugte options

#### 1. Download fil og gem med originalt navn

```bash
wget https://example.com/fil.zip
```

#### 2. Download og gem med bestemt filnavn

```bash
wget -O nyt_navn.zip https://example.com/fil.zip
```

#### 3. Fortsæt afbrudt download

```bash
wget -c https://example.com/stor_fil.iso
```

#### 4. Download i baggrunden

```bash
wget -b https://example.com/fil.zip
```

#### 5. Download hel hjemmeside rekursivt

```bash
wget -r -np https://example.com/
```

---

## which – Find stien til en kommando

```bash
which kommando
```

### which – Top 5 mest brugte options

#### 1. Find stien til en kommando

```bash
which python3
```

#### 2. Find alle forekomster i PATH

```bash
which -a python
```

#### 3. Tjek om en kommando eksisterer

```bash
which git && echo "git er installeret"
```

#### 4. Find sti til flere kommandoer på én gang

```bash
which bash sh dash
```

#### 5. Brug i scripts til at verificere installationer

```bash
if ! which docker > /dev/null; then echo "Docker ikke fundet"; fi
```

---
