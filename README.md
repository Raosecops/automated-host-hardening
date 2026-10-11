# Automated Host Hardening & Systemd Attack Surface Mitigation

## Project Overview
Engineered an automated host hardening and attack surface reduction framework on an Ubuntu production node (`prd-eu-sec-node01`). Conducted socket-level discovery via `ss` to baseline open listeners, disabling unneeded services like CUPS and Avahi to minimize exposure. Implemented enterprise sysctl controls to mitigate SYN floods, IP spoofing, and source routing. Enforced strict UFW default-deny ingress filtering with explicit SSH access, and validated security posture through continuous auditing benchmarks.

## Key Features & Implementation
- **Attack Surface Discovery:** Audited active network listeners and open ports using `ss -tulnp` and `nmap`.
- **Kernel Hardening (`sysctl`):** Configured persistent security rules under `/etc/sysctl.d/` to protect against IP spoofing, redirects, and SYN flood denial-of-service attacks.
- **Service Minimization:** Disabled non-essential background daemons (`cups.service`, `avahi-daemon.service`) to reduce the system's attack surface.
- **Firewall Enforcement (`UFW`):** Implemented strict default-deny ingress packet filtering while maintaining explicit SSH remote administration access.

## Skills & Technologies
- **Linux Hardening & Kernel Tuning:** `sysctl`, TCP SYN cookies, ICMP redirect mitigation.
- **Network Auditing:** `ss`, `nmap`, socket statistics analysis.
- **Service Management:** `systemd`, unit file management.
- **Firewall Control:** `UFW`, ingress/egress policy enforcement.
- **Virtualization:** Canonical `Multipass`.

## Quick Deployment Guide

1. **Apply Kernel Hardening:**
   ```bash
   sudo cp configs/99-security-hardening.conf /etc/sysctl.d/
   sudo sysctl --system

2 Disable Unneeded Daemons:

3 Config firewall:

sudo apt install -y ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw --force enable


