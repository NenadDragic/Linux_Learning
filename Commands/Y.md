# Y

## yes – Repeatedly output a string

```bash
yes
```

### Top 5 mest brugte options

### 1. Bekræft automatisk alle prompter

```bash
yes | apt install pakkenavn
```

### 2. Output en bestemt streng

```bash
yes "ja"
```

### 3. Output "no" til alle prompter

```bash
yes no | kommando
```

### 4. Kombiner med head for begrænset output

```bash
yes | head -n 5
```

### 5. Brug med rm til sletning uden bekræftelse

```bash
yes | rm -i *.txt
```

---

## yum – Pakkehåndtering til ældre RHEL/CentOS

```bash
sudo yum install pakkenavn
```

### yum – Top 5 mest brugte options

#### 1. Opdater systemet

```bash
sudo yum update -y
```

#### 2. Installer en pakke

```bash
sudo yum install pakkenavn
```

#### 3. Fjern en pakke

```bash
sudo yum remove pakkenavn
```

#### 4. Søg efter en pakke

```bash
yum search pakkenavn
```

#### 5. Vis pakkeinfo

```bash
yum info pakkenavn
```
