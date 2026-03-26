# F

## find

```bash
find . -type f -iname "*.zipx"
```

### Top 5 mest brugte options

### 1. Find tomme mapper

```bash
find . -type d -empty
```

### 2. Find filer efter navn

```bash
find . -name "filnavn.txt"
```

### 3. Find filer efter størrelse

```bash
find . -type f -size +100M
```

### 4. Find filer ændret inden for X dage

```bash
find . -type f -mtime -7
```

### 5. Find filer og udfør en kommando på dem

```bash
find . -type f -name "*.log" -exec rm {} \;
```

---

## fg – Bring et baggrundsjob til forgrunden

```bash
fg
```

### fg – Top 5 mest brugte options

#### 1. Bring seneste baggrundsjob til forgrunden

```bash
fg
```

#### 2. Bring bestemt job til forgrunden (jobnummer)

```bash
fg %1
```

#### 3. List baggrundsjob før brug

```bash
jobs
```

#### 4. Bring job med bestemt navn til forgrunden

```bash
fg %nano
```

#### 5. Suspender et kørende job og send til baggrund

```bash
Ctrl+Z
bg
```

---

## file – Bestem filtype

```bash
file filnavn
```

### file – Top 5 mest brugte options

#### 1. Vis filtype for en fil

```bash
file billede.png
```

#### 2. Vis filtype for alle filer i mappe

```bash
file *
```

#### 3. Vis kun MIME-typen

```bash
file --mime-type billede.png
```

#### 4. Følg symboliske links

```bash
file -L linknavn
```

#### 5. Vis komprimeret indhold

```bash
file -z arkiv.gz
```

---

## fr24feed – FlightRadar24 datafeed til ADS-B

```bash
fr24feed
```

### fr24feed – Top 5 mest brugte options

#### 1. Start fr24feed-tjenesten

```bash
sudo systemctl start fr24feed
```

#### 2. Stop fr24feed-tjenesten

```bash
sudo systemctl stop fr24feed
```

#### 3. Kør opsætningsguiden

```bash
sudo fr24feed --signup
```

#### 4. Vis status for tjenesten

```bash
sudo systemctl status fr24feed
```

#### 5. Vis logfil

```bash
sudo journalctl -u fr24feed -f
```

---
