# Automation

This document outlines the automation layer of the homelab.  
Automation is primarily handled through Home Assistant, ESPHome, and Monit scripts, with dedicated displays for quick access.

---

## Home Assistant Automations

- **Side Door Lock Automation**  
  If the side door smart lock is left unlocked for 15 minutes, it automatically relocks.  
  *Purpose: Improves security by preventing the door from being left unlocked.*

- **Sunset/Sunrise Kitchen Counter Lights**  
  At sunset, the kitchen counter switches and lights are turned on. At sunrise, they are turned off.  
  *Purpose: Provides automatic kitchen lighting based on daylight cycles.*

- **Kitchen Display**  
  The kitchen dashboard display powers off at midnight and powers on again at 8:00 AM daily.  
  *Purpose: Ensures the Home Assistant dashboard is visible during the day but not wasting power overnight.*

- **Server Cabinet Cooling Control**  
  A DHT22 sensor monitors cabinet temperature. If it rises above 30 °C, the exhaust fan turns on. When it drops back to safe levels, the fan turns off.  
  *Purpose: Prevents overheating of Proxmox nodes and storage in the server cabinet.*

- **Camera Socket Presence Control**  
  If both household members are away, the living room camera socket is turned on and both phones receive a notification. If either person is home, the socket is turned off and a notification is sent confirming someone arrived.  
  *Purpose: Automates CCTV power state and provides presence-based security alerts.*

---

## ESPHome Devices

- **ESP32 DHT22 Sensors**  
  Located in the Kitchen, Server Cabinet, Computer Room, Bedroom, and Living Room.  
  They monitor temperature and humidity, feeding data into Home Assistant.  

- **Custom Displays**  
  ESP32-based screens show real-time room metrics.  
  Future plan: add touch input for simple local controls.

---

## Monitoring Displays

- **Kitchen Monitor**  
  Displays the Home Assistant dashboard with live sensor data, automations, and device states.  

- **Bedroom Tablet**  
  Dedicated to showing a self-hosted **network monitoring website**, giving a quick overview of Proxmox nodes, TrueNAS, and key services.  

---

## Monit Scripts

- **Service Monitoring**  
  Plex, TrueNAS, Home Assistant, OPNsense, and UniFi Controller are actively monitored.  
  If services fail, email alerts are sent.  

- **Router Health**  
  Regular ping checks to OPNsense VM and ISP router.  
  Alerts trigger if OPNsense goes offline.  

- **Disk SMART Reports**  
  Daily reports summarize drive health, with warnings for aging disks or reallocated sectors.  
