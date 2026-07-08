# Day 7 – Password-less SSH Authentication from Jump Host to App Servers

## Objective
Set up password‑less SSH access from the `thor` user on **jump-host** to all application servers using their respective sudo users:
- `tony` on **stapp01**
- `steve` on **stapp02**
- `banner` on **stapp03**

This enables automated scripts running on the jump host to execute commands on the app servers without manual password entry.

---

## Environment Details

| Server      | Target User | Password  |
|-------------|-------------|-----------|
| jump-host   | thor        | (current) |
| stapp01     | tony        | Ir0nM@n   |
| stapp02     | steve       | Am3ric@   |
| stapp03     | banner      | BigGr33n  |

---

## – Generate an SSH Key Pair (on jump-host)

Check if a key already exists:
```bash
ls ~/.ssh/id_rsa.pub

# SSH Key Configuration Guide

If a key pair does not exist, generate a new one (password-less):

```bash
ssh-keygen -t rsa -b 2048 -N "" -f ~/.ssh/id_rsa
```

### Parameter Breakdown:
* **`-t rsa`** – Uses RSA encryption
* **`-b 2048`** – Key length (2048 bits is secure and fast)
* **`-N ""`** – Empty passphrase (no password prompt)
* **`-f ~/.ssh/id_rsa`** – Saves the key in the default location

---

##  – Copy the Public Key to Each App Server

Use `ssh-copy-id` to add the public key to each target user's `~/.ssh/authorized_keys`.

### stapp01 (user: tony)
```bash
ssh-copy-id tony@stapp01
```
*Enter password: `Ir0nM@n` when prompted.*

### stapp02 (user: steve)
```bash
ssh-copy-id steve@stapp02
```
*Enter password: `Am3ric@` when prompted.*

### stapp03 (user: banner)
```bash
ssh-copy-id banner@stapp03
```

###  – Verify Password-less Access
```text

ssh tony@stapp01 "hostname"
ssh steve@stapp02 "hostname"
ssh banner@stapp03 "hostname"
```
