# P

## passwd – Update user password

```bash
passwd
```

### passwd – Top 5 mest brugte options

#### 1. Skift adgangskode for en bestemt bruger

```bash
passwd brugernavn
```

#### 2. Lås en brugers adgangskode

```bash
passwd -l brugernavn
```

#### 3. Lås op for en brugers adgangskode

```bash
passwd -u brugernavn
```

#### 4. Tving bruger til at skifte adgangskode ved næste login

```bash
passwd -e brugernavn
```

#### 5. Slet adgangskode (ingen adgangskode kræves)

```bash
passwd -d brugernavn
```

---

## paste – Merge lines of files

```bash
paste fil1.txt fil2.txt
```

### paste – Top 5 mest brugte options

#### 1. Brug bestemt separator

```bash
paste -d',' fil1.txt fil2.txt
```

#### 2. Flet linjer fra samme fil serielt

```bash
paste -s fil.txt
```

#### 3. Flet tre filer

```bash
paste fil1.txt fil2.txt fil3.txt
```

#### 4. Brug tab som separator (standard)

```bash
paste fil1.txt fil2.txt
```

#### 5. Kombiner med pipe

```bash
ls | paste - - -
```

---

## ps – Show process information

```bash
ps
```

### ps – Top 5 mest brugte options

#### 1. Vis alle kørende processer

```bash
ps aux
```

#### 2. Søg efter bestemt proces

```bash
ps aux | grep procesnavn
```

#### 3. Vis processer som træstruktur

```bash
ps -ejH
```

#### 4. Vis processer for bestemt bruger

```bash
ps -u brugernavn
```

#### 5. Vis bestemt PID

```bash
ps -p PID
```

#### 6. Vis alle processer i fuld format (bruges ofte med grep)

```bash
ps -ef
```

---

## pwd – Print working directory

```bash
pwd
```

### pwd – Top 5 mest brugte options

#### 1. Vis absolut sti (standard)

```bash
pwd
```

#### 2. Undgå symboliske links (vis fysisk sti)

```bash
pwd -P
```

#### 3. Vis logisk sti (med symlinks)

```bash
pwd -L
```

#### 4. Gem nuværende sti i variabel

```bash
NUVAERENDE=$(pwd)
```

#### 5. Kombiner med cd

```bash
cd /ny/mappe && pwd
```

---

## ping – Test netværksforbindelse til en vært

```bash
ping 192.168.1.1
```

### ping – Top 5 mest brugte options

#### 1. Ping et domæne

```bash
ping google.com
```

#### 2. Send bestemt antal pakker

```bash
ping -c 5 google.com
```

#### 3. Angiv interval mellem pakker (sekunder)

```bash
ping -i 2 google.com
```

#### 4. Sæt pakke-størrelse

```bash
ping -s 1024 google.com
```

#### 5. Vis kun statistik til sidst

```bash
ping -q -c 10 google.com
```

---

## pip – Installer Python-pakker (Python 2)

```bash
pip install pakkernavn
```

### pip – Top 5 mest brugte options

#### 1. Installer en pakke

```bash
pip install requests
```

#### 2. Afinstaller en pakke

```bash
pip uninstall requests
```

#### 3. Vis installerede pakker

```bash
pip list
```

#### 4. Gem pakkeliste til fil

```bash
pip freeze > requirements.txt
```

#### 5. Installer fra requirements-fil

```bash
pip install -r requirements.txt
```

---

## pip3 – Installer Python 3-pakker

```bash
pip3 install pakkenavn
```

### pip3 – Top 5 mest brugte options

#### 1. Installer en pakke

```bash
pip3 install numpy
```

#### 2. Opdater en pakke

```bash
pip3 install --upgrade numpy
```

#### 3. Vis installerede pakker

```bash
pip3 list
```

#### 4. Søg efter pakke

```bash
pip3 search pakkenavn
```

#### 5. Installer i virtuelt miljø

```bash
python3 -m venv venv && source venv/bin/activate && pip3 install pakkenavn
```

---

## python – Kør Python 2-script eller -fortolker

```bash
python script.py
```

### python – Top 5 mest brugte options

#### 1. Kør et Python-script

```bash
python script.py
```

#### 2. Start interaktiv Python-fortolker

```bash
python
```

#### 3. Kør Python-kode direkte

```bash
python -c "print('Hej verden')"
```

#### 4. Vis Python-version

```bash
python --version
```

#### 5. Kør modul som script

```bash
python -m http.server 8080
```

---

## python3 – Kør Python 3-script eller -fortolker

```bash
python3 script.py
```

### python3 – Top 5 mest brugte options

#### 1. Kør et Python 3-script

```bash
python3 script.py
```

#### 2. Start interaktiv Python 3-fortolker

```bash
python3
```

#### 3. Kør Python 3-kode direkte

```bash
python3 -c "print('Hej verden')"
```

#### 4. Opret virtuelt miljø

```bash
python3 -m venv mit_env
```

#### 5. Kør indbygget HTTP-server

```bash
python3 -m http.server 8080
```

---
