# D

## date – Display the current date and time

```bash
date
```

### date – Top 5 mest brugte options

#### 1. Vis dato i bestemt format

```bash
date +"%Y-%m-%d"
```

#### 2. Vis dato og tid

```bash
date +"%Y-%m-%d %H:%M:%S"
```

#### 3. Sæt systemdatoen

```bash
date -s "2026-03-17 10:00:00"
```

#### 4. Vis dato for X dage siden

```bash
date -d "7 days ago"
```

#### 5. Vis Unix timestamp

```bash
date +%s
```

---

## df – Display free disk space

```bash
df
```

### df – Top 5 mest brugte options

#### 1. Vis i menneskevenligt format (GB/MB)

```bash
df -h
```

#### 2. Vis en specifik mappe

```bash
df -h /home
```

#### 3. Vis filsystemtype

```bash
df -T
```

#### 4. Vis kun lokale filsystemer

```bash
df -l
```

#### 5. Vis i MB

```bash
df -m
```

---

## diff – Compare differences between files

```bash
diff fil1.txt fil2.txt
```

### diff – Top 5 mest brugte options

#### 1. Vis i unified format (lettere at læse)

```bash
diff -u fil1.txt fil2.txt
```

#### 2. Sammenlign to mapper

```bash
diff -r mappe1/ mappe2/
```

#### 3. Ignorer mellemrum

```bash
diff -w fil1.txt fil2.txt
```

#### 4. Vis kun om filerne er forskellige

```bash
diff -q fil1.txt fil2.txt
```

#### 5. Ignorer store/små bogstaver

```bash
diff -i fil1.txt fil2.txt
```

---

## dig – DNS lookup

```bash
dig example.com
```

### dig – Top 5 mest brugte options

#### 1. Slå en bestemt record type op

```bash
dig example.com MX
```

#### 2. Brug specifik DNS-server

```bash
dig @8.8.8.8 example.com
```

#### 3. Kort output

```bash
dig +short example.com
```

#### 4. Reverse DNS lookup

```bash
dig -x 8.8.8.8
```

#### 5. Vis alle record typer

```bash
dig example.com ANY
```

---

## du – Count and display file and directory total sizes

```bash
du
```

### du – Top 5 mest brugte options

#### 1. Vis i menneskevenligt format

```bash
du -h mappe/
```

#### 2. Vis kun total størrelse

```bash
du -sh mappe/
```

#### 3. Vis størrelse på alle filer og undermapper

```bash
du -ah mappe/
```

#### 4. Sorter efter størrelse

```bash
du -h mappe/ | sort -h
```

#### 5. Vis kun X niveauer dybt

```bash
du -h --max-depth=1 mappe/
```
