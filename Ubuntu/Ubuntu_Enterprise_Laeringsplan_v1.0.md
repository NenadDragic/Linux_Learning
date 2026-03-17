# Personal Ubuntu Enterprise Learning Plan
**Version:** 1.0  
**Platform:** Primary PC with Proxmox + Ubuntu 24.04 LTS  
**Updated:** March 2026

---

## Overview

| Phase | Weeks | Focus |
|-------|-------|-------|
| Foundation | 0–3 | Proxmox lab, Ubuntu basics, networking, firewall |
| Automation | 4–6 | Ansible, Nginx/TLS, CI/CD pipeline |
| Identity & Security | 7–9 | FreeIPA, AppArmor, Ubuntu Pro/CIS |
| Observability & Alerting | 10–11 | Prometheus + Grafana + Loki + PagerDuty/Opsgenie |
| Cloud Provider Fundamentals | 12 | AWS/Azure CLI, IAM, cloud networking basics |
| Python for Ops | 13 | Python scripting for cloud operations |
| Containers & Orchestration | 14–16 | Docker, k3s, Ingress, TLS |
| Resilience | 17–18 | Backup/restore, HA with HAProxy + Keepalived |
| ITSM & Operations Practice | 19–20 | Runbooks, ITIL, ticketing, SLA/SLO/SLI, change mgmt |
| Consolidation & Mastery | 21–28 | Drills, tuning, end-to-end rehearsals, certification prep |

---

## Lab Architecture

```
Proxmox Host (Primary PC)
├── vmbr0        — Management VLAN 10 (10.10.10.0/24)
├── vmbr1        — Application VLAN 20 (10.10.20.0/24)
└── vmbr2        — Storage/backup VLAN 30 (10.10.30.0/24)

VMs
├── mgmt01       — Ansible control node, Gitea, Woodpecker CI
├── idm01        — FreeIPA identity server
├── srv01–srv02  — Application servers (nginx, docker workloads)
├── monitor01    — Prometheus + Grafana + Loki + Zabbix
├── k8s-cp01     — k3s control plane
├── k8s-wk01     — k3s worker node
└── backup01     — Restic repository server
```

---

## Week 0: Preparation (2 hours)

### Tasks
- [ ] Download Proxmox VE ISO and verify checksum
- [ ] Plan VLAN layout and IP addressing (see Lab Architecture above)
- [ ] Create Git repo with structure: `/docs`, `/ansible`, `/scripts`, `/diagrams`, `/terraform`, `/runbooks`
- [ ] Read through this plan and mark your start date

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Proxmox VE — Network Configuration | https://pve.proxmox.com/wiki/Network_Configuration |
| 📄 Docs | Ansible — Getting Started | https://docs.ansible.com/ansible/latest/getting_started/index.html |

---

## Week 1: Proxmox + First Ubuntu VM

### Tasks
- [ ] Install Proxmox VE on primary PC
- [ ] **Configure storage pools**: understand `local-lvm` (VM disks) vs. `local` (ISOs/backups). Consider ZFS if hardware allows — enables snapshots at no cost
- [ ] Create VLAN-aware bridges: `vmbr0` (VLAN 10, management), `vmbr1` (VLAN 20, apps)
- [ ] Create `mgmt01` (Ubuntu 24.04 LTS) on VLAN 10
- [ ] Set up SSH key authentication on `mgmt01`, disable password login
- [ ] **Configure Proxmox Backup Server (PBS) or at minimum local backup jobs** — before adding more VMs, establish a snapshot habit

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Proxmox VE — Network Configuration | https://pve.proxmox.com/wiki/Network_Configuration |
| 📄 Docs | Proxmox VE — Storage | https://pve.proxmox.com/wiki/Storage |
| 📄 Docs | Proxmox Backup Server — Getting Started | https://pbs.proxmox.com/docs/getting-started.html |
| 📄 Docs | Ubuntu Server — Automatic Updates | https://documentation.ubuntu.com/server/how-to/software/automatic-updates/ |
| 🎬 Video | Proxmox Full Course — Learn Linux TV | https://www.youtube.com/watch?v=LCjuiIswXGs |

---

## Week 2: Ubuntu Operations — systemd, Logging, Patching

### Tasks
- [ ] Create `srv01` (Ubuntu 24.04 LTS) on VLAN 20
- [ ] Configure `unattended-upgrades` (security only) and understand `apt-daily` timers
- [ ] Install `needrestart` — alerts when services need restarting after kernel/lib updates
- [ ] Build a systemd service that crashes intentionally; debug with `journalctl -u`, `-b`, `--since`
- [ ] Understand `systemctl list-timers` and create a custom systemd timer
- [ ] **Write your first runbook**: document the steps to diagnose and recover a failed systemd service. Store it in `/runbooks/systemd-service-recovery.md`. Write a runbook for every incident drill from this point forward

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Ubuntu Server — Automatic Updates | https://documentation.ubuntu.com/server/how-to/software/automatic-updates/ |
| 📄 Docs | Ubuntu Server — systemd (OneUptime) | https://oneuptime.com/blog/post/2026-01-07-ubuntu-systemd-management/view |
| 📄 Docs | systemd.service man page | https://www.freedesktop.org/software/systemd/man/latest/systemd.service.html |
| 🎬 Video | Systemd Deep Dive — Learn Linux TV | https://www.youtube.com/watch?v=5JVBpXiYMKo |

