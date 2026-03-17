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
