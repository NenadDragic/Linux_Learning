# I

## id – Print user and group IDs

```bash
id
```

### Top 5 mest brugte options

### 1. Vis info for en specifik bruger

```bash
id brugernavn
```

### 2. Vis kun bruger-ID (UID)

```bash
id -u
```

### 3. Vis kun gruppe-ID (GID)

```bash
id -g
```

### 4. Vis alle gruppe-ID'er

```bash
id -G
```

### 5. Vis kun navn (ikke nummer)

```bash
id -un
```

---

## ifconfig – Vis og konfigurer netværksgrænseflader

```bash
ifconfig
```

### ifconfig – Top 5 mest brugte options

#### 1. Vis alle aktive netværksgrænseflader

```bash
ifconfig
```

#### 2. Vis alle grænseflader inkl. inaktive

```bash
ifconfig -a
```

#### 3. Vis bestemt grænseflade

```bash
ifconfig eth0
```

#### 4. Tildel IP-adresse til grænseflade

```bash
ifconfig eth0 192.168.1.100 netmask 255.255.255.0
```

#### 5. Deaktiver en netværksgrænseflade

```bash
ifconfig eth0 down
```

---

## iftop – Vis netværksbåndbredde per forbindelse

```bash
iftop
```

### iftop – Top 5 mest brugte options

#### 1. Overvåg bestemt netværksgrænseflade

```bash
iftop -i eth0
```

#### 2. Vis porte i stedet for tjenester

```bash
iftop -P
```

#### 3. Vis numeriske IP-adresser (ingen DNS-opslag)

```bash
iftop -n
```

#### 4. Filtrér på bestemt vært

```bash
iftop -f "host 192.168.1.1"
```

#### 5. Kør uden farver

```bash
iftop -c
```

---

## ip – Vis og administrer netværk og routing

```bash
ip addr
```

### ip – Top 5 mest brugte options

#### 1. Vis alle IP-adresser

```bash
ip addr show
```

#### 2. Vis routing-tabel

```bash
ip route show
```

#### 3. Tilføj IP-adresse til grænseflade

```bash
ip addr add 192.168.1.100/24 dev eth0
```

#### 4. Aktiver netværksgrænseflade

```bash
ip link set eth0 up
```

#### 5. Vis ARP-tabel (naboer)

```bash
ip neigh show
```

---

## ipconfig – Vis netværkskonfiguration (Windows-kommando)

```bash
ipconfig
```

### ipconfig – Top 5 mest brugte options

#### 1. Vis alle netværksadaptere (Linux-ækvivalent)

```bash
ip addr show
```

#### 2. Vis kortfattet netværksoversigt

```bash
ip -brief addr show
```

#### 3. Frigivelse og fornyelse af DHCP-adresse

```bash
dhclient -r eth0 && dhclient eth0
```

#### 4. Vis DNS-oplysninger

```bash
resolvectl status
```

#### 5. Vis standard gateway

```bash
ip route | grep default
```

---
