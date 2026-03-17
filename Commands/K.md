# K

## kill – Kill a process using its PID

```bash
kill PID
```

### kill – Top 5 mest brugte options

#### 1. Tving afslutning (SIGKILL)

```bash
kill -9 PID
```

#### 2. Send SIGTERM (blød afslutning)

```bash
kill -15 PID
```

#### 3. List alle signaler

```bash
kill -l
```

#### 4. Find PID med ps

```bash
ps aux | grep procesnavn
```

#### 5. Send signal til alle processer i en gruppe

```bash
kill -9 -PGID
```

---

## killall – Terminate processes by name

```bash
killall procesnavn
```

### killall – Top 5 mest brugte options

#### 1. Tving afslutning

```bash
killall -9 procesnavn
```

#### 2. Ignorer store/små bogstaver

```bash
killall -I procesnavn
```

#### 3. Vis hvad der afsluttes

```bash
killall -v procesnavn
```

#### 4. Spørg inden afslutning

```bash
killall -i procesnavn
```

#### 5. Afslut kun processer fra bestemt bruger

```bash
killall -u brugernavn procesnavn
```
