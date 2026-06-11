# Lab Setup

## Domain Controller Setup
<img width="1545" height="791" alt="image" src="https://github.com/user-attachments/assets/3b68e6a8-7a5c-4c25-b09b-f304cfc53558" />


- Windows Server 2022 installed on VMware
- Promoted to Domain Controller for lab.local
- Created Organizational Unit: Corp
- Created users: jsmith, sjones, svcbackup

## SPN Registration
<img width="1533" height="782" alt="image" src="https://github.com/user-attachments/assets/574764dc-66c4-4325-a78a-7bfdf0b3058c" />


Registered HTTP SPN on svcbackup to make it 
Kerberoastable:
setspn -a HTTP/backup.lab.local svcbackup

## Client Setup
<img width="1529" height="787" alt="image" src="https://github.com/user-attachments/assets/2a1c11e8-fd07-4468-81ce-30c97064f955" />


<img width="1535" height="775" alt="image" src="https://github.com/user-attachments/assets/5f506607-80fe-4ca5-9bbf-5b9b562ae102" />


- Windows 11 Enterprise joined to lab.local domain
- DNS pointed to Domain Controller IP (192.168.30.141)
- Logged in as domain user jsmith
