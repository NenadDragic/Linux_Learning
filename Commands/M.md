# M

## mkdir – Create new directories

```bash
mkdir mappenavn
```

### mkdir – Top 5 mest brugte options

#### 1. Opret hele mappestien på én gang

```bash
mkdir -p mappe/undermappe/underundermappe
```

#### 2. Vis hvad der oprettes

```bash
mkdir -v mappenavn
```

#### 3. Sæt rettigheder ved oprettelse

```bash
mkdir -m 755 mappenavn
```

#### 4. Opret flere mapper på én gang

```bash
mkdir mappe1 mappe2 mappe3
```

#### 5. Opret mappe og sæt ejer

```bash
mkdir mappenavn && chown bruger:gruppe mappenavn
```

---

## mkfs – Create a filesystem on disk

```bash
mkfs -t ext4 /dev/sdb1
```

### mkfs – Top 5 mest brugte options

#### 1. Opret ext4 filesystem

```bash
mkfs.ext4 /dev/sdb1
```

#### 2. Opret FAT32 filesystem

```bash
mkfs.vfat -F 32 /dev/sdb1
```

#### 3. Opret med label

```bash
mkfs.ext4 -L "MinDisk" /dev/sdb1
```

#### 4. Vis fremgang

```bash
mkfs.ext4 -v /dev/sdb1
```

#### 5. Kontroller disk inden formatering

```bash
mkfs.ext4 -c /dev/sdb1
```

---

## mount – Mount filesystems

```bash
mount /dev/sdb1 /mnt/disk
```

### mount – Top 5 mest brugte options

#### 1. Vis alle monterede filsystemer

```bash
mount
```

#### 2. Montér med bestemt filsystemtype

```bash
mount -t ext4 /dev/sdb1 /mnt/disk
```

#### 3. Montér read-only

```bash
mount -o ro /dev/sdb1 /mnt/disk
```

#### 4. Remontér (fx for at skifte til rw)

```bash
mount -o remount,rw /mnt/disk
```

#### 5. Montér ISO-fil

```bash
mount -o loop billede.iso /mnt/iso
```

---

## mv – Rename files or directories

```bash
mv gammelt_navn nyt_navn
```

### mv – Top 5 mest brugte options

#### 1. Flyt fil til anden mappe

```bash
mv fil.txt /destination/mappe/
```

#### 2. Spørg inden overskrivning

```bash
mv -i fil.txt destination/
```

#### 3. Vis hvad der flyttes

```bash
mv -v fil.txt destination/
```

#### 4. Opdater kun nyere filer

```bash
mv -u fil.txt destination/
```

#### 5. Flyt flere filer til en mappe

```bash
mv fil1.txt fil2.txt destination/
```

---

## man – Vis manual for en kommando

```bash
man kommando
```

### man – Top 5 mest brugte options

#### 1. Vis manualsiden for en kommando

```bash
man ls
```

#### 2. Søg i alle manualsider

```bash
man -k søgeord
```

#### 3. Vis bestemt sektion af manualen

```bash
man 5 passwd
```

#### 4. Vis alle tilgængelige manualsider for en kommando

```bash
man -a kommando
```

#### 5. Åbn manualside i HTML-browser

```bash
man -H kommando
```

---

## mkfifo – Opret en navngivet pipe (FIFO)

```bash
mkfifo rørfil
```

### mkfifo – Top 5 mest brugte options

#### 1. Opret en FIFO-fil

```bash
mkfifo min_pipe
```

#### 2. Opret med bestemt rettigheder

```bash
mkfifo -m 644 min_pipe
```

#### 3. Skriv data til pipe

```bash
echo "data" > min_pipe &
```

#### 4. Læs data fra pipe

```bash
cat min_pipe
```

#### 5. Brug FIFO til kommunikation mellem processer

```bash
mkfifo /tmp/pipe && cat /tmp/pipe | grep "mønster"
```

---

## more – Vis filindhold én side ad gangen

```bash
more filnavn.txt
```

### more – Top 5 mest brugte options

#### 1. Vis fil én side ad gangen

```bash
more filnavn.txt
```

#### 2. Start visning fra bestemt linje

```bash
more +42 filnavn.txt
```

#### 3. Sæt antal linjer per side

```bash
more -20 filnavn.txt
```

#### 4. Kombiner med pipe

```bash
ps aux | more
```

#### 5. Søg efter mønster (inde i more)

```bash
more filnavn.txt
# Tryk / og skriv søgeord
```

---
