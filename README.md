# CVE-2021-3493
Ubuntu OverlayFS Local Privileges Escalation 

Description
"Ubuntu specific issue in the overlayfs file system in the Linux kernel where it did not properly validate the application of file system capabilities with respect to user namespaces. A local attacker could use this to gain elevated privileges, due to a patch carried in Ubuntu to allow unprivileged overlayfs mounts." - Ubuntu Security

Fixed in Linux 5.11

Affected Versions
Ubuntu 20.10
Ubuntu 20.04 LTS
Ubuntu 19.04 LTS
Ubuntu 18.04 LTS
Ubuntu 16.04 LTS
Ubuntu 14.04 ESM
checklist: https://ubuntu.com/security/CVE-2021-3493

Usage
gcc -static kernel_exploit.c -o kernel_exploit
chmod +x kernel_exploit
./kernel_exploit

References
https://github.com/briskets/CVE-2021-3493
