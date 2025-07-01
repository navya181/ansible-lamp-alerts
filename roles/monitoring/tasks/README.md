# 📊 Monitoring Role (Prometheus + Alertmanager)

This role sets up basic monitoring and alerting using **Prometheus**, **Node Exporter**, and **Alertmanager** on an Ubuntu server.

---

## 🔧 What This Role Does

- Installs:
  - **Prometheus** – collects system metrics
  - **Node Exporter** – sends CPU, RAM, and disk info to Prometheus
  - **Alertmanager** – sends alerts (e.g., to Spike.sh)
- Starts and enables all services so they run automatically on boot
- Uploads custom **alert rules** to `/etc/prometheus/alert-rules.yml`
- Updates the Prometheus config to load your alert rules
- Notifies Prometheus to restart if any config changes

---

## 🔁 Services Started

- `prometheus`
- `prometheus-node-exporter`
- `prometheus-alertmanager`

---

## 📂 File Locations

- Prometheus config: `/etc/prometheus/prometheus.yml`
- Alert rules: `/etc/prometheus/alert-rules.yml`

---

## 🚀 Example Usage in Playbook

```yaml
- hosts: all
  become: true
  roles:
    - monitoring
```
---

## 📝 Notes
This is a basic setup. Prometheus and Alertmanager web UIs are available on:

- [Prometheus Web UI](http://your-server-ip:9090)
- [Alertmanager Web UI](http://your-server-ip:9093)


Alerts will only work if connected to a receiver (like Spike.sh via webhook).


---
