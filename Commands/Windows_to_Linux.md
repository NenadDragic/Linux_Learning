# Windows → Linux kommando-oversigt

En oversigt over almindelige Windows-kommandoer og deres Linux-ækvivalenter.

---

## Filer og mapper

| Windows | Linux | Beskrivelse |
|---------|-------|-------------|
| `dir` | `ls -l` | List filer med detaljer |
| `dir /s` | `ls -lR` eller `find .` | Rekursiv liste |
| `dir *.txt /s` | `find . -name "*.txt"` | Rekursiv søgning efter filtype |
| `dir *.* /s` | `find . -name "*.*"` | Alle filer rekursivt |
| `cd` | `cd` | Skift mappe |
| `cd ..` | `cd ..` | Gå én mappe op |
| `mkdir` | `mkdir` | Opret mappe |
| `rmdir /s /q` | `rm -rf` | Slet mappe og indhold |
| `del` | `rm` | Slet fil |
| `copy` | `cp` | Kopiér fil |
| `move` | `mv` | Flyt eller omdøb fil |
| `ren` | `mv` | Omdøb fil |
| `type filnavn` | `cat filnavn` | Vis filindhold |
| `more filnavn` | `less filnavn` | Vis fil side for side |
| `attrib` | `chmod` / `chown` | Ændre filattributter/rettigheder |
| `where kommando` | `which kommando` | Find sti til en kommando |

---

## Tekst og søgning

| Windows | Linux | Beskrivelse |
|---------|-------|-------------|
| `find "tekst" fil.txt` | `grep "tekst" fil.txt` | Søg efter tekst i fil |
| `findstr /s "tekst" *` | `grep -r "tekst" .` | Rekursiv tekstsøgning |
| `echo tekst` | `echo tekst` | Skriv tekst til terminal |

---

## System og processer

| Windows | Linux | Beskrivelse |
|---------|-------|-------------|
| `tasklist` | `ps -ef` | Vis kørende processer |
| `taskkill /PID 1234` | `kill 1234` | Stop en proces |
| `cls` | `clear` | Ryd terminal |
| `ipconfig` | `ip a` eller `ifconfig` | Vis netværksinfo |
| `ping` | `ping` | Test netværksforbindelse |
| `netstat` | `ss` eller `netstat` | Vis netværksforbindelser |
| `hostname` | `hostname` | Vis computernavn |
| `set` | `env` eller `printenv` | Vis miljøvariabler |
| `set VAR=værdi` | `export VAR=værdi` | Sæt miljøvariabel |

---

## Disk og lager

| Windows | Linux | Beskrivelse |
|---------|-------|-------------|
| `chkdsk` | `fsck` | Tjek filsystem |
| `diskpart` | `fdisk` / `parted` | Partitionér disk |
| `format` | `mkfs` | Formater disk |
| `dir` (diskforbrug) | `df -h` | Vis ledig diskplads |
| — | `du -sh *` | Vis mappestørrelser |

---

## Eksempel: `dir *.* /s` på Linux

Den direkte ækvivalent til `dir *.* /s` er:

```bash
find . -name "*.*"
```

Eller med detaljer (permissions, størrelse, dato):

```bash
ls -lR
```

Kun filer med en bestemt extension, f.eks. `.sh`:

```bash
find . -name "*.sh"
```

`find` er generelt mere fleksibel og foretrækkes i scripts.
