# S

## sha256sum – Beregn og verificer SHA-256 hash

```bash
sha256sum filnavn.txt
```

### sha256sum – Top 5 mest brugte options

#### 1. Beregn hash på en fil

```bash
sha256sum filnavn.txt
```

#### 2. Tjek hash mod en liste (verify)

```bash
sha256sum -c kontrolfil.sha256
```

#### 3. Gem hash til fil

```bash
sha256sum filnavn.txt > filnavn.sha256
```

#### 4. Beregn hash på flere filer

```bash
sha256sum fil1.txt fil2.txt fil3.txt
```

#### 5. Vis kun hash uden filnavn

```bash
sha256sum filnavn.txt | awk '{print $1}'
```

---

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

---

## service – Administrer systemtjenester (SysV-stil)

```bash
service tjenestenavn start
```

### service – Top 5 mest brugte options

#### 1. Start en tjeneste

```bash
service nginx start
```

#### 2. Stop en tjeneste

```bash
service nginx stop
```

#### 3. Genstart en tjeneste

```bash
service nginx restart
```

#### 4. Vis status for en tjeneste

```bash
service nginx status
```

#### 5. List alle tjenester

```bash
service --status-all
```

---

## sh – Kør kommandoer med POSIX-shell

```bash
sh script.sh
```

### sh – Top 5 mest brugte options

#### 1. Kør et shell-script

```bash
sh script.sh
```

#### 2. Kør med debugging

```bash
sh -x script.sh
```

#### 3. Kør kode direkte fra streng

```bash
sh -c "echo Hej verden"
```

#### 4. Afslut ved første fejl

```bash
sh -e script.sh
```

#### 5. Start interaktiv sh-shell

```bash
sh
```

---

## shutdown – Luk systemet ned eller genstart

```bash
shutdown now
```

### shutdown – Top 5 mest brugte options

#### 1. Luk ned med det samme

```bash
shutdown now
```

#### 2. Genstart systemet

```bash
shutdown -r now
```

#### 3. Planlæg nedlukning om X minutter

```bash
shutdown +10
```

#### 4. Annuller planlagt nedlukning

```bash
shutdown -c
```

#### 5. Send besked til brugere inden nedlukning

```bash
shutdown +5 "Systemet lukker ned om 5 minutter"
```

---

## source – Kør kommandoer fra en fil i nuværende shell

```bash
source fil.sh
```

### source – Top 5 mest brugte options

#### 1. Indlæs miljøvariabler fra en fil

```bash
source ~/.bashrc
```

#### 2. Kortere notation med punktum

```bash
. ~/.bashrc
```

#### 3. Aktiver et virtuelt Python-miljø

```bash
source venv/bin/activate
```

#### 4. Indlæs funktioner fra ekstern fil

```bash
source funktioner.sh
```

#### 5. Genindlæs .bash_profile

```bash
source ~/.bash_profile
```

---

## ss – Vis socket-statistik og netværksforbindelser

```bash
ss
```

### ss – Top 5 mest brugte options

#### 1. Vis alle lyttende TCP-porte

```bash
ss -tlnp
```

#### 2. Vis alle aktive forbindelser

```bash
ss -a
```

#### 3. Vis UDP-sockets

```bash
ss -u
```

#### 4. Vis forbindelser med procesnavn og PID

```bash
ss -p
```

#### 5. Vis forbindelser til bestemt port

```bash
ss -tnp dst :443
```

---

## ssh-keygen – Generer SSH-nøglepar

```bash
ssh-keygen
```

### ssh-keygen – Top 5 mest brugte options

#### 1. Generer standard RSA-nøgle

```bash
ssh-keygen -t rsa -b 4096
```

#### 2. Generer ED25519-nøgle (anbefalet)

```bash
ssh-keygen -t ed25519
```

#### 3. Angiv filnavn til nøglen

```bash
ssh-keygen -t ed25519 -f ~/.ssh/min_nøgle
```

#### 4. Vis fingeraftryk af nøgle

```bash
ssh-keygen -lf ~/.ssh/id_ed25519.pub
```

#### 5. Kopiér offentlig nøgle til server

```bash
ssh-copy-id -i ~/.ssh/id_ed25519.pub bruger@server
```

---

## systemctl – Administrer systemd-tjenester og -enheder

```bash
systemctl status tjenestenavn
```

### systemctl – Top 5 mest brugte options

#### 1. Start en tjeneste

```bash
systemctl start nginx
```

#### 2. Aktiver tjeneste ved opstart

```bash
systemctl enable nginx
```

#### 3. Vis status for en tjeneste

```bash
systemctl status nginx
```

#### 4. Stop en tjeneste

```bash
systemctl stop nginx
```

#### 5. Genindlæs systemd-konfiguration

```bash
systemctl daemon-reload
```

---
