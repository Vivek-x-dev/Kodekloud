# Day 5 – SELinux Setup on App Server 3

## Objective
Install the required SELinux packages and **permanently disable** SELinux (it will be re‑enabled later after configuration changes).  
No reboot is required; the change will take effect after tonight’s scheduled maintenance reboot.

**Server:** `stapp03`  
**Credentials:** `banner / BigGr33n`

---

##  – Identify the Package Manager

Before installing, it’s good practice to know which package manager the system uses.  
On RHEL/CentOS systems (the Nautilus environment), both `yum` and `dnf` are available.

Check with:
```bash

which yum   # RHEL/CentOS 7 and older
which dnf   # RHEL/CentOS 8+ (also Fedora)
which apt   # Debian/Ubuntu
which zypper # SUSE
```
##  other way to check 
```
cat /etc/os-release
```

### SELinux: Package Installation and Permanent Disablement Guide

This guide covers the installation of core SELinux packages and the process of permanently
 disabling SELinux on RHEL derivatives (such as CentOS, AlmaLinux, or Rocky Linux).

---
text
##  – Install SELinux Packages

The standard SELinux packages required for management are:

- **`policycoreutils`** – Core utilities (e.g., `semanage`, `setenforce`).
- **`selinux-policy`** – Base SELinux policy.
- **`selinux-policy-targeted`** – Default targeted policy.

Run the following command (using `yum`; replace with `dnf` if preferred):
{ get this from internet }

```bash
sudo yum install -y policycoreutils selinux-policy selinux-policy-targeted

```
## - Permanently Disable SELinux

SELinux behavior at boot is controlled by `/etc/selinux/config`. The `SELINUX=` directive defines 
the operating mode. Setting this value to `disabled` prevents SELinux from loading during system startup.

###  Configuration

Open the configuration file using a text editor:

```bash
sudo vi /etc/selinux/config
```
find this:

SELINUX=enforcing

and update it to this :

SELINUX=disabled


### - Save and exit (:wq in vi).

### - Verify it and all set 

```bash
grep ^SELINUX= /etc/selinux/config
```
...