---

## Week 3: Networking + Firewall + Baseline Security

### Tasks
- [ ] Create `srv02` (Ubuntu 24.04 LTS) on VLAN 20
- [ ] **Netplan**: configure static IPs; test safely with `netplan try` before applying
- [ ] **VLAN tagging practice**: assign `srv01` to VLAN 20 and verify it cannot reach `mgmt01` on VLAN 10 without explicit routing — fundamental enterprise network segmentation
- [ ] **UFW**: set `default deny incoming`, allow SSH only from `mgmt01`'s IP, allow app ports only on VLAN 20
- [ ] **Fail2ban**: install, configure `jail.local`, enable `sshd` jail, test with intentional failed logins
- [ ] Verify with `ss -tlnp` and `nmap` from another VM that only expected ports are open
- [ ] **Log analysis exercise**: after the Fail2ban test, find the brute-force attempts in `/var/log/auth.log` manually using `grep` and `awk`. Practice reading logs — not just reacting to alerts

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Ubuntu Server — Networking (Netplan) | https://documentation.ubuntu.com/server/how-to/networking/ |
| 📄 Docs | Ubuntu Server — Firewall (UFW) | https://ubuntu.com/server/docs/how-to/security/firewalls/ |
| 📄 Docs | Ubuntu Community — UFW | https://help.ubuntu.com/community/UFW |
| 📄 Docs | Ubuntu Community — Fail2ban | https://help.ubuntu.com/community/Fail2ban |
| 🎬 Video | UFW Firewall Tutorial — Learn Linux TV | https://www.youtube.com/watch?v=nEDeCYCXqZ4 |

---

## Week 4: Ansible Intro — Inventory + First Playbook

### Tasks
- [ ] Install Ansible on `mgmt01`
- [ ] Build inventory for `srv01` and `srv02` with group variables
- [ ] Write `site.yml` playbook — install packages, create users, configure UFW
- [ ] Test and enforce **idempotency**: run the playbook twice, confirm no changes on second run
- [ ] **Ansible Vault**: encrypt at least one variable (a password or API key). Never commit plaintext secrets to Git — establish this habit now

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Ansible — Getting Started | https://docs.ansible.com/ansible/latest/getting_started/index.html |
| 📄 Docs | Ansible — Build Your Inventory | https://docs.ansible.com/ansible/latest/network/getting_started/first_inventory.html |
| 📄 Docs | Ansible — Vault (secrets encryption) | https://docs.ansible.com/ansible/latest/vault_guide/index.html |
| 📄 Docs | Ansible — Best Practices | https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html |
| 🎬 Video | Ansible Full Course — Learn Linux TV | https://www.youtube.com/watch?v=w9eCU4bGgjQ |

---

## Week 5: Ansible Roles + CI/CD Pipeline

### Tasks
- [ ] Refactor playbooks into roles (`baseline`, `nginx`, `docker`)
- [ ] Use `tags`, `handlers`, `group_vars`, `host_vars`
- [ ] **Install Gitea on `mgmt01`** (self-hosted Git) — push your Ansible repo to it
- [ ] **Install Woodpecker CI** — configure a pipeline that:
  - Runs `ansible-lint` on every push
  - Runs `yamllint` on playbooks
  - Optionally: runs `ansible-playbook --check` (dry-run) against inventory
- [ ] This mirrors the enterprise workflow: commit → lint → dry-run → manual approve → apply

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Ansible — Roles | https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html |
| 📄 Docs | LearnAnsible.dev — Roles Best Practices | https://learnansible.dev/article/Ansible_Roles_Best_Practices_and_Examples.html |
| 📄 Docs | Ansible — Best Practices | https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html |
| 📄 Docs | Gitea — Installation | https://docs.gitea.com/installation/install-from-binary |
| 📄 Docs | Woodpecker CI — Getting Started | https://woodpecker-ci.org/docs/intro |
| 🎬 Video | Ansible Roles Tutorial — TechWorld with Nana | https://www.youtube.com/watch?v=i_mBRGbHMso |

---

## Week 6: Web + TLS + Fault Tolerance

### Tasks
- [ ] Deploy Nginx via Ansible role
- [ ] Add TLS with Let's Encrypt (if internet-accessible) or self-signed cert otherwise
- [ ] **Break/fix exercise**: introduce a deliberate syntax error in nginx config, observe failure, roll back with Ansible using `--check` + `--diff`
- [ ] Configure Nginx as a reverse proxy for a simple backend
- [ ] **Write a change request document** for the Nginx deployment: what changed, rollback plan, test criteria. Every significant change in the lab should be treated as if it needs approval — this mirrors real driftcenter practice

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Ubuntu Server — Configure Nginx | https://documentation.ubuntu.com/server/how-to/web-services/configure-nginx/ |
| 📄 Docs | nginx.org — Configuring HTTPS servers | https://nginx.org/en/docs/http/configuring_https_servers.html |
| 🎬 Video | Nginx Crash Course — Traversy Media | https://www.youtube.com/watch?v=7VAI73roXaY |

