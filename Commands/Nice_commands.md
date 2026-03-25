# Nice Commands

## Tæl alle .zipx filer rekursivt

```bash
find . -type f -iname "*.zipx" | wc -l
```

### Hvad gør den?

Kommandoen finder alle filer med `.zipx` endelsen i den nuværende mappe og alle undermapper, og tæller hvor mange der er.

### Forklaring del for del

| Del | Beskrivelse |
| --- | ----------- |
| `find .` | Start søgning fra nuværende mappe |
| `-type f` | Kun filer, ikke mapper |
| `-iname "*.zipx"` | Filnavn slutter på `.zipx` (ikke case-sensitiv, fx .ZIPX virker også) |
| `\|` | Sender resultatet videre til næste kommando |
| `wc -l` | Tæller antallet af linjer = antallet af filer fundet |

---

## Tjek om et script kører

```bash
ps -ef | grep mit_script.sh
```

### Hvad gør ps -ef | grep?

Kommandoen lister alle kørende processer og filtrerer output, så kun linjer der indeholder `mit_script.sh` vises. Bruges til at tjekke om et script allerede er i gang.

### Forklaring del for del – ps -ef | grep

| Del | Beskrivelse |
| --- | ----------- |
| `ps -ef` | Lister alle kørende processer med fuld information (bruger, PID, kommando osv.) |
| `\|` | Sender resultatet videre til næste kommando |
| `grep mit_script.sh` | Filtrerer og viser kun linjer der indeholder `mit_script.sh` |

---

## Verificer integritet af en fil med SHA-256

```bash
sha256sum filnavn.txt
```

### Hvad gør sha256sum?

Kommandoen beregner en unik hash-værdi (fingeraftryk) af filen. Bruges til at verificere at en fil ikke er blevet ændret eller beskadiget, fx efter download.

### Forklaring del for del – sha256sum

| Del | Beskrivelse |
| --- | ----------- |
| `sha256sum` | Beregner SHA-256 hash af filen |
| `filnavn.txt` | Filen der skal kontrolleres |

**Eksempel på output:**

```text
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855  filnavn.txt
```

Den lange streng er hashværdien — er den ens to gange, er filen uændret.
