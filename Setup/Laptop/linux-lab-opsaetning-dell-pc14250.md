# Opsætningsplan: Intro-til-Linux lab

**Maskine:** Dell Pro 14 (PC14250) · Intel Core Ultra · 32 GB RAM · 512 GB NVMe SSD
**Vært-OS:** Ubuntu 24.04 LTS (Desktop) + HWE-kernel
**Virtualisering:** KVM/QEMU + virt-manager
**Formål:** Undervisning i Linux-platformen — CLI, filsystem, pakkehåndtering (apt + dnf), brugere/rettigheder, systemd, simpel netværk. Eleverne arbejder i VM'er og kan nulstille via snapshots.

---

## Fase 0 — BIOS/UEFI og boot-medie

1. Tænd, tryk **F2** ved Dell-logo → UEFI/BIOS.
2. Slå **Intel Virtualization Technology (VT-x)** og **VT for Direct I/O (VT-d)** til (typisk slået til som standard).
3. Lad **Secure Boot** være slået TIL — KVM/libvirts moduler er signeret i Ubuntu, så det giver ingen problemer. (Det ville først blive et tema hvis I senere brugte VirtualBox.)
4. Lav et bootbart USB-stik med **nyeste Ubuntu 24.04.x Desktop ISO** (Rufus/balenaEtcher/`dd`). Brug det seneste punktrelease — det har den nyeste installer-kerne.
5. Boot fra USB (**F12** = engangs-bootmenu).

---

## Fase 1 — Partitionering

Vælg **"Something else" / manuel partitionering** i installeren. Anbefalet layout (ca.-tal — 512 GB ≈ 476 GiB brugbart):

| Partition | Størrelse | Filsystem | Mountpoint | Hvorfor |
|---|---|---|---|---|
| EFI System (ESP) | 1 GB | FAT32 | `/boot/efi` | Boot |
| Rod | 80 GB | ext4 | `/` | Vært-OS + programmer |
| Hjem | 40 GB | ext4 | `/home` | Brugerdata adskilt fra OS |
| VM-pulje | ~resten (~340 GB) | ext4 | `/var/lib/libvirt/images` | **Isolerer VM-diske fra `/`** |
| Swap | 8 GB | swap | — | Rigeligt ved 32 GB RAM (uden dvale) |

> **Enklere variant** (hvis manuel partitionering er for meget): brug guided/"Erase disk", som laver ESP + rod + swapfil automatisk. VM'erne lander så på rod-partitionen — fungerer fint, men du mister isoleringen ved punkt 1 i beslutningerne.
>
> **LVM** er valgfrit. Det giver nem resize senere, men tilføjer kompleksitet — til et intro-lab er almindelige ext4-partitioner nemmere at fejlfinde og forklare.

Fortsæt installationen normalt (sprog, tastatur, bruger). Vælg "Minimal installation" hvis du vil holde værten ren.

---

## Fase 2 — Vært: opdater og sæt HWE-kernel

```bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install -y linux-generic-hwe-24.04
sudo reboot
```

Efter genstart, bekræft nyere kerne (forvent 6.11 eller nyere):

```bash
uname -r
```

---

## Fase 3 — Installér KVM/QEMU + virt-manager

```bash
sudo apt install -y qemu-kvm libvirt-daemon-system libvirt-clients \
                    bridge-utils virtinst virt-manager ovmf cpu-checker
```

