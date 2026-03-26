# A

## alias – Create an alias for Linux commands

```bash
alias name='command'
```

### Top 5 mest brugte options

### 1. Opret en simpel alias

```bash
alias ll='ls -la'
```

### 2. Naviger hurtigt med genvej

```bash
alias ..='cd ..'
```

### 3. Farvet grep output

```bash
alias grep='grep --color=auto'
```

### 4. List alle aktive aliases

```bash
alias -p
```

### 5. Fjern en alias

```bash
unalias ll
```

---

## adduser – Tilføj en ny bruger til systemet

```bash
adduser brugernavn
```

### adduser – Top 5 mest brugte options

#### 1. Opret bruger med interaktiv opsætning

```bash
adduser ny_bruger
```

#### 2. Tilføj bruger til en eksisterende gruppe

```bash
adduser brugernavn gruppenavn
```

#### 3. Opret systembruger uden hjemmemappe

```bash
adduser --system --no-create-home brugernavn
```

#### 4. Angiv hjemmemappe manuelt

```bash
adduser --home /custom/sti brugernavn
```

#### 5. Angiv shell for brugeren

```bash
adduser --shell /bin/bash brugernavn
```

---

## apt-get – Pakkehåndtering til Debian/Ubuntu

```bash
apt-get install pakkernavn
```

### apt-get – Top 5 mest brugte options

#### 1. Opdater pakkelisten

```bash
apt-get update
```

#### 2. Opgrader alle installerede pakker

```bash
apt-get upgrade
```

#### 3. Installer en pakke

```bash
apt-get install pakkenavn
```

#### 4. Fjern en pakke

```bash
apt-get remove pakkenavn
```

#### 5. Fjern pakke og dens konfigurationsfiler

```bash
apt-get purge pakkenavn
```

---

## awk – Mønstermatchning og tekstbehandling

```bash
awk '{print $1}' fil.txt
```

### awk – Top 5 mest brugte options

#### 1. Udskriv bestemt kolonne

```bash
awk '{print $2}' fil.txt
```

#### 2. Brug brugerdefineret separator

```bash
awk -F: '{print $1}' /etc/passwd
```

#### 3. Filtrer linjer der matcher et mønster

```bash
awk '/mønster/ {print}' fil.txt
```

#### 4. Beregn sum af en kolonne

```bash
awk '{sum += $1} END {print sum}' fil.txt
```

#### 5. Udskriv linjer med mere end X felter

```bash
awk 'NF > 3' fil.txt
```

---
