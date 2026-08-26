# Essential Linux Logs (/var/log/)

En oversigt over de vigtigste logfiler på et Linux-system, og hvordan man læser dem.

---

## 1. Generelt system

`/var/log/syslog` (Debian/Ubuntu) eller `/var/log/messages` (RHEL/CentOS)

Central hub for generelle systembeskeder og ikke-kritiske fejl.

```bash
grep "error" /var/log/syslog
tail -f /var/log/syslog
```

---

## 2. Sikkerhed & autentificering

`/var/log/auth.log` (Debian/Ubuntu) eller `/var/log/secure` (RHEL/CentOS)

Logger alle succesfulde/mislykkede loginforsøg og sudo-brug.

```bash
grep "Failed password" /var/log/auth.log
```

---

## 3. Kernel & boot

`/var/log/dmesg`

Gemmer kernel ring-buffer beskeder. God til hardware-/driverproblemer.

```bash
dmesg | less
```

---

## 4. Web services

`/var/log/nginx/` (eller `/var/log/apache2/`)

Access- og error-logs for webservere.

```bash
tail -f /var/log/nginx/access.log
tail -f /var/log/apache2/error.log
```

---

## 5. Systemd journal

`journalctl`

Binære logs til systemer der bruger systemd. Hurtigere og mere kontekstbevidst visning end flad-fil logs.

```bash
journalctl -xe
journalctl -u nginx
```

---

## Se også

[D.md](D.md) for `dmesg`, [J.md](J.md) for `journalctl`, [T.md](T.md) for `tail`, [G.md](G.md) for `grep`.
