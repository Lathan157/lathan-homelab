# Services and Applications

This document lists the main services running in the homelab, organized by Proxmox node and offsite systems.  
Each service includes its purpose and hosting location.

---

## Node 1 – Proxmox (Primary Storage and Media)
- **TrueNAS SCALE (VM)**
  - Manages all ZFS pools (Hornet, Knight, Greenpath, Deepnest)
  - Provides SMB/NFS storage to other nodes
- **Plex Media Server (VM, Ubuntu 24.04)**
  - GPU passthrough (RTX 3060) for hardware transcoding
  - Primary media server for Plex clients
- **Home Assistant (VM)**
  - Automation hub for Zigbee, Z-Wave, ESP32 devices
  - Integrates with UniFi network and cameras
- **UniFi Controller (Docker on Ubuntu 24.04 VM)**
  - Centralized management of UniFi devices (switches, AP)

---

## Node 2 – Proxmox (Network Core)
- **OpenWRT (VM)**
  - Handles PPPoE termination for Bell 3 Gbps fiber
- **OPNsense (VM)**
  - Firewall, VLANs, DHCP/DNS, inter-VLAN routing
- **Pi-hole (VM, Docker on Ubuntu 24.04)**
  - DNS filtering and ad blocking
- **Prowlarr, Sonarr, Radarr (Docker on Ubuntu 24.04 VM)**
  - Media automation services
  - Runs behind NordVPN for torrenting privacy

---

## Node 3 – Proxmox Mini PC (Remote Access and Monitoring)
- **Nextcloud (VM)**
  - File sync and sharing platform
  - Storage backend mounted from Node 1’s USB SSD (NQ-FS-01, 238 GB)
- **Tailscale VPN (VM)**
  - Exit node and subnet router for secure remote access
- **Monit Watchdog (VM)**
  - Monitors uptime and critical services, sends email alerts
- **Python Web Flask Backend (LXC)**
  - Lightweight backend for custom web applications
- **Tautulli (VM, Ubuntu 24.04)**
  - Plex usage monitoring and reporting

---

## Node 4 – Proxmox (Video Processing and Secondary Storage)
- **Frigate NVR (VM, Ubuntu 24.04)**
  - AI-powered CCTV NVR
  - GPU passthrough to RTX 3060
- **Obico 3D Printer Monitor (VM)**
  - AI monitoring for 3D printing jobs
- **TrueNAS SCALE (VM)**
  - Manages Node 4’s local SATA drives
  - Used for secondary storage and backups
- **Lathan Website (VM, Ubuntu 24.04)**
  - Personal/portfolio site hosting
  - Backend powered by Nginx + Docker containers

---

## External / Remote Systems
- **Raspberry Pi 4 (4 GB RAM)**
  - Z-Wave Plus Hub for smart home automation
- **Gaming Computer (Ryzen 7 9800X3D, RTX 3080)**
  - Primary gaming and workstation PC
  - Also used for development and video editing
- **Offsite Node – Dell Wyse 3040**
  - Tailscale VPN relay
  - Lightweight monitoring
- **Offsite Node – Dell OptiPlex 390**
  - Offsite backup (SMB share, 4 TB Seagate HDD)
  - Monit alerts for connectivity
- **WD My Cloud NAS (4 TB)**
  - Legacy external NAS for basic file storage
- **Offsite PC (i7-10700K, RX 6600)**
  - 4 TB HDD
  - Used for backup and testing workloads

---

## Website Hosting
- **Lathan Website (Node 4, Ubuntu VM)**
  - Self-hosted portfolio and homelab documentation site
  - Uses Nginx web server
  - Accessible locally via homelab network and remotely through Tailscale