---

## Week 7: Identity — FreeIPA + SSSD

### Tasks
- [ ] Create `idm01` VM (min. 2GB RAM, correct FQDN and DNS configured before install)
- [ ] Install FreeIPA server on `idm01`
- [ ] Enroll `srv01`, `srv02`, and `mgmt01` as FreeIPA clients via SSSD
- [ ] **Integrate FreeIPA actively throughout the rest of the lab**:
  - Create IPA user groups (`admins`, `webops`)
  - Configure sudo rules in IPA (not in local `/etc/sudoers`)
  - Verify a FreeIPA user can SSH to `srv01` and run sudo without a local account

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | FreeIPA — Quick Start Guide | https://www.freeipa.org/page/Quick_Start_Guide |
| 📄 Docs | HowtoForge — Add Ubuntu to FreeIPA | https://www.howtoforge.com/how-to-add-ubuntu-system-to-freeipa-server/ |
| 📄 Docs | Kifarunix — FreeIPA Client on Ubuntu 24.04 | https://kifarunix.com/install-and-configure-freeipa-client-on-ubuntu-24-04/ |
| 📄 Docs | Ubuntu Server — SSSD | https://documentation.ubuntu.com/server/how-to/sssd/ |

---

## Week 8: AppArmor — Profiles + Enforcement

### Tasks
- [ ] Check status with `aa-status`; understand `complain` vs. `enforce` mode
- [ ] Put at least one profile (e.g., nginx) in enforce mode
- [ ] Deliberately trigger a denial; read it in `journalctl` or `/var/log/syslog`
- [ ] Use `aa-genprof` to build a profile for a custom script

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Ubuntu Server — AppArmor | https://documentation.ubuntu.com/server/how-to/security/apparmor/ |
| 🎬 Video | AppArmor Tutorial — LearnLinux.tv | https://www.youtube.com/watch?v=DgrEGoFrOFk |

---

## Week 9: Ubuntu Pro — ESM + Livepatch + CIS Hardening

### Tasks
- [ ] Attach Ubuntu Pro (free for up to 5 machines: `ubuntu.com/pro`)
- [ ] Enable ESM-infra and ESM-apps; observe the expanded patch count
- [ ] Enable Livepatch on `srv01` — understand when it patches vs. when a reboot is still needed
- [ ] Run `usg audit` against CIS Level 1 profile; document findings
- [ ] Fix at least 5 CIS findings with Ansible — don't fix manually, automate it

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Ubuntu Pro — What's Included | https://documentation.ubuntu.com/pro/services-overview/ |
| 📄 Docs | Ubuntu Pro Client — Enable CIS/USG | https://documentation.ubuntu.com/pro-client/en/latest/howtoguides/enable_cis/ |
| 📄 Docs | Ubuntu — CIS Benchmark | https://ubuntu.com/security/cis |

---

## Week 10: Full Observability Stack

> Three-pillar observability: **metrics + logs + dashboards**.

### Tasks
- [ ] Create `monitor01` VM
- [ ] **Prometheus**: install on `monitor01`, configure scrape intervals
- [ ] **Node Exporter**: deploy to all nodes via Ansible role (CPU, memory, disk, network)
- [ ] **Grafana**: install, connect Prometheus, import Node Exporter dashboard (ID: 1860)
- [ ] **Grafana Alloy**: install as log agent on all nodes (replaces deprecated Promtail)
- [ ] **Loki**: install on `monitor01`, configure Alloy to ship logs, add Loki as Grafana data source
- [ ] Create alert rules: disk > 80%, service down, SSH failure rate > 10/min

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Prometheus — Getting Started | https://prometheus.io/docs/prometheus/latest/getting_started/ |
| 📄 Docs | DigitalOcean — Install Prometheus on Ubuntu | https://www.digitalocean.com/community/tutorials/how-to-install-prometheus-on-ubuntu-16-04 |
| 📄 Docs | Grafana Alloy — Installation | https://grafana.com/docs/alloy/latest/set-up/install/ |
| 📄 Docs | Grafana Loki — Promtail deprecation + Alloy migration | https://grafana.com/docs/loki/latest/send-data/promtail/ |
| 📄 Docs | OTC — Migrating from Promtail to Grafana Alloy | https://arch.otc-service.com/docs/blueprints/by-use-case/observability/migrate-from-promtail-to-grafana-alloy |
| 🎬 Video | Prometheus + Grafana Tutorial — TechWorld with Nana | https://www.youtube.com/watch?v=h4Sl21AKiDg |

---

## Week 11: Alert Routing — PagerDuty / Opsgenie

> Seeing an alert in Grafana is not enough. In a driftcenter, alerts must reach the right person automatically — at any hour.

