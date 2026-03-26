# N

## nano – Text editor

```bash
nano filnavn.txt
```

### nano – Top 5 mest brugte options

#### 1. Åbn fil og gå til bestemt linje

```bash
nano +42 filnavn.txt
```

#### 2. Åbn i read-only tilstand

```bash
nano -v filnavn.txt
```

#### 3. Vis linjenumre

```bash
nano -l filnavn.txt
```

#### 4. Gem og afslut (inde i nano)

```bash
Ctrl+O  # Gem
Ctrl+X  # Afslut
```

#### 5. Søg i fil (inde i nano)

```bash
Ctrl+W  # Søg
```

---

## netstat – Network utility for reading and writing data

```bash
netstat
```

### netstat – Top 5 mest brugte options

#### 1. Vis alle aktive forbindelser

```bash
netstat -a
```

#### 2. Vis lyttende porte

```bash
netstat -l
```

#### 3. Vis med PID og procesnavn

```bash
netstat -p
```

#### 4. Vis numeriske adresser (ingen DNS opslag)

```bash
netstat -n
```

#### 5. Vis routing tabel

```bash
netstat -r
```

---

## nslookup – Perform DNS lookups and query DNS servers

```bash
nslookup example.com
```

### nslookup – Top 5 mest brugte options

#### 1. Slå MX record op (mail server)

```bash
nslookup -type=MX example.com
```

#### 2. Brug specifik DNS-server

```bash
nslookup example.com 8.8.8.8
```

#### 3. Reverse lookup (IP til domæne)

```bash
nslookup 8.8.8.8
```

#### 4. Slå AAAA record op (IPv6)

```bash
nslookup -type=AAAA example.com
```

#### 5. Interaktiv tilstand

```bash
nslookup
> set type=MX
> example.com
```

---

## nload – Vis netværkstrafik i realtid

```bash
nload
```

### nload – Top 5 mest brugte options

#### 1. Overvåg bestemt netværksgrænseflade

```bash
nload eth0
```

#### 2. Skift visningsintervallet (millisekunder)

```bash
nload -t 500
```

#### 3. Skift mellem grænseflader (inde i nload)

```bash
nload
# Brug pil venstre/højre
```

#### 4. Vis alle grænseflader

```bash
nload -m
```

#### 5. Indstil visningsenhed (fx Mbit/s)

```bash
nload -u M
```

---

## nmap – Netværksscanner og portscanner

```bash
nmap 192.168.1.1
```

### nmap – Top 5 mest brugte options

#### 1. Scan åbne porte på en vært

```bash
nmap 192.168.1.1
```

#### 2. Scan et helt subnet

```bash
nmap 192.168.1.0/24
```

#### 3. Detektér operativsystem

```bash
nmap -O 192.168.1.1
```

#### 4. Scan bestemte porte

```bash
nmap -p 22,80,443 192.168.1.1
```

#### 5. Hurtig scanning (de 100 mest almindelige porte)

```bash
nmap -F 192.168.1.1
```

---

## nohup – Kør kommando immune over for hangup-signaler

```bash
nohup kommando &
```

### nohup – Top 5 mest brugte options

#### 1. Kør script i baggrunden uden at stoppe ved logout

```bash
nohup bash script.sh &
```

#### 2. Omdirigér output til bestemt fil

```bash
nohup kommando > output.log 2>&1 &
```

#### 3. Kør lang proces og log output

```bash
nohup python3 script.py > log.txt &
```

#### 4. Vis PID på baggrundsjob

```bash
nohup kommando & echo "PID: $!"
```

#### 5. Kør med lav prioritet

```bash
nohup nice -n 10 kommando &
```

---
