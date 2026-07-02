# Task 4 – Grant Execute Permissions to Backup Script (App Server 2)

## Objective
Make the script `/tmp/xfusioncorp.sh` executable by all users on App Server 2 to enable automated backup processes.

**Server:** `stapp02`  
**Credentials:** `steve / Am3ric@`

---

## Steps Performed

###  SSH into App Server 2
```bash
ssh steve@stapp02
```
### Check current permissions and add 
```bash
ls -l /tmp/xfusioncorp.sh

then

sudo chmod a+x /tmp/xfusioncorp.sh
```
### then verify again and all set 
```bash
ls -l /tmp/xfusioncorp.sh