### Tasks
- [ ] Sign up for PagerDuty or Opsgenie (both have free tiers)
- [ ] Connect Grafana alerting to PagerDuty/Opsgenie via webhook
- [ ] Configure an **on-call schedule** with an escalation policy
- [ ] Test the full chain: trigger a real alert (fill disk to >80%) → Grafana fires → PagerDuty/Opsgenie notifies
- [ ] Practice **acknowledging and resolving** alerts — understand ack vs. resolve
- [ ] Configure a scheduled silence for planned maintenance windows

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | PagerDuty — Getting Started | https://support.pagerduty.com/docs/introduction |
| 📄 Docs | Opsgenie — Getting Started | https://docs.opsgenie.com/docs/getting-started |
| 📄 Docs | Grafana — PagerDuty integration | https://grafana.com/docs/grafana/latest/alerting/configure-notifications/manage-contact-points/integrations/pagerduty/ |
| 🎬 Video | PagerDuty Introduction | https://www.youtube.com/watch?v=2a_hIk7cMZs |

---

## Week 12: Cloud Provider Fundamentals

> Your lab runs on-prem, but cloud drift means working directly against AWS, Azure, or GCP.

### Tasks
- [ ] Create a free-tier account on AWS **or** Azure — go deep on one rather than shallow on both
- [ ] Install `awscli` or `az cli` on `mgmt01`
- [ ] **Hands-on with core concepts**:
  - Compute: launch and terminate a VM instance (EC2 / Azure VM)
  - Networking: security groups / NSGs — how they map to UFW concepts you already know
  - Storage: create and attach a block volume; create a storage bucket
  - IAM: create a service account with least-privilege; understand roles vs. policies
- [ ] SSH into your cloud VM from `mgmt01` using key authentication
- [ ] Run your Ansible `baseline` role against the cloud VM — your automation should work with minimal changes
- [ ] **Terminate all resources when done** — understand cost management from day one

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | AWS — Getting Started with EC2 | https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html |
| 📄 Docs | AWS CLI — Getting Started | https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html |
| 📄 Docs | Azure — Create a Linux VM | https://learn.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-cli |
| 📄 Docs | Azure CLI — Getting Started | https://learn.microsoft.com/en-us/cli/azure/get-started-with-azure-cli |
| 🎬 Video | AWS Fundamentals Full Course — freeCodeCamp | https://www.youtube.com/watch?v=ulprqHHWlng |
| 🎬 Video | Azure Fundamentals Full Course — freeCodeCamp | https://www.youtube.com/watch?v=NKEFWyqJ5XA |

---

## Week 13: Python for Ops

> Cloud operations in 2026 expects Python for API calls, JSON parsing, and automation beyond shell scripting.

### Tasks
- [ ] Learn Python basics if needed: variables, loops, functions, dictionaries, error handling
- [ ] **Write these four practical ops scripts**:
  1. Query the Prometheus HTTP API and print the top 3 hosts by CPU usage
  2. Read a log file, filter lines matching a pattern, write a summary report
  3. Use `boto3` or `azure-sdk` to list all running VMs and their states
  4. Health-check script: ping a list of services, send an alert if any are down
- [ ] Add a Python lint step (`flake8`) to your Woodpecker CI pipeline

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Python — Official Tutorial | https://docs.python.org/3/tutorial/ |
| 📄 Docs | boto3 — AWS SDK for Python | https://boto3.amazonaws.com/v1/documentation/api/latest/index.html |
| 📄 Docs | Prometheus HTTP API | https://prometheus.io/docs/prometheus/latest/querying/api/ |
| 🎬 Video | Python for Beginners Full Course — freeCodeCamp | https://www.youtube.com/watch?v=eWRfhZUzrAc |
| 🎬 Video | Python for Network Engineers — NetworkChuck | https://www.youtube.com/watch?v=xZFEFxWMoG8 |

---

## Week 14: Containers on Ubuntu (Docker)

### Tasks
- [ ] Install Docker Engine on Ubuntu 24.04 (use the official Docker apt repo, not snap)
- [ ] **Docker + UFW security hole**: Docker bypasses UFW by writing directly to `iptables`. Fix this with `ufw-docker` or the `DOCKER-USER` chain. Verify with `nmap` that published ports UFW should block are actually blocked
- [ ] Deploy a multi-container app with Docker Compose
- [ ] Write a Dockerfile for a simple custom app; build, push to a local registry, pull and run

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Docker Docs — Install Docker Engine on Ubuntu | https://docs.docker.com/engine/install/ubuntu/ |
| 📄 Docs | ufw-docker — Fix Docker UFW bypass | https://github.com/chaifeng/ufw-docker |
| 📄 Docs | Docker Compose — Getting Started | https://docs.docker.com/compose/gettingstarted/ |
| 🎬 Video | Docker Tutorial for Beginners — TechWorld with Nana | https://www.youtube.com/watch?v=pg19Z8LL06w |

---

## Week 15: Kubernetes (k3s) — Control Plane

### Tasks
- [ ] Create `k8s-cp01` VM (min. 2 vCPU, 2GB RAM)
- [ ] Install k3s on `k8s-cp01`
- [ ] Configure `kubeconfig` for `kubectl` access from `mgmt01`
- [ ] Deploy a test workload (nginx deployment + service)
- [ ] Understand `kubectl get`, `describe`, `logs`, `exec`

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | k3s — Installation | https://docs.k3s.io/installation |
| 📄 Docs | OneUptime — Install k3s on Ubuntu | https://oneuptime.com/blog/post/2026-02-02-k3s-installation-ubuntu/view |
| 🎬 Video | Kubernetes Full Course — TechWorld with Nana | https://www.youtube.com/watch?v=X48VuDVv0do |

