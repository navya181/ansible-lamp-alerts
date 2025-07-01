# 🐘 PHP Role

This role installs **PHP** and necessary modules for the LAMP stack on an Ubuntu server using Ansible.

---

## 🔧 What This Role Does

- Installs:
  - `php` – PHP scripting language
  - `libapache2-mod-php` – Enables Apache to run PHP files
  - `php-mysql` – Lets PHP interact with MySQL databases
- Notifies the Apache service to restart after installation (so PHP support is enabled)

---

## 🔁 Handler

This role triggers a handler:
```yaml
notify:
  - Restart Apache
```
Make sure you’ve defined this handler in your handler/main.yml.

## 🚀 Example Usage
```yaml
- hosts: all
  become: true
  roles:
    - php
```
