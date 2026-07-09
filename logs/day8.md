# Day 8 – Install Ansible on Jump Host

## Objective
Install **Ansible version 4.8.0** on the Jump Host using `pip3` only, and ensure the `ansible` binary is available globally for all users.

**Server:** `jump-host`  
**User:** `thor`

---

## – Verify Python 3 and pip3

First, check that Python 3 and `pip3` are installed:

```bash
python3 --version
pip3 --version

```
If pip3 is not installed, install it:

```bash
sudo yum install -y python3-pip
```

Or for older systems:

```bash
sudo easy_install pip
```

> **Why pip3?** Ansible is a Python application, and using pip ensures we get the exact version requested (4.8.0) without relying on distribution repositories which may offer older versions.

---

## – Install Ansible 4.8.0 using pip3

Install the specific version:

```bash
sudo pip3 install ansible==4.8.0
```

* This installs Ansible and its dependencies in the Python site‑packages directory.
* The `sudo` is required because the installation is system‑wide.

---

##  – Verify the Installation

Check the installed version:

```bash
ansible --version
```

Expected output should show:

```text
ansible 4.8.0
```

*Note: If the `ansible` command is not found, proceed to Step 4.*

---

## – Make Ansible Binary Globally Available

`pip3` typically installs binaries in `/usr/local/bin/` or `/usr/bin/`. If the `ansible` command is not in the PATH for all users, create a symlink.

Check where pip installed Ansible:

```bash
which ansible
```

Or find it:

```bash
find /usr -name ansible -type f 2>/dev/null | grep bin
```

If it's in `/usr/local/bin/ansible`, ensure `/usr/local/bin` is in the system PATH. If not, create a symlink to a directory already in the default PATH:

```bash
sudo ln -s /usr/local/bin/ansible /usr/bin/ansible
```

Also create symlinks for other Ansible binaries (optional but recommended):

```bash
sudo ln -s /usr/local/bin/ansible-playbook /usr/bin/ansible-playbook
sudo ln -s /usr/local/bin/ansible-inventory /usr/bin/ansible-inventory
sudo ln -s /usr/local/bin/ansible-doc /usr/bin/ansible-doc
sudo ln -s /usr/local/bin/ansible-galaxy /usr/bin/ansible-galaxy
sudo ln -s /usr/local/bin/ansible-config /usr/bin/ansible-config
sudo ln -s /usr/local/bin/ansible-connection /usr/bin/ansible-connection
sudo ln -s /usr/local/bin/ansible-console /usr/bin/ansible-console
sudo ln -s /usr/local/bin/ansible-vault /usr/bin/ansible-vault
sudo ln -s /usr/local/bin/ansible-pull /usr/bin/ansible-pull
```

---
