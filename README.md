# BankShield — Banking Session Security Lab

A controlled Application Security coursework project using a fictional banking application and three isolated virtual machines.

## Safety and scope
Use only the lab VMs and fictional demo data. Do not connect this application to real banks, payment providers, real credentials, or real customer information. Keep any intentionally vulnerable configuration on a private isolated virtual network; never expose it to the internet or a bridged LAN.

## Project layout
- `app/` — application source and templates
- `docs/` — architecture, host setup, guest setup, experiments, troubleshooting
- `lab/` — isolated virtual network configuration
- `scripts/` — reproducible helper commands

## Lab topology
| VM | Role | Address |
|---|---|---|
| Kali Linux | Security tester | 192.168.56.10 |
| Ubuntu Desktop | Customer test browser | 192.168.56.11 |
| Ubuntu Server | Fictional banking application | 192.168.56.12 |

Private subnet: `192.168.56.0/24`. No public routing or bridged adapter for the vulnerable target.

## Technology
- Python 3 and Flask
- SQLite for fictional account and transaction records
- QEMU/KVM and libvirt on an Arch Linux host
- Kali Linux and Ubuntu 24.04 guests

## Documentation
1. [Project architecture](docs/01-architecture.md)
2. [Arch Linux host setup](docs/02-host-setup-arch.md)
3. [Create the three VMs](docs/03-create-vms.md)
4. [Guest network setup](docs/04-guest-networking.md)
5. [Application installation](docs/05-install-server.md)
6. [Controlled experiments and remediation](docs/06-experiments.md)
7. [Troubleshooting](docs/07-troubleshooting.md)

## Severity
Do not assume the finding is High merely because it is a banking-themed scenario. Record the demonstrated preconditions and impact, then calculate CVSS 4.0 using the official methodology.

## Project status
Documentation-first repository scaffold. Application implementation and validated lab instructions will be committed in subsequent milestones.
