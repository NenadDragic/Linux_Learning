# B

## bash – Start en ny Bash-shell eller kør et script

```bash
bash script.sh
```

### bash – Top 5 mest brugte options

#### 1. Kør et shell-script

```bash
bash script.sh
```

#### 2. Kør script med debugging (vis kommandoer)

```bash
bash -x script.sh
```

#### 3. Kør script og afslut ved første fejl

```bash
bash -e script.sh
```

#### 4. Læs kommandoer fra en streng

```bash
bash -c "echo Hej verden"
```

#### 5. Start interaktiv login-shell

```bash
bash -l
```

---

## bmon – Realtidsovervågning af netværksbåndbredde

```bash
bmon
```

### bmon – Top 5 mest brugte options

#### 1. Overvåg bestemt netværksgrænseflade

```bash
bmon -p eth0
```

#### 2. Angiv opdateringsinterval i sekunder

```bash
bmon -r 2
```

#### 3. Kør i ikke-interaktiv tilstand (output til terminal)

```bash
bmon -o ascii
```

#### 4. Vis kun en bestemt grænseflade med ASCII-output

```bash
bmon -p wlan0 -o ascii
```

#### 5. Vis hjælp og tilgængelige options

```bash
bmon --help
```

---
