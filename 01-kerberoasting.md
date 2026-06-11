# Attack 1 — Kerberoasting

**MITRE ATT\&CK TTP:** T1558.003 — Steal or Forge
Kerberos Tickets
**Severity:** High
**Tool:** Rubeus v2.2.0

## What is Kerberoasting?

Any domain user can request a Kerberos service ticket
for any account with an SPN registered. The ticket is
encrypted with the service account's NTLM hash —
meaning it can be taken offline and cracked without
any interaction with the target account.

## Steps

### 1\. Identified Kerberoastable Account

<img width="1633" height="774" alt="image" src="https://github.com/user-attachments/assets/8097e226-44f2-4570-9cd0-b1282362f53e" />


Target account: svcbackup
SPN: HTTP/backup.lab.local

### 2\. Extracted Hash

Command run:
.\\Rubeus.exe kerberoast /outfile:hashes.txt
Hash saved to: C:\\Tools\\hashes.txt
<img width="1635" height="831" alt="image" src="https://github.com/user-attachments/assets/3db69cbf-bde7-405a-a35a-5bdc92584961" />


## Detection

* Monitor Event ID 4769 — Kerberos Service Ticket
requested with RC4 encryption
* Alert on multiple TGS requests from single user
in short timeframe

## Remediation

* Use strong passwords (25+ chars) on service accounts
* Use Group Managed Service Accounts (gMSA)
* Enable AES encryption, disable RC4 for Kerberos

