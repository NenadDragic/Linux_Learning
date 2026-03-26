# E

## echo – Display text on terminal screen

```bash
echo "Hej verden"
```

### echo – Top 5 mest brugte options

#### 1. Skriv uden ny linje

```bash
echo -n "Ingen newline"
```

#### 2. Fortolk escape-tegn

```bash
echo -e "Linje1\nLinje2"
```

#### 3. Skriv output til en fil

```bash
echo "tekst" > fil.txt
```

#### 4. Tilføj til eksisterende fil

```bash
echo "ny linje" >> fil.txt
```

#### 5. Vis værdien af en variabel

```bash
echo $HOME
```

---

## egrep – Pattern search (extended regex)

```bash
egrep "mønster" fil.txt
```

### egrep – Top 5 mest brugte options

#### 1. Søg med flere mønstre

```bash
egrep "ord1|ord2" fil.txt
```

#### 2. Ignorer store/små bogstaver

```bash
egrep -i "mønster" fil.txt
```

#### 3. Vis linjenumre

```bash
egrep -n "mønster" fil.txt
```

#### 4. Vis kun filnavne med match

```bash
egrep -l "mønster" *.txt
```

#### 5. Søg rekursivt i mapper

```bash
egrep -r "mønster" mappe/
```

---

## env – Display environment variables

```bash
env
```

### env – Top 5 mest brugte options

#### 1. Vis en specifik variabel

```bash
env | grep HOME
```

#### 2. Kør kommando med midlertidig variabel

```bash
env VAR=værdi kommando
```

#### 3. Kør kommando med tomt miljø

```bash
env -i kommando
```

#### 4. Fjern en variabel midlertidigt

```bash
env -u VARIABEL kommando
```

#### 5. Sæt variabel og kør kommando

```bash
env PATH=/custom/path:$PATH kommando
```

---

## eval – Evaluate multiple arguments

```bash
eval "kommando"
```

### eval – Top 5 mest brugte options

#### 1. Udfør en dynamisk bygget kommando

```bash
cmd="ls -la"; eval $cmd
```

#### 2. Ekspander og kør kommando fra variabel

```bash
eval $(ssh-agent)
```

#### 3. Sæt variabel dynamisk

```bash
eval "${name}=værdi"
```

#### 4. Byg og udfør kommando i loop

```bash
for i in 1 2 3; do eval "var$i=$i"; done
```

#### 5. Udfør kommando med citationstegn

```bash
eval 'echo $HOME'
```

---

## eject – Skub medie ud af drev

```bash
eject
```

### eject – Top 5 mest brugte options

#### 1. Skub standard CD/DVD-drev ud

```bash
eject
```

#### 2. Skub bestemt drev ud

```bash
eject /dev/cdrom
```

#### 3. Luk drevet igen

```bash
eject -t
```

#### 4. Skub USB-medie ud

```bash
eject /dev/sdb
```

#### 5. Vis hjælp

```bash
eject --help
```

---

## exit – Afslut den aktuelle shell-session

```bash
exit
```

### exit – Top 5 mest brugte options

#### 1. Afslut med statuskode 0 (succes)

```bash
exit 0
```

#### 2. Afslut med fejlkode

```bash
exit 1
```

#### 3. Afslut SSH-session

```bash
exit
```

#### 4. Afslut undershell i script

```bash
(exit 0)
```

#### 5. Brug i script for at stoppe ved fejl

```bash
kommando || exit 1
```

---
