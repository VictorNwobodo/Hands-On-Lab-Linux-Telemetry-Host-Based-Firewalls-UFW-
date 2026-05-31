# Hands-On-Lab-Linux-Telemetry-Host-Based-Firewalls-UFW-
**Date:** May 31, 2026  
**Role:** Junior SOC Engineer (Training Environment)

## Objective
To analyze Linux authentication logs in real-time, isolate a simulated brute-force SSH attack, and implement immediate host-based firewall mitigation to secure the endpoint.

<img width="2000" height="1125" alt="1 (3)" src="https://github.com/user-attachments/assets/2eb851c9-6b53-4b89-96e5-9ac41a186988" />

## Log Telemetry Exploration
Enterprise systems track security events independently from general application data to optimize search efficiency and prevent log tampering. On Ubuntu systems, authentication details are stored in:
* `/var/log/auth.log`

### Live Parsing Architecture
To actively monitor the host without crashing system resources, a dynamic pipeline was constructed using a Linux pipe (`|`) to feed a live text stream directly into a regex filter:

```bash
tail -f /var/log/auth.log | grep "Failed"
