# ADSOC Lab Architecture

## Overview

The ADSOC lab simulates a small Active Directory enterprise environment designed to generate and investigate Windows Security telemetry relevant to SOC operations, authentication monitoring, Active Directory reconnaissance, and privileged access detection.

The environment consists of:

- A Windows Server 2022 Domain Controller (`DC01`)
- A domain-joined Windows 11 workstation (`WS01`)
- A Kali Linux system (`KALI`) used to simulate reconnaissance activity

---

## Network Architecture

| System | Role | Operating System | Purpose |
|---|---|---|---|
| `DC01` | Domain Controller | Windows Server 2022 | Active Directory, authentication, security telemetry |
| `WS01` | Workstation | Windows 11 Pro | Domain-joined client used for authentication scenarios |
| `KALI` | Adversary Simulation | Kali Linux | Simulated reconnaissance and authentication activity |

All systems operate within the same virtual lab network to simulate enterprise authentication and Active Directory interactions.

---

## Domain Environment

| Configuration | Value |
|---|---|
| Domain Name | `adsoc.local` |
| Domain Controller | `DC01` |
| Workstation | `WS01` |
| Adversary Host | `KALI` |

---

## Authentication & Security Monitoring

The lab generates Windows Security telemetry used for detection engineering and SOC-style investigations.

Observed Windows Security Event IDs include:

| Event ID | Purpose |
|---|---|
| `4624` | Successful logon |
| `4625` | Failed logon |
| `4728` | Security group membership modification |
| `4740` | Account lockout |

---

## Implemented Scenarios

| Scenario | Focus |
|---|---|
| Security Group Membership Monitoring | Identity and access monitoring |
| Password Spraying Detection | Authentication abuse detection |
| Account Lockout Investigation | Authentication investigation |
| Active Directory Reconnaissance | Discovery and reconnaissance monitoring |
| Privileged Group Monitoring | Privilege escalation monitoring |

---

## Detection Engineering

The project includes lab-oriented KQL-style detections based on observed telemetry:

- Password spraying detection
- Account lockout detection
- Privileged group membership monitoring
- Active Directory reconnaissance detection

---

## Architecture Summary

The ADSOC lab demonstrates:

- Active Directory administration fundamentals
- Windows Security log investigation
- Authentication monitoring
- Privileged access monitoring
- Active Directory reconnaissance visibility
- Detection engineering concepts using KQL-style logic
- SOC-style investigation workflows