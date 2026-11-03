# MediCare EOOD

## Company Profile

* **Company Name:** MediCare EOOD

* **Sector:** Healthcare / Private Clinics

* **Headquarters:** Sofia (HQ)

* **Regional Medical Centers:** Burgas, Ruse, Stara Zagora

* **Compliance Framework:** GDPR (Regulation EU 2016/679) & ISO/IEC 27001 / Annex A Controls

### Description

MediCare EOOD operates a network of private medical centers across four cities in Bulgaria. The core system manages sensitive patient medical records subject to strict GDPR requirements. Access to the centralized patient database is restricted solely to authorized medical personnel (doctors), whereas administrative staff only have access to aggregated reporting data.

## Network Infrastructure & VM Topology

| Office / Location | VM / Device Role | IP Address / Subnet | Port / Protocol | Description | 
| ----- | ----- | ----- | ----- | ----- | 
| **Sofia HQ** | Firewall & DB Server | `10.10.0.1` / `10.10.0.10` | `5432/TCP` (PostgreSQL) | Central Database with TLS encryption & Main Gateway | 
| **Sofia HQ** | Reporting Module | `10.10.0.10` (DMZ/LAN) | `8443/TCP` (HTTPS) | Aggregated Reporting Web Portal behind Proxy | 
| **Burgas** | Doctor Terminal | `10.11.0.20` | `5432/TCP` | Full DB Access for Medical Staff | 
| **Ruse** | Doctor Terminal | `10.12.0.20` | `5432/TCP` | Full DB Access for Medical Staff | 
| **Stara Zagora** | Administrative Workstation | `10.13.0.30` | `8443/TCP` | Strictly restricted to Reporting Module | 

## Network Filtering & Firewall Requirements (Lab 9)

1. **Medical Terminals Access:** Terminals in Burgas (`10.11.0.20`) and Ruse (`10.12.0.20`) are granted full access to the central PostgreSQL Database at Sofia HQ on port `5432/TCP`.

2. **Administrative Access:** The workstation in Stara Zagora (`10.13.0.30`) can only access the Reporting Module on port `8443/TCP`.

3. **Database Isolation:** Stara Zagora (`10.13.0.30`) is strictly denied direct access to port `5432/TCP` (PostgreSQL DB).

4. **ICMP Rule:** ICMP packets (ping/diagnostics) are allowed only within the internal network range `10.10.0.0/8`.

5. **Logging:** All dropped packets must be logged with the log prefix `[MEDICARE-DROP]`.