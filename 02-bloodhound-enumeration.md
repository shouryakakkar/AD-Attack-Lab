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
[INSERT SCREENSHOT → Page 4, SharpHound running 
showing "Happy Graphing!" completion message]

Command:
.\SharpHound.exe -c All
Collected: 302 objects, 1747 relationships

### 2. Imported Data into BloodHound
[INSERT SCREENSHOT → Page 7, Database Info showing:
Users: 6, Groups: 32, Computers: 1, OUs: 2, 
Relationships: 1747]

### 3. Identified Domain Admins
[INSERT SCREENSHOT → Page 6, BloodHound graph 
showing "Find all Domain Admins" query result]

### 4. Analysed Administrator Account
[INSERT SCREENSHOT → Page 7, ADMINISTRATOR@LAB.LOCAL 
Node Info panel]

### 5. Kerberoastable Accounts
[INSERT SCREENSHOT → Page 6, BloodHound Analysis 
panel showing Kerberos Interaction section]

## Detection
- Monitor for LDAP queries collecting large amounts 
  of AD object data
- Alert on SharpHound signatures in EDR

## Remediation
- Implement tiered admin model
- Restrict unnecessary LDAP query permissions
- Use BloodHound defensively to find and fix 
  attack paths proactively