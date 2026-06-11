# AD Attack Lab — Active Directory Penetration Testing

## Overview
A home lab simulating real-world Active Directory attacks 
mapped to MITRE ATT&CK TTPs. Built to practice offensive 
security techniques in an isolated environment.

## Lab Architecture
<img width="1532" height="819" alt="image" src="https://github.com/user-attachments/assets/695d8aaa-e5eb-4322-8113-3bc1315074e8" />


- **Domain Controller:** Windows Server 2022 (lab.local)
- **Client Machine:** Windows 11 Enterprise
- **Domain:** lab.local
- **Tools Used:** Rubeus, Mimikatz, BloodHound, SharpHound

## Attacks Performed
| Attack | MITRE TTP | Status |
|--------|-----------|--------|
| Kerberoasting | T1558.003 | ✅ Successful |
| AD Enumeration (BloodHound) | T1087.002 | ✅ Successful |
| Credential Dumping (Mimikatz) | T1003.001 | ⚠️ Blocked by Credential Guard |

## Key Findings
- Kerberoastable service account (svcbackup) identified 
  and hash extracted
- 1747 AD relationships mapped via BloodHound
- Windows 11 Credential Guard successfully blocked 
  LSASS memory access — defensive control documented

## Setup Guide
See [Lab Setup](setup/lab-setup.md)
