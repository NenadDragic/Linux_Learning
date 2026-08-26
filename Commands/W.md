# W

## w – Vis hvem der er logget på systemet og hvad de laver

```bash
w
```

### w – Top 5 mest brugte options

#### 1. Vis alle indloggede brugere

```bash
w
```

#### 2. Vis uden overskriftslinje

```bash
w -h
```

#### 3. Vis kort format (uden login-tid/JCPU/PCPU)

```bash
w -s
```

#### 4. Vis kun for en specifik bruger

```bash
w brugernavn
```

#### 5. Vis IP-adresse i stedet for hostname

```bash
w -f
```

---

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

## whatis – Vis kort en-linjes beskrivelse af en kommando

```bash
whatis kommando
```

### whatis – Top 5 mest brugte options

#### 1. Vis beskrivelse af en kommando

```bash
whatis ls
```

#### 2. Vis beskrivelser for flere kommandoer

```bash
whatis ls cd grep
```

#### 3. Opdater whatis-databasen

```bash
sudo mandb
```

#### 4. Kombiner med apropos for bredere søgning

```bash
apropos kopier
```

#### 5. Vis alle betydninger (flere manual-sektioner)

```bash
whatis -a printf
```

---

## whereis – Find binary, kildekode og manual-filer for en kommando

```bash
whereis kommando
```

### whereis – Top 5 mest brugte options

#### 1. Find alle placeringer for en kommando

```bash
whereis bash
```

#### 2. Vis kun binary-filen

```bash
whereis -b bash
```

#### 3. Vis kun manual-siden

```bash
whereis -m bash
```

#### 4. Vis kun kildekode

```bash
whereis -s bash
```

#### 5. Søg i alternative stier

```bash
whereis -u bash
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

## whoami – Vis nuværende brugernavn

```bash
whoami
```

### whoami – Top 5 mest brugte options

#### 1. Vis nuværende bruger

```bash
whoami
```

#### 2. Vis bruger-id og gruppe-id (relateret kommando)

```bash
id
```

#### 3. Vis effektiv bruger via sudo

```bash
sudo whoami
```

#### 4. Brug i script til betinget logik

```bash
if [ "$(whoami)" = "root" ]; then echo "Kører som root"; fi
```

#### 5. Vis hjælp

```bash
whoami --help
```

---

## whois – Slå ejer- og registreringsoplysninger op for et domæne

```bash
whois example.com
```

### whois – Top 5 mest brugte options

#### 1. Slå domæne op

```bash
whois example.com
```

#### 2. Slå IP-adresse op

```bash
whois 8.8.8.8
```

#### 3. Angiv specifik whois-server

```bash
whois -h whois.verisign-grs.com example.com
```

#### 4. Vis rå output uden lokal formattering

```bash
whois -H example.com
```

#### 5. Slå flere domæner op i træk

```bash
for d in example.com example.org; do whois $d; done
```

---
