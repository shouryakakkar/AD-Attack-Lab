# Lab Setup

## Domain Controller Setup
[INSERT SCREENSHOT → Page 1, Server Manager showing 
AD DS + DNS roles installed]

- Windows Server 2022 installed on VMware
- Promoted to Domain Controller for lab.local
- Created Organizational Unit: Corp
- Created users: jsmith, sjones, svcbackup

## SPN Registration
[INSERT SCREENSHOT → Page 1, PowerShell showing 
setspn command for svcbackup]

Registered HTTP SPN on svcbackup to make it 
Kerberoastable:
setspn -a HTTP/backup.lab.local svcbackup

## Client Setup
[INSERT SCREENSHOT → Page 2, showing "Welcome to 
lab.local domain" popup]

[INSERT SCREENSHOT → Page 2, showing Windows 11 
Enterprise edition confirmation]

- Windows 11 Enterprise joined to lab.local domain
- DNS pointed to Domain Controller IP (192.168.30.141)
- Logged in as domain user jsmith