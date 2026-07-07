# Day 6 – Cron Job Setup on All App Servers

## Objective
Install the `cronie` package, start the `crond` service, and add a sample cron job that runs every 5 minutes and writes `hello` to `/tmp/cron_text` for the **root** user.

**Servers:** `stapp01`, `stapp02`, `stapp03`  
**Credentials:**
| Server  | User   | Password  |
|---------|--------|-----------|
| stapp01 | tony   | Ir0nM@n   |
| stapp02 | steve  | Am3ric@   |
| stapp03 | banner | BigGr33n  |

---

## – Install `cronie` (on each server)

The `cronie` package provides the cron daemon and utilities.  
Use the appropriate package manager (`yum` or `dnf` – both work).

```bash
sudo yum install -y cronie

# Step 2 – Start and Enable crond Service
Start the cron daemon and enable it to start automatically at boot.

```bash
sudo systemctl start crond
sudo systemctl enable crond
```

Verify the service status:

```bash
sudo systemctl status crond
```

You should see `active (running)`.

## – Add the Cron Job for Root User
The cron job must run as root and execute:
`*/5 * * * * echo hello > /tmp/cron_text`

###  Using crontab -e 
Edit the root user’s crontab:

```bash
sudo crontab -e
```

Add the following line at the end:

```text
*/5 * * * * echo hello > /tmp/cron_text
```

Save and exit (e.g., `:wq` in vi).

## – Verify the Crontab
List the current cron jobs for root:

```bash
sudo crontab -l
```

You should see the line:

```text
*/5 * * * * echo hello > /tmp/cron_text
```
