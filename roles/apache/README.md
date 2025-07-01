# 🔒 Firewall Role (UFW)

This role configures the **Uncomplicated Firewall (UFW)** on Ubuntu servers to allow only the necessary traffic for LAMP stack services and monitoring tools.

---

## ✅ What It Does

- Installs `ufw` if not already present
- Allows incoming traffic for:
  - **Apache Web Server** (HTTP & HTTPS)
  - **Prometheus** (port **9090**)
  - **Node Exporter** (port **9100**)
  - **Alertmanager** (port **9093**)
- Enables UFW using `--force` to skip interactive confirmation

---

## 🚀 Example Usage

```yaml
- hosts: all
  become: true
  roles:
    - firewall
```
---
## 📝 Notes

- Be careful not to **lock yourself out** — UFW blocks everything except explicitly allowed ports.
- You can extend this role to allow more services (e.g., SSH, custom ports).
- For logging, you can enable UFW logs manually or via a task.

