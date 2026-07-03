# Day 3 – Disable Direct SSH Root Login (All App Servers)

## Objective
Enforce the new security protocol by preventing `root` from logging in directly via SSH on all application servers in the Stratos Datacenter.

---

## Servers & Credentials
| Server  | User   | Password  |
|---------|--------|-----------|
| stapp01 | tony   | Ir0nM@n   |
| stapp02 | steve  | Am3ric@   |
| stapp03 | banner | BigGr33n  |

---

## Procedure (Repeat on Each Server)

### SSH into the server
```bash
ssh tony@stapp01    # or steve@stapp02, banner@stapp03

```
###  Edit the SSH daemon configuration
```bash
sudo vi /etc/ssh/sshd_config
```
### Modify the PermitRootLogin directive

Locate the line containing PermitRootLogin.

```Change it to:
PermitRootLogin no
If the line is commented out (#PermitRootLogin yes), remove the # and set the value to no.

If the line does not exist, add it at the end of the file.
```

### Save the file and exit


### Restart the SSH service
```bash
sudo systemctl restart sshd
```
### Verify
```bash
sudo sshd -T | grep permitrootlogin
