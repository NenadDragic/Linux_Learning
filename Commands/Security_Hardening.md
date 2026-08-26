# Linux Security Hardening

En tjekliste med kommandoer til grundlæggende hardening af et Linux-system. Tilpas efter distro (Debian/RHEL/Arch).

---

## Opdater systemet fuldt

```bash
sudo apt update && sudo apt upgrade -y   # Debian/Ubuntu
sudo dnf update -y                        # RHEL/Fedora
sudo pacman -Syu                          # Arch
```

## Lås root-kontoen for login

```bash
sudo passwd -l root
```

## Firewall — bloker uopfordrede indgående forbindelser

```bash
sudo ufw default deny incoming              # Debian/Ubuntu
sudo firewall-cmd --set-default-zone=drop   # RHEL/Arch
```

## Sæt idle-timeout for sessioner

```bash
echo "export TMOUT=600" | sudo tee -a /etc/bash.bashrc
```

## Hærd SSH

Deaktiver root-login, aktiver SSH-nøgleautentificering og deaktiver adgangskode-login i:

```bash
sudo nano /etc/ssh/sshd_config
```

## Find og gennemgå farlige filrettigheder

```bash
find / -type f -perm -o+w                     # world-writable filer
find / -type d -perm -0002 ! -perm -1000       # world-writable mapper uden sticky bit
find / -type f -perm /6000 -ls                 # filer med SUID/SGID
```

## Fjern ubrugte pakker/afhængigheder

```bash
sudo apt autoremove -y                          # Debian
sudo dnf autoremove -y                          # RHEL
sudo pacman -Rns $(pacman -Qdtq)                # Arch
```

## Inspicér auto-startende services og deaktiver ubrugte

```bash
systemctl list-unit-files --type=service --state=enabled
```

## Tjek alle aktive lyttende porte og luk usikre porte

```bash
ss -tulpan
```

## USB whitelisting — tillad kun aktive enheder, bloker resten

```bash
sudo usbguard generate-policy > /etc/usbguard/rules.conf && sudo systemctl enable --now usbguard
```

## Tjek for usikre legacy-services

```bash
dpkg -l | grep -Ei 'telnet|rsh|xinetd|vsftpd|tftp'   # Debian (brug rpm -qa på RHEL eller pacman -Q på Arch)
```

## Log sikkerhedsrelaterede kernel- og brugerspace-hændelser

```bash
sudo apt install auditd -y && sudo systemctl enable --now auditd
```

## Fuld systemsikkerhedsaudit med anbefalinger

```bash
sudo apt install lynis -y && sudo lynis audit system
```

---

## Se også

[U.md](U.md) for `ufw`/`usbguard`, [F.md](F.md) for `firewall-cmd`, [A.md](A.md) for `apt`/`auditd`, [L.md](L.md) for `lynis`, [P.md](P.md) for `pacman`/`passwd`.
