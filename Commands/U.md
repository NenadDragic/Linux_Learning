# U

## ulimit – Limit user resources

```bash
ulimit -a
```

### ulimit – Top 5 mest brugte options

#### 1. Vis alle grænser

```bash
ulimit -a
```

#### 2. Sæt max filstørrelse (KB)

```bash
ulimit -f 102400
```

#### 3. Sæt max antal åbne filer

```bash
ulimit -n 4096
```

#### 4. Sæt max stack størrelse

```bash
ulimit -s unlimited
```

#### 5. Sæt max antal processer

```bash
ulimit -u 1000
```

---

## uname – Print system information

```bash
uname
```

### uname – Top 5 mest brugte options

#### 1. Vis al systeminfo

```bash
uname -a
```

#### 2. Vis kernel version

```bash
uname -r
```

#### 3. Vis arkitektur (64bit/32bit)

```bash
uname -m
```

#### 4. Vis operativsystemtype

```bash
uname -s
```

#### 5. Vis hostname

```bash
uname -n
```

---

## uniq – Filter repeated lines in text

```bash
uniq fil.txt
```

### uniq – Top 5 mest brugte options

#### 1. Vis kun unikke linjer

```bash
sort fil.txt | uniq
```

#### 2. Vis kun duplikerede linjer

```bash
sort fil.txt | uniq -d
```

#### 3. Tæl forekomster

```bash
sort fil.txt | uniq -c
```

#### 4. Ignorer store/små bogstaver

```bash
sort fil.txt | uniq -i
```

#### 5. Vis kun linjer der optræder én gang

```bash
sort fil.txt | uniq -u
```

---

## unlink – Remove a file

```bash
unlink filnavn.txt
```

### unlink – Top 5 mest brugte options

#### 1. Slet en enkelt fil

```bash
unlink filnavn.txt
```

#### 2. Slet et symbolisk link

```bash
unlink linknavn
```

#### 3. Alternativ med rm

```bash
rm filnavn.txt
```

#### 4. Slet fil og verificer

```bash
unlink filnavn.txt && echo "Slettet"
```

#### 5. Vis hjælp

```bash
unlink --help
```

---

## useradd – Create a new user

```bash
useradd brugernavn
```

### useradd – Top 5 mest brugte options

#### 1. Opret bruger med hjemmemappe

```bash
useradd -m brugernavn
```

#### 2. Opret bruger med bestemt shell

```bash
useradd -m -s /bin/bash brugernavn
```

#### 3. Tilføj til en gruppe

```bash
useradd -m -G sudo brugernavn
```

#### 4. Opret med kommentar/fuldt navn

```bash
useradd -c "Fuldt Navn" -m brugernavn
```

#### 5. Sæt adgangskode efter oprettelse

```bash
useradd -m brugernavn && passwd brugernavn
```

---

## usermod – Modify a user

```bash
usermod -aG gruppe brugernavn
```

### usermod – Top 5 mest brugte options

#### 1. Tilføj bruger til gruppe

```bash
usermod -aG sudo brugernavn
```

#### 2. Skift brugerens shell

```bash
usermod -s /bin/bash brugernavn
```

#### 3. Skift brugerens hjemmemappe

```bash
usermod -d /ny/sti brugernavn
```

#### 4. Lås brugerkonto

```bash
usermod -L brugernavn
```

#### 5. Lås op for brugerkonto

```bash
usermod -U brugernavn
```

---

## umount – Afmonter et filsystem

```bash
umount /mnt/disk
```

### umount – Top 5 mest brugte options

#### 1. Afmonter bestemt monteringspunkt

```bash
umount /mnt/disk
```

#### 2. Afmonter bestemt enhed

```bash
umount /dev/sdb1
```

#### 3. Tving afmontering

```bash
umount -f /mnt/disk
```

#### 4. Afmonter dovent (vent til den ikke bruges)

```bash
umount -l /mnt/disk
```

#### 5. Afmonter alle filsystemer af bestemt type

```bash
umount -t tmpfs
```

---

## uptime – Vis systemets oppetid og belastning

```bash
uptime
```

### uptime – Top 5 mest brugte options

#### 1. Vis oppetid

```bash
uptime
```

#### 2. Vis oppetid i menneskevenligt format

```bash
uptime -p
```

#### 3. Vis tidspunkt for seneste opstart

```bash
uptime -s
```

#### 4. Vis load average i et script

```bash
uptime | awk '{print $NF}'
```

#### 5. Kombiner med watch til løbende overvågning

```bash
watch -n 5 uptime
```

---
