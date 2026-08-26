# Linux File Permissions

En oversigt over hvordan filrettigheder virker, og hvordan de beregnes.

---

## Rettighedsværdier

| Binær | Oktal | String | Betydning |
|-------|-------|--------|-----------|
| 000 | 0 (0+0+0) | `---` | Ingen rettighed |
| 001 | 1 (0+0+1) | `--x` | Execute |
| 010 | 2 (0+2+0) | `-w-` | Write |
| 011 | 3 (0+2+1) | `-wx` | Write + Execute |
| 100 | 4 (4+0+0) | `r--` | Read |
| 101 | 5 (4+0+1) | `r-x` | Read + Execute |
| 110 | 6 (4+2+0) | `rw-` | Read + Write |
| 111 | 7 (4+2+1) | `rwx` | Read + Write + Execute |

---

## Rettighedsstruktur

Rettigheder er delt op i tre grupper: **Owner**, **Group**, **Other**.

```
r w x   r w -   r - x
Owner   Group   Other
```

| Bogstav | Betydning | Talværdi |
|---------|-----------|----------|
| `r` | Read | 4 |
| `w` | Write / Edit | 2 |
| `x` | Execute | 1 |

---

## Eksempel-beregning

| Rettighed | Beregning |
|-----------|-----------|
| `rwx` | 4+2+1 = 7 |
| `rw-` | 4+2+0 = 6 |
| `r-x` | 4+0+1 = 5 |

`rwx` (owner) + `rw-` (group) + `r-x` (other) → **765**

---

## Almindelige eksempler

| Kommando | Betydning |
|----------|-----------|
| `chmod 777 fil` | Fuld adgang for alle |
| `chmod 755 fil` | Owner fuld adgang, andre read+execute |
| `chmod 644 fil` | Owner read+write, andre read |

---

## Se også

[C.md](C.md) for `chmod` og `chown` med flere eksempler.
