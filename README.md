# CVE-2021-3493 – Ubuntu OverlayFS Local Privilege Escalation

**Ubuntu-specific vulnerability in OverlayFS allowing unprivileged users to gain root privileges.**

> "Ubuntu specific issue in the overlayfs file system in the Linux kernel where it did not properly validate the application of file system capabilities with respect to user namespaces. A local attacker could use this to gain elevated privileges, due to a patch carried in Ubuntu to allow unprivileged overlayfs mounts."  
> — Ubuntu Security

## Overview

This is a proof-of-concept exploit for **CVE-2021-3493**, a local privilege escalation vulnerability affecting several Ubuntu versions due to incorrect handling of file capabilities in user namespaces when using OverlayFS.

The exploit sets full capabilities (`cap_sys_admin+ep`, etc.) on a binary inside an OverlayFS mount inside a user namespace — a combination that Ubuntu's backport accidentally made dangerous.

**Fixed upstream** in Linux kernel **5.11**.

## Affected Distributions / Versions

- Ubuntu 20.10
- Ubuntu 20.04 LTS
- Ubuntu 19.04
- Ubuntu 18.04 LTS
- Ubuntu 16.04 LTS
- Ubuntu 14.04 ESM

**Not affected**:
- Official upstream kernels before Ubuntu's unprivileged mount patch
- Ubuntu versions with the security update applied (see Ubuntu's tracker)

→ Official Ubuntu security page: https://ubuntu.com/security/CVE-2021-3493

## Exploit

### Requirements
- Vulnerable Ubuntu version (unpatched)
- gcc (for compilation)

### Build & Run

```bash
# Compile as static binary (recommended)
gcc -static kernel_exploit.c -o exploit

# Make executable
chmod +x exploit

# Run the exploit
./exploit

