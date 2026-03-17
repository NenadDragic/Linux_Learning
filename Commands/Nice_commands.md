# Nice Commands

## Tæl alle .zipx filer rekursivt

```bash
find . -type f -iname "*.zipx" | wc -l
```

### Hvad gør den?

Kommandoen finder alle filer med `.zipx` endelsen i den nuværende mappe og alle undermapper, og tæller hvor mange der er.

### Forklaring del for del

| Del | Beskrivelse |
|-----|-------------|
| `find .` | Start søgning fra nuværende mappe |
| `-type f` | Kun filer, ikke mapper |
| `-iname "*.zipx"` | Filnavn slutter på `.zipx` (ikke case-sensitiv, fx .ZIPX virker også) |
| `\|` | Sender resultatet videre til næste kommando |
| `wc -l` | Tæller antallet af linjer = antallet af filer fundet |
