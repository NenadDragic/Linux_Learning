# Linux Logs — hvor de er, og hvordan man læser dem

En komplet oversigt over de vigtigste logkilder på et Linux-system: flad-fil logs, den binære journal, autentificeringshistorik og de forensiske spor.

---

## 1. `/var/log` — mappekortet

Alt centraliseres (som udgangspunkt) under `/var/log/`. Sådan finder du hurtigt ud af, hvad der ligger hvor:

```bash
ls -lh /var/log/               # oversigt over filer og undermapper
du -sh /var/log/* | sort -rh   # hvad fylder mest
```

| Fil/mappe | Indhold |
| --- | --- |
| `syslog` / `messages` | Generel systemlog (catch-all) |
| `auth.log` / `secure` | Login, sudo, SSH, PAM |
| `kern.log` | Kernel-beskeder (uddrag af `dmesg`) |
| `boot.log` | Beskeder fra boot-processen |
| `cron` / `cron.log` | Cron-jobs kørt eller ej |
| `dpkg.log` / `yum.log` | Pakkeinstallation/-opdatering |
| `wtmp` | Login-historik (binær) |
| `btmp` | Mislykkede login-forsøg (binær) |
| `lastlog` | Seneste login pr. bruger (binær) |
| `audit/audit.log` | Auditd's forensiske hændelseslog |
| `nginx/`, `apache2/` | Webserver access/error-logs |
| `journal/` | Systemd's binære journal (hvis persistent) |

De fleste tekstbaserede logs kan læses direkte med `cat`, `less`, `tail` eller `grep`. De binære (`wtmp`, `btmp`, `lastlog`, `journal/`) kræver deres eget værktøj — se nedenfor.

---

## 2. `syslog` — det generelle systemstream

`/var/log/syslog` (Debian/Ubuntu) eller `/var/log/messages` (RHEL/CentOS)

Catch-all for beskeder fra services og daemons, der ikke har deres egen dedikerede log.

```bash
tail -f /var/log/syslog             # følg live
grep -i "error" /var/log/syslog     # find fejl
zgrep -i "error" /var/log/syslog.*.gz   # søg i roterede/gzippede filer
```

---

## 3. `auth.log` — login, sudo og brute-force

`/var/log/auth.log` (Debian/Ubuntu) eller `/var/log/secure` (RHEL/CentOS)

Alt der har med autentificering at gøre: SSH-login, sudo-brug, PAM-fejl.

```bash
grep "Failed password" /var/log/auth.log       # mislykkede loginforsøg
grep "Accepted" /var/log/auth.log              # succesfulde logins
grep "sudo:" /var/log/auth.log                 # sudo-brug
grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -rn
                                                 # tæl mislykkede forsøg pr. IP (brute-force-jagt)
```

---

## 4. `kern.log` — kernel, OOM, disk & hardware

`/var/log/kern.log` (uddrag af kernel ring-bufferen, samme kilde som `dmesg`)

Her finder man OOM-killeren, diskfejl (I/O errors), USB-tilslutninger og drivermeddelelser.

```bash
grep -i "out of memory" /var/log/kern.log       # OOM-killer ramte en proces
grep -i "error" /var/log/kern.log               # disk-/hardwarefejl
dmesg -T | grep -i "usb"                        # live kernel-buffer, tidsstemplet
dmesg --level=err,crit,alert,emerg              # kun alvorlige beskeder
```

---

## 5. `journald` — spørg systemd-journalen ordentligt

`journalctl` erstatter (eller supplerer) fladfil-logs på systemd-baserede systemer. Binær, indekseret, og strukturkorrekt.

```bash
journalctl -xe                       # seneste beskeder + forklaringer
journalctl -u nginx                  # kun for én service/unit
journalctl -u nginx --since today
journalctl -f                        # følg live (som tail -f)
journalctl -p err                    # kun fejlniveau eller derover
journalctl --since "1 hour ago" --until now
journalctl -k                        # kun kernel-beskeder (svarer til dmesg)
journalctl -b                        # kun siden sidste boot
journalctl -b -1                     # log fra den *foregående* boot (nyttigt efter et crash)
journalctl --disk-usage              # hvor meget plads journalen fylder
sudo journalctl --vacuum-time=2weeks # ryd op i gamle journal-data
```

> Er journalen ikke persistent (forsvinder ved reboot)? Tjek `/etc/systemd/journald.conf` for `Storage=` og sæt den til `persistent`.

---

## 6. `boot.log` — hvorfor kom en service ikke op?

`/var/log/boot.log` viser output fra services under selve boot-sekvensen.

```bash
cat /var/log/boot.log
journalctl -b                              # systemd-ækvivalenten, mere detaljeret
systemctl --failed                         # list alle units der fejlede ved boot
systemctl status <service>                 # detaljeret status + seneste log-linjer
journalctl -u <service> -b                 # servicens log for netop denne boot
systemd-analyze blame                      # hvilke services var langsomst at starte
systemd-analyze critical-chain             # hvad blokerede for hvad
```

---

## 7. `nginx` & `apache` — access + error logs

