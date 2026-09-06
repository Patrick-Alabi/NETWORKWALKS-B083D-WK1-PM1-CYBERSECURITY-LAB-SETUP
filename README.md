# NETWORKWALKS-B083D-WK1-PM1-CYBERSECURITY-LAB-SETUP

# Cybersecurity Lab Setup — Week 1 (VirtualBox + Kali Linux)

## Overview
This project documents the setup of a personal cybersecurity testing lab as part of Week 1 of the Networkwalks Cybersecurity Internship Program. The lab serves as the foundation for future offensive security, SOC analysis, and OSINT practice modules.

## Objective
Build a virtualized lab environment with an isolated attacker network, configured for full internet access and file interoperability between host and guest machines.

## Environment & Tools
- **Hypervisor:** Oracle VirtualBox (latest version)
- **Attack Machine:** Kali Linux
- **Host OS:** Windows
- **Network Mode:** NAT Network (custom, isolated subnet)

## Network Configuration
| Setting | Value |
|---|---|
| Subnet | 10.0.0.0/24 |
| Network Type | NATNetwork (custom) |
| Kali Linux IP | 10.0.0.2/24 |
| Gateway | 10.0.0.1 |
| DNS | 8.8.8.8 (fallback: 10.0.0.1) |
| Internet Access | Enabled |

## Setup Steps
1. Installed 7-Zip for archive extraction.
2. Installed the latest version of Oracle VirtualBox.
3. Created a custom NAT Network (`NatNetwork`) with subnet `10.0.0.0/24` and DHCP enabled.
4. Downloaded and imported the Kali Linux VM appliance into VirtualBox.
5. Attached the Kali Linux VM's network adapter to the NAT Network.
6. Configured Kali Linux with a static IP (`10.0.0.2/24`), gateway `10.0.0.1`, and DNS `8.8.8.8`.
7. Enabled clipboard sharing and drag-and-drop (Bidirectional) in VM settings.
8. Enabled a shared folder mapping the host's `/Downloads` directory to the VM.
9. Verified internet connectivity from Kali Linux.
10. Took a snapshot of the VM to preserve the clean baseline state.

## Troubleshooting Notes
Encountered an internet connectivity issue on Kali Linux, common with VirtualBox v7 / Kali 2026.1+ due to IPv4 duplicate address detection (DAD) delays. Resolved with:
```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

## Verification
- [x] Kali Linux boots successfully within the NAT Network
- [x] Static IP `10.0.0.2/24` confirmed via `ip a`
- [x] Internet access confirmed via `ping` and package manager update
- [x] Clipboard and drag-and-drop functioning between host and guest
- [x] Shared folder accessible from within Kali Linux
- [x] Snapshot taken

## Next Steps (Phase 2)
- Add additional VMs (Windows 10/11, Server 2016, Android) to the same NAT Network
- Perform inter-VM ping tests
- Snapshot each machine post-configuration
- Begin practical offensive/defensive exercises within the lab

## About
Part of my hands-on cybersecurity learning journey — SOC analysis, penetration testing, and OSINT — documented for portfolio purposes.

**Connect with me:**
- LinkedIn / Medium: Dasilvercass
- GitHub: [Patrick-Alabi](https://github.com/Patrick-Alabi)
