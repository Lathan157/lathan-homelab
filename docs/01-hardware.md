# Hardware Overview

This document details all nodes in the homelab, including their specifications and roles.  
The environment is designed around Proxmox for virtualization, with specialized nodes for storage, routing, monitoring, and automation.  
A dedicated gaming workstation is also included.

---

## Node 1 – Proxmox (Primary Storage and Media)

- **CPU:** AMD Ryzen 5 3600 (6 cores, 12 threads)  
- **RAM:** 80 GB DDR4-3200  
- **GPU:** NVIDIA RTX 3060 12GB  
- **Motherboard:** MSI B550 Gaming Gen3  
- **Networking:** 2.5 GbE PCIe NIC (TP-Link TX201)  

### Physical Drives
- SPCC Solid State Drive – 115 GB SATA SSD  
- Samsung MZVL2512HCJQ-00BL7 – 512 GB NVMe SSD  
- WDC WD40EMRX-82U – 4 TB SATA HDD  
- Seagate ST4000VN006-3CW1 – 4 TB SATA HDD  
- HGST Ultrastar HUH721212AL4200 – 12 TB SAS HDD  
- 6 × Seagate ST6000NM0105 – 6 TB SAS HDDs  
- 2 × 4 TB SATA HDDs (QEMU passthrough)  
- 4 × 2 TB SATA HDDs (mixed models)  
- NQ-FS-01 – 238 GB USB SSD  

### Case / PSU
- Cooler Master NR600 (ATX Mid Tower)  
- Gigabyte GP-G750H 750W 80+ Gold  

### Role
- Primary storage node  
- Provides passthrough of all data drives to TrueNAS SCALE VM  
- Hosts Plex VM with GPU passthrough for transcoding  
- Runs additional server VMs  
 

---

## Node 2 – Proxmox (Network Core)
- **CPU:** Intel Core i9-9900K (8 cores, 16 threads)  
- **RAM:** 16 GB DDR4  
- **Networking:**  
  - 2× Intel X540-T2 dual 10 GbE NICs  
  - Intel I350-T2 dual 1 GbE NIC  
- **Role:**  
  - OPNsense VM (firewall, VLANs, routing)  
  - OpenWRT VM (PPPoE termination for Bell Fiber 3 Gbps)  
  - Provides uplinks to 10 GbE and 2.5 GbE switches  
  - Primary gateway for all VLANs  

---

## Node 3 – Proxmox Mini PC (Remote Access and Monitoring)
- **Model:** MINIX Z97 Mini PC  
- **CPU:** Intel Alder Lake N97 (quad-core, up to 3.6 GHz)  
- **RAM:** 12 GB LPDDR5X  
- **Storage:** 512GB NVMe SSD  
- **Networking:** Dual 1 GbE LAN  
- **Role:**  
  - Tailscale exit node and subnet router  
  - Monit monitoring with email alerts  
  - Lightweight Nextcloud instance  
  - Redundant access if Node 2 goes down  

---

## Node 4 – Proxmox (Video Processing and NVR)
- **CPU:** AMD Ryzen 5 3600  
- **RAM:** 16 GB DDR4-3200  
- **GPU:** NVIDIA RTX 3060 12GB  
- **Motherboard:** Asus Prime B450M-A II  
- **Storage:**  
  - Crucial BX500 240GB SSD (boot)  
  - 3× 2TB Seagate Barracuda HDDs (ST2000DM001, ST2000DM008 ×2)  
  - 1× 1.5TB Seagate Barracuda Green HDD (ST1500DL001)  
  - 1× 2TB WD Green HDD (WD20EADS)  
- **Case/PSU:** Open bench chassis, MSI MAG A550BN 550W PSU  
- **Role:**  
  - Frigate NVR for Reolink cameras (GPU accelerated)  
  - Obico AI for 3D printer monitoring  
  - Backup services and experimentation
 

---

## Remote Node – Dell OptiPlex (Offsite Backup)
- **Model:** Dell OptiPlex 390 SFF  
- **CPU:** Intel Core i5-2400 (quad-core)  
- **RAM:** 8 GB DDR3  
- **Storage:** 1 TB HDD  
- **Role:**  
  - Offsite backup server (located at parents’ house)  
  - Secondary monitoring via Monit  
 
---

## Gaming Workstation
- **CPU:** AMD Ryzen 7 9800X3D (8 cores, 16 threads, 4.7 GHz)  
- **Motherboard:** Gigabyte X870 AORUS ELITE WIFI7 ICE (ATX, AM5)  
- **RAM:** Corsair Vengeance RGB 32 GB (2×16 GB) DDR5-6000 CL36  
- **GPU:** Gigabyte AORUS GeForce RTX 3080 XTREME WATERFORCE WB 10GB (custom water-cooled)  
- **Storage:**  
  - Lexar NM610 1TB NVMe (PCIe 3.0)  
  - Samsung 980 1TB NVMe (PCIe 3.0)  
  - Seagate BarraCuda 1TB HDD (7200 RPM)  
- **Case:** Lian Li O11D XL-W (ATX Full Tower)  
- **PSU:** Corsair RM1000x (2021) 1000W 80+ Gold, fully modular  
- **Role:** Primary gaming PC, also used for development, video editing, and testing workloads outside the homelab cluster  
