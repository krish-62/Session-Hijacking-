# BankShield — Banking Session Security Lab

A fictional banking application for an Application Security mini-project. The project compares weak session lifecycle behavior with defensive controls using three isolated virtual machines.

## Safety
Use only the VMs and fictional accounts in this project. Never use real banking credentials or customer data. Do not attach the vulnerable target VM to a bridged/public network, port-forward it, or expose it to the internet. No real payments are made.

## Lab topology
| VM | Role | Address |
|---|---|---|
| Kali Linux | Security tester | 192.168.56.10 |
| Ubuntu Desktop | Customer browser | 192.168.56.11 |
| Ubuntu Server | BankShield app | 192.168.56.12 |

Subnet: `192.168.56.0/24`, private isolated libvirt network.

## Project package
The complete starter project is supplied as `BankShield-project.zip` in this ChatGPT conversation. Extract it, then copy its contents into a local clone of this repository. It includes:
- Flask banking demo with fictional accounts, balances and simulated transfers
- Vulnerable and hardened session configurations
- HTML templates and CSS
- Isolated libvirt network definition
- Step-by-step Arch host, VM, guest network and server setup guides
- Experiment, remediation, severity and troubleshooting documentation

## Add the supplied project package to this repository

On your Arch host, after downloading and extracting `BankShield-project.zip`:

```bash
# Clone your GitHub repository
git clone https://github.com/krish-62/Session-Hijacking-.git
cd Session-Hijacking-

# Copy the extracted BankShield project contents into this repository.
# If the extracted folder is ~/Downloads/BankShield, run:
cp -a ~/Downloads/BankShield/. .

# Review before committing
git status
find . -maxdepth 3 -type f | sort

# Commit and push
git add .
git commit -m "Add BankShield banking session security lab"
git push origin main
```

If your extracted folder is elsewhere, replace `~/Downloads/BankShield` with its actual path. Do not overwrite files you have independently edited without reviewing the diff.

## Demo accounts
| Role | Username | Password |
|---|---|---|
| Customer | `alice` | `AliceDemo!234` |
| Operations (read-only) | `ops` | `OpsDemo!234` |

These are public training fixtures. Never reuse them elsewhere.

## Run on Ubuntu Server VM

After the project files are pushed and cloned to the server VM:

```bash
sudo apt update
sudo apt install -y python3 python3-venv python3-pip git
git clone https://github.com/krish-62/Session-Hijacking-.git
cd Session-Hijacking-
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Start vulnerable lab mode:

```bash
BANKSHIELD_MODE=vulnerable BANKSHIELD_HOST=192.168.56.12 python app.py
```

For hardened comparison, stop with `Ctrl+C` and run:

```bash
BANKSHIELD_MODE=secure BANKSHIELD_HOST=192.168.56.12 python app.py
```

Open `http://192.168.56.12:5000` from the victim VM.

## Documentation
- `docs/01-architecture.md`
- `docs/02-host-setup-arch.md`
- `docs/03-create-vms.md`
- `docs/04-guest-networking.md`
- `docs/05-install-server.md`
- `docs/06-experiments.md`
- `docs/07-troubleshooting.md`

## Severity
Do not assume High or Critical from the banking theme. Record demonstrated preconditions and impact, then calculate CVSS 4.0 using the official methodology. Cookie flags alone do not stop replay after a bearer token has already been copied; revocation, expiration, HTTPS, re-authentication and monitoring are complementary controls.