---

## Week 16: Kubernetes Worker + Ingress + TLS

### Tasks
- [ ] Create `k8s-wk01` VM; join to cluster with k3s agent token
- [ ] Confirm `kubectl get nodes` shows both nodes as `Ready`
- [ ] Configure Traefik Ingress (bundled with k3s) to route traffic to a deployed app
- [ ] Add TLS using cert-manager and a self-signed issuer

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | k3s — Installation (worker join) | https://docs.k3s.io/installation |
| 📄 Docs | DigitalOcean — k3s Cluster on Ubuntu | https://www.digitalocean.com/community/tutorials/how-to-setup-k3s-kubernetes-cluster-on-ubuntu |
| 📄 Docs | cert-manager — Getting Started | https://cert-manager.io/docs/getting-started/ |

---

## Week 17: Backup + Restore + Disaster Drills

### Tasks
- [ ] Create `backup01` VM on VLAN 30 (isolated storage network)
- [ ] Initialize a Restic repository on `backup01`
- [ ] Back up `/etc`, `/var/www`, `/home` from `srv01` and `srv02`
- [ ] **Restore to a different machine** — not the same one. This is the only way to know the backup works
- [ ] Simulate disk failure: delete critical files, restore from Restic, time yourself
- [ ] Automate daily backups with a systemd timer
- [ ] Document your **RPO** (how much data can you lose?) and **RTO** (how long to restore?) — these come up in every driftcenter SLA conversation

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Restic — Introduction / Quickstart | https://restic.readthedocs.io/en/stable/010_introduction.html |
| 📄 Docs | Restic — Full Documentation | https://restic.readthedocs.io/en/latest/ |
| 🎬 Video | Linux Backup with Restic — Learn Linux TV | https://www.youtube.com/watch?v=oFMSZ-bkEs8 |

---

## Week 18: High Availability — HAProxy + Keepalived

### Tasks
- [ ] Install HAProxy on two VMs; configure a shared Virtual IP (VIP) with Keepalived
- [ ] Test failover: shut down the primary, confirm VIP moves to secondary within seconds
- [ ] Configure HAProxy health checks so traffic only routes to healthy backends
- [ ] Document your actual measured RTO

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Kifarunix — HA HAProxy + Keepalived on Ubuntu | https://kifarunix.com/configure-highly-available-haproxy-with-keepalived-on-ubuntu/ |
| 📄 Docs | MKBN-Tech — HAProxy + Keepalived | https://www.mkbntech.com/posts/haproxy-keepalived/ |
| 🎬 Video | Load Balancing with Nginx — TechWorld with Nana | https://www.youtube.com/watch?v=a41jxGP9Ic8 |

---

## Week 19: ITSM, Runbooks and Change Management

> This week is about process, not technology. In a driftcenter, how you handle changes and incidents matters as much as technical skill.

### Tasks
- [ ] **Learn ITIL basics** — the four processes relevant to driftcenter work:
  - **Incident management**: something is broken — fix it fast
  - **Problem management**: something keeps breaking — find root cause
  - **Change management**: planned changes — approval, testing, rollback plan
  - **Service request management**: routine tasks — handled by runbook
- [ ] **Set up a ticketing system**: install Zammad (self-hosted, free) on `mgmt01` or use a free Jira Service Management cloud account
- [ ] **Simulate a full incident workflow**:
  1. A Grafana alert fires (disk full on `srv01`)
  2. PagerDuty/Opsgenie notifies you
  3. You create a ticket in the ticketing system
  4. You follow your runbook to resolve it
  5. You close the ticket with a resolution note and post-incident summary
- [ ] **Write three runbooks** in `/runbooks/`:
  - `disk-full-recovery.md`
  - `service-restart-procedure.md`
  - `ssh-login-failure-investigation.md`
- [ ] A good runbook contains: trigger condition, severity, step-by-step resolution, escalation path, rollback procedure

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | ITIL 4 Foundation — overview | https://www.axelos.com/certifications/itil-service-management/itil-4-foundation |
| 📄 Docs | Zammad — Getting Started | https://docs.zammad.org/en/latest/ |
| 📄 Docs | Jira Service Management — Getting Started | https://www.atlassian.com/software/jira/service-management/guides |
| 🎬 Video | ITIL 4 Foundation Crash Course | https://www.youtube.com/watch?v=HloTigHUk8I |

---

## Week 20: SLA, SLO, SLI and Network Monitoring

> You will work with these concepts every day in a driftcenter. Understanding them is non-negotiable.

### Tasks
- [ ] **Learn the definitions**:
  - **SLI** (Service Level Indicator): the actual measured metric — e.g. "uptime was 99.94% this month"
  - **SLO** (Service Level Objective): the internal target — e.g. "we aim for 99.9% uptime"
  - **SLA** (Service Level Agreement): the contract with the customer — e.g. "we guarantee 99.5% uptime"
  - **Error budget**: the allowed downtime before SLA breach — 99.9% = 43.8 minutes/month
