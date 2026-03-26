# J

## jobs – List active jobs

```bash
jobs
```

### Top 5 mest brugte options

### 1. Vis alle job med PID

```bash
jobs -l
```

### 2. Vis kun kørende job

```bash
jobs -r
```

### 3. Vis kun stoppede job

```bash
jobs -s
```

### 4. Send job til baggrunden

```bash
bg %1
```

### 5. Bring job til forgrunden

```bash
fg %1
```

---

## journalctl – Læs systemlog fra systemd

```bash
journalctl
```

### journalctl – Top 5 mest brugte options

#### 1. Vis log for en bestemt tjeneste

```bash
journalctl -u nginx
```

#### 2. Følg log i realtid

```bash
journalctl -f
```

#### 3. Vis log siden seneste opstart

```bash
journalctl -b
```

#### 4. Vis kun fejl og kritiske beskeder

```bash
journalctl -p err
```

#### 5. Vis log for et bestemt tidsinterval

```bash
journalctl --since "2026-03-01" --until "2026-03-25"
```

---
