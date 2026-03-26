# H

## head – Display the first lines of files

```bash
head filnavn.txt
```

### head – Top 5 mest brugte options

#### 1. Vis de første N linjer

```bash
head -n 20 filnavn.txt
```

#### 2. Vis de første N bytes

```bash
head -c 100 filnavn.txt
```

#### 3. Vis første linjer fra flere filer

```bash
head fil1.txt fil2.txt
```

#### 4. Kombiner med pipe

```bash
ls -la | head -n 10
```

#### 5. Vis alt undtagen de sidste N linjer

```bash
head -n -5 filnavn.txt
```

---

## history – Command history

```bash
history
```

### history – Top 5 mest brugte options

#### 1. Vis de seneste N kommandoer

```bash
history 20
```

#### 2. Søg i historik

```bash
history | grep "kommando"
```

#### 3. Kør en kommando fra historikken

```bash
!42
```

#### 4. Kør seneste kommando der starter med X

```bash
!ls
```

#### 5. Ryd historikken

```bash
history -c
```

---

## hostname – Print set or system name

```bash
hostname
```

### hostname – Top 5 mest brugte options

#### 1. Vis fuldt domænenavn (FQDN)

```bash
hostname -f
```

#### 2. Vis IP-adresse

```bash
hostname -I
```

#### 3. Skift hostname midlertidigt

```bash
hostname nyt-navn
```

#### 4. Vis kun kort hostname

```bash
hostname -s
```

#### 5. Vis domænenavn

```bash
hostname -d
```

---

## hostnamectl – Vis og sæt systemets hostname

```bash
hostnamectl
```

### hostnamectl – Top 5 mest brugte options

#### 1. Vis nuværende hostname og systeminfo

```bash
hostnamectl
```

#### 2. Sæt nyt statisk hostname

```bash
hostnamectl set-hostname nyt-hostname
```

#### 3. Sæt pretty hostname (med specialtegn)

```bash
hostnamectl set-hostname "Mit System" --pretty
```

#### 4. Vis kun hostname

```bash
hostnamectl --static
```

#### 5. Vis operativsystem og kernel-information

```bash
hostnamectl status
```

---

## htop – Interaktiv procesovervåger

```bash
htop
```

### htop – Top 5 mest brugte options

#### 1. Start htop

```bash
htop
```

#### 2. Vis processer for bestemt bruger

```bash
htop -u brugernavn
```

#### 3. Sorter efter hukommelsesforbrug (inde i htop)

```bash
htop
# Tryk F6, vælg MEM%
```

#### 4. Søg efter proces (inde i htop)

```bash
htop
# Tryk F3 og skriv procesnavn
```

#### 5. Dræb en proces (inde i htop)

```bash
htop
# Marker proces og tryk F9
```

---