- [ ] **Define SLOs for your lab**: what is your uptime target for `srv01`? For the k3s cluster? Write them down
- [ ] Calculate: if your SLA is 99.9%, how many minutes of downtime are allowed per month? Per year?
- [ ] **SNMP/network monitoring**: install Zabbix on `monitor01`. Configure SNMP polling of your Proxmox host. Create a network availability dashboard — this is what driftcenters use for infrastructure visibility

### Resources
| Type | Title | URL |
|------|-------|-----|
| 📄 Docs | Google SRE Book — SLIs, SLOs, SLAs | https://sre.google/sre-book/service-level-objectives/ |
| 📄 Docs | Zabbix — Getting Started | https://www.zabbix.com/documentation/current/en/manual/quickstart |
| 🎬 Video | SLI, SLO, SLA Explained — TechWorld with Nana | https://www.youtube.com/watch?v=tEylFyxbDLE |
| 🎬 Video | Zabbix Tutorial for Beginners — Learn Linux TV | https://www.youtube.com/watch?v=x0DNKPGIQuE |

---

## Weeks 21–28: Consolidation & Mastery

> Each consolidation week has a **concrete measurable goal**.

### Week 21 — Compliance Deep Dive
**Goal:** Achieve CIS Level 1 compliance on `srv01` enforced via Ansible.
- Run `usg audit`; document all failures
- Write Ansible tasks to fix every finding; re-run to confirm zero failures
- Push to Gitea; CI pipeline validates on every change

| 📄 | Ubuntu Pro Client — Enable CIS/USG | https://documentation.ubuntu.com/pro-client/en/latest/howtoguides/enable_cis/ |
|----|------------------------------------|--------------------------------------------------------------------------------|
| 📄 | Ubuntu — CIS | https://ubuntu.com/security/cis |

---

### Week 22 — Patch Strategy + Change Management
**Goal:** Define and document a formal patch policy; write and submit a change request for a planned patch cycle.
- Compare `livepatch status` vs. `needs-restarting -r`
- Document: which services get maintenance windows? Which get Livepatch?
- Write a full change request: scope, rollback plan, test criteria, approval (even if you approve it yourself)

| 📄 | Ubuntu Server — Automatic Updates | https://documentation.ubuntu.com/server/how-to/software/automatic-updates/ |
|----|-----------------------------------|-----------------------------------------------------------------------------|
| 📄 | Ubuntu Pro — Services Overview | https://documentation.ubuntu.com/pro/services-overview/ |

---

### Week 23 — AppArmor Advanced
**Goal:** Write a custom AppArmor profile from scratch; enforce with zero false denials.
- Use `aa-genprof` to capture a baseline, tune with `aa-logprof`
- Commit the profile to your Ansible repo so it deploys automatically

| 📄 | Ubuntu Server — AppArmor | https://documentation.ubuntu.com/server/how-to/security/apparmor/ |
|----|--------------------------|---------------------------------------------------------------------|

---

### Week 24 — Ansible Repo Best Practices
**Goal:** Your Ansible repo passes `ansible-lint` with zero warnings; CI blocks any merge that fails.
- All secrets in Vault; no plaintext credentials anywhere
- Every role has a README with usage examples

| 📄 | Ansible — Best Practices | https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html |
|----|--------------------------|-------------------------------------------------------------------------------|

---

### Week 25 — Observability Tuning + Alert Fatigue
**Goal:** Every alert that fires is actionable — no noise, no false positives.
- Review all alert rules; remove or tune any that fire unnecessarily
- Every alert must have a corresponding runbook entry
- Document the on-call escalation policy in writing

| 📄 | Google SRE Book — Practical Alerting | https://sre.google/sre-book/practical-alerting/ |
|----|--------------------------------------|--------------------------------------------------|

---

### Week 26 — Incident Response Drill
**Goal:** Investigate and resolve a simulated incident in under 30 minutes. Write a full incident report.
- Inject a fault: failing service, disk fill, memory leak, or brute-force attempt
- Triage using `journalctl`, Grafana, Loki
- Write a post-incident report: timeline, root cause, fix, prevention
- Log it as a closed ticket in your ticketing system

| 📄 | OneUptime — systemd Management | https://oneuptime.com/blog/post/2026-01-07-ubuntu-systemd-management/view |
|----|--------------------------------|---------------------------------------------------------------------------|

---

### Week 27 — Hardening Pass + Least Privilege Audit
**Goal:** No service runs as root unnecessarily; all sudo managed by FreeIPA; second CIS audit shows improvement.
- Audit: `systemctl list-units --type=service --state=running`
- Verify FreeIPA-managed sudo rules are the only sudo source on all enrolled nodes
- Run a second CIS audit and document improvement vs. Week 21

| 📄 | Ubuntu Server — AppArmor | https://documentation.ubuntu.com/server/how-to/security/apparmor/ |
|----|--------------------------|---------------------------------------------------------------------|
| 📄 | Ubuntu — CIS | https://ubuntu.com/security/cis |

