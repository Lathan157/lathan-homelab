# Lathan's Homelab

This repository documents the architecture, configuration, and services of my multi-node homelab.  
It is intended both as personal documentation and as a professional portfolio project, showcasing skills in networking, storage, virtualization, and automation.  

---

## Goals
- Learn and practice enterprise-level IT and DevOps concepts at home  
- Build a scalable and secure environment for real-world services  
- Experiment with Proxmox, OPNsense, OpenWRT, TrueNAS, Kubernetes, and Home Assistant  
- Maintain clear documentation for repeatability and professional reference  

---

## Architecture Overview
The homelab includes:  
- Proxmox cluster (4 nodes)  
- OPNsense and OpenWRT for routing, firewall, and PPPoE  
- TrueNAS SCALE for ZFS storage management  
- Docker and Kubernetes (in progress) for service orchestration  
- Home Assistant for smart home automation  
- Monitoring via Monit, SMART reports, and custom scripts  

Detailed documentation and diagrams are available in the [docs/](./docs) folder.  

---

## Hardware
- **Node 1** – Ryzen 5 3600, 80GB RAM, RTX 3060, multiple ZFS pools  
- **Node 2** – i9-9900K, OPNsense VM, OpenWRT VM, networking core  
- **Node 3** – Intel N97 Mini PC, Tailscale, Monit, Nextcloud  
- **Node 4** – Ryzen 5 3600, RTX 3060, Frigate NVR, Obico AI, secondary TrueNAS  
- **Remote Node** – Dell OptiPlex at offsite location for backups and monitoring  

More details: [docs/01-hardware.md](./docs/01-hardware.md)  

---

## Networking
- Bell 3 Gbps Fiber → OpenWRT → OPNsense  
- VLANs:  
  - VLAN 5 – Trusted  
  - VLAN 15 – Servers  
  - VLAN 25 – Media  
  - VLAN 45 – IoT  
  - VLAN 70 – CCTV  
- Switching: Ubiquiti US-24, USW-Flex-2.5G-8, YuanLey 8-port PoE  
- Wi-Fi: UniFi 6+ AP  

More details: [docs/02-network.md](./docs/02-network.md)  

---

## Storage
- TrueNAS SCALE VM with multiple ZFS pools:  
  - `Hornet` – 12TB bulk Plex storage  
  - `Knight` – 6× 6TB SAS RAIDZ2  
  - `Greenpath` – 2× 4TB RAID1  
  - `Deepnest` – 4× 2TB RAIDZ1  
- Offsite: Dell OptiPlex SMB share (ST4000DM004), WD My Cloud 4TB  
- Daily scrubs and SMART health monitoring  

More details: [docs/03-storage.md](./docs/03-storage.md)  

---

## Services
- Plex Media Server with GPU transcoding  
- Home Assistant for automation and IoT integration  
- Frigate NVR for Reolink cameras (with go2rtc integration)  
- Pi-hole / AdGuard for network-wide ad blocking  
- Tailscale for secure remote access and subnet routing  
- Monit for network and service monitoring with email alerts  
- Nextcloud for file sync and sharing  
- Self-hosted website (portfolio + dashboards)  

More details: [docs/04-virtualization.md](./docs/04-virtualization.md)  

---

## Automation and Monitoring
- Home Assistant automations for presence, lighting, cooling, and security  
- ESPHome with ESP32 sensors for temperature and humidity tracking  
- Monit service checks for Plex, TrueNAS, Home Assistant, OPNsense, and UniFi  
- Custom scripts for SMART reports and automated backups  

More details: [docs/05-automation.md](./docs/05-automation.md)  

---
## Rack and Cooling

The server rack is powered and cooled using a combination of smart fans and a Furman power conditioner.  

![Server Cabinet](docs/pictures/server-cabinet.jpg)

## Repository Structure
