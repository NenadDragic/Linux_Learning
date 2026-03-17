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