---

### Week 28 — End-to-End Rehearsal
**Goal:** Rebuild the entire lab from scratch in under 4 hours using only Ansible, scripts, and documentation. Nothing manual.

**Checklist:**
- [ ] All VMs provisioned via Proxmox API or `qm` CLI
- [ ] `ansible-playbook site.yml` configures everything: users, UFW, FreeIPA enrollment, Nginx, Docker, monitoring agents
- [ ] Backup restored from Restic on `backup01`
- [ ] k3s cluster running with workloads deployed
- [ ] Grafana dashboards populated, alerts active, PagerDuty/Opsgenie connected
- [ ] Ticketing system running with at least one test incident logged and closed
- [ ] Zero manual steps that are not documented in a runbook

| 📄 | Restic — Quickstart | https://restic.readthedocs.io/en/stable/010_introduction.html |
|----|---------------------|---------------------------------------------------------------|
| 📄 | Ansible — Best Practices | https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html |

---

## Certification Roadmap

Certifications validate your skills to a new employer and provide structured learning milestones. Recommended order for cloud drift / driftcenter roles:

| Priority | Certification | Focus | Cost | URL |
|----------|--------------|-------|------|-----|
| 1st | **CompTIA Linux+ XK0-006** | Linux admin, automation, cloud, CI/CD | ~$230 | https://www.comptia.org/certifications/linux |
| 2nd | **LPIC-1** | Vendor-neutral Linux, valid 5 years | ~$200 | https://www.lpi.org/our-certifications/lpic-1-overview |
| 3rd | **AWS Cloud Practitioner** or **AZ-900** | Cloud fundamentals — pick your employer's platform | ~$100 | https://aws.amazon.com/certification/ |
| 4th | **ITIL 4 Foundation** | ITSM processes, incident and change management | ~$350 | https://www.axelos.com/certifications/itil-service-management/itil-4-foundation |

> CompTIA Linux+ XK0-006 (released July 2025) includes strong emphasis on automation, CI/CD pipelines, cloud, and basic Python — directly aligned with this plan.

---

## Master Resource List

### Official Documentation
| Title | URL |
|-------|-----|
| Ubuntu Server documentation | https://documentation.ubuntu.com/server/ |
| Ubuntu Server — Automatic Updates | https://documentation.ubuntu.com/server/how-to/software/automatic-updates/ |
| Ubuntu Server — Networking (Netplan) | https://documentation.ubuntu.com/server/how-to/networking/ |
| Ubuntu Server — Firewall (UFW) | https://ubuntu.com/server/docs/how-to/security/firewalls/ |
| Ubuntu Server — AppArmor | https://documentation.ubuntu.com/server/how-to/security/apparmor/ |
| Ubuntu Server — Configure Nginx | https://documentation.ubuntu.com/server/how-to/web-services/configure-nginx/ |
| Ubuntu Server — SSSD | https://documentation.ubuntu.com/server/how-to/sssd/ |
| Ubuntu Pro — Services Overview | https://documentation.ubuntu.com/pro/services-overview/ |
| Ubuntu Pro Client — Enable CIS/USG | https://documentation.ubuntu.com/pro-client/en/latest/howtoguides/enable_cis/ |
| Ubuntu — CIS Benchmark | https://ubuntu.com/security/cis |
| Ubuntu Community — UFW | https://help.ubuntu.com/community/UFW |
| Ubuntu Community — Fail2ban | https://help.ubuntu.com/community/Fail2ban |

### Infrastructure & Virtualization
| Title | URL |
|-------|-----|
| Proxmox VE — Network Configuration | https://pve.proxmox.com/wiki/Network_Configuration |
| Proxmox VE — Storage | https://pve.proxmox.com/wiki/Storage |
| Proxmox Backup Server — Getting Started | https://pbs.proxmox.com/docs/getting-started.html |

### Automation & CI/CD
| Title | URL |
|-------|-----|
| Ansible — Getting Started | https://docs.ansible.com/ansible/latest/getting_started/index.html |
| Ansible — Build Your Inventory | https://docs.ansible.com/ansible/latest/network/getting_started/first_inventory.html |
| Ansible — Vault (secrets) | https://docs.ansible.com/ansible/latest/vault_guide/index.html |
| Ansible — Best Practices | https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html |
| Ansible — Roles | https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html |
| LearnAnsible.dev — Roles Best Practices | https://learnansible.dev/article/Ansible_Roles_Best_Practices_and_Examples.html |
| Gitea — Installation | https://docs.gitea.com/installation/install-from-binary |
| Woodpecker CI — Getting Started | https://woodpecker-ci.org/docs/intro |

### Identity
| Title | URL |
|-------|-----|
| FreeIPA — Quick Start Guide | https://www.freeipa.org/page/Quick_Start_Guide |
| HowtoForge — Add Ubuntu to FreeIPA | https://www.howtoforge.com/how-to-add-ubuntu-system-to-freeipa-server/ |
| Kifarunix — FreeIPA Client on Ubuntu 24.04 | https://kifarunix.com/install-and-configure-freeipa-client-on-ubuntu-24-04/ |

