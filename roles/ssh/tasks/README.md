# 🔐 SSH Role (Key-Based Access)

This role installs **OpenSSH Server** and sets up **key-based SSH access** for secure remote login using Ansible.

---

## 🔧 What This Role Does

- Installs the `openssh-server` package
- Creates a `.ssh` directory for the user if it doesn’t exist
- Adds the user’s public SSH key to `authorized_keys` for passwordless login

---

## 👤 Target User

This script is configured for the user:
navyasattineni


If you use a different username, update the playbook variables accordingly.

---

## 📝 Note

- The public key must exist locally at:
```bash
~/.ssh/ansible_key.pub
```
The .ssh folder is created with permission 0700, which is required for SSH to work properly.

You should not hardcode usernames in production — use variables or inventory vars.

---

## 🚀 Example Usage
```yaml

- hosts: all
  become: true
  roles:
    - ssh
```