Tilføj din bruger til grupperne (så du slipper for sudo til VM'er):

```bash
sudo usermod -aG libvirt,kvm $USER
```

Aktivér og start libvirt:

```bash
sudo systemctl enable --now libvirtd
```

**Log ud og ind igen** (eller genstart), så gruppemedlemskabet træder i kraft.

Bekræft at hardware-acceleration virker:

```bash
kvm-ok
```

Forventet output: *"KVM acceleration can be used"*.

---

## Fase 4 — Netværk og storage-pulje

Standard-NAT-netværket er det rette til et lab: VM'erne får internet og er isoleret fra LAN'et.

```bash
virsh net-list --all
sudo virsh net-start default      # hvis det ikke allerede er aktivt
sudo virsh net-autostart default
```

Bekræft at standard-storage-puljen peger på din VM-partition:

```bash
virsh pool-list --all
virsh pool-dumpxml default | grep path     # skal vise /var/lib/libvirt/images
```

---

## Fase 5 — Opret gæste-VM'er (undervisningsmiljøerne)

Hent ISO-filer til `/var/lib/libvirt/images/`:

- **Ubuntu** (apt-familien) — primært miljø.
- **Fedora** eller **Rocky/AlmaLinux** (dnf-familien) — så eleverne ser den anden økosystem-side.

Anbefalede specs pr. intro-VM: **2 vCPU · 4 GB RAM · 30 GB qcow2-disk** (thin — fylder kun det skrevne).

**Nemmest:** opret via virt-manager (GUI) → "Create a new virtual machine" → peg på ISO.

**Via kommandolinje (eksempel, Ubuntu-gæst):**

```bash
virt-install \
  --name ubuntu-lab \
  --memory 4096 \
  --vcpus 2 \
  --disk path=/var/lib/libvirt/images/ubuntu-lab.qcow2,size=30,format=qcow2 \
  --cdrom /var/lib/libvirt/images/ubuntu-24.04.iso \
  --os-variant ubuntu24.04 \
  --graphics spice \
  --network network=default
```

(Til Fedora-gæst: skift `--os-variant` til fx `fedora40` og peg på Fedora-ISO'en.)

---

## Fase 6 — Snapshots (den vigtigste undervisningsfunktion)

Når en gæst er installeret rent, tag et snapshot — så eleverne kan eksperimentere og rulle tilbage.

**virt-manager:** Åbn VM → fanen *Snapshots* → **+**.

**Kommandolinje:**

```bash
# Tag rent snapshot
virsh snapshot-create-as --domain ubuntu-lab clean "Frisk installation"

# Vis snapshots
virsh snapshot-list ubuntu-lab

# Rul tilbage til ren tilstand (efter eleverne har "ødelagt" noget)
virsh snapshot-revert ubuntu-lab clean
```

Snapshots virker rent med qcow2-diske.

---

## Fase 7 — Flere elever / nulstilling (valgfrit)

- **Golden image + kloner:** byg én VM, og lav derefter kloner til flere elev-miljøer:
  ```bash
  virt-clone --original ubuntu-lab --name elev01 --auto-clone
  ```
  (Brug *linked clones* hvis du vil spare disk — de deler basis-imaget.)
- **Eller** bare `snapshot-revert` mellem hold/sessioner.
- **Klon hele værten** til andre identiske Dell-enheder med fx Clonezilla, hvis hele lab'et skal udrulles.

---

## Disk-budget i praksis

- Vært-OS bruger ~30 GB. VM-puljen har ~340 GB.
- Med 30 GB thin-VM'er er der plads til ~10 images, men kør kun **2–3 ad gangen** (RAM/CPU sætter grænsen, ikke disk).
- Til et intro-forløb er **én Ubuntu-gæst + én dnf-gæst** rigeligt.
- Fylder disken op senere: M.2-disken er udskiftelig på PC14250 → opgradér til 1–2 TB NVMe.

---

## Hurtig tjekliste

- [ ] VT-x/VT-d slået til i BIOS
- [ ] Ubuntu 24.04 installeret med separat `/var/lib/libvirt/images`
- [ ] HWE-kernel aktiv (`uname -r` ≥ 6.11)
- [ ] `kvm-ok` siger OK
- [ ] Bruger i `libvirt` + `kvm` grupper
- [ ] `default` NAT-netværk aktivt og autostart
- [ ] Mindst én gæst-VM installeret
- [ ] "clean" snapshot taget på hver gæst
