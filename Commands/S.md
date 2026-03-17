# S

## scp – Secure copy remotely

```bash
scp fil.txt bruger@server:/remote/sti/
```

### scp – Top 5 mest brugte options

#### 1. Kopier mappe rekursivt

```bash
scp -r mappe/ bruger@server:/remote/sti/
```

#### 2. Brug bestemt port

```bash
scp -P 2222 fil.txt bruger@server:/remote/sti/
```

#### 3. Kopier fra server til lokalt

```bash
scp bruger@server:/remote/fil.txt /lokal/sti/
```

#### 4. Vis fremgang

```bash
scp -v fil.txt bruger@server:/remote/sti/
```

#### 5. Bevar filrettigheder og tidsstempel

```bash
scp -p fil.txt bruger@server:/remote/sti/
```

---

## sed – Stream editor

```bash
sed 's/gammelt/nyt/' fil.txt
```

### sed – Top 5 mest brugte options

#### 1. Erstat alle forekomster på linjen

```bash
sed 's/gammelt/nyt/g' fil.txt
```

#### 2. Rediger fil direkte (in-place)

```bash
sed -i 's/gammelt/nyt/g' fil.txt
```

#### 3. Slet linjer der matcher et mønster

```bash
sed '/mønster/d' fil.txt
```

#### 4. Vis kun bestemte linjer

```bash
sed -n '5,10p' fil.txt
```

#### 5. Tilføj linje efter match

```bash
sed '/mønster/a\Ny linje' fil.txt
```

---

## seq – Generate sequences of numbers

```bash
seq 10
```

### seq – Top 5 mest brugte options

#### 1. Generer fra X til Y

```bash
seq 1 10
```

#### 2. Generer med trin

```bash
seq 0 2 20
```

#### 3. Brug bestemt separator

```bash
seq -s ',' 1 10
```

#### 4. Formater output (med nulstilling)

```bash
seq -w 1 10
```

#### 5. Kombiner med loops

```bash
for i in $(seq 1 5); do echo $i; done
```

---

## ssh – Secure shell

```bash
ssh bruger@server
```

### ssh – Top 5 mest brugte options

#### 1. Brug bestemt port

```bash
ssh -p 2222 bruger@server
```

#### 2. Brug SSH nøgle

```bash
ssh -i ~/.ssh/min_nøgle bruger@server
```

#### 3. Kør kommando på server uden at logge ind

```bash
ssh bruger@server "ls -la /home"
```

#### 4. Port forwarding (lokal til remote)

```bash
ssh -L 8080:localhost:80 bruger@server
```

#### 5. Kopiér SSH nøgle til server

```bash
ssh-copy-id bruger@server
```

---

## stat – Display file status

```bash
stat filnavn.txt
```

### stat – Top 5 mest brugte options

#### 1. Vis kun filstørrelse

```bash
stat -c %s filnavn.txt
```

#### 2. Vis kun ændringstidspunkt

```bash
stat -c %y filnavn.txt
```

#### 3. Vis i menneskevenligt format

```bash
stat filnavn.txt
```

#### 4. Vis filsystem info

```bash
stat -f /
```

#### 5. Vis rettigheder i oktal

```bash
stat -c %a filnavn.txt
```

---

## su – Switch user

```bash
su brugernavn
```

### su – Top 5 mest brugte options

#### 1. Skift til root

```bash
su -
```

#### 2. Skift til bestemt bruger med login shell

```bash
su - brugernavn
```

#### 3. Kør kommando som anden bruger

```bash
su -c "kommando" brugernavn
```

#### 4. Skift til bruger uden at ændre miljø

```bash
su brugernavn
```

#### 5. Vis nuværende bruger

```bash
whoami
```

---

## sudo – Execute a command as another user

```bash
sudo kommando
```

### sudo – Top 5 mest brugte options

#### 1. Kør kommando som root

```bash
sudo apt update
```

#### 2. Åbn shell som root

```bash
sudo -i
```

#### 3. Kør kommando som bestemt bruger

```bash
sudo -u brugernavn kommando
```

#### 4. Vis tilladte sudo kommandoer

```bash
sudo -l
```

#### 5. Kør forrige kommando med sudo

```bash
sudo !!
```

---

## tail – Display end of files

```bash
tail filnavn.txt
```

### tail – Top 5 mest brugte options

#### 1. Vis de sidste N linjer

```bash
tail -n 20 filnavn.txt
```

#### 2. Følg fil i realtid (log filer)

```bash
tail -f /var/log/syslog
```

#### 3. Følg fil og vis nye linjer løbende

```bash
tail -F /var/log/syslog
```

#### 4. Vis fra linje N og frem

```bash
tail -n +10 filnavn.txt
```

#### 5. Kombiner med pipe

```bash
journalctl | tail -n 50
```

---

## tar – Archive files

```bash
tar -cvf arkiv.tar mappe/
```

### tar – Top 5 mest brugte options

#### 1. Opret komprimeret arkiv (gzip)

```bash
tar -czvf arkiv.tar.gz mappe/
```

#### 2. Udpak arkiv

```bash
tar -xzvf arkiv.tar.gz
```

#### 3. Vis indhold uden at udpakke

```bash
tar -tzvf arkiv.tar.gz
```

#### 4. Udpak til bestemt mappe

```bash
tar -xzvf arkiv.tar.gz -C /destination/
```

#### 5. Opret arkiv med bzip2 komprimering

```bash
tar -cjvf arkiv.tar.bz2 mappe/
```
