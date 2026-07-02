
# Day 1 – System Administration Tasks (Nautilus Project)

## Overview
This document summarizes the configuration changes made on the application servers (`stapp01`, `stapp02`, `stapp03`) in the Stratos Datacenter as part of the Day 1 automation and security rollout.

---

## Task 1: Create User with Non‑Interactive Shell (App Server 2)
**Objective:** Create a user `ravi` (or `james`) with a non‑interactive shell for backup agent tools.

**Server:** `stapp02`  
**Credentials:** `steve / Am3ric@`

**Commands executed:**
```bash
ssh steve@stapp02
sudo useradd -s /sbin/nologin ravi

```

## Verification
grep ravi /etc/passwd
 ```Output: ravi:x:1001:1001::/home/ravi:/sbin/nologin```
