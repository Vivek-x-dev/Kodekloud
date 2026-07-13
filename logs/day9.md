# Day 9 – Restore MariaDB Service on Database Server

## Issue
The Nautilus application cannot connect to the database because the `mariadb` service is down on **stdb01**.

**Server:** `stdb01`  
**Credentials:** `peter / Sp!dy`

---

## Resolution Steps

1. **SSH into the database server**:
   ```bash
   ssh peter@stdb01



| Command | Purpose |
| :--- | :--- |
| `sudo mkdir -p /run/mariadb` | Creates the directory (if missing) |
| `sudo chown mysql:mysql /run/mariadb` | Sets ownership to the `mysql` user and group |
| `sudo chmod 755 /run/mariadb` | Grants read/write/execute for owner, read/execute for others (secure) |
| `sudo systemctl start mariadb` | Starts the MariaDB service |
| `sudo systemctl status mariadb` | Verifies the service is running |

---

##  After the Fix

* MariaDB is now **active (running)**.
* The Nautilus application should be able to connect to the database.

---

##  Last Steps

Enable automatic startup:
```bash
sudo systemctl enable mariadb
```

Test database connectivity (from the app server or locally):
```bash
mysql -u <app-user> -p -e "SELECT 1"
```

stay tuend byeeee.