### Observability & Alerting
| Title | URL |
|-------|-----|
| Prometheus — Getting Started | https://prometheus.io/docs/prometheus/latest/getting_started/ |
| DigitalOcean — Install Prometheus on Ubuntu | https://www.digitalocean.com/community/tutorials/how-to-install-prometheus-on-ubuntu-16-04 |
| Grafana Alloy — Installation | https://grafana.com/docs/alloy/latest/set-up/install/ |
| Grafana Loki — Promtail deprecation + Alloy migration | https://grafana.com/docs/loki/latest/send-data/promtail/ |
| OTC — Migrating from Promtail to Grafana Alloy | https://arch.otc-service.com/docs/blueprints/by-use-case/observability/migrate-from-promtail-to-grafana-alloy |
| PagerDuty — Getting Started | https://support.pagerduty.com/docs/introduction |
| Opsgenie — Getting Started | https://docs.opsgenie.com/docs/getting-started |
| Google SRE Book — Practical Alerting | https://sre.google/sre-book/practical-alerting/ |

### Cloud Providers
| Title | URL |
|-------|-----|
| AWS — Getting Started with EC2 | https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html |
| AWS CLI — Getting Started | https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html |
| Azure — Create a Linux VM | https://learn.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-cli |
| Azure CLI — Getting Started | https://learn.microsoft.com/en-us/cli/azure/get-started-with-azure-cli |

### Python for Ops
| Title | URL |
|-------|-----|
| Python — Official Tutorial | https://docs.python.org/3/tutorial/ |
| boto3 — AWS SDK for Python | https://boto3.amazonaws.com/v1/documentation/api/latest/index.html |
| Prometheus HTTP API | https://prometheus.io/docs/prometheus/latest/querying/api/ |

### ITSM & Operations
| Title | URL |
|-------|-----|
| Google SRE Book — SLIs, SLOs, SLAs | https://sre.google/sre-book/service-level-objectives/ |
| Google SRE Book (full, free online) | https://sre.google/sre-book/table-of-contents/ |
| ITIL 4 Foundation — overview | https://www.axelos.com/certifications/itil-service-management/itil-4-foundation |
| Zammad — Getting Started | https://docs.zammad.org/en/latest/ |
| Zabbix — Getting Started | https://www.zabbix.com/documentation/current/en/manual/quickstart |

### Containers & Orchestration
| Title | URL |
|-------|-----|
| Docker Docs — Install Docker Engine on Ubuntu | https://docs.docker.com/engine/install/ubuntu/ |
| ufw-docker — Fix Docker UFW bypass | https://github.com/chaifeng/ufw-docker |
| Docker Compose — Getting Started | https://docs.docker.com/compose/gettingstarted/ |
| k3s — Installation | https://docs.k3s.io/installation |
| DigitalOcean — k3s Cluster on Ubuntu | https://www.digitalocean.com/community/tutorials/how-to-setup-k3s-kubernetes-cluster-on-ubuntu |
| OneUptime — Install k3s on Ubuntu | https://oneuptime.com/blog/post/2026-02-02-k3s-installation-ubuntu/view |
| cert-manager — Getting Started | https://cert-manager.io/docs/getting-started/ |

### Resilience
| Title | URL |
|-------|-----|
| Restic — Introduction / Quickstart | https://restic.readthedocs.io/en/stable/010_introduction.html |
| Restic — Full Documentation | https://restic.readthedocs.io/en/latest/ |
| Kifarunix — HA HAProxy + Keepalived on Ubuntu | https://kifarunix.com/configure-highly-available-haproxy-with-keepalived-on-ubuntu/ |
| MKBN-Tech — HAProxy + Keepalived | https://www.mkbntech.com/posts/haproxy-keepalived/ |

### Web
| Title | URL |
|-------|-----|
| nginx.org — Configuring HTTPS servers | https://nginx.org/en/docs/http/configuring_https_servers.html |

### General References (use throughout)
| Title | URL |
|-------|-----|
| ExplainShell — understand any command | https://explainshell.com/ |
| tldr pages — quick command examples | https://tldr.sh/ |
| Linux man-pages online | https://www.man7.org/linux/man-pages/ |
| OverTheWire: Bandit — learn by solving | https://overthewire.org/wargames/bandit/ |
| Linux Journey — free structured course | https://linuxjourney.com/ |

### Recommended YouTube Channels
| Channel | Strength |
|---------|----------|
| [Learn Linux TV](https://www.youtube.com/@LearnLinuxTV) | Ubuntu Server, Proxmox, Ansible, Zabbix |
| [TechWorld with Nana](https://www.youtube.com/@TechWorldwithNana) | Docker, Kubernetes, CI/CD, SRE concepts |
| [NetworkChuck](https://www.youtube.com/@NetworkChuck) | Networking, security, cloud, Python |
| [Computerphile](https://www.youtube.com/@Computerphile) | TLS, cryptography, protocols — deep dives |
| [freeCodeCamp](https://www.youtube.com/@freecodecamp) | Full courses: Python, AWS, Azure, Linux |

---

*Plan maintained at: `/docs/learning-plan.md` in your lab Git repo*