```bash
tail -f /var/log/nginx/access.log
tail -f /var/log/nginx/error.log
tail -f /var/log/apache2/access.log        # Debian/Ubuntu (RHEL: /var/log/httpd/)
tail -f /var/log/apache2/error.log

awk '{print $1}' /var/log/nginx/access.log | sort | uniq -c | sort -rn | head
                                            # top-IP'er efter antal requests
awk '{print $9}' /var/log/nginx/access.log | sort | uniq -c
                                            # fordeling af HTTP-statuskoder
grep " 500 " /var/log/nginx/access.log     # find server-fejl
```

---

## 8. `cron` — kørte det planlagte job overhovedet?

`/var/log/cron` (RHEL) eller `/var/log/syslog` (Debian/Ubuntu, cron logger ind i syslog) — ellers via journalen.

```bash
grep CRON /var/log/syslog                  # Debian/Ubuntu
cat /var/log/cron                          # RHEL/CentOS
journalctl -u cron                         # systemd-baseret cron-log
journalctl -u cron --since "1 hour ago"
grep "CRON.*<bruger>" /var/log/syslog      # jobs for en specifik bruger
```

Hvis jobbet slet ikke optræder: tjek at crontab findes (`crontab -l -u <bruger>`), at cron-daemonen kører (`systemctl status cron`), og at stien/environment i selve jobbet er korrekt — cron kører med et meget minimalt miljø.

---

## 9. `wtmp` · `btmp` — login-historik (de binære)

Disse er **ikke** tekstfiler — de skal læses med de rigtige værktøjer, ikke `cat`/`grep`.

```bash
last -f /var/log/wtmp          # login-historik (wtmp er default for `last`)
last -x                        # inkl. system boot/shutdown-events
lastb                          # mislykkede login-forsøg, læser btmp (kræver root)
lastlog                        # seneste login pr. bruger, læser /var/log/lastlog
who /var/log/wtmp              # simplere visning
```

Er filerne korrupte eller for store, virker `last`/`lastb` ikke — så er det en tegn på, at nogen har rodet med systemet (eller at loggen aldrig er blevet roteret).

---

## 10. `audit.log` — det forensiske spor

`/var/log/audit/audit.log`, genereret af **auditd** (se også [Security_Hardening.md](Security_Hardening.md) for opsætning). Langt mere detaljeret end syslog: filadgang, syscalls, SELinux-nægtelser, brugerhandlinger — sporbart ned til den enkelte proces og bruger.

```bash
sudo systemctl status auditd
sudo ausearch -m avc -ts recent            # seneste SELinux-nægtelser
sudo ausearch -ua <uid>                    # alt en given bruger har gjort
sudo ausearch -f /etc/passwd               # hvem har rørt en specifik fil
sudo aureport --auth                       # opsummering af autentificeringshændelser
sudo aureport --failed                     # opsummering af mislykkede hændelser
sudo auditctl -w /etc/passwd -p wa -k passwd_changes
                                            # overvåg en fil for skrivning/attributændring
```

---

## 11. `logrotate` — læs roterede & gzippede arkiver

Logs roteres automatisk (typisk dagligt/ugentligt) for ikke at vokse uendeligt. Regler ligger i `/etc/logrotate.conf` og `/etc/logrotate.d/`.

```bash
cat /etc/logrotate.d/nginx                 # se rotationsregler for en specifik service
sudo logrotate -d /etc/logrotate.conf      # dry-run: se hvad der *ville* ske
sudo logrotate -f /etc/logrotate.conf      # tving rotation nu

zcat /var/log/syslog.2.gz | less           # læs en gzippet, roteret logfil
zgrep "error" /var/log/syslog.*.gz         # søg på tværs af alle roterede arkiver
zcat /var/log/syslog.*.gz | cat - /var/log/syslog | grep "error"
                                            # søg i hele historikken, ældst til nyest
```

Navngivningskonventionen er typisk `navn.log`, `navn.log.1` (nyeste roterede, ukomprimeret), `navn.log.2.gz`, `navn.log.3.gz` osv.

---

## 12. Tøm en logfil uden at slette den

```bash
: > fil.txt
```

`:` er en indbygget no-op kommando (returnerer altid succes uden output). Ved at omdirigere dens (tomme) output til filen med `>` bliver filen straks trunkeret til 0 bytes.

Bruges typisk til at tømme store logfiler, fx `: > /var/log/syslog`, uden at slette selve filen — hvilket er vigtigt hvis en anden proces (fx en dæmon) allerede har filen åben via en filhandle. Sletter man filen (`rm`) og opretter en ny, skriver processen stadig til den gamle (nu usynlige) fil, indtil den genstartes. Alternativer med samme effekt: `> fil.txt` eller `truncate -s 0 fil.txt`.

```bash
: > /var/log/syslog
```

---

## Se også

[D.md](D.md) for `dmesg`, [J.md](J.md) for `journalctl`, [T.md](T.md) for `tail`, [G.md](G.md) for `grep`/`zgrep`, [A.md](A.md) for `awk`/`ausearch`/`aureport`, [L.md](L.md) for `last`/`lastb`/`lastlog`/`logrotate`, [S.md](S.md) for `systemctl`/`systemd-analyze`, [Security_Hardening.md](Security_Hardening.md) for opsætning af `auditd`.
