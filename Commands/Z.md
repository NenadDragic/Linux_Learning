# Z

## zip – Package and compress files

```bash
zip arkiv.zip fil.txt
```

### Top 5 mest brugte options

### 1. Komprimer en hel mappe

```bash
zip -r arkiv.zip mappe/
```

### 2. Udpak en zip-fil

```bash
unzip arkiv.zip
```

### 3. Vis indhold uden at udpakke

```bash
unzip -l arkiv.zip
```

### 4. Udpak til bestemt mappe

```bash
unzip arkiv.zip -d /destination/
```

### 5. Tilføj fil til eksisterende zip

```bash
zip arkiv.zip nyfil.txt
```

---

## unzip – Udpak zip-arkiver

```bash
unzip arkiv.zip
```

### unzip – Top 5 mest brugte options

#### 1. Udpak til bestemt mappe

```bash
unzip arkiv.zip -d /destination/
```

#### 2. Vis indhold uden at udpakke

```bash
unzip -l arkiv.zip
```

#### 3. Overskriv uden at spørge

```bash
unzip -o arkiv.zip
```

#### 4. Udpak stille (uden output)

```bash
unzip -q arkiv.zip
```

#### 5. Test integritet af arkiv

```bash
unzip -t arkiv.zip
```

---

## zypper – Pakkehåndtering til openSUSE

```bash
sudo zypper install pakkenavn
```

### zypper – Top 5 mest brugte options

#### 1. Opdater systemet

```bash
sudo zypper update
```

#### 2. Installer en pakke

```bash
sudo zypper install pakkenavn
```

#### 3. Fjern en pakke

```bash
sudo zypper remove pakkenavn
```

#### 4. Søg efter en pakke

```bash
zypper search pakkenavn
```

#### 5. Vis pakkeinfo

```bash
zypper info pakkenavn
```
