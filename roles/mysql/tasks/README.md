# 🐬 MySQL Role

This role installs and configures **MySQL Server** on an Ubuntu machine using Ansible.

---

## 🔧 What This Role Does

- Installs the `mysql-server` package
- Starts and enables the MySQL service to run on system boot
- Sets the **root user password** for MySQL (using Ansible’s `mysql_user` module)

---

## 🚀 Example Usage in Playbook

```yaml
- hosts: all
  become: true
  roles:
    - MySQL
```
---

## ⚠️ Important Notes

- The root password is **hardcoded** in the playbook (`your_secure_password`).  
  For real environments, you should store passwords securely using **Ansible Vault**.
- The `check_implicit_admin: yes` option ensures that Ansible can connect even if MySQL uses auth plugins.
