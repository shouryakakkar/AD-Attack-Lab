# Attack 2 — Active Directory Enumeration (BloodHound)

**MITRE ATT&CK TTP:** T1087.002 — Account Discovery: 
Domain Account
**Tool:** SharpHound v2.13 + BloodHound v4.3

## What is BloodHound?
BloodHound maps Active Directory relationships and 
identifies attack paths to Domain Admin using graph 
theory. SharpHound collects the raw data; BloodHound 
visualises it.

## Steps

### 1. Ran SharpHound Collection
<img width="1636" height="814" alt="image" src="https://github.com/user-attachments/assets/ac7e6ccd-002f-43ec-8481-269104872245" />
<img width="1635" height="538" alt="image" src="https://github.com/user-attachments/assets/4f7ff808-3c5b-4b92-83bf-25e3744fac97" />
<img width="1636" height="767" alt="image" src="https://github.com/user-attachments/assets/03a7f2c0-8557-43ae-b62c-5281062ae6a9" />


Command:
.\SharpHound.exe -c All
Collected: 302 objects, 1747 relationships

### 2. Imported Data into BloodHound
<img width="1640" height="821" alt="image" src="https://github.com/user-attachments/assets/e03f52b7-492b-46f7-b431-3ec006d9dd3b" />


### 3. Identified Domain Admins
<img width="1637" height="830" alt="image" src="https://github.com/user-attachments/assets/8ae297ea-9035-4e14-b935-31d9711997f8" />


### 4. Analysed Administrator Account
<img width="1632" height="830" alt="image" src="https://github.com/user-attachments/assets/8429e52e-1939-46bd-9266-b690187d92da" />


### 5. Kerberoastable Accounts
<img width="1637" height="834" alt="image" src="https://github.com/user-attachments/assets/c3e502da-526a-4c7b-8d00-125b6bf5b98e" />


## Detection
- Monitor for LDAP queries collecting large amounts 
  of AD object data
- Alert on SharpHound signatures in EDR

## Remediation
- Implement tiered admin model
- Restrict unnecessary LDAP query permissions
- Use BloodHound defensively to find and fix 
  attack paths proactively
