# T

## tee – Redirect output to multiple files

```bash
kommando | tee fil.txt
```

### tee – Top 5 mest brugte options

#### 1. Tilføj til fil i stedet for at overskrive

```bash
kommando | tee -a fil.txt
```

#### 2. Skriv til flere filer samtidig

```bash
kommando | tee fil1.txt fil2.txt
```

#### 3. Kombiner med pipe og vis i terminal

```bash
ls -la | tee output.txt
```

#### 4. Ignorer interrupt signaler

```bash
kommando | tee -i fil.txt
```

#### 5. Skriv til fil og send videre i pipe

```bash
cat fil.txt | tee kopi.txt | grep "mønster"
```

---

## test – Check file conditions

```bash
test -f filnavn.txt && echo "Findes"
```

### test – Top 5 mest brugte options

#### 1. Tjek om fil eksisterer

```bash
test -f filnavn.txt
```

#### 2. Tjek om mappe eksisterer

```bash
test -d mappenavn
```

#### 3. Tjek om fil er ikke-tom

```bash
test -s filnavn.txt
```

#### 4. Sammenlign strenge

```bash
test "abc" = "abc" && echo "Ens"
```

#### 5. Sammenlign tal

```bash
test 5 -gt 3 && echo "5 er større end 3"
```

---

## top – Display running processes

```bash
top
```

### top – Top 5 mest brugte options

#### 1. Sorter efter CPU-brug

```bash
top -o %CPU
```

#### 2. Vis processer for bestemt bruger

```bash
top -u brugernavn
```

#### 3. Opdater hvert X sekund

```bash
top -d 2
```

#### 4. Kør én gang og afslut (batch mode)

```bash
top -b -n 1
```

#### 5. Vis kun N processer

```bash
top -b -n 1 | head -20
```

---

## touch – Create new files or update time

```bash
touch filnavn.txt
```

### touch – Top 5 mest brugte options

#### 1. Opret flere filer på én gang

```bash
touch fil1.txt fil2.txt fil3.txt
```

#### 2. Sæt bestemt tidsstempel

```bash
touch -t 202603171200 filnavn.txt
```

#### 3. Opdater kun adgangstidspunkt

```bash
touch -a filnavn.txt
```

#### 4. Opdater kun ændringstidspunkt

```bash
touch -m filnavn.txt
```

#### 5. Brug tidsstempel fra en anden fil

```bash
touch -r reference.txt filnavn.txt
```

---

## type – Describe a command

```bash
type kommando
```

### type – Top 5 mest brugte options

#### 1. Vis om kommando er alias, funktion eller program

```bash
type ls
```

#### 2. Vis alle steder kommandoen findes

```bash
type -a ls
```

#### 3. Vis kun filstien

```bash
type -P ls
```

#### 4. Vis type uden beskrivelse

```bash
type -t ls
```

#### 5. Tjek om kommando eksisterer

```bash
type kommando &>/dev/null && echo "Findes"
```

---

## trash-empty – Tøm papirkurven fra terminalen

```bash
trash-empty
```

### trash-empty – Top 5 mest brugte options

#### 1. Tøm papirkurven

```bash
trash-empty
```

#### 2. Slet filer ældre end X dage fra papirkurven

```bash
trash-empty 30
```

#### 3. Vis hvad der ligger i papirkurven

```bash
trash-list
```

#### 4. Flyt fil til papirkurven i stedet for rm

```bash
trash-put filnavn.txt
```

#### 5. Gendan fil fra papirkurven

```bash
trash-restore
```

---
