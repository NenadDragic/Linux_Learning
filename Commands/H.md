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
