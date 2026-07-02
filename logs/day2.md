# Day 2 – System Administration Tasks (Nautilus Project)

## Overview
This document covers the Day 2 system administration task performed on App Server 1 in the Stratos Datacenter.

---

## Task: Create Temporary User with Expiry (App Server 1)
**Objective:** Create a temporary user `ammar` with an account expiry date of **2027-04-15** to support a developer's limited‑duration access.

**Server:** `stapp01`  
**Credentials:** `tony / Ir0nM@n`

### Steps Performed

1. **SSH into App Server 1:**
   ```bash
   ssh tony@stapp01

  ### Create the user with an expiry date:
  ```bash
  sudo useradd -e 2027-04-15 ammar
```

###Verification
```bash
sudo chage -l ammar
```
Look for the line:
Account expires                     : Apr 15, 2027
