# Storage Overview

This document describes the storage configuration of the homelab.  
Most storage is managed by a TrueNAS SCALE VM running on Proxmox Node 1.  
Additional offsite and external storage devices are also included.

---

## Local Storage (Node 1 → TrueNAS SCALE VM passthrough)

- HGST Ultrastar HUH721212AL4200 – 12 TB SAS HDD  
- 6 × Seagate ST6000NM0105 – 6 TB SAS HDDs  
- 2 × 4 TB SATA HDDs (QEMU passthrough)  
- 4 × 2 TB SATA HDDs (mixed models)  
- WDC WD40EMRX-82U – 4 TB SATA HDD  
- Seagate ST4000VN006-3CW1 – 4 TB SATA HDD  
- NQ-FS-01 – 238 GB USB SSD (dedicated to Nextcloud)  

---

## ZFS Pools (Managed by TrueNAS)

### Hornet
- 12 TB HGST Ultrastar  
- Role: Bulk Plex storage  

### Knight
- 6 × 6 TB Seagate SAS (RAIDZ2)  
- Role: Reliable media and document storage  

### Greenpath
- 2 × 4 TB SATA HDDs (mirror)  
- Role: Smaller critical data set  

### Deepnest
- 4 × 2 TB SATA HDDs (RAIDZ1)  
- Role: Legacy pool, less critical data  

### External
- 238 GB USB SSD (NQ-FS-01)  
- Role: Portable storage, dedicated backend for Nextcloud  

---

## Additional Attached Storage (Node 3)

- WDC WD10JMVW-11AJGS1 – 1 TB USB HDD  
- WDC WD20NMVW-11EDZS7 – 2 TB USB HDD  
- WD My Passport 0740 – 500 GB USB HDD  
- Role: Lightweight backup or overflow storage (not part of ZFS pools)  

---

## Offsite / External Storage

- Offsite PC SMB Share – Seagate ST400DM004-2CV104 – 4 TB SATA HDD  
- WD My Cloud NAS – Western Digital WDBCTL0040HWT-NESN – 4 TB external NAS  

---

## Maintenance

- Scheduled scrubs for all ZFS pools  
- SMART monitoring with email alerts  
- Manual checks on external/offsite devices  
- Offsite sync tasks planned for SMB share and WD My Cloud  
