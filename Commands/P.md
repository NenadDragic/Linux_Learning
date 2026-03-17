# P

## passwd – Update user password

```bash
passwd
```

### passwd – Top 5 mest brugte options

#### 1. Skift adgangskode for en bestemt bruger

```bash
passwd brugernavn
```

#### 2. Lås en brugers adgangskode

```bash
passwd -l brugernavn
```

#### 3. Lås op for en brugers adgangskode

```bash
passwd -u brugernavn
```

#### 4. Tving bruger til at skifte adgangskode ved næste login

```bash
passwd -e brugernavn
```

#### 5. Slet adgangskode (ingen adgangskode kræves)

```bash
passwd -d brugernavn
```

---

## paste – Merge lines of files

```bash
paste fil1.txt fil2.txt
```

### paste – Top 5 mest brugte options

#### 1. Brug bestemt separator

```bash
paste -d',' fil1.txt fil2.txt
```

#### 2. Flet linjer fra samme fil serielt

```bash
paste -s fil.txt
```

#### 3. Flet tre filer

```bash
paste fil1.txt fil2.txt fil3.txt
```

#### 4. Brug tab som separator (standard)

```bash
paste fil1.txt fil2.txt
```

#### 5. Kombiner med pipe

```bash
ls | paste - - -
```

---

## ps – Show process information

```bash
ps
```

### ps – Top 5 mest brugte options

#### 1. Vis alle kørende processer

```bash
ps aux
```

#### 2. Søg efter bestemt proces

```bash
ps aux | grep procesnavn
```

#### 3. Vis processer som træstruktur

```bash
ps -ejH
```

#### 4. Vis processer for bestemt bruger

```bash
ps -u brugernavn
```

#### 5. Vis bestemt PID

```bash
ps -p PID
```

---

## pwd – Print working directory

```bash
pwd
```

### pwd – Top 5 mest brugte options

#### 1. Vis absolut sti (standard)

```bash
pwd
```

#### 2. Undgå symboliske links (vis fysisk sti)

```bash
pwd -P
```

#### 3. Vis logisk sti (med symlinks)

```bash
pwd -L
```

#### 4. Gem nuværende sti i variabel

```bash
NUVAERENDE=$(pwd)
```

#### 5. Kombiner med cd

```bash
cd /ny/mappe && pwd
```
