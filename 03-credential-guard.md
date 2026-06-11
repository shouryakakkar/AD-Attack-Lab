# Attack 3 — Credential Dumping (Blocked by Credential Guard)

**MITRE ATT&CK TTP:** T1003.001 — OS Credential 
Dumping: LSASS Memory
**Tool:** Mimikatz
**Result:** ⚠️ Blocked — Defensive control documented

## What is Pass-the-Hash?
Attackers dump NTLM hashes from LSASS memory and 
use them to authenticate as other users without 
knowing their plaintext password.

## Attempt

### 1. Escalated Privileges
[INSERT SCREENSHOT → Page 3, Mimikatz showing 
"privilege::debug → Privilege '20' OK"]

### 2. LSASS Access Blocked
ERROR kuhl_m_sekurlsa_acquireLSA ;
Handle on memory (0x00000005)
Windows 11 Credential Guard prevented direct 
LSASS memory access even with SeDebugPrivilege.

### 3. LSASS Dump via Task Manager Also Blocked
"Access is denied" — Credential Guard protecting 
LSASS at virtualisation layer.

## Why This Matters
Windows 11 enables Virtualization Based Security 
(VBS) and Credential Guard by default, isolating 
LSASS in a secure enclave inaccessible even to 
SYSTEM-level processes. This is a significant 
defensive improvement over Windows 10.

## Detection
This attack was **detected and prevented** by:
- Windows Defender Credential Guard (VBS)
- LSA Protection (RunAsPPL)

## Remediation
- Keep Credential Guard enabled (default on Win 11)
- Enable memory integrity in Windows Security
- Monitor Event ID 3033/3063 for Credential Guard 
  activity