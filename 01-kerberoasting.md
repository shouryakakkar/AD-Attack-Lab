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

\[INSERT SCREENSHOT → Page 3, Rubeus output showing
svcbackup as kerberoastable user with full hash]

Target account: svcbackup
SPN: HTTP/backup.lab.local

### 2\. Extracted Hash

Command run:
.\\Rubeus.exe kerberoast /outfile:hashes.txt
Hash saved to: C:\\Tools\\hashes.txt

\[INSERT SCREENSHOT → Page 4, showing hashes.txt
file in C:\\Tools folder]

## Detection

* Monitor Event ID 4769 — Kerberos Service Ticket
requested with RC4 encryption
* Alert on multiple TGS requests from single user
in short timeframe

## Remediation

* Use strong passwords (25+ chars) on service accounts
* Use Group Managed Service Accounts (gMSA)
* Enable AES encryption, disable RC4 for Kerberos

